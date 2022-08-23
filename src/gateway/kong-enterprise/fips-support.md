---
title: FIPS 140-2
badge: enterprise
---

With version 3.0.0.0, {{site.base_gateway}} provides support for the Federal Information Processing Standard (FIPS 140-2). Compliance with this standard is typically required for working with U.S. federal government agencies and their contractors.

{{site.base_gateway}} FIPS support is achieved by shipping a package in which Kong links against a BoringSSL version whose core library BoringCrypto has been FIPS validated and providing a mode in which incompatible ciphers are disabled. However, Kong as a whole is not FIPS validated.

## Getting Started

Currently, the only supported {{site.base_gateway}} distribution is based on Ubuntu 20.04 and can be installed with the usual steps for the Ubuntu distribution. The package is distinctively named `kong-enterprise-edition-fips`; this way, instead of `apt install kong-enterprise-edition`, one needs to run `apt install kong-enterprise-edition-fips`.

### Configuration Reference

Once the FIPS package is installed, the following directive needs to be set to start {{site.base_gateway}} in FIPS mode:

```
fips = on # fips mode is enabled, causing incompatible ciphers to be disabled
```

or via the equivalent environment variable:

```bash
export KONG_FIPS=on
```

{:.important .no-icon}
> FIPS mode is only supported in Ubuntu 20.04

{:.important .no-icon}
> Migrating from non-FIPS to FIPS mode requires manually resetting RBAC
tokens at this time. We plan to facilitate this migration in the future.
