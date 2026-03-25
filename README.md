# GSAP Animated Stacking Cards

A small single-page animation demo built with GSAP + ScrollTrigger.

The page includes:
- A hero section with an animated title reveal on page load
- A pinned scroll section with stacked cards
- Scroll-driven card transitions where each card slides in from the bottom
- A full-screen footer section to complete the scroll narrative

## Preview Behavior

1. On load, the `SOLUTIONS` title animates from wide letter spacing and blur to a sharp final state.
2. On scroll, the `.stack-container` gets pinned.
3. Each subsequent `.card` animates upward (`yPercent: 100 -> 0`) as you continue scrolling.

## Tech Stack

- HTML5
- CSS3
- JavaScript (vanilla)
- GSAP 3.12.2 (CDN)
- ScrollTrigger plugin (CDN)

## Project Structure

```text
.
|-- index.html
|-- script.js
|-- style.css
`-- assets/
```

Notes:
- Main implementation currently lives inside inline `<style>` and `<script>` blocks in `index.html`.
- `script.js` and `style.css` exist but are empty right now.

## Run Locally

Because assets are loaded via relative paths and GSAP is loaded from CDN, run this with a local web server:

```bash
# from project root
python3 -m http.server 8000
```

Then open:

- http://localhost:8000

## Key GSAP Logic

- Plugin registration: `gsap.registerPlugin(ScrollTrigger)`
- Hero intro animation: `gsap.fromTo(".main-title", ...)`
- Card collection: `gsap.utils.toArray(".card")`
- Scroll timeline: `gsap.timeline({ scrollTrigger: { pin: true, scrub: true, ... } })`
- Card stacking animation:

```js
cards.forEach((card, i) => {
  if (i > 0) {
    tl.from(card, { yPercent: 100, ease: "none" });
  }
});
```

## Customization Ideas

- Move inline CSS/JS into `style.css` and `script.js` for cleaner separation.
- Tune scroll distance via `end: "+=300%"`.
- Add more cards by duplicating `.card` blocks in `index.html`.
- Add responsive typography/media queries for smaller screens.

## License

No license file is included yet. Add one if you plan to share or publish this project.
