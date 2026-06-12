---
title: "Unable to access internet with static ip"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by sahkiuvl on 2013-02-25
Ubuntu 12.10
I have configured static ip for my system in /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1

#up route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1 dev eth0

I also tried configuring route but after i configure static ip the internet doesn't work for me. With DHCP the internet works fine, please guide me on how to get the internet working with the static ip.

---

### Post by chili555 on 2013-02-25
If Network Manager is installed and running on your computer, editting */etc/network/interfaces* will not likely work. If it is, then I suggest you make the needed changes in there. Please see attached.

If NM is not running, then I suggest you amend *interfaces* to something like:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.[COLOR="Red"]105[/COLOR]
netmask 255.255.255.0
gateway 192.168.1.1
[COLOR="Red"]dns-nameservers 8.8.8.8 192.168.1.1[/COLOR]
```Please be sure you use a static address outside the range used by the DHCP server in the router so as to avoid collisions. Second, if you declare a static IP address, then be sure to declare DNS nameservers.

---

