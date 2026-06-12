---
title: "Why can't I have two network interfaces (DHCP and static)??"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-01-22
I'm trying to set up a DRBL server for use with CloneZilla. I'm using Hardy 8.04.

I uninstalled network manager and edited my network interfaces file. It reads as follows.



autho lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0




Note - My static IP is working on a closed network with no DHCP server. Simply a switch with other computers. 

My idea is to have a static NIC for use with the switch with other computers on a closed network, and the other NIC for use with DHCP so I can plug in to another outlet and get external access for updates and whatnot.

My DHCP does not work. The only way I can get DHCP to work is if I comment out all 4 lines of the static input and reboot. Then, DHCP works. :(

---

