# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

@AGENTS.md

## Project

Arcade Vault is an online platform for playing games and competing for the highest score. The project follows **Spec Driven Design** using the `/spec` and `/spec-impl` skills from [Klerith/fernando-skills](https://github.com/Klerith/fernando-skills) (install with `npx skills@latest add Klerith/fernando-skills`). New features should go through a spec first, then be implemented from that spec.

The codebase is currently a fresh `create-next-app` scaffold. `app/page.tsx` and the metadata in `app/layout.tsx` are still placeholders.

## Commands

```bash
npm run dev     # start dev server (also regenerates the AGENTS.md block)
npm run build   # production build (includes type checking)
npm run start   # serve the production build
npm run lint    # ESLint 9 flat config (next core-web-vitals + typescript)
```

No test runner is configured yet.

## Stack and conventions

- **Next.js 16.3 (App Router) + React 19.2**. APIs differ from older Next.js versions. Before writing Next.js code, check the bundled docs in `node_modules/next/dist/docs/` (`01-app/`, `03-architecture/`, …).
- Route props use the global generated types, e.g. `LayoutProps<"/">` / `PageProps<"/route">`, instead of hand-written prop interfaces. They are generated into `.next/types`, so run `dev` or `build` first if they are missing.
- **Tailwind CSS v4** via `@tailwindcss/postcss`. There is no `tailwind.config.*`: theme tokens live in `app/globals.css` under `@theme inline`, mapped from CSS variables (`--background`, `--foreground`, Geist font vars). Dark mode uses `prefers-color-scheme`.
- TypeScript strict mode; the import alias `@/*` maps to the repo root.
