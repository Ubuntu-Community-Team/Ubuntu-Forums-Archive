---
title: "Wireless not detecting/starting on 8.04"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by rahulugale on 2009-11-19
I could not find wireless network in network settings. So i could not able to use wireless network. I could see that my cards getting detected but not showing in when i go for configuring it. Even on right network icon there is no option for wireless network
Here are some details from my system

rahul@rahul-laptop:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.3 LTS"

rahul@rahul-laptop:~$ uname -r
2.6.24-24-generic

rahul@rahul-laptop:/lib/modules/2.6.24-24-generic$ lsmod | grep iwl
iwl3945                89840  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211

rahul@rahul-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

rahul@rahul-laptop:~$ lsusb 
Bus 005 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  

root@rahul-laptop:/lib/modules/2.6.24-24-generic# sudo lspci -v
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
Subsystem: Dell Wireless 1395 WLAN Mini-Card
Flags: bus master, fast devsel, latency 0, IRQ 11
Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [40] Power Management version 3
Capabilities: [58] Vendor Specific Information
Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Capabilities: [d0] Express Endpoint IRQ 0


root@rahul-laptop:/lib/modules/2.6.24-24-generic# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d8:19:c0
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=172.17.17.29 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

Please help

---

