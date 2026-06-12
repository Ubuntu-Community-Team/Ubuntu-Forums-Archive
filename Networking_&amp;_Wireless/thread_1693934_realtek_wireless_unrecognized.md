---
title: "realtek wireless unrecognized"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by gian on 2011-02-23
hello All,

I have a new laptop, a Lenovo Edge 11.6" with AMD K345, where I installed Maverick, and the wireless card, Realtek, is unrecognized.

Here is lspci:
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

Here is lshw -c network:
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:af:5f:ea
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.56 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:43 ioport:bc00(size=256) memory:d0200000-d0200fff memory:d0000000-d0003fff memory:d0020000-d003ffff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:c000(size=256) memory:d0600000-d0603fff

Realtek drivers in /lib/firmware:
/lib/firmware/RTL8192E:
boot.img  data.img  main.img

/lib/firmware/RTL8192SE:
rtl8192sfw492.bin  rtl8192sfw74.bin  rtl8192sfw.bin

I have Googled around a lot, but I can't find a way to make it work...

thanks for reading,
-Gian

---

