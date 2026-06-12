---
title: "Wired network not being detected"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by f35acepilot on 2009-10-12
I just installed Ubuntu 9.04, and I'm having some trouble getting the wired network to work. The network works great in Windows, but in Ubuntu it won't register and is greyed out in the network connections panel. I did have some trouble with it in Windows before, and I had to change the speed from automatic detection to 10 Mbps, but I don't see this option in Ubuntu. I'm using an Nvidia nForce Ethernet card, perhaps I need to install drivers for that but I haven't been able to find one as everyone says it should come installed with ubuntu.

I'm pretty new to linux, and don't know many commands past installing a tar file, so it would be great if you posted the exact commands I need to type. If you need any more information from me, just ask. I don't really know what you would need past what I wrote above. Thanks!

---

### Post by Iowan on 2009-10-13
Hmmm, greyed out doesn't sound too good...
From a terminal, check **lshw -C network** - post results.  That should show if the card is recognized, gets an alias (like eth0), and has a driver associated with it.

---

### Post by f35acepilot on 2009-10-23
Typing "lshw -C network" gets this:

```
*-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:22:68:37:67:34
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:18:79:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.5 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:7e:99:77:37:a9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by wikitywack on 2009-10-26
the following worked for me:
sudo su
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

---

