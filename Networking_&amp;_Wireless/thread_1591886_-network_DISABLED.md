---
title: "*-network DISABLED"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by dencolp on 2010-10-10
Hi Ubuntu Gurus,
 
Thanks in advance for your help.  I have used Linux and/or Ubuntu for about 3 hours total in my life.  I installed Ubuntu on my laptop and I am now trying to get my wireless network card working.
 
After typing "command lshw -C Network" I get the following output:
 
```

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:05:00.0"]pci@0000:05:00.0[/EMAIL]
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:08:00.0"]pci@0000:08:00.0[/EMAIL]
       logical name: eth0
       version: 02
       serial: 00:19:b9:76:14:dd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:7a:56:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```
 
Why is my "wireless interface" network marked as DISABLED?
How do I enable it?
 
Thanks,
D

---

### Post by sanderj on 2010-10-10
Why not use the GUI? In the upper right bar: what does the network icon say? What can you do when you right click on that icon?

And: the wifi switch is on, right?

---

### Post by Iowan on 2010-10-10
Just a guess, but it might be a driver issue - what chipset is in the machine?

---

### Post by bkratz on 2010-10-10
Here are several methods--see posts 3 and later. One depends on having wired connection and the other if no wired is available.

[http://ubuntuforums.org/showthread.php?p=9936499](http://ubuntuforums.org/showthread.php?p=9936499)

---

### Post by dencolp on 2010-10-12
Thanks all for your responses.

Hi sanderj: in the upper right bar, the wireless network icon has the red exclamation mark, indicating that it is not connected.  After right-clicking the upper-right network icon, everything is checked as it should be.

Hi bkratz: Enabling the driver via System, Administration, Hardware Drivers seems to have worked.

Thanks again.

---

