---
title: "Kworld tv tunner  - ubuntu"
date: 2008-07-20
forum: Multimedia Software
---

### Post by UbuGr on 2008-07-20
Hello, 
before a few days I get a kworld usb tv tunner like this 
[http://www.kworld.com.tw/product_overview.aspx?P_ID=294](http://www.kworld.com.tw/product_overview.aspx?P_ID=294) but the 355u model.
My question is, can I use it to watch tv programs on Ubuntu 8.04??

thank u!

---

### Post by xc3RnbFO8P on 2008-07-20
Show the output of **dmesg** in Terminal.

---

### Post by UbuGr on 2008-07-20
> **Ringi said:**
> Show the output of **dmesg** in Terminal.

here is the output from dmesg

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f670000 (usable)
[    0.000000]  BIOS-e820: 000000003f670000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f65c0
[    0.000000] Entering add_active_range(0, 0, 259696) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259696
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259696
[    0.000000] On node 0 totalpages: 259696
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 236 pages used for memmap
[    0.000000]   HighMem zone: 30084 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6510 checksum 0
[    0.000000] ACPI: RSDP 000F6510, 0014 (r0 TOSINV)
[    0.000000] ACPI: RSDT 3F67E201, 0048 (r1 TOSINV Capell00  6040000  LTP        0)
[    0.000000] ACPI: FACP 3F685DEE, 0074 (r1 TOSINV CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: DSDT 3F67F8B6, 6538 (r1 TOSINV CALISTGA  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 3F686FC0, 0040
[    0.000000] ACPI: APIC 3F685E62, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 3F685ECA, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 3F685F02, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: BOOT 3F685FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: APIC 3F685F70, 0068 (r1 TOSINV   APIC    6040000  LTP        0)
[    0.000000] ACPI: SSDT 3F67F263, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F67EBD1, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F67E249, 04F6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257668

[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1828.812 MHz processor.
[   22.952641] Console: colour VGA+ 80x25
[   22.952647] console [tty0] enabled
[   22.952970] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.953394] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.989777] Memory: 1017644k/1038784k available (2177k kernel code, 20428k reserved, 1006k data, 368k init, 121280k highmem)
[   22.989789] virtual kernel memory layout:
[   22.989790]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   22.989792]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.989794]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.989796]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.989797]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   22.989799]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   22.989801]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   22.989806] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.989853] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   22.989993] hpet clockevent registered
[   23.069867] Calibrating delay using timer specific routine.. 3662.78 BogoMIPS (lpj=7325576)
[   23.069895] Security Framework initialized
[   23.069901] SELinux:  Disabled at boot.
[   23.069917] AppArmor: AppArmor initialized
[   23.069923] Failure registering capabilities with primary security module.
[   23.069936] Mount-cache hash table entries: 512
[   23.070096] Initializing cgroup subsys ns
[   23.070102] Initializing cgroup subsys cpuacct
[   23.070116] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   23.070128] monitor/mwait feature present.
[   23.070131] using mwait in idle threads.
[   23.070137] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.070141] CPU: L2 cache: 2048K
[   23.070144] CPU: Physical Processor ID: 0
[   23.070147] CPU: Processor Core ID: 0
[   23.070150] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   23.070163] Compat vDSO mapped to ffffe000.
[   23.070182] Checking 'hlt' instruction... OK.
[   23.086473] SMP alternatives: switching to UP code
[   23.089152] Early unpacking initramfs... done
[   23.658193] ACPI: Core revision 20070126
[   23.658264] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.716528] CPU0: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 06
[   23.716552] SMP alternatives: switching to SMP code
[   23.717707] Booting processor 1/1 eip 3000
[   23.728067] Initializing CPU#1
[   23.804611] Calibrating delay using timer specific routine.. 3657.60 BogoMIPS (lpj=7315215)
[   23.804622] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   23.804630] monitor/mwait feature present.
[   23.804635] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.804638] CPU: L2 cache: 2048K
[   23.804641] CPU: Physical Processor ID: 0
[   23.804643] CPU: Processor Core ID: 1
[   23.804645] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   23.805509] CPU1: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 06
[   23.805542] Total of 2 processors activated (7320.39 BogoMIPS).
[   23.805751] ENABLING IO-APIC IRQs
[   23.805963] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.952524] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   23.972516] Brought up 2 CPUs
[   23.972550] CPU0 attaching sched-domain:
[   23.972554]  domain 0: span 03
[   23.972557]   groups: 01 02
[   23.972562] CPU1 attaching sched-domain:
[   23.972565]  domain 0: span 03
[   23.972568]   groups: 02 01
[   23.972943] net_namespace: 64 bytes
[   23.972955] Booting paravirtualized kernel on bare hardware
[   23.973699] Time:  9:27:39  Date: 07/20/08
[   23.973742] NET: Registered protocol family 16
[   23.974083] EISA bus registered
[   23.974091] ACPI: bus type pci registered
[   23.974365] PCI: PCI BIOS revision 2.10 entry at 0xfd875, last bus=7
[   23.974369] PCI: Using configuration type 1
[   23.974386] Setting up standard PCI resources
[   23.980925] ACPI: EC: Look up EC in DSDT
[   24.009762] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   24.010653] ACPI: Interpreter enabled
[   24.010658] ACPI: (supports S0 S3 S4 S5)
[   24.010682] ACPI: Using IOAPIC for interrupt routing
[   24.113135] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[   24.113139] ACPI: EC: driver started in poll mode
[   24.113217] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.114319] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   24.114325] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   24.115795] PCI: Transparent bridge - 0000:00:1e.0
[   24.115927] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.116439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   24.116657] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   24.116871] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   24.117104] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   24.240577] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   24.240752] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   24.240920] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   24.241087] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   24.241254] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   24.241420] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   24.241588] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   24.241754] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   24.242012] ACPI: Power Resource [FN00] (off)
[   24.242099] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.242155] pnp: PnP ACPI init
[   24.242167] ACPI: bus type pnp registered
[   24.312217] pnp: PnP ACPI: found 10 devices
[   24.312221] ACPI: ACPI bus type pnp unregistered
[   24.312228] PnPBIOS: Disabled by ACPI PNP
[   24.312626] PCI: Using ACPI for IRQ routing
[   24.312630] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.371656] NET: Registered protocol family 8
[   24.371660] NET: Registered protocol family 20
[   24.371720] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   24.371727] hpet0: 3 64-bit timers, 14318180 Hz
[   24.372779] AppArmor: AppArmor Filesystem Enabled
[   24.375640] Time: tsc clocksource has been installed.
[   24.375659] Switched to high resolution mode on CPU 0
[   24.375815] Switched to high resolution mode on CPU 1
[   24.387614] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   24.387620] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   24.387625] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   24.387630] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   24.387635] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   24.387640] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   24.387645] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   24.387658] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   24.387669] system 00:06: ioport range 0x400-0x401 has been reserved
[   24.387673] system 00:06: ioport range 0x680-0x69f has been reserved
[   24.387678] system 00:06: ioport range 0x800-0x80f has been reserved
[   24.387682] system 00:06: ioport range 0x1000-0x107f has been reserved
[   24.387687] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   24.387691] system 00:06: ioport range 0x1640-0x164f has been reserved
[   24.418383] PCI: Bridge: 0000:00:1c.0
[   24.418386]   IO window: disabled.
[   24.418394]   MEM window: disabled.
[   24.418400]   PREFETCH window: disabled.
[   24.418408] PCI: Bridge: 0000:00:1c.1
[   24.418413]   IO window: 2000-2fff
[   24.418421]   MEM window: d8000000-d9ffffff
[   24.418427]   PREFETCH window: d2000000-d3ffffff
[   24.418435] PCI: Bridge: 0000:00:1c.2
[   24.418440]   IO window: 3000-3fff
[   24.418448]   MEM window: da000000-dbffffff
[   24.418454]   PREFETCH window: d4000000-d5ffffff
[   24.418473] PCI: Bus 8, cardbus bridge: 0000:07:06.0
[   24.418476]   IO window: 00004400-000044ff
[   24.418483]   IO window: 00004800-000048ff
[   24.418490]   PREFETCH window: 50000000-53ffffff
[   24.418496]   MEM window: 54000000-57ffffff
[   24.418502] PCI: Bridge: 0000:00:1e.0
[   24.418507]   IO window: 4000-4fff
[   24.418515]   MEM window: dc000000-dc0fffff
[   24.418520]   PREFETCH window: disabled.
[   24.418563] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   24.418573] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.418606] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   24.418614] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   24.418647] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   24.418655] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   24.418674] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.418696] PCI: Enabling device 0000:07:06.0 (0000 -> 0003)
[   24.418702] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   24.418725] NET: Registered protocol family 2
[   24.455527] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.455880] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.456576] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.456896] TCP: Hash tables configured (established 131072 bind 65536)
[   24.456900] TCP reno registered
[   24.467611] checking if image is initramfs... it is
[   25.587104] Freeing initrd memory: 7323k freed
[   25.587323] Simple Boot Flag at 0x36 set to 0x1
[   25.588427] audit: initializing netlink socket (disabled)
[   25.588445] audit(1216546059.428:1): initialized
[   25.588729] highmem bounce pool size: 64 pages
[   25.592220] VFS: Disk quotas dquot_6.5.1
[   25.592347] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.592565] io scheduler noop registered
[   25.592568] io scheduler anticipatory registered
[   25.592571] io scheduler deadline registered
[   25.592589] io scheduler cfq registered (default)
[   25.592606] Boot video device is 0000:00:02.0
[   25.592728] PCI: Firmware left 0000:07:08.0 e100 interrupts enabled, disabling
[   25.592908] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   25.592984] assign_interrupt_mode Found MSI capability
[   25.593049] Allocate Port Service[0000:00:1c.0:pcie00]
[   25.593110] Allocate Port Service[0000:00:1c.0:pcie02]
[   25.593257] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   25.593333] assign_interrupt_mode Found MSI capability
[   25.593394] Allocate Port Service[0000:00:1c.1:pcie00]
[   25.593450] Allocate Port Service[0000:00:1c.1:pcie02]
[   25.593612] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   25.593687] assign_interrupt_mode Found MSI capability
[   25.593747] Allocate Port Service[0000:00:1c.2:pcie00]
[   25.593805] Allocate Port Service[0000:00:1c.2:pcie02]
[   25.594233] isapnp: Scanning for PnP cards...
[   25.948199] isapnp: No Plug & Play device found
[   25.992048] Real Time Clock Driver v1.12ac
[   25.992404] hpet_resources: 0xfed00000 is busy
[   25.992455] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.994934] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.995044] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.995215] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   25.997802] i8042.c: Detected active multiplexing controller, rev 1.1.
[   25.999296] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.999303] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   25.999308] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   25.999312] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   25.999315] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   26.020905] mice: PS/2 mouse device common for all mice
[   26.021098] EISA: Probing bus 0 at eisa.0
[   26.021106] Cannot allocate resource for EISA slot 1
[   26.021111] Cannot allocate resource for EISA slot 2
[   26.021114] Cannot allocate resource for EISA slot 3
[   26.021117] Cannot allocate resource for EISA slot 4
[   26.021141] EISA: Detected 0 cards.
[   26.021145] cpuidle: using governor ladder
[   26.021148] cpuidle: using governor menu
[   26.021272] NET: Registered protocol family 1
[   26.021314] Using IPI No-Shortcut mode
[   26.021356] registered taskstats version 1
[   26.021520]   Magic number: 0:388:475
[   26.021610] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.021613] EDD information not available.
[   26.021849] Freeing unused kernel memory: 368k freed
[   26.054378] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   27.385093] fuse init (API version 7.9)
[   27.407131] ACPI: Transitioning device [FAN0] to D3
[   27.407136] ACPI: Transitioning device [FAN0] to D3
[   27.407141] ACPI: Fan [FAN0] (off)
[   27.416076] ACPI: SSDT 3F67E9A0, 01A8 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   27.416447] ACPI: SSDT 3F67E73F, 01DC (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   27.417204] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   27.417212] ACPI: Processor [CPU0] (supports 8 throttling states)
[   27.417610] ACPI: SSDT 3F67EB48, 0089 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   27.417955] ACPI: SSDT 3F67E91B, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   27.418871] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   27.418880] ACPI: Processor [CPU1] (supports 8 throttling states)
[   27.420953] ACPI: Thermal Zone [TZ00] (33 C)
[   27.424401] ACPI: Invalid passive threshold
[   27.429293] ACPI: Transitioning device [FAN0] to D0
[   27.429296] ACPI: Transitioning device [FAN0] to D0
[   27.429299] ACPI: Unable to turn cooling device [f7c46468] 'on'
[   27.429305] ACPI: Thermal Zone [TZ01] (30 C)
[   28.057746] usbcore: registered new interface driver usbfs
[   28.057791] usbcore: registered new interface driver hub
[   28.057836] usbcore: registered new device driver usb
[   28.064521] USB Universal Host Controller Interface driver v3.0
[   28.064597] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   28.064613] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   28.064620] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   28.064918] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   28.064957] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   28.065158] usb usb1: configuration #1 chosen from 1 choice
[   28.065198] hub 1-0:1.0: USB hub found
[   28.065206] hub 1-0:1.0: 2 ports detected
[   28.116295] SCSI subsystem initialized
[   28.165262] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   28.165281] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   28.165288] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   28.165326] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   28.165366] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   28.165549] usb usb2: configuration #1 chosen from 1 choice
[   28.165588] hub 2-0:1.0: USB hub found
[   28.165597] hub 2-0:1.0: 2 ports detected
[   28.203849] libata version 3.00 loaded.
[   28.203907] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   28.203910] e100: Copyright(c) 1999-2006 Intel Corporation
[   28.269078] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   28.269096] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   28.269103] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   28.269143] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   28.269182] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   28.269363] usb usb3: configuration #1 chosen from 1 choice
[   28.269404] hub 3-0:1.0: USB hub found
[   28.269411] hub 3-0:1.0: 2 ports detected
[   28.372903] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   28.372920] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   28.372927] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   28.372964] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   28.373003] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   28.373187] usb usb4: configuration #1 chosen from 1 choice
[   28.373227] hub 4-0:1.0: USB hub found
[   28.373235] hub 4-0:1.0: 2 ports detected
[   28.404768] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   28.476933] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   28.476953] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   28.476959] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   28.476997] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   28.480926] ehci_hcd 0000:00:1d.7: debug port 1
[   28.480936] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   28.480946] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xdc444000
[   28.524682] usb 1-1: device descriptor read/64, error -71
[   28.536496] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.536692] usb usb5: configuration #1 chosen from 1 choice
[   28.536734] hub 5-0:1.0: USB hub found
[   28.536743] hub 5-0:1.0: 8 ports detected
[   28.640628] ACPI: PCI Interrupt 0000:07:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   28.669906] e100: eth0: e100_probe: addr 0xdc005000, irq 21, MAC addr 00:a0:d1:60:76:8c
[   28.675068] ACPI: PCI Interrupt 0000:07:06.1[B] -> GSI 17 (level, low) -> IRQ 16
[   28.724844] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[dc006000-dc0067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   28.726493] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   28.726542] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.726562] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   28.732664] ata_piix 0000:00:1f.2: version 2.12
[   28.732673] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   28.887923] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   28.887975] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.888080] scsi0 : ata_piix
[   28.888164] scsi1 : ata_piix
[   28.889596] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[   28.889601] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[   29.052168] ata1.00: ATA-6: TOSHIBA MK8032GSX, AS112M, max UDMA/100
[   29.052176] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   29.060155] ata1.00: configured for UDMA/100
[   29.151440] Clocksource tsc unstable (delta = -3226930166 ns)
[   29.155512] Time: hpet clocksource has been installed.
[   29.163092] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   29.172307] usb 1-1: device descriptor read/64, error -71
[   29.173221] ata2.00: ATAPI: MATSHITADVD-RAM UJ-841S, 1.60, max UDMA/33
[   29.188347] ata2.00: configured for UDMA/33
[   29.188617] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8032GS AS11 PQ: 0 ANSI: 5
[   29.190345] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.60 PQ: 0 ANSI: 5
[   29.202256] Driver 'sd' needs updating - please use bus_type methods
[   29.202374] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   29.202394] sd 0:0:0:0: [sda] Write Protect is off
[   29.202398] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.202426] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.202499] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   29.202516] sd 0:0:0:0: [sda] Write Protect is off
[   29.202519] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.202547] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.202552]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   29.233906]  sda1 sda2 sda3 sda4
[   29.236187] usb 1-1: device descriptor read/64, error -71
[   29.261271] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.269308] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.269342] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   29.269898] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   29.269904] Uniform CD-ROM driver Revision: 3.20
[   29.269978] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.451813] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   29.574612] usb 1-1: device descriptor read/64, error -71
[   29.646781] Attempting manual resume
[   29.646787] swsusp: Resume From Partition 8:4
[   29.646789] PM: Checking swsusp image.
[   29.647094] PM: Resume from disk failed.
[   29.692222] kjournald starting.  Commit interval 5 seconds
[   29.692263] EXT3-fs: mounted filesystem with ordered data mode.
[   29.762741] usb 1-1: device descriptor read/64, error -71
[   29.974397] usb 1-1: new low speed USB device using uhci_hcd and address 5
[   30.389657] usb 1-1: device not accepting address 5, error -71
[   30.496317] usb 1-1: new low speed USB device using uhci_hcd and address 6
[   30.907601] usb 1-1: device not accepting address 6, error -71
[   42.043782] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.098355] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.154548] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   42.286166] Linux agpgart interface v0.102
[   42.495162] intel_rng: FWH not detected
[   42.664704] agpgart: Detected an Intel 945GM Chipset.
[   42.666416] agpgart: Detected 7932K stolen memory.
[   42.686162] agpgart: AGP aperture is 256M @ 0xc0000000
[   43.236175] iTCO_vendor_support: vendor-support=0
[   43.252180] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   43.293751] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   43.299229] ACPI: Battery Slot [BAT0] (battery present)
[   43.360052] input: Power Button (FF) as /devices/virtual/input/input3
[   43.413153] ACPI: Power Button (FF) [PWRF]
[   43.413282] input: Lid Switch as /devices/virtual/input/input4
[   43.437210] ACPI: Lid Switch [LID]
[   43.437358] input: Power Button (CM) as /devices/virtual/input/input5
[   43.524215] ACPI: Power Button (CM) [PWRB]
[   43.524632] ACPI: AC Adapter [ADP0] (off-line)
[   43.769510] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   43.769522] synaptics: Toshiba Satellite A100 detected, limiting rate to 40pps.
[   43.802133] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   43.829642] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   43.829698] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   43.895690] Yenta: CardBus bridge found at 0000:07:06.0 [1179:ff10]
[   43.895717] Yenta: Enabling burst memory read transactions
[   43.895725] Yenta: Using CSCINT to route CSC interrupts to PCI
[   43.895728] Yenta: Routing CardBus interrupts to PCI
[   43.895737] Yenta TI: socket 0000:07:06.0, mfunc 0x01a01b22, devctl 0x66
[   44.127709] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   44.127715] Socket status: 30000006
[   44.127719] Yenta: Raising subordinate bus# of parent bus (#07) from #07 to #0b
[   44.127726] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   44.127731] cs: IO port probe 0x4000-0x4fff: clean.
[   44.128176] pcmcia: parent PCI bridge Memory window: 0xdc000000 - 0xdc0fffff
[   44.167927] ACPI: PCI Interrupt 0000:07:06.2[A] -> GSI 18 (level, low) -> IRQ 18
[   44.554200] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   44.554207] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   44.554380] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   44.554399] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   44.554431] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   44.686736] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   44.737805] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   44.738332] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   44.769750] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   44.885617] sdhci: Secure Digital Host Controller Interface driver
[   44.885623] sdhci: Copyright(c) Pierre Ossman
[   45.753725] NET: Registered protocol family 10
[   45.754102] lo: Disabled Privacy Extensions
[   45.754699] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.659343] sdhci: SDHCI controller found at 0000:07:06.3 [104c:803c] (rev 0)
[   46.659373] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 18
[   46.659461] mmc0: SDHCI at 0xdc006800 irq 18 DMA
[   46.659528] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   46.659553] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   46.685568] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[   46.752315] iwl3945: Radio Frequency Kill Switch is On:
[   46.752318] Kill switch must be turned off for wireless networking to work.
[   46.754231] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   46.764283] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   46.784254] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   46.811835] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   46.831804] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   46.973053] cs: IO port probe 0x100-0x3af: clean.
[   46.975172] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   46.976040] cs: IO port probe 0x820-0x8ff: clean.
[   46.976764] cs: IO port probe 0xc00-0xcf7: clean.
[   46.977733] cs: IO port probe 0xa00-0xaff: clean.
[   47.327826] lp: driver loaded but no devices found
[   47.650738] Adding 1020116k swap on /dev/sda4.  Priority:-1 extents:1 across:1020116k
[   47.696304] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   47.696684] EXT3 FS on sda3, internal journal
[   48.151796] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x10a90000
[   48.922932] ip_tables: (C) 2000-2006 Netfilter Core Team
[   50.160721] ACPI: Error installing notify handler
[   50.160818] No dock devices found.
[   51.214812] apm: BIOS not found.
[   51.391116] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   51.391121] vboxdrv: Successfully done.
[   51.391183] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   51.391187] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).
[   53.752072] Bluetooth: Core ver 2.11
[   53.752206] NET: Registered protocol family 31
[   53.752209] Bluetooth: HCI device and connection manager initialized
[   53.752214] Bluetooth: HCI socket layer initialized
[   53.780096] Bluetooth: L2CAP ver 2.9
[   53.780102] Bluetooth: L2CAP socket layer initialized
[   53.891267] Bluetooth: RFCOMM socket layer initialized
[   53.891277] Bluetooth: RFCOMM TTY layer initialized
[   53.891278] Bluetooth: RFCOMM ver 1.8
[   53.900289] usb 1-1: new low speed USB device using uhci_hcd and address 7
[   53.903379] usb 1-1: device descriptor read/64, error -71
[   53.908777] usb 1-1: device descriptor read/64, error -71
[   53.911716] usb 1-1: new low speed USB device using uhci_hcd and address 8
[   53.914722] usb 1-1: device descriptor read/64, error -71
[   53.918735] usb 1-1: device descriptor read/64, error -71
[   53.920757] usb 1-1: new low speed USB device using uhci_hcd and address 9
[   53.926564] usb 1-1: device not accepting address 9, error -71
[   53.928164] usb 1-1: new low speed USB device using uhci_hcd and address 10
[   53.932243] usb 1-1: device not accepting address 10, error -71
[   56.486951] [drm] Initialized drm 1.1.0 20060810
[   56.489717] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   56.489724] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   56.489789] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  116.919840] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  116.925828] usb 2-1: configuration #1 chosen from 1 choice
[  117.348781] usbcore: registered new interface driver hiddev
[  117.353963] input: Acrox USB & PS/2 Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input9
[  117.358820] input,hidraw0: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:1d.1-1
[  117.358851] usbcore: registered new interface driver usbhid
[  117.358858] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  133.128756] CPU0 attaching NULL sched-domain.
[  133.128762] CPU1 attaching NULL sched-domain.
[  133.143495] CPU0 attaching sched-domain:
[  133.143501]  domain 0: span 03
[  133.143504]   groups: 01 02
[  133.143510]   domain 1: span 03
[  133.143513]    groups: 03
[  133.143517] CPU1 attaching sched-domain:
[  133.143519]  domain 0: span 03
[  133.143522]   groups: 02 01
[  133.143526]   domain 1: span 03
[  133.143529]    groups: 03
[  151.923934] ACPI: Transitioning device [FAN0] to D0
[  151.923938] ACPI: Transitioning device [FAN0] to D0
[  151.923940] ACPI: Unable to turn cooling device [f7c46468] 'on'
[  168.084124] CPU0 attaching NULL sched-domain.
[  168.084130] CPU1 attaching NULL sched-domain.
[  168.106128] CPU0 attaching sched-domain:
[  168.106133]  domain 0: span 03
[  168.106137]   groups: 01 02
[  168.106142] CPU1 attaching sched-domain:
[  168.106145]  domain 0: span 03
[  168.106148]   groups: 02 01
[  174.071777] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  174.073758] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  184.138080] eth0: no IPv6 routers present
[ 5429.796107] usb 5-6: new high speed USB device using ehci_hcd and address 4
[ 5429.927883] usb 5-6: configuration #1 chosen from 1 choice
[ 5430.030130] usbcore: registered new interface driver libusual
[ 5430.059482] Initializing USB Mass Storage driver...
[ 5430.060492] scsi2 : SCSI emulation for USB Mass Storage devices
[ 5430.060570] usb-storage: device found at 4
[ 5430.060573] usbcore: registered new interface driver usb-storage
[ 5430.060575] usb-storage: waiting for device to settle before scanning
[ 5430.060579] USB Mass Storage support registered.
[ 5435.051117] usb-storage: device scan complete
[ 5436.349291] scsi 2:0:0:0: Direct-Access     ST332082 0AS                   PQ: 0 ANSI: 2 CCS
[ 5436.419864] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 5436.420493] sd 2:0:0:0: [sdb] Write Protect is off
[ 5436.420498] sd 2:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 5436.420502] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 5436.421606] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 5436.422228] sd 2:0:0:0: [sdb] Write Protect is off
[ 5436.422232] sd 2:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 5436.422235] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 5436.422240]  sdb: sdb1 sdb2
[ 5436.444417] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 5436.444475] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 5437.145301] kjournald starting.  Commit interval 5 seconds
[ 5437.145880] EXT3 FS on sdb2, internal journal
[ 5437.145884] EXT3-fs: recovery complete.
[ 5437.146500] EXT3-fs: mounted filesystem with ordered data mode.
[18811.012550] kjournald starting.  Commit interval 5 seconds
[18811.013132] EXT3 FS on sdb2, internal journal
[18811.013139] EXT3-fs: mounted filesystem with ordered data mode.
```

---

### Post by xc3RnbFO8P on 2008-07-20
And now **lsusb** in Terminal.

---

### Post by UbuGr on 2008-07-20
> **Ringi said:**
> And now **lsusb** in Terminal.

here is it

Bus 005 Device 005: ID eb1a:e355 eMPIA Technology, Inc. 
Bus 005 Device 004: ID 059f:0951 LaCie, Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by xc3RnbFO8P on 2008-07-20
We can try to install the driver to V4L.

---

### Post by UbuGr on 2008-07-20
thank you,
the post #3 its ok now, it was very exhausting to schroll down the post,sorry.

---

### Post by xc3RnbFO8P on 2008-07-21
Here we go:
> sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
> cd  /home/your_folder/v4l-dvb
> make all
> sudo make install
Restart the computer and **dmesg** in Terminal.
Only copy/paste dvb/TV part.

---

