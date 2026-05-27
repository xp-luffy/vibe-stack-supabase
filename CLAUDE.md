# Project conventions

## Stack
- **Next.js 15** App Router, React 19, TypeScript strict
- **Tailwind v4** — CSS-first config in `app/globals.css` (no `tailwind.config.ts`)
- **Supabase** via `@supabase/ssr` (cookie-based sessions)
- **Bun** package manager

## Supabase client patterns
| Context | Import from |
|---|---|
| Client component | `lib/supabase/client.ts` |
| Server component / Route handler / Server action | `lib/supabase/server.ts` |
| Middleware | `lib/supabase/middleware.ts` |

- **Never** expose `SUPABASE_SERVICE_ROLE_KEY` to the browser
- **Never** use deprecated `@supabase/auth-helpers-nextjs`
- Server components are default — add `"use client"` only when needed
- Use Server Actions for mutations (prefer over `/api` routes)

## Path aliases
`@/*` → repo root

## gstack workflow
This repo uses [gstack](https://github.com/garrytan/gstack):
- **Plan:** `/office-hours` → `/autoplan`
- **Review:** `/review` before merging
- **Ship:** `/ship` (bumps version, opens PR)
- **Deploy:** `/land-and-deploy` after PR merge
- **QA:** `/qa <preview-url>` on every deploy
- **Security audit:** `/cso` before going public
