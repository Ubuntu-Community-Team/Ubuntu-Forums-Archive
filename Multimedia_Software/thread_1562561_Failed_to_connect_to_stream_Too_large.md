---
title: "Failed to connect to stream: Too large"
date: 2010-08-27
forum: Multimedia Software
---

### Post by pivotraze on 2010-08-27
So I recently made the switch to Ubuntu 10.04 with my Gateway MX8734 laptop. I got some music transferred, but Exaile, Rythmbox, and MPlayer REFUSE to play it, all giving the same error, "Failed to connect to stream: Too large" With VLC, the titlebar just blinks for a second.

I followed the following thread: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) to try and fix it, but it failed. I do not know what else to do. It worked out of the box with my old desktop, not even YouTube audio works? Please help! I'm dying without music D:

Sound Card is SigmaTel HD Audio CODEC

Commands run in terminal to diagnose, feel free to read info:
> 

cody@cody-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
cody@cody-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d4100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d4200000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, fast devsel, latency 0
	Memory at d4180000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2000000-d3ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d4444000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d4000000-d40fffff
	Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 25
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at d4444400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
	Subsystem: Gateway 2000 Device 0685
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

03:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at d4004000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at d4007000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 44000000-47fff000
	I/O window 0: 00003400-000034ff
	I/O window 1: 00003800-000038ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at d4006000 (32-bit, non-prefetchable) [size=2K]
	Memory at d4000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at d4005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1


---

### Post by andrew.46 on 2010-08-27
Hi pivotraze,

I wonder if it is a pulse-audio problem... Can you try playing an mp3 from the commandline as follows:

```
mplayer -ao alsa my_file.mp3
```

where of course you should substitute the actual name of the file for my_file.mp3.

All the best,

Andrew

---

### Post by pivotraze on 2010-08-27
Amazingly, after a reboot, it just started working...

---

