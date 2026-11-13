# Isolated Cindy CI recovery acceptance

Dedicated test environment; no production source, accounts, credentials or data.

The Actions job installs a lab-only dependency by requesting release metadata
from this repository. Initially the dependency is intentionally not provisioned,
so the real GitHub endpoint returns HTTP 404. Provisioning the dependency outside
the PR repairs that controlled infrastructure condition without changing PR code.
This is disclosed fault injection, not an assertion of a spontaneous CI flake.

The isolated Cindy plugin uses production 1.5.19 main.js byte-for-byte, with a
separate unpublished plugin identity and a manually supplied, Host-managed token.
The token is limited to this repository: Contents read/write, Actions read-only,
Pull requests read-only, Metadata read-only. It must never be stored here or
copied into a tool argument, script, KV, log, screenshot or conversation.

Normal rerun is attempted with that identity. Only a real explicit permission
denial permits considering the original PR Skill's recovery rules. No mock
response, workflow approval, protection bypass or empty commit qualifies.

Keep the evidence and test repository available for review. No production PR,
including makecindy/cindy#10355, is used or changed by this fixture.
