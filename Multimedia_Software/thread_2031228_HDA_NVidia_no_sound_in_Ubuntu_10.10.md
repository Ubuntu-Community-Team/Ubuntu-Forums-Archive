---
title: "HDA NVidia no sound in Ubuntu 10.10"
date: 2012-07-21
forum: Multimedia Software
---

### Post by Muixca on 2012-07-21
Greetings!
Just bought a DELL Latitude E6430 (specs further down). Normally DELL does not give me trouble with Ubuntu but this time it does, big time. Got the video working but the audio, no way.
I applied all instructions on [http://www.benking.me.uk/2010/08/13/ubuntu-10-x-nvidia-hdmi-audio-out/](http://www.benking.me.uk/2010/08/13/ubuntu-10-x-nvidia-hdmi-audio-out/) but to no avail.

Ref the aplay output, all four devices are unmuted but F4 tells me that none of them has capturing controls. I got the card to turn up in the gnome-volume-control panel (initially there was just dummy output, now it says HDA NVidia Stereo but (sigh)
HDA NVidia Digital Stereo shows up in gnome-volume-control.

Here's the output of lspci -v, lshw, aplay -l

Your attention and any help appreciated!

**aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**lspci -v

00:00.0 Host bridge: Intel Corporation Device 0154 (rev 09)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Device 0151 (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f5000000-f60fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:14.0 USB Controller: Intel Corporation Device 1e31 (rev 04) (prog-if 30)
    Subsystem: Dell Device 0534
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7720000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd

00:16.0 Communication controller: Intel Corporation Device 1e3a (rev 04)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f773c000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f7700000 (32-bit, non-prefetchable) [size=128K]
    Memory at f7739000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation Device 1e2d (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0534
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7738000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Device 1e20 (rev 04)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 4
    Memory at f7730000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation Device 1e10 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Device 1e12 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f7600000-f76fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation Device 1e14 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=07, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f6b00000-f74fffff
    Prefetchable memory behind bridge: 00000000f2b00000-00000000f34fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation Device 1e16 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=0b, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f6100000-f6afffff
    Prefetchable memory behind bridge: 00000000f2100000-00000000f2afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation Device 1e1a (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
    Memory behind bridge: f7500000-f75fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation Device 1e26 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0534
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at f7737000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Device 1e55 (rev 04)
    Subsystem: Dell Device 0534
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 04)
    Subsystem: Dell Device 0534
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 48
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f020 [size=32]
    Memory at f7736000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation Device 1e22 (rev 04)
    Subsystem: Dell Device 0534
    Flags: medium devsel, IRQ 11
    Memory at f7735000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Device 0dfc (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at f6000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f6080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

03:00.0 Network controller: Intel Corporation 6000 Series Gen2 (rev 34)
    Subsystem: Intel Corporation Device 1321
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f7600000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>

0c:00.0 SD Host controller: O2 Micro, Inc. Device 8221 (rev 05) (prog-if 01)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7502000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

**lshw

Latitude-E6430
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 5932MiB
     *-cpu
          product: Intel(R) Core(TM) i5-3320M CPU @ 2.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) memory:f5000000-f60fffff ioport:e0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f6000000-f607ffff
           *-multimedia
                description: Audio device
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:f6080000-f6083fff
        *-usb:0
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:16 memory:f7720000-f772ffff
        *-communication UNCLAIMED
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f773c000-f773c00f
        *-network
             description: Ethernet interface
             product: 82579LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 04
             serial: d4:be:d9:39:fd:4a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=0.13-3 ip=192.168.1.144 latency=0 multicast=yes
             resources: irq:47 memory:f7700000-f771ffff memory:f7739000-f7739fff ioport:f040(size=32)
        *-usb:1
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f7738000-f77383ff
        *-multimedia UNCLAIMED
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f7730000-f7733fff
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 memory:f7600000-f76fffff
           *-network UNCLAIMED
                description: Network controller
                product: 6000 Series Gen2
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 34
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:f7600000-f7601fff
        *-pci:3
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:d000(size=4096) memory:f6b00000-f74fffff ioport:f2b00000(size=10485760)
        *-pci:4
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:c000(size=4096) memory:f6100000-f6afffff ioport:f2100000(size=10485760)
        *-pci:5
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 memory:f7500000-f75fffff
           *-generic
                description: SD Host controller
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:f7502000-f75021ff
        *-usb:2
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:f7737000-f77373ff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: RAID bus controller
             product: Mobile 82801 SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:48 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f020(size=32) memory:f7736000-f77367ff
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7735000-f77350ff ioport:f000(size=32)

---

### Post by bobsan on 2012-07-21
Why are you still running Ubuntu 10.10? It is a dead OS. Dead since April. You won't receive bug fixes or any security update. Time to move on.

---

### Post by Muixca on 2012-07-22
Hi! thanks for the suggestion. I indeed tried to install everything ranging from 12.04 (32 and 64) over 11 to 10... which was finally the only one I could install on this particular machine; spent a week on the issue. All over 10.10 hangs, stops, stalls due to graphic card incompatibility. No way to get them installed, I read the whole internet. The alt versions don't work either, they install but stall launching...
Again, thanks for taking the trouble.
m

---

