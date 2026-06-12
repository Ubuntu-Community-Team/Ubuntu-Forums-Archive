---
title: "Dlink  DWA-130 won't work"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by dannyl2005 on 2009-10-26
Im trying to use my dwa-130 rev D on linux to be able to use wireless-n but linux isn't detecting it. I'm using thing on my laptop. I've installed ndiswrapper and installed xp driver also it's showing that hardware is present but after restarting ubuntu 9.10 it's still not picking it up.
  
Ubuntu only picks up the wireless adapter that is built in with my laptop... would my built in wireless adapter be causing a problem?

---

### Post by bkratz on 2009-10-26
> **dannyl2005 said:**
> Im trying to use my dwa-130 rev D on linux to be able to use wireless-n but linux isn't detecting it. I'm using thing on my laptop. I've installed ndiswrapper and installed xp driver also it's showing that hardware is present but after restarting ubuntu 9.10 it's still not picking it up.
  
Ubuntu only picks up the wireless adapter that is built in with my laptop... would my built in wireless adapter be causing a problem?



What do you see it when you do a lsusb and lspci in terminal? I use the version A of the DWA130 with Ndiswrapper and would be happy to help; I'm still on 9.04 but I suspect there will be little difference. I'm pretty sure Network manager can only manage one interface at a time. Do you have a switch to turn off the internal, or can you access the bios and turn it off there?
Please post the output of  "sudo lshw -C network"  Are you on a 32 bit sytem or 64?   You can see this with "uname -mr".

---

### Post by dannyl2005 on 2009-10-26
I'm using 32bit , I've tried switching off the internal wireless adapter but still didn't work.

When using lsusb i get:

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 07d1:3a0f D-Link System 
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


when using lspci i get:

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

My internal adapter is probably showing because im using it right now.

lshw -c network:

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:60:77:75
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:3000(size=256) memory:c9010000-c9010fff(prefetchable) memory:c9000000-c900ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:63:5a:b3:07
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.5.106 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:cb100000-cb10ffff


* I used these commands with the internal wifi on and the usb dwa 130.

---

### Post by bkratz on 2009-10-26
I am going to have to do some research on this, perhaps someone else knows off the top, anyway a quick search showed this up

[http://ubuntuforums.org/showthread.php?t=1253240&highlight=turn+internal+wireless](http://ubuntuforums.org/showthread.php?t=1253240&highlight=turn+internal+wireless)

---

### Post by bkratz on 2009-10-26
> **bkratz said:**
> I am going to have to do some research on this, perhaps someone else knows off the top, anyway a quick search showed this up

[http://ubuntuforums.org/showthread.php?t=1253240&highlight=turn+internal+wireless](http://ubuntuforums.org/showthread.php?t=1253240&highlight=turn+internal+wireless)



Found this one ( kinda old but doesn't seem dated) anyway look here

[http://ubuntuforums.org/showthread.php?t=512020](http://ubuntuforums.org/showthread.php?t=512020)

here another

[http://www.uluga.ubuntuforums.org/showthread.php?p=8070785](http://www.uluga.ubuntuforums.org/showthread.php?p=8070785)

---

### Post by dannyl2005 on 2009-10-26
I blacklisted ath5k to disable my internal adapter then restarted the computer but still nothing

---

### Post by bkratz on 2009-10-26
> **dannyl2005 said:**
> I blacklisted ath5k to disable my internal adapter then restarted the computer but still nothing

When you do your "lshw -C network" command does the usb controller show up now, or does it still show the old one, but no driver?

---

