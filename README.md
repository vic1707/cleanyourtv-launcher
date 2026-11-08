# Clean Your TV launcher builds

Unmodified APK builds of the [Clean Your TV](https://github.com/Gathin23/cleanyourtv)
launcher (`launcher/`, MIT), which upstream publishes as source only.

Renovate bumps `CLEANYOURTV_VERSION` in `.github/workflows/build.yml` when
upstream tags a release; the merged bump builds that tag, signs it with this
repository's key, attests its build provenance and publishes it as a release
of the same version. A version that is already released is not rebuilt.

Every release is signed with the same key, so an update installs over the
previous one. It is not upstream's key: an APK from here does not update a
launcher built from source, and the reverse (uninstall first).

## Verify

```sh
gh attestation verify cleanyourtv-launcher-<version>.apk --repo vic1707/cleanyourtv-launcher
apksigner verify --print-certs cleanyourtv-launcher-<version>.apk
```
