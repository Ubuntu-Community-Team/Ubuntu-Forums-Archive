---
title: "Need help urgently with Berlkin F5D7001uk"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by sammygone on 2010-01-17
Hi

I have basically no computer knowledge, and I have recently downloaded Ubuntu 9.0. 

Before I had Windows XP, and I used a Berlkin f5d7001uk, it get wireless internet, and it worked fine with Windows. But it doesnt seam to work with Ubuntu. It recognises it, but it doesnt allow me to run it.

I have no idea what to do!! or how to make it work

---

### Post by bkratz on 2010-01-17
> **sammygone said:**
> Hi

I have basically no computer knowledge, and I have recently downloaded Ubuntu 9.0. 

Before I had Windows XP, and I used a Berlkin f5d7001uk, it get wireless internet, and it worked fine with Windows. But it doesnt seam to work with Ubuntu. It recognises it, but it doesnt allow me to run it.

I have no idea what to do!! or how to make it work



Have a look at this thread

[http://ubuntuforums.org/showthread.php?t=1182269&highlight=f5d7001uk](http://ubuntuforums.org/showthread.php?t=1182269&highlight=f5d7001uk)

---

### Post by sammygone on 2010-01-18
Hi

the link wasn't very helpful. I'm still having problems with connecting to the internet

---

### Post by bkratz on 2010-01-18
> **sammygone said:**
> Hi

the link wasn't very helpful. I'm still having problems with connecting to the internet

I guess the first thing we have to do is determine the chipset used
go to the terminal
Applications>>Accessories>>Terminal

and post the outputs (copy/paste) back here for

lspci
that is LSPCI in lowercase) 
and
sudo lshw -C network
(LSHW)

---

### Post by sammygone on 2010-01-18
for lspci this was the output was

samah@samah-desktop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02) 
00:01.0 PCI bridge: Intel Corporation 82946GZ/PL/GL PCI Express Root Port (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] 
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE] 
02:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 
02:03.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14) 
samah@samah-desktop:~$  



and for the other one the output was

samah@samah-desktop:~$ sudo lshw -C network 
[sudo] password for samah:  
  *-network:0              
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 1 
       bus info: pci@0000:02:01.0 
       version: 03 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 
       resources: irq:18 memory:fdefe000-fdefffff 
  *-network:1 
       description: Ethernet interface 
       product: 88E8001 Gigabit Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 3 
       bus info: pci@0000:02:03.0 
       logical name: eth0 
       version: 14 
       serial: 00:15:58:66:7d:76 
       capacity: 1GB/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=23 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair 
       resources: irq:16 memory:fdef8000-fdefbfff ioport:ee00(size=256) memory:fdd00000-fdd1ffff(prefetchable) 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:11:50:3b:5d:af 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
samah@samah-desktop:~$

---

### Post by bkratz on 2010-01-18
since

Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 

See this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

The second half

---

### Post by bkratz on 2010-01-18
Or
a completely open source version

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)



Gave the wrong one above

[http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318)

---

