---
title: "dhcp connection lagging"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by grim340 on 2010-03-23
using ubuntu 9.10
when i try to connect to google.com it starts loading
then just hangs.
how do i set the dns ips

---

### Post by Iowan on 2010-03-23
A DHCP client *should* get a list of servers from the DHCP server (and stash them in */etc/resolv.conf* Network Manager gives you the option to manually configure DNS servers under the Edit>IPv4 Settings tab.

---

