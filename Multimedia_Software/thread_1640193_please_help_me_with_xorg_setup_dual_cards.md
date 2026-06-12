---
title: "please help me with xorg setup dual cards"
date: 2010-12-07
forum: Multimedia Software
---

### Post by peruses on 2010-12-07
Hi, 

I hope I am in the right place I need help with my xorg.conf setup
I've been trying to do a manual setup folowing the instructions here [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) but don't realy understand what I am doing 

the details 
ubuntu 10.04
ati radeaon 3200hd onboard 
ati radeon 4350 in the pcie slot
one monitor on each card on vga conections
open scource drivers

current xorg.conf contents

Section "Device"
        Identifier      "Radeon 3200"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Device"
        Identifier      "Radeon 4350"
        Driver          "ati"
        BusID           "PCI:2:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic"
        Option          "DPMS"
        EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Radeon 4350"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"                
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen2"
        Device          "Radeon 3200"
        Monitor         "Generic"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection


lspci output

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
02:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
04:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
04:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

I've tried a few variations for the "server layout" section but so far every time I add that section and restart I get a splash screen on the left (onboard video) screen and then both monitors report no signal
oddly when I start up without the server layout section I get s splash screen on the left screen then the right screen comes up 

I hope someone can help this is about ready to drive me back to windows because I am incredibly more productive with two screens.

Thank you 
-Brice

---

### Post by pme 72 on 2010-12-07
I stumbled across a discussion awhile ago about two cards, three monitors. Perhaps it might be helpful?

[http://ubuntuforums.org/showthread.php?t=1489377](http://ubuntuforums.org/showthread.php?t=1489377)

Just an interested observer, I have no experience with such setups. Sorry I can not provide direct assistance.

---

