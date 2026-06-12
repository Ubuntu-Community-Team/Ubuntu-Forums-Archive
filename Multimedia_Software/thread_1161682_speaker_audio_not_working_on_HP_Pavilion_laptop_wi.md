---
title: "speaker audio not working on HP Pavilion laptop with Jaunty x64"
date: 2009-05-16
forum: Multimedia Software
---

### Post by jdunn on 2009-05-16
I followed the comprehensive audio guide but haven't had much success.  I have an HP Pavilion laptop.  The sound worked through the speakers when I had Intrepid x64 installed.  I made a clean install-over of Jaunty x64 and now I can only get sound through the headphones.

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d0000000-d2ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a0e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at a0c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at df305c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3621
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at df300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: de200000-df2fffff
	Prefetchable memory behind bridge: 00000000d3000000-00000000d3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00006000-00007fff
	Memory behind bridge: dd200000-de1fffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d50fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: dc200000-dd1fffff
	Prefetchable memory behind bridge: 00000000d5100000-00000000d60fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: db200000-dc1fffff
	Prefetchable memory behind bridge: 00000000d6100000-00000000d70fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: da100000-db1fffff
	Prefetchable memory behind bridge: 00000000d7100000-00000000d80fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d9100000-da0fffff
	Prefetchable memory behind bridge: 00000000d8100000-00000000d90fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at a0a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at a080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at a040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at df305800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2296
	I/O ports at a108 [size=8]
	I/O ports at a114 [size=4]
	I/O ports at a100 [size=8]
	I/O ports at a110 [size=4]
	I/O ports at a020 [size=32]
	Memory at df305000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: medium devsel, IRQ 11
	Memory at df306000 (64-bit, non-prefetchable) [size=256]
	I/O ports at a000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: fast devsel, IRQ 11
	Memory at df304000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 9000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation Device 1211
	Flags: bus master, fast devsel, latency 0, IRQ 2294
	Memory at de200000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 2295
	I/O ports at 6000 [size=256]
	Memory at d4010000 (64-bit, prefetchable) [size=4K]
	Memory at d4000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d4020000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at da100000 (32-bit, non-prefetchable) [size=2K]
	Memory at da100d00 (32-bit, non-prefetchable) [size=128]
	Memory at da100c80 (32-bit, non-prefetchable) [size=128]
	Memory at da100c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at da100b00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: fast devsel, IRQ 16
	Memory at da100a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at da100900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at da100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

I also ran alsamixer and didn't see that any sound output was muted.

Please help.

---

### Post by jdunn on 2009-05-17
bump

---

### Post by jdunn on 2009-05-17
Bump

---

### Post by jdunn on 2009-05-17
bump

---

### Post by jdunn on 2009-05-18
So nobody has an HP Pavilion with sound issues in Jaunty?

---

### Post by vonti on 2009-05-18
I've got a HP Pavilion dv-5 1150ew and I had the same problem

> [http://ubuntuforums.org/showthread.php?t=1145561](http://ubuntuforums.org/showthread.php?t=1145561)

P.S.: HP doesn't go well withe the amd_64 edition of Ubuntu, or the 9.04, try downloading th 8.10, just like I did, and all your problem will be history.

---

### Post by droundy on 2009-06-24
I've got a similar problem with my HP computer, it has:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 30d4
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at ec004000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```

I can get sound out of the headphones jack, but nowhere else (in particular, the built-in speakers don't work).  Alas, I remain at a loss as to how to fix this.  The audio used to work just fine with Hardy... I wish I hadn't upgraded.  :(

---

### Post by vonti on 2009-06-26
It's Gentoo, but it should help
```

http://en.gentoo-wiki.com/wiki/HP_Pavilion_DV5_(PUMA)
```

---

### Post by diepes on 2010-10-09
HP EliteBook 8740w
$ sudo lspci -v
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
    Subsystem: Hewlett-Packard Company Device 1520
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at d4420000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

I had problem where mute was inverted but all worked, then upgraded to 10.10(pre) and got no sound.
2.6.35-22-generic #33-Ubuntu

Solution: Under sound prefrences (Just below volume  control)  on the [Output] tab i had to change the [Connector: ....] from Analog Output to Analog Speakers
 Now all is fine, can here sound and mute is not inverted anymore.

---

