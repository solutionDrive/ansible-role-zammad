ansible-role-zammad
===================

This role installs and/or configures Zammad, known from https://zamma.org .


Requirements
------------

To run zammad, you have to meet the requirements from
https://docs.zammad.org/en/latest/prerequisites-software.html .

Please note that is highly recommended *not* to run the database server
on the same machine as zammad itself.

You have to install ruby, bundler, rake and rails before.
Use for example geerlingguy.ruby but choose to build ruby from source as package manager's package may be outdated.


Role Variables
--------------

    # Install prerequisites via apt (disable and do it manually to use another package manager)
    zammad_install_prerequisites: true

    # Install zammad itself (from source)
    zammad_install: true

    # Configure existing zammad installation (setup can be done by setting ```zammad_install``` to true)
    zammad_configure: false

    # Install nginx as a reverse proxy in front of zammad
    zammad_install_nginx: true

    # Configure existing nginx as reverse proxy for zammad installation
    zammad_configure_nginx: false
    
    # Remove nginx's default vhost to enable only zammad
    zammad_remove_nginx_default_vhost: false

    # Set to true to create the database
    zammad_db_create: false
    
    # Set to true to run database migrations (you MUST do this is  zammad_db_create  is set to true)
    zammad_db_migrate: false
    
    # Set to true to seed the database with initial values (DON'T DO THIS ON AN EXISTING DATABASE!)
    zammad_db_seed: false

    # Set to true to install with MySQL as database driver
    zammad_db_mysql: true

    # Set to true to install with PostgreSQL as database driver
    zammad_db_postgresql: false


**Do not set both ```zammad_db_mysql``` and ```zammad_db_postgresql``` to true!**


    # Database parameters should be self explaining    
    zammad_db_host: 127.0.0.1
    zammad_db_port: 3306
    zammad_db_username: zammad
    zammad_db_password: ~
    zammad_db_name: zammad

    # The username zammad should be installed under
    zammad_user: zammad
    
    # The group zammad should be installed under
    zammad_group: zammad
    
    # Set to true to automatically create user and group if they don't exist yet
    zammad_user_group_create: true

    # Enable or disable installation of systemd services
    zammad_install_systemd_service: true



Dependencies
------------

None so far.


Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: solutiondrive.ansible-role-zammad }


License
-------

MIT


Author Information
------------------

Created by solutionDrive GmbH.
https://solutionDrive.de/
