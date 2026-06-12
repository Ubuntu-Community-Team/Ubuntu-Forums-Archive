---
title: "Wifi not active on installed Ubuntu but works on Live CD Ubuntu.  :'("
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by jim29 on 2012-04-18
Hello,

I have just installed Ubuntu 11.10 and am having issues with the Wireless not working.  Its not active and can't see any networks.

The strange thing is.....  When I loaded the live demo from the CD I had full network access.  I checked lshw and the same driver is being used.

Any ideas where to start please or further information required to assist?

Many thanks in advance.  Ubuntu is looking really nice.  :)

Live CD lshw

  *-network 
       description: Wireless interface 
       product: RT3090 Wireless 802.11n 1T/1R PCIe 
       vendor: Ralink corp. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:24:21:d4:ba:f4 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-12-generic firmware=0.34 ip=192.168.1.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:19 memory:febf0000-febfffff 


Installed Ubuntu lshw


  *-network 
       description: Wireless interface 
       product: RT3090 Wireless 802.11n 1T/1R PCIe 
       vendor: Ralink corp. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:24:21:d4:ba:f4 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-17-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:19 memory:febf0000-febfffff

---

### Post by jim29 on 2012-04-18
Hello, here is the lspci output as well.


nick@nkwubu11:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03) 
03:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe

---

### Post by chili555 on 2012-04-18
How about showing us:```
rfkill list all
dmesg | grep rt2
```Thanks.

---

### Post by jim29 on 2012-04-18
Very strange, logged into Ubuntu to get the requested information and suddenly I'm online?

Bizare, happy to close unable to replicate fault.  Thanks for your assistance. 

:)  Later.

---

