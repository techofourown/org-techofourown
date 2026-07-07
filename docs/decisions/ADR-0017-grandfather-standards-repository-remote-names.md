# ADR-0017: Grandfather Standards Repository Remote Names


## Context

ADR-0002 and ADR-0003 require typed, lowercase, hyphen-separated
repository names. Standards repositories normally use the `std-` prefix.

The current standards publication work uses existing Git remotes whose
repository names predate that convention or were created outside it:

- `protean_computing`
- `protean_organization`
- `protean_companions`
- `tooo-std-register`
- `conformance-artifacts`

The first three names use underscores and lack an approved typed prefix.
The register name is lowercase and hyphen-separated but uses `tooo-` as
the leading token rather than an approved repository type prefix.
`conformance-artifacts` is lowercase and hyphen-separated but lacks the
`std-` or `tool-` typed prefix expected for standards-family artifact
repositories.
Renaming these repositories is externally stateful because it affects
remote URLs, automation, clones, CI configuration, documentation links,
and cross-repository references.

## Decision

The five current standards remotes listed above are grandfathered as
legacy exceptions to ADR-0002 and ADR-0003. They may continue to be used
as authoritative remotes until a rename or mirror migration is scheduled
and completed.

This exception does not make the legacy names conforming examples. New
standards repositories shall use the `std-` prefix and lower-hyphen
tokens. When these four repositories are renamed or mirrored for public
consumption, the preferred target shape is:

- `std-protean-computing`
- `std-protean-organization`
- `std-protean-companions`
- `std-tooo-register`
- `std-conformance-artifacts`

Any public conformance or repository-hygiene review may cite this ADR as
the explicit exception record for the current remote names, but shall not
treat the legacy names as satisfying the normal naming rule.

## Rationale

The standards work is already coupled to the current remotes. A forced
rename during active publication work would create avoidable operational
risk without changing the standards content.

Recording a narrow exception preserves the naming law for future
repositories while making the current state reviewable. It also gives a
clear migration target for later cleanup.

## Consequences

### Positive

- Repository hygiene reviews have an explicit governance record for the
  current standards remotes.
- Existing clones, automation, and references keep working during active
  standards publication work.
- Future standards repositories still follow the `std-` typed-prefix
  rule.

### Negative

- Repository lists will continue to contain nonconforming legacy names
  until migration.
- Documentation and automation may need to recognize both legacy and
  target names during any mirror or rename transition.

### Mitigation

- Treat the listed names as a closed exception set.
- Prefer `std-*` names for any new standards repositories immediately.
- When a rename or mirror is scheduled, document redirects and update
  automation, manifests, and public links in the same change window.

## References

- [ADR-0002: Adopt Typed Prefix Repository Naming Convention](./ADR-0002-adopt-typed-prefix-repo-names.md)
- [ADR-0003: Standardize Naming Across Artifacts Using Typed Prefixes and Stable Identifiers](./ADR-0003-standardize-naming-across-artifacts.md)
