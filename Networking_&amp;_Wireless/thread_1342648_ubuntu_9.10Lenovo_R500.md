---
title: "ubuntu 9.10/Lenovo R500"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by howdoesitmatter on 2009-12-01
System: Lenovo R500. Ubuntu version: 9.10 

I migrated to ubuntu from Vista a week ago. The wireless doesnt work. Ubuntu recognizes bluetooth but not the wireless. The following are the details. Hope someone can help me with what to do.

 
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. Device e020
        Flags: bus master, fast devsel, latency 0, IRQ 11
        I/O ports at 2000 [size=256]
        Memory at f4300000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
        Subsystem: Lenovo Device 20d5
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Memory at f4800000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: tg3
        Kernel modules: tg3

iwconfig gives me these results

lo        no wireless extensions.

eth0      no wireless extensions.

sudo lshw -C network gave the following results:

*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f4300000-f4303fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:22:68:16:29:43
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.13 ip=192.168.15.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:31 memory:f4800000-f480ffff

---

### Post by utnubuuser on 2009-12-01
1 active thread> [http://ubuntuforums.org/showthread.php?t=1182457]("http://ubuntuforums.org/showthread.php?t=1182457")

---

