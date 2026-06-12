---
title: "eth0 config - wireless nm-applet"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by 123betty on 2009-10-22
Hello

I'd like to configure /etc/network/interfaces for eth0. This file is always read at startup, even when no one is logged in.
And to use nm-applet for wireless as this has always different logins for different locations.


I cannot get it working.

In /etc/network/interfaces:
auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

in /etc/NetworkManager/nm-system-settings.conf
managed=false


Still not working.

Even if I do killall nm-applet for testing.

Please help me out.

---

### Post by Iowan on 2009-10-22
I presume you restarted networking after editing */etc/network/interfaces*? 
Post results of **ifconfig -a**

---

