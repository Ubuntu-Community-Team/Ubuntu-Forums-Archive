---
title: "Music plays 5x faster"
date: 2009-05-18
forum: Multimedia Software
---

### Post by Crypticz on 2009-05-18
It plays about 5x faster than it normally would and is crackling. 

Post here what do you need to know and the way to reach for it.

been looking around for solutions without success

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 2f00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at ec00 [size=64]
    I/O ports at 2d00 [size=64]
    I/O ports at 2e00 [size=64]
    Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at febff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
    Memory at febfec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at febfe800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: Device f019:2609
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at febf8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
    I/O ports at e480 [size=8]
    I/O ports at e400 [size=4]
    I/O ports at e080 [size=8]
    I/O ports at e000 [size=4]
    I/O ports at dc00 [size=16]
    Memory at febf6000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2296
    Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at d880 [size=8]
    Memory at febfe400 (32-bit, non-prefetchable) [size=256]
    Memory at febfe000 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2)
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

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

```

---

### Post by Crypticz on 2009-05-19
After re-installing ubuntu few times I have come to a conclusion that my nVidia graphics drivers are doing this all

that means i am forced to disable my video drivers to listen any music or play any sounds properly

halp me nao

---

### Post by adam_kimber on 2009-05-19
Hmmmm how did come to that conclusion? Have a look at this thread [http://ubuntuforums.org/showthread.php?t=1146319](http://ubuntuforums.org/showthread.php?t=1146319)

---

### Post by Crypticz on 2009-05-19
> **adam_kimber said:**
> Hmmmm how did come to that conclusion? Have a look at this thread [http://ubuntuforums.org/showthread.php?t=1146319](http://ubuntuforums.org/showthread.php?t=1146319)

well, I tried like 2 days to find out what could be wrong until I ended up doing few formats and installing things and restarting until I noticed that removing the graphic card's drivers would fix the problem and installing them would make the problem come back ;)

---

### Post by Crypticz on 2009-05-19
bump

---

