# GCP Terraform Compute (Simple Web Server)

This configuration creates a minimal VPC + subnetwork, firewall rules for HTTP/SSH, and a single Compute Engine VM running nginx that serves a custom landing page.

## Layout
- `main.tf` wires the network and compute modules.
- `variables.tf` / `terraform.tfvars` hold inputs (project/region/zone, network/compute settings, page text).
- `outputs.tf` exposes network links and the VM external IP.
- `modules/network` defines the VPC, subnet, and firewall rule.
- `modules/compute` defines the VM and nginx startup script.



## Prerequisites
- Terraform >= 1.0
- Google Cloud project with billing enabled
- Application Default Credentials or other auth usable by the Google provider
- Existing GCS bucket for the remote backend (see `versions.tf`)

## Usage
```bash
terraform init          # configure backend and providers
terraform plan          # review resources
terraform apply         # create the web server
```

After apply, visit the `instance_external_ip` output on port 80 to see the nginx page with your `startup_page_text`.



