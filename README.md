# Tanzu App Accelerators Importer

## Application Accelerator List Repo Reconciler

## Problem Description
Tanzu application accelerator CRD are explicitly added to a tanzu cluster using kubectl. Create privileges are thus required in the accelerator-system namespace. While future updates to created accelerators need only have commits made to the underlying git repos where they're stored, the addition of new accelerators requires this elevated permission on the cluster.

## Solution
Deploy a kapp that instructs the kapp-controller to ensure all accelerators defined in a given git-repo will be deployed automatically to the TAP cluster.

Now when new accelerators are to be added to the cluster, the only requirement is that their definitions files are checked into this repo.


## Usage
Fork this repo and update your accelerators-list.yaml to refer to your fork.

Use kapp to continuously deploy reconciling this accelerator repo.

Place any desired application accelerator definitions in the _accelerators_ subfolder

``` 
kapp deploy -a accelerators-list -f ./accelerators-list.yaml
```


