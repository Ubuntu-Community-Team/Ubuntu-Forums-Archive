---
title: "WiFi: How to when using /etc/network/interfaces"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by kenm_uk on 2011-03-11
I have set up my interface in /etc/network/interfaces so that I can assign several ip addresses to a network interface:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
     address 192.168.0.100
     netmask 255.255.255.0
     gateway 192.168.0.1

auto eth0:1
iface eth0:1 inet static
     address 192.168.0.101
     netmask 255.255.255.0
     gateway 192.168.0.1

auto eth0:2
iface eth0:2 inet static
     address 192.168.0.102
     netmask 255.255.255.0
     gateway 192.168.0.1

```

However, doing this means appears to mean that I can no longer use the Network Manager to manage WiFi connections.  There is no longer an icon on the tool bar for connecting/disconnecting to wifi networks.

What is the best way for me to again use the Network Manager for managing wifi connections while also having several IP addresses assigned to the interface?

Thanks,
Ken

---

