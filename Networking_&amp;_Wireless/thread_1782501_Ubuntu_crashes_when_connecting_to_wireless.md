---
title: "Ubuntu crashes when connecting to wireless"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by Tumetsu on 2011-06-14
I have had this problem with live USB of Ubuntu 11.4 and now Linux Mint. When in live, I get notification that there is wireless networks available. When I click to connect, wireless icon cycles couple of times and mouse starts to lag seriously. Wireless icon is completely frozen and after a while whole system freezes (can't move mouse or access terminal). What could be a problem? Here is my computer's specs which I listed in old topic:
> *-network UNCLAIMED 
description: Network controller
product: Atheros Communications Inc.
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory:fbff0000-fbffffff
*-network
description: Ethernet interface
product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:01:00.0
logical name: eth0
version: c0
serial: 48:5b:39:87:3b:d6
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI duplex=full firmware=N/A ip=192.168.11.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: irq:29 memory:f7fc0000-f7ffffff ioport:ec00(size=12
tuomas@Tuomas-netbook:~$
It's Asus R101 netbook. Ubuntu 10.4 worked otherwise nice though to access wireless network, I had to install newer kernel. I'm now installing Mint and will try that after it but until that and in case it doesn't help, what is the matter and how to fix it? Thanks.

---

### Post by Tumetsu on 2011-06-15
I installed Linux Mint and tried to update Kernel from Daily Mainline but couldn't dues some dependency issues. I tried with synaptic some generic ppa package too though. And computer freezes totally when trying to access wireless network.

I have had this problem with Ubuntu 11.4, Linux Mint 11 but not with Ubuntu 10.4 or newest Jolicloud. What could be the problem? Gnome's wireless app...? What could be the main differences between listed distros which could afect to wireless as it seems to do?

---

