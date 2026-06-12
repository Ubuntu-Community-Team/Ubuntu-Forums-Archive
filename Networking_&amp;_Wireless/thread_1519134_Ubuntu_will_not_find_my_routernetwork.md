---
title: "Ubuntu will not find my router/network"
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by Synyster06Gates on 2010-06-27
I'm trying to get online on my laptop, I just installed Ubuntu 10.04 (Side by side with Windows 7.) I'm looking over the networking help files, as well as the troubleshooting and nothing seems to be working. 

[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)
From this troubleshooting guide it tells me to open the terminal and type the command "sudo lshw -C network" [FONT=Verdana]and when I do, it asks me for my password but when I try to type it, nothing comes up. So I run it without typing sudo. It says "*-network DISABLED" which in the troubleshooting guide means that my router is off, but I'm clearly online on this computer as of right now. What do I do here?[/FONT]

---

### Post by Synyster06Gates on 2010-06-28
Bump. Any help?

---

### Post by Iowan on 2010-06-28
When you enter the password, nothing will appear - it's a security thing...
The results may be slightly different using **sudo** versus without.

Drivers are always a possible problem - especially for wireless. **sudo lshw -C network** should reveal more information about your interfaces.

---

### Post by Synyster06Gates on 2010-06-29
> **Iowan said:**
> When you enter the password, nothing will appear - it's a security thing...
The results may be slightly different using **sudo** versus without.

Drivers are always a possible problem - especially for wireless. **sudo lshw -C network** should reveal more information about your interfaces.

```
 	 	 austin@austin-laptop:~$ sudo lshw -C network  
 [sudo] password for austin:  
   *-network                
        description: Ethernet interface  
        product: 88E8071 PCI-E Gigabit Ethernet Controller  
        vendor: Marvell Technology Group Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 15  
        serial: 00:1d:72:3f:24:4e  
        capacity: 1GB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair  
        resources: irq:27 memory:f0200000-f0203fff ioport:a000(size=256) memory:84000000-8401ffff(prefetchable)  
   *-network  
        description: Network controller  
        product: BCM4312 802.11b/g  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:05:00.0  
        version: 01  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: driver=b43-pci-bridge latency=0  
        resources: irq:17 memory:f0300000-f0303fff  
   *-network DISABLED  
        description: Wireless interface  
        physical id: 1  
        logical name: wlan0  
        serial: 00:1f:e2:a6:01:ce  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg  
 
```

---

