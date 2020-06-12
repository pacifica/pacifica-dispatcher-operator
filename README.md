# Pacifica Dispatcher Operator

This repository contains an
[Ansible Kubernetes Operator](https://sdk.operatorframework.io/docs/ansible/quickstart/)
to manage Pacifica
[Dispatchers](https://github.com/pacifica/pacifica-dispatcher-k8s).
The process for building a custom Dispatcher is handled in the
Dispatcher repository. The deployment options for a custom resource
is managed here.

## Kubernetes Required Resources

There are some required resources needed to deploy a dispatcher.

 * Shared Persistent Volume Claim
   * The persistent volume behind the claim must be able to support the data the dispatcher will work on.
 * Notification Subscription Secret
   * The secret is of a specific format but has hooks to let you provide a custom format.

## Custom Resource Variables

| Variable Name | Type   | Description                               |
| ------------- | ------ | ----------------------------------------- |
| size          | int    | Number of dispatchers to deploy.          |
| env           | list   | Environment variables array.              |
| secret_name   | string | Name of the notify subscription secret    |
| shared_pvc    | string | Name of the Shared PVC                    |
| image         | string | Container image to use                    |
| wait_services | list   | Strings of services to wait for (init)    |
| subscription  | object | The notifications posted object           |
