# React Real Estate UI Design

A real estate UI built with React 19 and Vite 8.

## Requirements

- Node.js 20.19+ / 22.12+ / 24+ (Vite 8 requirement). `node -v` to check.
- npm 10+ (ships with the Node versions above).

If you use [nvm](https://github.com/nvm-sh/nvm):

```bash
nvm install --lts
nvm use --lts
```

## Setup

```bash
git clone https://github.com/thelinos/react-estate-ui.git
cd react-estate-ui
npm install
```

## Running

```bash
npm run dev       # dev server with HMR on http://localhost:5173
npm run build     # production build into dist/
npm run preview   # serve the production build locally
npm run lint      # ESLint (flat config, fails on any warning)
```

To expose the dev server on your network (e.g. to test from another device):

```bash
npm run dev -- --host 0.0.0.0 --port 5173
```

## Project structure

```
index.html          Vite entry HTML
vite.config.js      Vite + @vitejs/plugin-react config
eslint.config.js    ESLint flat config
public/             Static assets served at /
src/main.jsx        React entry point
src/App.jsx         Root component
src/index.css       Global styles
```

## Upgrading dependencies

1. See what is outdated:

   ```bash
   npm outdated
   ```

2. Upgrade within the current semver ranges (safe, patch/minor only):

   ```bash
   npm update
   ```

3. Upgrade across major versions. Either bump the ranges in `package.json` by
   hand and re-run `npm install`, or install explicit versions:

   ```bash
   npm install react@latest react-dom@latest
   npm install -D vite@latest @vitejs/plugin-react@latest eslint@latest \
     @eslint/js@latest eslint-plugin-react@latest \
     eslint-plugin-react-hooks@latest eslint-plugin-react-refresh@latest \
     @types/react@latest @types/react-dom@latest globals@latest
   ```

   Peer-dependency conflicts (`ERESOLVE`) mean one of the plugins does not
   support that major yet — pin that dependency to the newest version it does
   support instead of forcing the install with `--force`/`--legacy-peer-deps`.
   For example, `eslint-plugin-react` currently caps ESLint at 9.x, so ESLint
   stays on 9 until the plugin supports 10.

4. Fix advisories:

   ```bash
   npm audit
   npm audit fix
   ```

5. Verify after every upgrade:

   ```bash
   npm run lint && npm run build && npm run dev
   ```

6. Commit both `package.json` and `package-lock.json`.

### Notes on major upgrades

- **React 18 → 19**: `react` and `react-dom` must be upgraded together, along
  with `@types/react` and `@types/react-dom`.
- **Vite 5 → 8**: requires a modern Node version (see Requirements) and
  `@vitejs/plugin-react` 6+.
- **ESLint 8 → 9**: uses flat config. `.eslintrc.cjs` was replaced by
  `eslint.config.js`, and the `--ext` flag is gone from the `lint` script
  (file globs are configured via `files` inside the config).
