# Ansible Role: Firewall (iptables)
With a help of the role you can create firewall rules from inside target role.

It can be usefull if you want to encapsulate an application firewalling logic inside of the role where the application deployment process definedd. 

## Requirements
CentOS/RHEL based system.

## Role Variables
None

## Dependencies
None

## Usage Example
Add `firewall` in dependencies (`meta/main.yml`) of your role:

    ---
    dependencies:
      - {role: firewall}


If `firewall` role directory is placed in the `roles/firewall`, adding new firewall rules for your target role as simple as following:

    - name: Open whitelisted IPs
      include: ../../firewall/tasks/do.yml
      vars:
        add_rules:
          - {proto: "tcp", shost: ["123.123.123.123", "234.234.234.234"], dport: [80], comment: "Graphite WebApp"}
          - {proto: "udp", shost: "{{ list_of_ips }}", dport: [8125], comment: "StatsD port"}


## License

MIT / BSD

## Author Information

This role was created in 2015 by [Oleg Tokarev](http://otokarev.com/).
