---
title: "Wireless connection to Lenovo T500"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by doyleknight on 2010-03-06
I installed Ubuntu 9.10 on my Lenovo T500.  The wireless interface information is listed at the bottom of this message.

I would like to connect to my Airport Extreme wireless router which is password protected.  The bottom of the router lists three MAC addresses with different symbols next to them.  I assume the symbols mean different types of connections (e.g., firewire, ethernet cable, etc).

The network icon on the upper right corner of the screen indicates that wireless is enabled.  However, I don't get a wireless connection.  I checked that the switch on the front of the laptop is "on" for wireless.

Any suggestions ?

Thanks.


lshw -C network yields:

[I]*-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:a9:96:98
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:f4200000-f4201fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=no multicast=yes

---

### Post by doyleknight on 2010-03-06
I figured out the problem.  :)  I left clicked on the network icon and selected the network.  Now I have wireless.  (Actually, I found this solution elsewhere on the Ubuntu forum).

---

