# renovatebot/renovate#14137 reproduction

The repository have a `kustomization.yaml` file with a nginx-ingress helm chart dependency using the helm chart generator (https://github.com/kubernetes-sigs/kustomize/blob/master/examples/chart.md).

The `kustomization.yaml` specifies the version of the nginx-ingress helm chart to `0.11.0` with the latest available version being `0.12.0`.

## Current behavior

Renovate creates the following [pull request](https://github.com/pnordh/renovate-14137-reproduction/pull/1) where it has resolved an upgrade to the nginx-ingress helm chart and updates the `kustomization.yaml` file but it doesn't upgrade the vendored chart.

## Expected behavior

In order for the PR to not require human manipulation Renovate should be able to determine that the chart dependency is vendored and requires to be replaced by the updated chart.

See https://github.com/kubernetes-sigs/kustomize/blob/master/examples/chart.md for information on how kustomize pulls helm charts.
