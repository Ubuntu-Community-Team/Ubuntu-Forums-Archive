---
title: "cannot detect wireless on ubuntu 10.04"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by Ericyue on 2012-08-08
hi, 

as shown on the title, i cannot detect the wireless on my laptop. 

can anyone teach me how to configure it ? 

i have try this command "sudo lshw -c network" and the result is as shown at below: 

  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:d9500000-d9503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:a1:f0:9d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.105 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:3000(size=256) memory:d3410000-d3410fff(prefetchable) memory:d3400000-d340ffff(prefetchable) memory:d3420000-d343ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:21:00:e5:00:88
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by Ericyue on 2012-08-08
i knows what the problem already. i have install the wrong wireless driver on the machine. 


Now , it is solve. :)

---

