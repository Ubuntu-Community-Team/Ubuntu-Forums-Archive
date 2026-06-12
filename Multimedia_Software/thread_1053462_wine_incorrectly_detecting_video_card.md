---
title: "wine incorrectly detecting video card"
date: 2009-01-28
forum: Multimedia Software
---

### Post by AndThenWhat on 2009-01-28
Ok,

So I am trying to run Spore using wine version 1.1.13.  However, wine has not been correctly detecting my graphics card.  Every time I try to start the game I get Spore's error 2001: 

"Sorry, your graphics card is below our min. spec. The game will not run. Please see the README for details. [2001]"

I don't understand why this is happening because I have an integrated Intel graphics card chipset capable of running the game on Windows.

lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

WINE Registry Keys I have tried:

```

VideoPciVendorID        27a2 (DWORD)
VideoPciDeviceID        8086 (DWORD)
VideoMemorySize         224 (STRING)
VertexShaderMode        hardware (STRING)
UseGLSL                 enabled (STRING)
PixelShaderMode         enabled (STRING)
OffscreenRenderingMode  fbo (STRING)
DirectDrawRenderer      opengl (STRING)

```

If I use the -safe flag it doesn't do anything other than output this in terminal:
```
fixme:thread:SetThreadIdealProcessor (0x80): stub
fixme:thread:SetThreadIdealProcessor (0x88): stub
```

Please I have no idea what else to try.  If anyone has fixed this please help.

---

### Post by AndThenWhat on 2009-01-29
*nudge*

---

### Post by FRuMMaGe on 2009-03-14
Same issue here. Any help would be awesome

---

