---
title: "pvr-150 ir blaster"
date: 2008-09-16
forum: Mythbuntu
---

### Post by roob85 on 2008-09-16
im running 8.04 and ive been using mythtv with the cable directly plugged into my pvr-150..but i just got a cable box from comcast(scientific atlanta) and now i need to get my ir blaster working. i seem to be suffering from this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/222359](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/222359)  but there is no solution or fix posted yet. If there is any other information that will be usefull please let me know so i can post it.

dmesg:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff90000 (usable)
[    0.000000]  BIOS-e820: 000000007ff90000 - 000000007ff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff9e000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524176) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524176
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524176
[    0.000000] On node 0 totalpages: 524176
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292497 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA980 checksum 0
[    0.000000] ACPI: RSDP 000FA980, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FF90000, 003C (r1 KOZIRO FRONTIER  1000730 MSFT       97)
[    0.000000] ACPI: FACP 7FF90200, 0084 (r2 MSTEST OEMFACP   1000730 MSFT       97)
[    0.000000] ACPI: DSDT 7FF905C0, 8F8F (r1  A0545 A0545000        0 INTL 20060113)
[    0.000000] ACPI: FACS 7FF9E000, 0040
[    0.000000] ACPI: APIC 7FF90390, 006C (r1 MSTEST OEMAPIC   1000730 MSFT       97)
[    0.000000] ACPI: MCFG 7FF90400, 003C (r1 MSTEST OEMMCFG   1000730 MSFT       97)
[    0.000000] ACPI: SLIC 7FF90440, 0176 (r1 KOZIRO FRONTIER  1000730 MSFT       97)
[    0.000000] ACPI: OEMB 7FF9E040, 007B (r1 MSTEST AMI_OEM   1000730 MSFT       97)
[    0.000000] ACPI: HPET 7FF99550, 0038 (r1 MSTEST OEMHPET   1000730 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a202 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520081
[    0.000000] Kernel command line: root=UUID=677e4e11-a9a1-4146-b858-2bf45ea358ee ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2599.964 MHz processor.
[   26.260537] Console: colour VGA+ 80x25
[   26.260539] console [tty0] enabled
[   26.260760] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   26.260967] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.322252] Memory: 2065796k/2096704k available (2177k kernel code, 29532k reserved, 1006k data, 368k init, 1179200k highmem)
[   26.322257] virtual kernel memory layout:
[   26.322258]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   26.322258]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.322259]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   26.322260]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   26.322260]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   26.322261]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   26.322262]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   26.322264] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.322297] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   26.322396] hpet clockevent registered
[   26.402224] Calibrating delay using timer specific routine.. 5203.33 BogoMIPS (lpj=10406664)
[   26.402240] Security Framework initialized
[   26.402245] SELinux:  Disabled at boot.
[   26.402255] AppArmor: AppArmor initialized
[   26.402258] Failure registering capabilities with primary security module.
[   26.402263] Mount-cache hash table entries: 512
[   26.402355] Initializing cgroup subsys ns
[   26.402359] Initializing cgroup subsys cpuacct
[   26.402366] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   26.402370] monitor/mwait feature present.
[   26.402371] using mwait in idle threads.
[   26.402374] CPU: L1 I cache: 32K, L1 D cache: 32K
[   26.402376] CPU: L2 cache: 2048K
[   26.402377] CPU: Physical Processor ID: 0
[   26.402378] CPU: Processor Core ID: 0
[   26.402380] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   26.402386] Compat vDSO mapped to ffffe000.
[   26.402396] Checking 'hlt' instruction... OK.
[   26.418504] SMP alternatives: switching to UP code
[   26.419601] Early unpacking initramfs... done
[   26.661574] ACPI: Core revision 20070126
[   26.661611] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.692119] CPU0: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 02
[   26.692130] SMP alternatives: switching to SMP code
[   26.692611] Booting processor 1/1 eip 3000
[   26.703283] Initializing CPU#1
[   26.781382] Calibrating delay using timer specific routine.. 5199.73 BogoMIPS (lpj=10399476)
[   26.781386] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   26.781390] monitor/mwait feature present.
[   26.781392] CPU: L1 I cache: 32K, L1 D cache: 32K
[   26.781393] CPU: L2 cache: 2048K
[   26.781395] CPU: Physical Processor ID: 0
[   26.781395] CPU: Processor Core ID: 1
[   26.781396] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   26.781770] CPU1: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 02
[   26.781785] Total of 2 processors activated (10403.07 BogoMIPS).
[   26.781919] ENABLING IO-APIC IRQs
[   26.782075] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.929136] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   26.949103] Brought up 2 CPUs
[   26.949122] CPU0 attaching sched-domain:
[   26.949124]  domain 0: span 03
[   26.949125]   groups: 01 02
[   26.949127] CPU1 attaching sched-domain:
[   26.949128]  domain 0: span 03
[   26.949129]   groups: 02 01
[   26.949289] net_namespace: 64 bytes
[   26.949296] Booting paravirtualized kernel on bare hardware
[   26.949595] Time: 16:53:45  Date: 09/16/08
[   26.949614] NET: Registered protocol family 16
[   26.949745] EISA bus registered
[   26.949748] ACPI: bus type pci registered
[   26.949899] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[   26.949901] PCI: Using configuration type 1
[   26.949913] Setting up standard PCI resources
[   26.959028] ACPI: EC: Look up EC in DSDT
[   26.963400] ACPI: Interpreter enabled
[   26.963402] ACPI: (supports S0 S1 S3 S4 S5)
[   26.963413] ACPI: Using IOAPIC for interrupt routing
[   26.968664] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.969202] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   26.969205] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   26.969934] PCI: Transparent bridge - 0000:00:1e.0
[   26.969959] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.970068] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   26.970129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   26.970215] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   26.970277] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   26.970337] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   26.972439] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   26.972526] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   26.972612] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   26.972697] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   26.972783] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   26.972868] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   26.972954] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   26.973040] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[   26.973133] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  E4, should be D7 [20070126]
[   26.973138] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.973159] pnp: PnP ACPI init
[   26.973164] ACPI: bus type pnp registered
[   26.975943] pnp: PnP ACPI: found 16 devices
[   26.975945] ACPI: ACPI bus type pnp unregistered
[   26.975947] PnPBIOS: Disabled by ACPI PNP
[   26.976107] PCI: Using ACPI for IRQ routing
[   26.976109] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.004973] NET: Registered protocol family 8
[   27.004975] NET: Registered protocol family 20
[   27.005003] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   27.005007] hpet0: 3 64-bit timers, 14318180 Hz
[   27.006028] AppArmor: AppArmor Filesystem Enabled
[   27.008974] Time: tsc clocksource has been installed.
[   27.008984] Switched to high resolution mode on CPU 0
[   27.009060] Switched to high resolution mode on CPU 1
[   27.024974] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   27.024983] system 00:08: ioport range 0x290-0x297 has been reserved
[   27.024988] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   27.024990] system 00:09: ioport range 0x800-0x87f has been reserved
[   27.024992] system 00:09: ioport range 0x480-0x4bf has been reserved
[   27.024995] system 00:09: iomem range 0xffafe000-0xffb0cbff could not be reserved
[   27.024997] system 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[   27.025000] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   27.025002] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[   27.025004] system 00:09: iomem range 0xfff00000-0xfffffffe could not be reserved
[   27.025007] system 00:09: iomem range 0xfebfe000-0xfebfec00 has been reserved
[   27.025013] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   27.025015] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   27.025021] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[   27.025026] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   27.025028] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
[   27.025030] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   27.025033] system 00:0f: iomem range 0x100000-0x7fffffff could not be reserved
[   27.025035] system 00:0f: iomem range 0x0-0x0 could not be reserved
[   27.055304] PCI: Bridge: 0000:00:01.0
[   27.055306]   IO window: 9000-9fff
[   27.055308]   MEM window: fa700000-fe7fffff
[   27.055310]   PREFETCH window: b7e00000-d7dfffff
[   27.055313] PCI: Bridge: 0000:00:1c.0
[   27.055313]   IO window: disabled.
[   27.055316]   MEM window: disabled.
[   27.055319]   PREFETCH window: d7e00000-d7efffff
[   27.055322] PCI: Bridge: 0000:00:1c.3
[   27.055324]   IO window: b000-bfff
[   27.055327]   MEM window: fe900000-fe9fffff
[   27.055329]   PREFETCH window: disabled.
[   27.055333] PCI: Bridge: 0000:00:1c.4
[   27.055334]   IO window: a000-afff
[   27.055337]   MEM window: fe800000-fe8fffff
[   27.055340]   PREFETCH window: disabled.
[   27.055343] PCI: Bridge: 0000:00:1e.0
[   27.055344]   IO window: disabled.
[   27.055347]   MEM window: fea00000-feafffff
[   27.055349]   PREFETCH window: d7f00000-dfefffff
[   27.055361] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.055364] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   27.055377] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.055380] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   27.055393] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[   27.055396] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   27.055408] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   27.055412] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   27.055419] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   27.055426] NET: Registered protocol family 2
[   27.092843] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   27.093031] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   27.093361] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   27.093544] TCP: Hash tables configured (established 131072 bind 65536)
[   27.093546] TCP reno registered
[   27.104876] checking if image is initramfs... it is
[   27.583115] Freeing initrd memory: 8146k freed
[   27.583680] audit: initializing netlink socket (disabled)
[   27.583691] audit(1221584025.113:1): initialized
[   27.583852] highmem bounce pool size: 64 pages
[   27.585187] VFS: Disk quotas dquot_6.5.1
[   27.585236] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.585326] io scheduler noop registered
[   27.585327] io scheduler anticipatory registered
[   27.585329] io scheduler deadline registered
[   27.585336] io scheduler cfq registered (default)
[   35.565960] 0000:00:1a.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   35.566137] Boot video device is 0000:01:00.0
[   35.566222] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   35.566246] assign_interrupt_mode Found MSI capability
[   35.566265] Allocate Port Service[0000:00:01.0:pcie00]
[   35.566318] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   35.566348] assign_interrupt_mode Found MSI capability
[   35.566372] Allocate Port Service[0000:00:1c.0:pcie00]
[   35.566393] Allocate Port Service[0000:00:1c.0:pcie02]
[   35.566450] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   35.566480] assign_interrupt_mode Found MSI capability
[   35.566504] Allocate Port Service[0000:00:1c.3:pcie00]
[   35.566525] Allocate Port Service[0000:00:1c.3:pcie02]
[   35.566582] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   35.566612] assign_interrupt_mode Found MSI capability
[   35.566636] Allocate Port Service[0000:00:1c.4:pcie00]
[   35.566657] Allocate Port Service[0000:00:1c.4:pcie02]
[   35.566820] isapnp: Scanning for PnP cards...
[   35.919036] isapnp: No Plug & Play device found
[   35.935463] Real Time Clock Driver v1.12ac
[   35.935594] hpet_resources: 0xfed00000 is busy
[   35.935627] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.935723] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.936146] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.936689] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.936734] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   35.936799] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   35.936801] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   35.937287] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.954534] mice: PS/2 mouse device common for all mice
[   35.954611] EISA: Probing bus 0 at eisa.0
[   35.954633] EISA: Detected 0 cards.
[   35.954636] cpuidle: using governor ladder
[   35.954637] cpuidle: using governor menu
[   35.954697] NET: Registered protocol family 1
[   35.954717] Using IPI No-Shortcut mode
[   35.954739] registered taskstats version 1
[   35.954824]   Magic number: 8:257:894
[   35.954844]   hash matches device ptyy4
[   35.954867] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   35.954868] EDD information not available.
[   35.955003] Freeing unused kernel memory: 368k freed
[   35.972298] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   37.090440] fuse init (API version 7.9)
[   37.104160] ACPI: SSDT 7FF9E0C0, 01C6 (r1    AMI   CPU1PM        1 INTL 20060113)
[   37.104431] ACPI: SSDT 7FF9E290, 013A (r1    AMI   CPU2PM        1 INTL 20060113)
[   37.104601] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   37.104609] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   37.116053] device-mapper: uevent: version 1.0.3
[   37.116084] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   37.327258] usbcore: registered new interface driver usbfs
[   37.327275] usbcore: registered new interface driver hub
[   37.327758] usbcore: registered new device driver usb
[   37.335684] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   37.335695] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   37.335698] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   37.335888] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   37.339776] ehci_hcd 0000:00:1a.7: debug port 1
[   37.339780] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   37.339787] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfebffc00
[   37.352437] USB Universal Host Controller Interface driver v3.0
[   37.354975] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.355070] usb usb1: configuration #1 chosen from 1 choice
[   37.355086] hub 1-0:1.0: USB hub found
[   37.355091] hub 1-0:1.0: 4 ports detected
[   37.364427] SCSI subsystem initialized
[   37.397625] libata version 3.00 loaded.
[   37.452642] Floppy drive(s): fd0 is 1.44M
[   37.458837] r8169 Gigabit Ethernet driver 2.2LK loaded
[   37.458862] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[   37.458879] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   37.459129] eth0: RTL8168b/8111b at 0xf888c000, 00:1a:92:59:69:1a, XID 38000000 IRQ 219
[   37.460215] ahci 0000:02:00.0: version 3.0
[   37.460238] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.472373] FDC 0 is a post-1991 82077
[   38.459552] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   38.459556] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   38.459562] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   38.459705] scsi0 : ahci
[   38.459849] scsi1 : ahci
[   38.459894] ata1: SATA max UDMA/133 abar m8192@0xfe8fe000 port 0xfe8fe100 irq 16
[   38.459897] ata2: SATA max UDMA/133 abar m8192@0xfe8fe000 port 0xfe8fe180 irq 16
[   38.778829] ata1: SATA link down (SStatus 0 SControl 300)
[   39.098119] ata2: SATA link down (SStatus 0 SControl 300)
[   39.098183] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
[   39.098215] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   39.098225] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   39.098243] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
[   39.098259] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   39.098267] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[   39.098290] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[   39.098297] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 17 (level, low) -> IRQ 19
[   39.098324] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   39.098333] ACPI: PCI interrupt for device 0000:02:00.1 disabled
[   39.098623] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   39.098630] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   39.098633] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   39.098654] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   39.102553] ehci_hcd 0000:00:1d.7: debug port 1
[   39.102558] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   39.102564] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfebff800
[   39.119060] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   39.119157] usb usb2: configuration #1 chosen from 1 choice
[   39.119179] hub 2-0:1.0: USB hub found
[   39.119184] hub 2-0:1.0: 6 ports detected
[   39.222916] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   39.222924] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   39.222928] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   39.222950] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   39.222971] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000dc00
[   39.223066] usb usb3: configuration #1 chosen from 1 choice
[   39.223081] hub 3-0:1.0: USB hub found
[   39.223084] hub 3-0:1.0: 2 ports detected
[   39.329684] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 19
[   39.329694] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   39.329698] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   39.329719] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   39.329743] uhci_hcd 0000:00:1a.1: irq 19, io base 0x0000e000
[   39.329840] usb usb4: configuration #1 chosen from 1 choice
[   39.329856] hub 4-0:1.0: USB hub found
[   39.329859] hub 4-0:1.0: 2 ports detected
[   39.429450] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   39.429457] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   39.429460] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   39.429478] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   39.429498] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000d480
[   39.429599] usb usb5: configuration #1 chosen from 1 choice
[   39.429616] hub 5-0:1.0: USB hub found
[   39.429619] hub 5-0:1.0: 2 ports detected
[   39.533213] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   39.533219] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   39.533222] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   39.533241] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   39.533263] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d800
[   39.533369] usb usb6: configuration #1 chosen from 1 choice
[   39.533385] hub 6-0:1.0: USB hub found
[   39.533388] hub 6-0:1.0: 2 ports detected
[   39.636992] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   39.636999] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   39.637002] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   39.637022] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   39.637042] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d880
[   39.637132] usb usb7: configuration #1 chosen from 1 choice
[   39.637156] hub 7-0:1.0: USB hub found
[   39.637159] hub 7-0:1.0: 2 ports detected
[   39.743131] ata_piix 0000:00:1f.2: version 2.12
[   39.743135] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   39.773593] usb 5-2: new low speed USB device using uhci_hcd and address 2
[   39.896378] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
[   39.896406] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   39.896439] scsi2 : ata_piix
[   39.896590] scsi3 : ata_piix
[   39.897663] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 17
[   39.897665] ata4: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 17
[   39.995374] usb 5-2: configuration #1 chosen from 1 choice
[   40.007303] usbcore: registered new interface driver hiddev
[   40.035390] input: Microsoft Corporation Microsoft &#65533; Laser Mouse 6000 as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input2
[   40.064004] input,hidraw0: USB HID v1.11 Mouse [Microsoft Corporation Microsoft &#65533; Laser Mouse 6000] on usb-0000:00:1d.0-2
[   40.064016] usbcore: registered new interface driver usbhid
[   40.064019] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   40.101422] ata3.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[   40.101426] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   40.167906] ata3.00: configured for UDMA/133
[   40.363047] ata4.00: ATA-7: ST3500630AS, 3.AAE, max UDMA/133
[   40.363050] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   40.429546] ata4.00: configured for UDMA/133
[   40.429650] scsi 2:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[   40.429760] scsi 3:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[   40.429803] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[   40.429817] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
[   40.429840] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   40.429874] scsi4 : ata_piix
[   40.429905] scsi5 : ata_piix
[   40.430683] ata5: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 17
[   40.430685] ata6: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 17
[   40.618579] ata5.00: ATA-7: ST3250824AS, 3.AAH, max UDMA/133
[   40.618582] ata5.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   40.685075] ata5.00: configured for UDMA/133
[   40.846506] ata6.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
[   40.846510] ata6.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   40.854499] ata6.00: configured for UDMA/133
[   40.854584] scsi 4:0:0:0: Direct-Access     ATA      ST3250824AS      3.AA PQ: 0 ANSI: 5
[   40.854691] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   40.854857] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 17 (level, low) -> IRQ 19
[   40.854885] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   40.855040] scsi6 : pata_jmicron
[   40.855071] scsi7 : pata_jmicron
[   40.855508] ata7: PATA max UDMA/100 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 19
[   40.855510] ata8: PATA max UDMA/100 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 19
[   40.859461] Driver 'sd' needs updating - please use bus_type methods
[   40.859514] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   40.859521] sd 2:0:0:0: [sda] Write Protect is off
[   40.859523] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   40.859534] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.859567] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   40.859573] sd 2:0:0:0: [sda] Write Protect is off
[   40.859575] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   40.859586] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.859588]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 >
[   40.944585] sd 2:0:0:0: [sda] Attached SCSI disk
[   40.944633] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   40.944641] sd 3:0:0:0: [sdb] Write Protect is off
[   40.944643] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   40.944655] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.944687] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   40.944694] sd 3:0:0:0: [sdb] Write Protect is off
[   40.944695] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   40.944707] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.944709]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
[   40.992765] sd 3:0:0:0: [sdb] Attached SCSI disk
[   40.992804] sd 4:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   40.992813] sd 4:0:0:0: [sdc] Write Protect is off
[   40.992815] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   40.992831] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.992873] sd 4:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   40.992880] sd 4:0:0:0: [sdc] Write Protect is off
[   40.992881] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   40.992892] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.992894]  sdc: unknown partition table
[   41.007495] sd 4:0:0:0: [sdc] Attached SCSI disk
[   41.007534] sd 5:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[   41.007551] sd 5:0:0:0: [sdd] Write Protect is off
[   41.007552] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   41.007564] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.007589] sd 5:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[   41.007596] sd 5:0:0:0: [sdd] Write Protect is off
[   41.007598] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   41.007610] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.007612]  sdd: sdd1 sdd2 < sdd5 sdd6 sdd7 >
[   41.062897] sd 5:0:0:0: [sdd] Attached SCSI disk
[   41.066066] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   41.066080] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   41.066093] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   41.066106] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   41.174999] ata7.00: ATAPI: PIONEER DVD-RW  DVR-115D, 1.13, max UDMA/66
[   41.345643] ata7.00: configured for UDMA/66
[   41.519667] scsi 6:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-115D 1.13 PQ: 0 ANSI: 5
[   41.519741] scsi 6:0:0:0: Attached scsi generic sg4 type 5
[   41.524543] Driver 'sr' needs updating - please use bus_type methods
[   41.584582] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   41.584586] Uniform CD-ROM driver Revision: 3.20
[   41.584631] sr 6:0:0:0: Attached scsi CD-ROM sr0
[   46.936572] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
[   46.936579] ReiserFS: sda5: using ordered data mode
[   46.940427] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   46.940648] ReiserFS: sda5: checking transaction log (sda5)
[   46.965613] ReiserFS: sda5: Using r5 hash to sort names
[   50.553660] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.618500] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   50.665060] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   50.696326] iTCO_vendor_support: vendor-support=0
[   50.711210] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   50.711275] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0860)
[   50.711305] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   50.761319] parport_pc 00:0b: reported by Plug and Play ACPI
[   50.761419] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   50.804090] Linux agpgart interface v0.102
[   50.910606] input: Power Button (FF) as /devices/virtual/input/input4
[   50.963750] ACPI: Power Button (FF) [PWRF]
[   50.963820] input: Power Button (CM) as /devices/virtual/input/input5
[   51.027589] ACPI: Power Button (CM) [PWRB]
[   51.747101] Linux video capture interface: v2.00
[   51.838751] r8169: eth0: link up
[   51.838755] r8169: eth0: link up
[   51.939184] nvidia: module license 'NVIDIA' taints kernel.
[   52.209206] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   52.209214] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   52.209335] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   52.365802] ivtv:  Start initialization, version 1.1.0
[   52.365862] ivtv0: Initializing card #0
[   52.365864] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   52.373985] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 23 (level, low) -> IRQ 20
[   52.432948] tveeprom 0-0050: Hauppauge model 26152, rev F1B2, serial# 9946456
[   52.432951] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   52.432953] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   52.432954] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   52.432956] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   52.432957] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   52.432960] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   52.432961] ivtv0: Reopen i2c bus for IR-blaster support
[   52.451208] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   52.451226] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   52.565845] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   52.793813] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   52.799682] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   52.808329] tuner-simple 0-0061: type set to 50 (TCL 2002N)
[   52.808331] tuner 0-0061: type set to TCL 2002N
[   52.808519] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   52.808533] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   52.808547] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   52.808561] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   52.808563] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   52.808574] ivtv:  End initialization
[   52.994659] loop: module loaded
[   53.011857] lp0: using parport0 (interrupt-driven).
[   53.070232] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
[   53.159215] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 22 (level, low) -> IRQ 21
[   53.735588] MadWifi: ath_attach: Switching rfkill capability off.
[   53.750345] wifi0: Atheros AR2414 chip found (MAC 7.9, PHY 2112A 4.5, Radio 5.6)
[   53.765521] ath_pci: wifi0: Atheros 5212: mem=0xfeaf0000, irq=21
[   53.779490] lirc_dev: IR Remote Control driver registered, at major 61 
[   53.838960] bttv: driver version 0.9.17 loaded
[   53.838963] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   53.892402] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   53.915534] lirc_i2c: chip 0x10020 found @ 0x71 (Hauppauge PVR150)
[   53.915552] lirc_dev: lirc_register_plugin: sample_rate: 10
[   53.992366] w83627ehf: Found W83627DHG chip at 0x290
[   53.992469] w83627ehf w83627ehf.656: VID pins in output mode, CPU VID not available
[   54.037059] Adding 2618552k swap on /dev/sda6.  Priority:-1 extents:1 across:2618552k
[  120.062010] ReiserFS: sda11: found reiserfs format "3.6" with standard journal
[  120.062025] ReiserFS: sda11: using ordered data mode
[  120.071301] ReiserFS: sda11: journal params: device sda11, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  120.071557] ReiserFS: sda11: checking transaction log (sda11)
[  120.117230] ReiserFS: sda11: Using r5 hash to sort names
[  120.150735] ReiserFS: sdb5: found reiserfs format "3.6" with standard journal
[  120.150740] ReiserFS: sdb5: using ordered data mode
[  120.158570] ReiserFS: sdb5: journal params: device sdb5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  120.158843] ReiserFS: sdb5: checking transaction log (sdb5)
[  120.210190] ReiserFS: sdb5: Using r5 hash to sort names
[  120.241605] ReiserFS: sdb1: found reiserfs format "3.6" with standard journal
[  120.241611] ReiserFS: sdb1: using ordered data mode
[  120.244937] ReiserFS: sdb1: journal params: device sdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  120.245227] ReiserFS: sdb1: checking transaction log (sdb1)
[  120.276627] ReiserFS: sdb1: Using r5 hash to sort names
[  120.333238] ReiserFS: sdb7: found reiserfs format "3.6" with standard journal
[  120.333246] ReiserFS: sdb7: using ordered data mode
[  120.337670] ReiserFS: sdb7: journal params: device sdb7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  120.337965] ReiserFS: sdb7: checking transaction log (sdb7)
[  120.383991] ReiserFS: sdb7: Using r5 hash to sort names
[  120.628499] ReiserFS: sdd6: found reiserfs format "3.6" with standard journal
[  120.628510] ReiserFS: sdd6: using ordered data mode
[  120.638327] ReiserFS: sdd6: journal params: device sdd6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  120.638621] ReiserFS: sdd6: checking transaction log (sdd6)
[  120.684654] ReiserFS: sdd6: Using r5 hash to sort names
[  120.719168] ReiserFS: sda8: found reiserfs format "3.6" with standard journal
[  120.719174] ReiserFS: sda8: using ordered data mode
[  120.726862] ReiserFS: sda8: journal params: device sda8, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  120.727145] ReiserFS: sda8: checking transaction log (sda8)
[  120.756455] ReiserFS: sda8: Using r5 hash to sort names
[  120.776256] ReiserFS: sda10: found reiserfs format "3.6" with standard journal
[  120.776262] ReiserFS: sda10: using ordered data mode
[  120.780861] ReiserFS: sda10: journal params: device sda10, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  120.781170] ReiserFS: sda10: checking transaction log (sda10)
[  120.789225] ReiserFS: sda10: Using r5 hash to sort names
[  120.803490] ReiserFS: sda7: found reiserfs format "3.6" with standard journal
[  120.803495] ReiserFS: sda7: using ordered data mode
[  120.812154] ReiserFS: sda7: journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  120.812458] ReiserFS: sda7: checking transaction log (sda7)
[  120.846227] ReiserFS: sda7: Using r5 hash to sort names
[  120.869970] ReiserFS: sda9: found reiserfs format "3.6" with standard journal
[  120.869976] ReiserFS: sda9: using ordered data mode
[  120.878142] ReiserFS: sda9: journal params: device sda9, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  120.878423] ReiserFS: sda9: checking transaction log (sda9)
[  120.898524] ReiserFS: sda9: Using r5 hash to sort names
[  120.926137] ReiserFS: dm-0: found reiserfs format "3.6" with standard journal
[  120.926148] ReiserFS: dm-0: using ordered data mode
[  120.928625] ReiserFS: dm-0: journal params: device dm-0, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  120.928937] ReiserFS: dm-0: checking transaction log (dm-0)
[  120.961924] ReiserFS: dm-0: Using r5 hash to sort names
[  123.258372] ip_tables: (C) 2000-2006 Netfilter Core Team
[  123.361921] Bridge firewalling registered
[  123.362002] br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  123.363489] device eth0 entered promiscuous mode
[  123.363496] audit(1221598521.573:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  123.366374] br0: port 1(eth0) entering learning state
[  132.342744] br0: topology change detected, propagating
[  132.342748] br0: port 1(eth0) entering forwarding state
[  132.684750] NET: Registered protocol family 10
[  132.684964] lo: Disabled Privacy Extensions
[  133.277799] tun: Universal TUN/TAP device driver, 1.6
[  133.277801] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[  133.278212] tun: Disabled Privacy Extensions
[  133.329611] tun: Disabled Privacy Extensions
[  133.757758] No dock devices found.
[  137.507612] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[  137.707988] ivtv0: Encoder revision: 0x02060039
[  137.868624] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  137.868628] apm: disabled - APM is not SMP safe.
[  137.980839] ppdev: user-space parallel port driver
[  138.072465] audit(1221598537.020:3): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6564 profile="/usr/sbin/cupsd" namespace="default"
[  141.387871] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[  144.016393] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  144.016398] vboxdrv: Successfully done.
[  144.016399] vboxdrv: Found 2 processor cores.
[  144.016854] vboxdrv: fAsync=0 offMin=0x340 offMax=0x950
[  144.016859] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  144.016861] vboxdrv: Successfully loaded version 2.0.2 (interface 0x00090000).
[  144.471011] device vbox0 entered promiscuous mode
[  144.471019] audit(1221598543.432:4): dev=vbox0 prom=256 old_prom=0 auid=4294967295
[  144.471024] br0: port 2(vbox0) entering learning state
[  149.349801] Bluetooth: Core ver 2.11
[  149.349875] NET: Registered protocol family 31
[  149.349877] Bluetooth: HCI device and connection manager initialized
[  149.349879] Bluetooth: HCI socket layer initialized
[  149.403928] Bluetooth: L2CAP ver 2.9
[  149.403933] Bluetooth: L2CAP socket layer initialized
[  149.483376] Bluetooth: RFCOMM socket layer initialized
[  149.483386] Bluetooth: RFCOMM TTY layer initialized
[  149.483389] Bluetooth: RFCOMM ver 1.8
[  149.845568] sysfs: duplicate filename 'i2c ir driver' can not be created
[  149.845573] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[  149.845576] Pid: 7432, comm: modprobe Tainted: P        2.6.24-19-generic #1
[  149.845600]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[  149.845623]  [<c01d7a18>] create_dir+0x48/0x90
[  149.845642]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[  149.845648]  [<c02154cf>] kobject_get+0xf/0x20
[  149.845656]  [<c0215993>] kobject_add+0x93/0x1b0
[  149.845677]  [<c0215b41>] kobject_register+0x21/0x50
[  149.845685]  [<c0282041>] bus_add_driver+0x71/0x1e0
[  149.845707]  [<f8b39770>] i2c_register_driver+0x70/0x120 [i2c_core]
[  149.845723]  [<fa670088>] init_module+0x48/0x50 [lirc_pvr150]
[  149.845731]  [<c01507c6>] sys_init_module+0x126/0x19c0
[  149.845814]  [<f8c91e00>] lirc_register_plugin+0x0/0x500 [lirc_dev]
[  149.845843]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[  149.845876]  =======================
[  149.845880] kobject_add failed for i2c ir driver with -EEXIST, don't try to register things with the same name in the same directory.
[  149.845884] Pid: 7432, comm: modprobe Tainted: P        2.6.24-19-generic #1
[  149.845890]  [<c0215a13>] kobject_add+0x113/0x1b0
[  149.845910]  [<c0215b41>] kobject_register+0x21/0x50
[  149.845917]  [<c0282041>] bus_add_driver+0x71/0x1e0
[  149.845937]  [<f8b39770>] i2c_register_driver+0x70/0x120 [i2c_core]
[  149.845952]  [<fa670088>] init_module+0x48/0x50 [lirc_pvr150]
[  149.845959]  [<c01507c6>] sys_init_module+0x126/0x19c0
[  149.846034]  [<f8c91e00>] lirc_register_plugin+0x0/0x500 [lirc_dev]
[  149.846061]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[  149.846093]  =======================
[  151.167221] /dev/vmmon[7625]: VMCI: Driver initialized.
[  151.167274] /dev/vmmon[7625]: Module vmmon: registered with major=10 minor=165
[  151.167300] /dev/vmmon[7625]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[  151.167304] /dev/vmmon[7625]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[  151.167306] /dev/vmmon[7625]: Module vmmon: initialized
[  151.739026] /dev/vmnet: open called by PID 7682 (vmnet-bridge)
[  151.739034] /dev/vmnet: hub 0 does not exist, allocating memory.
[  151.739041] /dev/vmnet: port on hub 0 successfully opened
[  151.739049] bridge-ath0: enabling the bridge
[  151.739053] bridge-ath0: is a Wireless Adapter
[  151.739056] bridge-ath0: up
[  151.739057] bridge-ath0: already up
[  151.739059] bridge-ath0: attached
[  152.079298] /dev/vmnet: open called by PID 7699 (vmnet-dhcpd)
[  152.079307] /dev/vmnet: hub 1 does not exist, allocating memory.
[  152.079316] /dev/vmnet: port on hub 1 successfully opened
[  152.119707] /dev/vmnet: open called by PID 7711 (vmnet-dhcpd)
[  152.119716] /dev/vmnet: hub 8 does not exist, allocating memory.
[  152.119725] /dev/vmnet: port on hub 8 successfully opened
[  152.132400] /dev/vmnet: open called by PID 7719 (vmnet-natd)
[  152.132412] /dev/vmnet: port on hub 8 successfully opened
[  153.447937] br0: topology change detected, propagating
[  153.447942] br0: port 2(vbox0) entering forwarding state
[  162.036370] /dev/vmnet: open called by PID 7853 (vmnet-netifup)
[  162.036382] /dev/vmnet: port on hub 1 successfully opened
[  162.057486] /dev/vmnet: open called by PID 7864 (vmnet-netifup)
[  162.057500] /dev/vmnet: port on hub 8 successfully opened
[  202.444581] tun: Disabled Privacy Extensions
[  202.463850] tun: Disabled Privacy Extensions
[  272.469931] tun: Disabled Privacy Extensions
[  272.488152] tun: Disabled Privacy Extensions
[  342.037218] tun: Disabled Privacy Extensions
[  342.055966] tun: Disabled Privacy Extensions
[  411.897127] tun: Disabled Privacy Extensions
[  411.916516] tun: Disabled Privacy Extensions
[  481.726582] tun: Disabled Privacy Extensions
[  481.747191] tun: Disabled Privacy Extensions
[  551.687447] tun: Disabled Privacy Extensions
[  551.705628] tun: Disabled Privacy Extensions



lspci:
lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:01.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
05:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)



/etc/lirc/hardware.conf:
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Hauppauge PVR-150 (pci) : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_pvr150 lirc_dev"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

---

### Post by roob85 on 2008-09-16
well ive been playing around with this for a while tonight and when i make a change in mcc for the ir blaster and hit apply it gets hung up...its been sitting for almost 5 mins. I see some lines in ps x that show its stalled doing a modprobe....and i also saw some interesting output in dmesg so i figured id update this with the info.


ps x:
18520 ?        Ss     0:02 python /usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre
18567 ?        S      0:00 /usr/bin/perl -w /usr/sbin/dpkg-reconfigure lirc
18606 ?        S      0:00 /bin/sh /var/lib/dpkg/info/lirc.postinst configure 0.8.3~pre1-0ubuntu7.1
18814 ?        S      0:00 /bin/sh /usr/sbin/invoke-rc.d lirc start
18830 ?        S      0:00 /bin/sh /etc/init.d/lirc start
18843 ?        D      0:00 modprobe -k lirc_i2c
18969 pts/2    R+     0:00 ps x




dmesg:
[  481.747191] tun: Disabled Privacy Extensions
[  551.687447] tun: Disabled Privacy Extensions
[  551.705628] tun: Disabled Privacy Extensions
[15262.066868] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000010
[15262.066874] printing eip: c0319ff4 *pde = 00000000
[15262.066878] Oops: 0000 [#1] SMP
[15262.066881] Modules linked in: vmnet(P) vmblock(P) vmmon(P) binfmt_misc lirc_pvr150 rfcomm l2cap bluetooth vboxdrv ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table video output container sbs sbshc dock battery tun ipv6 bridge iptable_filter ip_tables x_tables vfat fat aes_i586 dm_crypt ac w83627ehf hwmon_vid cx8800 cx88xx bttv ir_common compat_ioctl32 videobuf_dma_sg videobuf_core btcx_risc lirc_dev wlan_scan_sta ath_rate_sample ath_pci wlan ath_hal(P) lp loop wm8775 cx25840 tuner tea5767 tda8290 tuner_simple mt20xx tea5761 snd_hda_intel snd_pcm_oss snd_mixer_oss ivtv snd_pcm i2c_algo_bit nvidia(P) snd_page_alloc snd_hwdep cx2341x snd_seq_dummy tveeprom i2c_core videodev v4l2_common v4l1_compat snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device button snd intel_agp agpgart parport_pc parport iTCO_wdt iTCO_vendor_support shpchp evdev soundcore pcspkr pci_hotplug reiserfs sr_mod cdrom sg sd_mod usbhid hid pata_jmicron ata_piix ata_generic floppy pata_acpi ahci r8169 libata scsi_mod uhci_hcd ehci_hcd usbcore dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
[15262.066955]
[15262.066957] Pid: 18656, comm: rmmod Tainted: P        (2.6.24-19-generic #1)
[15262.066960] EIP: 0060:[<c0319ff4>] EFLAGS: 00010296 CPU: 1
[15262.066965] EIP is at klist_del+0x14/0x50
[15262.066967] EAX: 00000000 EBX: 00000000 ECX: 00000000 EDX: 00000000
[15262.066969] ESI: fa67344c EDI: fa673488 EBP: fa673420 ESP: df97defc
[15262.066971]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[15262.066973] Process rmmod (pid: 18656, ti=df97c000 task=f5971700 task.ti=df97c000)
[15262.066974] Stack: fa673488 fa67344c f8b3d9a0 c031a088 dfadd000 c028221c dfadd000 df648974
[15262.066980]        df648974 f8b39902 f5971700 c0125f20 00100100 00200200 eff2d700 dfccb23c
[15262.066985]        dfccb1a4 df648974 f8b3dab4 fa673780 00000000 00000000 df97c000 fa67000a
[15262.066990] Call Trace:
[15262.066999]  [<c031a088>] klist_remove+0x8/0x20
[15262.067005]  [<c028221c>] bus_remove_driver+0x6c/0xa0
[15262.067013]  [<f8b39902>] i2c_del_driver+0x22/0x180 [i2c_core]
[15262.067022]  [<c0125f20>] default_wake_function+0x0/0x10
[15262.067037]  [<fa67000a>] cleanup_module+0xa/0x40 [lirc_pvr150]
[15262.067042]  [<c01521a2>] sys_delete_module+0x112/0x190
[15262.067052]  [<c01804a0>] do_munmap+0x180/0x1f0
[15262.067070]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[15262.067082]  [<c0310000>] unix_stream_sendmsg+0x110/0x390
[15262.067093]  =======================
[15262.067094] Code: 43 04 8b 14 24 8b 30 85 d2 0f 95 44 24 07 eb 9b 8d b4 26 00 00 00 00 83 ec 0c 89 7c 24 08 89 c7 89 1c 24 89 74 24 04 8b 18 89 d8 <8b> 73 10 e8 a4 23 00 00 89 f8 e8 1d ff ff ff 83 f8 01 19 c0 f7
[15262.067122] EIP: [<c0319ff4>] klist_del+0x14/0x50 SS:ESP 0068:df97defc
[15262.067127] ---[ end trace a05aa1978a184d45 ]---



Something seems very wrong with this. please let me know if anyone has any ideas or suggestions.

---

