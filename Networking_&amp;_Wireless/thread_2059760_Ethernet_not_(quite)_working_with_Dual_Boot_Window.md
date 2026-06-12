---
title: "Ethernet not (quite) working with Dual Boot Windows/Precise"
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by ecoulter on 2012-09-18
I've got an Asus laptop running Ubuntu 12.04 and Windows 7 on separate partitions. Ethernet/wireless works fine if I do the following:
1. Boot into Windows (first thing in the morning)
2. Boot into Ubuntu (first thing in the morning or a long time after using windows)
3. Boot into Windows immediately after being in Ubuntu. 

However, if I have booted into Windows, shut down, and restart into Ubuntu (with only a short pause), something funny happens with the ethernet card, and I can't access the internet. In ifconfig, the only change is in the line RX packets, there will by some small number of errors, and frame = number of errors. 

If instead of restarting into ubuntu, I:
power down (after being in windows),
remove the battery and AC power cord,
hold down the power button for ~20 seconds,
and THEN boot into Ubuntu, everything works fine. Somehow letting everything discharge works.(resetting interfaces between BIOS and Hardware? [http://www.sevenforums.com/hardware-devices/199389-shut-down-computer-remove-all-power-sources-hold-down-power-button.html](http://www.sevenforums.com/hardware-devices/199389-shut-down-computer-remove-all-power-sources-hold-down-power-button.html))  

Is anyone familiar with something like this, or knows a way that I can change my linux/windows settings to be able to switch between windows and linux without the hardware reset rigmarole?

Meant to include this, as it may be helpful:
lshw -c network ouput:
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:23:54:5f:4e:0f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.4 duplex=full ip=128.186.7.165 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 memory:f9ffcc00-f9ffcc7f ioport:cc00(size=128)
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:43:71:c1:4f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-30-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fdff0000-fdffffff

---

