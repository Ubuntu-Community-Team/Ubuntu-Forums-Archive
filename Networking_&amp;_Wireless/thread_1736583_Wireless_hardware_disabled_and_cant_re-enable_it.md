---
title: "Wireless hardware disabled and cant re-enable it"
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by motherboyxx on 2011-04-22
So I was cleaning my laptop and hit the wireless shortcut key on my Dell inspiron and disabled the wirless card.  The key will not turn it back on either (I maybe messed with the short cut but dont remember). In the network manager it says "wireless hardware disabled".  I am running 11.04 beta with gnome 3 shell. 

Here is from terminal 

dan@dan-Inspiron-1545:~$ sudo lshw -C network
[sudo] password for dan: 
PCI (sysfs)  
  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:63:13:6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff

It had been working fine till i hit the key.  

Is there a command to turn the card back on?

I am only slightly familiar with command windows and linux. 

Thanks guys

---

### Post by josephmills on 2011-04-22
could we Please see ```
rfkill list all
``` thanks

---

### Post by motherboyxx on 2011-04-22
Well I had restarted before I posted the first time but now after restarting again it is working fine.  Whatever, thanks though everybody

---

### Post by josephmills on 2011-04-22
glad to hear that it all worked out

---

### Post by Dent244 on 2011-04-24
ok so i am having the same probled as you, and i tried the code with it. I have a wired bridged connection for a temporary fix. this is the code from terminal

denton@Denton:~$ sudo lshw -C network
[sudo] password for denton: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:61:89:91
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.121 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:42 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:25:9b:bf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c2003fff
What can i do now? and also i am very new to this. i am running ubuntu 10.10

---

### Post by Dent244 on 2011-04-24
this is the results of the other code

denton@Denton:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

---

### Post by andrew.kunk on 2011-04-24
I had this same problem, and a pretty good solution is to go into:
System>Admin>Synaptic Package Manager

Search network-manager. mark it for removal

search wicd. mark it for installation

apply changes

---

### Post by josephmills on 2011-04-24
> **Dent244 said:**
> this is the results of the other code

denton@Denton:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```
rfkill unblock all 
``` or ```
rfkill unblock wifi
```

---

### Post by dineshs on 2011-04-25
> Hard blocked: yesDo you have a hardware switch for wifi ? If yes ensure that it is ON

---

