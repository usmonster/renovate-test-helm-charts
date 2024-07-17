# 29943

Reproduction for [Renovate discussion #29943](https://github.com/renovatebot/renovate/discussions/29943).

## Current behavior

### Changelog missing from [#20](https://github.com/usmonster/renovate-test-helm-charts/pull/20)

The changelog is missing, even though there are well-formatted GitHub releases for the dependency.

### Changelog points to wrong releases on [#15](https://github.com/usmonster/renovate-test-helm-charts/pull/15)

The changelog links point to older unprefixed releases in the source monorepo which are not related to the actual changes in the proposed chart update.

## Expected behavior

### Changelog should be present in [#20](https://github.com/usmonster/renovate-test-helm-charts/pull/20)

The pull request should include a changelog (similarly to [#14](https://github.com/usmonster/renovate-test-helm-charts/pull/14) & [#19](https://github.com/usmonster/renovate-test-helm-charts/pull/19)) based on the latest GitHub releases here:
https://github.com/usmonster/renovate-test-helm-charts/releases

Otherwise, if Renovate can't successfully fetch the changelog, the scan logs should contain a message explaining why.

### Changelog on [#15](https://github.com/usmonster/renovate-test-helm-charts/pull/15) should point to prefixed releases

The changelog links should point to the corresponding GitHub releases for the specific package in the monorepo:
https://github.com/actions/actions-runner-controller/releases?q=gha-runner-scale-set&expanded=true

_Hypothesis: Renovate may be trying to match releases & tags of the format `<version>` before it searches for the more exact `<depName>-<version>` format common in monorepos, but I would expect the more exact match to take preference._
