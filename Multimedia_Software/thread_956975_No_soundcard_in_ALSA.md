---
title: "No soundcard in ALSA"
date: 2008-10-23
forum: Multimedia Software
---

### Post by vanweezy on 2008-10-23
I recently attempted to move to OSS in hopes of more compatibility with my soundcard (creative blaster x-fi).  it didn't work out as hoped, and i am not moving back to ALSA, however after reinstalling ALSA i get 

eric@beanie:~$ aplay -l
aplay: device_list:205: no soundcards found...

and then

eric@beanie:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 50200000-502fffff
	Prefetchable memory behind bridge: 0000000040000000-000000004fffffff
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 50100000-501fffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: 50400000-504fffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: 50500000-505fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 4080 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 4060 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 4040 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 4020 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at 50300000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 50000000-500fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 40b0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 40c8 [size=8]
	I/O ports at 40e4 [size=4]
	I/O ports at 40c0 [size=8]
	I/O ports at 40e0 [size=4]
	I/O ports at 40a0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: medium devsel, IRQ 10
	I/O ports at 4000 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Unknown device 2302
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 40000000 (64-bit, prefetchable) [size=256M]
	Memory at 50200000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 3000 [size=256]
	Expansion ROM at 50220000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (Secondary)
	Subsystem: ATI Technologies Inc Unknown device 2303
	Flags: bus master, fast devsel, latency 0
	Memory at 50210000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at 50100000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at 2000 [size=32]
	Capabilities: <access denied>

05:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs SB0790 X-Fi XA
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at 1000 [size=32]
	Capabilities: <access denied>

05:01.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
	Subsystem: Atheros Communications Inc. Unknown device 1151
	Flags: bus master, medium devsel, latency 168, IRQ 21
	Memory at 50000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

05:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at 50014000 (32-bit, non-prefetchable) [size=2K]
	Memory at 50010000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
so it is recognizing my soundcard, but when i attempt to load the drivers for the soundcard nothing changes? any ideas?

---

### Post by cariboo on 2008-10-23
Check here:

[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

For a driver for your sound card, you should also check Creative's web site to see if there are newer drivers.

Jim

---

### Post by vanweezy on 2008-10-23
eric@beanie:~$ sudo modprobe snd-ca0106
FATAL: Error inserting snd (/lib/modules/2.6.24-21-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-21-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-21-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-21-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-21-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.24-21-generic/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.24-21-generic/updates/alsa/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-21-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.24-21-generic/updates/alsa/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_rawmidi (/lib/modules/2.6.24-21-generic/updates/alsa/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_rawmidi
FATAL: Error inserting snd_ca0106 (/lib/modules/2.6.24-21-generic/updates/alsa/pci/ca0106/snd-ca0106.ko): Unknown symbol in module, or unknown parameter (see dmesg)
eric@beanie:~$

---

### Post by Syam_ on 2009-10-31
Have same audio issue upgrading from jaunty to karmic with ICH7 Audio Intel HDA :

```
aplay -l
aplay: device_list:223: no soundcards found...
```Just do a
```
modprobe snd-hda-intel
```Then it work for me.

Additionaly, install the gnome-alsamixer (because audio applet don't allow me to access any mixer as jaunty does ..)
```
gnome-alsamixer
```

---

