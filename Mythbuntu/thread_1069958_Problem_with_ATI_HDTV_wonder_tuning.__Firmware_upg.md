---
title: "Problem with ATI HDTV wonder tuning.  Firmware upgraded"
date: 2009-02-14
forum: Mythbuntu
---

### Post by molder on 2009-02-14
I am having tons of trouble getting MythTV setup to use ATI HDTV Wonder.  I have upgraded the firmware but still having scan timeout/no table errors.  Here is a truncated cut and paste of the output of the dmesg command after a fresh cold reboot.  I have also included the entirety of the output. Is the a IRQ conflict?

Thanks

**_Truncated Output (cx88):_**

IRQ 17
[   13.756409] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.176025] intel8x0_measure_ac97_clock: measured 54852 usecs
[   14.176031] intel8x0: clocking to 48000
[   14.281706] Linux video capture interface: v2.00
[   14.584293] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   14.585023] cx88[0]: subsystem: 1002:a101, board: ATI HDTV Wonder [card=34,autodetected]
[   14.585028] cx88[0]: TV tuner type 68, Radio tuner type -1
[   14.610215] cx2388x alsa driver version 0.0.6 loaded
[   14.648266] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   15.228881] cx88[0]/2: cx2388x 8802 Driver Manager
[   15.228910] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.228923] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 18, latency: 64, mmio: 0xfd000000
[   15.248101] cx88_audio 0000:01:06.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.248146] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   15.249047] cx8800 0000:01:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.249058] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 18, latency: 64, mmio: 0xfb000000
[   15.249185] cx88[0]/0: registered device video0 [v4l2]
[   15.249266] cx88[0]/0: registered device vbi0
[   15.447821] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   15.447827] cx88/2: registering cx8802 driver, type: dvb access: shared
[   15.447832] cx88[0]/2: subsystem: 1002:a101, board: ATI HDTV Wonder [card=34]
[   15.447837] cx88[0]/2: cx2388x based DVB/ATSC card
[   15.695791] nxt200x: NXT2004 Detected
[   15.875359] tuner-simple 0-0061: creating new instance
[   15.875366] tuner-simple 0-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   15.875374] DVB: registering new adapter (cx88[0])
[   15.875380] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   20.948734] end_request: I/O error, dev sr0, sector 1232504
[   20.948746] Buffer I/O error on device sr0, logical block 308126
[   21.128260] end_request: I/O error, dev sr0, sector 1232504
[   21.128266] Buffer I/O error on device sr0, logical block 308126
[   21.351728] end_request: I/O error, dev sr0, sector 1232504
[   21.351735] Buffer I/O error on device sr0, logical block 308126
[   21.543606] end_request: I/O error, dev sr0, sector 1232504
[   21.543612] Buffer I/O error on device sr0, logical block 308126
[   21.742152] end_request: I/O error, dev sr0, sector 1232504
[   21.742158] Buffer I/O error on device sr0, logical block 308126
[   21.993583] end_request: I/O error, dev sr0, sector 1232504
[   21.993589] Buffer I/O error on device sr0, logical block 308126
[   22.174865] end_request: I/O error, dev sr0, sector 1232504
[   22.174871] Buffer I/O error on device sr0, logical block 308126
[   22.534979] end_request: I/O error, dev sr0, sector 1232504
[   22.534986] Buffer I/O error on device sr0, logical block 308126
[   22.706498] end_request: I/O error, dev sr0, sector 1232504
[   22.706504] Buffer I/O error on device sr0, logical block 308126
[   23.816951] loop: module loaded
[   23.921866] lp: driver loaded but no devices found
[   24.460259] Adding 1694816k swap on /dev/sda5.  Priority:-1 extents:1 across:1694816k
[   25.345776] EXT3 FS on sda1, internal journal
[   27.702775] type=1505 audit(1234640463.047:2): 

**_Entire Output:_**

andrew@MythTV-Molder:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f774000 (usable)
[    0.000000]  BIOS-e820: 000000002f774000 - 000000002f776000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002f776000 - 000000002f797000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002f797000 - 000000002f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x2f774 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 2f774000 @ 7000-d000
[    0.000000] RAMDISK: 2ef8e000 - 2f763bb3
[    0.000000] ACPI: RSDP 000FEB80, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD2EA, 0034 (r1 DELL    2400           7 ASL        61)
[    0.000000] ACPI: FACP 000FD31E, 0074 (r1 DELL    2400           7 ASL        61)
[    0.000000] ACPI: DSDT FFFCBE22, 2404 (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 2F774000, 0040
[    0.000000] ACPI: SSDT FFFCE363, 00BA (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FD392, 006C (r1 DELL    2400           7 ASL        61)
[    0.000000] ACPI: BOOT 000FD3FE, 0028 (r1 DELL    2400           7 ASL        61)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2f774000
[    0.000000]   low ram: 00000000 - 2f774000
[    0.000000]   bootmap 00009000 - 0000eef0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002f774000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [002ef8e000 - 002f763bb3]          RAMDISK ==> [002ef8e000 - 002f763bb3]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000009000 - 000000f000]          BOOTMAP ==> [0000009000 - 000000f000]
[    0.000000] found SMP MP-table at [c00fe710] 000fe710
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002f774
[    0.000000]   HighMem  0x0002f774 -> 0x0002f774
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0002f774
[    0.000000] On node 0 totalpages: 194324
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 188651 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f800000:cf400000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 192615
[    0.000000] Kernel command line: root=UUID=375f9637-753d-4eb8-bd79-d830a1dfd1fc ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2193.513 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 756284k/777680k available (2576k kernel code, 20772k reserved, 1165k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf0000000 - 0xff3fe000   ( 243 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xef774000   ( 759 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 4387.02 BogoMIPS (lpj=8774052)
[    0.004042] Security Framework initialized
[    0.004052] SELinux:  Disabled at boot.
[    0.004083] AppArmor: AppArmor initialized
[    0.004099] Mount-cache hash table entries: 512
[    0.004376] Initializing cgroup subsys ns
[    0.004383] Initializing cgroup subsys cpuacct
[    0.004388] Initializing cgroup subsys memory
[    0.004413] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004418] CPU: L2 cache: 512K
[    0.004423] CPU: Hyper-Threading is disabled
[    0.004444] Checking 'hlt' instruction... OK.
[    0.020681] SMP alternatives: switching to UP code
[    0.030620] ACPI: Core revision 20080609
[    0.042674] ACPI: Checking initramfs for custom DSDT
[    0.496649] ENABLING IO-APIC IRQs
[    0.496847] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.536540] CPU0: Intel(R) Pentium(R) 4 CPU 2.20GHz stepping 09
[    0.540031] Brought up 1 CPUs
[    0.540031] Total of 1 processors activated (4387.02 BogoMIPS).
[    0.540031] CPU0 attaching NULL sched-domain.
[    0.540031] net_namespace: 840 bytes
[    0.540031] Booting paravirtualized kernel on bare hardware
[    0.540031] Time: 19:40:35  Date: 02/14/09
[    0.540031] NET: Registered protocol family 16
[    0.540031] EISA bus registered
[    0.540031] ACPI: bus type pci registered
[    0.540031] PCI: PCI BIOS revision 2.10 entry at 0xfbc7f, last bus=1
[    0.540031] PCI: Using configuration type 1 for base access
[    0.540809] ACPI: EC: Look up EC in DSDT
[    0.571366] ACPI: Interpreter enabled
[    0.571376] ACPI: (supports S0 S1 S3 S4 S5)
[    0.571404] ACPI: Using IOAPIC for interrupt routing
[    0.603244] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.603371] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, efffffff]
[    0.603454] PCI: 0000:00:02.0 reg 10 32bit mmio: [f0000000, f7ffffff]
[    0.603463] PCI: 0000:00:02.0 reg 14 32bit mmio: [feb80000, febfffff]
[    0.603584] PCI: 0000:00:1d.0 reg 20 io port: [ff80, ff9f]
[    0.603644] PCI: 0000:00:1d.1 reg 20 io port: [ff60, ff7f]
[    0.603705] PCI: 0000:00:1d.2 reg 20 io port: [ff40, ff5f]
[    0.603774] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ffa80800, ffa80bff]
[    0.604051] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.604058] pci 0000:00:1d.7: PME# disabled
[    0.604105] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.604107] * this clock source is slow. If you are sure your timer does not have
[    0.604109] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.604157] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.604166] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.604171] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.604195] PCI: 0000:00:1f.1 reg 10 io port: [ed90, ed97]
[    0.604204] PCI: 0000:00:1f.1 reg 14 io port: [ed88, ed8b]
[    0.604212] PCI: 0000:00:1f.1 reg 18 io port: [ed98, ed9f]
[    0.604221] PCI: 0000:00:1f.1 reg 1c io port: [ed8c, ed8f]
[    0.604229] PCI: 0000:00:1f.1 reg 20 io port: [ffa0, ffaf]
[    0.604238] PCI: 0000:00:1f.1 reg 24 32bit mmio: [feb7fc00, feb7ffff]
[    0.604296] PCI: 0000:00:1f.3 reg 20 io port: [eda0, edbf]
[    0.604347] PCI: 0000:00:1f.5 reg 10 io port: [ee00, eeff]
[    0.604355] PCI: 0000:00:1f.5 reg 14 io port: [edc0, edff]
[    0.604363] PCI: 0000:00:1f.5 reg 18 32bit mmio: [feb7fa00, feb7fbff]
[    0.604372] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [feb7f900, feb7f9ff]
[    0.604403] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.604409] pci 0000:00:1f.5: PME# disabled
[    0.604465] PCI: 0000:01:06.0 reg 10 32bit mmio: [fb000000, fbffffff]
[    0.604542] PCI: 0000:01:06.1 reg 10 32bit mmio: [fc000000, fcffffff]
[    0.604617] PCI: 0000:01:06.2 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.604701] PCI: 0000:01:09.0 reg 10 32bit mmio: [fe9fe000, fe9fffff]
[    0.604734] PCI: 0000:01:09.0 reg 30 32bit mmio: [fea00000, fea03fff]
[    0.604750] pci 0000:01:09.0: supports D1
[    0.604753] pci 0000:01:09.0: supports D2
[    0.604756] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.604761] pci 0000:01:09.0: PME# disabled
[    0.604793] pci 0000:00:1e.0: transparent bridge
[    0.604802] PCI: bridge 0000:00:1e.0 32bit mmio: [fb000000, feafffff]
[    0.604816] bus 00 -> node 0
[    0.604827] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.605485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.776768] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.777134] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.777498] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.777861] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.778220] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.778582] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.778942] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.779314] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 15)
[    0.779612] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.779671] pnp: PnP ACPI init
[    0.779686] ACPI: bus type pnp registered
[    0.797010] pnp 00:06: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.797017] pnp 00:06: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.797952] pnp: PnP ACPI: found 7 devices
[    0.797956] ACPI: ACPI bus type pnp unregistered
[    0.797964] PnPBIOS: Disabled by ACPI PNP
[    0.798579] PCI: Using ACPI for IRQ routing
[    0.798754] NET: Registered protocol family 8
[    0.798754] NET: Registered protocol family 20
[    0.798754] NetLabel: Initializing
[    0.798754] NetLabel:  domain hash size = 128
[    0.798754] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.798754] NetLabel:  unlabeled traffic allowed by default
[    0.800444] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.800449]    actual entries 65620
[    0.800744] AppArmor: AppArmor Filesystem Enabled
[    0.800773] ACPI: RTC can wake from S4
[    0.800855] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.800861] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[    0.800865] system 00:00: iomem range 0x1000000-0x2f773fff could not be reserved
[    0.800869] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
[    0.800874] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.800878] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.800882] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
[    0.800886] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.800891] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.800907] system 00:06: ioport range 0xc00-0xc7f has been reserved
[    0.836433] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.836437] pci 0000:00:1e.0:   IO window: disabled
[    0.836445] pci 0000:00:1e.0:   MEM window: 0xfb000000-0xfeafffff
[    0.836451] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x000000300fffff
[    0.836474] pci 0000:00:1e.0: setting latency timer to 64
[    0.836480] bus: 00 index 0 io port: [0, ffff]
[    0.836483] bus: 00 index 1 mmio: [0, ffffffff]
[    0.836486] bus: 01 index 0 mmio: [0, 0]
[    0.836489] bus: 01 index 1 mmio: [fb000000, feafffff]
[    0.836492] bus: 01 index 2 mmio: [30000000, 300fffff]
[    0.836495] bus: 01 index 3 io port: [0, ffff]
[    0.836497] bus: 01 index 4 mmio: [0, ffffffff]
[    0.836517] NET: Registered protocol family 2
[    0.836756] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.837307] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.838789] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.839750] TCP: Hash tables configured (established 131072 bind 65536)
[    0.839758] TCP reno registered
[    0.840123] NET: Registered protocol family 1
[    0.840343] checking if image is initramfs... it is
[    1.340086] Switched to high resolution mode on CPU 0
[    1.747948] Freeing initrd memory: 8022k freed
[    1.748309] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    1.748313] Simple Boot Flag at 0x7a set to 0x1
[    1.749088] audit: initializing netlink socket (disabled)
[    1.749121] type=2000 audit(1234640435.748:1): initialized
[    1.755024] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.758376] VFS: Disk quotas dquot_6.5.1
[    1.758526] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.758711] msgmni has been set to 1493
[    1.758929] io scheduler noop registered
[    1.758934] io scheduler anticipatory registered
[    1.758937] io scheduler deadline registered
[    1.758959] io scheduler cfq registered (default)
[    1.758987] pci 0000:00:02.0: Boot video device
[    1.759589] isapnp: Scanning for PnP cards...
[    2.113596] isapnp: No Plug & Play device found
[    2.181138] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.185025] brd: module loaded
[    2.185143] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.185423] PNP: No PS/2 controller found. Probing ports directly.
[    2.188484] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.188493] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.189102] mice: PS/2 mouse device common for all mice
[    2.189349] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.189377] rtc0: alarms up to one day
[    2.189575] EISA: Probing bus 0 at eisa.0
[    2.189616] EISA: Detected 0 cards.
[    2.189622] cpuidle: using governor ladder
[    2.189625] cpuidle: using governor menu
[    2.190400] TCP cubic registered
[    2.190448] Using IPI No-Shortcut mode
[    2.190839] registered taskstats version 1
[    2.191019]   Magic number: 13:175:698
[    2.191203] rtc_cmos 00:05: setting system clock to 2009-02-14 19:40:37 UTC (1234640437)
[    2.191208] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.191211] EDD information not available.
[    2.191941] Freeing unused kernel memory: 424k freed
[    2.192047] Write protecting the kernel text: 2580k
[    2.192090] Write protecting the kernel read-only data: 940k
[    2.500058] fuse init (API version 7.9)
[    2.776027] processor ACPI0007:00: registered as cooling_device0
[    3.436196] usbcore: registered new interface driver usbfs
[    3.436238] usbcore: registered new interface driver hub
[    3.450964] No dock devices found.
[    3.488118] usbcore: registered new device driver usb
[    3.532120] SCSI subsystem initialized
[    3.546944] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.547096] USB Universal Host Controller Interface driver v3.0
[    3.547159] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.547171] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.547176] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.547256] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.547295] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    3.547558] usb usb1: configuration #1 chosen from 1 choice
[    3.547600] hub 1-0:1.0: USB hub found
[    3.547615] hub 1-0:1.0: 2 ports detected
[    3.552776] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    3.620185] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
[    3.620223] b44.c:v2.0
[    3.640541] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0b:db:be:64:37
[    3.648484] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.648505] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.648511] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.648556] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.648597] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    3.648763] usb usb2: configuration #1 chosen from 1 choice
[    3.648806] hub 2-0:1.0: USB hub found
[    3.648822] hub 2-0:1.0: 2 ports detected
[    3.655174] libata version 3.00 loaded.
[    3.856461] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.856476] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.856481] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.856524] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.856566] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    3.856730] usb usb3: configuration #1 chosen from 1 choice
[    3.856788] hub 3-0:1.0: USB hub found
[    3.856807] hub 3-0:1.0: 2 ports detected
[    3.968058] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.064496] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    4.064517] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.064522] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.064576] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    4.068486] ehci_hcd 0000:00:1d.7: debug port 1
[    4.068495] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    4.068514] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
[    4.096047] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.096346] usb usb4: configuration #1 chosen from 1 choice
[    4.096393] hub 4-0:1.0: USB hub found
[    4.096411] hub 4-0:1.0: 6 ports detected
[    4.306051] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.306114] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    4.306134] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    4.311586] ata_piix 0000:00:1f.1: version 2.12
[    4.311605] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.311673] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.312286] scsi0 : ata_piix
[    4.312459] scsi1 : ata_piix
[    4.312519] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    4.312523] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    4.476611] ata1.00: ATA-7: Maxtor 2F040L0, VAM51JJ0, max UDMA/133
[    4.476618] ata1.00: 80293248 sectors, multi 8: LBA 
[    4.476640] ata1.00: limited to UDMA/33 due to 40-wire cable
[    4.492357] usb 2-1: device not accepting address 2, error -71
[    4.492484] ata1.00: configured for UDMA/33
[    4.548123] hub 2-0:1.0: unable to enumerate USB device on port 1
[    4.664487] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-248F, R602, max UDMA/33
[    4.664531] ata2.01: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-106S 0122, E1.22, max UDMA/66
[    4.664557] ata2.01: limited to UDMA/33 due to 40-wire cable
[    4.680354] ata2.00: configured for UDMA/33
[    4.696304] ata2.01: configured for UDMA/33
[    4.696485] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 2F040L0   VAM5 PQ: 0 ANSI: 5
[    4.698236] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-248F  R602 PQ: 0 ANSI: 5
[    4.699753] scsi 1:0:1:0: CD-ROM            PIONEER  DVD-ROM DVD-106  1.22 PQ: 0 ANSI: 5
[    4.720430] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.720490] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.720547] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    4.763729] Driver 'sd' needs updating - please use bus_type methods
[    4.767139] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors (41110 MB)
[    4.767169] sd 0:0:0:0: [sda] Write Protect is off
[    4.767173] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.767218] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.767337] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors (41110 MB)
[    4.767362] sd 0:0:0:0: [sda] Write Protect is off
[    4.767366] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.767408] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.767414]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.795699]  sda1 sda2 < sda5 >
[    4.829900] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.836627] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.836636] Uniform CD-ROM driver Revision: 3.20
[    4.836787] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.839831] sr1: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[    4.840064] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    5.032040] usb 4-6: new high speed USB device using ehci_hcd and address 4
[    5.171773] usb 4-6: configuration #1 chosen from 1 choice
[    5.412018] usb 2-1: new low speed USB device using uhci_hcd and address 4
[    5.591578] usb 2-1: configuration #1 chosen from 1 choice
[    5.832017] usb 2-2: new low speed USB device using uhci_hcd and address 5
[    6.007501] usb 2-2: configuration #1 chosen from 1 choice
[    6.010802] usbcore: registered new interface driver libusual
[    6.011256] usbcore: registered new interface driver hiddev
[    6.022069] Initializing USB Mass Storage driver...
[    6.023191] scsi2 : SCSI emulation for USB Mass Storage devices
[    6.023331] usb-storage: device found at 4
[    6.023334] usb-storage: waiting for device to settle before scanning
[    6.028829] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input1
[    6.040306] input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1d.1-1
[    6.053736] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input2
[    6.054356] input,hidraw1: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.1-2
[    6.054413] usbcore: registered new interface driver usb-storage
[    6.054420] USB Mass Storage support registered.
[    6.054628] usbcore: registered new interface driver usbhid
[    6.054634] usbhid: v2.6:USB HID core driver
[    6.158331] PM: Starting manual resume from disk
[    6.158338] PM: Resume from partition 8:5
[    6.158340] PM: Checking hibernation image.
[    6.158802] PM: Resume from disk failed.
[    6.251750] kjournald starting.  Commit interval 5 seconds
[    6.251775] EXT3-fs: mounted filesystem with ordered data mode.
[   10.601924] udevd version 124 started
[   11.020149] usb-storage: device scan complete
[   11.021144] scsi 2:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
[   11.022613] sd 2:0:0:0: [sdb] 3948543 512-byte hardware sectors (2022 MB)
[   11.023360] sd 2:0:0:0: [sdb] Write Protect is off
[   11.023365] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   11.023369] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   11.026725] sd 2:0:0:0: [sdb] 3948543 512-byte hardware sectors (2022 MB)
[   11.027480] sd 2:0:0:0: [sdb] Write Protect is off
[   11.027487] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   11.027490] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   11.027500]  sdb: sdb1
[   11.216300] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   11.216517] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   12.064391] iTCO_vendor_support: vendor-support=0
[   12.199160] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   12.207171] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)
[   12.207383] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.399291] Linux agpgart interface v0.103
[   12.481047] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   12.481199] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[   12.560350] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   12.568027] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   12.575075] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.746928] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.811069] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.877506] intel_rng: FWH not detected
[   13.036118] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   13.064292] ACPI: Power Button (FF) [PWRF]
[   13.064389] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   13.092374] ACPI: Power Button (CM) [VBTN]
[   13.756377] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.756409] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.176025] intel8x0_measure_ac97_clock: measured 54852 usecs
[   14.176031] intel8x0: clocking to 48000
[   14.281706] Linux video capture interface: v2.00
[   14.584293] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   14.585023] cx88[0]: subsystem: 1002:a101, board: ATI HDTV Wonder [card=34,autodetected]
[   14.585028] cx88[0]: TV tuner type 68, Radio tuner type -1
[   14.610215] cx2388x alsa driver version 0.0.6 loaded
[   14.648266] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   15.228881] cx88[0]/2: cx2388x 8802 Driver Manager
[   15.228910] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.228923] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 18, latency: 64, mmio: 0xfd000000
[   15.248101] cx88_audio 0000:01:06.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.248146] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   15.249047] cx8800 0000:01:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.249058] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 18, latency: 64, mmio: 0xfb000000
[   15.249185] cx88[0]/0: registered device video0 [v4l2]
[   15.249266] cx88[0]/0: registered device vbi0
[   15.447821] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   15.447827] cx88/2: registering cx8802 driver, type: dvb access: shared
[   15.447832] cx88[0]/2: subsystem: 1002:a101, board: ATI HDTV Wonder [card=34]
[   15.447837] cx88[0]/2: cx2388x based DVB/ATSC card
[   15.695791] nxt200x: NXT2004 Detected
[   15.875359] tuner-simple 0-0061: creating new instance
[   15.875366] tuner-simple 0-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   15.875374] DVB: registering new adapter (cx88[0])
[   15.875380] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   20.948734] end_request: I/O error, dev sr0, sector 1232504
[   20.948746] Buffer I/O error on device sr0, logical block 308126
[   21.128260] end_request: I/O error, dev sr0, sector 1232504
[   21.128266] Buffer I/O error on device sr0, logical block 308126
[   21.351728] end_request: I/O error, dev sr0, sector 1232504
[   21.351735] Buffer I/O error on device sr0, logical block 308126
[   21.543606] end_request: I/O error, dev sr0, sector 1232504
[   21.543612] Buffer I/O error on device sr0, logical block 308126
[   21.742152] end_request: I/O error, dev sr0, sector 1232504
[   21.742158] Buffer I/O error on device sr0, logical block 308126
[   21.993583] end_request: I/O error, dev sr0, sector 1232504
[   21.993589] Buffer I/O error on device sr0, logical block 308126
[   22.174865] end_request: I/O error, dev sr0, sector 1232504
[   22.174871] Buffer I/O error on device sr0, logical block 308126
[   22.534979] end_request: I/O error, dev sr0, sector 1232504
[   22.534986] Buffer I/O error on device sr0, logical block 308126
[   22.706498] end_request: I/O error, dev sr0, sector 1232504
[   22.706504] Buffer I/O error on device sr0, logical block 308126
[   23.816951] loop: module loaded
[   23.921866] lp: driver loaded but no devices found
[   24.460259] Adding 1694816k swap on /dev/sda5.  Priority:-1 extents:1 across:1694816k
[   25.345776] EXT3 FS on sda1, internal journal
[   27.702775] type=1505 audit(1234640463.047:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3922
[   27.703267] type=1505 audit(1234640463.047:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3922
[   27.816767] type=1505 audit(1234640463.163:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=3926
[   28.244785] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.273846] ACPI: WMI: Mapper loaded
[   32.964212] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   33.933858] NET: Registered protocol family 10
[   33.936867] lo: Disabled Privacy Extensions
[   37.609281] ppdev: user-space parallel port driver
[   49.884943] Bluetooth: Core ver 2.13
[   49.887531] NET: Registered protocol family 31
[   49.887538] Bluetooth: HCI device and connection manager initialized
[   49.887544] Bluetooth: HCI socket layer initialized
[   50.024929] Bluetooth: L2CAP ver 2.11
[   50.024938] Bluetooth: L2CAP socket layer initialized
[   50.170339] Bluetooth: RFCOMM socket layer initialized
[   50.170729] Bluetooth: RFCOMM TTY layer initialized
[   50.170737] Bluetooth: RFCOMM ver 1.10
[   50.206544] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   50.206552] Bluetooth: BNEP filters: protocol multicast
[   50.494769] Bridge firewalling registered
[   50.959306] Bluetooth: SCO (Voice Link) ver 0.6
[   50.959314] Bluetooth: SCO socket layer initialized
[   52.091196] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   52.091209] firmware: requesting dvb-fe-nxt2004.fw
[   52.160183] nxt2004: Waiting for firmware upload(2)...
[   53.672694] nxt2004: Firmware upload complete
[   55.052090] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.961005] [drm] Initialized drm 1.1.0 20060810
[   57.008521] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   57.008535] pci 0000:00:02.0: setting latency timer to 64
[   57.010915] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   57.816171] b44: eth0: Link is up at 100 Mbps, full duplex.
[   57.816179] b44: eth0: Flow control is off for TX and off for RX.
[   57.817048] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   58.466561] NET: Registered protocol family 17
[   68.412018] eth0: no IPv6 routers present
[   81.639658] ecryptfs_parse_options: eCryptfs: unrecognized option 'rw'
[   81.640153] ecryptfs_parse_options: eCryptfs: unrecognized option 'user=andrew'
[   81.860406] padlock: VIA PadLock not detected.

---

