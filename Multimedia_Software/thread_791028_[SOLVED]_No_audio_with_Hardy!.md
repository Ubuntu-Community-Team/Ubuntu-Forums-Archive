---
title: "[SOLVED] No audio with Hardy!"
date: 2008-05-11
forum: Multimedia Software
---

### Post by drakos on 2008-05-11
I just got my hands on an older Gateway laptop, and I've been having problems getting the audio to work. I've tried to set-up PulseAudio but that fixed nothing. 

Here's the results of lspci -v

```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, fast devsel, latency 0
	Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 5
	I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 3
	Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=0a, sec-latency=32
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: e0200000-e02fffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Memory at 70000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Rioworks Unknown device 203a
	Flags: medium devsel, IRQ 10
	I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
	Memory at e0100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Rioworks Unknown device 2030
	Flags: medium devsel, IRQ 10
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at e0202000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 74000000-77fff000 (prefetchable)
	Memory window 1: 78000000-7bfff000
	I/O window 0: 00003400-000034ff
	I/O window 1: 00003800-000038ff
	16-bit legacy interface ports at 0001

02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at e0203000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 7c000000-7ffff000 (prefetchable)
	Memory window 1: 80000000-83fff000
	I/O window 0: 00003c00-00003cff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001

02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01) (prog-if 10 [OHCI])
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at e0201000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Rioworks Unknown device 202d
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at 3000 [size=256]
	Memory at e0201800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
	Subsystem: Intel Corporation Unknown device 2701
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at e0200000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

```

---

### Post by valjour on 2008-05-11
Did you look at this?

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Hope it helps.  My old Dell PC works great after making these changes.  Didn't have to tweak drivers but had a problem with the restricted Nvidia video.  Disabled the upgrade and all was go.

Kind of iffy with apt get, synaptic and update on Hardy.  I found I had to check with synaptic if apt get was successful.  Might try Java changes by itself (seperate).  Had to redo some of the gets in my terminal before the changes took hold even though I only got one error message while doing (almost) everything on this major advisory post.  Setting up Java is a nuisance.  If that "configuring" window appears close terminal, open new one and do the dpkg...-a as suggested below.  Don't do the ...-f one or you will wind up at the same place with the java window in your face.  Then use updater to install java bin and other updates it shows.

---

### Post by drakos on 2008-05-12
No luck as of yet, and I've confirmed that there is no audio with Gutsy as well, so it's most likely a hardware recognition problem. Ugh.

---

### Post by mc4man on 2008-05-13
i don't know if this will help - somewhat dated but anyway
[http://goesping.org/archives/2006/05/13/ubuntu-sound-on-gateway-laptop/](http://goesping.org/archives/2006/05/13/ubuntu-sound-on-gateway-laptop/)
read thru to bottom

---

### Post by drakos on 2008-05-13
I don't think it was just disabling External Amp that did it, I had tried that before and got no results, there was a lot of mixing and matching of Volume control options.

Anyway, with external, headphones began working, and with headphone jack sense off it all works now! Thanks for the helpful link.

---

