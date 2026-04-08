# Chaucerian-Hands
Raise your hands to the webcam and watch Chaucer's words appear at your fingertips. No install needs - runs in your browser! (Made for the Guild of Medieval Makers introduction post 'Victoria Craggs')

# ❦ The Craft So Long to Lerne

**A hand-tracking experiment with Chaucer — raise your hands and watch medieval verse appear at your fingertips.**

## What It Does

Open `index.html` in your browser, allow camera access, and raise both hands with fingers spread. Chaucer's line appears — one word per fingertip:

> **The lyf so short, the craft so long to lerne.**
> — Geoffrey Chaucer, *The Parliament of Fowls*

Shake your hands and the text changes to:

> **With a community, not so long at all!**

## Try It Now

1. **Download** this repository (click the green **Code** button → **Download ZIP**)
2. **Unzip** the folder
3. **Open** `index.html` in Chrome, Edge, or Firefox
4. **Allow** camera access when prompted
5. **Raise both hands** with fingers spread

That's it. No installation, no terminal, no servers.

> **Privacy note:** Your camera feed is processed entirely in your browser using [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands.html). No video or data is sent anywhere.

## How to Customise the Text

Want to display your own words? Open `index.html` in any text editor (Notepad, TextEdit, VS Code — anything works). Near the top of the `<script>` section, you'll find this block:

```javascript
const QUOTES = [
  // Quote 0 — displayed first
  ["The", "lyf", "so", "short,", "the", "craft", "so", "long", "to", "lerne."],
  // Quote 1 — shown after shaking
  ["With", "a", "community,", "not", "so", "long", "at", "all!", "✦", "✦"],
];
```

### To change the words:

Edit the text inside the quotation marks. Each word maps to one fingertip, reading left to right across both hands (left pinky → left thumb, then right thumb → right pinky).

**Keep exactly 10 words per line** for two hands. If your phrase has fewer than 10 words, pad the end with `"✦"` or `""`. If it has more, you'll need to abbreviate.

### To add more quotes:

Add another line to the array. Each shake cycles to the next quote:

```javascript
const QUOTES = [
  ["The", "lyf", "so", "short,", "the", "craft", "so", "long", "to", "lerne."],
  ["With", "a", "community,", "not", "so", "long", "at", "all!", "✦", "✦"],
  ["Your", "new", "quote", "goes", "here,", "ten", "words", "in", "a", "row."],
];
```

Save the file and refresh your browser — that's all.

## How It Works (for the curious)

The page loads **MediaPipe Hands**, a free hand-tracking library from Google that runs entirely in your browser. It identifies 21 landmarks on each hand, including the fingertips. The code:

1. Opens your webcam and feeds each frame to MediaPipe
2. Finds the fingertip positions (landmarks 4, 8, 12, 16, 20)
3. Draws each word from the current quote at the corresponding fingertip
4. Monitors wrist movement — if rapid back-and-forth motion is detected (a "shake"), it advances to the next quote

All of this happens on your machine. The only external resources loaded are the MediaPipe model files and two Google Fonts.

## Requirements

- A modern browser (Chrome, Edge, or Firefox recommended)
- A webcam
- An internet connection (to load MediaPipe from CDN on first visit)

## License

Do whatever you like with this. It's a small thing made for a community of people who love old words and new tools.
