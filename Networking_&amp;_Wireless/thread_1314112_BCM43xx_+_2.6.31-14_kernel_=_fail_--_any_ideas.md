---
title: "BCM43xx + 2.6.31-14 kernel = fail -- any ideas?"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by jamaisvu on 2009-11-04
I've just updated the last of my computers (you know, the old one that always springs some sort of nasty surprise on you -- I'm sure everyone has one) to Karmic. And the BCM4303 wireless card doesn't want to play with the new kernel.

I've run:

```
james@james-desktop:~$ sudo aptitude reinstall bcmwl-kernel-source
[sudo] password for james: 
Reading package lists... Wedi Gorffen
Building dependency tree             
Reading state information... Wedi Gorffen
Reading extended state information       
Initializing package states... Wedi Gorffen
The following packages will be REINSTALLED:
  bcmwl-kernel-source 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
Need to get 0B/618kB of archives. After unpacking 0B will be used.
Writing extended state information... Wedi Gorffen
(Reading database ... 399804 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.10.91.9+bdcom-0ubuntu4 (using .../bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.10.91.9+bdcom-0ubuntu4) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
Reading package lists... Wedi Gorffen             
Building dependency tree             
Reading state information... Wedi Gorffen
Reading extended state information       
Initializing package states... Wedi Gorffen
```

Which looked like a good result to me. So I followed that with:

```
james@james-desktop:~$ sudo reboot now
```

But when it rebooted, it still didn't work. Here's the output of dmesg:

```
james@james-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003dff0000 (usable)
[    0.000000]  BIOS-e820: 000000003dff0000 - 000000003dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003dff3000 - 000000003e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3dff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03E000000 mask FFE000000 uncachable
[    0.000000]   2 base 0D0000000 mask FF8000000 write-combining
[    0.000000]   3 base 0D0000000 mask FF8000000 write-combining
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
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003dff0000 (usable)
[    0.000000]  modified: 000000003dff0000 - 000000003dff3000 (ACPI NVS)
[    0.000000]  modified: 000000003dff3000 - 000000003e000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37869000 - 37fef929
[    0.000000] Allocated new RAMDISK: 008ad000 - 01033929
[    0.000000] Move RAMDISK from 0000000037869000 - 0000000037fef928 to 008ad000 - 01033928
[    0.000000] ACPI: RSDP 000f8250 00014 (v00 VT8375)
[    0.000000] ACPI: RSDT 3dff3000 0002C (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 3dff3040 00074 (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 3dff30c0 039ED (v01 VT8375 AWRDACPI 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 3dff0000 00040
[    0.000000] ACPI: APIC 3dff6ac0 0005A (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 103MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac0b2]              BRK ==> [00008a9000 - 00008ac0b2]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 0001033929]      NEW RAMDISK ==> [00008ad000 - 0001033929]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f6750] f6750
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003dff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003dff0
[    0.000000] On node 0 totalpages: 253823
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1034200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 208 pages used for memmap
[    0.000000]   HighMem zone: 26402 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3e000000 (gap: 3e000000:c0c00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c17f8000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 251839
[    0.000000] Kernel command line: root=UUID=bb004439-1fad-4b3c-b3be-b978a90d2de1 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5078400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003dff0)
[    0.000000] Memory: 985556k/1015744k available (4565k kernel code, 29348k reserved, 2143k data, 540k init, 106440k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1533.115 MHz processor.
[    0.001430] Console: colour VGA+ 80x25
[    0.001437] console [tty0] enabled
[    0.004019] Calibrating delay loop (skipped), value calculated using timer frequency.. 3066.23 BogoMIPS (lpj=6132460)
[    0.004068] Security Framework initialized
[    0.004130] AppArmor: AppArmor initialized
[    0.004144] Mount-cache hash table entries: 512
[    0.004421] Initializing cgroup subsys ns
[    0.004430] Initializing cgroup subsys cpuacct
[    0.004436] Initializing cgroup subsys memory
[    0.004452] Initializing cgroup subsys freezer
[    0.004456] Initializing cgroup subsys net_cls
[    0.004479] CPU: CLK_CTL MSR was 60031223. Reprogramming to 20031223
[    0.004485] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004490] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004498] mce: CPU supports 4 MCE banks
[    0.004534] Performance Counters: AMD PMU driver.
[    0.004545] ... version:                 0
[    0.004548] ... bit width:               48
[    0.004551] ... generic counters:        4
[    0.004554] ... value mask:              0000ffffffffffff
[    0.004557] ... max period:              00007fffffffffff
[    0.004560] ... fixed-purpose counters:  0
[    0.004563] ... counter mask:            000000000000000f
[    0.004572] Checking 'hlt' instruction... OK.
[    0.020875] SMP alternatives: switching to UP code
[    0.028048] Freeing SMP alternatives: 19k freed
[    0.028121] ACPI: Core revision 20090521
[    0.040805] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.082154] CPU0: AMD Athlon(tm) XP 1800+ stepping 01
[    0.084001] Brought up 1 CPUs
[    0.084001] Total of 1 processors activated (3066.23 BogoMIPS).
[    0.084001] CPU0 attaching NULL sched-domain.
[    0.084001] Booting paravirtualized kernel on bare hardware
[    0.084001] regulator: core version 0.5
[    0.084001] Time: 13:33:52  Date: 11/04/09
[    0.084001] NET: Registered protocol family 16
[    0.084001] EISA bus registered
[    0.084001] ACPI: bus type pci registered
[    0.090208] PCI: PCI BIOS revision 2.10 entry at 0xfbd30, last bus=1
[    0.090212] PCI: Using configuration type 1 for base access
[    0.091748] bio: create slab <bio-0> at 0
[    0.092517] ACPI: EC: Look up EC in DSDT
[    0.099062] ACPI: Interpreter enabled
[    0.099075] ACPI: (supports S0 S1 S4 S5)
[    0.099109] ACPI: Using IOAPIC for interrupt routing
[    0.104318] ACPI: No dock devices found.
[    0.104497] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.104589] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.104691] pci 0000:00:01.0: supports D1
[    0.104730] pci 0000:00:06.0: reg 10 32bit mmio: [0xe0100000-0xe0101fff]
[    0.104772] pci 0000:00:06.0: supports D1 D2
[    0.104776] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.104782] pci 0000:00:06.0: PME# disabled
[    0.104844] pci 0000:00:10.0: reg 20 io port: [0xa000-0xa01f]
[    0.104870] pci 0000:00:10.0: supports D1 D2
[    0.104873] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.104879] pci 0000:00:10.0: PME# disabled
[    0.104930] pci 0000:00:10.1: reg 20 io port: [0xa400-0xa41f]
[    0.104956] pci 0000:00:10.1: supports D1 D2
[    0.104960] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.104965] pci 0000:00:10.1: PME# disabled
[    0.105016] pci 0000:00:10.2: reg 20 io port: [0xa800-0xa81f]
[    0.105042] pci 0000:00:10.2: supports D1 D2
[    0.105046] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105051] pci 0000:00:10.2: PME# disabled
[    0.105089] pci 0000:00:10.3: reg 10 32bit mmio: [0xe0102000-0xe01020ff]
[    0.105132] pci 0000:00:10.3: supports D1 D2
[    0.105135] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105140] pci 0000:00:10.3: PME# disabled
[    0.105208] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.105219] pci 0000:00:11.0: quirk: region 4000-407f claimed by vt8235 PM
[    0.105225] pci 0000:00:11.0: quirk: region 5000-500f claimed by vt8235 SMB
[    0.105291] pci 0000:00:11.1: reg 20 io port: [0xac00-0xac0f]
[    0.105359] pci 0000:00:11.5: reg 10 io port: [0xb000-0xb0ff]
[    0.105404] pci 0000:00:11.5: supports D1 D2
[    0.105442] pci 0000:00:12.0: reg 10 io port: [0xb400-0xb4ff]
[    0.105450] pci 0000:00:12.0: reg 14 32bit mmio: [0xe0103000-0xe01030ff]
[    0.105489] pci 0000:00:12.0: supports D1 D2
[    0.105493] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105498] pci 0000:00:12.0: PME# disabled
[    0.105559] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe007ffff]
[    0.105567] pci 0000:01:00.0: reg 14 32bit mmio: [0xd8000000-0xdfffffff]
[    0.105588] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.105607] pci 0000:01:00.0: supports D1 D2
[    0.105647] pci 0000:00:01.0: bridge 32bit mmio: [0xe0000000-0xe00fffff]
[    0.105654] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.105663] pci_bus 0000:00: on NUMA node 0
[    0.105670] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.124478] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.124711] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[    0.124956] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[    0.125201] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.125438] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.125665] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.125923] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.126163] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[    0.126527] SCSI subsystem initialized
[    0.126728] libata version 3.00 loaded.
[    0.126901] usbcore: registered new interface driver usbfs
[    0.126930] usbcore: registered new interface driver hub
[    0.126980] usbcore: registered new device driver usb
[    0.127213] ACPI: WMI: Mapper loaded
[    0.127217] PCI: Using ACPI for IRQ routing
[    0.127474] Bluetooth: Core ver 2.15
[    0.127530] NET: Registered protocol family 31
[    0.127533] Bluetooth: HCI device and connection manager initialized
[    0.127539] Bluetooth: HCI socket layer initialized
[    0.127543] NetLabel: Initializing
[    0.127545] NetLabel:  domain hash size = 128
[    0.127548] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.127576] NetLabel:  unlabeled traffic allowed by default
[    0.131829] pnp: PnP ACPI init
[    0.131888] ACPI: bus type pnp registered
[    0.136500] pnp: PnP ACPI: found 13 devices
[    0.136505] ACPI: ACPI bus type pnp unregistered
[    0.136513] PnPBIOS: Disabled by ACPI PNP
[    0.136542] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.136547] system 00:02: ioport range 0x294-0x297 has been reserved
[    0.171328] AppArmor: AppArmor Filesystem Enabled
[    0.171365] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.171369] pci 0000:00:01.0:   IO window: disabled
[    0.171378] pci 0000:00:01.0:   MEM window: 0xe0000000-0xe00fffff
[    0.171384] pci 0000:00:01.0:   PREFETCH window: 0xd8000000-0xdfffffff
[    0.171403] pci 0000:00:01.0: setting latency timer to 64
[    0.171415] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.171419] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.171424] pci_bus 0000:01: resource 1 mem: [0xe0000000-0xe00fffff]
[    0.171428] pci_bus 0000:01: resource 2 pref mem [0xd8000000-0xdfffffff]
[    0.171506] NET: Registered protocol family 2
[    0.171670] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.172391] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.175911] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.177758] TCP: Hash tables configured (established 131072 bind 65536)
[    0.177766] TCP reno registered
[    0.178010] NET: Registered protocol family 1
[    0.178182] Trying to unpack rootfs image as initramfs...
[    0.511399] Freeing initrd memory: 7706k freed
[    0.534804] cpufreq-nforce2: No nForce2 chipset.
[    0.534859] Scanning for low memory corruption every 60 seconds
[    0.535115] audit: initializing netlink socket (disabled)
[    0.535158] type=2000 audit(1257341632.531:1): initialized
[    0.547430] highmem bounce pool size: 64 pages
[    0.547442] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.549808] VFS: Disk quotas dquot_6.5.2
[    0.549910] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.550792] fuse init (API version 7.12)
[    0.550925] msgmni has been set to 1732
[    0.551302] alg: No test for stdrng (krng)
[    0.551324] io scheduler noop registered
[    0.551328] io scheduler anticipatory registered
[    0.551331] io scheduler deadline registered
[    0.551402] io scheduler cfq registered (default)
[    0.551425] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.551515] pci 0000:01:00.0: Boot video device
[    0.551640] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.551678] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.551904] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.551913] ACPI: Power Button [PWRF]
[    0.552037] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.552043] ACPI: Power Button [PWRB]
[    0.552122] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.552130] ACPI: Sleep Button [SLPB]
[    0.552200] fan PNP0C0B:00: registered as cooling_device0
[    0.552208] ACPI: Fan [FAN] (on)
[    0.552569] Marking TSC unstable due to TSC halts in idle
[    0.552606] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.552633] processor LNXCPU:00: registered as cooling_device1
[    0.555670] thermal LNXTHERM:01: registered as thermal_zone0
[    0.555682] ACPI: Thermal Zone [THRM] (49 C)
[    0.555914] isapnp: Scanning for PnP cards...
[    0.556634] Switched to high resolution mode on CPU 0
[    0.909664] isapnp: No Plug & Play device found
[    0.911383] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.911544] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.911644] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.912027] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.912167] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.913799] brd: module loaded
[    0.914516] loop: module loaded
[    0.914700] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.915538] pata_via 0000:00:11.1: version 0.3.4
[    0.916138] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.916143] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.916157]   alloc irq_desc for 20 on node -1
[    0.916161]   alloc kstat_irqs on node -1
[    0.916178] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.916549] scsi0 : pata_via
[    0.916762] scsi1 : pata_via
[    0.920717] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xac00 irq 14
[    0.920723] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xac08 irq 15
[    0.921331] Fixed MDIO Bus: probed
[    0.921391] PPP generic driver version 2.4.2
[    0.921617] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.922000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[    0.922005] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    0.922014]   alloc irq_desc for 21 on node -1
[    0.922018]   alloc kstat_irqs on node -1
[    0.922030] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.922063] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.922173] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.922275] ehci_hcd 0000:00:10.3: irq 21, io mem 0xe0102000
[    0.932015] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.932168] usb usb1: configuration #1 chosen from 1 choice
[    0.932229] hub 1-0:1.0: USB hub found
[    0.932250] hub 1-0:1.0: 6 ports detected
[    0.932356] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.932397] uhci_hcd: USB Universal Host Controller Interface driver
[    0.932537] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.932554] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.932614] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.932646] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000a000
[    0.932779] usb usb2: configuration #1 chosen from 1 choice
[    0.932819] hub 2-0:1.0: USB hub found
[    0.932836] hub 2-0:1.0: 2 ports detected
[    0.932911] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.932921] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.932983] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.933008] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000a400
[    0.933139] usb usb3: configuration #1 chosen from 1 choice
[    0.933193] hub 3-0:1.0: USB hub found
[    0.933208] hub 3-0:1.0: 2 ports detected
[    0.933283] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.933294] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.933339] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.933363] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000a800
[    0.933501] usb usb4: configuration #1 chosen from 1 choice
[    0.933539] hub 4-0:1.0: USB hub found
[    0.933555] hub 4-0:1.0: 2 ports detected
[    0.933713] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.934112] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.934129] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.934240] mice: PS/2 mouse device common for all mice
[    0.934424] rtc_cmos 00:04: RTC can wake from S4
[    0.934489] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.934526] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.934736] device-mapper: uevent: version 1.0.3
[    0.934955] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.935114] device-mapper: multipath: version 1.1.0 loaded
[    0.935120] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.935358] EISA: Probing bus 0 at eisa.0
[    0.935383] Cannot allocate resource for EISA slot 4
[    0.935386] Cannot allocate resource for EISA slot 5
[    0.935402] EISA: Detected 0 cards.
[    0.935554] cpuidle: using governor ladder
[    0.935624] cpuidle: using governor menu
[    0.936450] TCP cubic registered
[    0.936677] NET: Registered protocol family 10
[    0.937335] lo: Disabled Privacy Extensions
[    0.937817] NET: Registered protocol family 17
[    0.937856] Bluetooth: L2CAP ver 2.13
[    0.937859] Bluetooth: L2CAP socket layer initialized
[    0.937864] Bluetooth: SCO (Voice Link) ver 0.6
[    0.937867] Bluetooth: SCO socket layer initialized
[    0.937979] Bluetooth: RFCOMM TTY layer initialized
[    0.937984] Bluetooth: RFCOMM socket layer initialized
[    0.937987] Bluetooth: RFCOMM ver 1.11
[    0.938043] powernow-k8: Processor cpuid 681 not supported
[    0.938092] Using IPI No-Shortcut mode
[    0.938238] PM: Resume from disk failed.
[    0.938267] registered taskstats version 1
[    0.938428]   Magic number: 1:737:583
[    0.938632] rtc_cmos 00:04: setting system clock to 2009-11-04 13:33:53 UTC (1257341633)
[    0.938640] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.938643] EDD information not available.
[    0.964927] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.149024] ata1.00: ATA-7: ST3160215A, 3.AAC, max UDMA/100
[    1.149029] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.149438] ata1.01: ATA-5: ExcelStor Technology J240, VA2OAF0C, max UDMA/100
[    1.149443] ata1.01: 80418240 sectors, multi 16: LBA 
[    1.215599] ata1.00: configured for UDMA/100
[    1.236603] ata1.01: configured for UDMA/100
[    1.236829] scsi 0:0:0:0: Direct-Access     ATA      ST3160215A       3.AA PQ: 0 ANSI: 5
[    1.237052] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.237159] scsi 0:0:1:0: Direct-Access     ATA      ExcelStor Techno VA2O PQ: 0 ANSI: 5
[    1.237311] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.237386] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.237476] sd 0:0:0:0: [sda] Write Protect is off
[    1.237481] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.237526] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.237768]  sda: sda1 sda2 sda3
[    1.287072] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.287091] sd 0:0:1:0: [sdb] 80418240 512-byte logical blocks: (41.1 GB/38.3 GiB)
[    1.287164] sd 0:0:1:0: [sdb] Write Protect is off
[    1.287169] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.287208] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.287401]  sdb: unknown partition table
[    1.300171] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.408397] ata2.00: ATAPI: HL-DT-STDVD-ROM GDR8161B, 0100, max UDMA/33
[    1.408440] ata2.01: ATAPI: SONY CD-RW CRX1611, TYS7, max MWDMA2
[    1.424276] ata2.00: configured for UDMA/33
[    1.440274] ata2.01: configured for MWDMA2
[    1.447177] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8161B 0100 PQ: 0 ANSI: 5
[    1.459737] sr0: scsi3-mmc drive: 20x/48x cd/rw xa/form2 cdda tray
[    1.459743] Uniform CD-ROM driver Revision: 3.20
[    1.459929] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.460067] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    1.460775] scsi 1:0:1:0: CD-ROM            SONY     CD-RW CRX1611    TYS7 PQ: 0 ANSI: 5
[    1.464049] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.464168] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.464239] sr 1:0:1:0: Attached scsi generic sg3 type 5
[    1.464286] Freeing unused kernel memory: 540k freed
[    1.465617] Write protecting the kernel text: 4568k
[    1.465667] Write protecting the kernel read-only data: 1836k
[    1.809296] Linux agpgart interface v0.103
[    1.829980] agpgart: Detected VIA PM266/KM266 chipset
[    1.844830] Floppy drive(s): fd0 is 1.44M
[    1.864126] FDC 0 is a post-1991 82077
[    1.999486] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
[    1.999696] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.999703] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    2.000289] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[    2.000294] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    2.000307]   alloc irq_desc for 23 on node -1
[    2.000311]   alloc kstat_irqs on node -1
[    2.000324] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    2.027265] eth0: VIA Rhine II at 0xe0103000, 00:0c:76:26:0b:8f, IRQ 23.
[    2.027980] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    3.052976] xor: automatically using best checksumming function: pIII_sse
[    3.072007]    pIII_sse  :  3224.000 MB/sec
[    3.072012] xor: using function: pIII_sse (3224.000 MB/sec)
[    3.077414] device-mapper: dm-raid45: initialized v0.2594b
[    3.563080] PM: Starting manual resume from disk
[    3.563090] PM: Resume from partition 8:2
[    3.563093] PM: Checking hibernation image.
[    3.563400] PM: Resume from disk failed.
[    3.597830] EXT4-fs (sda1): barriers enabled
[    3.615605] kjournald2 starting: pid 339, dev sda1:8, commit interval 5 seconds
[    3.615634] EXT4-fs (sda1): delayed allocation enabled
[    3.615640] EXT4-fs: file extents enabled
[    3.627926] EXT4-fs: mballoc enabled
[    3.627956] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.449580] type=1505 audit(1257341637.009:2): operation="profile_load" pid=362 name=/usr/share/gdm/guest-session/Xsession
[    4.467064] type=1505 audit(1257341637.025:3): operation="profile_load" pid=363 name=/sbin/dhclient3
[    4.467509] type=1505 audit(1257341637.025:4): operation="profile_load" pid=363 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.467764] type=1505 audit(1257341637.025:5): operation="profile_load" pid=363 name=/usr/lib/connman/scripts/dhclient-script
[    4.506616] type=1505 audit(1257341637.065:6): operation="profile_load" pid=364 name=/usr/bin/evince
[    4.514942] type=1505 audit(1257341637.073:7): operation="profile_load" pid=364 name=/usr/bin/evince-previewer
[    4.520392] type=1505 audit(1257341637.081:8): operation="profile_load" pid=364 name=/usr/bin/evince-thumbnailer
[    4.560263] type=1505 audit(1257341637.121:9): operation="profile_load" pid=366 name=/usr/lib/cups/backend/cups-pdf
[    4.560840] type=1505 audit(1257341637.121:10): operation="profile_load" pid=366 name=/usr/sbin/cupsd
[    5.992203] Adding 2000084k swap on /dev/sda2.  Priority:-1 extents:1 across:2000084k 
[    6.727643] EXT4-fs (sda1): internal journal on sda1:8
[    7.871744] udev: starting version 147
[    7.894755] kjournald starting.  Commit interval 5 seconds
[    7.895005] EXT3 FS on sda3, internal journal
[    7.895014] EXT3-fs: mounted filesystem with writeback data mode.
[   10.783323] irda_init()
[   10.783360] NET: Registered protocol family 23
[   11.156461] ip_tables: (C) 2000-2006 Netfilter Core Team
[   11.746521] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.849375] parport_pc 00:0a: reported by Plug and Play ACPI
[   11.849491] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   12.055792] lp0: using parport0 (interrupt-driven).
[   12.063488] ppdev: user-space parallel port driver
[   12.586323] psmouse serio1: ID: 10 00 64
[   12.836224] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   12.836232] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   12.836242]   alloc irq_desc for 22 on node -1
[   12.836246]   alloc kstat_irqs on node -1
[   12.836259] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   12.836427] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   13.061451] __ratelimit: 6 callbacks suppressed
[   13.061458] type=1505 audit(1257341645.621:13): operation="profile_replace" pid=757 name=/usr/share/gdm/guest-session/Xsession
[   13.065566] type=1505 audit(1257341645.625:14): operation="profile_replace" pid=758 name=/sbin/dhclient3
[   13.066022] type=1505 audit(1257341645.625:15): operation="profile_replace" pid=758 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   13.066279] type=1505 audit(1257341645.625:16): operation="profile_replace" pid=758 name=/usr/lib/connman/scripts/dhclient-script
[   13.082119] type=1505 audit(1257341645.641:17): operation="profile_replace" pid=759 name=/usr/bin/evince
[   13.091783] type=1505 audit(1257341645.649:18): operation="profile_replace" pid=759 name=/usr/bin/evince-previewer
[   13.097867] type=1505 audit(1257341645.657:19): operation="profile_replace" pid=759 name=/usr/bin/evince-thumbnailer
[   13.108704] type=1505 audit(1257341645.669:20): operation="profile_replace" pid=761 name=/usr/lib/cups/backend/cups-pdf
[   13.109285] type=1505 audit(1257341645.669:21): operation="profile_replace" pid=761 name=/usr/sbin/cupsd
[   13.113524] type=1505 audit(1257341645.673:22): operation="profile_replace" pid=762 name=/usr/sbin/mysqld-akonadi
[   13.155195] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   20.273259] eth0: link down
[   20.273671] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.313183] [drm] Initialized drm 1.1.0 20060810
[   27.316798]   alloc irq_desc for 16 on node -1
[   27.316804]   alloc kstat_irqs on node -1
[   27.316821] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.317086] [drm] Initialized savage 2.4.1 20050313 for 0000:01:00.0 on minor 0
```

And lspci:

```
james@james-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:06.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
```

And ifconfig (NB wlan0 completely absent):

```
james@james-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:26:0b:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```

I'm really at a bit of a loss. Has anyone got any ideas as to what to try next?

(Fortunately the legacy BCM43xx fwcutter driver still works with the 2.6.28-16 kernel, so at least I won't have the fun of physically moving this dinosaur to be next to an ethernet port.)

---

### Post by Ayuthia on 2009-11-04
Try installing b43-fwcutter instead.  The bcmwl-kernel-source is the proprietary driver created by Broadcom and it does not support this card.

If it does not work, try the following:
```
sudo modprobe -r b43 b43legacy ssb wl
sudo modprobe b43legacy
sudo iwlist scan
```

If it still does not work after you install b43-fwcutter (and restart), please post the results of:
```
lsmod|grep -e b43 -e ssb -e wl
lshw -C network
dmesg|grep b43
```

---

### Post by jamaisvu on 2009-11-14
> **Ayuthia said:**
> Try installing b43-fwcutter instead.  The bcmwl-kernel-source is the proprietary driver created by Broadcom and it does not support this card.

Thanks, I knew I had done something stupid and obvious. This at least means that the computer can see the card, but it still doesn't work with the 2.6.31 kernel.

> If it does not work, try the following:
```
sudo modprobe -r b43 b43legacy ssb wl
sudo modprobe b43legacy
sudo iwlist scan
```

No luck there.

> If it still does not work after you install b43-fwcutter (and restart), please post the results of:
```
lsmod|grep -e b43 -e ssb -e wl
lshw -C network
dmesg|grep b43
```

Those produce:

```
james@james-desktop:~$ lsmod|grep -e b43 -e ssb -e wl
b43legacy             117752  0 
mac80211              181236  1 b43legacy
cfg80211               93052  2 b43legacy,mac80211
led_class               4096  1 b43legacy
ssb                    35300  2 b43legacy,b44
```

```
james@james-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:17 memory:e0100000-e0101fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0c:76:26:0b:8f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.7 latency=32 maxlatency=8 mingnt=3 multicast=yes
       resources: irq:23 ioport:b400(size=256) memory:e0103000-e01030ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:06:25:23:2f:59
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
```

```
james@james-desktop:~$ dmesg|grep b43
[    1.851840] b43-pci-bridge 0000:00:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.907845] b43legacy-phy0: Broadcom 4301 WLAN found
[   20.936990] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   20.937018] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[   20.960115] b43legacy-phy0 debug: Radio initialized
[   23.231849] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   23.264312] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   23.284107] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   23.577027] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   23.692196] b43legacy-phy0 debug: Chip initialized
[   23.692634] b43legacy-phy0 debug: 30-bit DMA initialized
[   23.708838] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2B
[   23.708845] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x78
[   23.708849] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2E
[   23.708853] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x19
[   23.708915] b43legacy-phy0 debug: Wireless interface started
[   23.708945] b43legacy-phy0: Radio hardware status changed to DISABLED
[   23.708955] b43legacy-phy0 debug: Radio initialized
[   23.710804] b43legacy-phy0 debug: Adding Interface type 2
[   23.780088] b43legacy-phy0: Radio turned on by software
[   23.780100] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   23.780702] b43legacy-phy0 debug: Removing Interface type 2
[   23.781026] b43legacy-phy0 debug: Wireless interface stopped
[   23.781214] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   23.781305] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[   23.781402] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   23.788303] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   23.796091] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   23.804101] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   23.812099] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   23.820099] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   23.828097] b43legacy-phy0 debug: Radio initialized
[   23.828114] b43legacy-phy0 debug: Radio initialized
[  168.108616] b43legacy-phy0: Broadcom 4301 WLAN found
[  168.132036] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[  168.132067] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[  168.156038] b43legacy-phy0 debug: Radio initialized
[  168.240072] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[  168.251300] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[  168.266305] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[  168.380058] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  168.436773] b43legacy-phy0 debug: Chip initialized
[  168.437348] b43legacy-phy0 debug: 30-bit DMA initialized
[  168.437601] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2B
[  168.437607] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x78
[  168.437611] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2E
[  168.437615] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x19
[  168.437665] b43legacy-phy0 debug: Wireless interface started
[  168.437684] b43legacy-phy0 debug: Adding Interface type 2
[  168.449982] b43legacy-phy0: Radio hardware status changed to DISABLED
[  168.450027] b43legacy-phy0 debug: Radio initialized
[  168.450631] b43legacy-phy0 debug: Removing Interface type 2
[  168.450961] b43legacy-phy0 debug: Wireless interface stopped
[  168.451136] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  168.451232] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  168.451330] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  168.456094] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  168.464374] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  168.472054] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  168.480035] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  168.488031] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  168.496031] b43legacy-phy0 debug: Radio initialized
[  168.496047] b43legacy-phy0 debug: Radio initialized
```

I think I can see the problem in there: it's looking for a hardware switch to be on, but there isn't a hardware switch on this card (and I can't see anything relevant in BIOS either). Is there some way of getting it not to look for one?

---

### Post by jamaisvu on 2009-11-16
(Bump.) Any ideas about what next, anyone?

---

### Post by hpadrick on 2009-11-25
You need to follow the directions outlined here:

[http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp](http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp)

There is a section for using the legacy driver. Hope that helps. I just installed form for the BCM4306 and it works great.

---

