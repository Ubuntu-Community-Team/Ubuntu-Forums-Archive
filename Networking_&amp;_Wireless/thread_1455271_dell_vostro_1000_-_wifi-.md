---
title: "dell vostro 1000 - wifi-"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by marc88 on 2010-04-15
Hello, this is my first message in the forum, and as you see my English is not perfect!

I installed on my Dell Vostro 1000 Ubuntu 9.10 (final), but I have no way to connect internet. The card is Broadcom 1390 wlan mini.

I state that I have very little familiarity with Linux

Does anyone know how to solve the problem?


```
marco@marco-laptop:~$ ipconfig 
No command 'ipconfig' found, did you mean: 
 Command 'tpconfig' from package 'tpconfig' (universe) 
 Command 'iwconfig' from package 'wireless-tools' (main) 
 Command 'ifconfig' from package 'net-tools' (main) 
ipconfig: command not found 
marco@marco-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10) 
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
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
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M] 
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) 
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01) 
marco@marco-laptop:~$
```

Thanks

---

### Post by ublintu on 2010-04-16
Hi,
I have dell vostro 1000 as well
wifi: (I used this, the first one)  [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865) 
        [http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

Is everything fine with your ati card?

---

### Post by marc88 on 2010-04-18
It is the error that the driver Broadcom..


[http://img717.imageshack.us/img717/299/screenshot4de.png](http://img717.imageshack.us/img717/299/screenshot4de.png)


[http://img695.imageshack.us/img695/4610/screenshot3lu.png](http://img695.imageshack.us/img695/4610/screenshot3lu.png)

---

### Post by marc88 on 2010-04-21
What do you recommend?

---

### Post by ublintu on 2010-04-21
It's working for me and I just followed the instructions. I don't know. Did you use a clean install?

---

