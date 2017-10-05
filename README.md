Role Name
=========

RedHat Internal RHN subscription manager role. This role only manages subscriptions!

Requirements
------------

None

Role Variables
--------------

| Name              | Default Value       | Description          |
|-------------------|---------------------|----------------------|
| `rhn_repositories_enabled` | NULL | A list of repositories to enable |
| `rhn_repositories_disabled` | NULL | A list of repositories to enable (see note below to disable all) |
| `rhn_skip_rhn_repos_disable` | false | Skip disabling repositories |
| `rhn_skip_rhn_repos_enable` | false | Skip disabling repositories |


**Note**: the purpose of the *skip* variables is to forcefully prevent multiple
invocations of the subscription commands when this role is used as a dependency
of others.

**Note**: to disable all repositories, set the `rhn_skip_rhn_repos_disable` variable
to [ '"*"' ].

Dependencies
------------

None

Example Playbook
----------------

Usage:

	- hosts: all
		vars:
			rhn_repositories_enabled:
				- 'rhel-{{ ansible_distribution_major_version }}-server-extras-rpms'
				- 'rhel-{{ ansible_distribution_major_version }}-server-rpms'
				- 'rhel-{{ ansible_distribution_major_version }}-server-optional-rpms'
			rhn_repositories_disabled:
	      - 'rhel-{{ ansible_distribution_major_version }}-server-tus-rpms'
		remote_user: root
		roles:
			- ansible-rhn-subscribe

License
-------

Apache 2.0


Author Information
------------------

Messaging QE team @ RedHat
