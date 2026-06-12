---
title: "Sound has stopped working after a gparted job"
date: 2009-04-12
forum: Multimedia Software
---

### Post by Zboarda on 2009-04-12
Hi there! Happy Easter to you all!!!! :D 

I've been using Ubuntu for about 6 months and loving it. On my laptop, Acer have put a few partitions which I didn't like, so I resized them on both internal harddrives to give more space to my Windows and Ubuntu partitions. After I did this, Windows wouldn't boot up. Ubuntu works fine except I can't get any sound now. I was using my X-Fi Sound Blaster 5.1 USB card for audio as the internal audio isn't pleasant. It worked fine in Ubuntu before but now it doesn't work, nor does the internal audio work. I get the error when I double click on the volume control panel:
```

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

```
You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

I've tried aplay -l and asoundconf list but to no avail. No cards to display. Though the audio device does appear in lspci. Strange... :s

Here is the output for lspci:
```

tim@tim-laptop:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c4000000-c6ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: Acer Incorporated [ALI] Device 0145
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [140] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fc304800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f6000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0145
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0145
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: c0000000-c1ffffff
	Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0145
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=09, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: c2000000-c20fffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000c9ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0145
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0b, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: fa000000-fc0fffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0145
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fc304c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=32
	Capabilities: [50] Subsystem: Gammagraphx, Inc. Device 0000

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP])
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18a0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix, ata_generic, pata_acpi

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2297
	I/O ports at 18d8 [size=8]
	I/O ports at 18cc [size=4]
	I/O ports at 18d0 [size=8]
	I/O ports at 18c8 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fc304000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: medium devsel, IRQ 10
	Memory at c2100000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9650M GS (rev a1)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
	Subsystem: Acer Incorporated [ALI] Device 0145
	Flags: bus master, fast devsel, latency 0, IRQ 2296
	Memory at f6000000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 3000 [size=128]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [180] Device Serial Number ff-d1-a0-00-61-2b-aa-ff
	Kernel driver in use: ATL1E
	Kernel modules: atl1e

08:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1101
	Flags: bus master, fast devsel, latency 0, IRQ 2295
	Memory at c2000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 7f-03-1d-ff-ff-3b-1f-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

```

Here is the output for lshw:
```

tim@tim-laptop:~$ sudo lshw
tim-laptop                
    description: Notebook
    product: Aspire 8920
    vendor: Acer
    version: Aspire 8920
    serial: LXAP70U06883400B5B2300
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=B3F38E10-6A89-11DD-A70E-00A0D1AA2B61
  *-core
       description: Motherboard
       product: Aspire 8920
       vendor: Acer
       physical id: 0
       version: Aspire 8920
       serial: Not Applicable
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.13 (07/25/08)
          size: 110KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: CPU Version
          slot: U2E1
          size: 2501MHz
          capacity: 4096MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm ida cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 6MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 9650M GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: L1 Gigabit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: b0
                serial: 00:a0:d1:aa:2b:61
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wmaster0
                version: 61
                serial: 00:1f:3b:1d:03:7f
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.0.6 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
        *-pci:5
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f4
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: BD ROM BC-5500A
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom1
                version: 1.B6
                serial: [Optiarc BD ROM BC-5500A 1.B6 Mar31,2008
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom1
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk:0
                description: ATA Disk
                product: WDC WD3200BEVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXE508L66004
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=64c05fc0
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 3ef5-5a23
                   size: 12GiB
                   capacity: 13GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-06-10 22:35:50 filesystem=ntfs label=PQSERVICE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 562c8907-338c-2d49-8400-7a045c6c9cef
                   size: 265GiB
                   capacity: 265GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-04-03 03:25:33 filesystem=ntfs label=ACER state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 5693249d-2ac6-6948-af64-04da81ce51ec
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-08-19 20:07:26 filesystem=ntfs label=DATA modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:3
                   description: Windows NTFS volume
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   version: 3.1
                   serial: 267f-089a
                   size: 3615MiB
                   capacity: 3630MiB
                   capabilities: primary boot ntfs initialized
                   configuration: clustersize=4096 created=2009-02-21 13:29:59 filesystem=ntfs state=clean
           *-disk:1
                description: ATA Disk
                product: WDC WD3200BEVT-2
                vendor: Western Digital
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 11.0
                serial: WD-WXE508PM2741
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b85faebf
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 9ca46584-25b1-214e-9f15-a5c73038d135
                   size: 261GiB
                   capacity: 261GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-08-19 20:03:51 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdb2
                   size: 6283MiB
                   capacity: 6283MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 6283MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@3:0.0.0,3
                   logical name: /dev/sdb3
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: fa5aea5b-2d44-486b-a537-fb66fcefb4ee
                   size: 30GiB
                   capacity: 30GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-04 12:13:45 filesystem=ext3 modified=2009-04-12 19:27:23 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-04-12 19:27:23 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-battery
       description: Lithium Ion Battery
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1
       slot: Rear
       capacity: 1000mWh
       configuration: voltage=0.0V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 16:cc:e9:6b:48:1a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Any help would be greatly appreciated.

Zboarda

---

### Post by Zboarda on 2009-04-13
Can anyone help me?

---

### Post by avilella on 2009-04-13
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

If you have access to any of the laptops below and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[http://bugs.launchpad.net/bugs/312756](http://bugs.launchpad.net/bugs/312756)

Sony Vaio Z-series (intel/nvidia)
Fujitsu Siemens Amilo XI 3650 (intel/nvidia)
BenQ Joybook S42 (intel/nvidia)
ASUS N10J (intel/nvidia)
Dell Studio XPS 13 (nvidia/nvidia)
ASUS Intros G71Gx (?/nvidia GeForce 260M)
MSI GT628 (?/nvidia GeForce 160M)
LG Xnote P510 Laptop (?/nvidia GeForce GT 130M)
HP HDX 18t (?/nvidia GeForce GT 130M)
Dell XPS M1730 (nvidia/nvidia)
MSI EX630 (nvidia/nvidia -- )
Toshiba Qosmio X305-Q706/Q708 (nvidia/nvidia -- 9400m + 2x9800m GTS)
Acer Aspire 7530 (nvidia/nvidia -- 9100M G + GeForce 9300M GS)
ASUS X83Vm-X1 (?/nvidia)
+ Clevo M860TU (?/nvidia GeForce 9800M GTS)
+ Acer Aspire 8930G (?/nvidia GeForce 9700M GT)
+ Asus G50V (?/nvidia GeForce 9700M GT)
+ Zepto Mythos A15 (?/nvidia)
+ Asus M70VN (?/nvidia GeForce 9650M GT)
+ Acer Aspire 8920 (?/nvidia GeForce 9650M GS)
Lenovo ThinkPad T500 (intel/ati)
Lenovo ThinkPad T400 (intel/ati)
ASUS M51Ta (intel/ati)
Fujitsu-Siemens Amilo Sa 3650 (intel/ati)
MSI PX211 12'' (intel/ati)
HP Pavilion tx2500 (intel/ati)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

---

