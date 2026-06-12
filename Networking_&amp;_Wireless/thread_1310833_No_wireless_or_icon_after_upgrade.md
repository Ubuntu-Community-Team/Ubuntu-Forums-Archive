---
title: "No wireless or icon after upgrade"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by cyclopse on 2009-11-02
Hi all,

Did a upgrade and like many others no wireless icon. This is on a Dell Mini 9.
Drivers state Broadcom STA proprietary wireless driver. I have the green lamp and it states the driver is activated but not currently in use. lshw - C output;-

*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:cc:5f:9c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)

Any advice greatly received.

Thanks

Cyclopse :(

---

### Post by foottuns on 2009-11-02
you need to extract the firmware so that the drivers will work, have try to go at system/administration/hardware drivers and enable the driver from there, if will not work u need to extract the firmware so it will work, i have the tutorial at home so i can give you the website.

---

### Post by cyclopse on 2009-11-02
That would be great. I'm fairly new to Ubuntu but with a tutorial I should be OK.

Thanks

Cyclopse

---

### Post by cyclopse on 2009-11-09
Bump. Still no wireless option if anyone can help?

---

