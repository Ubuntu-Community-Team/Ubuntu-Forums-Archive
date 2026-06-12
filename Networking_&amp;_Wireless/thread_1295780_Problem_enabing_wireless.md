---
title: "Problem enabing wireless"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by megaman2000 on 2009-10-19
I'm not sure how to enable my wireless card...But I'm pretty sure the driver is installed. here's the sudo lshw -c network 

> *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:25:cc:a6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.0.104 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:4e:f0:e3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f2:49:3b:2c:a6:28
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Can anyone please tell me how I enable it?

---

### Post by waraltca on 2009-10-19
could you enable it??

I have the same problem!

---

### Post by megaman2000 on 2009-10-19
Nope,I sure couldn't...that's kind of why I posted.

---

### Post by megaman2000 on 2009-10-21
bump?

---

### Post by megaman2000 on 2009-10-24
bump

---

### Post by dreamingdarkness on 2009-10-25
Quick search pulled up something possibly relevant. Might take a look at:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
It depends on what version of Ubuntu you have installed. Hope that helps.

Let us know if the NetworkManager is present/started in the top right of your pc, which will help make sure that at least is running.

I don't have many other ideas, but you might want to post your iwconfig results, and check in System->Administration-> Log file Viewer
So, you can try posting the results of:
```
iwconfig
sudo ifconfig
``` (sudo may not be needed)
These will hopefully help narrow down if there is anything claiming correctly.


Go to "View" then "Find" and search for "NetworkManager", search for errors on it connecting. And possibly look for wlan0, or errrors in general during your start-up that indicate a failure to initiate the wireless correctly.

Best of luck!

---

