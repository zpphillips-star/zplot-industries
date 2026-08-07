# Z-Plot Industries — zplotindustries.com

One-page app directory for Z-Plot Industries, served via **GitHub Pages** at [zplotindustries.com](https://zplotindustries.com).

## Tech stack

Plain HTML5 + CSS custom properties. No build step, no npm, no framework. Edit and ship directly. Branding assets live in `assets/` and were sourced from the local `files.zip` package.

---

## App links

Canonical public domains are used where available. Vercel deployment URLs are retained only where no separate public domain has been confirmed.


| App | URL | Status |
|-----|-----|--------|
| TrueStar | https://truestar.vercel.app | ✅ Live |
| Hallowed Hop Society | https://hallowedhopsociety.com | ✅ Live |
| Family Fables | https://familyfables.org | ✅ Live |
| Woodinville | *(TBD — no repo detected)* | 🚧 TODO |
| CastWA | https://castwa.com | ✅ Live |
| Scorpanion | https://scorpanion.com | ✅ Live |
| WCScores | https://wcscores.com | ✅ Live |

> **Woodinville app URL** — no repo was found under `zpphillips-star` at time of site creation. Update the `href` in `index.html` and remove the `card--todo` class when the app is ready.

---

## GitHub Pages setup

### 1. Enable GitHub Pages in repo settings

```bash
# Via gh CLI (after repo exists):
gh api repos/zpphillips-star/zplot-industries/pages \
  --method POST \
  --field source='{"branch":"main","path":"/"}'
```

Or in the GitHub UI: **Settings → Pages → Source → Deploy from a branch → main / (root)**.

### 2. CNAME file

The `CNAME` file at the repo root contains exactly:

```
zplotindustries.com
```

GitHub Pages reads this and serves the site at your custom domain.

---

## Bluehost DNS configuration

Set these records in your **Bluehost DNS Zone Editor** (do NOT use Bluehost's Parked/Redirect features):

### A records — point apex domain to GitHub Pages IPs

| Type | Host | Points to | TTL |
|------|------|-----------|-----|
| A | @ | 185.199.108.153 | 600 |
| A | @ | 185.199.109.153 | 600 |
| A | @ | 185.199.110.153 | 600 |
| A | @ | 185.199.111.153 | 600 |

### CNAME record — www subdomain

| Type | Host | Points to | TTL |
|------|------|-----------|-----|
| CNAME | www | zpphillips-star.github.io | 600 |

> DNS propagation can take 10 minutes to 48 hours. GitHub Pages also provisions a free TLS certificate via Let's Encrypt — check the **Pages** settings tab to enable "Enforce HTTPS" once DNS resolves.

---

## Verify deployment

```bash
# Check GitHub Pages API status
gh api repos/zpphillips-star/zplot-industries/pages

# DNS check (once propagated)
nslookup zplotindustries.com
# Should return the four GitHub Pages IPs above

# HTTPS check
curl -I https://zplotindustries.com
```

---

## Local preview

No build step needed — just open `index.html` in a browser, or use any static server:

```bash
# Python 3
python -m http.server 8080

# Node (npx)
npx serve .
```

---

## Updating app links

1. Open `index.html`
2. Find the card for the app you want to update
3. Change the `href` attribute on the relevant app CTA/link
4. Remove the coming-soon card styling/badge when ready
5. Commit and push — GitHub Pages deploys automatically within ~30 seconds

---

## Repository structure

```
zplot-industries/
├── index.html   # Main (and only) page
├── style.css    # All styles — mobile-first, custom properties
├── assets/      # App icons and Z-Plot brand assets
├── CNAME        # Custom domain: zplotindustries.com
└── README.md    # This file
```
