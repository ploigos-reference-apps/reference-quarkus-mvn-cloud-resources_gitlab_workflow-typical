# reference-quarkus-mvn-cloud-resources (GitLab) (Workflow: Typical)
The cloud resources for the [reference-quarkus-mvn](https://github.com/ploigos-reference-apps/reference-quarkus-mvn)
application when using GitLab and the Typical workflow.

## Install

### 0. Prerequisite

* TODO

### 1. Deploy Ploigos Kubernetes Resources

```bash
# this should be the namespace that GitLab is running in
WORKFLOW_NAMESPACE=
helm dependency update charts/reference-quarkus-mvn-workflow

helm secrets upgrade --install \
    reference-quarkus-mvn-workflow-typ ./charts/reference-quarkus-mvn-workflow \
    -f charts/reference-quarkus-mvn-workflow/values.yaml \
    -f charts/reference-quarkus-mvn-workflow/secrets.yaml \
    --namespace ${WORKFLOW_NAMESPACE} \
    --render-subchart-notes
```

### 2. Update .gitlab-ci.yml

1. The helm chart run will have output `PGP Keys Secret: ${PGP_KEYS_SECRET}`, you need to update
the `pgpKeysSecretName` parameter in the .gitlab-ci.yml in the associated project to this one
with that value.
2. TODO

### 2. Configure GitLab

1. TODO
