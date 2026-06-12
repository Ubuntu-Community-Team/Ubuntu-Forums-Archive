---
title: "No Sound, fresh install of Jaunty"
date: 2009-05-10
forum: Multimedia Software
---

### Post by Opeth115 on 2009-05-10
I jsut bought a new laptop and have installed ubuntu onto it, HP HDX Premium Series.  And everything works great minus the lack of sound.  I am going underway soon on a patrol to central and South America and would like to have my sound working so i can watch some movies in my rack ;P  Neither my headphone jacks or the speakers will put out any sound.  Any help is appreciated!  Here's my output of aplay -l and lspci -v

aplay -l :

```
matt@hp-ubu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v :

```
matt@hp-ubu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: d0000000-d2ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 80e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 80c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at dd005c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dd000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: dc000000-dcffffff
	Prefetchable memory behind bridge: 00000000d3000000-00000000d3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: db000000-dbffffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d4ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: da000000-daffffff
	Prefetchable memory behind bridge: 00000000d5000000-00000000d5ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d9000000-d9ffffff
	Prefetchable memory behind bridge: 00000000d6000000-00000000d6ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d8000000-d8ffffff
	Prefetchable memory behind bridge: 00000000d7000000-00000000d7ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 80a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 8080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 8060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 8040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at dd005800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2297
	I/O ports at 8108 [size=8]
	I/O ports at 8114 [size=4]
	I/O ports at 8100 [size=8]
	I/O ports at 8110 [size=4]
	I/O ports at 8020 [size=32]
	Memory at dd005000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: medium devsel, IRQ 11
	Memory at dd006000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 8000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: fast devsel, IRQ 11
	Memory at dd004000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 7000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation Device 1211
	Flags: bus master, fast devsel, latency 0, IRQ 2295
	Memory at dc000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, fast devsel, latency 0, IRQ 2296
	I/O ports at 5000 [size=256]
	Memory at d4010000 (64-bit, prefetchable) [size=4K]
	Memory at d4000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d4020000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d9000000 (32-bit, non-prefetchable) [size=2K]
	Memory at d9000d00 (32-bit, non-prefetchable) [size=128]
	Memory at d9000c80 (32-bit, non-prefetchable) [size=128]
	Memory at d9000c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d9000b00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: fast devsel, IRQ 16
	Memory at d9000a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d9000900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 361b
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d9000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

Everything is set to max in alsamixer and it seems to me as if my sound card is detected, so i'm unsure of what is actually wrong...

---

### Post by Triptol on 2009-05-10
Did you start alsmixer and check that your channels are unmuted?

---

### Post by Opeth115 on 2009-05-10
> **Triptol said:**
> Did you start alsmixer and check that your channels are unmuted?

Yes, everything in alsamixer is unmuted and set to max right now.

---

### Post by Opeth115 on 2009-05-10
anyone have any clue as to what's going on?

---

### Post by Triptol on 2009-05-11
Sorry to go back to alsamixer, I've found this German post: [http://forum.ubuntuusers.de/topic/kein-sound-intel-ich9-chipsatz/?highlight=g45#post-1589109](http://forum.ubuntuusers.de/topic/kein-sound-intel-ich9-chipsatz/?highlight=g45#post-1589109), the solution there was to flip the IEC958 switch. Might be one for you as well.

This bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364706)) also looks familiar. There are a couple of workarounds there, which might do it for you.

---

