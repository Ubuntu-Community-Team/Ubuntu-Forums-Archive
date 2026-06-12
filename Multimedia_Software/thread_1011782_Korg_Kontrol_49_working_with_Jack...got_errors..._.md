---
title: "Korg Kontrol 49 working with Jack...got errors...  Help??"
date: 2008-12-15
forum: Multimedia Software
---

### Post by cleverest on 2008-12-15
Any help appreciated....

I'm running Ubuntu 8.10 + Gnome + Compiz+fusion, etc...

When I launch Jack D, I choose SETUP, change interface to HW:1 (which if I click the little arrow it shows my KONTROL49

Am I supposed to choose anything in the MIDI box?  It is currently NON, but there is the choices:  RAW and SEQ

Anyways, with it as none...when I click START, I get this error in the MESSAGE Box:

> 
02:36:11.318 JACK is starting...
02:36:11.318 /usr/bin/jackd -dalsa -dhw:1 -r44100 -p1024 -n2
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
02:36:11.327 JACK was started with PID=31589.
[B]ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa[/B]
no message buffer overruns
02:36:11.330 JACK was stopped successfully.
02:36:11.330 Post-shutdown script...
02:36:11.330 killall jackd
jackd: no process killed
02:36:11.736 Post-shutdown script terminated with exit status=256.
**02:36:13.540 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server.** Please check the messages window for more info.

Also, in my CONNECTIONS setting of JACK, it does show my Korg 49 under the ALSA Tab as:  20:Kontrol49 and if I right click and click connect in the context menu it appears to connect and then says disconnect if I right click again as an option....

This is my lspci -v 

> 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at fe00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at fd00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fd900000-fd9fffff
	Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at fc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at fb00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at fa00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at f900 [size=8]
	I/O ports at f800 [size=4]
	I/O ports at f700 [size=8]
	I/O ports at f600 [size=4]
	I/O ports at f500 [size=16]
	I/O ports at f400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: medium devsel, IRQ 11
	Memory at fdffd000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at f200 [size=8]
	I/O ports at f100 [size=4]
	I/O ports at f000 [size=8]
	I/O ports at ef00 [size=4]
	I/O ports at ee00 [size=16]
	I/O ports at ed00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
	Subsystem: Device 19f1:0765
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at af00 [size=128]
	[virtual] Expansion ROM at fb000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd9fe000 (32-bit, non-prefetchable) [size=8K]
	[virtual] Expansion ROM at fde00000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at cf00 [size=8]
	I/O ports at ce00 [size=4]
	I/O ports at cd00 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at cb00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at bc00 [size=256]
	Memory at fdcff000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at fdb00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: ABIT Computer Corp. Device 1083
	Flags: bus master, medium devsel, latency 68, IRQ 21
	Memory at fdcfe000 (32-bit, non-prefetchable) [size=2K]
	Memory at fdcf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

04:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs Device 2002
	Flags: bus master, medium devsel, latency 64, IRQ 23
	I/O ports at bf00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

04:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
	Subsystem: Creative Labs Device 0040
	Flags: bus master, medium devsel, latency 0
	I/O ports at be00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp

04:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10)
	Subsystem: Creative Labs Device 0010
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fdcfd000 (32-bit, non-prefetchable) [size=2K]
	Memory at fdcf4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394


Any ideas?  I'm coming from a windows world, and I'm just learning the whole dual-boot...getting the essential working...and this midi controller is for sure, essential to me...

eventually I hope to have REASON 4 working in some capacity with it after I get Qsynth or the like working...but I just want to get the hardware working first, lol.

Any help greatly appreciated!

- Brett

---

### Post by cleverest on 2008-12-15
Sorry for the length of my post...I just wanted to be as clear as possible...if anyone could help me...anyone have a Korg Kontrol midi controller or something similar?

If you have any questions, please ask me....it's probably very simple, but I'm quite the Linux n00b still....

- Brett

---

