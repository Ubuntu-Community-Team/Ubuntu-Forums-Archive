---
title: "ubuntu 8.10 (an oldie but a goodie) HDMI sound question"
date: 2011-11-29
forum: Multimedia Software
---

### Post by voncloft on 2011-11-29
Is there anyway to have sound with a NVIDIA GT 430 ZOTAC with its HDMI.

I downgraded from 11.10 because frankly it just doesn't "fit" me for my needs.

I put in aplay -l and i get:

nicholas@voncloft:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


However:
lspci-v shows:

nicholas@voncloft:~$ lspci -v
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. Device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: ASUSTeK Computer Inc. Device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device 815a
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at e400 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: nForce2_smbus
        Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at db004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ohci_hcd
        Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20)
        Subsystem: ASUSTeK Computer Inc. Device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device 812a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=256]
        Memory at db003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
        Subsystem: Device f043:815a
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: pata_amd
        Kernel modules: ata_generic, pata_acpi, pata_amd

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at d800 [size=16]
        Memory at db002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: sata_nv
        Kernel modules: ata_generic, pata_acpi, sata_nv

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at c400 [size=16]
        Memory at db001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: sata_nv
        Kernel modules: ata_generic, pata_acpi, sata_nv

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=128
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0000000-d7ffffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. Device 8141
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at db000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b000 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: forcedeth
        Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d8000000-daffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Kernel driver in use: k8temp
        Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1)
        Subsystem: ZOTAC International (MCO) Ltd. Device 4301
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=128M]
        Memory at c8000000 (64-bit, prefetchable) [size=32M]
        I/O ports at 9000 [size=128]
        [virtual] Expansion ROM at d9000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb

01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
        Subsystem: ZOTAC International (MCO) Ltd. Device 4301
        Flags: bus master, fast devsel, latency 0, IRQ 3
        Memory at da000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

05:06.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs Device 0021
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at a000 [size=32]
        Memory at d4000000 (64-bit, non-prefetchable) [size=2M]
        Memory at d0000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

I used the driver from the nvidia website a .bin file....it got the graphics up and running great...however there is no proprietary driver for this card.

Any advice at all would be great. If it can be done I would like to know how...if not then I guess i am stuck using speakers on the motherboard

---

### Post by BC59 on 2011-11-29
Yes but newer upgrades have solutions to older problems.

How you can now solve your problems if you are using a version which is not longer supported? 

And it's not only the problem of hardware incompatibilities but there are security issues as well. Not supported means you are alone with the hackers.

---

### Post by voncloft on 2011-11-29
I got tired of the GUI interface with ubuntu 11.10...also couldnt vnc the way I wanted...just created more problems than solutions in my honest opinion....any way to get this started

---

