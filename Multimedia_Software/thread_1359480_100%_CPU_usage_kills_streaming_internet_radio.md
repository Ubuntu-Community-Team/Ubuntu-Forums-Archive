---
title: "100% CPU usage kills streaming internet radio"
date: 2009-12-19
forum: Multimedia Software
---

### Post by cigtoxdoc on 2009-12-19
My favorite streaming Internet radio station (WQXR) does not have a Real Player stream only mp3 and acc+.  Use of any of VLC or other players starts out okay, but as soon as CPU usage hits 100%, the audio stops.  If I use Real Player and listen to WCPE, the audio will run as long as I like because CPU usgae stays low.  My CPU is Pentium III at 1 GHz (Coppermine) with 1 GB RAM.  Ubuntu version is 9.10.

I have another PC running Ubuntu 9.10 where CPU is 2.6 GHz, and it des not suffer from the CPU overload problem.

Can someone explain what is happening?

John

---

### Post by RedSingularity on 2009-12-19
What makes the CPU hit 100?  Is it VLC thats doing it?

---

### Post by cigtoxdoc on 2009-12-19
I don't know what is driving CPU to 100%.  I was listening to WQXR using [http://www.wqxr.org/popup_player/#station=wqxr](http://www.wqxr.org/popup_player/#station=wqxr) and had System Monitor going at same time.  Every once in a while, CPU usage would go to 100% for 30 to 60 seconds, the sound would stop and then restart when CPU drops.  After about 80 minutes, CPU usage went to 100% and stayed there.  I had to kill all Firefox and related processes and start over again to get sound.

Hopefully, the Ubuntu gurus are watching this post and will recommend a solution.

John

---

### Post by RedSingularity on 2009-12-19
Whats hogging the CPU though?  Firefox?

---

### Post by cigtoxdoc on 2009-12-19
About the only thing hogging CPU is firefox.

output of lspci -v with audio on is as follows:

john@john-desktop:~$ sudo lspci -v

[sudo] password for john: 

00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)

	Subsystem: ASUSTeK Computer Inc. Device 80e7

	Flags: bus master, medium devsel, latency 0

	Memory at f0000000 (32-bit, prefetchable) [size=128M]

	Capabilities: [a0] AGP version 2.0

	Capabilities: [c0] Power Management version 2

	Kernel driver in use: agpgart-via

	Kernel modules: via-agp



00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]

	Flags: bus master, 66MHz, medium devsel, latency 0

	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0

	Memory behind bridge: de000000-dfefffff

	Prefetchable memory behind bridge: dff00000-efffffff

	Capabilities: [80] Power Management version 2

	Kernel modules: shpchp



00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)

	Subsystem: ASUSTeK Computer Inc. Device 80e7

	Flags: bus master, stepping, medium devsel, latency 0

	Capabilities: [c0] Power Management version 2

	Kernel driver in use: parport_pc

	Kernel modules: parport_pc



00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])

	Subsystem: ASUSTeK Computer Inc. Device 80e7

	Flags: bus master, stepping, medium devsel, latency 32

	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]

	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]

	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]

	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]

	I/O ports at d800 [size=16]

	Capabilities: [c0] Power Management version 2

	Kernel driver in use: pata_via



00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)

	Subsystem: First International Computer, Inc. Device 1234

	Flags: bus master, medium devsel, latency 32, IRQ 11

	I/O ports at d400 [size=32]

	Capabilities: [80] Power Management version 2

	Kernel driver in use: uhci_hcd



00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)

	Subsystem: First International Computer, Inc. Device 1234

	Flags: bus master, medium devsel, latency 32, IRQ 11

	I/O ports at d000 [size=32]

	Capabilities: [80] Power Management version 2

	Kernel driver in use: uhci_hcd



00:04.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)

	Flags: medium devsel, IRQ 9

	Capabilities: [68] Power Management version 2

	Kernel modules: via686a, i2c-viapro



00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

	Subsystem: ASUSTeK Computer Inc. Device 80e7

	Flags: bus master, stepping, medium devsel, latency 32, IRQ 11

	I/O ports at b800 [size=256]

	Capabilities: [c0] Power Management version 2

	Kernel driver in use: C-Media PCI

	Kernel modules: snd-cmipci



00:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)

	Subsystem: D-Link System Inc Device 1301

	Flags: bus master, medium devsel, latency 32, IRQ 11

	I/O ports at b400 [size=256]

	Memory at dd800000 (32-bit, non-prefetchable) [size=256]

	Capabilities: [50] Power Management version 2

	Kernel driver in use: 8139too

	Kernel modules: 8139too



01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

	Subsystem: ABIT Computer Corp. Device 8f15

	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 5

	Memory at de000000 (32-bit, non-prefetchable) [size=16M]

	Memory at e0000000 (32-bit, prefetchable) [size=128M]

	[virtual] Expansion ROM at dffe0000 [disabled] [size=128K]

	Capabilities: [60] Power Management version 2

	Capabilities: [44] AGP version 3.0

	Kernel driver in use: nvidia

	Kernel modules: nvidia, nvidiafb



john@john-desktop:~$ 


does the above output look anything but NORMAL?

John

---

### Post by RedSingularity on 2009-12-19
Installing a newer firefox may solve the problem.  Do you know how to install from the repositories?

---

### Post by cigtoxdoc on 2009-12-19
Update manager had a new version of firefox this afternoon.  After i updated, version is 3.5.6.

is that the latest?

---

### Post by RedSingularity on 2009-12-19
Yeah that looks like the latest one........maybe a fresh install of firefox will do it.  Do you know how to do a fresh install?  Oh and do you have favorites saved that you want to keep?

---

### Post by cigtoxdoc on 2009-12-20
Thank you for your help.

Please let me know correct way to do this.  A simple motherboard repalcement has become a nightmare.  between time old board failed and new one installed, Ubuntu went from 9.04 to 9.10.  One would hope that a 1 GHz PIII CPU and 1 GB RAM should run well.

John

---

### Post by RedSingularity on 2009-12-20
Ok do the following...........

sudo apt-get autoremove --purge firefox*

Then..............

sudo rm -rf ~/.mozilla

When all that is done reboot and reinstall firefox with

sudo apt-get install firefox.

---

