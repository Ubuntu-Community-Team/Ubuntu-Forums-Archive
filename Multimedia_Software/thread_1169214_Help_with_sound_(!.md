---
title: "Help with sound :(!"
date: 2009-05-24
forum: Multimedia Software
---

### Post by Kryptorious on 2009-05-24
I just upgraded and got the latest version and now my sound wont work :(

here is my aplay -l

[php]**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/php]

  

and here is my lspci -v

[php]00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
    Subsystem: Dell Device 0160
    Flags: bus master, fast devsel, latency 0
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
    Subsystem: Dell Device 0160
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
    Subsystem: Dell Device 0160
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
    Subsystem: Dell Device 0160
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
    Subsystem: Dell Device 0160
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
    Subsystem: Dell Device 0160
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-feafffff
    Prefetchable memory behind bridge: 20000000-200fffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 0160
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
    Subsystem: Dell Device 0160
    Flags: medium devsel, IRQ 3
    I/O ports at eda0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
    Subsystem: Dell Device 0160
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ee00 [size=256]
    I/O ports at edc0 [size=64]
    Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
    Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:06.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
    Subsystem: Creative Labs Device 1003
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at dfe0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: EMU10K1X
    Kernel modules: snd-emu10k1x

01:06.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
    Subsystem: Creative Labs Device 1003
    Flags: bus master, medium devsel, latency 64
    I/O ports at dfa8 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: Emu10k1_gameport
    Kernel modules: emu10k1-gp

01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
    Subsystem: Dell Device 8127
    Flags: bus master, fast devsel, latency 64, IRQ 17
    Memory at fe9fe000 (32-bit, non-prefetchable) [size=8K]
    Expansion ROM at 20000000 [disabled] [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b44
    Kernel modules: b44
[/php]


please help :(!! :KS

---

### Post by Kryptorious on 2009-05-25
oh if there is a site where i can download the last version befo 9.+ 

link plz

---

### Post by Kryptorious on 2009-05-25
anyone help plz?

---

