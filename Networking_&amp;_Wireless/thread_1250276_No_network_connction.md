---
title: "No network connction"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by anafshalom on 2009-08-26
I did some messing around yesterday, and now my computer does not connect to internet

/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

ifup eth0 returns:
ifup interface eth0 already configured

---

### Post by superprash2003 on 2009-08-26
take out the # infront of the iface line and restart networking

---

### Post by Iowan on 2009-08-26
... or, put the # in front of **auto eth0** and see if Network Manager will handle it. (You'll still need to restart networking - and maybe Network Manager.)

---

