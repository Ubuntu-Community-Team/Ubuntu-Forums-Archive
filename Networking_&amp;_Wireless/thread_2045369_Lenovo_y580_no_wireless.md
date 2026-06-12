---
title: "Lenovo y580 no wireless"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by calgreen on 2012-08-21
Can someone please help me get my wireless working?

---

### Post by Finnicella on 2012-08-21
Hi, first we must see you wireless card with this command:
```
sudo lshw -C network
```
then we can see if there are some blocks with:
```
sudo rfkill list all
```
and the last command to see if your wireless find the network:
```
iwconfig
```
Copy the output here with the tag "#"
Bye and sorry for my english. ;)

---

### Post by calgreen on 2012-08-21
OK Im back.

INPUT: sudo lshw -C network 
```
[sudo] password for chumrick: 
  *-network UNCLAIMED "     
       description: Ethernet controller 
       product: Atheros Communications 
       vendor: Atheros Communications 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 08 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi msix bus_master cap_list 
       configuration: latency=0 
       resources: memory:d3600000-d363ffff ioport:2000(size=128) 
  *-network UNCLAIMED 
       description: Network controller 
       product: Intel Corporation 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: c4 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress cap_list 
       configuration: latency=0 
       resources: memory:d3500000-d3501fff 
```
INPUT: sudo rfkill list all 
```
#0: ideapad_wlan: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: ideapad_bluetooth: Bluetooth 
	Soft blocked: no 
	Hard blocked: no 
```
INPUT: iwconfig 
```
lo        no wireless extensions. 
```

---

### Post by Finnicella on 2012-08-23
I can't see your wireless card.
Plese give this command:
```
lspci
```
You don't have drivers installed.
Go in system settings and try to see if in additional driver there are driver for your wireless card.
Does your ethernet connection work?
Bye:D

---

