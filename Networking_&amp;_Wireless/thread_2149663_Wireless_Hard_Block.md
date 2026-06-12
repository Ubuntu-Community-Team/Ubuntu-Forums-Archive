---
title: "Wireless Hard Block"
date: 2013-05-29
forum: Networking &amp; Wireless
---

### Post by alexchase678 on 2013-05-29
rfkill shows: 

$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes




lshw -C network shows:

*-network DISABLED      
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:14:11:8a:48
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-17-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:da100000-da101fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: c8:0a:a9:0e:3d:14
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:17 ioport:4000(size=256) memory:d4104000-d4104fff memory:d4100000-d4103fff memory:d4110000-d411ffff

I added options iwlwifi 11n_disable=1 to the file /etc/modprobe.d/iwlwifi.conf.

---

### Post by alexchase678 on 2013-05-29
Fixed it, in grub I had added the flag acpi=off.  I removed it and now wifi works fine.

---

