---
title: "Device Not Ready"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by jmona789 on 2013-02-06
I just installed Ubuntu 12.04.1 LTS on my Laptop and when I try to connect to a wireless network it says "device not ready(firmware missing)."  How do i fix this?

---

### Post by Bucky Ball on 2013-02-06
Welcome to the forums. Start by posting the result of:

```
sudo lshw -C network
```

---

### Post by jmona789 on 2013-02-06
*-network               
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:7c:f9:9c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.13 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:93:43:3c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-29-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by jmona789 on 2013-02-06
anybody?

---

### Post by Hadaka on 2013-02-06
hi try this,,

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43 
```

---

