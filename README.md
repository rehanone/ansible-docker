ansible-docker
=========

An ansible role for managing the installation of `docker`.

It also installs `docker compose` plugin and can manage docker networks. More information on `docker-ce` installation on various platforms can be found here:

  - [https://docs.docker.com/engine/install/]https://docs.docker.com/engine/install/)

This role currently use the `docker-ce` version for `Debian` and `Ubuntu` based systems.

Requirements
------------

This role requires `docker`  package to be avalible in package manager on the target systems othe than `Debian` and `Ubuntu`.

Example Playbook
----------------

### 1. All Options

This example shows all possible options and their default values on an `Ubuntu` system.

```yaml
- hosts: all
  roles:
    - role: rehanone.docker
      vars:
        docker:
          debug: true
          main:
            manage: true
            packages:
            - docker-ce
            - docker-ce-cli
            - containerd.io
            - docker-compose-plugin
            state: present
          networks: []
          service:
            enabled: true
            manage: true
            name: docker
            state: started
          support:
            manage: true
            packages:
            - ca-certificates
            - curl
            - gnupg
            - lsb-release
            state: present
          upstream:
            key:
              file: docker.asc
              home: "/etc/apt/keyrings"
              url: https://download.docker.com/linux/ubuntu/gpg
            manage: true
            package:
              file: docker.list
              home: "/etc/apt/sources.list.d"
              url: https://download.docker.com/linux/ubuntu
            state: present
```

### 2. Minimum Required Options

This example shows minimum required options for using this role.

```yaml
- hosts: all
  roles:
    - role: rehanone.docker
      vars:
        docker:
```

License
-------

Apache-2.0
