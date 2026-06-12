---
title: "Vanished sound"
date: 2012-09-12
forum: Multimedia Software
---

### Post by nnjond on 2012-09-12
Hi,

I've run number of live and installed distros, and I can see evidence of my sound working ok, but can't hear anything?

Alsamixer doesn't seem to be muted?

At the present I've installed kde mint13.

Any comment's please


lspci -v
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 4f00 [size=256]

00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at 4900 [size=64]
        I/O ports at 4d00 [size=64]
        I/O ports at 4e00 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: nForce2_smbus
        Kernel modules: i2c-nforce2

00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: 66MHz, fast devsel

00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fdf7f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ohci_hcd

00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fdf7ec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Capabilities: <access denied>

00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at fdf78000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: pata_amd
        Kernel modules: pata_amd

00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 43
        Memory at fdf7d000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e480 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: forcedeth
        Kernel modules: forcedeth

00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at e400 [size=8]
        I/O ports at e080 [size=4]
        I/O ports at e000 [size=8]
        I/O ports at dc00 [size=4]
        I/O ports at d880 [size=16]
        Memory at fdf7c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: sata_nv
        Kernel modules: sata_nv

00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at d800 [size=8]
        I/O ports at d480 [size=4]
        I/O ports at d400 [size=8]
        I/O ports at d080 [size=4]
        I/O ports at d000 [size=16]
        Memory at fdf77000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: sata_nv
        Kernel modules: sata_nv

00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: fe000000-fe0fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: Elitegroup Computer Systems Device 2602
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at fdf40000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nouveau
        Kernel modules: nouveau, nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>
        Kernel driver in use: k8temp
        Kernel modules: k8temp

---

### Post by Bucky Ball on 2012-09-12
*Moved to **Multimedia & Video***

---

