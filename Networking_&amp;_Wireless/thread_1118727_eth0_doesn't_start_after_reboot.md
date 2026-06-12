---
title: "eth0 doesn't start after reboot"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by toxiwell on 2009-04-07
Hello guys!

I've problem when my server comes back after reboot. It looses eth0 interface settings and I haven't access to my box via network.
There is my /etc/network/interfaces

[HTML]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.109
netmask 255.255.255.0
gateway 192.168.1.1

[/HTML]

What it can be?

---

### Post by Iowan on 2009-04-07
Check the settings in */etc/NetworkManager/nm-system-settings.conf *.

---

### Post by superprash2003 on 2009-04-07
i dont know if this makes a difference.. insert the auto eth0 line at the end of the file

---

### Post by toxiwell on 2009-04-07
Thanks guys! I'll try it!

---

