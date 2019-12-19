ROS 2 (Robot Operating System)
=========

[![Build Status](https://travis-ci.org/rarrais/ansible-role-ros2.svg?branch=master)](https://travis-ci.org/rarrais/ansible-role-ros2)

An Ansible Role that installs ROS 2 (Robot Operating System) on Ubuntu. 🤖

Requirements
------------

None.


Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):


  ```yaml
  # Retrieved from ROS2 installation instructions
  ros2_gpg_key_url: https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc
  ros2_repository_url: http://packages.ros.org/ros2/ubuntu

  # Ubuntu Bionic (18.04) Options: bouncy; crystal; dashing (LTS); eloquent
  ros2_distribution: dashing

  # Options: ros-desktop (recommended); ros-base (bare bones)
  ros2_configuration: ros-base

  # Default username and group for catkin_ws installation
  ros2_user:
      name: ubuntu
      group: ubuntu

  dev_ws: dev_ws

  ros2_domain_id: 0

  install_argcomplete: true

  # List of ROS packages to be installed without ros-<distro> prefix
  ros2_packages:
  ```


Dependencies
------------

None.

Example Playbook
----------------

Example to install ROS desktop-full configuration with turtlesim on the host system with a custom (existing) username:

```yaml
- hosts: localhost
  connection: local
  become: true
  vars:
    ros2_user:
        name: rarrais
        group: rarrais
    ros2_configuration: ros-desktop
    ros2_packages:
      - turtlesim
  roles:
    - rarrais.ros2
```

License
-------

MIT

Author Information
------------------

This role was created in 2019 by [Rafael Arrais](https://github.com/rarrais).
