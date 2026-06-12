---
title: "Intel WIFI 5300 UNCLAIMED"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by asdrubalxx on 2009-05-09
Hi, need some help here.
Have Samsung nc10 with an Intel 5300 AGN wifi wich I lost a whole day trying to config. Had an Atheros wifi with ubuntu 8.10 and it worked really fine but this week I made an upgrade changing the atheros for an intel 5300 and installed 9.04 remix as well.

Using lshw -C network I'm getting the network UNCLAIMED and no logical name. Had installed the iwlagn drive with modprobe and put the iwlwifi5000-1.ucode on /lib/firmware.
I have been trying a lot others solutions from different forums but no results, the card works fine on winxp so I don't think it's hardware.
Any ideas how to solve it?

  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:d2:ce:91
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.0.156 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 42:95:d3:50:47:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

