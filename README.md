# AWS Load Balancer controller Kubernetes system service for Wodby

AWS Load Balancer Controller connects Kubernetes Services and ingress resources
to AWS Elastic Load Balancing for Wodby-managed clusters.

This repository defines the Wodby service manifests and operational
configuration for AWS Load Balancer controller.

- [Wodby Kubernetes platform](https://wodby.com)
- [Wodby service documentation](https://wodby.com/docs/2.0/services/)
- [Service manifest reference](https://wodby.com/docs/2.0/services/template/)

## Wodby system stacks using this service

- [AWS Load Balancer controller system stack](https://github.com/wodby/stack-aws-lb-controller)

## Service overview

| Property | Manifest configuration |
| --- | --- |
| Service name | `aws-lb-controller` |
| Type | Infrastructure service |
| Workloads | `main` (Deployment), primary; fixed replica count |
| Containers | `aws-load-balancer-controller` |
| Helm | chart `eks/aws-load-balancer-controller`; version `1.9.0` |
| Configuration | 1 certificates |

## Role in Wodby infrastructure

Wodby installs this service through a Kubernetes system stack when it is
required by the cluster provider or selected infrastructure configuration. It
runs as a cluster-owned system app and is not offered as a user-deployable
application service.

## Platform maintenance

Changes to this repository can affect cluster provisioning, upgrades,
networking, or observability. Coordinate manifest and Helm changes with every
dependent system stack and preserve service, workload, endpoint, config, and
volume identifiers.

Wodby platform maintainers can validate the manifests with:

```bash
wodby service validate-manifest service.yml --org <org-id>
```

See the [service manifest reference](https://wodby.com/docs/2.0/services/template/) and the [managed services index](https://github.com/wodby/services).
