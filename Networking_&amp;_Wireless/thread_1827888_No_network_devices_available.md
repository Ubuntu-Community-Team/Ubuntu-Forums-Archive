---
title: "No network devices available"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by erelsgl on 2011-08-18
I have just installed  Wubi with Ubuntu 10.04, and I have no network connection at all.

The network icon says something like "No network devices available".

I have a standard wired network card (Intel 82579LM Gigabit Net Conn).

ifconfig shows only "lo", no "eth0". 

/etc/network/interfaces also shows only "lo". I tried to manually add:

auto eth0
iface eth0 inet dhcp

but it didn't help.

I have network connection when I connect with Windows. Can anyone help?

---

