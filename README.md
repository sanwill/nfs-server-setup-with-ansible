# NFS Server setup on Fedora with Ansible Playbook
The idea is to automate the NFS server setup on Fedora.

## Requirements:
* OS: Fedora (or Fedora based distro)
* Ansible is setup at installation server or locally at NFS server
* Have superuser right
* The [playbook](https://github.com/sanwill/nfs-server-setup-with-ansible/blob/main/configure_nfs_fedora_generic.yaml)

## Few Notes:
* Update the yaml files with your local configuration. Look for ```#Note:``` it gives hints on which values need to be updated on certain task.
* Here I use expansion disk (e.g. sdb) for the NFS storage, different from the primary disk where the OS is located.
* The playbook only automate the mount of 1 expansion disk however it can be updated to mount multiple disk.
* The YAML playbook was tested on [Nobara](https://nobaraproject.org/) 37. The similar approach can be used for Ubuntu but you need to replace the package manager from dnf to apt, change the systemd services etc.
* This guide only cover the NFS server at Fedora, it doesn't cover NFS clientsetup.

## Playbook Structure
There are 2 parts on the playbook. 
1. Setup the disk mount
2. Setup the NFS server 

## Commands:
Run ```ansible-playbook``` to execute the playbook.

For example:

```ansible-playbook -i <nodes_inventory> configure_samba_fedora_generic.yaml --extra-vars "ansible_become_password=<root password>"```

