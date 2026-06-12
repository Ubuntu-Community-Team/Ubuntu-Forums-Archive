---
title: "Couldn't play sound from my internal speaker card"
date: 2011-05-04
forum: Multimedia Software
---

### Post by shyamkkhadka on 2011-05-04
[SIZE=3]Hi all,
I am using Ubuntu 11.04 in my Lenovo Device 3047. I can listen sound using earphone. But I couldn't listen through internal speakers. 
The output after command "lspci -v"  is
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: Lenovo Device 3047
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3047
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fc000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1c70 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
    Subsystem: Lenovo Device 3047
    Flags: bus master, fast devsel, latency 0
    Memory at fc400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
    Subsystem: Lenovo Device 3047
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at fc524000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03) (prog-if 85 [Master SecO PriO])
    Subsystem: Lenovo Device 3047
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    I/O ports at 1c88 [size=8]
    I/O ports at 1c7c [size=4]
    I/O ports at 1c80 [size=8]
    I/O ports at 1c78 [size=4]
    I/O ports at 1c40 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_generic

00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03) (prog-if 02 [16550])
    Subsystem: Lenovo Device 3047
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
    I/O ports at 1c90 [size=8]
    Memory at fc526000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
    Subsystem: Lenovo Device 3047
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fc500000 (32-bit, non-prefetchable) [size=128K]
    Memory at fc527000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 1820 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Lenovo Device 3047
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1840 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Lenovo Device 3047
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1860 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Lenovo Device 3047
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1880 [SIZE=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 3047
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fc528000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

[/SIZE][SIZE=3][COLOR=Navy]00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
    Subsystem: Lenovo Device 3047
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fc520000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel[/COLOR][/SIZE][SIZE=3]

00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Lenovo Device 3047
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 18a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Lenovo Device 3047
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 18c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Lenovo Device 3047
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 3047
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at fc529000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=11, subordinate=11, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
    Subsystem: Lenovo Device 3047
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 3047
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at 1ca8 [size=8]
    I/O ports at 1c9c [size=4]
    I/O ports at 1ca0 [size=8]
    I/O ports at 1c98 [size=4]
    I/O ports at 1c00 [size=32]
    Memory at fc52a000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
    Subsystem: Lenovo Device 3047
    Flags: medium devsel, IRQ 10
    Memory at fc52b000 (64-bit, non-prefetchable) [disabled] [size=256]
    I/O ports at 1c20 [SIZE=32]
    Kernel modules: i2c-i801


Please anybody help me about this !![/SIZE]

---

### Post by lidex on 2011-05-04
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

