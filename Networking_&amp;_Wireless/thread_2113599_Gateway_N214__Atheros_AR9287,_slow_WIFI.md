---
title: "Gateway N214 / Atheros AR9287, slow WIFI"
date: 2013-02-07
forum: Networking &amp; Wireless
---

### Post by eak819 on 2013-02-07
First let  me say that Ubuntu is great!  I've used it in the past without any issues I couldn't fix by reading this forum.  I have an Gateway N214 everything  works great but the WIFI speed is sporadic and or non-existent.  Please tell me what info you need and I'll get it for you.

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by eak819 on 2013-02-07
```
*-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 1c:75:08:10:87:0a
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 memory:b3400000-b340ffff
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:65:9d:29:fb:58
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-23-generic firmware=N/A ip=192.168.0.18 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:b2400000-b240ffff
```

---

### Post by eak819 on 2013-02-09
Okay I found this article [http://pleph.appspot.com/init/posts/view/2657865](http://pleph.appspot.com/init/posts/view/2657865) when 
```
sudo ifconfig wlan0 down sudo rmmod -f ath9k sudo modprobe ath9k nohwcrypt=1 sudo ifconfig wlan0 up
```

Is running in the terminal everything seems to be going great. After I close the terminal it returns to slow performance noticeable most when signing into sites like Facebook.  What am I doing here? Can I make it permanent?
I've also noticed that performance is better at start-up and slowly goes down from there. Thanks for your help!

---

