# prithishshan.github.io

Personal site for Prithish Shan — an on-scroll **3D carousel** portfolio. Each domain
(MyoVerse, Medical AI, Foundational AI, AI Apps) is a rotating 3D ring of project
tiles; scrolling rolls each ring left, and clicking a title unravels the ring and
**blooms** a grid of project detail cards into view.

Built on the Codrops [3D Carousel](https://github.com/codrops/3DCarousel/) engine
(GSAP ScrollSmoother + ScrollTrigger + SplitText). The engine is reused as-is; only the
content and styling are custom.

## Stack
Plain HTML / CSS / JS. No build step, no framework. Deploys directly to GitHub Pages.

| File / Dir | Purpose |
|------------|---------|
| `index.html` | Hero (name, photo, contact, education) + 4 carousel scenes + 4 detail previews |
| `css/base.css` | Codrops carousel base styles (unchanged) |
| `css/portfolio.css` | **Edit this** for look & feel — nav, hero, card gradients, detail cards, themes |
| `js/index.js` | Codrops carousel engine. Only change from upstream: the `preloadImages` helper is inlined (removes the ES-module import) so the page also runs from a `file://` double-click |
| `js/*.min.js` | Vendored GSAP + imagesLoaded libraries |
| `assets/headshot.jpg` | **Add your photo here** (4:5). Missing → falls back to the "PRS" monogram |
| `Prithish_Shan_Resume.pdf` | Résumé download |
| `favicon.svg`, `.nojekyll` | Icon + Pages "serve as-is" flag |

## Editing content
All content is static HTML in `index.html`:

- **Carousel tile** = a `.carousel__cell > .card[data-theme]` inside a `.scene`. Its
  `.scene__title a[href="#preview-…"]` links to the matching preview.
- **Detail card** = a `.grid__item[data-theme]` inside the matching `.preview`.
- Add/adjust a tile by editing both the card and its detail item. Set the scene's
  `data-radius` to size the ring (more tiles → larger radius).
- `data-theme` values: `myoverse`, `medical`, `foundational`, `aiapps` (colors defined
  as CSS variables at the top of `portfolio.css`).

## Local preview
The demo works from a plain `file://` open, but a server is closest to production:

```bash
python -m http.server 8000   # then visit http://localhost:8000
```

## Deploy
Push to the `prithishshan.github.io` default branch. In **Settings → Pages**, set Source
to the default branch, root. Served over https, so everything (including the carousel)
runs normally.
