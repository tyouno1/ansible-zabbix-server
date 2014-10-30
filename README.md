wdijkerman.zabbix-server
=========

This is an role for installing and maintaining the zabbix-server. There are other roles for the proxy, javagateway and the agent. (Which will be available soon..)

Requirements
------------

Role Variables
--------------

There are some variables in de default/main.yml which can be changed:
* `zabbix_url`: This is the url on which the zabbix web interface is available. Default is zabbix.example.com, you should override it. For example, see "Example Playbook"
* `zabbix_version`: This is the version of zabbix. Default it is 2.4, but can be overriden to 2.2 or 2.0.
* `zabbix_timezone`: This is the timezone. The apache vhost needs this parameter. Default: Europe/Amsterdam

There are some zabbix-server specific variables which will be used for the zabbix-server configuration file, these can be found in the vars/main.yml file. There are 2 which needs some explanation:
```bash
  #database_type: mysql
  #database_type_long: mysql
  database_type: pgsql
  database_type_long: postgresql
```

There are 2 database_types which will be supported: mysql and postgresql. You'll need to comment or uncomment the database you would like to use. In example from above, the postgresql database is used.

Dependencies
------------

This role has 1 "hardcoded" dependency: geerlingguy.apache. This is an role which support the 3 main operating systems (Red Hat/Debian/Ubuntu). I can't find an mysql or postgresql role which also supports these 3 operating systems.

`You'll need to find the correct role by yourself. If there is an role which supports these 3 operating systems, please let me know and I'll use it as dependency.`

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: zabbix-server
      sudo: yes
      roles:
         - { role: geerlingguy.apache }
         - { role: wdijkerman.zabbix, zabbix_url: zabbix.dj-wasabi.nl }

License
-------

GPLv3

Author Information
------------------

This is my first attempt to create an ansible role, so please send suggestion or pull requests to make this role better. 

Github: https://github.com/dj-wasabi/ansible-zabbix-server
email: ikben [ at ] werner-dijkerman . nl
