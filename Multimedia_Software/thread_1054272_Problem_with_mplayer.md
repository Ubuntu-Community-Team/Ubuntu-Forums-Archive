---
title: "Problem with mplayer"
date: 2009-01-29
forum: Multimedia Software
---

### Post by gustavocm on 2009-01-29
Hi,

when o try to play a file with mplayer i get this

```
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  512x384  12bpp  25.000 fps  1060.3 kbps (129.4 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.

```

if I try to run with the "-vo x11" option then it plays, but plays very slowly.

What can i do to fix this?

thanks.

---

### Post by SqRt7744 on 2009-01-29
what graphics chip does your computer have? What specs in general? What version of Ubuntu? What's the output of 'lspci' in a terminal window?

---

### Post by gustavocm on 2009-01-29
Ubuntu 8.10. I have an ATI RADEON XPRESS 200M graphics card.

lspci:
```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by SqRt7744 on 2009-01-29
if you click on system->administration->hardware drivers, does it tell you that the recommended driver for your ATI is installed?

---

### Post by gustavocm on 2009-01-29
> **SqRt7744 said:**
> if you click on system->administration->hardware drivers, does it tell you that the recommended driver for your ATI is installed?

Yes. The driver is installed.

---

### Post by SqRt7744 on 2009-01-30
did you change anything in xorg.conf?
do films play smoothly with vlc or totem?

---

### Post by gustavocm on 2009-01-30
I did not change anything in xorg.conf.

Now i see that the video plays slow when the visual effects are enabled. When the visual effects are disabled it play smoothly. 

Anyway, i still can't understand why i have to set -vo x11.

---

### Post by SqRt7744 on 2009-01-31
well ati has released a new driver for your card, 9.1. You can get it from the homepage, or better: try installing envy-gtk which will help you with the install. The new driver supports 8.10 and is supposedly faster.

---

### Post by gustavocm on 2009-01-31
I tryed to install the new driver manually (as shown in the [wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually")) since the driver version in envyng is the same that i was using. 

I rebooted and couldn't log in. It was like it could not enter the "video mode". I had to use the ubuntu cd to uninstall the driver and install the old version with envyng. After that the login screen showed correctly.

---

### Post by whaevr on 2009-01-31
Ati has issues with playing videos when you have composite effects enabled, 9.1 was "supposed" to fix this but it didn't do it for me.

So from what you've said video plays fine with composite disabled..theres your fix. Until Ati gets around to fixing this problem.

---

### Post by Earl_Maroon on 2009-03-30
MPlayer is slow for me too, and I have the same graphics card. SMPlayer works well for me, however. Try that.

---

