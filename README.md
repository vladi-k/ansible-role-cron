ansible-role-cron
====

Install cron daemon, copy scripts and configure cron jobs.

Requirements
------------

* RHEL7+

Role Variables
--------------

* `cron_package` - name of cron daemon package.
* `cron_scripts` - list of scripts to copy, example:

```yaml
cron_scripts:
  - content: |
      #!/bin/bash
      echo "blabla"
    dest: /usr/lcal/bin/bla
  - src: /local/path/to/file.sh
    dest: /usr/local/bin/file.sh
```

* `cron_jobs` - list of cron jobs, example:

```yaml
cron_jobs:
  - name: job01
    hour: 7
    job: /usr/local/bin/file.sh
```

* `cron_service_name` - name of cron service

Dependencies
------------

N/A

Example Playbook
----------------

```
- hosts: my-servers
  vars:
    cron_jobs:
      - name: myjob
        hour: 2
        user: root
        job: "ls -l"
  roles:
    - ansible-role-cron
```

License
-------

GPLv3

Author Information
------------------

Vladimir Vasilev
