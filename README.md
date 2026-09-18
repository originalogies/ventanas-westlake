# Ventanas of Westlake

Marketing site for Ventanas of Westlake — an exclusive gated community of 52 homesites within Entrada, Westlake, TX.
Static site (plain HTML/CSS/JS, no build step). Presented by George & Noonan Real Estate Group at Synergy Realty, LLC.

## Files
- `index.html` — the site (self-contained)
- `thank-you.html` — confirmation page shown after a form submission
- `documents/index.html` — Community Documents page, served at `/documents/` (linked from the footer)
- `docs/` — put community PDFs here (CC&Rs, bylaws, design guidelines, plat) and update the links in `documents/index.html`
- `netlify.toml` — publish + security/caching headers
- `assets/` — hero photo, lot map, and logos (see "Assets" below)

## Deploy: GitHub → Netlify → Cloudflare

### 1. GitHub
1. Create a new repo (e.g. `ventanas-westlake`).
2. Add these files and push:
   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/<you>/ventanas-westlake.git
   git push -u origin main
   ```

### 2. Netlify
1. Netlify → **Add new site → Import an existing project** → pick the GitHub repo.
2. Build command: leave **empty**. Publish directory: `.` (root). Deploy.
3. **Forms:** the contact form is already wired for Netlify Forms. After the first deploy, submissions appear under **Site → Forms → ventanas-inquiry**. Add a notification email there (Forms → Settings → Form notifications) so you and the team get each lead.

### 3. Custom domain + Cloudflare
Two common setups:

**A. Keep DNS at Cloudflare, point to Netlify (recommended):**
1. Netlify → **Domain settings → Add a domain** → `ventanaswestlake.com`.
2. In Cloudflare DNS, add the records Netlify shows (typically a `CNAME`/`ALIAS` for `www` to your Netlify subdomain, and an apex record via Cloudflare flattening). Set proxy status to **Proxied** (orange cloud).
3. In Cloudflare **SSL/TLS**, use **Full (strict)**. Netlify auto-provisions its own certificate; Full (strict) keeps both ends encrypted.

**B. Let Netlify handle DNS:** point the domain's nameservers to Netlify instead. Simpler, but you lose Cloudflare's proxy/CDN in front.

> Note: you're currently on Squarespace. Only switch the live DNS **after** the Netlify deploy looks right on its temporary URL, to avoid downtime.

## Assets (included)
All imagery lives in `assets/` and is already wired into the site:
- `hero.jpg` — Ventanas home at dusk, 16:9 crop (hero)
- `architecture.jpg` — modern home at dusk (architecture section)
- `lot-map.png` — site plan with all 52 homesites (QR code removed)
- `ventanas-logo-white.png` / `ventanas-logo-black.png` — brand wordmark (white for the dark site, black for favicon/print)
- `otter-partners.png` — developer logo, transparent background
- `george-noonan.png` — brokerage wordmark, transparent background
- `social-preview.jpg` — 1200×630 link preview image

To add more photography (streetscapes, amenities, interiors), drop files into `assets/` and reference them in `index.html`. The `.arch .media img` block and the three `.life-grid` columns are natural places to add images.

## Editing content
All copy lives in `index.html` as plain text. Phone numbers, TREC links, and the address are in the contact section and footer.
