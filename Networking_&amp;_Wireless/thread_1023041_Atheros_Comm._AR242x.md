---
title: "Atheros Comm. AR242x"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by Dave16 on 2008-12-27
Greetings - I just installed Ubuntu 8.10 Desktop Edition, I can't connect to my wireless network.  I can't seem to locate this wireless network or any other wireless networks that I know exist as I can see them when I run off of this computer using Vista.  

I am able to use the internet via ethernet connection as all seems to work well. 

I believe my struggle is the fact that my wireless adapter is not Linux supported.  Can someone confirm this for me?  And if this is the case, am i just plain out of luck, or are there work arounds?

Thank you in advance for your help!! 


 description: Ethernet interface

       product: 88E8039 PCI-E Fast Ethernet Controller

       vendor: Marvell Technology Group Ltd.

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 15

       serial: 00:1a:80:25:49:a8

       size: 100MB/s

       capacity: 100MB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.101 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s

  *-network UNCLAIMED

       description: Ethernet controller

       product: AR242x 802.11abg Wireless PCI Express Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:06:00.0

       version: 01

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix cap_list

       configuration: latency=0

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: de:fb:de:ed:f2:88

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

