---
title: "Option GT Max 7.2 pcmcia drivers in Maverick AMD64"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by kacperpl1 on 2011-02-16
I have freshly installed and fully updated Maverick AMD64 and I'm trying to find out how to install the drivers for Option GT Max 7.2 HSDPA pcmcia modem, however all i can find is that it worked out of box in hardy(ages ago :p) and how to configure the dial ups for it.

Is there anyone that could help me with some hints how to do this?
My modem is recognised by lspcmcia as Cardbus Card
```
$ lspcmcia status
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:04.0)
  CardBus card -- see "lspci" for more information
```
but its not visible in lspci
```
$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
03:00.0 USB Controller: NEC Corporation Device 0031 (rev 43)
03:00.1 USB Controller: NEC Corporation Device 0031 (rev 43)
30:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
```

---

