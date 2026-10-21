# Monsnode Quad Player — Web prototype

GitHub Pages serves this static interface. A Cloudflare Worker fetches Monsnode search results, parses each `.listn` entry and its `redirect.php?v=...` link, and resolves selected redirects to `video.twimg.com` MP4 URLs.

## Deploy the Worker

From this folder's `worker` directory, run:

```powershell
npm install --save-dev wrangler@latest
npx wrangler login
npx wrangler deploy
```

Set `window.QUAD_API_BASE` in `config.js` to the deployed Worker URL. Search results use `/search`; selected videos resolve through `/resolve?id=<redirect-id>`.

## Publish on GitHub Pages

Upload only the static site files from the root of this folder: `index.html`, `config.js`, and optionally this `README.md`. Do not upload the `worker` folder; it is deployed separately and may contain `node_modules` with thousands of files. Configure GitHub Pages to deploy the `main` branch root.

Monsnode may change its page markup or restrict Worker requests. This prototype only uses links returned by Monsnode and does not bypass access restrictions.
