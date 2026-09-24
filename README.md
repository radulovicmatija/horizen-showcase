# Horizen — studio site

![Horizen homepage](./screenshot.jpg)

The site for my own studio — [horizen.rs](https://horizen.rs), React 19, TanStack Start, Supabase. Source is private; this documents what's built.

It's also the front door to the CRM: the quote form calls a Postgres function directly with the site's anon key, the same way the CRM's own inquiry flow does (see [horizen-crm-showcase](https://github.com/radulovicmatija/horizen-crm-showcase) for that function).

The CRM and the public site are one codebase and one deploy, but they don't ship together to visitors:

```jsx
const AdminApp = lazy(() => import("../admin/AdminApp"));
```

`/admin` only downloads when someone actually navigates there. A visitor to the marketing site never pulls in CRM code, without needing a separate app or a monorepo split to enforce it.

## What's not great

The intro-pricing toggle is a single hardcoded boolean in the pricing config. There's no way to run two pricing versions at once, or roll one back without a deploy.

---

Matija Radulović
