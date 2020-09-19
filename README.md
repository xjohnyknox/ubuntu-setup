# ubuntu-setup
This playbook will execute a initial setup for a brand new Ubuntu 20.04 systems.

A number of packages will be created with the options specified in the `vars/default.yml` variable file.

Why? Becasue i was tired of spending so much time in the process of setup a new installation of ubuntu, so with a playbook would be better to mainting a single script for all the usecases... (Spotify, VScode, steam, etc).

## Settings

- `create_user`: the name of the remote sudo user to create, (this is optional)
- `copy_local_key`: path to a local SSH public key that will be copied as authorized key for the new user. By default, it copies the key from the current system user running Ansible. (optional)
- `sys_packages`: array with list of packages that should be installed. --> This is the important

Also, inside the playbook.yml:

There is a part for use installation scripts for common software like Microsoft Teams, Browsers, and so on.
- `#  Scripts for install more packages`

## Running this Playbook

Quick Steps:

### 1. Obtain the playbook
```shell
git clone https://github.com/xjohnyknox/ubuntu-setup.git
cd ubuntu-setup
```

### 2. Customize Options

```shell
nano vars/default.yml
```

```yml
#vars/default.yml
---
create_user: sammy
copy_local_key: "{{ lookup('file', lookup('env','HOME') + '/.ssh/id_rsa.pub') }}"
sys_packages: [ 'name-of-package-to-install','name-of-package-to-install2','name-of-package-to-install3']
```

### 3. Run the Playbook

```command
ansible-playbook -l [target] -i [inventory file] -u [remote user] playbook.yml
```
That's all, i'm trying to improve this playbook, as i test it from my own ubuntu laptop :)
