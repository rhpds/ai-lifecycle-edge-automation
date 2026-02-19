# ocp4_workload_microshift

Deploy a MicroShift instance inside a KubeVirt virtual machine on OpenShift.

The role creates a namespace, provisions a KubeVirt VM from a pre-built RHEL + MicroShift QCOW2 image,
exposes the VM via OpenShift routes (API and ingress), and copies the MicroShift kubeconfig to the bastion
for CLI access.

## Usage

```yaml
workloads:
- <collection>.ocp4_workload_microshift
```

Set `ocp4_workload_microshift_vm_image` to point to your QCOW2 image. If the image is in a private S3 bucket,
also set `ocp4_workload_microshift_s3_access_key`, `ocp4_workload_microshift_s3_secret_key`, and
`ocp4_workload_microshift_s3_region`.

All configurable variables are documented in `defaults/main.yml`.

## Requirements

- OpenShift Virtualization (KubeVirt) must be installed on the cluster
- The `virtctl` CLI must be available on the bastion
- The `community.crypto` Ansible collection (for SSH key generation)
