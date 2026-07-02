# platform-xp-example-resources

Example claims for testing and validating the `urukube` platform XRD packages.
Each folder maps to one XRD package repo.

| Folder | XRD package | Claim kind |
|---|---|---|
| `s3/` | `platform-xp-s3` | `US3Bucket` |
| `networking/` | `platform-xp-networking` | `UNetwork` |
| `eks/` | `platform-xp-eks` | `UEks` |

## Usage

Apply a claim directly to the orchestrator cluster:

```bash
kubectl apply -f s3/claim-test-s3.yaml
```

Watch it reconcile:

```bash
kubectl get managed -l crossplane.io/claim-name=<claim-name>
```

## Folder structure

```
platform-xp-example-resources/
├── s3/
│   └── claim-test-s3.yaml             # US3Bucket — basic bucket in BU001 account
├── networking/
│   ├── claim-network-dev.yaml         # UNetwork — dev VPC (single NAT GW, 2 AZs, auto-CIDRs)
│   └── claim-network-prod.yaml        # UNetwork — prod VPC (per-AZ NAT GWs, 3 AZs, auto-CIDRs)
└── eks/
    ├── claim-eks-dev.yaml             # UEks — dev cluster (public endpoint, t3.medium)
    └── claim-eks-prod.yaml            # UEks — prod cluster (private endpoint, m5.large, 3 AZs)
```
