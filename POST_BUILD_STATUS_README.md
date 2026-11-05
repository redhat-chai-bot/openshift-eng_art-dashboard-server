# post-build-status branch

This branch bundles the complete **post-build** support for both ART build
dashboards so every post-build change is present in one place:

- **build-history dashboard** — at the repository root (this is the
  `art-build-history` dashboard). Adds the post-build pipeline URL/status to
  the build-history API (`app.py`) and renders the post-build status button in
  `build → post-build → ITS → release` order (`static/js/index.js`), omitting
  it when the image did not configure a post-build step.
- **build-failures dashboard** — under `art-build-failures/` (the
  `art-build-failures` dashboard). Adds the `post-build-failure` failure type to
  the failure-type enumeration/queries (`art-build-failures/app.py`,
  `mock_data.py`) and to the failures view (selector, badge, colour, legend in
  `art-build-failures/static/js/failures.js` and `static/css/failures.css`).

Both dashboards are self-contained Flask apps that normally live on their own
branches of `openshift-eng/art-dashboard-ui` (`art-build-history` and
`art-build-failures`). Clean, per-dashboard branches for review/PR are also
available: `post-build-status` (build-history only, root) history and
`post-build-status-failures` (build-failures only) on the
`redhat-chai-bot/art-dashboard-ui` fork.
