---
title: "A real sound stumper"
date: 2009-09-24
forum: Multimedia Software
---

### Post by Illender on 2009-09-24
Okay, here we go.
I run (Ed)Ubuntu 9.04 Jaunty Jackalope on a compaq evo n620c. I had sound troubles before where no sound worked at all, speakers or headphones(cept for the live cd) and after failing to correct it using the help presented on this forum(uninstalled packages, played with alsa, upgraded alsa), I just reinstalled. Problem solved.

So I thought.

So this time around I was paranoid about installing any upgrades or packages as I had no idea why sound quite working.
Well, one day I booted up and BAM! No sound. Huh, I said, lemme check the live cd.  Yep, it works. Played a little with alsa and found that sound works through the headphone jack,but not through the speakers. Left some music playing and changed option after option to no avail.

Using the comprehensive sound diagnostic thread advice I did some checking:
```

illender@maxitronj:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And, 
```

illender@maxitronj:~$ sudo lspci -v 
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: bus master, fast devsel, latency 0
	Memory at b0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: [e4] Vendor Specific Information <?>
	Capabilities: [a0] AGP version 2.0
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 90200000-902fffff
	Prefetchable memory behind bridge: 98000000-9fffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 38c0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 38e0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 3c00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: bus master, medium devsel, latency 0, IRQ 10
	Memory at a0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=0080
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=32
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 90000000-901fffff
	Prefetchable memory behind bridge: 30000000-39ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 3c20 [size=16]
	Memory at 3a000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: medium devsel
	I/O ports at 1200 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 3000 [size=256]
	I/O ports at 3880 [size=64]
	Memory at a0100000 (32-bit, non-prefetchable) [size=512]
	Memory at a0180000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: medium devsel, IRQ 11
	I/O ports at 3400 [size=256]
	I/O ports at 3800 [size=128]
	Capabilities: [50] Power Management version 2
	Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: bus master, stepping, 66MHz, medium devsel, latency 66, IRQ 10
	Memory at 98000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at 90200000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at 90220000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
	Capabilities: [50] Power Management version 2
	Kernel modules: radeonfb

02:06.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
	Memory at 90080000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 3c000000-3ffff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:06.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
	Memory at 90100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 34000000-37fff000 (prefetchable)
	Memory window 1: 40000000-43fff000
	I/O window 0: 00004800-000048ff
	I/O window 1: 00004c00-00004cff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
	Subsystem: Compaq Computer Corporation Device 0058
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at 90000000 (64-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at 38000000 [disabled] [size=64K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
	Kernel driver in use: tg3
	Kernel modules: tg3

04:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 22, IRQ 10
	Memory at 40000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 4800 [size=32]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: uhci_hcd

04:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 22, IRQ 10
	Memory at 40000100 (32-bit, non-prefetchable) [size=256]
	I/O ports at 4820 [size=32]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: uhci_hcd

04:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20)
	Subsystem: VIA Technologies, Inc. USB 2.0
	Flags: bus master, medium devsel, latency 22, IRQ 10
	Memory at 40000200 (32-bit, non-prefetchable) [size=256]
	Memory at 40000300 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd

illender@maxitronj:~$ 


```

So. 
Once again I'm beating my head against a silent wall, and grow tired of having to use headphones to listen to my laptop(the cord is short and this thing doubles as my MP3 player while doing housework).
I will reinstall one more time as a last resort, and if it happens again I'm quitting, and going back to windows<gag>.

---

### Post by mudguts on 2010-02-23
That is really bizarre.
I have a Compaq Evo n620c and the sound worked out of the box with 9.04

when you press the volume keys on the front, does the overlay of the volume pop up in the top right?

let me know if you need to see my config files or anything.

---

### Post by drauchomyn on 2010-02-24
Try looking at this troubleshooting guide and follow instructions:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Also, look at this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

