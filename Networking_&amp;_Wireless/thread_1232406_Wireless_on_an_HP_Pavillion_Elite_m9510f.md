---
title: "Wireless on an HP Pavillion Elite m9510f"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by DevinMcElheran on 2009-08-05
I can't get the wireless working on my new HP, all I know is that it's an Atheros card. It shows "Atheros 'unknown'" in my lspci, or something along those lines. Any help will be greatly appreciated.

---

### Post by superprash2003 on 2009-08-05
post output of **lshw -C network** from the terminal

---

### Post by DevinMcElheran on 2009-08-06
*-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:8c:5c:f5:a1
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair

is my output, I don't know what good it'll do. But if it does any, thanks a lot.

---

