---
title: "HP analog TV Tuner"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by doobiemilkshake on 2007-07-02
Hi,
 I just threw ubuntu on my HP dv5140us about a week ago.  However, I can't figuere out how to use the tv card that came with it.  On the device it says HP ExpressCard Analog TV Tuner, HP's site calls it  Yuan EC680 Analog TV Tuner Driver.  I threw mythtv on my computer with no success.  I'm pretty sure that this is due to the fact that the expressCard slot probably isn't installed.  Any help, suggestions, or links would be appreciated, thank you!

Heres a lspci, if it helps
lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by mailson on 2007-07-22
I have the same issue.
Is it working now or still?

---

### Post by dsiddens on 2007-09-11
HP Pavilion dv8000 laptop, AMD64, Feisty, and EC860 Analog TV Tuner.  Looking for solutions to get it working.  -Doug

---

### Post by reckless2k2 on 2007-09-11
i don't see the tv tuner in your lspci. is it not plugged in?

---

### Post by shadowhywind on 2007-10-04
I have the same card, and wondering if anyone was able to get it to work yet?

---

### Post by vcinfio on 2007-10-21
i have the same computer, same card...

HP dv5140us
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

I think that the key is configuring MythTV if anybody knows how

---

### Post by br8kpoint on 2008-02-22
> **reckless2k2 said:**
> i don't see the tv tuner in your lspci. is it not plugged in?

Actually, this card shows up in lsusb listing. It attaches on the usb bus. I am at the beginning stage of trying to get this to work as well.

lsusb listing:

mike@mike-laptop:~$ lsusb
Bus 003 Device 011: ID 1164:0601 YUAN High-Tech Development Co., Ltd 
Bus 003 Device 009: ID 046d:c216 Logitech, Inc. Dual Action Gamepad
Bus 003 Device 007: ID 045e:00db Microsoft Corp. 
Bus 003 Device 010: ID 0bc2:2000 Seagate RSS LLC 
Bus 003 Device 008: ID 0471:0815 Philips 
Bus 003 Device 002: ID 059f:0951 LaCie, Ltd 
Bus 003 Device 003: ID 0409:0050 NEC Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000

---

### Post by stingrayl on 2008-06-08
So anyone got sucess with this card i have the same issue in a DV9580us and a Analog/Digital TvTunner - by Hauppauge...

no luck with MythTV.

---

