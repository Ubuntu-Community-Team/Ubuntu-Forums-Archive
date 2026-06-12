---
title: "Wireless Not Showing"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by Crimex on 2009-06-13
When booting into Ubuntu using Linux Kernel 2.6.28-13, Ubuntu does not give me any options to connection to wireless. The Network menu just says:
Right Click Menu:
Enable Networking
Edit Connections...
About

Left Click Menu:
Wired Network
 disconnected
VPN Connections

In Edit Connections... under the Wireless tab, all wireless settings that were saved under Linux Kernel 2.6.24-23 still exist.

If I boot into Ubuntu using Linux Kernel 2.6.24-23, the wireless works as expected.


How do I go about fixing the wireless under Linux Kernel 2.6.28-13

---

### Post by The Toxic Mite on 2009-06-13
First, can you post the results of the following Terminal command please?

```
lshw -c network
```Assuming you are using GNOME, go to Applications > Accessories > Terminal.

:)

---

### Post by Crimex on 2009-06-13
*-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:37:1c:4e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f6:a2:61:94:5c:65
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by The Toxic Mite on 2009-06-13
Right... Broadcom wireless woes yet again... :|

I cannot go any further, but someone else might be able to help sort your problems out.

:)

---

### Post by Crimex on 2009-06-15
Ok, thanks anyway.

---

