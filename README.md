# Boathouse Foundation Repair & Maintenance

A single-page marketing site for a "Boathouse Foundation Repair & Maintenance" service line, built as a static HTML/CSS/JS page. No framework, no build step, no dependencies — just `index.html` plus local assets.

## Project structure

```
.
├── index.html        # entire page (markup, CSS, JS in one file)
├── assets/            # locally hosted images used on the page
│   └── dbs/            # reference photos/logos/badges (rehosted, no external hotlinking)
├── package.json       # optional local dev script only — no build/runtime deps
├── vercel.json         # static hosting config (cache headers, clean URLs)
└── .gitignore
```

Everything the page needs — photos, icons, logos, trust badges — is stored under `assets/` and referenced with relative paths. The page has **no external image dependencies**, so it won't break if a third-party site changes or removes an asset.

## Local development

No build step is required. Either:

**Option A — open directly**
```bash
open index.html
```

**Option B — run a local server** (recommended, avoids any `file://` quirks)
```bash
npm run dev
```
This runs `npx serve . -l 4210` and serves the site at http://localhost:4210.

## Deploying

### 1. Push to a private GitHub repository

```bash
# from inside this project folder
git add -A
git commit -m "Initial commit"

# create the repo on GitHub first (web UI, or `gh repo create` if you have the GitHub CLI),
# then point this local repo at it:
git remote add origin git@github.com:<your-username>/<repo-name>.git
git branch -M main
git push -u origin main
```

### 2. Deploy to Vercel

**Via the Vercel dashboard (recommended):**
1. Go to [vercel.com/new](https://vercel.com/new) and import the GitHub repository.
2. Framework preset: **Other** (static site — no build command, no output directory override needed).
3. Deploy.

**Via the Vercel CLI:**
```bash
npm i -g vercel   # if not already installed
vercel login
vercel            # preview deployment
vercel --prod     # production deployment
```

`vercel.json` is already configured for clean URLs and long-lived caching on `/assets/*`.

## Content notes

This page recreates the layout and structure of an existing foundation-repair company's real site (DBS Repair) as a new "boathouse" service page, and reuses that company's real logo, trust badges, and project photography (now rehosted locally under `assets/`). Before deploying this publicly:

- Confirm you have the rights/authorization to use DBS Repair's branding, photography, and customer review content.
- Replace placeholder phone numbers and CTA links (`tel:`, `#contact`, social links) with the correct live numbers/URLs.
- Update the ZIP code / service-area lookup form — it is currently a static UI with no backend wired up.

## License

Private — not licensed for redistribution.
