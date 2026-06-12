---
title: "Tv tuner help please"
date: 2010-05-18
forum: Multimedia Software
---

### Post by ManyBeers on 2010-05-18
Gateway desktop running Ubuntu LL 10.04(64 bit) with Asus/ViXS Combo-210E NTSC/ATSC TV Tuner card:

link to card...[http://support.gateway.com/s/vidcard/asustek/6003130R/6003130Rnv.shtml]("http://support.gateway.com/s/vidcard/asustek/6003130R/6003130Rnv.shtml")

Ubuntu lists the card when I do lshw in a terminal but it shows as 'unclaimed'. Is that important? Also what software is neccessary to watch tv? Basically could somebody help me get tv working in Ubuntu. The card works fine in Windows7

---

### Post by ManyBeers on 2010-05-19
bump

---

### Post by xc3RnbFO8P on 2010-05-19
In Terminal show the output of:
> lspci -vnn
> dmesg

---

### Post by ManyBeers on 2010-05-19
> **Ringi said:**
> In Terminal show the output of:

Ok```
mark@marksdesktop:~$ lspci -vnn
00:00.0 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
	Subsystem: Elitegroup Computer Systems Device [1019:2601]
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
	Subsystem: Elitegroup Computer Systems Device [1019:2601]
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
	Subsystem: Elitegroup Computer Systems Device [1019:2601]
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at fc00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at f400 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
	Subsystem: Elitegroup Computer Systems Device [1019:2601]
	Flags: 66MHz, fast devsel

00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a3) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device [1019:2601]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3) (prog-if 20)
	Subsystem: Elitegroup Computer Systems Device [1019:2601]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: fd800000-fd8fffff
	Capabilities: <access denied>

00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
	Subsystem: Elitegroup Computer Systems Device [1019:2601]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Elitegroup Computer Systems Device [1019:2601]
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Elitegroup Computer Systems Device [1019:2601]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at dc00 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:08.1 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Elitegroup Computer Systems Device [1019:2601]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c800 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0d.0 VGA compatible controller [0300]: nVidia Corporation C61 [GeForce 6150SE nForce 430] [10de:03d0] (rev a2)
	Subsystem: Elitegroup Computer Systems Device [1019:2601]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 80000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:06.0 Communication controller [0780]: Conexant Systems, Inc. Device [14f1:2f40]
	Subsystem: Conexant Systems, Inc. Device [14f1:2000]
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at bc00 [size=8]
	Capabilities: <access denied>

01:09.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024] (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device [1019:8024]
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fdff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
	Subsystem: Elitegroup Computer Systems Device [1019:8039]
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at fdcfc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 9c00 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

04:00.0 Multimedia controller [0480]: ViXS Systems, Inc. XCode 2100 Series [1745:2100]
	Subsystem: ASUSTeK Computer Inc. Device [1043:4899]
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at fd900000 (64-bit, prefetchable) [size=1M]
	Memory at fdaf0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at <unassigned>
	Capabilities: <access denied>

mark@marksdesktop:~$ 

```

dmesg:
```
[    0.558417] vgaarb: loaded
[    0.558747] SCSI subsystem initialized
[    0.559005] libata version 3.00 loaded.
[    0.559322] usbcore: registered new interface driver usbfs
[    0.559373] usbcore: registered new interface driver hub
[    0.559468] usbcore: registered new device driver usb
[    0.560113] ACPI: WMI: Mapper loaded
[    0.560116] PCI: Using ACPI for IRQ routing
[    0.560708] NetLabel: Initializing
[    0.560709] NetLabel:  domain hash size = 128
[    0.560711] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.560743] NetLabel:  unlabeled traffic allowed by default
[    0.560857] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.560862] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.570163] Switching to clocksource hpet
[    0.576077] AppArmor: AppArmor Filesystem Enabled
[    0.576107] pnp: PnP ACPI init
[    0.576140] ACPI: bus type pnp registered
[    0.590012] pnp: PnP ACPI: found 12 devices
[    0.590014] ACPI: ACPI bus type pnp unregistered
[    0.590034] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.590040] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.590044] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.590048] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.590052] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.590056] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.590060] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.590064] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.590070] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.590075] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[    0.590079] system 00:01: iomem range 0x78000000-0x7fffffff has been reserved
[    0.590091] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.590096] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.590100] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.590112] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.590122] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[    0.590126] system 00:0b: iomem range 0xfeff0000-0xfeff00ff has been reserved
[    0.590131] system 00:0b: iomem range 0x77ee0000-0x77efffff could not be reserved
[    0.590135] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.590139] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.590143] system 00:0b: iomem range 0x100000-0x77edffff could not be reserved
[    0.590147] system 00:0b: iomem range 0x77f00000-0x7fefffff could not be reserved
[    0.590152] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.590156] system 00:0b: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.590160] system 00:0b: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.590164] system 00:0b: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.590169] system 00:0b: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.590173] system 00:0b: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.595185] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.595191] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[    0.595198] pci 0000:00:04.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.595204] pci 0000:00:04.0:   PREFETCH window: 0xfd800000-0xfd8fffff
[    0.595211] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.595216] pci 0000:00:09.0:   IO window: 0xa000-0xafff
[    0.595221] pci 0000:00:09.0:   MEM window: 0xfde00000-0xfdefffff
[    0.595227] pci 0000:00:09.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.595233] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.595238] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff
[    0.595243] pci 0000:00:0b.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.595248] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.595254] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.595259] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff
[    0.595264] pci 0000:00:0c.0:   MEM window: 0xfda00000-0xfdafffff
[    0.595269] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.595284] pci 0000:00:04.0: setting latency timer to 64
[    0.595294] pci 0000:00:09.0: setting latency timer to 64
[    0.595303] pci 0000:00:0b.0: setting latency timer to 64
[    0.595312] pci 0000:00:0c.0: setting latency timer to 64
[    0.595319] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.595322] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.595329] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.595335] pci_bus 0000:01: resource 1 mem: [0xfdf00000-0xfdffffff]
[    0.595340] pci_bus 0000:01: resource 2 pref mem [0xfd800000-0xfd8fffff]
[    0.595344] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.595347] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.595353] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.595356] pci_bus 0000:02: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.595360] pci_bus 0000:02: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.595364] pci_bus 0000:03: resource 0 io:  [0x9000-0x9fff]
[    0.595367] pci_bus 0000:03: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.595371] pci_bus 0000:03: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.595375] pci_bus 0000:04: resource 0 io:  [0x8000-0x8fff]
[    0.595379] pci_bus 0000:04: resource 1 mem: [0xfda00000-0xfdafffff]
[    0.595382] pci_bus 0000:04: resource 2 pref mem [0xfd900000-0xfd9fffff]
[    0.595441] NET: Registered protocol family 2
[    0.595749] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.598060] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.600819] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.601427] TCP: Hash tables configured (established 262144 bind 65536)
[    0.601431] TCP reno registered
[    0.601574] NET: Registered protocol family 1
[    0.620132] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.620202] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.620284] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.620360] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.620442] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.620530] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.620624] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.620634] pci 0000:00:0d.0: Boot video device
[    0.621555] Scanning for low memory corruption every 60 seconds
[    0.621788] audit: initializing netlink socket (disabled)
[    0.621802] type=2000 audit(1274261100.620:1): initialized
[    0.631006] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.635991] VFS: Disk quotas dquot_6.5.2
[    0.636118] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.638098] fuse init (API version 7.13)
[    0.638369] msgmni has been set to 3759
[    0.638899] alg: No test for stdrng (krng)
[    0.639082] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.639086] io scheduler noop registered
[    0.639088] io scheduler anticipatory registered
[    0.639090] io scheduler deadline registered
[    0.639202] io scheduler cfq registered (default)
[    0.639674]   alloc irq_desc for 24 on node 0
[    0.639677]   alloc kstat_irqs on node 0
[    0.639691] pcieport 0000:00:09.0: irq 24 for MSI/MSI-X
[    0.639698] pcieport 0000:00:09.0: setting latency timer to 64
[    0.639940]   alloc irq_desc for 25 on node 0
[    0.639942]   alloc kstat_irqs on node 0
[    0.639951] pcieport 0000:00:0b.0: irq 25 for MSI/MSI-X
[    0.639958] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.640199]   alloc irq_desc for 26 on node 0
[    0.640201]   alloc kstat_irqs on node 0
[    0.640211] pcieport 0000:00:0c.0: irq 26 for MSI/MSI-X
[    0.640218] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.640383] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.640464] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.640731] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.640737] ACPI: Power Button [PWRB]
[    0.640935] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.640941] ACPI: Power Button [PWRF]
[    0.641080] fan PNP0C0B:00: registered as cooling_device0
[    0.641101] ACPI: Fan [FAN] (on)
[    0.642497] processor LNXCPU:00: registered as cooling_device1
[    0.642623] processor LNXCPU:01: registered as cooling_device2
[    0.657444] thermal LNXTHERM:01: registered as thermal_zone0
[    0.657476] ACPI: Thermal Zone [THRM] (40 C)
[    0.662564] Linux agpgart interface v0.103
[    0.662650] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.662796] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.663402] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.666867] brd: module loaded
[    0.668480] loop: module loaded
[    0.668767] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.669264] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.670557] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.670563]   alloc irq_desc for 23 on node 0
[    0.670565]   alloc kstat_irqs on node 0
[    0.670578] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.670610] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.670630] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.671809] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    0.671813]   alloc irq_desc for 22 on node 0
[    0.671815]   alloc kstat_irqs on node 0
[    0.671826] pata_acpi 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.671857] pata_acpi 0000:00:08.1: setting latency timer to 64
[    0.671877] pata_acpi 0000:00:08.1: PCI INT B disabled
[    0.673227] Fixed MDIO Bus: probed
[    0.673334] PPP generic driver version 2.4.2
[    0.673453] tun: Universal TUN/TAP device driver, 1.6
[    0.673455] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.673699] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.674886] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.674891]   alloc irq_desc for 21 on node 0
[    0.674892]   alloc kstat_irqs on node 0
[    0.674904] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.674935] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.674939] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.675034] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.675071] ehci_hcd 0000:00:02.1: debug port 1
[    0.675082] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.675125] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfe02e000
[    0.690040] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.690269] usb usb1: configuration #1 chosen from 1 choice
[    0.690329] hub 1-0:1.0: USB hub found
[    0.690341] hub 1-0:1.0: 10 ports detected
[    0.690510] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.691743] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    0.691748]   alloc irq_desc for 20 on node 0
[    0.691750]   alloc kstat_irqs on node 0
[    0.691762] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    0.691786] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.691790] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.691893] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.691937] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    0.752228] usb usb2: configuration #1 chosen from 1 choice
[    0.752288] hub 2-0:1.0: USB hub found
[    0.752299] hub 2-0:1.0: 10 ports detected
[    0.752440] uhci_hcd: USB Universal Host Controller Interface driver
[    0.752629] PNP: No PS/2 controller found. Probing ports directly.
[    0.753118] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.753132] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.753443] mice: PS/2 mouse device common for all mice
[    0.753724] rtc_cmos 00:05: RTC can wake from S4
[    0.753845] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.753889] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.754235] device-mapper: uevent: version 1.0.3
[    0.754455] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.754620] device-mapper: multipath: version 1.1.0 loaded
[    0.754626] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.755107] cpuidle: using governor ladder
[    0.755109] cpuidle: using governor menu
[    0.755634] TCP cubic registered
[    0.755902] NET: Registered protocol family 10
[    0.756661] lo: Disabled Privacy Extensions
[    0.757114] NET: Registered protocol family 17
[    0.757180] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ processors (2 cpu cores) (version 2.20.00)
[    0.757316] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xa
[    0.757319] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xb
[    0.757321] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xd
[    0.757323] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[    0.757652] PM: Resume from disk failed.
[    0.757692] registered taskstats version 1
[    0.758320]   Magic number: 10:747:424
[    0.758429] rtc_cmos 00:05: setting system clock to 2010-05-19 09:25:01 UTC (1274261101)
[    0.758434] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.758435] EDD information not available.
[    0.758552] Freeing unused kernel memory: 876k freed
[    0.759193] Write protecting the kernel read-only data: 7680k
[    0.798941] udev: starting version 151
[    1.010131] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.024088] pata_amd 0000:00:06.0: version 0.4.1
[    1.024161] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.043591] scsi0 : pata_amd
[    1.052293] sky2 driver version 1.25
[    1.057065] scsi1 : pata_amd
[    1.062073] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.062077] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.083004] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[    1.083014]   alloc irq_desc for 16 on node 0
[    1.083016]   alloc kstat_irqs on node 0
[    1.083029] sky2 0000:03:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[    1.083048] sky2 0000:03:00.0: setting latency timer to 64
[    1.083094] sky2 0000:03:00.0: Yukon-2 FE chip revision 3
[    1.083154]   alloc irq_desc for 27 on node 0
[    1.083156]   alloc kstat_irqs on node 0
[    1.083168] sky2 0000:03:00.0: irq 27 for MSI/MSI-X
[    1.083235] sata_nv 0000:00:08.0: version 3.5
[    1.083244] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.083302] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.085078] sky2 eth0: addr 00:1b:b9:5d:60:17
[    1.085177] scsi2 : sata_nv
[    1.085372] scsi3 : sata_nv
[    1.086049] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 23
[    1.086053] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 23
[    1.086839] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    1.086923] sata_nv 0000:00:08.1: setting latency timer to 64
[    1.087057] scsi4 : sata_nv
[    1.087175] scsi5 : sata_nv
[    1.087664] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc800 irq 22
[    1.087667] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc808 irq 22
[    1.164984] usb 1-2: configuration #1 chosen from 1 choice
[    1.179179] Initializing USB Mass Storage driver...
[    1.179397] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.179586] usb-storage: device found at 2
[    1.179590] usb-storage: waiting for device to settle before scanning
[    1.179615] usbcore: registered new interface driver usb-storage
[    1.179620] USB Mass Storage support registered.
[    1.240292] ata1.00: ATAPI: ATAPI   DVD A  DH16A1P, RG11, max UDMA/66
[    1.240318] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[    1.240322] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.280234] ata1.00: configured for UDMA/33
[    1.281955] scsi 0:0:0:0: CD-ROM            ATAPI    DVD A  DH16A1P   RG11 PQ: 0 ANSI: 5
[    1.287083] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.287088] Uniform CD-ROM driver Revision: 3.20
[    1.287360] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.287515] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.287722] ata2: port disabled. ignoring.
[    1.350024] usb 1-7: new high speed USB device using ehci_hcd and address 4
[    1.420337] ata5: SATA link down (SStatus 0 SControl 300)
[    1.512176] usb 1-7: configuration #1 chosen from 1 choice
[    1.512556] scsi7 : SCSI emulation for USB Mass Storage devices
[    1.512924] usb-storage: device found at 4
[    1.512925] usb-storage: waiting for device to settle before scanning
[    1.580041] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.642735] ata3.00: ATA-7: ST3250820AS, 3.AAD, max UDMA/133
[    1.642738] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.734378] ata3.00: configured for UDMA/133
[    1.734545] scsi 2:0:0:0: Direct-Access     ATA      ST3250820AS      3.AA PQ: 0 ANSI: 5
[    1.734947] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.735007] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.735238] sd 2:0:0:0: [sda] Write Protect is off
[    1.735241] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.735305] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.735652]  sda: sda1 sda2 sda3
[    1.783029] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.850022] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    2.087180] usb 2-3: configuration #1 chosen from 1 choice
[    2.105447] usbcore: registered new interface driver hiddev
[    2.114586] input: Chicony USB Wireless HID Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3
[    2.115415] generic-usb 0003:04F2:0420.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony USB Wireless HID Receiver] on usb-0000:00:02.0-3/input0
[    2.134260] input: Chicony USB Wireless HID Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input4
[    2.134773] generic-usb 0003:04F2:0420.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Chicony USB Wireless HID Receiver] on usb-0000:00:02.0-3/input1
[    2.143499] input: Chicony USB Wireless HID Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.2/input/input5
[    2.143769] generic-usb 0003:04F2:0420.0003: input,hidraw2: USB HID v1.11 Mouse [Chicony USB Wireless HID Receiver] on usb-0000:00:02.0-3/input2
[    2.143826] usbcore: registered new interface driver usbhid
[    2.143831] usbhid: v2.6:USB HID core driver
[    2.220039] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.240243] ata4.00: ATA-5: TOSHIBA MK2018GAP, M1.42 A, max UDMA/100
[    2.240246] ata4.00: 39070080 sectors, multi 16: LBA 
[    2.240257] ata4.00: applying bridge limits
[    2.260247] ata4.00: configured for UDMA/100
[    2.260392] scsi 3:0:0:0: Direct-Access     ATA      TOSHIBA MK2018GA M1.4 PQ: 0 ANSI: 5
[    2.260757] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.260781] sd 3:0:0:0: [sdb] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    2.260997] sd 3:0:0:0: [sdb] Write Protect is off
[    2.261000] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.261063] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.261410]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 >
[    2.366362] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.600335] ata6: SATA link down (SStatus 0 SControl 300)
[    2.618950] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    2.618961]   alloc irq_desc for 19 on node 0
[    2.618963]   alloc kstat_irqs on node 0
[    2.618978] ohci1394 0000:01:09.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    2.618986] ohci1394 0000:01:09.0: setting latency timer to 64
[    2.680076] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fdfff000-fdfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.273223] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[    3.990247] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff605e2c]
[    6.170479] usb-storage: device scan complete
[    6.173825] scsi 6:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
[    6.174745] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    6.184315] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    6.510226] usb-storage: device scan complete
[    6.510946] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    6.511561] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    6.512183] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    6.512810] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    6.513892] sd 7:0:0:0: Attached scsi generic sg4 type 0
[    6.514456] sd 7:0:0:1: Attached scsi generic sg5 type 0
[    6.515173] sd 7:0:0:2: Attached scsi generic sg6 type 0
[    6.515621] sd 7:0:0:3: Attached scsi generic sg7 type 0
[    6.516056] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[    6.516684] sd 7:0:0:1: [sde] Attached SCSI removable disk
[    6.518550] sd 7:0:0:2: [sdf] Attached SCSI removable disk
[    6.519254] sd 7:0:0:3: [sdg] Attached SCSI removable disk
[   25.036638] Adding 2000084k swap on /dev/sdb3.  Priority:-1 extents:1 across:2000084k 
[   25.053080] udev: starting version 151
[   25.119765] lp: driver loaded but no devices found
[   25.204915] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   25.374761] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   25.374860] i2c i2c-1: nForce2 SMBus adapter at 0xf400
[   25.405931] parport_pc 00:09: reported by Plug and Play ACPI
[   25.405988] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   25.490417] lp0: using parport0 (interrupt-driven).
[   25.609766] EDAC MC: Ver: 2.1.0 Apr 28 2010
[   25.780417] ppdev: user-space parallel port driver
[   25.852733] type=1505 audit(1274282726.594:2):  operation="profile_load" pid=624 name="/sbin/dhclient3"
[   25.853014] type=1505 audit(1274282726.594:3):  operation="profile_load" pid=624 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.853176] type=1505 audit(1274282726.594:4):  operation="profile_load" pid=624 name="/usr/lib/connman/scripts/dhclient-script"
[   25.892491] EDAC amd64_edac:  Ver: 3.2.0 Apr 28 2010
[   25.903220] [drm] Initialized drm 1.1.0 20060810
[   25.912068] type=1505 audit(1274282726.644:5):  operation="profile_load" pid=652 name="/usr/sbin/ntpd"
[   25.933070] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0819
[   25.933144] usbcore: registered new interface driver usblp
[   25.941571] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   25.941584] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   25.941586]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   25.941587]  (Note that use of the override may cause unknown side effects.)
[   25.941630] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   26.142715] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 23
[   26.142724] nouveau 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 23 (level, low) -> IRQ 23
[   26.142731] nouveau 0000:00:0d.0: setting latency timer to 64
[   26.154628] [drm] nouveau 0000:00:0d.0: failed to evaluate _DSM: 5
[   26.155027] [drm] nouveau 0000:00:0d.0: Detected an NV40 generation card (0x04c000a2)
[   26.155441] [drm] nouveau 0000:00:0d.0: Attempting to load BIOS image from PROM
[   26.155449] [drm] nouveau 0000:00:0d.0: ... BIOS signature not found
[   26.155451] [drm] nouveau 0000:00:0d.0: Attempting to load BIOS image from PRAMIN
[   26.195818] [drm] nouveau 0000:00:0d.0: ... appears to be valid
[   26.195824] [drm] nouveau 0000:00:0d.0: BIT BIOS found
[   26.195829] [drm] nouveau 0000:00:0d.0: Bios version 05.61.32.20
[   26.195833] [drm] nouveau 0000:00:0d.0: BIT table 'd' not found
[   26.195838] [drm] nouveau 0000:00:0d.0: Found Display Configuration Block version 3.0
[   26.195844] [drm] nouveau 0000:00:0d.0: DCB connector table: VHER 0x30 5 10 2
[   26.195848] [drm] nouveau 0000:00:0d.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[   26.195852] [drm] nouveau 0000:00:0d.0: Raw DCB entry 0: 01000310 00000023
[   26.195857] [drm] nouveau 0000:00:0d.0: Raw DCB entry 1: 00110204 97dd0000
[   26.195867] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 0 at offset 0xDCAA
[   26.195872] [drm] nouveau 0000:00:0d.0: ======= misaligned reg 0x0060081D =======
[   26.195933] [drm] nouveau 0000:00:0d.0: ======= misaligned reg 0x0060081D =======
[   26.196043] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 1 at offset 0xDE01
[   26.196047] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 2 at offset 0xDE02
[   26.196111] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 3 at offset 0xDF84
[   26.196117] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 4 at offset 0xDFCD
[   26.290925] [TTM] Zone  kernel: Available graphics memory: 962932 kiB.
[   26.290953] [drm] nouveau 0000:00:0d.0: 128 MiB VRAM
[   26.291769] [drm] nouveau 0000:00:0d.0: 64 MiB GART (aperture)
[   26.292140] [drm] nouveau 0000:00:0d.0: Allocating FIFO number 0
[   26.292607] [drm] nouveau 0000:00:0d.0: nouveau_channel_alloc: initialised FIFO 0
[   26.292619] [drm] nouveau 0000:00:0d.0: Initial CRTC_OWNER is 0
[   26.292628] [drm] nouveau 0000:00:0d.0: Saving VGA fonts
[   26.330089] [drm] nouveau 0000:00:0d.0: DCB type 4 not known
[   26.330096] [drm] nouveau 0000:00:0d.0: Detected a VGA connector
[   26.331230] [drm] nouveau 0000:00:0d.0: Setting dpms mode 3 on vga encoder (output 0)
[   26.497102] [drm] nouveau 0000:00:0d.0: allocated 1280x1024 fb: 0x49000, bo ffff88003769de00
[   26.497404] fb0: nouveaufb frame buffer device
[   26.497407] registered panic notifier
[   26.497419] [drm] Initialized nouveau 0.0.15 20090420 for 0000:00:0d.0 on minor 0
[   26.501698] vga16fb: initializing
[   26.501710] vga16fb: mapped to 0xffff8800000a0000
[   26.501719] vga16fb: not registering due to another framebuffer present
[   26.506315] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   26.506326] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   26.506333] hda_intel: Disable MSI for Nvidia chipset
[   26.506411] HDA Intel 0000:00:05.0: setting latency timer to 64
[   26.564606] EXT4-fs (sdb2): mounted filesystem with ordered data mode
[   26.600485] [drm] nouveau 0000:00:0d.0: Setting dpms mode 0 on vga encoder (output 0)
[   26.600494] [drm] nouveau 0000:00:0d.0: Output VGA-1 is running on CRTC 0 using output A
[   26.607295] Console: switching to colour frame buffer device 160x64
[   27.850039] hda_codec: ALC888: BIOS auto-probing.
[   28.360352] sky2 eth0: enabling interface
[   28.360828] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.378055] type=1505 audit(1274282729.111:6):  operation="profile_load" pid=892 name="/usr/share/gdm/guest-session/Xsession"
[   28.401293] type=1505 audit(1274282729.141:7):  operation="profile_replace" pid=893 name="/sbin/dhclient3"
[   28.401602] type=1505 audit(1274282729.141:8):  operation="profile_replace" pid=893 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   28.401788] type=1505 audit(1274282729.141:9):  operation="profile_replace" pid=893 name="/usr/lib/connman/scripts/dhclient-script"
[   28.419202] type=1505 audit(1274282729.151:10):  operation="profile_load" pid=897 name="/usr/bin/evince"
[   28.440554] type=1505 audit(1274282729.181:11):  operation="profile_load" pid=897 name="/usr/bin/evince-previewer"
[   28.630383] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input6
[   29.026156] [drm] nouveau 0000:00:0d.0: Allocating FIFO number 1
[   29.026650] [drm] nouveau 0000:00:0d.0: nouveau_channel_alloc: initialised FIFO 1
[   30.043404] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   30.043878] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   31.561881] usb 1-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   40.382518] eth0: no IPv6 routers present
[   92.510032] Clocksource tsc unstable (delta = -236097202 ns)
mark@marksdesktop:~$ 

```

---

### Post by iponeverything on 2010-05-19
ViXS PureTV-U 48B0 does not appear to have a driver for linux.

---

### Post by xc3RnbFO8P on 2010-05-19
@iponeverything, that is right.
**ViXS PureTV-U** 4899 (NTSC/ATSC Combo  ID 1043:4899
[http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards#Supported_ATSC_mini-PCI_cards:]("http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards#Supported_ATSC_mini-PCI_cards:")

---

### Post by ManyBeers on 2010-05-19
> **Ringi said:**
> @iponeverything, that is right.
**ViXS PureTV-U** 4899 (NTSC/ATSC Combo  ID 1043:4899
[http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards#Supported_ATSC_mini-PCI_cards:]("http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards#Supported_ATSC_mini-PCI_cards:")

Ouch. So I'm out of luck. Thanks

---

