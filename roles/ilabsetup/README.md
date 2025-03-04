# InstructLab Role

Ansible role to install, configure InstructLab on .rpm based distribution. Originally based on below blog post.
REF; https://www.redhat.com/en/blog/instructlab-tutorial-installing-and-fine-tuning-your-first-ai-model-part-1

## Requirements

- RHEL 7 or 8
- Ansible 2.9+

## Role Variables

All variables are defined in `vars/main.yml`. Here are the key variables:

- `instructlab_repo`: URL of the InstructLab repository (default: "https://github.com/your-org/instructlab.git")
- `install_dir`: Directory where InstructLab will be installed (default: "/opt/instructlab")
- `install_dir_owner`: Owner of the installation directory (default: "{{ ansible_user_id }}")
- `install_dir_group`: Group of the installation directory (default: "{{ ansible_user_id }}")
- `install_dir_mode`: Mode of the installation directory (default: '0755')
- `required_packages`: List of required packages (default: ['git', 'python3', 'python3-pip', 'docker'])
- `instructlab_version`: Branch or tag of the InstructLab repository to clone (default: "main")
- `pip_requirements`: Path to the `requirements.txt` file for Python dependencies (default: "{{ install_dir }}/requirements.txt")
- `pip_executable`: Executable for pip (default: "pip3")
- `install_script`: Path to the InstructLab installation script (default: "{{ install_dir }}/install.sh")
- `install_script_exists`: Path to check if the installation script exists (default: "{{ install_dir }}/install.sh")
- `verify_command`: Command to verify the InstructLab installation (default: "instructlab --version")

## Example Playbook

```yaml
- hosts: all
  become: yes
  roles:
    - common