---
title: "wireless is not working"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by suarez on 2013-02-16
[CENTER]after update my kernel to 3.2.0 the wireless is stop working is gone
sudo lshw -C network:
```
*-network               
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:fbd00000-fbd03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: f0:4d:a2:c6:2d:49
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:d000(size=256) memory:d0c10000-d0c10fff memory:d0c00000-d0c0ffff memory:fb300000-fb31ffff

```
sudo iwconfig:

```
ppp0      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

```

sudo rfkill list all
```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

any helps pleas i tired  to fix ittt:(
[/CENTER]

---

