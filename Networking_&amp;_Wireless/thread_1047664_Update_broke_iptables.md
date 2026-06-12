---
title: "Update broke iptables?"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by chip616 on 2009-01-22
I have a custom iptables script that I use on my work machines to block access to all sites except the one we need for work.  I have used this script for years, and it works fine.  A couple of days ago I did an update to this install of Kubuntu 8.04, and now my script fails to work properly, blocking ALL Internet access.

I hereby attach the output from a couple of iptables --list commands.  The first one is after a fresh boot, and the second one, as you can see, is after manually starting my firewall script.  Note that only after the manual start is access opened to the site I want (72.13.190.4).

> frontoffice@frontoffice:~$ sudo iptables --list
[sudo] password for root:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
o-eth0     all  --  anywhere             anywhere

Chain o-eth0 (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             192.168.0.0/24
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

[COLOR="Red"]frontoffice@frontoffice:~$ sudo /etc/init.d/chippyfirewall start[/COLOR]

frontoffice@frontoffice:~$ sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
o-eth0     all  --  anywhere             anywhere

Chain o-eth0 (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             192.168.0.0/24
ACCEPT     all  --  anywhere             72.13.190.4
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable
frontoffice@frontoffice:~$

As near as I can tell, the script is correctly linked in the rc(0-9).d files, and the syntax is correct.  The chippyfirewall script is located in init.d, has permissions 755, and belongs to user root, and group root.

I tried updating the script with update-rc.d but got the following output:

> frontoffice@frontoffice:~$ sudo update-rc.d chippyfirewall defaults 99
[sudo] password for root:
 System startup links for /etc/init.d/chippyfirewall already exist.
frontoffice@frontoffice:~$


So, why won't it run automatically?  Up until two days ago, it ran fine.  Did the update break something?

Thanks.

Frank.

---

