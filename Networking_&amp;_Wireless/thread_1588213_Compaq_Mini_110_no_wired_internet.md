---
title: "Compaq Mini 110 no wired internet"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by Russell Burrows on 2010-10-04
I found what I did wrong!!
The netbook wired internet was working fine UNTIL I reset the internet modem! and then it no longer was able to connect to the internet.


I read several threads and did sudo lshw -C network

It said network disabled
ethernet interface
Atheros AR8132 lic gigabit ethernet adapter
physical id  0
bus info pci@0000 :02:00.0



sonia@sonia-laptop:~$ sudo lshw -C network 
[sudo] password for sonia: 
  *-network               
       description: Network controller 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 
       resources: irq:16 memory:feafc000-feafffff 
  *-network DISABLED 
       description: Ethernet interface 
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter 
       vendor: Atheros Communications 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: c0 
       serial: 18:a9:05:92:5c:f8 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=yes multicast=yes port=twisted pair 
       resources: irq:17 memory:febc0000-febfffff ioport:ec80(size=128) 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 0c:ee:e6:d4:aa:eb 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
sonia@sonia-laptop:~$ 




Please help.
Thank you for reading this.

---

### Post by bkratz on 2010-10-04
See if post 8 in this helps

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557130)

---

### Post by Russell Burrows on 2010-10-04
Is there an easier solution.

Or is there an image that has these drivers as re re downloading an image is a hassle but its adoable option versus me trying to do a command line fix.

Thank you.

---

### Post by Russell Burrows on 2010-10-04
Will this fix the problem of no wired internet?
Is WICD better than network manager?

sudo apt-get remove network-manager network-manager-gnome
sudo apt-get install wicd


Thank you.

---

