A guide how to install xwiki with PostgerSQL on Kubernetes.

Images Used:
- Latest official "xwiki:stable-postgres-tomcat" image
- Latest official "postgres" image.

"xwiki_manifests" folder:
Manifest files in this folder will create:
- A single-pod xwiki Deployment
- NodePort service for xwiki deployment(set to be exposed on port 30001)
- A StatefulSet of single pod of PosgreSQL database.
- a ClusterIP service for PostgreSQL database StatefulSet.

How to deploy?
- Using git & Kubectl commands:
  - git clone https://github.com/yakovdonde/xwiki.git && kubectl apply -f xwiki/xwiki_manifests/*.yaml

"xwiki_manifests_with_pv_and_pvc" folder:

Manifest files in this folder will create:
- A single-pod xwiki Deployment
- Persistent volume (pv) for xwiki deployment
- Persistent volume claim (pvc) for xwiki deployment
- NodePort service for xwiki deployment(set to be exposed on port 30001)
- A StatefulSet of single pod of PosgreSQL database.
- Persistent volume (pv) for PostgreSQL StatefulSet.
- Persistent volume claim (pvc) for PostgreSQL StatefulSet.
- a ClusterIP service for PostgreSQL database StatefulSet.

Prerequisites:
- Create a directory for xwiki Persistent volume on the host. (e.g. mkdir xwiki-pv)
- Create a directory for PostgreSQL Persistent volume on the host. (e.g. mkdir postgres-pv)
- Clone this repo:
  - git clone https://github.com/yakovdonde/xwiki.git
- Adjust the directory you created in "xwiki-pv.yaml" file (e.g. path: "YOUR PHYSICAL DIRECTORY" --> path: ~/xwiki-pv)
- Adjust the directory you created in "xwiki-postgres-pv.yaml" file (e.g. path: "YOUR PHYSICAL DIRECTORY" --> path: ~/postgres-pv)

How to deploy:
- kubectl apply -f xwiki/xwiki_manifests/*.yaml