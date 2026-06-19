# CYBORG // Neural Interface

A sci-fi cyberpunk landing page built with pure HTML, CSS, and vanilla JavaScript. No frameworks, no dependencies — just a single self-contained file.

---

## Preview

The page features a full-screen hero with animated glitch text, a floating particle system, HUD-style corner decorations, and a scrollable layout with four content sections.

---

## Sections

**Hero** — Full-viewport intro with glitch-animated headline ("Human Enhancement Protocol"), system status bar, and HUD corner overlays showing live stats like core temp, sync rate, and battery.

**Enhancement Modules** — Six feature cards showcasing cybernetic upgrades: Neural Link, Optical Cortex, Power Core, Exo-Frame, Mesh Network, and Nano Repair. Cards use a clipped polygon border and a hover sweep animation.

**System Metrics** — Animated counters that count up on scroll: 99.9% uptime, 0.04ms latency, 847 installations, year 2045.

**Command Console** — A typewriter-effect terminal that plays back a boot sequence when scrolled into view.

**CTA** — A call-to-action block with an "Initialize Sequence" button.

---

## Features

- **Glitch text effect** — CSS `::before`/`::after` pseudo-elements with `clip-path` and keyframe animations create a chromatic-aberration glitch on the hero title
- **Particle canvas** — 100 floating particles drawn on a `<canvas>` with mouse-repulsion interaction and connection lines between nearby particles
- **Scroll reveal** — `IntersectionObserver` fades and slides elements up as they enter the viewport
- **Animated counters** — Stats count up with an ease-out curve when scrolled into view
- **Terminal typewriter** — Lines are injected one-by-one with staggered delays to simulate a real boot sequence
- **Scanline overlay** — A fixed `repeating-linear-gradient` on `body::before` gives a CRT monitor feel
- **Ripple effect** — Click any button to see a radial ripple animate outward from the cursor

---

## Fonts

All fonts are loaded from Google Fonts:

- `Orbitron` — headings, logo, buttons
- `Rajdhani` — body text
- `Share Tech Mono` — monospace labels, terminal, HUD data

---

## Color Palette

| Name | Hex |
|---|---|
| Neon Cyan | `#00f0ff` |
| Neon Magenta | `#ff00ff` |
| Neon Green | `#00ff88` |
| Dark Background | `#050508` |
| Panel Background | `rgba(10, 12, 20, 0.85)` |

---

## Usage

No build step needed. Just open the file in a browser:

```bash
# Download and open directly
open cyborg_landing_page.html

# Or serve locally
npx serve .
python -m http.server 8000
```

Works in all modern browsers. Requires an internet connection to load Google Fonts.

---

## File Structure

Everything lives in a single file:

```
cyborg_landing_page.html
├── <head>          — meta, Google Fonts link
├── <style>         — all CSS (CSS variables, layout, animations, responsive)
├── <body>          — HTML structure (nav, hero, features, stats, terminal, CTA, footer)
└── <script>        — particles, scroll reveal, counters, terminal typewriter, ripple
```

---

## Bug Fix (v1.1)

The "Enhancement Modules" section heading was visually overlapping due to the hero parallax scroll effect applying `translateY` to the entire `.hero` container. This caused the hero div to physically slide over the features section on scroll.

**Fix:** Parallax is now applied only to the inner `.hero-content` element at a reduced intensity (0.2x), and the `.features` section has an explicit background and elevated `z-index` to cleanly sit above the hero layer.
