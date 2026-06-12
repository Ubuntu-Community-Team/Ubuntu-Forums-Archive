---
title: "eth0 down on reboot"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by professor-g on 2008-12-11
Fresh re-install to 8.04.1
64-bit, server install
eth0 doesnt come up automatically 

Might be that I have to make it eth1
(had this problem in the past with onboard NIC cards using Ubuntu)

To get it working I have to do:

ifup eth0


/etc/network/interfaces looks like:


# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.11
netmask 255.255.255.0
gateway 192.168.2.1

---

### Post by Iowan on 2008-12-11
You might see if this [workaround]("http://ubuntuforums.org/showthread.php?t=974382") helps.

---

