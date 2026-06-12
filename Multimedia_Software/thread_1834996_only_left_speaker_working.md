---
title: "only left speaker working"
date: 2011-08-28
forum: Multimedia Software
---

### Post by blackone86 on 2011-08-28
Ive been trouble shooting for the past cpl hours and still cant figure it out. The left speaker on my laptop seems to work fine, the right has no sound. They were both working fine with windows 7 before. 

List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ryanblack@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, fast devsel, latency 0
    Memory at fc100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fc504800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f6000000-f7ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f8000000-f9ffffff
    Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: fa000000-fbffffff
    Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fc504c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=0c, sec-latency=56
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: fc200000-fc2fffff
    Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at 1c00 [size=8]
    I/O ports at 18d4 [size=4]
    I/O ports at 18d8 [size=8]
    I/O ports at 18d0 [size=4]
    I/O ports at 18e0 [size=32]
    Memory at fc504000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: medium devsel, IRQ 10
    Memory at 44000000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 1c20 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 2000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1050
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fa000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at fc204000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 48000000-4bfff000
    I/O window 0: 00005000-000050ff
    I/O window 1: 00005400-000054ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 32, IRQ 17
    Memory at fc206000 (32-bit, non-prefetchable) [size=2K]
    Memory at fc200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Sony Corporation VAIO VGN-NR120E
    Flags: bus master, medium devsel, latency 57, IRQ 18
    Memory at fc205000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

---

### Post by blackone86 on 2011-10-04
I never for sure figured this out, but im going to say that the issue is something with my computer and not with Ubuntu. My right speaker still does not work, my guess, a short. When plugging in an external device through the audio jac it plays fine in all speakers.

---

