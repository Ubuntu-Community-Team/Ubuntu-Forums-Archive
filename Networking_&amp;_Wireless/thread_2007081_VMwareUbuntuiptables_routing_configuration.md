---
title: "VMware/Ubuntu/iptables routing configuration"
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by mmihalos on 2012-06-20
I am trying to build a network in VMware environment and implement/test an iptables firewall for my thesis.

I have 3 virtual machines that each hosts an Ubuntu 12.10 installation.

RouterFW plays the role of the Router and Firewall and hosts 3 interfaces:
eth0: 192.168.160.128 / NAT, connects to the internet
eth1: 192.168.1.128 / Vmnet1 (Host-only), connects to the DMZ
eth2: 192.168.2.128 / Vmnet2 (Host-only), connects to an individual host, a workstation

DMZ is a DMZ that hosts web, mail and ftp server installations.
eth0: 192.168.1.129 / Vmnet1, connects with the RouterFW

Production Dpt. is a typical employee workstation
eth0: 192.168.2.129 / Vmnet2, connects with the RouterFW

I can traffic all incoming connections through PREROUTING for webserver, mailserver and ftp server ports and when I hit 192.168.160.128 on my host machine's browser I can access the website situated under the 192.168.1.129 DMZ vm.

**My problem is that the workstation virtual machine is required to have access to the internet.**

I have tried the following solution:
-POSTROUTING MASQUERADE traffic from 192.168.160.0/24 to -o eth2
iptables -t nat -A POSTROUTING -s 192.168.160.0/24 -o eth2 -j MASQUERADE

-Added the echo 1 >> /proc/sys/net/ipv4/ip_forward on the RouterFW machine.

-I changed the default gw for the workstation to be 192.168.2.128

But still the workstation virtual machine doesn't have internet access. Any clues on what could be going wrong?

Thank you in advance.

Michael

---

