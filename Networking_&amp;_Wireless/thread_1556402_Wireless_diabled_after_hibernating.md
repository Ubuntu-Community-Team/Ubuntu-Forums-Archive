---
title: "Wireless diabled after hibernating"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by dagarshali on 2010-08-19
Hi, 
I have a 64bit lucid lynx on my laptop. Yesterday, I was watching a video and didn't realize that i was on battery and it hibernated when the battery drained to critical levels. Since then, I see that the wireless is disabled. I have the physical wireless switch on my laptop turned on.

if i do sudo ifconfig wlan0 up I get
SIOCSIFFLAGS: Unknown error 132

The output of **rfkill list** is below


> 0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes  

the output of **lshw -C network**


> *-network DISABLED 
description: Wireless interface
product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:06:00.0
logical name: wlan0
version: 00
serial: 00:1e:65:28:73:30
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
resources: irq:32 memory:f4100000-f4101fff
*-network
description: Ethernet interface
product: NetLink BCM5784M Gigabit Ethernet PCIe
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:08:00.0
logical name: eth0
version: 10
serial: 00:23:8b:f2:51:1a
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.19 ip=192.168.1.106 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: irq:33 memory:f4000000-f400ff  

I also tried using the live cd and I still see that the wireless is disabled.

I installed wicd hoping that might resolve the issue and it did'nt. 

In the file /var/lib/Network-Manager/Network-Manager.state, wireless enabled=false. I set it to true and restarted the network manager and still no luck. When i checked the Network-Manger.state file again, wireless enabled was reset to false again.

I have no idea as how to get the wireless back. Could anybody please help me. 

I don't have a dual boot to see if i can get it enabled in windows. My bios has the wlan enable and disable. and it is set to enable.

Best regards,
vishwa

---

