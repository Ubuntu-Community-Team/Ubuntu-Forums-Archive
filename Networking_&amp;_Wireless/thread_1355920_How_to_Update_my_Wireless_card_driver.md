---
title: "How to Update my Wireless card driver"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by panddeb on 2009-12-15
I have ubuntu 9.04 installed on a PS3. I'm having problems with the wireless connection. I'm not using neither the network manager nor wcid since I tried both and couldnt make them to connect automatically on startup. So, I'm using a script. In the /etc/rc.local>
---------------------------
ifconfig eth0 down
ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid "XXXX"
iwconfig wlan0 mode Managed
ifconfig wlan0 up
dhclient wlan0
-------------------------

This works great, it connects at startup. The problem is that it disconects randomly from the wireless internet. 
 
I want to try to update the driver of my wireless card to see if that fixes the disconnection problem. How do I update the driver? The harwdware drivers app doesnt show me anything.
 
 

thanks for your reply!
--------------
Information
--------------
**$iwconfig wlan0**
wlan0 IEEE 802.11bg ESSID:"XXX" Nickname:"gelic_wl"
Mode:Managed Access Point: 00:23:69:31:93:FA 
Link Signal level=100/100 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

**$lspci**
doesnt give me anything

[B]$sudo lshw -C network
[/B]*-network:0 DISABLED 
description: Ethernet interface
physical id: 1
logical name: eth0
serial: 00:24:8d:08:d0:0d
size: 10MB/s
capacity: 1GB/s
capabilities: ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=Gelic Network Driver driverversion=2.0 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
*-network:1
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:24:8d:08:d0:0d
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=Gelic Network Driver driverversion=2.0 ip=192.168.1.104 link=yes multicast=yes wireless=IEEE 802.11bg
*-network:2 DISABLED
description: Ethernet interface
physical id: 3
logical name: pan0
serial: da:e8:58:02:16:5d
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


[B]$ uname -mr
[/B]2.6.28-6-powerpc64-smp ppc64

---

### Post by ubun2ibun3 on 2009-12-15
I'm not sure, but don't you need to upgrade the kernel to do that?  Or, if you know what your doing, you need to download the kernel source and then the module source for that card and compile it and all that.

I think it's really confusing...

---

### Post by panddeb on 2009-12-16
isnt there other way to just update the driver?

---

