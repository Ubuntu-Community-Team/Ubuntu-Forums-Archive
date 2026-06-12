---
title: "How to connect TV from laptop via s-video?"
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by RamR on 2008-03-29
My first post here.

I've been using Ubuntu 7.10 for less than a week and find myself at a loss after days of searching for info.

I want to connect from my laptop to my TV via the s-video cable as I was able to in Windows XP. I have searched several forums unsuccessfully and am now looking for some help.

My laptop is an Acer Travelmate 290 with Intel Extreme Graphics card.

Here is my report from lspc -v. Hopefully someone can guide me to success as I really like this OS but having the TV connected is something that is really important to me. Thank you in advance.

```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at b0000000 (32-bit, prefetchable) [size=128M]
        Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at e000 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: fast devsel
        Memory at 50000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at 58000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1200 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1600 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1700 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at f0080000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=05, sec-latency=32
        I/O behind bridge: 0000c000-0000dfff
        Memory behind bridge: e0000000-efffffff
        Prefetchable memory behind bridge: a0000000-afffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1100 [size=16]
        Memory at 58080000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: medium devsel, IRQ 255
        I/O ports at 1400 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0021
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at e100 [size=256]
        I/O ports at e200 [size=64]
        Memory at f0080400 (32-bit, non-prefetchable) [size=512]
        Memory at f0080600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: medium devsel, IRQ 10
        I/O ports at e300 [size=256]
        I/O ports at e400 [size=128]
        Capabilities: <access denied>

01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, stepping, medium devsel, latency 128, IRQ 10
        Memory at e0001800 (32-bit, non-prefetchable) [size=2K]
        I/O ports at c100 [size=128]
        Capabilities: <access denied>

01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, medium devsel, latency 128, IRQ 10
        I/O ports at c000 [size=256]
        Memory at e0001000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corporation MIM2000/Centrino
        Flags: bus master, medium devsel, latency 128, IRQ 10
        Memory at e0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 003d
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at e0002000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: a0000000-a3fff000 (prefetchable)
        Memory window 1: e4000000-e7fff000
        I/O window 0: 0000c400-0000c4ff
        I/O window 1: 0000c800-0000c8ff
        16-bit legacy interface ports at 0001

```

And here is my xorg

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by warp99 on 2008-03-29
I believe that work on the tv-out for the Intel 855GM has not been done since Intel decided to release the specifications:

[http://lists.freedesktop.org/archives/xorg/2007-August/026902.html](http://lists.freedesktop.org/archives/xorg/2007-August/026902.html)

That may change over time I would check with the developers to see if this is going to happen:

[http://www.intellinuxgraphics.org/index.html](http://www.intellinuxgraphics.org/index.html)

---

### Post by RamR on 2008-03-29
Does this mean that it is not possible at the moment to connect my laptop to my TV as a second screen?  This would be truly disappointing as the process was so easy in Windows XP.

---

### Post by linksolo74 on 2008-03-29
TV-output is one of the pitfalls of linux. I could never get it to work right myself. so i just have to reboot into windows for tv-output.

---

### Post by RamR on 2008-03-29
The thread at this link [http://ubuntuforums.org/showthread.p...t=dual+monitor](http://ubuntuforums.org/showthread.p...t=dual+monitor) seems to hold some promise.  I have been able to set up a clone screen with my TV through an s-video cable.  No luck with the dual screen though.  I have posted my xorg results for both and hope someone might be able to find my error in the latter one.

---

