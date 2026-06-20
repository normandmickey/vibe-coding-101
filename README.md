# 🦞 Vibe Coding 101

**A complete, no-fluff guide to vibe coding — what it is, how to do it well, and how to survive the disasters.**

A static multi-page website built with hand-written HTML and CSS. No frameworks, no build step, no JavaScript. Just open the files in a browser.

🔗 **Live site:** [vibe-coding-101.preview.saasclaw.ai](https://vibe-coding-101.preview.saasclaw.ai)

---

## What is this?

"Vibe coding" is the practice of building software by describing what you want in natural language and letting an AI generate the code. This site is a plain-English educational guide to it — friendly, fun, and honest about the pitfalls.

It's structured as a small content site: a main guide, four topical deep-dives, a glossary, and a product page for [SaaSClaw](https://saasclaw.ai) (the platform this project lives on).

## Pages

| Page | Title | What it covers |
|------|-------|----------------|
| [`index.html`](index.html) | The Complete Guide to Vibe Coding | The intro — what vibe coding is, what you can build, the fun, and the dangers |
| [`prompting.html`](prompting.html) | Prompting for Vibe Coders | How to talk to your AI: clarity, context, the words that move the needle |
| [`tools.html`](tools.html) | The Vibe Coder's Toolkit | The stack — AI editors, models, and where to host what you build |
| [`mistakes.html`](mistakes.html) | Mistakes & How to Survive Them | 7 classic mistakes, each with a survival move |
| [`deploy.html`](deploy.html) | "It Works On My Machine" | The unglamorous truth about shipping and maintaining apps |
| [`glossary.html`](glossary.html) | Vibe Coding Glossary | Theme-grouped definitions (Basics / Tooling / Danger Zones) with difficulty pills |
| [`saasclaw.html`](saasclaw.html) | Meet SaaSClaw | The platform page — why SaaSClaw is a better place to vibe code |

All seven pages are cross-linked through a shared navigation bar.

## Design system

Every page shares the same CSS design tokens and components, duplicated inline per file (no shared stylesheet — each page is fully self-contained).

### Color tokens

```css
:root {
  --accent: #7c3aed;         /* primary purple */
  --accent-dark: #5b21b6;
  --text: #1e293b;           /* near-black body text */
  --muted: #64748b;          /* secondary text */
  --bg: #ffffff;
  --soft: #f5f3ff;           /* soft purple wash */
  --warn-bg: #fef3c7;        --warn-border: #f59e0b;    /* amber */
  --danger-bg: #fee2e2;      --danger-border: #ef4444;  /* red */
  --success-bg: #dcfce7;     --success-border: #22c55e; /* green */
}
```

### Reusable components

| Component | Purpose |
|-----------|---------|
| `.eyebrow` | Small uppercase pill label above a page title |
| `.lead` | Larger intro paragraph |
| `h2 .num` | Numbered section headings (e.g. `01`, `02`) |
| `.callout` + variants | Highlighted notice boxes: `.callout.warn`, `.callout.danger`, `.callout.success` |
| `.callout-title` | Bold label inside a callout |
| `.grid` / `.card` | Responsive auto-fit card grid (`minmax(220px, 1fr)`, collapses to 1 column on mobile) |
| `.pill` | Small rounded tag (used in glossary for difficulty) |
| `.timeline` / `.timeline-item` | Vertical timeline (used in deploy.html) |
| `.cta` | Centered call-to-action block (usually links to SaaSClaw) |
| `blockquote` | Italic accent quote with left border |

### Navigation

A **CSS-only dropdown** — no JavaScript. The nav appears identically on all 7 pages:

```
🦞 Vibe Coding 101   [Guides ▾]   Glossary   Meet SaaSClaw
                          │
                          └─ The Guide
                             Prompting
                             Toolkit
                             Mistakes
                             Shipping
```

The "Guides ▾" dropdown uses a native `<details>`/`<summary>` element with `flex-wrap: wrap` on the nav so it stays usable on mobile.

## How it works

- **No build step.** These are plain `.html` files. Open them directly, or serve the folder with any static host.
- **Self-contained pages.** Each file has its own `<style>` block, so any page can be opened standalone with full styling.
- **Responsive.** Media query at `max-width: 600px` collapses grids to one column and shrinks headings.

## Tech stack

- **HTML5** — semantic structure (`<nav>`, `<header>`, `<article>`, `<footer>`)
- **CSS3** — custom properties (variables), grid, flexbox, native `<details>` dropdown
- **That's it.** No JS, no dependencies, no package manager.

## Local preview

```bash
# from the project root
python3 -m http.server 8000
# then open http://localhost:8000
```

## Project layout

```
vibe-coding-101/
├── index.html        # Main guide (homepage)
├── prompting.html    # Prompting deep-dive
├── tools.html        # Toolkit / stack overview
├── mistakes.html     # Common mistakes + survival guide
├── deploy.html       # Shipping & maintenance survival guide
├── glossary.html     # Term definitions (theme-grouped)
├── saasclaw.html     # SaaSClaw product page
└── README.md         # This file
```

## Conventions for editing

If you add or change a page, keep these rules so the site stays consistent:

1. **Clone an existing page** (e.g. `index.html`) as your starting template — it has the full design system inline.
2. **Reuse the components above.** Don't invent new color values; use the `--*` tokens.
3. **The nav must match exactly** across all pages: brand + Guides dropdown + Glossary + Meet SaaSClaw.
4. **Keep CSS inline per-file** (self-contained pages is an intentional choice).
5. **Set a unique `<title>` and meta description** on every page.

---

Built on [SaaSClaw](https://saasclaw.ai) — a better place to vibe code. 🦞
