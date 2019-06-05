## Kustomize stack deployment for frictionless canary spin-up


1. Clone the repo and `cd` into the cloned repo folder.

1. If the base Kustomize layer already exists, link its parent folder to the repo folder using `ln -s /path/to/base/layer/folder/ base`.

1. If the base Kustomize layer does not exist, link folder `from_current_deployment` to folder `base` with `ln -s from_current_deployment/ base` and then run `kubectl get deployment/DEPLOYMENT_NAME -o yaml > base/deployment.yaml`.

1. Generate final canary deployment with `kustomize build . > opsani-canary.yaml`.

1. Submit resulting deployment using `kubectl apply -f opsani-canary.yaml`.
