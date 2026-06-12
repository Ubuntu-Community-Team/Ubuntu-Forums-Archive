---
title: "Who can help getting a Pinnacle TV-card (PCI) working under Jaunty 9.0.4?"
date: 2009-08-02
forum: Multimedia Software
---

### Post by bosmana on 2009-08-02
Hi,

Another question from a complete newby:

I have Xubuntu running fine on my old machine, yet cannot seem to get the Pinnacle TV card in the PCI slot to work with TVTime. 

Can anyone tell me what I do wrong?

The listing for lpsci:
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)


and for dmesg:
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-13-generic (buildd@vernadsky) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 (Ubuntu 2.6.28-13.45-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x3bef0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  modified: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
[    0.000000]  modified: 000000003bef3000 - 000000003bf00000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378ad000 - 37fef5c7
[    0.000000] Allocated new RAMDISK: 0087b000 - 00fbd5c7
[    0.000000] Move RAMDISK from 00000000378ad000 - 0000000037fef5c6 to 0087b000 - 00fbd5c6
[    0.000000] ACPI: RSDP 000F7930, 0014 (r0 P4M80P)
[    0.000000] ACPI: RSDT 3BEF3040, 002C (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3BEF30C0, 0074 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3BEF3180, 4EA6 (r1 P4M80P AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BEF0000, 0040
[    0.000000] ACPI: APIC 3BEF8080, 0084 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 74MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087b000 - 0000fbd5c7]      NEW RAMDISK ==> [000087b000 - 0000fbd5c7]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f37a0] 000f37a0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0003bef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bef0
[    0.000000] On node 0 totalpages: 245375
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 150 pages used for memmap
[    0.000000]   HighMem zone: 19036 pages, LIFO batch:3
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3bf00000:c2d00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243457
[    0.000000] Kernel command line: root=UUID=a7fc80dc-0675-4c21-90d6-5ffc406bee75 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2133.713 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 4909440 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 952624k/981952k available (4110k kernel code, 28584k reserved, 2196k data, 532k init, 76744k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc0503b9f - 0xc0728e60   (2196 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0503b9f   (4110 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004022] Calibrating delay loop (skipped), value calculated using timer frequency.. 4267.42 BogoMIPS (lpj=8534852)
[    0.004055] Security Framework initialized
[    0.004069] SELinux:  Disabled at boot.
[    0.004104] AppArmor: AppArmor initialized
[    0.004122] Mount-cache hash table entries: 512
[    0.004383] Initializing cgroup subsys ns
[    0.004392] Initializing cgroup subsys cpuacct
[    0.004397] Initializing cgroup subsys memory
[    0.004405] Initializing cgroup subsys freezer
[    0.004435] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004440] CPU: L2 cache: 256K
[    0.004445] CPU: Hyper-Threading is disabled
[    0.004452] using mwait in idle threads.
[    0.004475] Checking 'hlt' instruction... OK.
[    0.021271] SMP alternatives: switching to UP code
[    0.200037] ACPI: Core revision 20080926
[    0.208444] ACPI: Checking initramfs for custom DSDT
[    0.633422] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.675088] CPU0: Intel(R) Celeron(R) CPU 2.13GHz stepping 01
[    0.676002] Brought up 1 CPUs
[    0.676002] Total of 1 processors activated (4267.42 BogoMIPS).
[    0.676002] CPU0 attaching NULL sched-domain.
[    0.676002] net_namespace: 776 bytes
[    0.676002] Booting paravirtualized kernel on bare hardware
[    0.676002] Time:  9:23:51  Date: 08/02/09
[    0.676002] regulator: core version 0.5
[    0.676002] NET: Registered protocol family 16
[    0.676002] EISA bus registered
[    0.676002] ACPI: bus type pci registered
[    0.683331] PCI: PCI BIOS revision 2.10 entry at 0xf9f30, last bus=1
[    0.683335] PCI: Using configuration type 1 for base access
[    0.685998] ACPI: EC: Look up EC in DSDT
[    0.698253] ACPI: Interpreter enabled
[    0.698271] ACPI: (supports S0 S3 S4 S5)
[    0.698308] ACPI: Using IOAPIC for interrupt routing
[    0.709441] ACPI: No dock devices found.
[    0.709467] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.709564] pci 0000:00:00.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.709941] pci 0000:00:01.0: supports D1
[    0.710004] pci 0000:00:0f.0: reg 10 io port: [0xfc00-0xfc07]
[    0.710014] pci 0000:00:0f.0: reg 14 io port: [0xf800-0xf803]
[    0.710023] pci 0000:00:0f.0: reg 18 io port: [0xf400-0xf407]
[    0.710033] pci 0000:00:0f.0: reg 1c io port: [0xf000-0xf003]
[    0.710042] pci 0000:00:0f.0: reg 20 io port: [0xec00-0xec0f]
[    0.710051] pci 0000:00:0f.0: reg 24 io port: [0xe800-0xe8ff]
[    0.710148] pci 0000:00:0f.1: reg 20 io port: [0xe400-0xe40f]
[    0.710247] pci 0000:00:10.0: reg 20 io port: [0xe000-0xe01f]
[    0.710272] pci 0000:00:10.0: supports D1 D2
[    0.710275] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.710281] pci 0000:00:10.0: PME# disabled
[    0.710346] pci 0000:00:10.1: reg 20 io port: [0xdc00-0xdc1f]
[    0.710371] pci 0000:00:10.1: supports D1 D2
[    0.710374] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.710379] pci 0000:00:10.1: PME# disabled
[    0.710444] pci 0000:00:10.2: reg 20 io port: [0xd800-0xd81f]
[    0.710469] pci 0000:00:10.2: supports D1 D2
[    0.710471] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.710477] pci 0000:00:10.2: PME# disabled
[    0.710542] pci 0000:00:10.3: reg 20 io port: [0xd400-0xd41f]
[    0.710566] pci 0000:00:10.3: supports D1 D2
[    0.710569] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.710575] pci 0000:00:10.3: PME# disabled
[    0.710617] pci 0000:00:10.4: reg 10 32bit mmio: [0xfdfff000-0xfdfff0ff]
[    0.710665] pci 0000:00:10.4: supports D1 D2
[    0.710667] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.710673] pci 0000:00:10.4: PME# disabled
[    0.710759] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.710820] pci 0000:00:11.5: reg 10 io port: [0xd000-0xd0ff]
[    0.710869] pci 0000:00:11.5: supports D1 D2
[    0.710915] pci 0000:00:12.0: reg 10 io port: [0xcc00-0xccff]
[    0.710925] pci 0000:00:12.0: reg 14 32bit mmio: [0xfdffe000-0xfdffe0ff]
[    0.710968] pci 0000:00:12.0: supports D1 D2
[    0.710971] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.710976] pci 0000:00:12.0: PME# disabled
[    0.711049] pci 0000:01:00.0: reg 10 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.711057] pci 0000:01:00.0: reg 14 32bit mmio: [0xfb000000-0xfbffffff]
[    0.711086] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.711097] pci 0000:01:00.0: supports D1 D2
[    0.711150] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
[    0.711156] pci 0000:00:01.0: bridge 32bit mmio: [0xfb000000-0xfcffffff]
[    0.711163] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf4000000-0xf7ffffff]
[    0.711175] bus 00 -> node 0
[    0.711191] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.789694] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.790034] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.790376] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.790677] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.790973] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.791254] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.791536] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.791817] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.792220] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[    0.792575] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[    0.792927] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[    0.793343] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[    0.793584] ACPI: WMI: Mapper loaded
[    0.793997] SCSI subsystem initialized
[    0.794095] libata version 3.00 loaded.
[    0.794202] usbcore: registered new interface driver usbfs
[    0.794238] usbcore: registered new interface driver hub
[    0.794301] usbcore: registered new device driver usb
[    0.794553] PCI: Using ACPI for IRQ routing
[    0.794728] Bluetooth: Core ver 2.13
[    0.794728] NET: Registered protocol family 31
[    0.794728] Bluetooth: HCI device and connection manager initialized
[    0.794728] Bluetooth: HCI socket layer initialized
[    0.794728] NET: Registered protocol family 8
[    0.794728] NET: Registered protocol family 20
[    0.794728] NetLabel: Initializing
[    0.794728] NetLabel:  domain hash size = 128
[    0.794728] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.794728] NetLabel:  unlabeled traffic allowed by default
[    0.794728] AppArmor: AppArmor Filesystem Enabled
[    0.794728] pnp: PnP ACPI init
[    0.794728] ACPI: bus type pnp registered
[    0.802614] pnp: PnP ACPI: found 13 devices
[    0.802620] ACPI: ACPI bus type pnp unregistered
[    0.802629] PnPBIOS: Disabled by ACPI PNP
[    0.802653] system 00:00: iomem range 0xcc000-0xcffff has been reserved
[    0.802658] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.802662] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.802666] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.802670] system 00:00: iomem range 0x3bef0000-0x3befffff could not be reserved
[    0.802675] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.802679] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.802683] system 00:00: iomem range 0x100000-0x3beeffff could not be reserved
[    0.802687] system 00:00: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.802691] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.802695] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.802707] system 00:02: ioport range 0x400-0x47f has been reserved
[    0.802711] system 00:02: ioport range 0x500-0x50f has been reserved
[    0.802732] system 00:03: ioport range 0xb78-0xb7b has been reserved
[    0.802736] system 00:03: ioport range 0xf78-0xf7b has been reserved
[    0.802740] system 00:03: ioport range 0xa78-0xa7b has been reserved
[    0.802743] system 00:03: ioport range 0xe78-0xe7b has been reserved
[    0.802747] system 00:03: ioport range 0xbbc-0xbbf has been reserved
[    0.802750] system 00:03: ioport range 0xfbc-0xfbf has been reserved
[    0.802754] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.802758] system 00:03: ioport range 0x800-0x87f has been reserved
[    0.802761] system 00:03: ioport range 0x880-0x8ff has been reserved
[    0.802765] system 00:03: ioport range 0x290-0x297 has been reserved
[    0.837641] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.837648] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    0.837656] pci 0000:00:01.0:   MEM window: 0xfb000000-0xfcffffff
[    0.837663] pci 0000:00:01.0:   PREFETCH window: 0x000000f4000000-0x000000f7ffffff
[    0.837685] pci 0000:00:01.0: setting latency timer to 64
[    0.837692] bus: 00 index 0 io port: [0x00-0xffff]
[    0.837696] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.837699] bus: 01 index 0 io port: [0xb000-0xbfff]
[    0.837702] bus: 01 index 1 mmio: [0xfb000000-0xfcffffff]
[    0.837706] bus: 01 index 2 mmio: [0xf4000000-0xf7ffffff]
[    0.837709] bus: 01 index 3 mmio: [0x0-0x0]
[    0.837727] NET: Registered protocol family 2
[    0.837968] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.838510] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.840032] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.840781] TCP: Hash tables configured (established 131072 bind 65536)
[    0.840788] TCP reno registered
[    0.841050] NET: Registered protocol family 1
[    0.841271] checking if image is initramfs... it is
[    1.339974] Switched to high resolution mode on CPU 0
[    1.721583] Freeing initrd memory: 7433k freed
[    1.721753] cpufreq: No nForce2 chipset.
[    1.722011] audit: initializing netlink socket (disabled)
[    1.722040] type=2000 audit(1249205031.720:1): initialized
[    1.733415] highmem bounce pool size: 64 pages
[    1.733426] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.735267] VFS: Disk quotas dquot_6.5.1
[    1.735393] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.736551] fuse init (API version 7.10)
[    1.736728] msgmni has been set to 1725
[    1.737112] alg: No test for stdrng (krng)
[    1.737147] io scheduler noop registered
[    1.737151] io scheduler anticipatory registered
[    1.737154] io scheduler deadline registered
[    1.737204] io scheduler cfq registered (default)
[    1.737232] PCI: VIA PCI bridge detected.Disabling DAC.
[    9.736014] pci 0000:00:10.4: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    9.736042] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    9.736055] pci 0000:01:00.0: Boot video device
[    9.744380] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    9.744397] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    9.744616] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    9.744621] ACPI: Power Button (FF) [PWRF]
[    9.744703] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    9.744708] ACPI: Power Button (CM) [PWRB]
[    9.744785] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    9.744794] ACPI: Sleep Button (CM) [SLPB]
[    9.745333] processor ACPI_CPU:00: registered as cooling_device0
[    9.750724] isapnp: Scanning for PnP cards...
[   10.103051] isapnp: No Plug & Play device found
[   10.105135] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[   10.105266] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.105881] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.107315] brd: module loaded
[   10.107992] loop: module loaded
[   10.108230] Fixed MDIO Bus: probed
[   10.108241] PPP generic driver version 2.4.2
[   10.108363] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[   10.108436] Driver 'sd' needs updating - please use bus_type methods
[   10.108452] Driver 'sr' needs updating - please use bus_type methods
[   10.108674] sata_via 0000:00:0f.0: version 2.4
[   10.109149] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   10.109165] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[   10.109232] sata_via 0000:00:0f.0: routed to hard irq line 11
[   10.109245] sata_via 0000:00:0f.0: setting latency timer to 64
[   10.109426] scsi0 : sata_via
[   10.109631] scsi1 : sata_via
[   10.109713] ata1: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 20
[   10.109718] ata2: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 20
[   10.312048] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   10.524036] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   10.534934] pata_via 0000:00:0f.1: version 0.3.3
[   10.534966] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[   10.535046] pata_via 0000:00:0f.1: setting latency timer to 64
[   10.535241] scsi2 : pata_via
[   10.535386] scsi3 : pata_via
[   10.539060] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[   10.539065] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[   10.708536] ata3.00: ATA-7: SAMSUNG SP0842N, BH100-35, max UDMA/100
[   10.708541] ata3.00: 156301488 sectors, multi 1: LBA48 
[   10.756622] ata3.01: ATA-7: ST3320833A, 3.AAH, max UDMA/100
[   10.756626] ata3.01: 625142448 sectors, multi 1: LBA48 
[   10.788426] ata3.00: configured for UDMA/100
[   10.831406] ata3.01: configured for UDMA/100
[   11.032396] ata4.00: ATAPI: TSSTcorpCD/DVDW SH-W162C, TS10, max UDMA/33
[   11.072303] ata4.00: configured for UDMA/33
[   11.072987] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG SP0842N  BH10 PQ: 0 ANSI: 5
[   11.073211] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[   11.073245] sd 2:0:0:0: [sda] Write Protect is off
[   11.073249] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.073297] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.073442] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[   11.073473] sd 2:0:0:0: [sda] Write Protect is off
[   11.073477] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.073523] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.073531]  sda: sda1 sda2 < sda5 >
[   11.103687] sd 2:0:0:0: [sda] Attached SCSI disk
[   11.103800] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   11.103996] scsi 2:0:1:0: Direct-Access     ATA      ST3320833A       3.AA PQ: 0 ANSI: 5
[   11.104228] sd 2:0:1:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   11.104260] sd 2:0:1:0: [sdb] Write Protect is off
[   11.104264] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   11.104312] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.104460] sd 2:0:1:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   11.104490] sd 2:0:1:0: [sdb] Write Protect is off
[   11.104494] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   11.104541] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.104549]  sdb: sdb1
[   11.120299] sd 2:0:1:0: [sdb] Attached SCSI disk
[   11.120406] sd 2:0:1:0: Attached scsi generic sg1 type 0
[   11.121543] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-W162C TS10 PQ: 0 ANSI: 5
[   11.131152] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   11.131160] Uniform CD-ROM driver Revision: 3.20
[   11.131386] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   11.131480] sr 3:0:0:0: Attached scsi generic sg2 type 5
[   11.131761] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   11.132289] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   11.132306] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[   11.132349] ehci_hcd 0000:00:10.4: setting latency timer to 64
[   11.132356] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   11.132527] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[   11.132616] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfdfff000
[   11.144025] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[   11.144158] usb usb1: configuration #1 chosen from 1 choice
[   11.144210] hub 1-0:1.0: USB hub found
[   11.144231] hub 1-0:1.0: 8 ports detected
[   11.144466] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   11.144513] uhci_hcd: USB Universal Host Controller Interface driver
[   11.144595] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[   11.144612] uhci_hcd 0000:00:10.0: setting latency timer to 64
[   11.144617] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   11.144734] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[   11.144768] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000e000
[   11.144938] usb usb2: configuration #1 chosen from 1 choice
[   11.144991] hub 2-0:1.0: USB hub found
[   11.145006] hub 2-0:1.0: 2 ports detected
[   11.145186] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[   11.145200] uhci_hcd 0000:00:10.1: setting latency timer to 64
[   11.145204] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   11.145312] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[   11.145343] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000dc00
[   11.145475] usb usb3: configuration #1 chosen from 1 choice
[   11.145524] hub 3-0:1.0: USB hub found
[   11.145541] hub 3-0:1.0: 2 ports detected
[   11.145724] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[   11.145738] uhci_hcd 0000:00:10.2: setting latency timer to 64
[   11.145742] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   11.145842] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[   11.145874] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[   11.146007] usb usb4: configuration #1 chosen from 1 choice
[   11.146063] hub 4-0:1.0: USB hub found
[   11.146078] hub 4-0:1.0: 2 ports detected
[   11.146249] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[   11.146263] uhci_hcd 0000:00:10.3: setting latency timer to 64
[   11.146267] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   11.146357] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[   11.146390] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d400
[   11.146533] usb usb5: configuration #1 chosen from 1 choice
[   11.146580] hub 5-0:1.0: USB hub found
[   11.146593] hub 5-0:1.0: 2 ports detected
[   11.146890] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.147429] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.147441] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.147693] mice: PS/2 mouse device common for all mice
[   11.148061] rtc_cmos 00:05: RTC can wake from S4
[   11.148151] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[   11.148212] rtc0: alarms up to one year, y3k, 242 bytes nvram
[   11.148357] device-mapper: uevent: version 1.0.3
[   11.148610] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[   11.148724] device-mapper: multipath: version 1.0.5 loaded
[   11.148730] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.148920] EISA: Probing bus 0 at eisa.0
[   11.148970] EISA: Detected 0 cards.
[   11.149041] cpuidle: using governor ladder
[   11.149046] cpuidle: using governor menu
[   11.149920] TCP cubic registered
[   11.150069] NET: Registered protocol family 10
[   11.150766] lo: Disabled Privacy Extensions
[   11.151359] NET: Registered protocol family 17
[   11.151417] Bluetooth: L2CAP ver 2.11
[   11.151421] Bluetooth: L2CAP socket layer initialized
[   11.151425] Bluetooth: SCO (Voice Link) ver 0.6
[   11.151428] Bluetooth: SCO socket layer initialized
[   11.151514] Bluetooth: RFCOMM socket layer initialized
[   11.151531] Bluetooth: RFCOMM TTY layer initialized
[   11.151534] Bluetooth: RFCOMM ver 1.10
[   11.151651] Using IPI No-Shortcut mode
[   11.151853] registered taskstats version 1
[   11.152076]   Magic number: 5:935:372
[   11.152216] rtc_cmos 00:05: setting system clock to 2009-08-02 09:24:02 UTC (1249205042)
[   11.152221] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   11.152224] EDD information not available.
[   11.153078] Freeing unused kernel memory: 532k freed
[   11.153256] Write protecting the kernel text: 4112k
[   11.153312] Write protecting the kernel read-only data: 1524k
[   11.188171] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[   11.688059] FDC 0 is a post-1991 82077
[   12.043719] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   12.043730] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   12.044374] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   12.044393] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[   12.044405] via-rhine 0000:00:12.0: setting latency timer to 64
[   12.045522] eth0: VIA Rhine II at 0xfdffe000, 00:16:17:1f:80:ed, IRQ 23.
[   12.046235] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link cde1.
[   12.726296] PM: Starting manual resume from disk
[   12.726305] PM: Resume from partition 8:5
[   12.726307] PM: Checking hibernation image.
[   12.726615] PM: Resume from disk failed.
[   12.762052] kjournald starting.  Commit interval 5 seconds
[   12.762082] EXT3-fs: mounted filesystem with ordered data mode.
[   18.298650] udev: starting version 141
[   18.515944] Linux agpgart interface v0.103
[   18.588405] agpgart: Detected VIA VT3314 chipset
[   18.599582] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   18.616362] parport_pc 00:0a: reported by Plug and Play ACPI
[   18.616424] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   18.677508] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.155144] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   19.339331] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   19.630372] psmouse serio1: ID: 10 00 64ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   19.671415] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   19.671598] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   19.953153] ppdev: user-space parallel port driver
[   20.272241] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   20.465393] lp0: using parport0 (interrupt-driven).
[   20.660842] Adding 1293192k swap on /dev/sda5.  Priority:-1 extents:1 across:1293192k
[   21.262695] EXT3 FS on sda1, internal journal
[   22.289027] kjournald starting.  Commit interval 5 seconds
[   22.289502] EXT3 FS on sdb1, internal journal
[   22.289514] EXT3-fs: mounted filesystem with ordered data mode.
[   22.769600] type=1505 audit(1249197854.115:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1902
[   22.769962] type=1505 audit(1249197854.115:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1902
[   22.770160] type=1505 audit(1249197854.115:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1902
[   22.770314] type=1505 audit(1249197854.115:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1902
[   23.004053] type=1505 audit(1249197854.351:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1907
[   23.004510] type=1505 audit(1249197854.351:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1907
[   23.058787] type=1505 audit(1249197854.403:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1911
[   28.969074] RPC: Registered udp transport module.
[   28.969080] RPC: Registered tcp transport module.
[   29.045668] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   29.195948] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   29.199954] NFSD: starting 90-second grace period
[   31.566719] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.566726] Bluetooth: BNEP filters: protocol multicast
[   31.599937] Bridge firewalling registered
[   36.655155] eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[   46.716021] eth0: no IPv6 routers present

---

### Post by realzippy on 2009-08-02
...the kernel NOT seems to recognize your TV card.Do you know its name?

---

### Post by bosmana on 2009-08-02
ooops, you are right, the PCI card was not entirely in the slot. After pushing it in, and rebooting the lspci gave me this:

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:07.0 Non-VGA unclassified device: Brooktree Corporation Bt878 Video Capture (rev 11)
00:07.1 Non-VGA unclassified device: Brooktree Corporation Device 087a (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)


So it looks like the card is ssen as "Brooktree Corporation Bt878 Video Capture (rev 11)"

Does that help?

---

### Post by realzippy on 2009-08-03
please type in terminal :

dmesg | grep bttv

and post the output.

---

### Post by bosmana on 2009-08-03
Thanks, I will Realzippy

However, this week I work in Sweden again, and my Xubuntu machine is back home in Holland. So it will only be possible this Saturday. I appreciate your help, and will post theoutput right after returning home.

Cheers
Arnold

---

### Post by bosmana on 2009-08-07
> **realzippy said:**
> please type in terminal :

dmesg | grep bttv

and post the output.


This is it:
[   19.765642] bttv: driver version 0.9.17 loaded
[   19.765649] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   19.766115] bttv: Bt8xx card found (0).
[   19.766146] bttv 0000:00:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.766162] bttv0: Bt878 (rev 2) at 0000:00:06.0, irq: 17, latency: 16, mmio: 0xfdfff000
[   19.766319] bttv0: detected: (Askey Magic/others) TView99 CPH06x [card=38], PCI subsystem ID is 144f:3000
[   19.766325] bttv0: using: Askey CPH06X TView99 [card=38,autodetected]
[   19.766394] bttv0: gpio: en=00000000, out=00000000 in=00ffefff [init]
[   19.766590] bttv0: tuner type=1
[   19.766598] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   19.767087] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   19.767575] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   19.966761] bttv0: registered device video0
[   19.966927] bttv0: registered device vbi0
[   19.966956] bttv0: PLL: 28636363 => 35468950 .. ok
[   19.996925] input: bttv IR (card=38) as /devices/pci0000:00/0000:00:06.0/input/input6

---

### Post by bosmana on 2009-08-09
This is the output file you asked for:
[   19.765642] bttv: driver version 0.9.17 loaded
[   19.765649] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   19.766115] bttv: Bt8xx card found (0).
[   19.766146] bttv 0000:00:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.766162] bttv0: Bt878 (rev 2) at 0000:00:06.0, irq: 17, latency: 16, mmio: 0xfdfff000
[   19.766319] bttv0: detected: (Askey Magic/others) TView99 CPH06x [card=38], PCI subsystem ID is 144f:3000
[   19.766325] bttv0: using: Askey CPH06X TView99 [card=38,autodetected]
[   19.766394] bttv0: gpio: en=00000000, out=00000000 in=00ffefff [init]
[   19.766590] bttv0: tuner type=1
[   19.766598] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   19.767087] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   19.767575] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   19.966761] bttv0: registered device video0
[   19.966927] bttv0: registered device vbi0
[   19.966956] bttv0: PLL: 28636363 => 35468950 .. ok
[   19.996925] input: bttv IR (card=38) as /devices/pci0000:00/0000:00:06.0/input/input6

---

### Post by realzippy on 2009-08-18
...output looks good.Which software do you use for watching TV?

---

### Post by cascade9 on 2009-08-18
This might help-

[http://tldp.org/HOWTO/html_single/BTTV/](http://tldp.org/HOWTO/html_single/BTTV/)

---

