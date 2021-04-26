Role Name
=========

Install Prometheus Node_Exporter from github repository

Requirements
------------

nope

Role Variables
--------------

all variables are defined in defaults:

```yaml
---
# defaults file for node_exporter

prometheus_user:                       prometheus
prometheus_group:                      prometheus
prometheus_install_path:               '/opt/prometheus'
prometheus_config_path:                '/etc/prometheus'
prometheus_pid_path:                   '/var/run/prometheus'
prometheus_loglevel:                   'info'

prometheus_node_exporter_install_path: '{{ prometheus_install_path }}'
prometheus_node_exporter_config_path:  '{{ prometheus_config_path }}'
prometheus_node_exporter_pid_path:     '{{ prometheus_pid_path }}'
prometheus_node_exporter_user:         '{{ prometheus_user }}'
prometheus_node_exporter_group:        '{{ prometheus_group }}'
prometheus_node_exporter_loglevel:     '{{ prometheus_loglevel }}'
prometheus_node_exporter_listen:       '{{ prometheus_node_exporter_listen_ip }}:{{ prometheus_node_exporter_listen_port }}'
prometheus_node_exporter_listen_port:  '9100'
prometheus_node_exporter_listen_ip:    ''
prometheus_node_exporter_version:      '0.17.0'

enable_ufw:                            false
prometheus_node_exporter_src_access:
  - "{{ ansible_default_ipv4.network }}/{{ ansible_default_ipv4.netmask }}"
```

For typical deployment you can eventually define enable ufw fw and define src access list
Based on defined variables you can set variables common for all prometheus stack

For Debian7 you can use `prometheus_node_exporter_validate_certs=false` to resolve problem with github cert (it's not recommended).

Dependencies
------------

If you want to set fw, you need to have ufw role

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
    - hosts: servers
      roles:
         - role: node_exporter
```

License
-------

BSD

Author Information
------------------

Tomasz Baczynski

