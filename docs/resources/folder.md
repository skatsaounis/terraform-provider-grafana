---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "grafana_folder Resource - terraform-provider-grafana"
subcategory: "Grafana OSS"
description: |-
  Official documentation https://grafana.com/docs/grafana/latest/dashboards/manage-dashboards/HTTP API https://grafana.com/docs/grafana/latest/developers/http_api/folder/
---

# grafana_folder (Resource)

* [Official documentation](https://grafana.com/docs/grafana/latest/dashboards/manage-dashboards/)
* [HTTP API](https://grafana.com/docs/grafana/latest/developers/http_api/folder/)

## Example Usage

```terraform
resource "grafana_folder" "test_folder" {
  title = "Terraform Test Folder"
}

resource "grafana_dashboard" "test_folder" {
  folder      = grafana_folder.test_folder.id
  config_json = <<EOD
{
  "title": "Dashboard in folder",
  "uid": "dashboard-in-folder"
}
EOD
}

resource "grafana_folder" "test_folder_with_uid" {
  uid   = "test-folder-uid"
  title = "Terraform Test Folder With UID"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `title` (String) The title of the folder.

### Optional

- `prevent_destroy_if_not_empty` (Boolean) Prevent deletion of the folder if it is not empty (contains dashboards or alert rules). Defaults to `false`.
- `uid` (String) Unique identifier.

### Read-Only

- `id` (String) Unique internal identifier.
- `url` (String) The full URL of the folder.

## Import

Import is supported using the following syntax:

```shell
terraform import grafana_folder.by_integer_id {{folder_id}}
terraform import grafana_folder.by_uid {{folder_uid}}
```
