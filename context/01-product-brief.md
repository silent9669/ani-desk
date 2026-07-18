# Product brief

## Audience

ani-web is the hosted, responsive edition of ani-desk for one family: approximately 5–10 named users on macOS, iPhone, iPad, and ordinary web browsers. It is a private media client, not a public streaming platform or multi-tenant SaaS product.

## Required user journeys

- Sign in with an administrator-created account; no public registration.
- Discover trending anime from AniList without spending provider request capacity.
- Select a language and provider, search that provider's catalog, inspect a title, choose an episode, and play it.
- Keep the search query while switching provider or language.
- Maintain per-user My List and Continue Watching state.
- Resume playback and persist progress across browsers for the same account.
- Download an episode through the browser where the provider permits it.
- Use the interface comfortably on a 16-inch Mac and current iPhone widths.
- Let an administrator create, disable, update, and delete family accounts.

## Product rules

- Provider choice is explicit. Each provider queries a different catalog and results must identify their source.
- AniList is metadata/discovery only. It must never be treated as proof that an episode is playable.
- The hero rail uses AniList trending titles. Selecting `Watch now` carries the title into provider search; it does not invent an episode mapping.
- Search, details, episode selection, playback, progress, favorites, and downloads must remain end-to-end coherent for every enabled provider.
- English and Vietnamese are separate catalog groups and require separate acceptance tests.
- Provider failure is a normal degraded state. The UI explains unavailable, blocked, verification-required, or retryable states.

## Quality attributes

Priority order:

1. Private and safe for family use.
2. Reliable playback and clear provider failures.
3. Simple command-line deployment, backup, rollback, and monitoring.
4. Responsive, accessible interaction across desktop and mobile.
5. Low maintenance and low homelab resource use.
6. Easy addition or repair of providers without rewriting the web service.

## Non-goals

- Public self-registration, social login, billing, subscriptions, or public sharing.
- Kubernetes, service mesh, event streaming, or independent microservices.
- Transcoding or permanently mirroring third-party video in the first release.
- A universal merged search ranking that hides the chosen provider.
- Native iOS distribution as a prerequisite; responsive/PWA behavior comes first.

## Capacity assumption

Design for 5–10 accounts, normally 1–3 simultaneous playback sessions, and a single homelab node. Media proxy bandwidth—not API or database compute—is the likely bottleneck. Capacity tests should therefore include concurrent HLS playback and WAN upload/download measurements.
