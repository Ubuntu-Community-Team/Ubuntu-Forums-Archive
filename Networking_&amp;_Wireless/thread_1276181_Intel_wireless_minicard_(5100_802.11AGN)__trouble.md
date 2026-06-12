---
title: "Intel wireless minicard (5100 802.11AGN)  trouble"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by Corin Gloom on 2009-09-26
im a newbie and my wireless wont connect
im using jaunty desktop edition

i know that i have the intel 5100 802.11AGN half mini card, but i dont know if i have the right dirver or how to check

**sudo lshw -C network** prints

 *-network               
  
         description: Wireless interface
  
         product: Wireless WiFi Link 5100
  
         vendor: Intel Corporation
  
         physical id: 0
  
         bus info: pci@0000:04:00.0
  
         logical name: wmaster0
  
         version: 00
  
         serial: 00:21:5d:80:cd:7a
  
         width: 64 bits
  
         clock: 33MHz
  
         capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
  
         configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  
    *-network
  
         description: Ethernet interface
  
         product: NetLink BCM5784M Gigabit Ethernet PCIe
  
         vendor: Broadcom Corporation
  
         physical id: 0
  
         bus info: pci@0000:08:00.0
  
         logical name: eth0
  
         version: 10
  
         serial: 00:21:70:8a:df:4d
  
         size: 100MB/s
  
         capacity: 1GB/s
  
         width: 64 bits
  
         clock: 33MHz
  
         capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
  
         configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=100MB/s
  
    *-network DISABLED
  
         description: Ethernet interface
  
         physical id: 2
  
         logical name: pan0
  
         serial: c6:4e:7a:3c:1a:96
  
         capabilities: ethernet physical
  
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

