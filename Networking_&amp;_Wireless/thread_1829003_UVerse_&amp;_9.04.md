---
title: "UVerse &amp; 9.04"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by cdmccreary on 2011-08-20
I have a similar problem with Uverse wireless. I need to load 9.04 from CD. Then to connect to ATT Uverse. Windows computers have no problem getting on the wireless network.
 
I normally use WPA TKIP on 802.11g. It never works on my ATT 2wire router but has no problem with a cheap Frys Wireless G router. I can see all the ATT wireless networks in my area.
 
Any clues. Thanks in advance.

---

### Post by bkratz on 2011-08-20
> **cdmccreary said:**
> I have a similar problem with Uverse wireless. I need to load 9.04 from CD. Then to connect to ATT Uverse. Windows computers have no problem getting on the wireless network.
 
I normally use WPA TKIP on 802.11g. It never works on my ATT 2wire router but has no problem with a cheap Frys Wireless G router. I can see all the ATT wireless networks in my area.
 
Any clues. Thanks in advance.

Back when I used to use 9.04 with my Uverse wireless network, I never did get it to connect with either wep or wpa, but wpa2 worked flawlessly. You might want to try another encryption. By  the way 9.04 is no longer supported. I thought it was the best ever, but upgraded to 10.04 LTS then 11.04 and back to 10.04. I had issues with the new desktop.

---

### Post by cdmccreary on 2011-08-20
My take is that ATT incorporated a way to prevent Linux variants from communicating with the UVERSE router; that way they would not have to answer any Linux questions.

---

### Post by bkratz on 2011-08-20
> **cdmccreary said:**
> My take is that ATT incorporated a way to prevent Linux variants from communicating with the UVERSE router; that way they would not have to answer any Linux questions.



unless they have recently changed something, that is how I have always used it.

---

### Post by wojox on 2011-08-20
> **cdmccreary said:**
> My take is that ATT incorporated a way to prevent Linux variants from communicating with the UVERSE router; that way they would not have to answer any Linux questions.

I work at Pace Technologies who bought 2Wire and holds the contract for AT&T UVerse. We use an embedded Linux system to power the router.  

What are the responses to these commands:

```
lshw -C network
lsmod
dmesg > dmesg.txt
```

Upload the .txt file and post the other commands back in code tags please. :)

---

### Post by cdmccreary on 2011-08-21
I used the 10.10 CD but have the same problem either version (only using 2wire router)
 
```

lshw -C network

```
see attachment
 
```

lsmod

```
see attachment
 
```
 
dmesg > dmesg.txt

```
 
```
 
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[ 0.000000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 00000000bf6d0000 (usable)
[ 0.000000] BIOS-e820: 00000000bf6d0000 - 00000000bf6df000 (ACPI NVS)
[ 0.000000] BIOS-e820: 00000000bf6df000 - 00000000c0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[ 0.000000] BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[ 0.000000] BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[ 0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[ 0.000000] DMI present.
[ 0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[ 0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[ 0.000000] last_pfn = 0xbf6d0 max_arch_pfn = 0x100000
[ 0.000000] MTRR default type: uncachable
[ 0.000000] MTRR fixed ranges enabled:
[ 0.000000] 00000-9FFFF write-back
[ 0.000000] A0000-BFFFF uncachable
[ 0.000000] C0000-FFFFF write-protect
[ 0.000000] MTRR variable ranges enabled:
[ 0.000000] 0 base 000000000 mask F80000000 write-back
[ 0.000000] 1 base 080000000 mask FC0000000 write-back
[ 0.000000] 2 base 0BF700000 mask FFFF00000 uncachable
[ 0.000000] 3 base 0BF800000 mask FFF800000 uncachable
[ 0.000000] 4 disabled
[ 0.000000] 5 disabled
[ 0.000000] 6 disabled
[ 0.000000] 7 disabled
[ 0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[ 0.000000] Scanning 1 areas for low memory corruption
[ 0.000000] modified physical RAM map:
[ 0.000000] modified: 0000000000000000 - 0000000000001000 (reserved)
[ 0.000000] modified: 0000000000001000 - 0000000000002000 (usable)
[ 0.000000] modified: 0000000000002000 - 0000000000010000 (reserved)
[ 0.000000] modified: 0000000000010000 - 000000000009f800 (usable)
[ 0.000000] modified: 000000000009f800 - 00000000000a0000 (reserved)
[ 0.000000] modified: 00000000000e0000 - 0000000000100000 (reserved)
[ 0.000000] modified: 0000000000100000 - 00000000bf6d0000 (usable)
[ 0.000000] modified: 00000000bf6d0000 - 00000000bf6df000 (ACPI NVS)
[ 0.000000] modified: 00000000bf6df000 - 00000000c0000000 (reserved)
[ 0.000000] modified: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] modified: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] modified: 00000000fed00000 - 00000000fed00400 (reserved)
[ 0.000000] modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[ 0.000000] modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[ 0.000000] modified: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] modified: 00000000ff000000 - 0000000100000000 (reserved)
[ 0.000000] initial memory mapped : 0 - 00c00000
[ 0.000000] found SMP MP-table at [c00f75b0] f75b0
[ 0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[ 0.000000] 0000000000 - 0000400000 page 4k
[ 0.000000] 0000400000 - 0037400000 page 2M
[ 0.000000] 0037400000 - 00377fe000 page 4k
[ 0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[ 0.000000] RAMDISK: 7f51e000 - 80000000
[ 0.000000] Allocated new RAMDISK: 009a5000 - 0148698f
[ 0.000000] Move RAMDISK from 000000007f51e000 - 000000007ffff98e to 009a5000 - 0148698e
[ 0.000000] ACPI: RSDP 000f7580 00024 (v02 PTLTD )
[ 0.000000] ACPI: XSDT bf6d386f 00094 (v01 GATEWA SYSTEM 06040000 LTP 00000000)
[ 0.000000] ACPI: FACP bf6dbbd2 000F4 (v03 INTEL CRESTLNE 06040000 ALAN 00000001)
[ 0.000000] ACPI: DSDT bf6d4e6e 06CF0 (v02 INTEL CRESTLNE 06040000 INTL 20050624)
[ 0.000000] ACPI: FACS bf6defc0 00040
[ 0.000000] ACPI: APIC bf6dbcc6 00068 (v01 INTEL CRESTLNE 06040000 LOHR 0000005A)
[ 0.000000] ACPI: HPET bf6dbd2e 00038 (v01 INTEL CRESTLNE 06040000 LOHR 0000005A)
[ 0.000000] ACPI: MCFG bf6dbd66 0003C (v01 INTEL CRESTLNE 06040000 LOHR 0000005A)
[ 0.000000] ACPI: TCPA bf6dbda2 00032 (v01 Intel CRESTLN 06040000 00005A52)
[ 0.000000] ACPI: TMOR bf6dbdd4 00026 (v01 PTLTD 06040000 PTL 00000003)
[ 0.000000] ACPI: SLIC bf6dbdfa 00176 (v01 GATEWA SYSTEM 06040000 Kevi 00000001)
[ 0.000000] ACPI: APIC bf6dbf70 00068 (v01 PTLTD ? APIC 06040000 LTP 00000000)
[ 0.000000] ACPI: BOOT bf6dbfd8 00028 (v01 PTLTD $SBFTBL$ 06040000 LTP 00000001)
[ 0.000000] ACPI: SSDT bf6d4b91 002DD (v01 SataRe SataAhci 00001000 INTL 20050624)
[ 0.000000] ACPI: SSDT bf6d4899 002F8 (v01 BrtRef DD01BRT 00001000 INTL 20050624)
[ 0.000000] ACPI: SSDT bf6d3e8f 0025F (v01 PmRef Cpu0Tst 00003000 INTL 20050624)
[ 0.000000] ACPI: SSDT bf6d3de9 000A6 (v01 PmRef Cpu1Tst 00003000 INTL 20050624)
[ 0.000000] ACPI: SSDT bf6d3903 004E6 (v01 PmRef CpuPm 00003000 INTL 20050624)
[ 0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[ 0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] 2174MB HIGHMEM available.
[ 0.000000] 887MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 377fe000
[ 0.000000] low ram: 0 - 377fe000
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000001 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x000377fe
[ 0.000000] HighMem 0x000377fe -> 0x000bf6d0
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[3] active PFN ranges
[ 0.000000] 0: 0x00000001 -> 0x00000002
[ 0.000000] 0: 0x00000010 -> 0x0000009f
[ 0.000000] 0: 0x00000100 -> 0x000bf6d0
[ 0.000000] On node 0 totalpages: 783968
[ 0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1488020
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3952 pages, LIFO batch:0
[ 0.000000] Normal zone: 1744 pages used for memmap
[ 0.000000] Normal zone: 221486 pages, LIFO batch:31
[ 0.000000] HighMem zone: 4350 pages used for memmap
[ 0.000000] HighMem zone: 552404 pages, LIFO batch:31
[ 0.000000] Using APIC driver default
[ 0.000000] ACPI: PM-Timer IO Port: 0x1008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[ 0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[ 0.000000] nr_irqs_gsi: 40
[ 0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[ 0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[ 0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[ 0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[ 0.000000] Booting paravirtualized kernel on bare hardware
[ 0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[ 0.000000] PERCPU: Embedded 14 pages/cpu @c3000000 s36416 r0 d20928 u2097152
[ 0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[ 0.000000] pcpu-alloc: [0] 0 1 
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 777842
[ 0.000000] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[ 0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[ 0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] allocated 15681580 bytes of page_cgroup
[ 0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[ 0.000000] Subtract (53 early reservations)
[ 0.000000] #1 [0000001000 - 0000002000] EX TRAMPOLINE
[ 0.000000] #2 [0000100000 - 00009a0adc] TEXT DATA BSS
[ 0.000000] #3 [00009a1000 - 00009a4150] BRK
[ 0.000000] #4 [00000f75c0 - 0000100000] BIOS reserved
[ 0.000000] #5 [00000f75b0 - 00000f75c0] MP-table mpf
[ 0.000000] #6 [000009f800 - 000009fd71] BIOS reserved
[ 0.000000] #7 [000009fee5 - 00000f75b0] BIOS reserved
[ 0.000000] #8 [000009fd71 - 000009fee5] MP-table mpc
[ 0.000000] #9 [0000010000 - 0000011000] TRAMPOLINE
[ 0.000000] #10 [0000011000 - 0000015000] ACPI WAKEUP
[ 0.000000] #11 [0000015000 - 0000016000] PGTABLE
[ 0.000000] #12 [00009a5000 - 0001487000] NEW RAMDISK
[ 0.000000] #13 [0001487000 - 0001488000] BOOTMEM
[ 0.000000] #14 [0001488000 - 0002c78000] BOOTMEM
[ 0.000000] #15 [0002c78000 - 0002c78004] BOOTMEM
[ 0.000000] #16 [0002c78040 - 0002c78100] BOOTMEM
[ 0.000000] #17 [0002c78100 - 0002c78154] BOOTMEM
[ 0.000000] #18 [0002c78180 - 0002c7b180] BOOTMEM
[ 0.000000] #19 [0002c7b180 - 0002c7b24c] BOOTMEM
[ 0.000000] #20 [0002c7b280 - 0002c87280] BOOTMEM
[ 0.000000] #21 [0002c87280 - 0002c872a5] BOOTMEM
[ 0.000000] #22 [0002c872c0 - 0002c872e7] BOOTMEM
[ 0.000000] #23 [0002c87300 - 0002c874c0] BOOTMEM
[ 0.000000] #24 [0002c874c0 - 0002c87500] BOOTMEM
[ 0.000000] #25 [0002c87500 - 0002c87540] BOOTMEM
[ 0.000000] #26 [0002c87540 - 0002c87580] BOOTMEM
[ 0.000000] #27 [0002c87580 - 0002c875c0] BOOTMEM
[ 0.000000] #28 [0002c875c0 - 0002c87600] BOOTMEM
[ 0.000000] #29 [0002c87600 - 0002c87640] BOOTMEM
[ 0.000000] #30 [0002c87640 - 0002c87680] BOOTMEM
[ 0.000000] #31 [0002c87680 - 0002c876c0] BOOTMEM
[ 0.000000] #32 [0002c876c0 - 0002c87700] BOOTMEM
[ 0.000000] #33 [0002c87700 - 0002c87740] BOOTMEM
[ 0.000000] #34 [0002c87740 - 0002c87780] BOOTMEM
[ 0.000000] #35 [0002c87780 - 0002c877c0] BOOTMEM
[ 0.000000] #36 [0002c877c0 - 0002c87800] BOOTMEM
[ 0.000000] #37 [0002c87800 - 0002c87810] BOOTMEM
[ 0.000000] #38 [0002c87840 - 0002c87850] BOOTMEM
[ 0.000000] #39 [0002c87880 - 0002c878e4] BOOTMEM
[ 0.000000] #40 [0002c87900 - 0002c87964] BOOTMEM
[ 0.000000] #41 [0003000000 - 000300e000] BOOTMEM
[ 0.000000] #42 [0003200000 - 000320e000] BOOTMEM
[ 0.000000] #43 [0002c89980 - 0002c89984] BOOTMEM
[ 0.000000] #44 [0002c899c0 - 0002c899c4] BOOTMEM
[ 0.000000] #45 [0002c89a00 - 0002c89a08] BOOTMEM
[ 0.000000] #46 [0002c89a40 - 0002c89a48] BOOTMEM
[ 0.000000] #47 [0002c89a80 - 0002c89b28] BOOTMEM
[ 0.000000] #48 [0002c89b40 - 0002c89ba8] BOOTMEM
[ 0.000000] #49 [0002c89bc0 - 0002c8dbc0] BOOTMEM
[ 0.000000] #50 [0002c8dbc0 - 0002d0dbc0] BOOTMEM
[ 0.000000] #51 [0002d0dbc0 - 0002d4dbc0] BOOTMEM
[ 0.000000] #52 [000320e000 - 000410282c] BOOTMEM
[ 0.000000] Initializing HighMem for node 0 (000377fe:000bf6d0)
[ 0.000000] Memory: 3075052k/3136320k available (4928k kernel code, 60820k reserved, 2336k data, 684k init, 2227016k highmem)
[ 0.000000] virtual kernel memory layout:
[ 0.000000] fixmap : 0xfff16000 - 0xfffff000 ( 932 kB)
[ 0.000000] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 0.000000] vmalloc : 0xf7ffe000 - 0xff7fe000 ( 120 MB)
[ 0.000000] lowmem : 0xc0000000 - 0xf77fe000 ( 887 MB)
[ 0.000000] .init : 0xc0819000 - 0xc08c4000 ( 684 kB)
[ 0.000000] .data : 0xc05d029e - 0xc0818668 (2336 kB)
[ 0.000000] .text : 0xc0100000 - 0xc05d029e (4928 kB)
[ 0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[ 0.000000] Hierarchical RCU implementation.
[ 0.000000] RCU dyntick-idle grace-period acceleration is enabled.
[ 0.000000] RCU-based detection of stalled CPUs is disabled.
[ 0.000000] Verbose stalled-CPUs detection is disabled.
[ 0.000000] NR_IRQS:2304 nr_irqs:512
[ 0.000000] Extended CMOS year: 2000
[ 0.000000] Console: colour VGA+ 80x25
[ 0.000000] console [tty0] enabled
[ 0.000000] hpet clockevent registered
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 1496.275 MHz processor.
[ 0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 2992.55 BogoMIPS (lpj=5985100)
[ 0.004013] pid_max: default: 32768 minimum: 301
[ 0.004038] Security Framework initialized
[ 0.004059] AppArmor: AppArmor initialized
[ 0.004062] Yama: becoming mindful.
[ 0.004133] Mount-cache hash table entries: 512
[ 0.004300] Initializing cgroup subsys ns
[ 0.004306] Initializing cgroup subsys cpuacct
[ 0.004313] Initializing cgroup subsys memory
[ 0.004324] Initializing cgroup subsys devices
[ 0.004327] Initializing cgroup subsys freezer
[ 0.004330] Initializing cgroup subsys net_cls
[ 0.004365] CPU: Physical Processor ID: 0
[ 0.004368] CPU: Processor Core ID: 0
[ 0.004371] mce: CPU supports 6 MCE banks
[ 0.004382] CPU0: Thermal monitoring handled by SMI
[ 0.004386] using mwait in idle threads.
[ 0.004396] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[ 0.004404] PEBS disabled due to CPU errata.
[ 0.004412] ... version: 2
[ 0.004415] ... bit width: 40
[ 0.004417] ... generic registers: 2
[ 0.004420] ... value mask: 000000ffffffffff
[ 0.004423] ... max period: 000000007fffffff
[ 0.004426] ... fixed-purpose events: 3
[ 0.004428] ... event mask: 0000000700000003
[ 0.009747] ACPI: Core revision 20100428
[ 0.024013] ftrace: converting mcount calls to 0f 1f 44 00 00
[ 0.024018] ftrace: allocating 21758 entries in 43 pages
[ 0.028063] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.028437] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.071030] CPU0: Intel(R) Core(TM)2 Duo CPU T5250 @ 1.50GHz stepping 0d
[ 0.072000] Booting Node 0, Processors #1 Ok.
[ 0.008000] Initializing CPU#1
[ 0.008000] CPU1: Thermal monitoring handled by SMI
[ 0.160019] Brought up 2 CPUs
[ 0.160023] Total of 2 processors activated (5985.07 BogoMIPS).
[ 0.160650] devtmpfs: initialized
[ 0.161366] regulator: core version 0.5
[ 0.161401] Time: 11:13:22 Date: 08/20/11
[ 0.161454] NET: Registered protocol family 16
[ 0.161485] Trying to unpack rootfs image as initramfs...
[ 0.161629] EISA bus registered
[ 0.161640] ACPI: bus type pci registered
[ 0.161740] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[ 0.161745] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[ 0.161748] PCI: Using MMCONFIG for extended config space
[ 0.161751] PCI: Using configuration type 1 for base access
[ 1.160206] bio: create slab <bio-0> at 0
[ 1.162552] ACPI: EC: Look up EC in DSDT
[ 1.167406] ACPI: BIOS _OSI(Linux) query ignored
[ 1.170299] ACPI: SSDT bf6d461d 001B4 (v01 PmRef Cpu0Ist 00003000 INTL 20050624)
[ 1.170961] ACPI: Dynamic OEM Table Load:
[ 1.170966] ACPI: SSDT (null) 001B4 (v01 PmRef Cpu0Ist 00003000 INTL 20050624)
[ 1.171322] ACPI: SSDT bf6d40ee 004AA (v01 PmRef Cpu0Cst 00003001 INTL 20050624)
[ 1.172144] ACPI: Dynamic OEM Table Load:
[ 1.172149] ACPI: SSDT (null) 004AA (v01 PmRef Cpu0Cst 00003001 INTL 20050624)
[ 1.172720] ACPI: SSDT bf6d47d1 000C8 (v01 PmRef Cpu1Ist 00003000 INTL 20050624)
[ 1.173369] ACPI: Dynamic OEM Table Load:
[ 1.173373] ACPI: SSDT (null) 000C8 (v01 PmRef Cpu1Ist 00003000 INTL 20050624)
[ 1.173577] ACPI: SSDT bf6d4598 00085 (v01 PmRef Cpu1Cst 00003000 INTL 20050624)
[ 1.174211] ACPI: Dynamic OEM Table Load:
[ 1.174215] ACPI: SSDT (null) 00085 (v01 PmRef Cpu1Cst 00003000 INTL 20050624)
[ 1.174486] ACPI: Interpreter enabled
[ 1.174491] ACPI: (supports S0 S3 S4 S5)
[ 1.174522] ACPI: Using IOAPIC for interrupt routing
[ 1.176024] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[ 1.176343] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[ 1.184522] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[ 1.184997] ACPI: No dock devices found.
[ 1.185003] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[ 1.185785] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[ 1.187314] pci_root PNP0A08:00: host bridge window [io 0x0000-0x0cf7] (ignored)
[ 1.187319] pci_root PNP0A08:00: host bridge window [io 0x0d00-0xffff] (ignored)
[ 1.187323] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[ 1.187328] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[ 1.187332] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[ 1.187336] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[ 1.187339] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[ 1.187344] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff] (ignored)
[ 1.187348] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff] (ignored)
[ 1.187439] pci 0000:00:02.0: reg 10: [mem 0xf3000000-0xf30fffff 64bit]
[ 1.187450] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[ 1.187457] pci 0000:00:02.0: reg 20: [io 0x1800-0x1807]
[ 1.187512] pci 0000:00:02.1: reg 10: [mem 0xf3100000-0xf31fffff 64bit]
[ 1.187643] pci 0000:00:1a.0: reg 20: [io 0x1820-0x183f]
[ 1.187717] pci 0000:00:1a.1: reg 20: [io 0x1840-0x185f]
[ 1.187791] pci 0000:00:1a.7: reg 10: [mem 0xf3404800-0xf3404bff]
[ 1.187868] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[ 1.187875] pci 0000:00:1a.7: PME# disabled
[ 1.187929] pci 0000:00:1b.0: reg 10: [mem 0xf3400000-0xf3403fff 64bit]
[ 1.188007] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[ 1.188013] pci 0000:00:1b.0: PME# disabled
[ 1.188127] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[ 1.188133] pci 0000:00:1c.0: PME# disabled
[ 1.188250] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[ 1.188256] pci 0000:00:1c.1: PME# disabled
[ 1.188373] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[ 1.188379] pci 0000:00:1c.2: PME# disabled
[ 1.188462] pci 0000:00:1d.0: reg 20: [io 0x1860-0x187f]
[ 1.188540] pci 0000:00:1d.1: reg 20: [io 0x1880-0x189f]
[ 1.188613] pci 0000:00:1d.2: reg 20: [io 0x18a0-0x18bf]
[ 1.188688] pci 0000:00:1d.7: reg 10: [mem 0xf3404c00-0xf3404fff]
[ 1.188761] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[ 1.188767] pci 0000:00:1d.7: PME# disabled
[ 1.188955] pci 0000:00:1f.0: quirk: [io 0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[ 1.188961] pci 0000:00:1f.0: quirk: [io 0x1180-0x11bf] claimed by ICH6 GPIO
[ 1.188968] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[ 1.188974] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[ 1.189036] pci 0000:00:1f.1: reg 10: [io 0x0000-0x0007]
[ 1.189046] pci 0000:00:1f.1: reg 14: [io 0x0000-0x0003]
[ 1.189056] pci 0000:00:1f.1: reg 18: [io 0x0000-0x0007]
[ 1.189066] pci 0000:00:1f.1: reg 1c: [io 0x0000-0x0003]
[ 1.189076] pci 0000:00:1f.1: reg 20: [io 0x1810-0x181f]
[ 1.189149] pci 0000:00:1f.2: reg 10: [io 0x1c00-0x1c07]
[ 1.189159] pci 0000:00:1f.2: reg 14: [io 0x18d4-0x18d7]
[ 1.189169] pci 0000:00:1f.2: reg 18: [io 0x18d8-0x18df]
[ 1.189179] pci 0000:00:1f.2: reg 1c: [io 0x18d0-0x18d3]
[ 1.189189] pci 0000:00:1f.2: reg 20: [io 0x18e0-0x18ff]
[ 1.189199] pci 0000:00:1f.2: reg 24: [mem 0xf3404000-0xf34047ff]
[ 1.189248] pci 0000:00:1f.2: PME# supported from D3hot
[ 1.189255] pci 0000:00:1f.2: PME# disabled
[ 1.189292] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[ 1.189322] pci 0000:00:1f.3: reg 20: [io 0x1c20-0x1c3f]
[ 1.189472] pci 0000:02:00.0: reg 10: [io 0x2000-0x20ff]
[ 1.189504] pci 0000:02:00.0: reg 18: [mem 0xf0000000-0xf0000fff 64bit]
[ 1.189536] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[ 1.189604] pci 0000:02:00.0: supports D1 D2
[ 1.189607] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[ 1.189614] pci 0000:02:00.0: PME# disabled
[ 1.189648] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device. You can enable it with 'pcie_aspm=force'
[ 1.189664] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[ 1.189672] pci 0000:00:1c.0: bridge window [io 0x2000-0x2fff]
[ 1.189678] pci 0000:00:1c.0: bridge window [mem 0xf0000000-0xf0ffffff]
[ 1.189688] pci 0000:00:1c.0: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 1.189859] pci 0000:04:00.0: reg 10: [mem 0xf1000000-0xf1000fff]
[ 1.190109] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[ 1.190123] pci 0000:04:00.0: PME# disabled
[ 1.190195] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device. You can enable it with 'pcie_aspm=force'
[ 1.190225] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[ 1.190232] pci 0000:00:1c.1: bridge window [io 0x3000-0x3fff]
[ 1.190239] pci 0000:00:1c.1: bridge window [mem 0xf1000000-0xf1ffffff]
[ 1.190249] pci 0000:00:1c.1: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 1.190319] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[ 1.190325] pci 0000:00:1c.2: bridge window [io 0x4000-0x4fff]
[ 1.190332] pci 0000:00:1c.2: bridge window [mem 0xf2000000-0xf2ffffff]
[ 1.190342] pci 0000:00:1c.2: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 1.190446] pci 0000:00:1e.0: PCI bridge to [bus 08-08] (subtractive decode)
[ 1.190452] pci 0000:00:1e.0: bridge window [io 0xf000-0x0000] (disabled)
[ 1.190459] pci 0000:00:1e.0: bridge window [mem 0xfff00000-0x000fffff] (disabled)
[ 1.190469] pci 0000:00:1e.0: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 1.190473] pci 0000:00:1e.0: bridge window [io 0x0000-0xffff] (subtractive decode)
[ 1.190477] pci 0000:00:1e.0: bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[ 1.190508] pci_bus 0000:00: on NUMA node 0
[ 1.190514] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 1.190917] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[ 1.191040] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[ 1.191159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[ 1.191339] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[ 1.208512] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[ 1.208659] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[ 1.208805] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[ 1.208945] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[ 1.209088] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[ 1.209231] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[ 1.209372] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[ 1.209513] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[ 1.209582] HEST: Table is not found!
[ 1.209688] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[ 1.209710] vgaarb: loaded
[ 1.209932] SCSI subsystem initialized
[ 1.210017] libata version 3.00 loaded.
[ 1.210091] usbcore: registered new interface driver usbfs
[ 1.210109] usbcore: registered new interface driver hub
[ 1.210142] usbcore: registered new device driver usb
[ 1.210321] ACPI: WMI: Mapper loaded
[ 1.210324] PCI: Using ACPI for IRQ routing
[ 1.210328] PCI: pci_cache_line_size set to 64 bytes
[ 1.210463] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[ 1.210466] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[ 1.210470] reserve RAM buffer: 00000000bf6d0000 - 00000000bfffffff 
[ 1.210601] NetLabel: Initializing
[ 1.210604] NetLabel: domain hash size = 128
[ 1.210606] NetLabel: protocols = UNLABELED CIPSOv4
[ 1.210623] NetLabel: unlabeled traffic allowed by default
[ 1.210663] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[ 1.210671] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 1.210679] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[ 3.060057] Switching to clocksource tsc
[ 3.077404] AppArmor: AppArmor Filesystem Enabled
[ 3.077427] pnp: PnP ACPI init
[ 3.077455] ACPI: bus type pnp registered
[ 3.080906] pnp: PnP ACPI: found 10 devices
[ 3.080911] ACPI: ACPI bus type pnp unregistered
[ 3.080917] PnPBIOS: Disabled by ACPI PNP
[ 3.080940] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[ 3.080945] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[ 3.080949] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[ 3.080954] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[ 3.080958] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[ 3.080962] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[ 3.080966] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[ 3.080971] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[ 3.080981] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[ 3.080991] system 00:06: [io 0x0680-0x069f] has been reserved
[ 3.080995] system 00:06: [io 0x0800-0x080f] has been reserved
[ 3.081000] system 00:06: [io 0x1000-0x107f] has been reserved
[ 3.081004] system 00:06: [io 0x1180-0x11bf] has been reserved
[ 3.081008] system 00:06: [io 0x1640-0x164f] has been reserved
[ 3.081011] system 00:06: [io 0xfe00] has been reserved
[ 3.117854] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff pref]
[ 3.117861] pci 0000:00:1c.1: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[ 3.117866] pci 0000:00:1c.2: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[ 3.117871] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0600000-0xc06000ff]
[ 3.117879] pci 0000:00:1f.3: BAR 0: set to [mem 0xc0600000-0xc06000ff] (PCI address [0xc0600000-0xc06000ff]
[ 3.117885] pci 0000:02:00.0: BAR 6: assigned [mem 0xc0000000-0xc001ffff pref]
[ 3.117889] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[ 3.117894] pci 0000:00:1c.0: bridge window [io 0x2000-0x2fff]
[ 3.117903] pci 0000:00:1c.0: bridge window [mem 0xf0000000-0xf0ffffff]
[ 3.117909] pci 0000:00:1c.0: bridge window [mem 0xc0000000-0xc01fffff pref]
[ 3.117920] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[ 3.117925] pci 0000:00:1c.1: bridge window [io 0x3000-0x3fff]
[ 3.117934] pci 0000:00:1c.1: bridge window [mem 0xf1000000-0xf1ffffff]
[ 3.117940] pci 0000:00:1c.1: bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[ 3.117950] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[ 3.117956] pci 0000:00:1c.2: bridge window [io 0x4000-0x4fff]
[ 3.117964] pci 0000:00:1c.2: bridge window [mem 0xf2000000-0xf2ffffff]
[ 3.117971] pci 0000:00:1c.2: bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[ 3.117982] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
[ 3.117984] pci 0000:00:1e.0: bridge window [io disabled]
[ 3.117992] pci 0000:00:1e.0: bridge window [mem disabled]
[ 3.117998] pci 0000:00:1e.0: bridge window [mem pref disabled]
[ 3.118025] alloc irq_desc for 17 on node -1
[ 3.118028] alloc kstat_irqs on node -1
[ 3.118038] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3.118046] pci 0000:00:1c.0: setting latency timer to 64
[ 3.118060] alloc irq_desc for 16 on node -1
[ 3.118062] alloc kstat_irqs on node -1
[ 3.118069] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[ 3.118075] pci 0000:00:1c.1: setting latency timer to 64
[ 3.118095] alloc irq_desc for 18 on node -1
[ 3.118097] alloc kstat_irqs on node -1
[ 3.118104] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 3.118110] pci 0000:00:1c.2: setting latency timer to 64
[ 3.118122] pci 0000:00:1e.0: setting latency timer to 64
[ 3.118130] pci_bus 0000:00: resource 0 [io 0x0000-0xffff]
[ 3.118134] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[ 3.118138] pci_bus 0000:02: resource 0 [io 0x2000-0x2fff]
[ 3.118141] pci_bus 0000:02: resource 1 [mem 0xf0000000-0xf0ffffff]
[ 3.118145] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc01fffff pref]
[ 3.118149] pci_bus 0000:04: resource 0 [io 0x3000-0x3fff]
[ 3.118152] pci_bus 0000:04: resource 1 [mem 0xf1000000-0xf1ffffff]
[ 3.118156] pci_bus 0000:04: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[ 3.118160] pci_bus 0000:06: resource 0 [io 0x4000-0x4fff]
[ 3.118164] pci_bus 0000:06: resource 1 [mem 0xf2000000-0xf2ffffff]
[ 3.118167] pci_bus 0000:06: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[ 3.118171] pci_bus 0000:08: resource 4 [io 0x0000-0xffff]
[ 3.118175] pci_bus 0000:08: resource 5 [mem 0x00000000-0xffffffff]
[ 3.118252] NET: Registered protocol family 2
[ 3.118371] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 3.118734] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 3.119230] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 3.119468] TCP: Hash tables configured (established 131072 bind 65536)
[ 3.119471] TCP reno registered
[ 3.119476] UDP hash table entries: 512 (order: 2, 16384 bytes)
[ 3.119487] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[ 3.119597] NET: Registered protocol family 1
[ 3.119621] pci 0000:00:02.0: Boot video device
[ 3.119831] PCI: CLS 64 bytes, default 64
[ 3.119865] Simple Boot Flag at 0x36 set to 0x1
[ 3.120147] cpufreq-nforce2: No nForce2 chipset.
[ 3.120188] Scanning for low memory corruption every 60 seconds
[ 3.120373] audit: initializing netlink socket (disabled)
[ 3.120387] type=2000 audit(1313838805.120:1): initialized
[ 3.135212] highmem bounce pool size: 64 pages
[ 3.135219] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 3.137354] VFS: Disk quotas dquot_6.5.2
[ 3.137443] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 3.138294] fuse init (API version 7.14)
[ 3.138422] msgmni has been set to 1656
[ 3.140607] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 3.140612] io scheduler noop registered
[ 3.140615] io scheduler deadline registered
[ 3.140635] io scheduler cfq registered (default)
[ 3.140798] pcieport 0000:00:1c.0: setting latency timer to 64
[ 3.140859] alloc irq_desc for 40 on node -1
[ 3.140863] alloc kstat_irqs on node -1
[ 3.140877] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[ 3.141014] pcieport 0000:00:1c.1: setting latency timer to 64
[ 3.141073] alloc irq_desc for 41 on node -1
[ 3.141076] alloc kstat_irqs on node -1
[ 3.141088] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[ 3.141224] pcieport 0000:00:1c.2: setting latency timer to 64
[ 3.141283] alloc irq_desc for 42 on node -1
[ 3.141286] alloc kstat_irqs on node -1
[ 3.141298] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[ 3.141456] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 3.141588] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 3.141715] intel_idle: MWAIT substates: 0x22220
[ 3.141718] intel_idle: does not run on family 6 model 15
[ 3.142103] ACPI: AC Adapter [AC] (on-line)
[ 3.142213] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[ 3.142460] ACPI: Lid Switch [LID0]
[ 3.142524] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[ 3.142531] ACPI: Power Button [PWRB]
[ 3.142592] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[ 3.142597] ACPI: Sleep Button [SLPB]
[ 3.142685] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[ 3.142690] ACPI: Power Button [PWRF]
[ 3.143100] ACPI: acpi_idle registered with cpuidle
[ 3.146609] Monitor-Mwait will be used to enter C-1 state
[ 3.146673] Monitor-Mwait will be used to enter C-2 state
[ 3.146800] Monitor-Mwait will be used to enter C-3 state
[ 3.146809] Marking TSC unstable due to TSC halts in idle
[ 3.147284] Switching to clocksource hpet
[ 3.477346] thermal LNXTHERM:01: registered as thermal_zone0
[ 3.477364] ACPI: Thermal Zone [TZ00] (55 C)
[ 3.477563] ERST: Table is not found!
[ 3.477958] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[ 3.480260] brd: module loaded
[ 3.481124] loop: module loaded
[ 3.481421] ata_piix 0000:00:1f.1: version 2.13
[ 3.481442] alloc irq_desc for 19 on node -1
[ 3.481445] alloc kstat_irqs on node -1
[ 3.481455] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 3.481508] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 3.481601] scsi0 : ata_piix
[ 3.484415] Freeing initrd memory: 11144k freed
[ 3.488254] scsi1 : ata_piix
[ 3.489438] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[ 3.489445] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[ 3.490073] Fixed MDIO Bus: probed
[ 3.490140] PPP generic driver version 2.4.2
[ 3.490293] tun: Universal TUN/TAP device driver, 1.6
[ 3.490296] tun: (C) 1999-2004 Max Krasnyansky <[EMAIL="maxk@qualcomm.com"]maxk@qualcomm.com[/EMAIL]>
[ 3.490483] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 3.490537] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 3.490584] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 3.490590] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[ 3.490652] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[ 3.490706] ehci_hcd 0000:00:1a.7: debug port 1
[ 3.491659] isapnp: Scanning for PnP cards...
[ 3.494604] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[ 3.494633] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf3404800
[ 3.508021] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[ 3.508236] hub 1-0:1.0: USB hub found
[ 3.508244] hub 1-0:1.0: 4 ports detected
[ 3.508361] alloc irq_desc for 23 on node -1
[ 3.508364] alloc kstat_irqs on node -1
[ 3.508374] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 3.508398] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 3.508403] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 3.508456] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[ 3.508498] ehci_hcd 0000:00:1d.7: debug port 1
[ 3.512395] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[ 3.512415] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf3404c00
[ 3.528022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[ 3.528170] hub 2-0:1.0: USB hub found
[ 3.528176] hub 2-0:1.0: 6 ports detected
[ 3.528288] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 3.528312] uhci_hcd: USB Universal Host Controller Interface driver
[ 3.528364] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3.528373] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 3.528378] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[ 3.528424] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[ 3.528469] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[ 3.528638] hub 3-0:1.0: USB hub found
[ 3.528645] hub 3-0:1.0: 2 ports detected
[ 3.528746] alloc irq_desc for 21 on node -1
[ 3.528749] alloc kstat_irqs on node -1
[ 3.528755] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 3.528764] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 3.528768] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[ 3.528815] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[ 3.528859] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[ 3.529021] hub 4-0:1.0: USB hub found
[ 3.529027] hub 4-0:1.0: 2 ports detected
[ 3.529117] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 3.529126] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 3.529130] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 3.529183] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[ 3.529214] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[ 3.529382] hub 5-0:1.0: USB hub found
[ 3.529387] hub 5-0:1.0: 2 ports detected
[ 3.529474] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 3.529483] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 3.529488] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 3.529536] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[ 3.529581] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[ 3.529746] hub 6-0:1.0: USB hub found
[ 3.529752] hub 6-0:1.0: 2 ports detected
[ 3.529842] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 3.529850] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 3.529855] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 3.529906] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[ 3.529937] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[ 3.530102] hub 7-0:1.0: USB hub found
[ 3.530108] hub 7-0:1.0: 2 ports detected
[ 3.530281] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 3.532514] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 3.532522] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 3.532612] mice: PS/2 mouse device common for all mice
[ 3.532816] rtc_cmos 00:07: RTC can wake from S4
[ 3.532870] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[ 3.532905] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[ 3.533052] device-mapper: uevent: version 1.0.3
[ 3.533202] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[ 3.533303] device-mapper: multipath: version 1.1.1 loaded
[ 3.533307] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 3.533464] EISA: Probing bus 0 at eisa.0
[ 3.533472] Cannot allocate resource for EISA slot 1
[ 3.533475] Cannot allocate resource for EISA slot 2
[ 3.533478] Cannot allocate resource for EISA slot 3
[ 3.533481] Cannot allocate resource for EISA slot 4
[ 3.533504] EISA: Detected 0 cards.
[ 3.533696] cpuidle: using governor ladder
[ 3.533850] cpuidle: using governor menu
[ 3.534311] TCP cubic registered
[ 3.534502] NET: Registered protocol family 10
[ 3.535034] lo: Disabled Privacy Extensions
[ 3.535387] NET: Registered protocol family 17
[ 3.536150] Using IPI No-Shortcut mode
[ 3.536258] PM: Resume from disk failed.
[ 3.536274] registered taskstats version 1
[ 3.536700] Magic number: 7:847:226
[ 3.536802] rtc_cmos 00:07: setting system clock to 2011-08-20 11:13:25 UTC (1313838805)
[ 3.536807] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 3.536809] EDD information not available.
[ 3.568358] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[ 3.663821] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WG02, max UDMA/33
[ 3.676298] ata1.00: configured for UDMA/33
[ 3.820038] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 3.846279] isapnp: No Plug & Play device found
[ 3.849571] scsi 0:0:0:0: CD-ROM HL-DT-ST DVDRAM GSA-T20N WG02 PQ: 0 ANSI: 5
[ 3.853583] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[ 3.853589] Uniform CD-ROM driver Revision: 3.20
[ 3.853779] sr 0:0:0:0: Attached scsi CD-ROM sr0
[ 3.853860] sr 0:0:0:0: Attached scsi generic sg0 type 5
[ 3.853943] Freeing unused kernel memory: 684k freed
[ 3.854443] Write protecting the kernel text: 4932k
[ 3.854520] Write protecting the kernel read-only data: 1976k
[ 3.883620] udev[92]: starting version 163
[ 4.017619] ACPI: Battery Slot [BAT0] (battery present)
[ 4.024692] Linux agpgart interface v0.103
[ 4.067270] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[ 4.068248] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[ 4.080060] usb 1-4: new high speed USB device using ehci_hcd and address 3
[ 4.091394] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 4.091425] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4.091484] r8169 0000:02:00.0: setting latency timer to 64
[ 4.091567] alloc irq_desc for 43 on node -1
[ 4.091570] alloc kstat_irqs on node -1
[ 4.091590] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[ 4.100908] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[ 4.100944] ahci 0000:00:1f.2: version 3.0
[ 4.100966] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 4.101022] alloc irq_desc for 44 on node -1
[ 4.101025] alloc kstat_irqs on node -1
[ 4.101040] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[ 4.101123] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[ 4.101128] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[ 4.101136] ahci 0000:00:1f.2: setting latency timer to 64
[ 4.110633] r8169 0000:02:00.0: eth0: RTL8101e at 0xf8036000, 00:03:25:41:38:a9, XID 14000000 IRQ 43
[ 4.118949] scsi2 : ahci
[ 4.120810] scsi3 : ahci
[ 4.120922] scsi4 : ahci
[ 4.121214] ata3: SATA max UDMA/133 abar m2048@0xf3404000 port 0xf3404100 irq 44
[ 4.121220] ata4: SATA max UDMA/133 abar m2048@0xf3404000 port 0xf3404180 irq 44
[ 4.121225] ata5: SATA max UDMA/133 abar m2048@0xf3404000 port 0xf3404200 irq 44
[ 4.139396] [drm] Initialized drm 1.1.0 20060810
[ 4.229659] Initializing USB Mass Storage driver...
[ 4.229808] scsi5 : usb-storage 1-4:1.0
[ 4.229928] usbcore: registered new interface driver usb-storage
[ 4.229931] USB Mass Storage support registered.
[ 4.385085] usb 2-4: new high speed USB device using ehci_hcd and address 3
[ 4.440068] ata5: SATA link down (SStatus 0 SControl 300)
[ 4.440103] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4.440133] ata4: SATA link down (SStatus 0 SControl 300)
[ 4.441211] ata3.00: unexpected _GTF length (8)
[ 4.441563] ata3.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
[ 4.441570] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[ 4.442866] ata3.00: unexpected _GTF length (8)
[ 4.443258] ata3.00: configured for UDMA/100
[ 4.457313] scsi 2:0:0:0: Direct-Access ATA Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[ 4.457517] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 4.457537] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[ 4.457632] sd 2:0:0:0: [sda] Write Protect is off
[ 4.457637] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4.457678] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4.458055] sda:
[ 4.532856] scsi6 : usb-storage 2-4:1.0
[ 4.776045] usb 5-1: new low speed USB device using uhci_hcd and address 2
[ 4.879727] sda1 sda2
[ 4.880186] sd 2:0:0:0: [sda] Attached SCSI disk
[ 4.913838] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4.913846] i915 0000:00:02.0: setting latency timer to 64
[ 4.945896] alloc irq_desc for 45 on node -1
[ 4.945901] alloc kstat_irqs on node -1
[ 4.945912] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[ 4.945927] [drm] set up 7M of stolen space
[ 4.967623] usbcore: registered new interface driver hiddev
[ 4.982963] input: Generic USB K/B as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input5
[ 4.983069] generic-usb 0003:13BA:0017.0001: input,hidraw0: USB HID v1.10 Keyboard [Generic USB K/B] on usb-0000:00:1d.0-1/input0
[ 5.002189] input: Generic USB K/B as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1/input/input6
[ 5.002470] generic-usb 0003:13BA:0017.0002: input,hidraw1: USB HID v1.10 Mouse [Generic USB K/B] on usb-0000:00:1d.0-1/input1
[ 5.002700] usbcore: registered new interface driver usbhid
[ 5.002704] usbhid: USB HID core driver
[ 5.061178] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[ 5.061494] [drm] initialized overlay support
[ 5.239201] scsi 5:0:0:0: CD-ROM ASUS SDR-08B1-U 1.00 PQ: 0 ANSI: 0
[ 5.253552] sr1: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda pop-up
[ 5.254244] sr 5:0:0:0: Attached scsi CD-ROM sr1
[ 5.255257] sr 5:0:0:0: Attached scsi generic sg2 type 5
[ 5.365041] Skipping EDID probe due to cached edid
[ 5.542622] scsi 6:0:0:0: Direct-Access Generic- Multi-Card 1.00 PQ: 0 ANSI: 0 CCS
[ 5.543390] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 5.551351] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 5.789474] Console: switching to colour frame buffer device 160x50
[ 5.794661] fb0: inteldrmfb frame buffer device
[ 5.794663] drm: registered panic notifier
[ 5.794667] Slow work thread pool: Starting up
[ 5.794805] Slow work thread pool: Ready
[ 5.794851] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[ 5.796336] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[ 5.802827] acpi device:07: registered as cooling_device2
[ 5.803225] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[ 5.803293] ACPI: Video Device [GFX0] (multi-head: yes rom: no post: no)
[ 5.803332] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[ 6.000127] Skipping EDID probe due to cached edid
[ 6.174094] Btrfs loaded
[ 6.181753] xor: automatically using best checksumming function: pIII_sse
[ 6.200012] pIII_sse : 5487.000 MB/sec
[ 6.200017] xor: using function: pIII_sse (5487.000 MB/sec)
[ 6.203723] device-mapper: dm-raid45: initialized v0.2594b
[ 11.279224] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 11.379899] ISO 9660 Extensions: RRIP_1991A
[ 11.620514] aufs 2-standalone.tree-35-rcN-20100705
[ 11.712634] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[ 75.373609] udev[1380]: starting version 163
[ 80.760631] Linux video capture interface: v2.00
[ 80.948297] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b027)
[ 80.960758] cfg80211: Calling CRDA to update world regulatory domain
[ 80.966726] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input8
[ 80.968392] usbcore: registered new interface driver uvcvideo
[ 80.968397] USB Video Class driver (v0.1.0)
[ 81.524420] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0/0x0
[ 81.567103] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[ 82.783993] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 82.783998] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[ 82.784365] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 82.784382] iwl3945 0000:04:00.0: setting latency timer to 64
[ 82.873442] iwl3945 0000:04:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[ 82.873450] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[ 82.873992] alloc irq_desc for 46 on node -1
[ 82.873996] alloc kstat_irqs on node -1
[ 82.874033] iwl3945 0000:04:00.0: irq 46 for MSI/MSI-X
[ 84.372851] phy0: Selected rate control algorithm 'iwl-3945-rs'
[ 85.862836] cfg80211: World regulatory domain updated:
[ 85.862842] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 85.862846] (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 85.862851] (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 85.862855] (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 85.862859] (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 85.862863] (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 86.138917] alloc irq_desc for 22 on node -1
[ 86.138921] alloc kstat_irqs on node -1
[ 86.138932] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 86.139214] alloc irq_desc for 47 on node -1
[ 86.139218] alloc kstat_irqs on node -1
[ 86.139234] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[ 86.139282] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 86.143582] r8169 0000:02:00.0: eth0: link down
[ 86.143884] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 86.605899] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[ 86.606203] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[ 86.998779] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
[ 87.106926] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 88.272656] lp: driver loaded but no devices found
[ 88.573817] ppdev: user-space parallel port driver
[ 100.188204] Skipping EDID probe due to cached edid
[ 100.204110] Skipping EDID probe due to cached edid
[ 114.133071] Skipping EDID probe due to cached edid
[ 114.160074] Skipping EDID probe due to cached edid
[ 114.608073] Skipping EDID probe due to cached edid
[ 114.632065] Skipping EDID probe due to cached edid
[ 170.929315] Skipping EDID probe due to cached edid
[ 170.945273] Skipping EDID probe due to cached edid
[ 173.328776] Skipping EDID probe due to cached edid
[ 173.352092] Skipping EDID probe due to cached edid
[ 173.401064] Skipping EDID probe due to cached edid
[ 173.417065] Skipping EDID probe due to cached edid
[ 180.793074] Skipping EDID probe due to cached edid
[ 187.252072] Skipping EDID probe due to cached edid
[ 337.806280] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 338.004104] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 338.204071] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 338.404064] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 349.433438] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 349.632149] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 349.832031] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 350.033043] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 361.102035] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 361.300140] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 361.500150] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 361.700150] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 372.726884] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 372.924181] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 373.124158] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 373.324180] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 384.418256] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 384.616049] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 384.817147] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 385.017140] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 462.890640] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 463.089138] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 463.288083] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 463.488174] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 474.583847] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 474.780130] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 474.980165] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 475.180185] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 486.274083] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 486.472172] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 486.672143] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 486.872176] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 497.921378] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 498.120092] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 498.320192] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 498.520190] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 509.580245] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 509.780150] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 509.980169] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 510.180172] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 809.761116] Skipping EDID probe due to cached edid
[ 3337.930831] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 3338.132169] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 3338.332138] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 3338.532158] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 3349.555734] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 3349.752169] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 3349.952162] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 3350.152171] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 3361.243801] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 3361.440955] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 3361.640072] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 3361.840053] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 3372.916080] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 3373.116167] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 3373.316148] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 3373.516184] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 3384.602959] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[ 3384.800145] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[ 3385.000160] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[ 3385.200187] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[ 3993.984119] Skipping EDID probe due to cached edid
[13513.060188] Skipping EDID probe due to cached edid
[24465.208134] Skipping EDID probe due to cached edid
[41828.388186] Skipping EDID probe due to cached edid
[43132.447716] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43132.644161] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43132.844161] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43133.044145] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43144.092712] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43144.292151] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43144.492173] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43144.692144] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43155.807515] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43156.004177] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43156.204170] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43156.404187] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43167.477781] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43167.676162] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43167.876186] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43168.076151] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43179.218350] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43179.416162] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43179.616162] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43179.816149] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43190.866938] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43191.064154] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43191.264182] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43191.464176] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43247.251232] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43247.449051] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43247.649120] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43247.849061] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43258.899119] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43259.096162] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43259.296169] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43259.496168] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43270.611872] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43270.808187] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43271.008171] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43271.208204] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43282.330598] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43282.528163] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43282.728157] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43282.928147] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43294.024918] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43294.224163] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43294.424147] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43294.624185] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43305.696415] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43305.897056] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43306.096063] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43306.296160] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43476.366753] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43476.564117] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43476.764126] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43476.964172] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43487.990838] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43488.188187] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43488.388159] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43488.588122] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43499.683376] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43499.880057] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43500.080063] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43500.280077] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43511.375938] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43511.572185] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43511.772170] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43511.972120] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43523.071663] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43523.268120] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43523.468178] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43523.669059] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43534.725656] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43534.924170] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43535.124132] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43535.324141] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43537.692269] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43537.892172] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43538.092148] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43538.292159] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43549.364371] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43549.564186] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43549.764163] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43549.964177] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43561.062196] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43561.260071] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43561.460162] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43561.660161] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43572.709987] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43572.908153] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43573.108173] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43573.308139] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43584.408421] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43584.608164] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43584.808148] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43585.008160] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43596.057021] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43596.256162] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43596.456156] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43596.656159] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43607.725801] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43607.924189] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43608.124153] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43608.324161] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43619.415605] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43619.612149] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43619.812147] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43620.012148] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43631.109046] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43631.308162] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43631.508167] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43631.708189] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43642.821466] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43643.020187] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43643.220149] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43643.420133] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43654.492198] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43654.692175] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43654.892159] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43655.092066] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43656.800040] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43657.000159] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43657.200191] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43657.400131] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43668.444963] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43668.644158] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43668.844167] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43669.044143] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43680.166616] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43680.364144] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43680.564158] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43680.765058] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43691.837231] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43692.036150] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43692.236160] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43692.436160] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43703.530622] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43703.728159] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43703.928141] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43704.128166] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43715.178850] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43715.376081] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43715.576059] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43715.776183] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43726.915091] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43727.112141] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43727.312180] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43727.512165] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43738.638767] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43738.837064] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43739.037142] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43739.237058] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43750.332592] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43750.532129] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43750.732159] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43750.932165] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43762.071672] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43762.268161] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43762.468147] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43762.668143] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[43773.719958] wlan0: authenticate with 00:1f:b3:75:40:49 (try 1)
[43773.916056] wlan0: authenticate with 00:1f:b3:75:40:49 (try 2)
[43774.116077] wlan0: authenticate with 00:1f:b3:75:40:49 (try 3)
[43774.316167] wlan0: authentication with 00:1f:b3:75:40:49 timed out
[44301.448200] usb 2-2: new high speed USB device using ehci_hcd and address 4
[44301.583465] scsi7 : usb-storage 2-2:1.0
[44302.580979] scsi 7:0:0:0: Direct-Access CBM USB 2.0 5.00 PQ: 0 ANSI: 2
[44302.582147] sd 7:0:0:0: Attached scsi generic sg4 type 0
[44302.582986] sd 7:0:0:0: [sdc] 2009088 512-byte logical blocks: (1.02 GB/981 MiB)
[44302.583974] sd 7:0:0:0: [sdc] Write Protect is off
[44302.583981] sd 7:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[44302.583987] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[44302.587914] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[44302.587930] sdc: sdc1
[44302.591413] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[44302.591423] sd 7:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by bkratz on 2011-08-21
I believe this may be useful too

ifconfig

---

### Post by wojox on 2011-08-21
> **bkratz said:**
> I believe this may be useful too

ifconfig

True or iwconfig since we need wireless. :P

Can you login into your router from another computer and check Settings -> Lan -> Wireless

Next to Authentication Type choose the drop down box and select "WPA-PSK" and save.

Get back on Ubuntu and run:

```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```

---

### Post by cdmccreary on 2011-08-28
attached files are screenshot from att router.  I remove all blocked MACs


ifconfig on working wireless FRYES router

```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:41:38:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4496 (4.4 KB)  TX bytes:4496 (4.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:3f:98:78  
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe3f:9878/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2204479 (2.2 MB)  TX bytes:373936 (373.9 KB)

ubuntu@ubuntu:~$ 
```

ifconfig with att wireless selected

```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:41:38:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4496 (4.4 KB)  TX bytes:4496 (4.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:3f:98:78  
          inet6 addr: fe80::21b:77ff:fe3f:9878/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7092875 (7.0 MB)  TX bytes:813540 (813.5 KB)

ubuntu@ubuntu:~$ 

```

sudo ifconfig wlan0 up

```
all this did was bring up the GUI for the password / when entered (again) does not work
```


sudo iwlist wlan0 scan


```
ubuntu@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:26:5A:FF:DE:87
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"FR-54RTR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001621c1dbe6
                    Extra: Last beacon: 1576ms ago
                    IE: Unknown: 000846522D3534525452
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD9A0050F204104A0001101044000102103B000103104700100000000000001000000000265AFFDE8710210004467279731023000B4672797320526F757465721024000846522D3534525452104200046E6F6E651054000800060050F204000110110015467279732053797374656D732046522D3534525452100800020086103C000103104900140024E26002000101600000020001600100020001
          Cell 02 - Address: 00:21:91:0E:36:DB
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009d7664f180
                    Extra: Last beacon: 1640ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: DD1E00904C334E101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050400000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 05043D640000
                    IE: Unknown: DD050050F20502
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: 00:1F:B3:75:40:49
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"2WIRE303"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004e57e818
                    Extra: Last beacon: 1528ms ago
                    IE: Unknown: 00083257495245333033
                    IE: Unknown: 010882848B8C12969824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C

ubuntu@ubuntu:~$ 

```

---

### Post by bkratz on 2011-08-28
Probably a stupid question--but did you add your mac address to the filter shown in your pdf?

---

### Post by cdmccreary on 2011-08-28
No. I did not add it and it was not there before I removed the rest of the MAC addresses filter. 
 
The router added one address all by itself after I deleted them. 8-[
 
The attached PDF shows the MAC addresses in the list on the router config [http://192.168.1.254](http://192.168.1.254) ...
 
But I will check one more time. I will remove the MAC filtering altogether and see if that passes through to the router. I dont see the MAC address on the allowed list.
 
It does not seem that the router is adding the MAC addresses of the Linux machines.

---

### Post by cdmccreary on 2011-08-29
I removed MAC filtering from the router. There is no change in the situation.

I have used two identical Gateway laptops with Ubuntu 10.10.  They all give the same results.

They access the Frys router not ATT 2WIRE.  Only with Windows.

It seemed the MAC address would not enter the allowed list for MAC filtering.  I am going to try manually entering it.

Alas no change. It no work...

---

