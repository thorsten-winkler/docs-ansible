# Ansible ecosystem - Information, tips, best practices

## Ansible
### Installation
```bash
# Ansible installation
$ pip install ansible

# Ansible upgrade
$ pip install --upgrade  ansible

# Example installation in an independent local virtual environment
$ python -m venv venv-ansible-installation
$ source venv-ansible-installation/bin/activate
$ pip install --upgrade pip
$ pip install ansible
```

### Inventory:
List all hosts of playbook/inventory file (default location: /etc/ansible/
hosts):
```
$ ansible-inventory -i hosts --graph
$ ansible-inventory -i hosts --list
```

### Roles:
Dependencies to other roles defined in
```
# cat <path-to-roles>/<role_name>/meta/main.yml:
- dependencies: []
```
### Plugins:
- Lookup plugins:
  - https://docs.ansible.com/ansible/latest/plugins/lookup.html
  - Get list of available plugins:\
    `$ ansible-doc -t lookup -l`
- List of plugin types (and therefore directory names for development)
  - https://docs.ansible.com/ansible/latest/dev_guide/developing_locally.html#adding-a-plugin-locally
        
        
## Ansible Galaxy
### Create new ansible role
- https://galaxy.ansible.com/docs/contributing/creating_role.html
  ```
  $ ansible-galaxy init --init-path <path-to-roles> <role_name>
  $ ls -la <path-to-roles>/<role_name>
      8 -rw-r--r--  1 user  staff   1,3K 15 Aug 13:13 .travis.yml
      8 -rw-r--r--  1 user  staff   1,3K 15 Aug 13:13 README.md
      0 drwxr-xr-x  3 user  staff    96B 15 Aug 13:13 defaults/
      0 drwxr-xr-x  2 user  staff    64B 15 Aug 13:13 files/
      0 drwxr-xr-x  3 user  staff    96B 15 Aug 13:13 handlers/
      0 drwxr-xr-x  3 user  staff    96B 15 Aug 13:13 meta/
      0 drwxr-xr-x  3 user  staff    96B 15 Aug 13:13 tasks/
      0 drwxr-xr-x  2 user  staff    64B 15 Aug 13:13 templates/
      0 drwxr-xr-x  4 user  staff   128B 15 Aug 13:13 tests/
      0 drwxr-xr-x  3 user  staff    96B 15 Aug 13:13 vars/
  ```

### List installed ansible roles
- `$ ansible-galaxy list`

### Download ansible roles from different sources
- https://docs.ansible.com/ansible/latest/reference_appendices/galaxy.html?highlight=role#installing-roles
- https://galaxy.ansible.com/docs/using/installing.html#installing-multiple-roles-from-a-file
- Create yaml file <requirements.yml>
  ```
  ---
  # from Github
  - src: https://github.com/bennojoy/nginx
  # from galaxy
  - src: yatesr.timezone
  ...
  ```
- Install roles from <requirements.yml>\
`$ ansible-galaxy install --roles-path <path-to-roles> -r <requirements.yml>`        

## Useful links/information/discussions/questions/decisions:
- Best Practices:
    - https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html
- YAML Syntax:
    - https://yaml.org/refcard.html
    - https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html
- Ansible lookups: vars vs. facts
    - https://opensolitude.com/2015/05/27/ansible-lookups-variables-vs-facts.html

## References
- Ansible Docs - https://docs.ansible.com/
- Ansible Galaxy Docs - https://galaxy.ansible.com/docs/
- Ansible Galaxy User Guide - https://docs.ansible.com/ansible/latest/galaxy/user_guide.html
