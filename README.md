# `.well-known` (domain verification)

Public **well-known** files for `walkingriver.com`, served at the domain root via GitHub Pages.

| Local folder | GitHub repo | Published URL |
|--------------|-------------|---------------|
| `~/git/well-known` | [`walkingriver/.well-known`](https://github.com/walkingriver/.well-known) | `https://walkingriver.com/.well-known/` |

The repo is named `.well-known` on GitHub (required URL path segment). The local clone uses `well-known` so the directory is not hidden.

## Files

Files live at the **repo root** (not in a nested `.well-known/` folder). Project Pages maps repo name → URL path:

| Repo file | Live URL |
|-----------|----------|
| `assetlinks.json` | `https://walkingriver.com/.well-known/assetlinks.json` |
| `apple-app-site-association` | `https://walkingriver.com/.well-known/apple-app-site-association` |

## Setup

1. Create the GitHub repo: `gh repo create walkingriver/.well-known --public --source=. --remote=origin`
2. Enable **Pages → Build and deployment → GitHub Actions** in repo settings.
3. Replace `REPLACE_WITH_RELEASE_SHA256_FINGERPRINT` in `assetlinks.json` with the **App signing** SHA-256 from Play Console → App integrity.
4. Push `main`; verify:

   ```bash
   curl -sS https://walkingriver.com/.well-known/assetlinks.json
   ```

Requires the org site (`walkingriver.github.io`) to use custom domain `walkingriver.com` so project paths inherit the apex domain.

## Local preview

```bash
python3 -m http.server 8080
```

Open http://localhost:8080/assetlinks.json (repo root simulates the `/.well-known/` path when deployed).
