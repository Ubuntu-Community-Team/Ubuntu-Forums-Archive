---
title: "Wireless and Ethernet not working after fresh install of 9.1"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by elydium on 2010-09-16
I just installed 9.10 to a dell inspiron 531s and neither the ethernet nor the wireless will find a signal. The results of sudo lshw -c network are 

*-network
product: BCM4318 [AirForce One 54g] 802.11g wireless LAN controller
vendor: Broadcom Corporation
physical id: 9
bus info: pci@000;01;09.1
version: 02
width: 32 bits
clock: 33 MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=32
resources: irq:17 memory:fd9fe000-fd9fffff
*-network DISABLED
decription: Wireless Interface
physical id: 1
logical name: wlan0
serial: 00:1b:fc:e3:63:9e
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by DirtDart on 2010-09-17
The **-network DISABLED* from the output is why your wireless isn't working.

Try this (it worked for me) from the console: 
```
sudo ifconfig wlan0 up
```

Please post the content of your */etc/network/interfaces* file.

---

