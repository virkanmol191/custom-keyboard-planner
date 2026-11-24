# Custom Keyboard Planner

A single-file, browser-based planner for mechanical keyboard switch builds. Lay out your board, paint every key with the switch type you want, watch the totals update live, and (optionally) pull matching switches from the [neomacro.in](https://neomacro.in) catalogue straight into a cart.

**Live site:** https://virkanmol191.github.io/custom-keyboard-planner/

> **Unofficial.** This is a vibe-coded, user-made project. It is not affiliated with, endorsed by, or maintained by neomacro.in.

## The story

I wanted to build my first custom keyboard and needed a way to plan it: which keys get which switches, how many of each, and what it would all cost. I looked around and couldn't find anything like it online, so I went full Thanos and built it myself over one weekend.

What started as a quick helper grew into a proper planner: it paints a layout, counts every switch type, combines coverage totals and can even build a neomacro.in cart for you.

## Thanks

A huge thank you to **dabber443** on the neomacro.in Discord, who tested the planner and helped me add new features along the way.

## Features

- **Layout presets:** 60%, 65%, 75%, TKL and 100%, plus an on-board per-key editor (rename, resize, add or remove keys).
- **Brushes:** colour-coded switch types (tactile, linear, silent, anything you like). Mark keys by clicking them or by pressing the real key on your keyboard.
- **Combine brushes:** fold any brush into any other to get combined coverage totals (for example tactile + silent), with a card, chart bar and export line per group.
- **Live stats and chart:** per-brush counts, percentages, unchecked keys and a coverage chart.
- **neomacro.in catalogue:** browse switches with live price and stock, assign them to brushes, keep a watchlist, add your own sources, apply a coupon and send the required packs to the neomacro.in cart. Product photos with a white background are made transparent automatically.
- **Shopping packs:** add extra packs of any switch on top of what your keyboard needs. Extra packs count towards the estimate and the checkout.
- **Allocation diagram:** opening it tucks the live keyboard away and shows a small colour-only preview of your board next to the chart.
- **Save and share:** save the whole workspace as a self-contained HTML file, copy or export the layout as text, and paste or open an existing layout (`.txt`, saved `.html` or `.json`).
- **Quality of life:** light and dark themes, accent colour and "tone everything down" graphics options (the sliders icon in the header), unsaved-changes prompt before closing the tab, first-run setup guide.

## Getting started

No build step and no dependencies to install.

1. Download or clone the repository.
2. Open `index.html` in a modern browser (Chromium, Firefox or Safari).

Or use the live site above. To host your own copy with GitHub Pages: **Settings → Pages → Deploy from a branch → `main` / `(root)`**.

> Styling uses the Tailwind Play CDN, so the first load needs an internet connection.

## Using it

1. Name your workspace and add brushes, or paste/open an existing layout.
2. Pick a layout from the header dropdown.
3. Choose a brush and click keys (or press keys on your keyboard) to assign them. Use **lock keyboard** if you need to type without marking keys.
4. Open **brushes & settings** to rename brushes, change colours, combine brushes or paste an existing layout.
5. Open the catalogue to assign neomacro.in switches to your brushes and check out.
6. Use **save file** to keep your work. Each saved copy carries its own state.

### Layout text format

Copy a layout from the **copy layout** button and paste it back at any time:

```text
my first board (84 keys total)
layout: 75_std (75% standard (84 keys))
total tactile coverage (+buy): 3 / 84 (3.6%)
tactile [#3b82f6]: 2 switches -> esc (escape), f1 (f1)
linear [#eab308]: 1 switches -> f2 (f2)
buy [#10b981] (+primary): 1 switches -> f3 (f3)
unchecked: 80 keys
```

The first line sets the workspace name. `(+primary)` or `(+brush name)` after a brush marks it as combined into another brush.

## neomacro.in integration

- Product data comes from neomacro.in's public store feed (`products.json`).
- Coupon codes are checked against the website, with a default fallback if it cannot be reached.
- **Checkout** posts the required switch packs (1 pack = 10 switches) to `neomacro.in/cart/add` in a new tab; you complete payment on their site.
- If the live feed is unavailable the planner keeps working with whatever data it already has.

## Privacy

There is no backend, analytics or account system. The browser stores only two small preferences in `localStorage` (the intro guide choice and your graphics options). Your workspace lives in the page and in files you save yourself.

## Customising

| What | Where |
| --- | --- |
| Splash logo image | set `NEOMACRO_LOGO_SRC` near the end of `index.html` |
| Splash letter text | edit the paragraphs inside the element with `id="splashLetterBody"` |
| Accent colours | `window.__KP_ACCENTS` in the `<head>` script |

## Project structure

```text
.
├── index.html     the whole application (HTML, CSS and JavaScript)
├── README.md
├── LICENSE
├── .editorconfig
└── .gitignore
```

## Contributing

Issues and pull requests are welcome. Keep changes small and focused, and test in at least one Chromium-based browser and one other engine. The app is intentionally a single self-contained file.

## Author

Made by xnmoll ([@virkanmol191](https://github.com/virkanmol191)).

## License

Released under the [MIT License](LICENSE).
