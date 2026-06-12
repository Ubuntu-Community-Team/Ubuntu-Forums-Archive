---
title: "Tried to remove Pulseaudio... no sound now :-/"
date: 2011-07-31
forum: Multimedia Software
---

### Post by tylersontag on 2011-07-31
To try to fix my sound after the new wine patch broke sound for windows emulators and it was recommended to remove pulseaudio as a solution.

It didn't work, and now i don't have any sound at all :-/

The biggest thing is the "Sound" node in the System>Preferences menu no longer exists, and if i try to run gnome-volume-control it brings up a different looking menu... its just a sound mixer, no option to select sound card or profile, heres a picture

[http://ubuntuone.com/p/17W5/](http://ubuntuone.com/p/17W5/)

Heres my sound info from that alsa bash that queries up all my sound settings

[http://www.alsa-project.org/db/?f=81c2c1cbb24a3f079424a6a3759ea6add9abefdf](http://www.alsa-project.org/db/?f=81c2c1cbb24a3f079424a6a3759ea6add9abefdf)

So far i've tried removing all sound packages in ubuntu with purge and reinstalling them but im not getting anywhere.  Anyone have any suggestions?

---

### Post by fdrake on 2011-07-31
run this.
```
lspci -vvv | nl | grep Audio
```
get the line number (on the left end). now run this other command.
```
lspci -vvv | nl | less
```
go to that line and copy all the audio entry in here.


also post here the output of:
```
dmesg
```

---------------------------------------------
try also to reinstall pulse audio

```
sudo apt-get install pulseaudio 
```
if there is a problem with the install copy and paste i  here.

---

### Post by tylersontag on 2011-07-31
```
   190  03:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 04)
   191          Subsystem: Creative Labs Device 0042
   192          Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
   193          Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
   194          Latency: 0, Cache Line Size: 32 bytes
   195          Interrupt: pin A routed to IRQ 17
   196          Region 0: Memory at fe8f0000 (64-bit, non-prefetchable) [size=64K]
   197          Region 2: Memory at fe600000 (64-bit, non-prefetchable) [size=2M]
   198          Region 4: Memory at fd000000 (64-bit, non-prefetchable) [size=16M]
   199          Capabilities: <access denied>
   200          Kernel driver in use: SB-XFi
   201          Kernel modules: snd-ctxfi

```

I notice that the capabilities weren't visable so i re-ran the lspci as sudo:

```

   361  03:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 04)
   362          Subsystem: Creative Labs Device 0042
   363          Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
   364          Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
   365          Latency: 0, Cache Line Size: 32 bytes
   366          Interrupt: pin A routed to IRQ 17
   367          Region 0: Memory at fe8f0000 (64-bit, non-prefetchable) [size=64K]
   368          Region 2: Memory at fe600000 (64-bit, non-prefetchable) [size=2M]
   369          Region 4: Memory at fd000000 (64-bit, non-prefetchable) [size=16M]
   370          Capabilities: [40] Power Management version 3
   371                  Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
   372                  Status: D0 PME-Enable- DSel=0 DScale=0 PME-
   373          Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
   374                  Address: 0000000000000000  Data: 0000
   375          Capabilities: [58] Express (v2) Endpoint, MSI 00
   376                  DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
   377                          ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
   378                  DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
   379                          RlxdOrd+ ExtTag- PhantFunc- AuxPwr+ NoSnoop+
   380                          MaxPayload 128 bytes, MaxReadReq 512 bytes
   381                  DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
   382                  LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <64ns, L1 <1us
   383                          ClockPM- Suprise- LLActRep- BwNot-
   384                  LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
   385                          ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
   386                  LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
   387          Capabilities: [100] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
   388          Capabilities: [300] Advanced Error Reporting <?>
   389          Kernel driver in use: SB-XFi
   390          Kernel modules: snd-ctxfi

```

Don't know if those capabilities are needed...

Heres dmesg, having RAID problems concurrently so they're cluttering up the log:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-33-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #71-Ubuntu SMP Wed Jul 20 17:30:40 UTC 2011 (Ubuntu 2.6.32-33.71-generic 2.6.32.41+drm33.18)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffa0000 - 00000000bffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffae000 - 00000000bfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbffa0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bffa0000 (usable)
[    0.000000]  modified: 00000000bffa0000 - 00000000bffae000 (ACPI data)
[    0.000000]  modified: 00000000bffae000 - 00000000bfff0000 (ACPI NVS)
[    0.000000]  modified: 00000000bfff0000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37329000 - 37fefa81
[    0.000000] Allocated new RAMDISK: 008e5000 - 015aba81
[    0.000000] Move RAMDISK from 0000000037329000 - 0000000037fefa80 to 008e5000 - 015aba80
[    0.000000] ACPI: RSDP 000f9430 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT bffa0000 00040 (v01 052609 RSDT1558 20090526 MSFT 00000097)
[    0.000000] ACPI: FACP bffa0200 00084 (v01 052609 FACP1558 20090526 MSFT 00000097)
[    0.000000] ACPI: DSDT bffa0440 05BAE (v01  1AAAA 1AAAA000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS bffae000 00040
[    0.000000] ACPI: APIC bffa0390 0006C (v01 052609 APIC1558 20090526 MSFT 00000097)
[    0.000000] ACPI: MCFG bffa0400 0003C (v01 052609 OEMMCFG  20090526 MSFT 00000097)
[    0.000000] ACPI: OEMB bffae040 00072 (v01 052609 OEMB1558 20090526 MSFT 00000097)
[    0.000000] ACPI: HPET bffa8440 00038 (v01 052609 OEMHPET  20090526 MSFT 00000097)
[    0.000000] ACPI: GSCI bffae0c0 02024 (v01 052609 GMCHSCI  20090526 MSFT 00000097)
[    0.000000] ACPI: SSDT bffb05f0 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2183MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e0ef8]    TEXT DATA BSS ==> [0000100000 - 00008e0ef8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008e1000 - 00008e40d7]              BRK ==> [00008e1000 - 00008e40d7]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008e5000 - 00015aba81]      NEW RAMDISK ==> [00008e5000 - 00015aba81]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bffa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bffa0
[    0.000000] On node 0 totalpages: 786223
[    0.000000] free_area_init_node: node 0, pgdat c079a7c0, node_mem_map c15ad200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4368 pages used for memmap
[    0.000000]   HighMem zone: 554642 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c3000000 s36312 r0 d21032 u1048576
[    0.000000] pcpu-alloc: s36312 r0 d21032 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 780079
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=b073bd6f-2697-4a89-8747-23bf986868b2 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 15726400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bffa0)
[    0.000000] Memory: 3081468k/3145344k available (4675k kernel code, 62216k reserved, 2127k data, 668k init, 2236040k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084c000   ( 668 kB)
[    0.000000]       .data : 0xc0590dc7 - 0xc07a4d88   (2127 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590dc7   (4675 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2500.367 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5000.73 BogoMIPS (lpj=10001468)
[    0.004018] Security Framework initialized
[    0.004037] AppArmor: AppArmor initialized
[    0.004042] Mount-cache hash table entries: 512
[    0.004160] Initializing cgroup subsys ns
[    0.004164] Initializing cgroup subsys cpuacct
[    0.004168] Initializing cgroup subsys memory
[    0.004173] Initializing cgroup subsys devices
[    0.004175] Initializing cgroup subsys freezer
[    0.004177] Initializing cgroup subsys net_cls
[    0.004196] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004198] CPU: L2 cache: 2048K
[    0.004200] CPU: Physical Processor ID: 0
[    0.004202] CPU: Processor Core ID: 0
[    0.004205] mce: CPU supports 6 MCE banks
[    0.004213] CPU0: Thermal monitoring enabled (TM2)
[    0.004216] using mwait in idle threads.
[    0.004222] Performance Events: Core2 events, Intel PMU driver.
[    0.004229] ... version:                2
[    0.004231] ... bit width:              40
[    0.004232] ... generic registers:      2
[    0.004234] ... value mask:             000000ffffffffff
[    0.004235] ... max period:             000000007fffffff
[    0.004237] ... fixed-purpose events:   3
[    0.004238] ... event mask:             0000000700000003
[    0.004244] Checking 'hlt' instruction... OK.
[    0.022514] ACPI: Core revision 20090903
[    0.032007] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032011] ftrace: allocating 21725 entries in 43 pages
[    0.036053] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036361] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078444] CPU0: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 0a
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 2048K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.164082] CPU1: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 0a
[    0.164089] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168021] Brought up 2 CPUs
[    0.168023] Total of 2 processors activated (9606.51 BogoMIPS).
[    0.168922] CPU0 attaching sched-domain:
[    0.168926]  domain 0: span 0-1 level MC
[    0.168928]   groups: 0 1
[    0.168933] CPU1 attaching sched-domain:
[    0.168934]  domain 0: span 0-1 level MC
[    0.168936]   groups: 1 0
[    0.168992] devtmpfs: initialized
[    0.168992] regulator: core version 0.5
[    0.168992] Time: 22:14:30  Date: 07/31/11
[    0.168992] NET: Registered protocol family 16
[    0.168992] Trying to unpack rootfs image as initramfs...
[    0.168992] EISA bus registered
[    0.168992] ACPI: bus type pci registered
[    0.168992] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.168992] PCI: Not using MMCONFIG.
[    0.168992] PCI: Using configuration type 1 for base access
[    0.172084] bio: create slab <bio-0> at 0
[    0.172796] ACPI: EC: Look up EC in DSDT
[    0.176489] ACPI: Executed 1 blocks of module-level executable AML code
[    0.180477] ACPI: Interpreter enabled
[    0.180480] ACPI: (supports S0 S3 S4 S5)
[    0.180499] ACPI: Using IOAPIC for interrupt routing
[    0.180545] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.185757] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.185760] PCI: Using MMCONFIG for extended config space
[    0.193514] ACPI Warning: Incorrect checksum in table [OEMB] - 11, should be 0C (20090903/tbutils-314)
[    0.194360] ACPI: No dock devices found.
[    0.194623] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.194726] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.194729] pci 0000:00:01.0: PME# disabled
[    0.194791] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfbefc000-0xfbefffff]
[    0.194830] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.194834] pci 0000:00:1b.0: PME# disabled
[    0.194893] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.194896] pci 0000:00:1c.0: PME# disabled
[    0.194956] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.194960] pci 0000:00:1c.1: PME# disabled
[    0.195024] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.195027] pci 0000:00:1c.2: PME# disabled
[    0.195072] pci 0000:00:1d.0: reg 20 io port: [0xcc00-0xcc1f]
[    0.195118] pci 0000:00:1d.1: reg 20 io port: [0xc880-0xc89f]
[    0.195163] pci 0000:00:1d.2: reg 20 io port: [0xc800-0xc81f]
[    0.195208] pci 0000:00:1d.3: reg 20 io port: [0xc480-0xc49f]
[    0.195261] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfbefbc00-0xfbefbfff]
[    0.195309] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.195313] pci 0000:00:1d.7: PME# disabled
[    0.195432] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.195474] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.195480] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.195486] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.195492] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.195498] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.195537] pci 0000:00:1f.2: reg 10 io port: [0xc400-0xc407]
[    0.195542] pci 0000:00:1f.2: reg 14 io port: [0xc080-0xc083]
[    0.195548] pci 0000:00:1f.2: reg 18 io port: [0xc000-0xc007]
[    0.195554] pci 0000:00:1f.2: reg 1c io port: [0xbc00-0xbc03]
[    0.195559] pci 0000:00:1f.2: reg 20 io port: [0xb880-0xb88f]
[    0.195583] pci 0000:00:1f.2: PME# supported from D3hot
[    0.195586] pci 0000:00:1f.2: PME# disabled
[    0.195629] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.195678] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.195686] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.195695] pci 0000:01:00.0: reg 1c 64bit mmio pref: [0xce000000-0xcfffffff]
[    0.195700] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.195706] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfbf80000-0xfbffffff]
[    0.195759] pci 0000:01:00.1: reg 10 32bit mmio: [0xfbf7c000-0xfbf7ffff]
[    0.195837] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.195840] pci 0000:00:01.0: bridge 32bit mmio: [0xfbf00000-0xfcffffff]
[    0.195845] pci 0000:00:01.0: bridge 64bit mmio pref: [0xce000000-0xdfffffff]
[    0.195944] pci 0000:03:00.0: reg 10 64bit mmio: [0xfe8f0000-0xfe8fffff]
[    0.195959] pci 0000:03:00.0: reg 18 64bit mmio: [0xfe600000-0xfe7fffff]
[    0.195974] pci 0000:03:00.0: reg 20 64bit mmio: [0xfd000000-0xfdffffff]
[    0.196077] pci 0000:00:1c.1: bridge 32bit mmio: [0xfd000000-0xfe8fffff]
[    0.196133] pci 0000:04:00.0: reg 10 64bit mmio: [0xfe9c0000-0xfe9fffff]
[    0.196164] pci 0000:04:00.0: reg 30 32bit mmio pref: [0xfe9a0000-0xfe9bffff]
[    0.196200] pci 0000:04:00.0: PME# supported from D3hot D3cold
[    0.196205] pci 0000:04:00.0: PME# disabled
[    0.196253] pci 0000:00:1c.2: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.196326] pci 0000:05:04.0: reg 10 64bit mmio: [0xfeb00000-0xfebfffff]
[    0.196334] pci 0000:05:04.0: reg 18 io port: [0xe800-0xe8ff]
[    0.196440] pci 0000:00:1e.0: transparent bridge
[    0.196443] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.196447] pci 0000:00:1e.0: bridge 32bit mmio: [0xfea00000-0xfebfffff]
[    0.196470] pci_bus 0000:00: on NUMA node 0
[    0.196474] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.196578] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.196656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.196699] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.196742] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.204828] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.204923] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.205015] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.205107] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.205199] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.205291] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.205384] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.205476] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.205579] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.205583] vgaarb: loaded
[    0.205694] SCSI subsystem initialized
[    0.205773] libata version 3.00 loaded.
[    0.205832] usbcore: registered new interface driver usbfs
[    0.205841] usbcore: registered new interface driver hub
[    0.205862] usbcore: registered new device driver usb
[    0.205967] ACPI: WMI: Mapper loaded
[    0.205969] PCI: Using ACPI for IRQ routing
[    0.206111] NetLabel: Initializing
[    0.206112] NetLabel:  domain hash size = 128
[    0.206114] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.206125] NetLabel:  unlabeled traffic allowed by default
[    0.206150] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.206155] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.206160] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.212157] Switching to clocksource tsc
[    0.213762] AppArmor: AppArmor Filesystem Enabled
[    0.213776] pnp: PnP ACPI init
[    0.213791] ACPI: bus type pnp registered
[    0.218566] pnp: PnP ACPI: found 17 devices
[    0.218568] ACPI: ACPI bus type pnp unregistered
[    0.218572] PnPBIOS: Disabled by ACPI PNP
[    0.218583] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.218586] system 00:01: iomem range 0xfed90000-0xfed93fff has been reserved
[    0.218593] system 00:08: ioport range 0xa00-0xa0f has been reserved
[    0.218595] system 00:08: ioport range 0xa10-0xa1f has been reserved
[    0.218597] system 00:08: ioport range 0xa20-0xa2f has been reserved
[    0.218599] system 00:08: ioport range 0xa30-0xa3f has been reserved
[    0.218604] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.218606] system 00:09: ioport range 0x800-0x87f has been reserved
[    0.218609] system 00:09: ioport range 0x480-0x4bf has been reserved
[    0.218611] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.218614] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.218619] system 00:0c: iomem range 0xffc00000-0xffefffff has been reserved
[    0.218623] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.218626] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.218631] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.218638] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.218641] system 00:10: iomem range 0xc0000-0xcffff could not be reserved
[    0.218643] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.218645] system 00:10: iomem range 0x100000-0xbfffffff could not be reserved
[    0.253350] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.253353] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.253357] pci 0000:00:01.0:   MEM window: 0xfbf00000-0xfcffffff
[    0.253360] pci 0000:00:01.0:   PREFETCH window: 0x000000ce000000-0x000000dfffffff
[    0.253364] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.253367] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.253372] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
[    0.253375] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    0.253381] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.253384] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
[    0.253388] pci 0000:00:1c.1:   MEM window: 0xfd000000-0xfe8fffff
[    0.253392] pci 0000:00:1c.1:   PREFETCH window: 0x000000c0400000-0x000000c05fffff
[    0.253398] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.253401] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff
[    0.253406] pci 0000:00:1c.2:   MEM window: 0xfe900000-0xfe9fffff
[    0.253409] pci 0000:00:1c.2:   PREFETCH window: 0x000000c0600000-0x000000c07fffff
[    0.253415] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.253418] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.253422] pci 0000:00:1e.0:   MEM window: 0xfea00000-0xfebfffff
[    0.253426] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.253445]   alloc irq_desc for 16 on node -1
[    0.253446]   alloc kstat_irqs on node -1
[    0.253453] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.253457] pci 0000:00:01.0: setting latency timer to 64
[    0.253464] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.253468] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.253472] pci 0000:00:1c.0: setting latency timer to 64
[    0.253479] pci 0000:00:1c.1: enabling device (0106 -> 0107)
[    0.253482]   alloc irq_desc for 17 on node -1
[    0.253483]   alloc kstat_irqs on node -1
[    0.253486] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.253490] pci 0000:00:1c.1: setting latency timer to 64
[    0.253497] pci 0000:00:1c.2: enabling device (0106 -> 0107)
[    0.253500]   alloc irq_desc for 18 on node -1
[    0.253501]   alloc kstat_irqs on node -1
[    0.253504] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.253508] pci 0000:00:1c.2: setting latency timer to 64
[    0.253514] pci 0000:00:1e.0: setting latency timer to 64
[    0.253518] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.253520] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.253522] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.253524] pci_bus 0000:01: resource 1 mem: [0xfbf00000-0xfcffffff]
[    0.253526] pci_bus 0000:01: resource 2 pref mem [0xce000000-0xdfffffff]
[    0.253528] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.253531] pci_bus 0000:02: resource 1 mem: [0xc0000000-0xc01fffff]
[    0.253533] pci_bus 0000:02: resource 2 pref mem [0xc0200000-0xc03fffff]
[    0.253535] pci_bus 0000:03: resource 0 io:  [0x2000-0x2fff]
[    0.253537] pci_bus 0000:03: resource 1 mem: [0xfd000000-0xfe8fffff]
[    0.253539] pci_bus 0000:03: resource 2 pref mem [0xc0400000-0xc05fffff]
[    0.253541] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.253543] pci_bus 0000:04: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.253545] pci_bus 0000:04: resource 2 pref mem [0xc0600000-0xc07fffff]
[    0.253548] pci_bus 0000:05: resource 0 io:  [0xe000-0xefff]
[    0.253550] pci_bus 0000:05: resource 1 mem: [0xfea00000-0xfebfffff]
[    0.253552] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.253554] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.253588] NET: Registered protocol family 2
[    0.253680] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.253964] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.254403] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.254639] TCP: Hash tables configured (established 131072 bind 65536)
[    0.254641] TCP reno registered
[    0.254721] NET: Registered protocol family 1
[    0.254835] pci 0000:01:00.0: Boot video device
[    0.255006] cpufreq-nforce2: No nForce2 chipset.
[    0.255029] Scanning for low memory corruption every 60 seconds
[    0.255132] audit: initializing netlink socket (disabled)
[    0.255142] type=2000 audit(1312150469.251:1): initialized
[    0.263276] highmem bounce pool size: 64 pages
[    0.263281] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.264540] VFS: Disk quotas dquot_6.5.2
[    0.264588] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.265062] fuse init (API version 7.13)
[    0.265132] msgmni has been set to 1653
[    0.265306] alg: No test for stdrng (krng)
[    0.265350] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.265353] io scheduler noop registered
[    0.265355] io scheduler anticipatory registered
[    0.265356] io scheduler deadline registered
[    0.265390] io scheduler cfq registered (default)
[    0.265511]   alloc irq_desc for 24 on node -1
[    0.265513]   alloc kstat_irqs on node -1
[    0.265521] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.265527] pcieport 0000:00:01.0: setting latency timer to 64
[    0.265612]   alloc irq_desc for 25 on node -1
[    0.265614]   alloc kstat_irqs on node -1
[    0.265620] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.265628] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.265728]   alloc irq_desc for 26 on node -1
[    0.265729]   alloc kstat_irqs on node -1
[    0.265735] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.265742] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.265840]   alloc irq_desc for 27 on node -1
[    0.265842]   alloc kstat_irqs on node -1
[    0.265848] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.265855] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.265935] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.265951] Firmware did not grant requested _OSC control
[    0.265966] Firmware did not grant requested _OSC control
[    0.265976] Firmware did not grant requested _OSC control
[    0.265999] Firmware did not grant requested _OSC control
[    0.266009] Firmware did not grant requested _OSC control
[    0.266019] Firmware did not grant requested _OSC control
[    0.266030] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.266113] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.266122] ACPI: Power Button [PWRB]
[    0.266163] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.266166] ACPI: Power Button [PWRF]
[    0.266738] ACPI: SSDT bffb00f0 00277 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.266984] processor LNXCPU:00: registered as cooling_device0
[    0.267331] ACPI: SSDT bffb0370 00277 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.267575] processor LNXCPU:01: registered as cooling_device1
[    0.272346] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.272436] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.272841] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.273702] brd: module loaded
[    0.274078] loop: module loaded
[    0.274148] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.274228] ata_piix 0000:00:1f.1: version 2.13
[    0.274240] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.274275] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.274349] scsi0 : ata_piix
[    0.274408] scsi1 : ata_piix
[    0.275381] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.275384] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.275402]   alloc irq_desc for 19 on node -1
[    0.275404]   alloc kstat_irqs on node -1
[    0.275409] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.275413] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.275442] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.275499] scsi2 : ata_piix
[    0.275541] scsi3 : ata_piix
[    0.275600] isapnp: Scanning for PnP cards...
[    0.276657] ata3: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xb880 irq 19
[    0.276659] ata4: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb888 irq 19
[    0.276929] Fixed MDIO Bus: probed
[    0.276958] PPP generic driver version 2.4.2
[    0.276993] tun: Universal TUN/TAP device driver, 1.6
[    0.276994] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.277062] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.277078]   alloc irq_desc for 23 on node -1
[    0.277079]   alloc kstat_irqs on node -1
[    0.277083] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.277096] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.277099] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.277127] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.277147] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.277156] ehci_hcd 0000:00:1d.7: debug port 1
[    0.281044] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.281065] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbefbc00
[    0.328769] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.328890] usb usb1: configuration #1 chosen from 1 choice
[    0.328921] hub 1-0:1.0: USB hub found
[    0.328929] hub 1-0:1.0: 8 ports detected
[    0.328992] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.329008] uhci_hcd: USB Universal Host Controller Interface driver
[    0.329048] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.329056] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.329059] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.329092] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.329116] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000cc00
[    0.329184] usb usb2: configuration #1 chosen from 1 choice
[    0.329204] hub 2-0:1.0: USB hub found
[    0.329209] hub 2-0:1.0: 2 ports detected
[    0.329246] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.329252] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.329255] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.329282] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.329303] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c880
[    0.329371] usb usb3: configuration #1 chosen from 1 choice
[    0.329393] hub 3-0:1.0: USB hub found
[    0.329399] hub 3-0:1.0: 2 ports detected
[    0.329433] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.329437] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.329440] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.329463] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.329493] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c800
[    0.329563] usb usb4: configuration #1 chosen from 1 choice
[    0.329585] hub 4-0:1.0: USB hub found
[    0.329590] hub 4-0:1.0: 2 ports detected
[    0.329624] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.329629] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.329631] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.329656] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.329682] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c480
[    0.329757] usb usb5: configuration #1 chosen from 1 choice
[    0.329776] hub 5-0:1.0: USB hub found
[    0.329785] hub 5-0:1.0: 2 ports detected
[    0.329864] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.329866] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.329984] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.330054] mice: PS/2 mouse device common for all mice
[    0.330129] rtc_cmos 00:03: RTC can wake from S4
[    0.330163] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.330184] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.330272] device-mapper: uevent: version 1.0.3
[    0.373888] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.417445] device-mapper: multipath: version 1.1.0 loaded
[    0.417448] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.427749] EISA: Probing bus 0 at eisa.0
[    0.427755] Cannot allocate resource for EISA slot 1
[    0.427757] Cannot allocate resource for EISA slot 2
[    0.427759] Cannot allocate resource for EISA slot 3
[    0.427772] EISA: Detected 0 cards.
[    0.434449] Freeing initrd memory: 13082k freed
[    0.471946] cpuidle: using governor ladder
[    0.471949] cpuidle: using governor menu
[    0.472363] TCP cubic registered
[    0.472502] NET: Registered protocol family 10
[    0.473176] NET: Registered protocol family 17
[    0.483042] Using IPI No-Shortcut mode
[    0.483146] PM: Resume from disk failed.
[    0.483158] registered taskstats version 1
[    0.483508]   Magic number: 3:838:250
[    0.483888] rtc_cmos 00:03: setting system clock to 2011-07-31 22:14:30 UTC (1312150470)
[    0.483891] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.483892] EDD information not available.
[    0.484385] ata4.01: ATA-8: WDC WD15EADS-00P8B0, 01.00A01, max UDMA/133
[    0.484388] ata4.01: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.487813] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.492414] ata4.01: configured for UDMA/133
[    0.526225] ata3.01: ATAPI: HL-DT-ST BD-RE  WH10LS30, 1.00, max UDMA/133
[    0.539713] ata3.01: configured for UDMA/133
[    0.646163] isapnp: No Plug & Play device found
[    0.655000] scsi 2:0:1:0: CD-ROM            HL-DT-ST BD-RE  WH10LS30  1.00 PQ: 0 ANSI: 5
[    0.683036] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.683041] Uniform CD-ROM driver Revision: 3.20
[    0.683176] sr 2:0:1:0: Attached scsi CD-ROM sr0
[    0.683237] sr 2:0:1:0: Attached scsi generic sg0 type 5
[    0.683332] scsi 3:0:1:0: Direct-Access     ATA      WDC WD15EADS-00P 01.0 PQ: 0 ANSI: 5
[    0.683416] sd 3:0:1:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    0.683430] sd 3:0:1:0: Attached scsi generic sg1 type 0
[    0.683454] sd 3:0:1:0: [sda] Write Protect is off
[    0.683456] sd 3:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    0.683476] sd 3:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.683594]  sda: sda1 sda2 sda3 < sda5 >
[    0.724923] sd 3:0:1:0: [sda] Attached SCSI disk
[    0.724935] Freeing unused kernel memory: 668k freed
[    0.725298] Write protecting the kernel text: 4676k
[    0.725331] Write protecting the kernel read-only data: 1848k
[    0.739267] udev: starting version 151
[    0.796859] Linux agpgart interface v0.103
[    0.800808] vga16fb: initializing
[    0.800812] vga16fb: mapped to 0xc00a0000
[    0.800871] fb0: VGA16 VGA frame buffer device
[    0.829751] sata_mv 0000:05:04.0: version 1.28
[    0.829798] sata_mv 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.829889] sata_mv 0000:05:04.0: Gen-IIE 32 slots 4 ports SCSI mode IRQ via INTx
[    0.833149] scsi4 : sata_mv
[    0.833263] scsi5 : sata_mv
[    0.833353] scsi6 : sata_mv
[    0.833433] scsi7 : sata_mv
[    0.833467] ata5: SATA max UDMA/133 mmio m1048576@0xfeb00000 port 0xfeb22000 irq 16
[    0.833471] ata6: SATA max UDMA/133 mmio m1048576@0xfeb00000 port 0xfeb24000 irq 16
[    0.833474] ata7: SATA max UDMA/133 mmio m1048576@0xfeb00000 port 0xfeb26000 irq 16
[    0.833477] ata8: SATA max UDMA/133 mmio m1048576@0xfeb00000 port 0xfeb28000 irq 16
[    0.907457] usb 1-6: new high speed USB device using ehci_hcd and address 5
[    1.012954] Console: switching to colour frame buffer device 80x30
[    1.038523] usb 1-6: configuration #1 chosen from 1 choice
[    1.044565] Initializing USB Mass Storage driver...
[    1.044649] scsi8 : SCSI emulation for USB Mass Storage devices
[    1.044728] usbcore: registered new interface driver usb-storage
[    1.044730] USB Mass Storage support registered.
[    1.044735] usb-storage: device found at 5
[    1.044736] usb-storage: waiting for device to settle before scanning
[    1.276016] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.352044] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.352861] ata5.15: Port Multiplier 1.1, 0x1095:0x3726 r23, 6 ports, feat 0x1/0x9
[    1.353572] ata5.00: hard resetting link
[    1.528135] usb 2-1: configuration #1 chosen from 1 choice
[    1.768016] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.768614] ata5.00: link resume succeeded after 1 retries
[    1.876808] ata5.01: hard resetting link
[    1.942262] usb 3-1: configuration #1 chosen from 1 choice
[    2.184015] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    2.196813] ata5.02: hard resetting link
[    2.362221] usb 3-2: configuration #1 chosen from 1 choice
[    2.369690] usbcore: registered new interface driver hiddev
[    2.387422] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4
[    2.387498] generic-usb 0003:046D:C50E.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.1-1/input0
[    2.399353] input: HP HP Wireless Keyboard Kit as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[    2.399400] generic-usb 0003:03F0:140C.0002: input,hidraw1: USB HID v1.11 Keyboard [HP HP Wireless Keyboard Kit] on usb-0000:00:1d.1-2/input0
[    2.437062] input: HP HP Wireless Keyboard Kit as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input6
[    2.437163] generic-usb 0003:03F0:140C.0003: input,hiddev96,hidraw2: USB HID v1.11 Mouse [HP HP Wireless Keyboard Kit] on usb-0000:00:1d.1-2/input1
[    2.437180] usbcore: registered new interface driver usbhid
[    2.437182] usbhid: v2.6:USB HID core driver
[    2.517208] ata5.03: hard resetting link
[    2.836710] ata5.04: hard resetting link
[    3.156706] ata5.05: hard resetting link
[    3.492064] ata5.02: ATA-8: ST32000542AS, CC34, max UDMA/133
[    3.492069] ata5.02: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.516095] ata5.02: configured for UDMA/133
[    3.532061] ata5.03: ATA-8: ST32000542AS, CC34, max UDMA/133
[    3.532067] ata5.03: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.556092] ata5.03: configured for UDMA/133
[    3.572559] ata5.04: ATA-8: ST32000542AS, CC34, max UDMA/133
[    3.572564] ata5.04: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.596094] ata5.04: configured for UDMA/133
[    3.596300] ata5: EH complete
[    3.596398] scsi 4:2:0:0: Direct-Access     ATA      ST32000542AS     CC34 PQ: 0 ANSI: 5
[    3.596534] sd 4:2:0:0: Attached scsi generic sg2 type 0
[    3.596605] sd 4:2:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.596626] scsi 4:3:0:0: Direct-Access     ATA      ST32000542AS     CC34 PQ: 0 ANSI: 5
[    3.596641] sd 4:2:0:0: [sdb] Write Protect is off
[    3.596644] sd 4:2:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.596662] sd 4:2:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.596731] sd 4:3:0:0: Attached scsi generic sg3 type 0
[    3.596791]  sdb:
[    3.596852] sd 4:3:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.596885] sd 4:3:0:0: [sdc] Write Protect is off
[    3.596887] sd 4:3:0:0: [sdc] Mode Sense: 00 3a 00 00
[    3.596906] sd 4:3:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.596913] scsi 4:4:0:0: Direct-Access     ATA      ST32000542AS     CC34 PQ: 0 ANSI: 5
[    3.597012] sd 4:4:0:0: Attached scsi generic sg4 type 0
[    3.597014]  sdc:
[    3.597054] sd 4:4:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.597087] sd 4:4:0:0: [sdd] Write Protect is off
[    3.597089] sd 4:4:0:0: [sdd] Mode Sense: 00 3a 00 00
[    3.597106] sd 4:4:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.597198]  sdd: sdc1
[    3.603998] sd 4:3:0:0: [sdc] Attached SCSI disk
[    3.607292]  sdd1
[    3.607532] sd 4:4:0:0: [sdd] Attached SCSI disk
[    3.617545]  sdb1
[    3.617785] sd 4:2:0:0: [sdb] Attached SCSI disk
[    3.916035] ata6: SATA link down (SStatus 0 SControl 300)
[    4.236537] ata7: SATA link down (SStatus 0 SControl 300)
[    4.556035] ata8: SATA link down (SStatus 0 SControl 300)
[    5.018811] md: linear personality registered for level -1
[    5.020872] md: multipath personality registered for level -4
[    5.022727] md: raid0 personality registered for level 0
[    5.025511] md: raid1 personality registered for level 1
[    5.027349] async_tx: api initialized (async)
[    5.028039] xor: automatically using best checksumming function: pIII_sse
[    5.047997]    pIII_sse  :  9549.000 MB/sec
[    5.047999] xor: using function: pIII_sse (9549.000 MB/sec)
[    5.116006] raid6: int32x1    954 MB/s
[    5.184055] raid6: int32x2    878 MB/s
[    5.252058] raid6: int32x4    740 MB/s
[    5.320050] raid6: int32x8    612 MB/s
[    5.388006] raid6: mmxx1     3096 MB/s
[    5.456001] raid6: mmxx2     3581 MB/s
[    5.524024] raid6: sse1x1    2111 MB/s
[    5.592000] raid6: sse1x2    2662 MB/s
[    5.660004] raid6: sse2x1    3808 MB/s
[    5.728009] raid6: sse2x2    4356 MB/s
[    5.728011] raid6: using algorithm sse2x2 (4356 MB/s)
[    5.732473] md: raid6 personality registered for level 6
[    5.732475] md: raid5 personality registered for level 5
[    5.732477] md: raid4 personality registered for level 4
[    5.738212] md: raid10 personality registered for level 10
[    5.768408] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    5.768413] EXT4-fs (sda1): write access will be enabled during recovery
[    6.044250] usb-storage: device scan complete
[    6.044733] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    6.045262] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    6.045759] scsi 8:0:0:2: Direct-Access     Generic  USB xD/SM Reader 1.02 PQ: 0 ANSI: 0
[    6.046383] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    6.046819] sd 8:0:0:0: Attached scsi generic sg5 type 0
[    6.047136] sd 8:0:0:1: Attached scsi generic sg6 type 0
[    6.047830] sd 8:0:0:2: Attached scsi generic sg7 type 0
[    6.047967] sd 8:0:0:3: Attached scsi generic sg8 type 0
[    6.052734] sd 8:0:0:0: [sde] Attached SCSI removable disk
[    6.053422] sd 8:0:0:3: [sdh] Attached SCSI removable disk
[    6.053977] sd 8:0:0:1: [sdf] Attached SCSI removable disk
[    6.054772] sd 8:0:0:2: [sdg] Attached SCSI removable disk
[    9.814937] EXT4-fs (sda1): recovery complete
[    9.815396] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   11.600162] Adding 2811332k swap on /dev/sda5.  Priority:-1 extents:1 across:2811332k 
[   12.866451] udev: starting version 151
[   14.898849] type=1505 audit(1312150484.912:2):  operation="profile_load" pid=707 name="/sbin/dhclient3"
[   14.899499] type=1505 audit(1312150484.912:3):  operation="profile_load" pid=707 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.899816] type=1505 audit(1312150484.912:4):  operation="profile_load" pid=707 name="/usr/lib/connman/scripts/dhclient-script"
[   15.702081] type=1505 audit(1312150485.716:5):  operation="profile_load" pid=734 name="/usr/sbin/ntpd"
[   16.211937] lp: driver loaded but no devices found
[   16.219738] parport_pc 00:06: reported by Plug and Play ACPI
[   16.219814] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.323367] intel_rng: FWH not detected
[   16.324267] lp0: using parport0 (interrupt-driven).
[   16.332971] ppdev: user-space parallel port driver
[   16.640254] Atheros(R) L2 Ethernet Driver - version 2.2.3
[   16.640256] Copyright (c) 2007 Atheros Corporation.
[   16.640294] atl2 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.640447] atl2 0000:04:00.0: setting latency timer to 64
[   17.373224] md: bind<sdc1>
[   17.846297] nvidia: module license 'NVIDIA' taints kernel.
[   17.846301] Disabling lock debugging due to kernel taint
[   18.991552] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.991562] nvidia 0000:01:00.0: setting latency timer to 64
[   18.991566] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   18.991777] NVRM: loading NVIDIA UNIX x86 Kernel Module  275.19  Tue Jul 12 18:29:18 PDT 2011
[   20.153635]   alloc irq_desc for 28 on node -1
[   20.153638]   alloc kstat_irqs on node -1
[   20.153655] atl2 0000:04:00.0: irq 28 for MSI/MSI-X
[   20.153784] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.358424] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   20.358578] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.884829] SB-XFi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.884885] SB-XFi 0000:03:00.0: setting latency timer to 64
[   21.429735] type=1505 audit(1312150491.444:6):  operation="profile_replace" pid=1111 name="/sbin/dhclient3"
[   21.430308] type=1505 audit(1312150491.444:7):  operation="profile_replace" pid=1111 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.430631] type=1505 audit(1312150491.444:8):  operation="profile_replace" pid=1111 name="/usr/lib/connman/scripts/dhclient-script"
[   21.527880] type=1505 audit(1312150491.540:9):  operation="profile_load" pid=1110 name="/usr/share/gdm/guest-session/Xsession"
[   21.548693] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.548721] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.775512] hda_codec: num_steps = 0 for NID=0x1c (ctl = Front Playback Volume)
[   21.775672] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   21.775858] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.775861] hda_intel: Disable MSI for Nvidia chipset
[   21.775889] HDA Intel 0000:01:00.1: setting latency timer to 64
[   22.045307] type=1505 audit(1312150492.060:10):  operation="profile_load" pid=1119 name="/usr/lib/cups/backend/cups-pdf"
[   22.046055] type=1505 audit(1312150492.060:11):  operation="profile_load" pid=1119 name="/usr/sbin/cupsd"
[   22.208962] type=1505 audit(1312150492.224:12):  operation="profile_load" pid=1253 name="/usr/sbin/mysqld"
[   22.211249] type=1505 audit(1312150492.224:13):  operation="profile_replace" pid=1254 name="/usr/sbin/ntpd"
[   22.220139] type=1505 audit(1312150492.232:14):  operation="profile_load" pid=1112 name="/usr/bin/evince"
[   22.227506] type=1505 audit(1312150492.240:15):  operation="profile_load" pid=1112 name="/usr/bin/evince-previewer"
[   22.584030] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.589131] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.592282] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.597161] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.606170] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.609739] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.613485] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.617055] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.620872] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.624488] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.627755] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.631618] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.634674] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.637642] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.644256] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.649036] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.652155] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.657438] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.660798] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.663883] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.667329] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.673809] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.676455] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.680937] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.684126] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.687583] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.691201] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.695565] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.699085] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.703376] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.706329] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.710402] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.715502] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.718414] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.722777] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.726345] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.729811] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.734442] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.739213] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.743939] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.747646] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.750924] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   22.754093] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[   25.482847] lirc_dev: IR Remote Control driver registered, major 61 
[   25.499984] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   25.499987] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   25.500017] usbcore: registered new interface driver lirc_mceusb
[   29.721687] __ratelimit: 6 callbacks suppressed
[   29.721690] type=1505 audit(1312150499.736:18):  operation="profile_replace" pid=1776 name="/usr/sbin/mysqld"
[   31.120509] eth0: no IPv6 routers present
[   33.922710] vboxdrv: Found 2 processor cores.
[   33.922826] vboxdrv: fAsync=0 offMin=0x1ce offMax=0x1b0d
[   33.923272] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   33.923275] vboxdrv: Successfully loaded version 3.2.12 (interface 0x00140001).
[   57.944229] CPU0 attaching NULL sched-domain.
[   57.944235] CPU1 attaching NULL sched-domain.
[   57.964560] CPU0 attaching sched-domain:
[   57.964563]  domain 0: span 0-1 level MC
[   57.964566]   groups: 0 1
[   57.964571] CPU1 attaching sched-domain:
[   57.964572]  domain 0: span 0-1 level MC
[   57.964574]   groups: 1 0
[   76.624747] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[  122.762579] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[  240.793220] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[  240.793450] gnome-alsamixer[3062]: segfault at 38 ip 0804cde2 sp bf8ff380 error 4 in gnome-alsamixer[8048000+c000]
[  242.795146] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[  242.795361] gnome-alsamixer[3065]: segfault at 38 ip 0804cde2 sp bff486c0 error 4 in gnome-alsamixer[8048000+c000]
[  260.877393] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[  307.337579] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[  307.337637] gnome-alsamixer[3097]: segfault at 38 ip 0804cde2 sp bff8cdf0 error 4 in gnome-alsamixer[8048000+c000]
[  426.840999] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[  426.841065] gnome-alsamixer[3100]: segfault at 38 ip 0804cde2 sp bf8174c0 error 4 in gnome-alsamixer[8048000+c000]
[ 1050.976859] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[ 1050.977114] gnome-alsamixer[3111]: segfault at 38 ip 0804cde2 sp bfd36520 error 4 in gnome-alsamixer[8048000+c000]
[ 1609.301507] mythfilldatabas[4164]: segfault at dac4c ip 00168569 sp b5f5bc60 error 4 in libmythdb-0.23.so.0.23.0[120000+a2000]
[ 1740.404880] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[ 1740.444815] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[ 1740.754952] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[ 2055.513914] soffice.bin[4490]: segfault at 77cd5e9 ip 077cd5e9 sp b3cf31a0 error 4 in libvorbis.so.0.4.3[78dc000+27000]
[ 2285.763909] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[ 2285.767986] hda_codec: num_steps = 0 for NID=0x1d (ctl = Headphone Playback Volume)
[ 2286.235451] hda_codec: num_steps = 0 for NID=0x1c (ctl = Front Playback Volume)
[ 3111.358581] md: md_d0 stopped.
[ 3111.358598] md: unbind<sdc1>
[ 3111.368042] md: export_rdev(sdc1)
[ 3112.475771] md: md0 stopped.
[ 3112.481985] md: bind<sdd1>
[ 3112.482513] md: bind<sdb1>
[ 3112.483551] md: bind<sdc1>
[ 3112.511263] raid5: device sdc1 operational as raid disk 1
[ 3112.511266] raid5: device sdd1 operational as raid disk 2
[ 3112.511552] raid5: allocated 3179kB for md0
[ 3112.511691] 1: w=1 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
[ 3112.511693] 2: w=2 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
[ 3112.511695] raid5: raid level 5 set md0 active with 2 out of 3 devices, algorithm 2
[ 3112.511698] RAID5 conf printout:
[ 3112.511700]  --- rd:3 wd:2
[ 3112.511701]  disk 1, o:1, dev:sdc1
[ 3112.511703]  disk 2, o:1, dev:sdd1
[ 3112.511731] md0: detected capacity change from 0 to 4000792444928
[ 3112.511971]  md0:RAID5 conf printout:
[ 3112.512190]  --- rd:3 wd:2
[ 3112.512192]  disk 0, o:1, dev:sdb1
[ 3112.512194]  disk 1, o:1, dev:sdc1
[ 3112.512195]  disk 2, o:1, dev:sdd1
[ 3112.512261] md: recovery of RAID array md0
[ 3112.512263] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[ 3112.512265] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[ 3112.512268] md: using 128k window, over a total of 1953511936 blocks.
[ 3112.516691]  unknown partition table

```

installed pulseaudio with no problems... except for the lack of sound :-)

---

### Post by tylersontag on 2011-07-31
Also, my media center/storage box that this concerns is Ubuntu 10.04 LTS

---

### Post by tylersontag on 2011-08-01
Had some more time to work on this when i got home last night and checked the pulseaudio install... the daemon was running in the background, where as before it would always fail silently everytime one tried to --start it.

So i tried reinstalling PulseAudio volume manager and to my suprise it actually opened (before i would get a "Connection Refused" error and crash on opening)  I went to the device manager tab and i think my audio had reverted to routing through my old embedded motherboard audio card rather than my PCI-e Creative Labs XFI.  Thus, giving me the impression my sound wasnt working.  I changed it back and everything worked.

The only outsanding issue, is that my keyboard volume control and the on-screen volume widget no longer actually impact the sound.  Does anyone know how i can change the keyboard mapping to increase/decrease the pulseaudio sound versus the non-working gnome-volume-control?

---

