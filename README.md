# Prerequisites

- Debian 12 base system

- python3.11 openssh-server

- Being able to SSH as root to the destination host

# Outcome

This will setup your Debian host to automatically run StepMania on boot. As soon as StepMania is closed, it will re-run it.

The "stepmania" user will be available to connect over SCP to push files

Credits to Enrico Zini for writing nodm and a LightDM configuration guide: https://www.enricozini.org/blog/2019/himblick/x-autologin/

# Installation steps

1. Install a Debian minimal OS into your host with the system utilities and SSH

2. Copy your SSH Key to the host.

3. Set the IP address or hostname of your host into the `inventory` file

4. Set the password for the `stepmania` user inside the `stepmania_password` variable of the `inventory` file

5. Find your gamepad usb port:
```sh
udevadm info -q all -n /dev/input/eventX
```
and set it in the `install_stepmania.yaml`

6. Run the Ansible playbook: `ansible-playbook install.yaml`
