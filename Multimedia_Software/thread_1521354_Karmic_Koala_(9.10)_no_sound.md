---
title: "Karmic Koala (9.10) no sound"
date: 2010-06-30
forum: Multimedia Software
---

### Post by Idanwin on 2010-06-30
Hello,
I've recently installed Ubuntu 10.04 over a Ubuntu 7.04, but noticed sound was not working and every time I logged in a message saying:
[QUOTE="Ubuntu 10.04"]There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)[/QUOTE]
so I decided to try an older version because I've never liked to use latest versions (too many bugs).
But in 9.10 I had no sound either. I didn't have the error message anymore.
I also tested Mepis 8.5.01. Something really strange happened there: When I tested the sound, the computer said the sound worked and played a test sound. But no audio or video files I played myself made any sound, so I switched back to ubuntu 'cos Mepis couldn't get the home directory right.
Back on Ubuntu 9.10 I have been struggling with the sound problem for two days now. I've tried nearly everything I've found which looked similar enough without succes. I've had help from some people on the chat, but none of the links they gave me has helped me solve this problem.

«*lshw -C sound*» gives
```
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:e0320000-e0323fff
```

«*aplay -l*» gives
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

«*lspci -v*» gives
```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at e0200000 (32-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 2440 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e0325900 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: heci
	Kernel modules: heci

00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
	Subsystem: Intel Corporation Device 0001
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at e0300000 (32-bit, non-prefetchable) [size=128K]
	Memory at e0324000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 20c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 20a0 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 2080 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at e0325400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Intel Corporation Device 2114
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at e0320000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: e0100000-e01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 2060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 2040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 2020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at e0325000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
	Memory behind bridge: e0000000-e00fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 2438 [size=8]
	I/O ports at 2454 [size=4]
	I/O ports at 2430 [size=8]
	I/O ports at 2450 [size=4]
	I/O ports at 2410 [size=16]
	I/O ports at 2400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: medium devsel, IRQ 10
	Memory at e0325800 (32-bit, non-prefetchable) [size=256]
	I/O ports at 2000 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 2428 [size=8]
	I/O ports at 244c [size=4]
	I/O ports at 2420 [size=8]
	I/O ports at 2448 [size=4]
	I/O ports at 20f0 [size=16]
	I/O ports at 20e0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at 1018 [size=8]
	I/O ports at 1024 [size=4]
	I/O ports at 1010 [size=8]
	I/O ports at 1020 [size=4]
	I/O ports at 1000 [size=16]
	Memory at e0100000 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
	Kernel driver in use: pata_marvell

06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at e0004000 (32-bit, non-prefetchable) [size=2K]
	Memory at e0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394
```


Boxes and headphones are plugged in correctly (sound worked on 7.04 and I didn't change anything).
The volume is turned on and I've changed the settings to nearly every possibility.

---

