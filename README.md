# webservco/pwa-vanilla

A Progressive Web App test.

Installable static web page with a service worker written in plain JavaScript, for testing caching, install detection and app styling without a framework.

- Requires: [ddev](https://ddev.com/), or any web server that serves `public/` over HTTPS
- Related: `webservco/app-skeleton` (a SvelteKit project template with a similar service worker)

---

## Installation

```shell
git clone git@github.com:webservco/pwa-vanilla.git
cd pwa-vanilla
ddev start
```

The URL is `https://pwa.ddev.site`.

---

## Usage

Open the page, then install it from the browser menu. The page shows which mode it runs in: in the browser, installed, or installed in standalone mode.

| File | Purpose |
| --- | --- |
| `public/index.html` | The page. Registers the service worker. |
| `public/service-worker.js` | Caches the static files on install, deletes old caches on activate, and serves every request cache first. |
| `public/app.webmanifest` | App name, icons, colors and display mode. |
| `public/css/app.css` | Accent color, system fonts, no text selection in the navigation, and the display mode tests. |

The service worker also generates `/js/worker-generated-script.js`, which doesn't exist on the server. Once the service worker controls the page, the script loads and shows a "hello" alert.

---

## Notes

Change `APP_VERSION` in `public/service-worker.js` after changing a file. The cache name includes it, and without a new name the old files stay cached.

Every response gets cached, including files from other sites. When you're offline and a file isn't in the cache, the request just fails.

The service worker logs each event and request, so keep the browser console open.

---

## License

[MIT](LICENSE.md)
