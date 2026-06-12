---
title: "Linksys wpc54g v4 not working on karmic"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by Joe Ker1086 on 2010-03-29
Hello:

I really need to get a linksys wpc54g version 4 pcmcia card to work....i have never really had a lot of problems with wireless and thit is a friends laptop that he wanted ubuntu on......if i cant get it to work he will go back to windows and i would not like that to happen lol....here is the output of dmesg and ifconfig lspci and lspcmcia....any help would be appriciated

```
thomas@thomas-laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bef0000 (usable)
[    0.000000]  BIOS-e820: 000000001bef0000 - 000000001beff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001beff000 - 000000001bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bf00000 - 000000001c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x1bef0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DAFFF uncachable
[    0.000000]   DB000-DBFFF write-protect
[    0.000000]   DC000-DFFFF write-back
[    0.000000]   E0000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF0000000 write-back
[    0.000000]   1 base 010000000 mask FF8000000 write-back
[    0.000000]   2 base 018000000 mask FFC000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001bef0000 (usable)
[    0.000000]  modified: 000000001bef0000 - 000000001beff000 (ACPI data)
[    0.000000]  modified: 000000001beff000 - 000000001bf00000 (ACPI NVS)
[    0.000000]  modified: 000000001bf00000 - 000000001c000000 (reserved)
[    0.000000]  modified: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001bef0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001bc00000 page 2M
[    0.000000]  001bc00000 - 001bef0000 page 4k
[    0.000000] kernel direct mapping tables up to 1bef0000 @ 10000-15000
[    0.000000] RAMDISK: 14828000 - 14f73957
[    0.000000] ACPI: RSDP 000f7290 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 1bef8b70 00030 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 1befee2b 00074 (v01 ATI    Raptor   06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 1bef8ba0 0628B (v01    ATI U1_M1535 06040000 MSFT 0100000D)
[    0.000000] ACPI: FACS 1befffc0 00040
[    0.000000] ACPI: BOOT 1befee9f 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 1befeec7 00139 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 446MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1bef0000
[    0.000000]   low ram: 0 - 1bef0000
[    0.000000]   node 0 low ram: 00000000 - 1bef0000
[    0.000000]   node 0 bootmap 00011000 - 000147e0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001bef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [0014828000 - 0014f73957]          RAMDISK ==> [0014828000 - 0014f73957]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008ae000 - 00008b1234]              BRK ==> [00008ae000 - 00008b1234]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000015000]          BOOTMAP ==> [0000011000 - 0000015000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001bef0
[    0.000000]   HighMem  0x0001bef0 -> 0x0001bef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001bef0
[    0.000000] On node 0 totalpages: 114303
[    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 862 pages used for memmap
[    0.000000]   Normal zone: 109458 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 1c000000 (gap: 1c000000:e3fc0000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1382000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113409
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=67b39849-a8d8-49ee-9cea-15a1765ffecf ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2288000 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 435292k/457664k available (4578k kernel code, 21656k reserved, 2146k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xdc6f0000 - 0xff7fe000   ( 561 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdbef0000   ( 446 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2120.219 MHz processor.
[    0.001416] Console: colour VGA+ 80x25
[    0.001422] console [tty0] enabled
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 4240.43 BogoMIPS (lpj=8480876)
[    0.004052] Security Framework initialized
[    0.004102] AppArmor: AppArmor initialized
[    0.004114] Mount-cache hash table entries: 512
[    0.004340] Initializing cgroup subsys ns
[    0.004347] Initializing cgroup subsys cpuacct
[    0.004353] Initializing cgroup subsys memory
[    0.004367] Initializing cgroup subsys freezer
[    0.004370] Initializing cgroup subsys net_cls
[    0.004391] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004395] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004402] mce: CPU supports 4 MCE banks
[    0.004431] Performance Counters: AMD PMU driver.
[    0.004438] ------------[ cut here ]------------
[    0.004457] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/apic/apic.c:247 native_apic_write_dummy+0x33/0x40()
[    0.004461] Hardware name: Presario 2100 (DZ414U)   
[    0.004464] Modules linked in:
[    0.004469] Pid: 0, comm: swapper Not tainted 2.6.31-20-generic #58-Ubuntu
[    0.004473] Call Trace:
[    0.004490]  [<c01450ad>] warn_slowpath_common+0x6d/0xa0
[    0.004495]  [<c011d713>] ? native_apic_write_dummy+0x33/0x40
[    0.004499]  [<c011d713>] ? native_apic_write_dummy+0x33/0x40
[    0.004504]  [<c01450f5>] warn_slowpath_null+0x15/0x20
[    0.004508]  [<c011d713>] native_apic_write_dummy+0x33/0x40
[    0.004515]  [<c010dcac>] perf_counters_lapic_init+0x2c/0x30
[    0.004525]  [<c0799af7>] init_hw_perf_counters+0x159/0x21c
[    0.004529]  [<c079973e>] identify_boot_cpu+0x21/0x23
[    0.004533]  [<c07998c0>] check_bugs+0xb/0xe9
[    0.004537]  [<c07928b6>] start_kernel+0x2dc/0x2ec
[    0.004540]  [<c0792406>] ? unknown_bootoption+0x0/0x19e
[    0.004550]  [<c079207c>] i386_start_kernel+0x7c/0x83
[    0.004564] ---[ end trace a7919e7f17c0a725 ]---
[    0.004576] ... version:                 0
[    0.004578] ... bit width:               48
[    0.004580] ... generic counters:        4
[    0.004582] ... value mask:              0000ffffffffffff
[    0.004585] ... max period:              00007fffffffffff
[    0.004587] ... fixed-purpose counters:  0
[    0.004589] ... counter mask:            000000000000000f
[    0.004596] Checking 'hlt' instruction... OK.
[    0.020721] SMP alternatives: switching to UP code
[    0.027937] Freeing SMP alternatives: 20k freed
[    0.028021] ACPI: Core revision 20090521
[    0.045465] ACPI: setting ELCR to 0200 (from 0e28)
[    0.047492] weird, boot CPU (#0) not listed by the BIOS.
[    0.047495] SMP motherboard not detected.
[    0.047499] Local APIC not detected. Using dummy APIC emulation.
[    0.047502] SMP disabled
[    0.047926] Brought up 1 CPUs
[    0.047930] Total of 1 processors activated (4240.43 BogoMIPS).
[    0.047952] CPU0 attaching NULL sched-domain.
[    0.048312] Booting paravirtualized kernel on bare hardware
[    0.048559] regulator: core version 0.5
[    0.048597] Time: 22:27:41  Date: 03/29/10
[    0.048687] NET: Registered protocol family 16
[    0.048891] EISA bus registered
[    0.048922] ACPI: bus type pci registered
[    0.061243] PCI: PCI BIOS revision 2.10 entry at 0xfd87b, last bus=2
[    0.061246] PCI: Using configuration type 1 for base access
[    0.062371] bio: create slab <bio-0> at 0
[    0.063154] ACPI: EC: Look up EC in DSDT
[    0.072014] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.076220] ACPI: Interpreter enabled
[    0.076230] ACPI: (supports S0 S3 S4 S5)
[    0.076252] ACPI: Using PIC for interrupt routing
[    0.084421] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.084425] ACPI: EC: driver started in interrupt mode
[    0.084591] ACPI: No dock devices found.
[    0.084867] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.084924] pci 0000:00:00.0: reg 10 32bit mmio: [0xd4000000-0xd7ffffff]
[    0.084930] pci 0000:00:00.0: reg 14 32bit mmio: [0xd0400000-0xd0400fff]
[    0.084937] pci 0000:00:00.0: reg 18 io port: [0x8090-0x8093]
[    0.085011] pci 0000:00:02.0: reg 10 32bit mmio: [0xd0000000-0xd0000fff]
[    0.085043] pci 0000:00:02.0: PME# supported from D3cold
[    0.085047] pci 0000:00:02.0: PME# disabled
[    0.085076] pci 0000:00:06.0: reg 10 io port: [0x8400-0x84ff]
[    0.085082] pci 0000:00:06.0: reg 14 32bit mmio: [0xd0001000-0xd0001fff]
[    0.085110] pci 0000:00:06.0: supports D1 D2
[    0.085112] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.085116] pci 0000:00:06.0: PME# disabled
[    0.085201] pci 0000:00:08.0: reg 10 32bit mmio: [0xd0002000-0xd0002fff]
[    0.085207] pci 0000:00:08.0: reg 14 io port: [0x8800-0x88ff]
[    0.085235] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.085238] pci 0000:00:08.0: PME# disabled
[    0.085267] pci 0000:00:0a.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.085282] pci 0000:00:0a.0: supports D1 D2
[    0.085284] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.085288] pci 0000:00:0a.0: PME# disabled
[    0.085329] pci 0000:00:10.0: reg 20 io port: [0x8080-0x808f]
[    0.085393] pci 0000:00:11.0: quirk: region 8000-803f claimed by ali7101 ACPI
[    0.085397] pci 0000:00:11.0: quirk: region 8040-805f claimed by ali7101 SMB
[    0.085425] pci 0000:00:12.0: reg 10 io port: [0x8c00-0x8cff]
[    0.085431] pci 0000:00:12.0: reg 14 32bit mmio: [0xd0003000-0xd0003fff]
[    0.085449] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.085463] pci 0000:00:12.0: supports D1 D2
[    0.085465] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.085469] pci 0000:00:12.0: PME# disabled
[    0.085519] pci 0000:01:05.0: reg 10 32bit mmio: [0xe0000000-0xefffffff]
[    0.085525] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.085531] pci 0000:01:05.0: reg 18 32bit mmio: [0xd0100000-0xd010ffff]
[    0.085545] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.085561] pci 0000:01:05.0: supports D1 D2
[    0.085590] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.085594] pci 0000:00:01.0: bridge 32bit mmio: [0xd0100000-0xd01fffff]
[    0.085599] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xefffffff]
[    0.085618] pci_bus 0000:00: on NUMA node 0
[    0.085623] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.085692] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.089286] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[    0.089433] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[    0.089577] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 10) *0, disabled.
[    0.089721] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 10) *0, disabled.
[    0.089866] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) *0, disabled.
[    0.090010] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 11) *0, disabled.
[    0.090152] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[    0.090296] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[    0.090438] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9
[    0.090689] SCSI subsystem initialized
[    0.090800] libata version 3.00 loaded.
[    0.090935] usbcore: registered new interface driver usbfs
[    0.090950] usbcore: registered new interface driver hub
[    0.090990] usbcore: registered new device driver usb
[    0.091176] ACPI: WMI: Mapper loaded
[    0.091179] PCI: Using ACPI for IRQ routing
[    0.091349] Bluetooth: Core ver 2.15
[    0.091393] NET: Registered protocol family 31
[    0.091396] Bluetooth: HCI device and connection manager initialized
[    0.091401] Bluetooth: HCI socket layer initialized
[    0.091404] NetLabel: Initializing
[    0.091406] NetLabel:  domain hash size = 128
[    0.091408] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.091436] NetLabel:  unlabeled traffic allowed by default
[    0.094875] pnp: PnP ACPI init
[    0.094916] ACPI: bus type pnp registered
[    0.096089] pnp 00:07: io resource (0x8004-0x8005) overlaps 0000:00:11.0 BAR 13 (0x8000-0x803f), disabling
[    0.099289] pnp: PnP ACPI: found 11 devices
[    0.099292] ACPI: ACPI bus type pnp unregistered
[    0.099299] PnPBIOS: Disabled by ACPI PNP
[    0.099321] system 00:07: ioport range 0x40b-0x40b has been reserved
[    0.099325] system 00:07: ioport range 0x480-0x48f has been reserved
[    0.099328] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.099331] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
[    0.099335] system 00:07: ioport range 0x8000-0x807f could not be reserved
[    0.099338] system 00:07: ioport range 0xff00-0xff01 has been reserved
[    0.099342] system 00:07: ioport range 0xfe00-0xfefe has been reserved
[    0.099347] system 00:07: iomem range 0xd0400000-0xd0400fff has been reserved
[    0.134087] AppArmor: AppArmor Filesystem Enabled
[    0.134125] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.134129] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.134135] pci 0000:00:01.0:   MEM window: 0xd0100000-0xd01fffff
[    0.134140] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xefffffff
[    0.134145] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[    0.134148] pci 0000:00:0a.0:   IO window: 0x001000-0x0010ff
[    0.134153] pci 0000:00:0a.0:   IO window: 0x001400-0x0014ff
[    0.134158] pci 0000:00:0a.0:   PREFETCH window: 0x1c000000-0x1fffffff
[    0.134162] pci 0000:00:0a.0:   MEM window: 0x20000000-0x23ffffff
[    0.134182] pci 0000:00:0a.0: enabling device (0000 -> 0003)
[    0.134406] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    0.134410] PCI: setting IRQ 11 as level-triggered
[    0.134416] pci 0000:00:0a.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[    0.134422] pci 0000:00:0a.0: setting latency timer to 64
[    0.134431] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.134435] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.134438] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.134441] pci_bus 0000:01: resource 1 mem: [0xd0100000-0xd01fffff]
[    0.134444] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.134448] pci_bus 0000:02: resource 0 io:  [0x1000-0x10ff]
[    0.134451] pci_bus 0000:02: resource 1 io:  [0x1400-0x14ff]
[    0.134454] pci_bus 0000:02: resource 2 pref mem [0x1c000000-0x1fffffff]
[    0.134457] pci_bus 0000:02: resource 3 mem: [0x20000000-0x23ffffff]
[    0.134515] NET: Registered protocol family 2
[    0.134644] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.135022] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.135385] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.135724] TCP: Hash tables configured (established 16384 bind 16384)
[    0.135728] TCP reno registered
[    0.135821] NET: Registered protocol family 1
[    0.135922] Trying to unpack rootfs image as initramfs...
[    0.379208] Freeing initrd memory: 7470k freed
[    0.395987] Simple Boot Flag at 0x36 set to 0x1
[    0.396177] cpufreq-nforce2: No nForce2 chipset.
[    0.396211] Scanning for low memory corruption every 60 seconds
[    0.396422] audit: initializing netlink socket (disabled)
[    0.396458] type=2000 audit(1269901661.396:1): initialized
[    0.405321] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.407050] VFS: Disk quotas dquot_6.5.2
[    0.407126] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.407795] fuse init (API version 7.12)
[    0.407888] msgmni has been set to 865
[    0.408212] alg: No test for stdrng (krng)
[    0.408230] io scheduler noop registered
[    0.408233] io scheduler anticipatory registered
[    0.408236] io scheduler deadline registered
[    0.408282] io scheduler cfq registered (default)
[    0.408298] pci 0000:00:00.0: ATI Northbridge, reserving I/O ports 0x3b0 to 0x3bb
[    0.624042] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    0.624066] pci 0000:01:05.0: Boot video device
[    0.624176] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.624205] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.624644] ACPI: AC Adapter [ACAD] (on-line)
[    0.624732] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.624740] ACPI: Power Button [PWRF]
[    0.624807] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.624811] ACPI: Power Button [PWRB]
[    0.624860] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.626399] ACPI: Lid Switch [LID]
[    0.626551] Marking TSC unstable due to TSC halts in idle
[    0.626573] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.626605] processor LNXCPU:00: registered as cooling_device0
[    0.628068] Switched to high resolution mode on CPU 0
[    0.633417] thermal LNXTHERM:01: registered as thermal_zone0
[    0.633426] ACPI: Thermal Zone [THRM] (38 C)
[    0.633480] isapnp: Scanning for PnP cards...
[    0.682760] ACPI: Battery Slot [BAT1] (battery absent)
[    0.900663] isapnp: No Plug & Play device found
[    0.901989] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.902160] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.902533] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.902824] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[    0.902828] PCI: setting IRQ 3 as level-triggered
[    0.902834] serial 0000:00:08.0: PCI INT A -> Link[LNKG] -> GSI 3 (level, low) -> IRQ 3
[    0.902842] serial 0000:00:08.0: PCI INT A disabled
[    0.904043] brd: module loaded
[    0.904611] loop: module loaded
[    0.904716] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.905017] pata_ali 0000:00:10.0: can't derive routing for PCI INT A
[    0.905269] scsi0 : pata_ali
[    0.905439] scsi1 : pata_ali
[    0.905681] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8080 irq 14
[    0.905685] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8088 irq 15
[    0.906434] Fixed MDIO Bus: probed
[    0.906488] PPP generic driver version 2.4.2
[    0.906591] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.906611] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.906863] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[    0.906867] PCI: setting IRQ 10 as level-triggered
[    0.906873] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LNKU] -> GSI 10 (level, low) -> IRQ 10
[    0.906905] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.906953] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    0.906983] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0000000
[    0.962172] usb usb1: configuration #1 chosen from 1 choice
[    0.962212] hub 1-0:1.0: USB hub found
[    0.962235] hub 1-0:1.0: 4 ports detected
[    0.962292] uhci_hcd: USB Universal Host Controller Interface driver
[    0.962394] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.967247] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.967256] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.967331] mice: PS/2 mouse device common for all mice
[    0.967519] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.967548] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    0.967628] device-mapper: uevent: version 1.0.3
[    0.967733] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.967879] device-mapper: multipath: version 1.1.0 loaded
[    0.967884] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.968052] EISA: Probing bus 0 at eisa.0
[    0.968063] Cannot allocate resource for EISA slot 1
[    0.968090] Cannot allocate resource for EISA slot 8
[    0.968093] EISA: Detected 0 cards.
[    0.968216] cpuidle: using governor ladder
[    0.968267] cpuidle: using governor menu
[    0.968849] TCP cubic registered
[    0.969018] NET: Registered protocol family 10
[    0.969557] lo: Disabled Privacy Extensions
[    0.969918] NET: Registered protocol family 17
[    0.969942] Bluetooth: L2CAP ver 2.13
[    0.969944] Bluetooth: L2CAP socket layer initialized
[    0.969948] Bluetooth: SCO (Voice Link) ver 0.6
[    0.969950] Bluetooth: SCO socket layer initialized
[    0.969997] Bluetooth: RFCOMM TTY layer initialized
[    0.970001] Bluetooth: RFCOMM socket layer initialized
[    0.970003] Bluetooth: RFCOMM ver 1.11
[    0.970040] powernow-k8: Processor cpuid 6a0 not supported
[    0.970130] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[    0.976433] powernow: No PST tables match this cpuid (0x7a0)
[    0.976436] powernow: This is indicative of a broken BIOS.
[    0.976438] powernow: Trying ACPI perflib
[    0.976496] powernow: Minimum speed 530 MHz. Maximum speed 2120 MHz.
[    0.976551] Using IPI No-Shortcut mode
[    0.976635] PM: Resume from disk failed.
[    0.976659] registered taskstats version 1
[    0.976798]   Magic number: 2:422:503
[    0.977007] rtc_cmos 00:02: setting system clock to 2010-03-29 22:27:44 UTC (1269901664)
[    0.977011] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.977013] EDD information not available.
[    1.002519] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.068534] ata1.00: failed to set max address (err_mask=0x1)
[    1.068538] ata1.00: device aborted resize (194980905 -> 195371568), skipping HPA handling
[    1.068548] ata1.00: ATA-6: TOSHIBA MK1032GAX, AB211A, max UDMA/100
[    1.068551] ata1.00: 194980905 sectors, multi 16: LBA48 
[    1.076188] ata1.00: configured for UDMA/100
[    1.076420] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1032GA AB21 PQ: 0 ANSI: 5
[    1.076575] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.076637] sd 0:0:0:0: [sda] 194980905 512-byte logical blocks: (99.8 GB/92.9 GiB)
[    1.076701] sd 0:0:0:0: [sda] Write Protect is off
[    1.076705] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.076737] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.076918]  sda: sda1 sda2 < sda5 >
[    1.137290] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.240257] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 0C29, max MWDMA2
[    1.240281] ata2.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    1.240284] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    1.256188] ata2.00: configured for MWDMA2
[    1.262491] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 0C29 PQ: 0 ANSI: 5
[    1.275471] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.275476] Uniform CD-ROM driver Revision: 3.20
[    1.275550] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.275605] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.275643] Freeing unused kernel memory: 540k freed
[    1.276764] Write protecting the kernel text: 4580k
[    1.276799] Write protecting the kernel read-only data: 1840k
[    1.487689] Linux agpgart interface v0.103
[    1.490369] agpgart-ati 0000:00:00.0: Ati IGP320/M chipset
[    1.499552] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input5
[    1.499632] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.525018] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[    1.525021]   originally by Donald Becker <becker@scyld.com>
[    1.525022]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[    1.628757] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xd4000000
[    1.629214] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    1.629222] natsemi 0000:00:12.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.631604] natsemi eth0: NatSemi DP8381[56] at 0xd0003000 (0000:00:12.0), 00:0f:20:1f:08:0d, IRQ 11, port TP.
[    1.729156] [drm] Initialized drm 1.1.0 20060810
[    1.763351] [drm] radeon default to kernel modesetting DISABLED.
[    1.763442] pci 0000:01:05.0: power state changed by ACPI to D0
[    1.763810] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    1.763817] pci 0000:01:05.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    1.764578] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[    1.787398] FDC 0 is a post-1991 82077
[    3.363553] PM: Starting manual resume from disk
[    3.363561] PM: Resume from partition 8:5
[    3.363563] PM: Checking hibernation image.
[    3.363850] PM: Resume from disk failed.
[    3.404210] EXT4-fs (sda1): barriers enabled
[    3.428720] kjournald2 starting: pid 330, dev sda1:8, commit interval 5 seconds
[    3.428781] EXT4-fs (sda1): delayed allocation enabled
[    3.428786] EXT4-fs: file extents enabled
[    3.442660] EXT4-fs: mballoc enabled
[    3.442686] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.937048] ACPI: EC: GPE storm detected, transactions will use polling mode
[    4.334882] type=1505 audit(1269901667.856:2): operation="profile_load" pid=354 name=/usr/share/gdm/guest-session/Xsession
[    4.339332] type=1505 audit(1269901667.859:3): operation="profile_load" pid=355 name=/sbin/dhclient3
[    4.339671] type=1505 audit(1269901667.859:4): operation="profile_load" pid=355 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.339872] type=1505 audit(1269901667.859:5): operation="profile_load" pid=355 name=/usr/lib/connman/scripts/dhclient-script
[    4.425901] type=1505 audit(1269901667.947:6): operation="profile_load" pid=356 name=/usr/bin/evince
[    4.433070] type=1505 audit(1269901667.955:7): operation="profile_load" pid=356 name=/usr/bin/evince-previewer
[    4.437376] type=1505 audit(1269901667.959:8): operation="profile_load" pid=356 name=/usr/bin/evince-thumbnailer
[    4.457087] type=1505 audit(1269901667.979:9): operation="profile_load" pid=358 name=/usr/lib/cups/backend/cups-pdf
[   15.643598] udev: starting version 147
[   15.656920] Adding 1301224k swap on /dev/sda5.  Priority:-1 extents:1 across:1301224k 
[   15.856424] lp: driver loaded but no devices found
[   15.917123] EXT4-fs (sda1): internal journal on sda1:8
[   16.038397] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.078532] yenta_cardbus 0000:00:0a.0: CardBus bridge found [103c:0024]
[   16.078555] yenta_cardbus 0000:00:0a.0: Using CSCINT to route CSC interrupts to PCI
[   16.078558] yenta_cardbus 0000:00:0a.0: Routing CardBus interrupts to PCI
[   16.078564] yenta_cardbus 0000:00:0a.0: TI: mfunc 0x01111112, devctl 0x64
[   16.125496] parport_pc 00:09: reported by Plug and Play ACPI
[   16.125572] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.219248] lp0: using parport0 (interrupt-driven).
[   16.327419] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0038, PCI irq 11
[   16.327426] yenta_cardbus 0000:00:0a.0: Socket status: 30000068
[   16.393514] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.397563] ppdev: user-space parallel port driver
[   16.494030] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[   16.494038] PCI: setting IRQ 5 as level-triggered
[   16.494044] ALI 5451 0000:00:06.0: PCI INT A -> Link[LNKH] -> GSI 5 (level, low) -> IRQ 5
[   16.921442] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   16.922229] __ratelimit: 6 callbacks suppressed
[   16.922233] type=1505 audit(1269916080.443:12): operation="profile_replace" pid=707 name=/usr/share/gdm/guest-session/Xsession
[   16.925402] type=1505 audit(1269916080.447:13): operation="profile_replace" pid=764 name=/sbin/dhclient3
[   16.925749] type=1505 audit(1269916080.447:14): operation="profile_replace" pid=764 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   16.925945] type=1505 audit(1269916080.447:15): operation="profile_replace" pid=764 name=/usr/lib/connman/scripts/dhclient-script
[   16.964126] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   16.964182] pci 0000:02:00.0: reg 10 io port: [0x00-0x1f]
[   16.964190] pci 0000:02:00.0: reg 14 32bit mmio: [0x000000-0x00001f]
[   16.964197] pci 0000:02:00.0: reg 18 32bit mmio: [0x000000-0x0007ff]
[   16.964243] pci 0000:02:00.0: supports D2
[   16.980786] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   17.009021] type=1505 audit(1269916080.531:16): operation="profile_replace" pid=776 name=/usr/bin/evince
[   17.028060] type=1505 audit(1269916080.551:17): operation="profile_replace" pid=776 name=/usr/bin/evince-previewer
[   17.032422] type=1505 audit(1269916080.555:18): operation="profile_replace" pid=776 name=/usr/bin/evince-thumbnailer
[   17.041929] eth0: DSPCFG accepted after 0 usec.
[   17.041941] eth0: link up.
[   17.041956] eth0: Setting full-duplex based on negotiated link capability.
[   17.055602] type=1505 audit(1269916080.575:19): operation="profile_replace" pid=785 name=/usr/lib/cups/backend/cups-pdf
[   17.056151] type=1505 audit(1269916080.579:20): operation="profile_replace" pid=785 name=/usr/sbin/cupsd
[   17.083168] type=1505 audit(1269916080.603:21): operation="profile_replace" pid=788 name=/usr/sbin/tcpdump
[   17.099200] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[   17.101449] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   17.102309] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   17.103124] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   17.104187] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   19.592040] AC'97 1 does not respond - RESET
[   19.608037] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   19.608094] ali mixer 1 creating error.
[   20.209418] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   20.209449] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   20.209485] pci 0000:01:05.0: putting AGP V2 device into 4x mode
[   20.341776] [drm] Setting GART location based on new memory map
[   20.341793] [drm] Loading R100 Microcode
[   20.341842] [drm] writeback test succeeded in 1 usecs
[   27.984051] eth0: no IPv6 routers present
[   49.570078] glxinfo:1537 freeing invalid memtype d4102000-d4112000
[   49.570091] glxinfo:1537 freeing invalid memtype d4112000-d4122000
[   49.570098] glxinfo:1537 freeing invalid memtype d4122000-d4132000
[   49.570105] glxinfo:1537 freeing invalid memtype d4132000-d4142000
[   49.570112] glxinfo:1537 freeing invalid memtype d4142000-d4152000
[   49.570119] glxinfo:1537 freeing invalid memtype d4152000-d4162000
[   49.570126] glxinfo:1537 freeing invalid memtype d4162000-d4172000
[   49.570133] glxinfo:1537 freeing invalid memtype d4172000-d4182000
[   49.570140] glxinfo:1537 freeing invalid memtype d4182000-d4192000
[   49.570147] glxinfo:1537 freeing invalid memtype d4192000-d41a2000
[   49.570154] glxinfo:1537 freeing invalid memtype d41a2000-d41b2000
[   49.570161] glxinfo:1537 freeing invalid memtype d41b2000-d41c2000
[   49.570168] glxinfo:1537 freeing invalid memtype d41c2000-d41d2000
[   49.570175] glxinfo:1537 freeing invalid memtype d41d2000-d41e2000
[   49.570182] glxinfo:1537 freeing invalid memtype d41e2000-d41f2000
[   49.570189] glxinfo:1537 freeing invalid memtype d41f2000-d4202000
[   49.570195] glxinfo:1537 freeing invalid memtype d4202000-d4212000
[   49.570202] glxinfo:1537 freeing invalid memtype d4212000-d4222000
[   49.570209] glxinfo:1537 freeing invalid memtype d4222000-d4232000
[   49.570216] glxinfo:1537 freeing invalid memtype d4232000-d4242000
[   49.570223] glxinfo:1537 freeing invalid memtype d4242000-d4252000
[   49.570230] glxinfo:1537 freeing invalid memtype d4252000-d4262000
[   49.570237] glxinfo:1537 freeing invalid memtype d4262000-d4272000
[   49.570244] glxinfo:1537 freeing invalid memtype d4272000-d4282000
[   49.570251] glxinfo:1537 freeing invalid memtype d4282000-d4292000
[   49.570257] glxinfo:1537 freeing invalid memtype d4292000-d42a2000
[   49.570264] glxinfo:1537 freeing invalid memtype d42a2000-d42b2000
[   49.570271] glxinfo:1537 freeing invalid memtype d42b2000-d42c2000
[   49.570278] glxinfo:1537 freeing invalid memtype d42c2000-d42d2000
[   49.570285] glxinfo:1537 freeing invalid memtype d42d2000-d42e2000
[   49.570292] glxinfo:1537 freeing invalid memtype d42e2000-d42f2000
[   49.570298] glxinfo:1537 freeing invalid memtype d42f2000-d4302000
[   79.632076] Clocksource tsc unstable (delta = -375057982 ns)
```

```
thomas@thomas-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:20:1f:08:0d  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fe1f:80d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1415 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2419188 (2.4 MB)  TX bytes:209940 (209.9 KB)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```
```
thomas@thomas-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
02:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
```

```
thomas@thomas-laptop:~$ lspcmcia
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:0a.0)
  CardBus card -- see "lspci" for more information


```

---

### Post by Joe Ker1086 on 2010-03-30
bump

---

### Post by Joe Ker1086 on 2010-03-30
Can anyone help at all with this one?????

---

### Post by Joe Ker1086 on 2010-07-19
This was resolved with ndiswrapper.....

---

