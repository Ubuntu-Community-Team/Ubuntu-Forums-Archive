---
title: "How to install wireless network in Ubuntu8.10 (with Asus K40IJ T6400)"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by thuynn on 2009-08-02
I'm a newbie in Ubuntu 8.10. I have installed WinXP before Ubuntu and can access wireless network normally, but when I installed Ubuntu, I can only wired network and I do not know how to install the wireless network. I have search on this forum and tried this command"sudo apt-get install linux-backports-modules-jaunty" and this is the output:

[COLOR="Red"]thuynnbk@thuynnbk-laptop:~$ sudo apt-get install linux-backports-modules-jaunty
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-backports-modules-jaunty

[/COLOR]When I tried the command "", this is the output:

[COLOR="Red"]thuynnbk@thuynnbk-laptop:~$ sudo lshw -C network
[sudo] password for thuynnbk:
*-network UNCLAIMED
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
*-network
description: Ethernet interface
product: L1 Gigabit Ethernet Adapter
vendor: Attansic Technology Corp.
physical id: 0
bus info: pci@0000:06:00.0
logical name: eth0
version: b0
serial: 00:24:8c:fd:3c:72
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.33 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 26:87:c9:e0:55:98
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

[/COLOR]
Please, help me. Any help would be appreciated.

---

### Post by Stochastic on 2009-08-02
Moved to Networking & Wireless.

---

