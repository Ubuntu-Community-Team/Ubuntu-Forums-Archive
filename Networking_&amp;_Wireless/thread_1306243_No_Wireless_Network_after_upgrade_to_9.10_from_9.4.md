---
title: "No Wireless Network after upgrade to 9.10 from 9.4"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by zoko9 on 2009-10-30
Hello all,
I am new to Ubuntu and I need help regarding my wireless which is the only way of connection. My old laptop Sony PCG FXA49 was connected from the very first second after formatting the disk and installed Ubuntu 9.4 for more than 4 months. I decided to upgrade to 9.10 Karmic and now wireless is dead. I have tried to research but it seems that everyone has a different way for fixing this. Any help will be greatly appreciated. My only resolution for now that I know is to go back to 9.4.
I am including an output of: 

sudo lshw -C network

  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 08:00:46:59:4a:df
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:10 ioport:1800(size=256) memory:e8004800-e80048ff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:9 memory:24000000-24001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:70:41:64:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by kayvortex on 2009-10-30
Try putting the installation CD in and then open up a terminal and entering:
```
sudo aptitude install bcmwl-kernel-source
```
and then restart.

Edit: if the package can't be found, then open up /etc/apt/sources.list with root privileges and remove the '#' from the start of the top line (with "deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release..." at the start) and then enter:
```
sudo aptitude update
```
before installing "bcmwl-kernel-source".

---

### Post by zoko9 on 2009-10-30
[COLOR=black][FONT=Courier New]I was able to run [/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo aptitude install bcmwl-kernel-source[/FONT][/COLOR]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[COLOR=black][FONT=Courier New]but when I used [/FONT][/COLOR]
[COLOR=black][FONT=Courier New][/FONT][/COLOR] 
[COLOR=black][FONT=Courier New]sudo aptitude update[/FONT][/COLOR]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[COLOR=black][FONT=Courier New]output is:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[COLOR=black][FONT=Courier New]Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]  Could not resolve 'security.ubuntu.com'[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]Reading package lists... Done  [/FONT][/COLOR]

---

### Post by suzypeppercorn on 2009-10-30
Everything worked great after a reboot when i followed your instructions, kayvortex. Thanks for the help :)

My wireless card is a broadcom 4311 rev02.

lspci outputs this for me:

```
$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: [COLOR="Red"]Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)[/COLOR]
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

---

