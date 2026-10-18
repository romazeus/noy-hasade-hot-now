# noy-hasade-hot-now

The list behind the Noy Hasade app's "חמים עכשיו" shelf: the products whose share of orders in the
last 14 days has risen most against the year before.

What is here, and nothing else:

- `current.json`: `{ "v": 1, "generated": "<date>", "file": "lists/<sha256-12>.json" }`, the list in use.
- `lists/<sha256-12>.json`: one list, named by the first 12 hex digits of its own SHA-256 and never
  rewritten: `{ "v": 1, "generated", "window": { "from", "to" }, "ids": [ product ids, ranked ] }`.

Each file holds product ids and dates only: no counts, no prices, no orders, no customers.

A weekly job on the shop's Mac writes it (Sunday 03:30 Israel time). The app fetches `current.json`
and keeps a bundled copy as its fallback; a list more than 21 days old is shown to nobody. The job's
rule, schedule and limits are documented in the app repository, `docs/HOT-NOW.md`.
