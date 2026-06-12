---
title: "Wireless problem"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by Jameshardy88 on 2009-07-15
Hi, thanks for taking the time to read this. 

I have been using ubuntu and linux for coming up to a year now and love it to bits but unfortunately im no expert. I recently bought a new laptop (obviously it had to have vista already on it. i set up a dual boot system of vista and jaunty and for a day everything worked prefectly. However all of a sudden vista would not boot. Fortunately a friend had a restore disk so i wiped my entire HD reinstalled vista and then put ubuntu back on. Its working fine again now except that for some reason i no longer can get wireless on my ubuntu partition. It seems willing to connect, it can see networks but not connect to them. What could be causing this when im using the same computer and the same disk? I have also tried installing Ibex and that encountered exactly the same problem.

below is the output from "shw -C network"

```

hardy@hardy-laptop:~$ sudo lshw -C network
[sudo] password for hardy: 
*-network 
description: Wireless interface
product: Wireless WiFi Link 5100
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: wmaster0
version: 00
serial: 00:22:fa:d3:12:84
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
*-network
description: Ethernet interface
product: 88E8040 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 12
serial: 00:23:8b:c2:e6:92
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.3 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 22:93:47:25:7f:0b
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Thanks for any help,

James

---

