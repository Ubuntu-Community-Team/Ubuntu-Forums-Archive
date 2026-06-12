---
title: "Trouble with interfaces ubuntu 11.04"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by ikazu on 2011-06-28
I have 2 NIC on my server.
one for LAN, and the other for Internet
I used static on both of them.

I've configured the interfaces

"
[B][SIZE=2]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.234
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet static
address 192.168.1.142
netmask 255.255.255.0
gateway 192.168.1.254

"

[/SIZE][/B][SIZE=2][FONT=Times New Roman][SIZE=1]restarted the NICs using the command "init.d/networking restart" but it showed me "failed to bring interface eth1"
and my eth1 turned into "eth1-eth0"

so..when i tried to connect to either one of them..it always only shows "eth1-eth0" is connected..

so what have i done wrong here?[/SIZE] i want to delete interface eth1-eth0, since it really annoys me..if it's possible, i would like rename it. help anyone ?[/FONT][/SIZE][B][SIZE=2][B][FONT=Times New Roman]
[/FONT][/B][/SIZE][/B]

---

### Post by jegumi on 2011-07-29
Do you fix the problem??

---

