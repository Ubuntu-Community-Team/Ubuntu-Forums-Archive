---
title: "AverMedia super 007 TV card installation problem."
date: 2010-06-04
forum: Multimedia Software
---

### Post by dpkg on 2010-06-04
Hey i browse at the forum and i did the top with the information i found.
now i need your help a little bit .

well 2 things that maybe help u

> lspci
gives me this:
> 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a1)
[COLOR="Red"]**06:00.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)**[/COLOR]
06:02.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)

now:
when i use the command:
**"dmesg"**
i got this:
> [    0.203191] pci 0000:00:1c.0: PME# disabled
[    0.203281] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.203288] pci 0000:00:1c.1: PME# disabled
[    0.203378] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.203385] pci 0000:00:1c.2: PME# disabled
[    0.203476] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.203483] pci 0000:00:1c.3: PME# disabled
[    0.203550] pci 0000:00:1d.0: reg 20 io port: [0xcc00-0xcc1f]
[    0.203618] pci 0000:00:1d.1: reg 20 io port: [0xd000-0xd01f]
[    0.203689] pci 0000:00:1d.2: reg 20 io port: [0xd400-0xd41f]
[    0.203756] pci 0000:00:1d.3: reg 20 io port: [0xd800-0xd81f]
[    0.203830] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfaafbc00-0xfaafbfff]
[    0.203896] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.203903] pci 0000:00:1d.7: PME# disabled
[    0.204077] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.204087] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.204094] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.204100] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0680-06ff
[    0.204107] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 4700-470f
[    0.204141] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.204152] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.204162] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.204173] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.204184] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.204243] pci 0000:00:1f.2: reg 10 io port: [0xec00-0xec07]
[    0.204253] pci 0000:00:1f.2: reg 14 io port: [0xe800-0xe803]
[    0.204263] pci 0000:00:1f.2: reg 18 io port: [0xe400-0xe407]
[    0.204272] pci 0000:00:1f.2: reg 1c io port: [0xe000-0xe003]
[    0.204282] pci 0000:00:1f.2: reg 20 io port: [0xdc00-0xdc0f]
[    0.204316] pci 0000:00:1f.2: PME# supported from D3hot
[    0.204322] pci 0000:00:1f.2: PME# disabled
[    0.204381] pci 0000:00:1f.3: reg 20 io port: [0xc800-0xc81f]
[    0.204458] pci 0000:01:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.204473] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.204487] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.204497] pci 0000:01:00.0: reg 24 io port: [0xac00-0xac7f]
[    0.204507] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfd000000-0xfd01ffff]
[    0.204593] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.204599] pci 0000:00:01.0: bridge 32bit mmio: [0xfb000000-0xfdffffff]
[    0.204606] pci 0000:00:01.0: bridge 32bit mmio pref: [0xc0000000-0xdfffffff]
[    0.204668] pci 0000:00:1c.0: bridge 32bit mmio: [0xfac00000-0xfacfffff]
[    0.204679] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xbfc00000-0xbfcfffff]
[    0.204743] pci 0000:00:1c.1: bridge 32bit mmio: [0xfad00000-0xfadfffff]
[    0.204754] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xbfd00000-0xbfdfffff]
[    0.204815] pci 0000:00:1c.2: bridge 32bit mmio: [0xfae00000-0xfaefffff]
[    0.204826] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xbfe00000-0xbfefffff]
[    0.204886] pci 0000:00:1c.3: bridge 32bit mmio: [0xfaf00000-0xfaffffff]
[    0.204897] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xbff00000-0xbfffffff]
[    0.204946] pci 0000:06:00.0: reg 10 32bit mmio: [0xfab00000-0xfab007ff]
[    0.205009] pci 0000:06:00.0: supports D1 D2
[    0.205059] pci 0000:06:02.0: reg 10 io port: [0xb800-0xb8ff]
[    0.205070] pci 0000:06:02.0: reg 14 32bit mmio: [0xfab00800-0xfab008ff]
[    0.205128] pci 0000:06:02.0: supports D1 D2
[    0.205132] pci 0000:06:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205140] pci 0000:06:02.0: PME# disabled
[    0.205198] pci 0000:00:1e.0: transparent bridge
[    0.205205] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]
[    0.205213] pci 0000:00:1e.0: bridge 32bit mmio: [0xfab00000-0xfabfffff]
[    0.205223] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xbfb00000-0xbfbfffff]
[    0.205260] pci_bus 0000:00: on NUMA node 0
[    0.205270] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.205478] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.205580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.205856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.205958] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.206059] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.206160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.207755] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.215482] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.215756] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.216029] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.216294] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.216549] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.216814] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.217067] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.217330] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.217593] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.217601] vgaarb: loaded
[    0.217822] SCSI subsystem initialized
[    0.217963] libata version 3.00 loaded.
[    0.218100] usbcore: registered new interface driver usbfs
[    0.218125] usbcore: registered new interface driver hub
[    0.218176] usbcore: registered new device driver usb
[    0.218434] ACPI: WMI: Mapper loaded
[    0.218439] PCI: Using ACPI for IRQ routing
[    0.218717] NetLabel: Initializing
[    0.218721] NetLabel:  domain hash size = 128
[    0.218725] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.218747] NetLabel:  unlabeled traffic allowed by default
[    0.218886] hpet clockevent registered
[    0.218892] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.218900] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.218910] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.224119] Switching to clocksource tsc
[    0.227599] AppArmor: AppArmor Filesystem Enabled
[    0.227625] pnp: PnP ACPI init
[    0.227650] ACPI: bus type pnp registered
[    0.234439] pnp: PnP ACPI: found 14 devices
[    0.234445] ACPI: ACPI bus type pnp unregistered
[    0.234452] PnPBIOS: Disabled by ACPI PNP
[    0.234482] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.234489] system 00:09: ioport range 0x400-0x47f has been reserved
[    0.234495] system 00:09: ioport range 0x500-0x53f has been reserved
[    0.234510] system 00:0b: iomem range 0xffc00000-0xfff7ffff has been reserved
[    0.234523] system 00:0c: ioport range 0x400-0x47f has been reserved
[    0.234529] system 00:0c: ioport range 0x680-0x6ff has been reserved
[    0.234535] system 00:0c: ioport range 0x500-0x53f has been reserved
[    0.234541] system 00:0c: iomem range 0xeec00000-0xeec03fff has been reserved
[    0.234548] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.234554] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.234561] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.234568] system 00:0c: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.234574] system 00:0c: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.234581] system 00:0c: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.234587] system 00:0c: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.234593] system 00:0c: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.234599] system 00:0c: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.234612] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.234618] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[    0.234624] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.234630] system 00:0d: iomem range 0x100000-0x3fffffff could not be reserved
[    0.269575] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.269582] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.269590] pci 0000:00:01.0:   MEM window: 0xfb000000-0xfdffffff
[    0.269597] pci 0000:00:01.0:   PREFETCH window: 0xc0000000-0xdfffffff
[    0.269606] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:05
[    0.269611] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.269619] pci 0000:00:1c.0:   MEM window: 0xfac00000-0xfacfffff
[    0.269626] pci 0000:00:1c.0:   PREFETCH window: 0x000000bfc00000-0x000000bfcfffff
[    0.269636] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.269642] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
[    0.269650] pci 0000:00:1c.1:   MEM window: 0xfad00000-0xfadfffff
[    0.269656] pci 0000:00:1c.1:   PREFETCH window: 0x000000bfd00000-0x000000bfdfffff
[    0.269666] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.269672] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff
[    0.269680] pci 0000:00:1c.2:   MEM window: 0xfae00000-0xfaefffff
[    0.269687] pci 0000:00:1c.2:   PREFETCH window: 0x000000bfe00000-0x000000bfefffff
[    0.269697] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:02
[    0.269703] pci 0000:00:1c.3:   IO window: 0x4000-0x4fff
[    0.269712] pci 0000:00:1c.3:   MEM window: 0xfaf00000-0xfaffffff
[    0.269719] pci 0000:00:1c.3:   PREFETCH window: 0x000000bff00000-0x000000bfffffff
[    0.269730] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.269737] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    0.269749] pci 0000:00:1e.0:   MEM window: 0xfab00000-0xfabfffff
[    0.269758] pci 0000:00:1e.0:   PREFETCH window: 0x000000bfb00000-0x000000bfbfffff
[    0.269782]   alloc irq_desc for 16 on node -1
[    0.269787]   alloc kstat_irqs on node -1
[    0.269798] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.269806] pci 0000:00:01.0: setting latency timer to 64
[    0.269821] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    0.269829]   alloc irq_desc for 17 on node -1
[    0.269832]   alloc kstat_irqs on node -1
[    0.269839] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.269847] pci 0000:00:1c.0: setting latency timer to 64
[    0.269859] pci 0000:00:1c.1: enabling device (0106 -> 0107)
[    0.269865] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.269872] pci 0000:00:1c.1: setting latency timer to 64
[    0.269884] pci 0000:00:1c.2: enabling device (0106 -> 0107)
[    0.269890]   alloc irq_desc for 18 on node -1
[    0.269893]   alloc kstat_irqs on node -1
[    0.269900] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.269907] pci 0000:00:1c.2: setting latency timer to 64
[    0.269919] pci 0000:00:1c.3: enabling device (0106 -> 0107)
[    0.269925]   alloc irq_desc for 19 on node -1
[    0.269928]   alloc kstat_irqs on node -1
[    0.269935] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.269942] pci 0000:00:1c.3: setting latency timer to 64
[    0.269952] pci 0000:00:1e.0: setting latency timer to 64
[    0.269960] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.269965] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.269971] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.269976] pci_bus 0000:01: resource 1 mem: [0xfb000000-0xfdffffff]
[    0.269981] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xdfffffff]
[    0.269986] pci_bus 0000:05: resource 0 io:  [0x1000-0x1fff]
[    0.269991] pci_bus 0000:05: resource 1 mem: [0xfac00000-0xfacfffff]
[    0.269996] pci_bus 0000:05: resource 2 pref mem [0xbfc00000-0xbfcfffff]
[    0.270001] pci_bus 0000:04: resource 0 io:  [0x2000-0x2fff]
[    0.270006] pci_bus 0000:04: resource 1 mem: [0xfad00000-0xfadfffff]
[    0.270011] pci_bus 0000:04: resource 2 pref mem [0xbfd00000-0xbfdfffff]
[    0.270016] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]
[    0.270021] pci_bus 0000:03: resource 1 mem: [0xfae00000-0xfaefffff]
[    0.270026] pci_bus 0000:03: resource 2 pref mem [0xbfe00000-0xbfefffff]
[    0.270031] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.270036] pci_bus 0000:02: resource 1 mem: [0xfaf00000-0xfaffffff]
[    0.270041] pci_bus 0000:02: resource 2 pref mem [0xbff00000-0xbfffffff]
[    0.270046] pci_bus 0000:06: resource 0 io:  [0xb000-0xbfff]
[    0.270051] pci_bus 0000:06: resource 1 mem: [0xfab00000-0xfabfffff]
[    0.270056] pci_bus 0000:06: resource 2 pref mem [0xbfb00000-0xbfbfffff]
[    0.270061] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.270066] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.270131] NET: Registered protocol family 2
[    0.270306] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.270900] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.271582] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.271868] TCP: Hash tables configured (established 131072 bind 65536)
[    0.271873] TCP reno registered
[    0.272046] NET: Registered protocol family 1
[    0.272206] pci 0000:01:00.0: Boot video device
[    0.272544] cpufreq-nforce2: No nForce2 chipset.
[    0.272595] Scanning for low memory corruption every 60 seconds
[    0.272788] audit: initializing netlink socket (disabled)
[    0.272804] type=2000 audit(1275654441.271:1): initialized
[    0.285147] highmem bounce pool size: 64 pages
[    0.285157] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.288131] VFS: Disk quotas dquot_6.5.2
[    0.288249] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.289440] fuse init (API version 7.13)
[    0.289617] msgmni has been set to 1716
[    0.289995] alg: No test for stdrng (krng)
[    0.290110] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.290116] io scheduler noop registered
[    0.290120] io scheduler anticipatory registered
[    0.290124] io scheduler deadline registered
[    0.290207] io scheduler cfq registered (default)
[    0.290442]   alloc irq_desc for 24 on node -1
[    0.290447]   alloc kstat_irqs on node -1
[    0.290460] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.290470] pcieport 0000:00:01.0: setting latency timer to 64
[    0.290633]   alloc irq_desc for 25 on node -1
[    0.290638]   alloc kstat_irqs on node -1
[    0.290650] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.290662] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.290838]   alloc irq_desc for 26 on node -1
[    0.290843]   alloc kstat_irqs on node -1
[    0.290854] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.290866] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.291046]   alloc irq_desc for 27 on node -1
[    0.291050]   alloc kstat_irqs on node -1
[    0.291061] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.291074] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.291277]   alloc irq_desc for 28 on node -1
[    0.291281]   alloc kstat_irqs on node -1
[    0.291293] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.291304] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.291460] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.291487] Firmware did not grant requested _OSC control
[    0.291516] Firmware did not grant requested _OSC control
[    0.291539] Firmware did not grant requested _OSC control
[    0.291562] Firmware did not grant requested _OSC control
[    0.291619] Firmware did not grant requested _OSC control
[    0.291644] Firmware did not grant requested _OSC control
[    0.291669] Firmware did not grant requested _OSC control
[    0.291691] Firmware did not grant requested _OSC control
[    0.291720] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.291905] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.291917] ACPI: Power Button [PWRB]
[    0.292002] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.292008] ACPI: Power Button [PWRF]
[    0.292499] processor LNXCPU:00: registered as cooling_device0
[    0.292617] processor LNXCPU:01: registered as cooling_device1
[    0.298505] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.298632] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.299192] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.301385] brd: module loaded
[    0.302332] loop: module loaded
[    0.302505] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.302679] ata_piix 0000:00:1f.1: version 2.13
[    0.302700] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.302757] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.302865] isapnp: Scanning for PnP cards...
[    0.351867] scsi0 : ata_piix
[    0.395533] scsi1 : ata_piix
[    0.397250] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.397257] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.397304] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.397314] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.397375] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.440957] scsi2 : ata_piix
[    0.441118] scsi3 : ata_piix
[    0.443153] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 19
[    0.443160] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 19
[    0.443910] Fixed MDIO Bus: probed
[    0.443989] PPP generic driver version 2.4.2
[    0.444086] tun: Universal TUN/TAP device driver, 1.6
[    0.444090] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.444271] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.444308]   alloc irq_desc for 23 on node -1
[    0.444313]   alloc kstat_irqs on node -1
[    0.444325] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.444352] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.444359] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.444425] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.444461] ehci_hcd 0000:00:1d.7: debug port 1
[    0.448358] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.448403] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfaafbc00
[    0.477353] Freeing initrd memory: 7777k freed
[    0.481663] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.481887] usb usb1: configuration #1 chosen from 1 choice
[    0.481941] hub 1-0:1.0: USB hub found
[    0.481955] hub 1-0:1.0: 8 ports detected
[    0.482065] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.482096] uhci_hcd: USB Universal Host Controller Interface driver
[    0.482159] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.482172] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.482177] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.482237] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.482269] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000cc00
[    0.482422] usb usb2: configuration #1 chosen from 1 choice
[    0.482469] hub 2-0:1.0: USB hub found
[    0.482481] hub 2-0:1.0: 2 ports detected
[    0.482552] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.482561] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.482566] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.482628] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.482656] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[    0.482798] usb usb3: configuration #1 chosen from 1 choice
[    0.482844] hub 3-0:1.0: USB hub found
[    0.482857] hub 3-0:1.0: 2 ports detected
[    0.482924] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.482933] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.482938] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.482993] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.483033] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[    0.483172] usb usb4: configuration #1 chosen from 1 choice
[    0.483236] hub 4-0:1.0: USB hub found
[    0.483246] hub 4-0:1.0: 2 ports detected
[    0.483317] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.483326] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.483331] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.483392] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.483429] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[    0.483571] usb usb5: configuration #1 chosen from 1 choice
[    0.483616] hub 5-0:1.0: USB hub found
[    0.483626] hub 5-0:1.0: 2 ports detected
[    0.483784] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.483789] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.484586] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.484764] mice: PS/2 mouse device common for all mice
[    0.484946] rtc_cmos 00:02: RTC can wake from S4
[    0.485007] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.485037] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.485226] device-mapper: uevent: version 1.0.3
[    0.485399] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.485506] device-mapper: multipath: version 1.1.0 loaded
[    0.485511] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.485705] EISA: Probing bus 0 at eisa.0
[    0.485714] Cannot allocate resource for EISA slot 1
[    0.485718] Cannot allocate resource for EISA slot 2
[    0.485721] Cannot allocate resource for EISA slot 3
[    0.485725] Cannot allocate resource for EISA slot 4
[    0.485743] EISA: Detected 0 cards.
[    0.485864] cpuidle: using governor ladder
[    0.485868] cpuidle: using governor menu
[    0.486660] TCP cubic registered
[    0.486897] NET: Registered protocol family 10
[    0.487741] lo: Disabled Privacy Extensions
[    0.488356] NET: Registered protocol family 17
[    0.488431] Using IPI No-Shortcut mode
[    0.488556] PM: Resume from disk failed.
[    0.488576] registered taskstats version 1
[    0.488982]   Magic number: 14:496:480
[    0.489081] rtc_cmos 00:02: setting system clock to 2010-06-04 12:27:22 UTC (1275654442)
[    0.489086] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.489089] EDD information not available.
[    0.504439] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.611347] ata3.01: NODEV after polling detection
[    0.619413] ata3.00: ATAPI: HL-DT-STDVD-RAM GH22NS30, 1.01, max UDMA/100
[    0.635443] ata3.00: configured for UDMA/100
[    0.647525] ata4.00: ATA-7: WDC WD1600JS-22NCB1, 10.02E02, max UDMA/133
[    0.647530] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.655559] ata4.00: configured for UDMA/133
[    0.669637] isapnp: No Plug & Play device found
[    0.670976] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NS30 1.01 PQ: 0 ANSI: 5
[    0.674717] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.674722] Uniform CD-ROM driver Revision: 3.20
[    0.674846] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    0.674925] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    0.675083] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1600JS-22N 10.0 PQ: 0 ANSI: 5
[    0.675251] sd 3:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.675274] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    0.675352] sd 3:0:0:0: [sda] Write Protect is off
[    0.675358] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.675415] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.675619]  sda: sda1 sda2 < sda5 >
[    0.719761] sd 3:0:0:0: [sda] Attached SCSI disk
[    0.719778] Freeing unused kernel memory: 656k freed
[    0.720247] Write protecting the kernel text: 4676k
[    0.720301] Write protecting the kernel read-only data: 1840k
[    0.744906] udev: starting version 151
[    0.949525] Floppy drive(s): fd0 is 1.44M
[    0.957506] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    0.957570] via-rhine 0000:06:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.964281] eth0: VIA Rhine III at 0xfab00800, 00:e0:4c:08:05:0f, IRQ 18.
[    0.965007] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[    0.965936] FDC 0 is a post-1991 82077
[    0.979646] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    1.148262] usb 4-1: configuration #1 chosen from 1 choice
[    1.174665] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.175332] usbcore: registered new interface driver hiddev
[    1.191617] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input4
[    1.191830] generic-usb 0003:1267:0201.0001: input,hidraw0: USB HID v1.10 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.2-1/input0
[    1.191882] usbcore: registered new interface driver usbhid
[    1.191890] usbhid: v2.6:USB HID core driver
[    2.698950] Adding 3002360k swap on /dev/sda5.  Priority:-1 extents:1 across:3002360k 
[    3.029867] udev: starting version 151
[    3.719664] type=1505 audit(1275654445.726:2):  operation="profile_load" pid=429 name="/sbin/dhclient3"
[    3.720588] type=1505 audit(1275654445.730:3):  operation="profile_load" pid=429 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    3.721028] type=1505 audit(1275654445.730:4):  operation="profile_load" pid=429 name="/usr/lib/connman/scripts/dhclient-script"
[    3.893439] lp: driver loaded but no devices found
[    4.211946] parport_pc 00:08: reported by Plug and Play ACPI
[    4.211979] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[    4.258975] ppdev: user-space parallel port driver
[    4.279227] intel_rng: Firmware space is locked read-only. If you can't or
[    4.279230] intel_rng: don't want to disable this in firmware setup, and if
[    4.279231] intel_rng: you are certain that your system has a functional
[    4.279233] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    4.309730] lp0: using parport0 (interrupt-driven).
[    4.377607] vga16fb: initializing
[    4.377616] vga16fb: mapped to 0xc00a0000
[    4.377915] fb0: VGA16 VGA frame buffer device
[    4.488278] Linux video capture interface: v2.00
[    4.562218] Linux agpgart interface v0.103
[    4.562949] Console: switching to colour frame buffer device 80x30
[    4.731763] nvidia: module license 'NVIDIA' taints kernel.
[    4.731768] Disabling lock debugging due to kernel taint
[    5.185807] saa7130/34: v4l2 driver version 0.2.15 loaded
[    5.185870]   alloc irq_desc for 21 on node -1
[    5.185875]   alloc kstat_irqs on node -1
[    5.185885] saa7134 0000:06:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    5.185895] saa7133[0]: found at 0000:06:00.0, rev: 209, irq: 21, latency: 32, mmio: 0xfab00000
[    5.185906] saa7133[0]: subsystem: 1461:f11d, board: Avermedia PCI pure analog (M135A) [card=149,autodetected]
[    5.185936] saa7133[0]: board init: gpio is 40000
[    5.186159] input: saa7134 IR (Avermedia PCI pure  as /devices/pci0000:00/0000:00:1e.0/0000:06:00.0/input/input5
[    5.186342] IRQ 21/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.321574] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.321586] nvidia 0000:01:00.0: setting latency timer to 64
[    5.321934] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
[    5.345199] saa7133[0]: i2c eeprom 00: 61 14 1d f1 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    5.345223] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[    5.345245] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 56 ff ff ff ff
[    5.345269] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345293] saa7133[0]: i2c eeprom 40: ff 22 00 c0 96 ff 03 30 15 00 ff ff ff ff ff ff
[    5.345315] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345339] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345361] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345384] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345406] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345429] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345451] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345474] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345498] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345526] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345554] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.345585] i2c i2c-0: Invalid 7-bit address 0x7a
[    5.860146] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[    5.944036] tda829x 0-004b: setting tuner address to 60
[    6.296038] tda829x 0-004b: type set to tda8290+75a
[    7.647448] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.647542] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.846068] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[    9.937825] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[    9.989472] type=1505 audit(1275654451.998:5):  operation="profile_load" pid=710 name="/usr/share/gdm/guest-session/Xsession"
[    9.992497] type=1505 audit(1275654452.002:6):  operation="profile_replace" pid=716 name="/sbin/dhclient3"
[    9.993227] type=1505 audit(1275654452.002:7):  operation="profile_replace" pid=716 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.993620] type=1505 audit(1275654452.002:8):  operation="profile_replace" pid=716 name="/usr/lib/connman/scripts/dhclient-script"
[   10.217140] saa7133[0]: registered device video0 [v4l2]
[   10.217185] saa7133[0]: registered device vbi0
[   10.217226] saa7133[0]: registered device radio0
[   10.478799] saa7134 ALSA driver for DMA sound loaded
[   10.478818] IRQ 21/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.478860] saa7133[0]/alsa: saa7133[0] at 0xfab00000 irq 21 registered as card -2
[   10.765883] type=1505 audit(1275654452.775:9):  operation="profile_load" pid=717 name="/usr/bin/evince"
[   10.775436] type=1505 audit(1275654452.783:10):  operation="profile_load" pid=717 name="/usr/bin/evince-previewer"
[   10.781634] type=1505 audit(1275654452.790:11):  operation="profile_load" pid=717 name="/usr/bin/evince-thumbnailer"
[   10.897214] type=1505 audit(1275654452.906:12):  operation="profile_load" pid=811 name="/usr/lib/cups/backend/cups-pdf"
[   10.898024] type=1505 audit(1275654452.906:13):  operation="profile_load" pid=811 name="/usr/sbin/cupsd"
[   10.929595] type=1505 audit(1275654452.938:14):  operation="profile_load" pid=812 name="/usr/sbin/mysqld-akonadi"
[   20.720035] eth0: no IPv6 routers present
[  735.088049] end_request: I/O error, dev fd0, sector 0
[  773.147337] end_request: I/O error, dev fd0, sector 0
[  811.200212] end_request: I/O error, dev fd0, sector 0
[  811.200221] __ratelimit: 3 callbacks suppressed
[  811.200225] Buffer I/O error on device fd0, logical block 0
[  849.263207] end_request: I/O error, dev fd0, sector 0
[  887.328465] end_request: I/O error, dev fd0, sector 0
[  887.328475] Buffer I/O error on device fd0, logical block 0
[  925.400749] end_request: I/O error, dev fd0, sector 0
[  925.400759] Buffer I/O error on device fd0, logical block 0
[  963.471231] end_request: I/O error, dev fd0, sector 0
[  963.471241] Buffer I/O error on device fd0, logical block 0
[ 1001.535184] end_request: I/O error, dev fd0, sector 0
[ 1001.535193] Buffer I/O error on device fd0, logical block 0
[ 1039.600830] end_request: I/O error, dev fd0, sector 0
[ 1039.600839] Buffer I/O error on device fd0, logical block 0
[ 1077.671942] end_request: I/O error, dev fd0, sector 0
[ 1077.671952] Buffer I/O error on device fd0, logical block 0
[ 1115.751898] end_request: I/O error, dev fd0, sector 0
[ 1115.751908] Buffer I/O error on device fd0, logical block 0
[ 1153.828396] end_request: I/O error, dev fd0, sector 0
[ 1153.828405] Buffer I/O error on device fd0, logical block 0
[ 1191.902922] end_request: I/O error, dev fd0, sector 0
[ 1191.902932] Buffer I/O error on device fd0, logical block 0
[ 1229.979011] end_request: I/O error, dev fd0, sector 0
[ 1229.979020] Buffer I/O error on device fd0, logical block 0
[ 1268.044203] end_request: I/O error, dev fd0, sector 0
[ 1268.044212] Buffer I/O error on device fd0, logical block 0
[ 1306.111231] end_request: I/O error, dev fd0, sector 0
[ 1306.111240] Buffer I/O error on device fd0, logical block 0
[ 1344.179976] end_request: I/O error, dev fd0, sector 0
[ 1344.179986] Buffer I/O error on device fd0, logical block 0
[ 1382.247740] end_request: I/O error, dev fd0, sector 0
[ 1382.247749] Buffer I/O error on device fd0, logical block 0
[ 1420.315845] end_request: I/O error, dev fd0, sector 0
[ 1420.315856] Buffer I/O error on device fd0, logical block 0


what is all the **errore on device fd0?!**
please help me get the TV ON!! :]

---

### Post by sisco311 on 2010-06-04
fd0 is the first floppy disk drive. You can ignore that error.


Your card should be automatically detected. Did you try a tv application like tvtime or kdetv? 

Check if the appropriate module is loaded:
```
lsmod | grep saa
```
and the device node is created:
```
ls -al /dev/video*
```

---

### Post by dpkg on 2010-06-05
Sorry for the long waiting i was on my girl this wekkend.

well, i post the lines on the terminal this is what i got:


> benny@benny-desktop:~$ lsmod | grep saa
saa7134_alsa           10380  1 
snd_pcm                70662  5 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    54148  22 saa7134_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
saa7134               143391  1 saa7134_alsa
ir_common              38875  1 saa7134
v4l2_common            15431  2 tuner,saa7134
videodev               34361  3 tuner,saa7134,v4l2_common
videobuf_dma_sg        10782  2 saa7134_alsa,saa7134
videobuf_core          16356  2 saa7134,videobuf_dma_sg
tveeprom               11102  1 saa7134
benny@benny-desktop:~$ ls -al /dev/video*
crw-rw----+ 1 root video 81, 0 2010-06-04 15:27 /dev/video0


stilll i use on "ME Tv" and when i try to pick a device i got an error massage that says this **"There are no digital tuner devices available"**

---

### Post by xc3RnbFO8P on 2010-06-06
Try **TVtime**

---

