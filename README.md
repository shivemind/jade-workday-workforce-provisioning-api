# Workday Workforce Provisioning API

Jade Global — **workforce-management** domain (WM)

## OpenAPI Spec

The canonical spec lives at [`openapi/workday-workforce-provisioning-api.yaml`](openapi/workday-workforce-provisioning-api.yaml).

## Postman Pipeline

On push to `main` (or manual dispatch), the GitHub Actions workflow:

1. **Bootstrap** — creates/refreshes a Postman workspace, uploads the spec to Spec Hub,
   and generates baseline, smoke, and contract collections from the spec.
2. **Repo Sync** — creates prod/stage environments, links the workspace to this repo,
   exports artifacts, and associates system environments for the API Catalog.
3. **Insights Onboarding** — links the Insights Agent's discovered service to the
   workspace so the API Catalog service graph populates from live traffic.

## Mock Service

A lightweight Node.js service (`k8s/mock-service/server.js`) that propagates
W3C `traceparent` headers and calls configurable downstream services. Used for
local Kubernetes traffic generation.

```bash
docker build -t jade-workday-workforce-provisioning-api:latest k8s/mock-service/
```
