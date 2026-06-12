---
title: "Hell-o-va confused ATI FireGL V5000 Graphics card"
date: 2006-02-08
forum: Multimedia &amp; Video
---

### Post by shuttleworthwannabe on 2006-02-08
Hi Everyone; I have tried to get my HP Compaq nw8240 screen resolution configured but without sucess. I have followed many threads here and seem to be running into a wall each time I follow the step-by-step instructions. SO let me try and explain.

The graphics card is a ATI FireGL V5000 with resoultion of 1920x1200. I followed the instrcutions to install the ATI drivers from the ati website [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300")

Also first followed these instructions: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) 
just after the first step of removing the exsiting drivers, and reconfiguring my xserver (choosing ATI display as suggested on this site); I rebooted and tried to go back into ubuntu; at the loging screen the screen shrunk and started flickering with stripes across horizontal. I could hardly see the desktop; with much dexterity I managed to get the terminal window open and typed
```
 $ sudo dpkg-reconfigure xserver-xorg 
```

But kept getting error that I do not have xorg server installed. Apt-get install also does not recognize the package requested.

I was left with no option but to reinstall Ubuntu. Now this time around I chose VESA generic driver and chose conservative screen resolutions (max 1600x1200). All went well till I logged in. I am now in 1600x1200 res.

Here is my ```
 lspci -v
``` output
```
$ lspci -v
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c8800000-c8bfffff
        Prefetchable memory behind bridge: c0000000-c7ffffff
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
        Memory behind bridge: c8000000-c83fffff
        Capabilities: <available only to root>

0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=20, subordinate=20, sec-latency=0
        I/O behind bridge: 00000000-00000fff
        Memory behind bridge: 00000000-000fffff
        Prefetchable memory behind bridge: 0000000000000000-0000000000000000
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 3000 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 3020 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 3040 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at c8c00000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=32
        Memory behind bridge: c8400000-c87fffff
        Capabilities: <available only to root>

0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 3100 [size=256]
        I/O ports at 3200 [size=64]
        Memory at c8c01000 (32-bit, non-prefetchable) [size=512]
        Memory at c8c02000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: medium devsel, IRQ 22
        I/O ports at 3400 [size=256]
        I/O ports at 3500 [size=128]
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 3580 [size=16]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5653 (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company: Unknown device 0940
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at c0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 2000 [size=256]
        Memory at c8800000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:02:04.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
        Subsystem: Hewlett-Packard Company: Unknown device 12f6
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at c8400000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:02:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at c8401000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 80000000-803ff000 (prefetchable)
        Memory window 1: 80400000-807ff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:02:06.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032 (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at c8402000 (32-bit, non-prefetchable) [size=2K]
        Memory at c8404000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:02:06.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at c8408000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

0000:02:06.4 0805: Texas Instruments: Unknown device 8034
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at c840a000 (32-bit, non-prefetchable) [size=256]
        Memory at c840b000 (32-bit, non-prefetchable) [size=256]
        Memory at c840c000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:06.5 Communication controller: Texas Instruments: Unknown device 8035
        Subsystem: Hewlett-Packard Company: Unknown device 0934
        Flags: medium devsel, IRQ 11
        Memory at c840d000 (32-bit, non-prefetchable) [size=4K]
        Memory at c840e000 (32-bit, non-prefetchable) [size=4K]
        Memory at c840f000 (32-bit, non-prefetchable) [size=4K]
        Memory at c8410000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:10:00.0 Ethernet controller: Broadcom Corporation: Unknown device 167d (rev 11)
        Subsystem: Hewlett-Packard Company: Unknown device 0940
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root> 
```

and here is my xorg.conf file
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Is there some who could walk me through this installation? I am basically making a plea kneeling down..please. I have gone through a lot of trouble and feel like i am completely at a loss. I am very new at Linux/Ubuntu, but am a very quick learner.

Pleas ehelp..one more time.
SWB

---

### Post by shuttleworthwannabe on 2006-02-11
bumping this to get attention; been a while since I posted this.

---

### Post by renzokuken on 2006-02-22
you need to choose the fglrx driver, not the ATI one, after u have installed the fglrx driver by the methods laid down in these forums

---

### Post by William the Conquerer on 2006-02-22
I have a similar graphics card, (v3200) when you say use fglrx isn't there an open source version and an official ati version of fglrx?  or is it just the oss one and the ati one has been renamed ati/radeon...  some clarification would be appreciated =).

---

### Post by renzokuken on 2006-02-23
to be perfectly honest i dont know, 

here are both guides for you anyway

latest drivers   [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

more compatible and easier to install fglrx [http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111)

---

