---
title: "2 Nics eth0 &amp; wlan0 connection problem"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by Rickzclinuxdude on 2010-01-15
Maybe someone can help

I have two nics  eth0 & wlan0

One of the nics is dhcp which allows me to surff the web, check e-mail etc.

The other nic card (wlano) is a closed class A network with static IP example ip 10.10.5.15 255.255.255.0 gw 10.10.5.1

This nic is used to monitor different types of specialized equipment that also are on the class A network

With Microsoft Windows, it's easy enough to add a presistant route statement so one can use both nic's at the same time. However with Ubuntu Linux, even adding a route statement will not allow me to use both nics at the same time.

What am I doing wrong?

Any suggestions or help would be much appreciated

Rickzc

---

### Post by Fire_Chief on 2010-01-15
You can have both NICs active but you should only have 1 gateway configured on the system otherwise it can get confused. So remove the gateway from the isolated network but leave the IP and netmask. The wlan0 NIC will still communicate with the directly attached isolated network and your other public side NIC should work as normal.

Cheers!

---

