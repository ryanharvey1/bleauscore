# BleauScore

Live climbing-conditions score for Fontainebleau sandstone — Rocher Canon, Bas Cuvier, Franchard Isatis and Apremont. In English and French.

*Note de grimpe en direct pour le grès de Fontainebleau, en anglais et en français.*

It's a single static page. The browser calls the free [Open-Meteo](https://open-meteo.com) forecast API directly (no key, CORS-enabled), so there's no server and nothing to keep running.

## Publish on GitHub Pages

1. Create a new **public** repository on GitHub named `bleauscore`.
2. Click **Add file → Upload files**, drag in `index.html`, `README.md` and `.nojekyll`, then **Commit changes**.
   (`.nojekyll` is optional; the site works without it.)
3. Go to **Settings → Pages**. Under *Build and deployment*, set **Source: Deploy from a branch**, **Branch: `main`**, folder **`/ (root)`**, and **Save**.
4. After a minute the site is live at `https://<your-username>.github.io/bleauscore/`.

Or from a terminal in this folder:

```bash
git init -b main && git add . && git commit -m "BleauScore"
gh repo create bleauscore --public --source=. --push
gh api -X POST repos/{owner}/bleauscore/pages -f "source[branch]=main" -f "source[path]=/"
```

## Sharing

- **Language:** EN/FR switch in the top bar. The page opens in French for French-language browsers, remembers each visitor's choice, and a link can force it: `…/bleauscore/?lang=fr`.
- **Sector:** link straight to one with a hash: `#apremont`, `#cuvier`, `#isatis`, `#canon` — e.g. `…/bleauscore/?lang=fr#apremont`.
- Every visit pulls a fresh forecast; a tab left open more than 30 minutes refreshes itself when you come back to it.

## Notes

- Open-Meteo's free API is for non-commercial use and asks for attribution (the footer links to it).
- To add a sector, add an entry to `SECTORS` in `index.html` (`id`, `name`, `lat`, `lon`) and a `"note.<id>"` line in both the `en` and `fr` blocks of `STR`.
- All text lives in the `STR` table near the top of the script, so wording changes don't touch the scoring code.
