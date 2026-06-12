---
title: "Video and sound problems"
date: 2011-09-14
forum: Multimedia Software
---

### Post by chezza on 2011-09-14
Hi 

I installed natty narwhal and now have video problem and a sound problem.

The pc is connected via hdmi
the graphics cards has built in sound and is a asus HD5450

The sound problem
There is no sound, I have checked its not muted and that the correct audio output is selected

aplay -l shows

[PHP]chez@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/PHP]sudo lspci shows

[PHP]00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 836d
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8445
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: f4000000-f41fffff
    Prefetchable memory behind bridge: 00000000f4200000-00000000f43fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 00000000f4400000-00000000f45fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at c480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at c800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at c880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at cc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe9fbc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
    I/O ports at c400 [size=8]
    I/O ports at c080 [size=4]
    I/O ports at c000 [size=8]
    I/O ports at bc00 [size=4]
    I/O ports at b880 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 03ca
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at feac0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at d000 [size=256]
    Expansion ROM at feaa0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
    Subsystem: ASUSTeK Computer Inc. Device aa68
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device 83fe
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

chez@HTPC:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 836d
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device 836d
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8445
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: f4000000-f41fffff
    Prefetchable memory behind bridge: 00000000f4200000-00000000f43fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 8179
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 00000000f4400000-00000000f45fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 8179
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at c480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at c800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at c880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at cc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe9fbc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 8179

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
    I/O ports at c400 [size=8]
    I/O ports at c080 [size=4]
    I/O ports at c000 [size=8]
    I/O ports at bc00 [size=4]
    I/O ports at b880 [size=16]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 03ca
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at feac0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at d000 [size=256]
    Expansion ROM at feaa0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
    Subsystem: ASUSTeK Computer Inc. Device aa68
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device 83fe
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-94-85-1b-14-da-e9-ff
    Kernel driver in use: atl1c
    Kernel modules: atl1c[/PHP]

What do i do ?


The video problem is that it plays about 50 x faster than it should do - it does look very sharp tho


Can any one help ?
thanks in advance

---

### Post by chezza on 2011-09-14
Actually I just realised I needed to activate a third party driver for the graphics card, which has (obviously) solved both problems.

I wish things were always this easy and I wish that this was the most braindead Id been all day .....

Thanks for taking the time to look

---

