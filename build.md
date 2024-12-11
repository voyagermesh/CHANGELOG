# Build commands

## defaultbackend

```
crane ls registry.k8s.io/defaultbackend-amd64
crane ls registry.k8s.io/defaultbackend-arm64

crane cp registry.k8s.io/defaultbackend-amd64:1.5 ghcr.io/voyagermesh/defaultbackend:1.5-amd64
crane cp registry.k8s.io/defaultbackend-arm64:1.5 ghcr.io/voyagermesh/defaultbackend:1.5-arm64

docker manifest create -a ghcr.io/voyagermesh/defaultbackend:1.5 ghcr.io/voyagermesh/defaultbackend:1.5-amd64 ghcr.io/voyagermesh/defaultbackend:1.5-arm64

docker manifest push ghcr.io/voyagermesh/defaultbackend:1.5
```

## Envoy proxy

```
crane cp ghcr.io/voyagermesh/envoy:v1.31.2-ac ghcr.io/voyagermesh/envoy:v1.31.2-ac-amd64
crane cp shiponcs/envoy-contrib:v1.31.2-arm64 ghcr.io/voyagermesh/envoy:v1.31.2-ac-arm64

docker manifest create -a ghcr.io/voyagermesh/envoy:v1.31.2-ac ghcr.io/voyagermesh/envoy:v1.31.2-ac-amd64 ghcr.io/voyagermesh/envoy:v1.31.2-ac-arm64

docker manifest push ghcr.io/voyagermesh/envoy:v1.31.2-ac
```

## Envoy Gateway

```
IMAGE=ghcr.io/voyagermesh/gateway TAG=v0.6.0 make push-multiarch
```

```
> cd ~/go/src/voyagermesh.dev/installer

> helm package  charts/voyager-gateway
> helm push voyager-gateway-v0.6.0.tgz oci://ghcr.io/appscode-charts
```

```
> helm upgrade -i gateway \
  oci://ghcr.io/appscode-charts/voyager-gateway --version=v0.6.0 \
  -n gateway-system --create-namespace
```

```
crane cp docker.io/shiponcs/envoy-contrib:v1.28.1 ghcr.io/voyagermesh/envoy:v1.28.1
```

**Update crds**

```
# manually update crds
> ./hack/scripts/import-crds.sh ../apimachinery/crds
```

```
ghcr.io/voyagermesh/gateway:v0.6.0
ghcr.io/voyagermesh/envoy:v1.28.1

docker-opc-ecv-group-cicd-nexus.rp-ocn.apps.ocn.infra.ftgroup/voyagermesh/gateway:v0.6.0
docker-opc-ecv-group-cicd-nexus.rp-ocn.apps.ocn.infra.ftgroup/voyagermesh/envoy:v1.28.1

docker-opc-ecv-group-cicd-nexus.rp-ocn.apps.ocn.infra.ftgroup/kubebuilder/kube-rbac-proxy:v0.11.0

```
