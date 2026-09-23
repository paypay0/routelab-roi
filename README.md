# RouteLab ROI

Backup-channel routing ROI simulator for payment operations.

## What it does

RouteLab helps evaluate whether adding a backup PSP / payment channel is worth it by modeling:

- blended payment success rate
- incremental routing cost
- incremental successful transactions
- cost per incremental success
- contribution-margin ROI
- target success-rate backsolving
- routing allocation under budget and traffic constraints
- minimum backup-channel PSR required to hit a target

The current model is **Direct Routing**. It does not include failover retry.

## Demo assumptions

Default example:

- Volume: 100,000 requests
- Channel A cost: R$0.01 / request
- Channel A PSR: 50%
- Channel B cost: R$0.03 / request
- Channel B PSR: 55%
- Channel B allocation: 20%
- Fixed integration cost: R$0

Expected output:

- Total cost: R$1,400
- Incremental cost: R$400
- Blended PSR: 51%
- PSR lift: +1 pp
- Incremental successes: +1,000
- Cost per incremental success: R$0.40

## Run locally

This project is intentionally dependency-free.

Open `index.html` directly in a browser, or serve the folder with any static HTTP server.

## GitHub Pages

Deployment is handled by `.github/workflows/pages.yml`.

The expected public URL is:

https://paypay0.github.io/routelab-roi/

## Model assumptions

1. Direct routing only; no failover retry.
2. Channel PSR is assumed constant as allocation changes.
3. Request-based pricing.
4. Fixed integration cost belongs to the selected evaluation period.
5. Contribution means incremental contribution profit per newly successful transaction.
6. Capacity degradation and issuer mix shifts are not modeled.

## Security

No API keys, tokens, credentials, or backend secrets are required.
