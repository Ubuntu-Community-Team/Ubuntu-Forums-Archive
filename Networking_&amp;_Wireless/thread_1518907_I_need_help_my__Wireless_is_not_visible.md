---
title: "I need help my  Wireless is not visible"
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by hoboy on 2010-06-27
I am using this.
Linux luc05-desktop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
When I install lucid my wireless worked out of box, but for some reason it has stopped working.
wireless Network is gray,by that I mean not active.

lucas05@lucas05-desktop:~$ sudo lshw -C network
[sudo] password for lucas05: 
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:24:21:10:ed:af
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.10 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:28 memory:f9e77000-f9e77fff ioport:b880(size=8) memory:f9e7e800-f9e7e8ff memory:f9e7e400-f9e7e40f
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:43:3a:98:89
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
lucas05@lucas05-desktop:~$

---

### Post by quixote on 2010-06-29
One thing that's happened to me (and more than once which is really embarrassing) is that the hardware wireless switch on the laptop was flipped to "off" accidentally.  Could that have happened on your machine?  

Have your tried turning the router off and back on and then rebooting your computer?

If none of those brute force methods work, I'm not sure what could cause a wireless card to go from fine to nonfunctioning without any other changes to the system.  Did this maybe happen after an update?

---

