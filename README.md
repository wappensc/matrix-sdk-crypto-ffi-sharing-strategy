# matrix-sdk-crypto-ffi: choose the room-key sharing strategy

A small patch to matrix-rust-sdk's `bindings/matrix-sdk-crypto-ffi` that adds an optional
`sharing_strategy` field to `EncryptionSettings`. With it, a client of the crypto FFI can choose
`CollectStrategy::IdentityBasedStrategy` — room keys only for devices their owner's identity has
signed (MSC4153). Without it, the FFI offers only `only_allow_trusted_devices` and
`error_on_verified_user_problem`, which select the other strategies.

- Made against the tag `matrix-sdk-0.19.1`. On 2026-10-20, upstream `main` had no such field yet.
- Backwards compatible: the field defaults to `None`, and the existing flags then decide as before.

## Apply

    git clone --depth 1 --branch matrix-sdk-0.19.1 https://github.com/matrix-org/matrix-rust-sdk
    cd matrix-rust-sdk
    git apply /path/to/matrix-sdk-crypto-ffi-sharing-strategy.patch

Then build `matrix-sdk-crypto-ffi` as usual.

## Why this is not a pull request upstream

We develop with AI — this patch was written by an AI agent (Anthropic's Claude) under our review.
matrix-rust-sdk's contribution guidelines (AI policy, items 4 and 6) do not accept contributions made
in an agent mode, nor pull request or issue text written with AI. So we publish the patch here
instead of submitting it. If the change is wanted upstream, it is best written there anew under the
project's own rules; this patch shows one way to do it.

## Status

Unmaintained: a patch for one tagged release, published as is. No issues, no pull requests, no
updates are planned.

## License

The patch changes matrix-rust-sdk, which is licensed under the Apache License 2.0, and is offered
under the same license (see LICENSE). Changed file: `bindings/matrix-sdk-crypto-ffi/src/lib.rs`.
