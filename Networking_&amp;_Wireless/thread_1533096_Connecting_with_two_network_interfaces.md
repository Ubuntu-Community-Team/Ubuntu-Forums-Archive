---
title: "Connecting with two network interfaces ?"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by Radar_mX on 2010-07-17
hi all

I have searched google but no luck

I want to connecting using wireless card (wlan0) and using ethernet at the same time (eth0) at the same time
NOTE: there are two different connections (networks)

my network manager is wcid , it only connects ether wireless or ethernet not both

I want to have two IPs at the same time

wlan0 should connects to AP and eth0 connects to ethernet my home router

I want this because with the ethernet I run vnc server and I open vncviewer with windows computer to control it and with other network I want to do some stuff ...etc not to mention


thanks

---

### Post by Radar_mX on 2010-07-18
up ??

---

### Post by Iowan on 2010-07-18
I haven't used wicd (or kubuntu, for that matter), so I'm not sure how well it plays with */etc/network/interfaces*.
You can *try* editing it:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```Remember to restart/reboot.

---

### Post by Radar_mX on 2010-07-19
tnanks

but no much help

these two lines already there 

any ideas ?

---

### Post by Iowan on 2010-07-19
What are results of **ifconfig -a** afterwards?

---

