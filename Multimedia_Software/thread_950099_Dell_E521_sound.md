---
title: "Dell E521 sound"
date: 2008-10-16
forum: Multimedia Software
---

### Post by chrispy9 on 2008-10-16
I'm a newbie.  Spent days trying to get sound working.  Spent hours reading posts - either I don't understand them, or they don't seem to apply to my issues, or they don't solve the problem.

1st with the fancy sound card I bought new with my PC 18 months ago (it's a Creative Labs Sound Blaster X-Fi XtremeMusic, which, as far as I can tell, is not supported in Ubuntu 8.04)...

Then I purchased a Creative X-Fi USB sound device, since I read many posts that said it worked well...

Then I removed my Creative PCI-express hardware & removed my Creative USB device & enabled in BIOS the sound chip on my Dell Inspiron E521 MotherBoard (NVidia / SigmaTel STAC 92xx).

Only luck was with the USB device, but only in one program (Movie Player), and not in RhythmBox, or Skype, or Firefox, or any application on VMVirtual machines.

At this point, I'd like help making the STAC 92xx on my MotherBoard work, unless there's an easy fix for the PCI-Express device.

With the STAC 92xx:
System / Preferences / Sound: All set to "Autodetect".  "TEST" works, but NO SOUND.

Thanks...Chris.

---

### Post by dagoth_pie on 2008-10-16
Yeah, linux sound drivers are to be honest, a nightmare, go to your terminal and enter:
```
lspci
```
then post what it comes up with here

---

### Post by chrispy9 on 2008-10-16
> **dagoth_pie said:**
> Yeah, linux sound drivers are to be honest, a nightmare, go to your terminal and enter:
```
lspci
```
then post what it comes up with here

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
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation Unknown device 0424 (rev a1)
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

---

### Post by chrispy9 on 2008-10-17
here's the lspci -v

 lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: nVidia Corporation C51 Host Bridge
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 0
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 1
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 5
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 4
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: nVidia Corporation C51 Host Bridge
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 3
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 2
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f6000000-f9ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: nVidia Corporation Unknown device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Dell Unknown device 01ed
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Dell Unknown device 01ed
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: <access denied>

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Dell Unknown device 01ed
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01ed
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 01ed
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Unknown device 01ed
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e000 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Unknown device 01ed
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at cc00 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Dell Unknown device 01ed
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

03:00.0 VGA compatible controller: nVidia Corporation Unknown device 0424 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: nVidia Corporation Unknown device 050a
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f6000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at f9000000 [disabled] [size=128K]
	Capabilities: <access denied>

04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Unknown device 01ed
	Flags: bus master, fast devsel, latency 64, IRQ 20
	Memory at fddfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

---

### Post by dagoth_pie on 2008-10-17
```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

From the looks of things the onboard sound card is being detected and drivers being loaded for it, but not the creative one, getting the creative one to work is a little beyond me, but I can try help get the onboard one working.

After a quick search, I've found that the nVida sound cards tend to run on oss rather than alsa (see what I mean about sound drivers being a nightmare), you should be able to install oss from the package manager, then set all the settings in /system/prefence/sound to either autodetect or oss. Reboot (just because it seems that sound drivers dont change over til you reboot sometimes) then let me know how it goes

EDIT:
Or if your up for something a little more complicated
[http://jblevins.org/computing/linux/mcp51-alsa](http://jblevins.org/computing/linux/mcp51-alsa)
as far as I know, more applications run with the alsa sound system than oss, but it helps having a sound card that runs both

---

### Post by chrispy9 on 2008-10-19
Unfortunately, installing OSS from the Synaptic Package Manager did not help.  I think I may have already had OSS installed, as it appeared under system/preference/sound...but I installed 2 additional OSS components which had not been instaleld in Synaptic Package Manager, and re-booted.

I looked at the [http://jblevins.org/computing/linux/mcp51-alsa](http://jblevins.org/computing/linux/mcp51-alsa)
post, and I don't even begin to understand that.

I'm not opposed to spending money - I've already spent $400 to try to make Ubuntu work ($100 on books, $150 on a new hard drive so I didn't risk messing-up data on my old hard drive, $90 on a new video card since my other card wasn't compatible, and $60 on a USB audio device to try to fix the audio problem (but it didn't).

I'd gladly spend more money if I thought it would really get me up & running with Ubuntu.

But I hate to throw good money after bad...if I have to revert to Windows, I've wasted $400 already.

I can't even seem to get Networking running.  And I do tech support part-time for Windows users, so I've got a reasonable aptitude for learning computers.

Any idea how I can get ANY of the THREE sound cards (the PCI-express, USB, or Motherboard) I already own working...or any suggestions for a 100% PLUG-and-PLAY sound card appreciated...Chris.

---

### Post by dagoth_pie on 2008-10-19
```
gksu gstreamer-properties
```
 Try putting that into the terminal and messing with settings from there, theres a lot less of them to confuse you, hopefully you have some luck with it, but if not, first thing to check, make sure you have the "nvsound" module installed, you probably do by default but worth checking to make sure, also, just since it's nVidia, have you checked under system/administrating/hardware drivers to see if there are proprietory drivers for it, it's usually only graphics cards that do, but there is the occasional modem I've seen

---

