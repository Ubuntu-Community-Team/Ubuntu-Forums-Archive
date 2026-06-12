---
title: "How to set up gateway"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by rhyancute on 2009-09-10
this is my interfaces

auto lo
iface lo inet loopback

allow-hotplug eth0

iface eth0 inet static
address 192.168.1.33
netmask 255.255.0.0

iface eth1 inet static
address 66.666.66.66
netmask 255.255.255.240
gateway 66.666.666.65

auto eth0

auto eth1

---------------------------------------------------------------
and this is my resolv.conf

search ns2.website.com
nameserver 55.555.555.51

---------------------------------------------------------------
it works fine, but i dont know how to share my internet so that clients can connect to internet..

---

### Post by Iowan on 2009-09-10
The artificial information isn't really useful (555 and 666 aren't valid).
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for connection sharing.

---

