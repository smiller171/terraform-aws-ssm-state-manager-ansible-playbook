# terraform-aws-ssm-state-manager-ansible-playbook
Template repository for terraform modules. Good for any cloud and any provider.

[![tflint](https://github.com/rhythmictech/terraform-aws-ssm-state-manager-ansible-playbook/workflows/tflint/badge.svg?branch=master&event=push)](https://github.com/rhythmictech/terraform-aws-ssm-state-manager-ansible-playbook/actions?query=workflow%3Atflint+event%3Apush+branch%3Amaster)
[![tfsec](https://github.com/rhythmictech/terraform-aws-ssm-state-manager-ansible-playbook/workflows/tfsec/badge.svg?branch=master&event=push)](https://github.com/rhythmictech/terraform-aws-ssm-state-manager-ansible-playbook/actions?query=workflow%3Atfsec+event%3Apush+branch%3Amaster)
[![yamllint](https://github.com/rhythmictech/terraform-aws-ssm-state-manager-ansible-playbook/workflows/yamllint/badge.svg?branch=master&event=push)](https://github.com/rhythmictech/terraform-aws-ssm-state-manager-ansible-playbook/actions?query=workflow%3Ayamllint+event%3Apush+branch%3Amaster)
[![misspell](https://github.com/rhythmictech/terraform-aws-ssm-state-manager-ansible-playbook/workflows/misspell/badge.svg?branch=master&event=push)](https://github.com/rhythmictech/terraform-aws-ssm-state-manager-ansible-playbook/actions?query=workflow%3Amisspell+event%3Apush+branch%3Amaster)
[![pre-commit-check](https://github.com/rhythmictech/terraform-aws-ssm-state-manager-ansible-playbook/workflows/pre-commit-check/badge.svg?branch=master&event=push)](https://github.com/rhythmictech/terraform-aws-ssm-state-manager-ansible-playbook/actions?query=workflow%3Apre-commit-check+event%3Apush+branch%3Amaster)
<a href="https://twitter.com/intent/follow?screen_name=RhythmicTech"><img src="https://img.shields.io/twitter/follow/RhythmicTech?style=social&logo=twitter" alt="follow on Twitter"></a>

## Example
Here's what using the module will look like
```hcl
module "example" {
  source = "rhythmictech/terraform-mycloud-mymodule
}
```

## About
A bit about this module

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.13.5 |
| aws | >= 3.0.0 |

## Providers

| Name | Version |
|------|---------|
| aws | >= 3.0.0 |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| name | Moniker to apply to all resources in the module | `string` | n/a | yes |
| target\_tag\_key | The AWS Tag key that you want to target for running the playbook | `string` | n/a | yes |
| ansible\_check\_mode | Whether or not the playbook should run in `check` mode | `bool` | `false` | no |
| ansible\_extra\_vars | A list of KEY=VALUE strings defining extra vars to pass to Ansible | `list(string)` | `[]` | no |
| ansible\_verbosity | How verbose do you want the Ansible output to be? Valid values are `default`, `more`, and `debug` | `string` | `"default"` | no |
| compliance\_severity | The compliance severity of this State Manager association. Allowed values are `UNSPECIFIED`, `LOW`, `MEDIUM`, or `CRITICAL` | `string` | `"UNSPECIFIED"` | no |
| log\_bucket\_name | Name of existing bucket to use for logging | `string` | `null` | no |
| max\_concurrency | The maximum number of targets allowed to run the association at the same time. You can specify a number, for example 10, or a percentage of the target set, for example 10%. | `string` | `null` | no |
| max\_errors | The number of errors that are allowed before the system stops sending requests to run the association on additional targets. You can specify a number, for example 10, or a percentage of the target set, for example 10%. | `string` | `null` | no |
| playbook\_file\_name | Name of the playbook file | `string` | `"provision.yml"` | no |
| s3\_log\_prefix | Path prefix where logs will be stored in S3 | `string` | `"logs/state_manager"` | no |
| schedule\_expression | A 6-field cron expression when the association will be applied to the target(s) | `string` | `null` | no |
| tags | User-Defined tags | `map(string)` | `{}` | no |
| target\_tag\_value | The AWS Tag value that you want to target for running the playbook. If omitted any instance with the key will be targetted regardless of value | `string` | `null` | no |

## Outputs

No output.

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## Getting Started
This workflow has a few prerequisites which are installed through the `./bin/install-x.sh` scripts and are linked below. The install script will also work on your local machine. 

- [pre-commit](https://pre-commit.com)
- [terraform](https://terraform.io)
- [tfenv](https://github.com/tfutils/tfenv)
- [terraform-docs](https://github.com/segmentio/terraform-docs)
- [tfsec](https://github.com/tfsec/tfsec)
- [tflint](https://github.com/terraform-linters/tflint)

We use `tfenv` to manage `terraform` versions, so the version is defined in the `versions.tf` and `tfenv` installs the latest compliant version.
`pre-commit` is like a package manager for scripts that integrate with git hooks. We use them to run the rest of the tools before apply. 
`terraform-docs` creates the beautiful docs (above),  `tfsec` scans for security no-nos, `tflint` scans for best practices. 
