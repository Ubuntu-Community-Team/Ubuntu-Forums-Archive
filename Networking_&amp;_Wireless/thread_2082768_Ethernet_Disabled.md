---
title: "Ethernet Disabled"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by ubunteshwar on 2012-11-10
I have been using only wireless for a long time but I am sure the ethernet worked some time but now it does not.  I recently did a clean install of Precise. I dont know if that broke the ethernet. Wireless works fine but I need ethernet at a place where there is no wireless.

lt1:~$ sudo lshw -class network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 01
       serial: 00:21:00:8d:8d:53
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=10.0.0.3 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:db600000-db603fff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A latency=0 link=no multicast=yes port=MII speed=100Mbit/s
       resources: irq:47 ioport:6000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff


If I go to System Settings - Network, I see  Wired as Unmanaged and has hardware address 00:00:00:00:00:00

How do I fix this? Thanks

---

### Post by chili555 on 2012-11-10
Let's have a look at:```
cat /etc/network/interfaces
dmesg | grep eth0
```Thanks.

---

