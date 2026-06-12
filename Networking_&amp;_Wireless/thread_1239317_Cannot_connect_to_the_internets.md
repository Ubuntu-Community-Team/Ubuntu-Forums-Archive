---
title: "Cannot connect to the internets"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by samsamson on 2009-08-13
I'm not sure if I should start a new thread, but I am having very similar problems to the original poster.

I have Windows XP on my Inspiron 530 desktop PC and have installed Ubuntu 9.04 using Wubi so that I could try it out. 

I have a wired internet connection which works perfectly in XP. There is not a wireless card in the PC.

In Ubuntu 9.04 it is "disconnected" 99% of the time, and randomly will work for around 30 seconds sometimes. 
 
Here are the results I got for **ifconfig -a** and **lshw -C network; **(hopefully they are correct since I'm brand new to this and not sure what I'm doing!)[B]



bash: ipconfig: command not found
mcnamee@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:9c:7e:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 latency=0 module=e1000e multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2a:e2:08:42:36:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



[/B]Any help would be much appreciated :)

---

### Post by Iowan on 2009-08-13
> **samsamson said:**
> bash: ipconfig: command not found
That'd be **ifconfig -a**. 
**ipconfig** is the Windows version.

---

### Post by bapoumba on 2009-08-13
Moved to its own thread (thanks Iowan ;)) and added [wubi] prefix.

---

