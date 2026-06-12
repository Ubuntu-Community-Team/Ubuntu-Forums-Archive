---
title: "Wireless Conection"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by lexo22 on 2009-08-16
Hello, some time ago, I installed ubuntu 9.04 on my computer... Before that, my Wireless was working excelent (on Windows Vista)... But now it doesn't...
 
Please help me find the problem so I can fix it... :popcorn:

---

### Post by Cuba71 on 2009-08-16
What type of Wireless Adapter is in you machine?

---

### Post by lexo22 on 2009-08-16
*-network UNCLAIMED 
description: Network controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:0c:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix cap_list
configuration: latency=0
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 02
serial: 00:21:70:8e:db:c5
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
*-network:0 DISABLED
description: Ethernet interface
physical id: 2
logical name: vboxnet0
serial: 0a:00:27:00:00:00
capabilities: ethernet physical
configuration: broadcast=yes multicast=yes
*-network:1 DISABLED
description: Ethernet interface
physical id: 3
logical name: pan0
serial: 0a:22:e6:64:2d:d9
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Cuba71 on 2009-08-16
I don't understand what's happening.

The Atheros AR242x is supported by both Ubuntu Jaunty 9.04 as well as Karmic 9.10 alpha-4.

The driver for this adapter is the ath5k.  

I have this card [168c:001c] in my Toshiba laptop and I dual-boot, Vista/Ubuntu without any problems 

Make sure you have this driver installed.

antonio

---

