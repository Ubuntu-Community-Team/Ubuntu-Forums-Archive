---
title: "Trying to bridge vlan connection from ubuntu to virtualbox via switch"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by jcclubb15 on 2013-07-01
Ok so I'm on a project for work and it seems impossible. I'm trying to use the bridge adapter function in virtual box to connect to my vlan configured through my switch. The only problem is, when I do the nmcli in the command line my vlan (vlan 2) is listed as down, but when I enter* nmcli con up id vlan 2* I get the message, Error: unknown device: vlan 2. But it shows up under ifconfig as having an ip address because I assigned one statically.. Any help would be greatly appreciated. We have assigned the switch an ip and used the gui to trunk one of our ports (port 24) for vlan trunking.

Ubuntu 12.04
Virtualbox with Ubuntu 12.04, Windows 7, Windows XP
Foundry EdgeIron 2402CF 24 port switch

---

