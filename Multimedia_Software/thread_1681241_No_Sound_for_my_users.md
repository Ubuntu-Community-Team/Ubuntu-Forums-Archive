---
title: "No Sound for my users"
date: 2011-02-03
forum: Multimedia Software
---

### Post by BCRailrodder on 2011-02-03
Hi,

Just upgraded to 10.04 on my desktop and while I have no problem playing sound (either mp3, ape, etc.) or sound contained in video, my other users are not able to get any sound at all (either mp3 or from youtube, etc.).

Any thoughts?

---

### Post by BCRailrodder on 2011-02-03
Just a further note - I just went and check one of my users while he was logged in and it doesn't appear as if the sound device is even recognized as it doesn't show up in System > Preferences > Sound.

---

### Post by BCRailrodder on 2011-02-07
bump

---

### Post by BCRailrodder on 2011-02-10
Hi again...

Ok, I think I narrowed down the problem a little bit.  I normally stay logged in and when my wife and son want to use the desktop, they switch users and log in.  Previously this was not a problem (of course) but since the upgrade it now appears that whoever logs in initially gets the sound.  If my wife logs in first after a reboot she has sound and if I switch users, I may or may not have sound.

When I lose sound, I can check the prefferences>Sound>Hardware tab and it shows no card.

Anyway, here's some info to start with:

```
kentc@shay:~$ sudo uname -r
2.6.32-28-generic

kentc@shay:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

kentc@shay:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, fast devsel, latency 0
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: [e4] Vendor Specific Information <?>
	Capabilities: [a0] AGP version 3.0
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: fc000000-feafffff
	Prefetchable memory behind bridge: e0000000-efffffff
	Kernel modules: shpchp

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
	Flags: fast devsel
	Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbf00000-fbffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Device 0151
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fea0 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Dell Device 0151
	Flags: medium devsel, IRQ 3
	I/O ports at eda0 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ee00 [size=256]
	I/O ports at edc0 [size=64]
	Memory at febffa00 (32-bit, non-prefetchable) [size=512]
	Memory at febff900 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
	Subsystem: Device 19f1:164c
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 3.0
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

02:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: AFAVLAB Technology Inc Device 0000
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at fbfdb800 (32-bit, non-prefetchable) [size=2K]
	Memory at fbfdc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at df00 [size=32]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: uhci_hcd

02:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at df20 [size=32]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: uhci_hcd

02:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20)
	Subsystem: VIA Technologies, Inc. USB 2.0
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at fbfdb700 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd

02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fbfe0000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at df40 [size=64]
	Capabilities: [dc] Power Management version 2
	Capabilities: [e4] PCI-X non-bridge device
	Capabilities: [f0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: e1000
	Kernel modules: e1000


```

I did modprobe for my drive (Intel8x0) and found it listed and since that didn't work, I followed the instructions for getting the alsa drivers from a fresh kernel.  While the purge and reinstall went fine it still didn't help.

Any suggestions, please??


Oh, I did check alsamixer and made sure everything was on and not muted

---

### Post by P4man on 2011-02-10
Wild guess; you had sound problems with your previous version and therefore removed pulseaudio? The upgrade didnt install it, but its now required to work with user switching? Try reinstalling pulseaudio.

---

### Post by BCRailrodder on 2011-02-10
Not that I am aware of but I'll give it a shot and let you know - thxs

Kent

---

### Post by P4man on 2011-02-11
Googled some more, looks like this bug:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654)

Post 47 has a solution

---

