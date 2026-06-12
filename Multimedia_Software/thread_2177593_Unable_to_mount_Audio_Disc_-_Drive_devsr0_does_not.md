---
title: "Unable to mount Audio Disc - Drive /dev/sr0 does not contain audio files"
date: 2013-09-29
forum: Multimedia Software
---

### Post by Tyler_Dence on 2013-09-29
I'm trying to load an audio disk recorded in a tascam cc-222 cd recorder, and this is the error I'm getting:

**Unable to mount Audio Disc **
Drive /dev/sr0 does not contain audio files

I've read CDs recorded by this recorder before, and I've tried other disks: all the other ones still work, so it doesn't appear to be a problem with my drive.

Dmesg shows no useful output:
```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-51-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #77-Ubuntu SMP Wed Jul 24 20:18:19 UTC 2013 (Ubuntu 3.2.0-51.77-generic 3.2.48)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-51-generic root=UUID=60c6137e-445d-410c-8b24-5fdc9b317929 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfd6b000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd6b000 - 00000000bfdbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfdbf000 - 00000000bfe83000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe83000 - 00000000bfebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfebf000 - 00000000bfedf000 (usable)
[    0.000000]  BIOS-e820: 00000000bfedf000 - 00000000bfef6000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfef6000 - 00000000bfefe000 (usable)
[    0.000000]  BIOS-e820: 00000000bfefe000 - 00000000bfeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (usable)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion dv7 Notebook PC/30F4, BIOS F.25 12/23/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 base 100000000 mask FC0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbff00 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bff00000
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bff00000 page 4k
[    0.000000] kernel direct mapping tables up to bff00000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ bfefc000-bfefe000
[    0.000000] RAMDISK: 36c5c000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 00000000bfefe120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bfef3000 000F4 (v04 HP     VADER    00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000bfee4000 0A496 (v01 HP     VADER    00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000bfe8c000 00040
[    0.000000] ACPI: DMAR 00000000bfef5000 00060 (v01               ? 00000001      00000000)
[    0.000000] ACPI: SSDT 00000000bfef4000 00655 (v01  PmRef    CpuPm 00003000 INTL 20060912)
[    0.000000] ACPI: HPET 00000000bfef2000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000bfef1000 0006C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000bfef0000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASF! 00000000bfeef000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000bfee3000 00176 (v01 HPQOEM SLIC-MPC 00000001 LOHR 000F4240)
[    0.000000] ACPI: BOOT 00000000bfee2000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bfee1000 00296 (v01 INTEL  SataAhci 00001000 INTL 20060912)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000013fffb000 - 000000013fffffff]
[    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff88013b600000-ffff88013f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bfd6b
[    0.000000]     0: 0x000bfdbf -> 0x000bfe83
[    0.000000]     0: 0x000bfebf -> 0x000bfedf
[    0.000000]     0: 0x000bfef6 -> 0x000bfefe
[    0.000000]     0: 0x000bfeff -> 0x000bff00
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048038
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 765592 pages, LIFO batch:31
[    0.000000]   Normal zone: 4096 pages used for memmap
[    0.000000]   Normal zone: 258048 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bfd6b000 - 00000000bfdbf000
[    0.000000] PM: Registered nosave memory: 00000000bfe83000 - 00000000bfebf000
[    0.000000] PM: Registered nosave memory: 00000000bfedf000 - 00000000bfef6000
[    0.000000] PM: Registered nosave memory: 00000000bfefe000 - 00000000bfeff000
[    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:38000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88013fc00000 s83136 r8192 d23360 u524288
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1027553
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-51-generic root=UUID=60c6137e-445d-410c-8b24-5fdc9b317929 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] ------------[ cut here ]------------
[    0.000000] WARNING: at /build/buildd/linux-3.2.0/drivers/iommu/dmar.c:492 warn_invalid_dmar+0x8f/0xa0()
[    0.000000] Hardware name: HP Pavilion dv7 Notebook PC
[    0.000000] Your BIOS is broken; DMAR reported at address 0!
[    0.000000] BIOS vendor: Hewlett-Packard; Ver: F.25; Product Version: F.25
[    0.000000] Modules linked in:
[    0.000000] Pid: 0, comm: swapper Not tainted 3.2.0-51-generic #77-Ubuntu
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff810681af>] warn_slowpath_common+0x7f/0xc0
[    0.000000]  [<ffffffff8166dc5c>] ? bad_to_user+0x7f6/0x7f6
[    0.000000]  [<ffffffff8106824f>] warn_slowpath_fmt_taint+0x3f/0x50
[    0.000000]  [<ffffffff81d0953c>] ? __acpi_map_table+0x13/0x19
[    0.000000]  [<ffffffff813912e9>] ? acpi_tb_checksum+0x9/0x1e
[    0.000000]  [<ffffffff81521fdf>] warn_invalid_dmar+0x8f/0xa0
[    0.000000]  [<ffffffff81d3a3d9>] check_zero_address+0x57/0xf7
[    0.000000]  [<ffffffff8166dc5c>] ? bad_to_user+0x7f6/0x7f6
[    0.000000]  [<ffffffff81d3a490>] detect_intel_iommu+0x17/0xb8
[    0.000000]  [<ffffffff81d04c0d>] pci_iommu_alloc+0x44/0x6f
[    0.000000]  [<ffffffff81d12102>] mem_init+0x19/0xec
[    0.000000]  [<ffffffff81cfca2b>] start_kernel+0x1da/0x3c2
[    0.000000]  [<ffffffff81cfc388>] x86_64_start_reservations+0x132/0x136
[    0.000000]  [<ffffffff81cfc140>] ? early_idt_handlers+0x140/0x140
[    0.000000]  [<ffffffff81cfc459>] x86_64_start_kernel+0xcd/0xdc
[    0.000000] ---[ end trace 42a28827722475eb ]---
[    0.000000] Memory: 4024228k/5242880k available (6583k kernel code, 1050728k absent, 167924k reserved, 6623k data, 924k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2261.000 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4522.00 BogoMIPS (lpj=9044000)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004036] Security Framework initialized
[    0.004054] AppArmor: AppArmor initialized
[    0.004056] Yama: becoming mindful.
[    0.004436] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.006502] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.008688] Mount-cache hash table entries: 256
[    0.008848] Initializing cgroup subsys cpuacct
[    0.008854] Initializing cgroup subsys memory
[    0.008864] Initializing cgroup subsys devices
[    0.008866] Initializing cgroup subsys freezer
[    0.008868] Initializing cgroup subsys blkio
[    0.008876] Initializing cgroup subsys perf_event
[    0.008909] CPU: Physical Processor ID: 0
[    0.008910] CPU: Processor Core ID: 0
[    0.008913] mce: CPU supports 6 MCE banks
[    0.008923] CPU0: Thermal monitoring enabled (TM1)
[    0.008927] using mwait in idle threads.
[    0.011658] ACPI: Core revision 20110623
[    0.020013] ftrace: allocating 26587 entries in 105 pages
[    0.024070] DMAR: Host address width 36
[    0.024073] DMAR: DRHD base: 0x00000000000000 flags: 0x1
[    0.024075] DMAR: parse DMAR table failure.
[    0.024401] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.065411] CPU0: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz stepping 06
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 99000
[    0.156039] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156082] Brought up 2 CPUs
[    0.156085] Total of 2 processors activated (9043.98 BogoMIPS).
[    0.158020] devtmpfs: initialized
[    0.158020] EVM: security.selinux
[    0.158020] EVM: security.SMACK64
[    0.158020] EVM: security.capability
[    0.158020] PM: Registering ACPI NVS region at bfe83000 (245760 bytes)
[    0.160019] print_constraints: dummy: 
[    0.160049] RTC time: 10:38:03, date: 09/29/13
[    0.160086] NET: Registered protocol family 16
[    0.160188] Trying to unpack rootfs image as initramfs...
[    0.160221] ACPI: bus type pci registered
[    0.160294] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.160298] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.175052] PCI: Using configuration type 1 for base access
[    0.176785] bio: create slab <bio-0> at 0
[    0.177050] ACPI: Added _OSI(Module Device)
[    0.177050] ACPI: Added _OSI(Processor Device)
[    0.177050] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.177050] ACPI: Added _OSI(Processor Aggregator Device)
[    0.177847] ACPI: EC: Look up EC in DSDT
[    0.180591] ACPI: Executed 1 blocks of module-level executable AML code
[    0.181644] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.186862] ACPI: SSDT 00000000bfd6ec18 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.187286] ACPI: Dynamic OEM Table Load:
[    0.187289] ACPI: SSDT           (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.187424] ACPI: SSDT 00000000bfd6c618 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.187832] ACPI: Dynamic OEM Table Load:
[    0.187835] ACPI: SSDT           (null) 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.240330] ACPI: SSDT 00000000bfd6de18 001CF (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.240771] ACPI: Dynamic OEM Table Load:
[    0.240774] ACPI: SSDT           (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.252163] ACPI: SSDT 00000000bfd6ef18 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.252587] ACPI: Dynamic OEM Table Load:
[    0.252590] ACPI: SSDT           (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.292040] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.344088] ACPI: Interpreter enabled
[    0.344098] ACPI: (supports S0 S3 S4 S5)
[    0.344141] ACPI: Using IOAPIC for interrupt routing
[    0.543250] Freeing initrd memory: 20048k freed
[    0.600257] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.601100] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.652054] ACPI: Power Resource [FN00] (off)
[    0.668426] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.668603] ACPI: No dock devices found.
[    0.668606] HEST: Table not found.
[    0.668610] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.668868] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.669370] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.669373] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.669375] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.669379] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.669394] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.669416] DMAR: Forcing write-buffer flush capability
[    0.669418] DMAR: Disabling IOMMU for graphics on this chipset
[    0.669446] pci 0000:00:01.0: [8086:2a41] type 1 class 0x000604
[    0.669487] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.669491] pci 0000:00:01.0: PME# disabled
[    0.669543] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.669609] pci 0000:00:1a.0: reg 20: [io  0x80e0-0x80ff]
[    0.669692] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.669761] pci 0000:00:1a.1: reg 20: [io  0x80c0-0x80df]
[    0.669857] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.669885] pci 0000:00:1a.7: reg 10: [mem 0xdf004c00-0xdf004fff]
[    0.670012] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.670017] pci 0000:00:1a.7: PME# disabled
[    0.670048] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.670068] pci 0000:00:1b.0: reg 10: [mem 0xdf000000-0xdf003fff 64bit]
[    0.670155] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.670160] pci 0000:00:1b.0: PME# disabled
[    0.670184] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.670274] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.670278] pci 0000:00:1c.0: PME# disabled
[    0.670304] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.670394] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.670398] pci 0000:00:1c.1: PME# disabled
[    0.670427] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.670515] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.670519] pci 0000:00:1c.2: PME# disabled
[    0.670547] pci 0000:00:1c.3: [8086:2946] type 1 class 0x000604
[    0.670636] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.670641] pci 0000:00:1c.3: PME# disabled
[    0.670668] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
[    0.670760] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.670764] pci 0000:00:1c.4: PME# disabled
[    0.670791] pci 0000:00:1c.5: [8086:294a] type 1 class 0x000604
[    0.670879] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.670884] pci 0000:00:1c.5: PME# disabled
[    0.670914] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.670983] pci 0000:00:1d.0: reg 20: [io  0x80a0-0x80bf]
[    0.671064] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.671129] pci 0000:00:1d.1: reg 20: [io  0x8080-0x809f]
[    0.671213] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.671282] pci 0000:00:1d.2: reg 20: [io  0x8060-0x807f]
[    0.671365] pci 0000:00:1d.3: [8086:2939] type 0 class 0x000c03
[    0.671436] pci 0000:00:1d.3: reg 20: [io  0x8040-0x805f]
[    0.671528] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.671556] pci 0000:00:1d.7: reg 10: [mem 0xdf004800-0xdf004bff]
[    0.671681] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.671687] pci 0000:00:1d.7: PME# disabled
[    0.671712] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.671794] pci 0000:00:1f.0: [8086:2919] type 0 class 0x000601
[    0.671944] pci 0000:00:1f.2: [8086:2929] type 0 class 0x000106
[    0.671968] pci 0000:00:1f.2: reg 10: [io  0x8108-0x810f]
[    0.671978] pci 0000:00:1f.2: reg 14: [io  0x8114-0x8117]
[    0.671989] pci 0000:00:1f.2: reg 18: [io  0x8100-0x8107]
[    0.671999] pci 0000:00:1f.2: reg 1c: [io  0x8110-0x8113]
[    0.672009] pci 0000:00:1f.2: reg 20: [io  0x8020-0x803f]
[    0.672019] pci 0000:00:1f.2: reg 24: [mem 0xdf004000-0xdf0047ff]
[    0.672091] pci 0000:00:1f.2: PME# supported from D3hot
[    0.672096] pci 0000:00:1f.2: PME# disabled
[    0.672117] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.672137] pci 0000:00:1f.3: reg 10: [mem 0xdf005000-0xdf0050ff 64bit]
[    0.672163] pci 0000:00:1f.3: reg 20: [io  0x8000-0x801f]
[    0.672280] pci 0000:01:00.0: [10de:0649] type 0 class 0x000300
[    0.672323] pci 0000:01:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
[    0.672361] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.672392] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit]
[    0.672411] pci 0000:01:00.0: reg 24: [io  0x7000-0x707f]
[    0.672430] pci 0000:01:00.0: reg 30: [mem 0xfff80000-0xffffffff pref]
[    0.680067] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.680070] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
[    0.680074] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    0.680078] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.680161] pci 0000:02:00.0: [8086:4237] type 0 class 0x000280
[    0.680199] pci 0000:02:00.0: reg 10: [mem 0xde000000-0xde001fff 64bit]
[    0.680386] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.680393] pci 0000:02:00.0: PME# disabled
[    0.688062] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.688067] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
[    0.688071] pci 0000:00:1c.0:   bridge window [mem 0xde000000-0xdeffffff]
[    0.688078] pci 0000:00:1c.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
[    0.688129] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.688133] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.688138] pci 0000:00:1c.1:   bridge window [mem 0xdd000000-0xddffffff]
[    0.688145] pci 0000:00:1c.1:   bridge window [mem 0xd4000000-0xd4ffffff 64bit pref]
[    0.688194] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.688199] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.688203] pci 0000:00:1c.2:   bridge window [mem 0xdc000000-0xdcffffff]
[    0.688210] pci 0000:00:1c.2:   bridge window [mem 0xd5000000-0xd5ffffff 64bit pref]
[    0.688285] pci 0000:05:00.0: [10ec:8168] type 0 class 0x000200
[    0.688304] pci 0000:05:00.0: reg 10: [io  0x3000-0x30ff]
[    0.688335] pci 0000:05:00.0: reg 18: [mem 0xd6010000-0xd6010fff 64bit pref]
[    0.688356] pci 0000:05:00.0: reg 20: [mem 0xd6000000-0xd600ffff 64bit pref]
[    0.688369] pci 0000:05:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.688450] pci 0000:05:00.0: supports D1 D2
[    0.688452] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.688458] pci 0000:05:00.0: PME# disabled
[    0.696059] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.696064] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.696068] pci 0000:00:1c.3:   bridge window [mem 0xdb000000-0xdbffffff]
[    0.696076] pci 0000:00:1c.3:   bridge window [mem 0xd6000000-0xd6ffffff 64bit pref]
[    0.696150] pci 0000:06:00.0: [197b:2380] type 0 class 0x000c00
[    0.696178] pci 0000:06:00.0: reg 10: [mem 0xda000000-0xda0007ff]
[    0.696198] pci 0000:06:00.0: reg 14: [mem 0xda000d00-0xda000d7f]
[    0.696253] pci 0000:06:00.0: reg 20: [mem 0xda000c80-0xda000cff]
[    0.696273] pci 0000:06:00.0: reg 24: [mem 0xda000c00-0xda000c7f]
[    0.696422] pci 0000:06:00.1: [197b:2382] type 0 class 0x000880
[    0.696446] pci 0000:06:00.1: reg 10: [mem 0xda000b00-0xda000bff]
[    0.696656] pci 0000:06:00.2: [197b:2381] type 0 class 0x000805
[    0.696679] pci 0000:06:00.2: reg 10: [mem 0xda000a00-0xda000aff]
[    0.696890] pci 0000:06:00.3: [197b:2383] type 0 class 0x000880
[    0.696914] pci 0000:06:00.3: reg 10: [mem 0xda000900-0xda0009ff]
[    0.697125] pci 0000:06:00.4: [197b:2384] type 0 class 0x000880
[    0.697148] pci 0000:06:00.4: reg 10: [mem 0xda000800-0xda0008ff]
[    0.704068] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.704073] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.704077] pci 0000:00:1c.4:   bridge window [mem 0xda000000-0xdaffffff]
[    0.704085] pci 0000:00:1c.4:   bridge window [mem 0xd7000000-0xd7ffffff 64bit pref]
[    0.704135] pci 0000:00:1c.5: PCI bridge to [bus 07-09]
[    0.704140] pci 0000:00:1c.5:   bridge window [io  0x1000-0x1fff]
[    0.704144] pci 0000:00:1c.5:   bridge window [mem 0xd9000000-0xd9ffffff]
[    0.704151] pci 0000:00:1c.5:   bridge window [mem 0xd8000000-0xd8ffffff 64bit pref]
[    0.704228] pci 0000:00:1e.0: PCI bridge to [bus 0a-0a] (subtractive decode)
[    0.704240] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.704243] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.704245] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.704248] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.704287] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.704458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.704523] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.704573] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.704617] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.704661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.704716] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.704784] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
[    0.704836]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.704840]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.704842] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.710233] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.710287] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.710339] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.710391] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.710443] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.710498] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.710550] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.710601] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.710790] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.710790] vgaarb: loaded
[    0.710790] vgaarb: bridge control possible 0000:01:00.0
[    0.710790] i2c-core: driver [aat2870] using legacy suspend method
[    0.710790] i2c-core: driver [aat2870] using legacy resume method
[    0.710790] SCSI subsystem initialized
[    0.710790] libata version 3.00 loaded.
[    0.710790] usbcore: registered new interface driver usbfs
[    0.710790] usbcore: registered new interface driver hub
[    0.710790] usbcore: registered new device driver usb
[    0.710790] PCI: Using ACPI for IRQ routing
[    0.713245] PCI: pci_cache_line_size set to 64 bytes
[    0.713389] reserve RAM buffer: 000000000009e000 - 000000000009ffff 
[    0.713391] reserve RAM buffer: 00000000bfd6b000 - 00000000bfffffff 
[    0.713394] reserve RAM buffer: 00000000bfe83000 - 00000000bfffffff 
[    0.713396] reserve RAM buffer: 00000000bfedf000 - 00000000bfffffff 
[    0.713398] reserve RAM buffer: 00000000bfefe000 - 00000000bfffffff 
[    0.713400] reserve RAM buffer: 00000000bff00000 - 00000000bfffffff 
[    0.713519] NetLabel: Initializing
[    0.713521] NetLabel:  domain hash size = 128
[    0.713522] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.713535] NetLabel:  unlabeled traffic allowed by default
[    0.713556] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.713556] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.713556] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.716142] Switching to clocksource hpet
[    0.723873] AppArmor: AppArmor Filesystem Enabled
[    0.723911] pnp: PnP ACPI init
[    0.723930] ACPI: bus type pnp registered
[    0.852271] pnp 00:00: [bus 00-ff]
[    0.852274] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.852276] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.852278] pnp 00:00: [io  0x0d00-0xffff window]
[    0.852281] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.852283] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.852285] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.852287] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.852289] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.852291] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.852294] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.852296] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.852298] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.852300] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.852306] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.852308] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.852310] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.852312] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.852315] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
[    0.852317] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.852401] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.852537] pnp 00:01: [io  0x002e-0x002f]
[    0.852539] pnp 00:01: [io  0x004e-0x004f]
[    0.852541] pnp 00:01: [io  0x164e-0x164f]
[    0.852543] pnp 00:01: [io  0x0061]
[    0.852545] pnp 00:01: [io  0x0068]
[    0.852546] pnp 00:01: [io  0x006c]
[    0.852548] pnp 00:01: [io  0x0070]
[    0.852550] pnp 00:01: [io  0x0080]
[    0.852552] pnp 00:01: [io  0x0092]
[    0.852554] pnp 00:01: [io  0x00b2-0x00b3]
[    0.852555] pnp 00:01: [io  0x0063]
[    0.852557] pnp 00:01: [io  0x0065]
[    0.852559] pnp 00:01: [io  0x0067]
[    0.852560] pnp 00:01: [io  0x0600-0x060f]
[    0.852562] pnp 00:01: [io  0x0610]
[    0.852564] pnp 00:01: [io  0x0800-0x080f]
[    0.852566] pnp 00:01: [io  0x0810-0x0817]
[    0.852568] pnp 00:01: [io  0x0820-0x0823]
[    0.852570] pnp 00:01: [io  0x0400-0x047f]
[    0.852572] pnp 00:01: [io  0x0500-0x053f]
[    0.852574] pnp 00:01: [mem 0xf8000000-0xfbffffff]
[    0.852576] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.852578] pnp 00:01: [mem 0xfed10000-0xfed13fff]
[    0.852580] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.852581] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.852583] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.852585] pnp 00:01: [mem 0xfed20000-0xfed8ffff]
[    0.852587] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.852622] pnp 00:01: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.5 BAR 13 [io  0x1000-0x1fff]
[    0.852704] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.852707] system 00:01: [io  0x0610] has been reserved
[    0.852710] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.852712] system 00:01: [io  0x0810-0x0817] has been reserved
[    0.852715] system 00:01: [io  0x0820-0x0823] has been reserved
[    0.852717] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.852720] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.852723] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.852726] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.852729] system 00:01: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.852731] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.852734] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.852737] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.852740] system 00:01: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.852742] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.852746] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.852756] pnp 00:02: [io  0x0000-0x001f]
[    0.852758] pnp 00:02: [io  0x0081-0x0091]
[    0.852760] pnp 00:02: [io  0x0093-0x009f]
[    0.852762] pnp 00:02: [io  0x00c0-0x00df]
[    0.852764] pnp 00:02: [dma 4]
[    0.852794] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.852817] pnp 00:03: [io  0x0070-0x0077]
[    0.852850] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.852907] pnp 00:04: [irq 0 disabled]
[    0.852927] pnp 00:04: [irq 8]
[    0.852929] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.852963] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.852974] pnp 00:05: [io  0x00f0]
[    0.852980] pnp 00:05: [irq 13]
[    0.853011] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.853021] pnp 00:06: [mem 0xff800000-0xffffffff]
[    0.853055] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)
[    0.853071] pnp 00:07: [io  0x0060]
[    0.853073] pnp 00:07: [io  0x0064]
[    0.853079] pnp 00:07: [irq 1]
[    0.853114] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.853132] pnp 00:08: [irq 12]
[    0.853166] pnp 00:08: Plug and Play ACPI device, IDs SYN0156 SYN0100 SYN0002 PNP0f13 (active)
[    0.853237] pnp 00:09: [irq 23]
[    0.853281] pnp 00:09: Plug and Play ACPI device, IDs HPQ0004 (active)
[    0.853304] pnp 00:0a: [io  0xfd60-0xfd63]
[    0.853310] pnp 00:0a: [irq 4]
[    0.853358] pnp 00:0a: Plug and Play ACPI device, IDs ENE0100 (active)
[    0.853425] pnp: PnP ACPI: found 11 devices
[    0.853427] ACPI: ACPI bus type pnp unregistered
[    0.860465] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.860470] pci 0000:05:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.860477] PCI: max bus depth: 1 pci_try_num: 2
[    0.860540] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x80000)
[    0.860544] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.860547] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
[    0.860550] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    0.860554] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.860558] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.860562] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
[    0.860567] pci 0000:00:1c.0:   bridge window [mem 0xde000000-0xdeffffff]
[    0.860572] pci 0000:00:1c.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
[    0.860579] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.860583] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.860588] pci 0000:00:1c.1:   bridge window [mem 0xdd000000-0xddffffff]
[    0.860593] pci 0000:00:1c.1:   bridge window [mem 0xd4000000-0xd4ffffff 64bit pref]
[    0.860600] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.860604] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.860609] pci 0000:00:1c.2:   bridge window [mem 0xdc000000-0xdcffffff]
[    0.860614] pci 0000:00:1c.2:   bridge window [mem 0xd5000000-0xd5ffffff 64bit pref]
[    0.860623] pci 0000:05:00.0: BAR 6: assigned [mem 0xd6020000-0xd602ffff pref]
[    0.860626] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.860629] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.860634] pci 0000:00:1c.3:   bridge window [mem 0xdb000000-0xdbffffff]
[    0.860639] pci 0000:00:1c.3:   bridge window [mem 0xd6000000-0xd6ffffff 64bit pref]
[    0.860646] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.860650] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.860655] pci 0000:00:1c.4:   bridge window [mem 0xda000000-0xdaffffff]
[    0.860659] pci 0000:00:1c.4:   bridge window [mem 0xd7000000-0xd7ffffff 64bit pref]
[    0.860667] pci 0000:00:1c.5: PCI bridge to [bus 07-09]
[    0.860670] pci 0000:00:1c.5:   bridge window [io  0x1000-0x1fff]
[    0.860676] pci 0000:00:1c.5:   bridge window [mem 0xd9000000-0xd9ffffff]
[    0.860680] pci 0000:00:1c.5:   bridge window [mem 0xd8000000-0xd8ffffff 64bit pref]
[    0.860688] pci 0000:00:1e.0: PCI bridge to [bus 0a-0a]
[    0.860712] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.860716] pci 0000:00:01.0: setting latency timer to 64
[    0.860724] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.860728] pci 0000:00:1c.0: setting latency timer to 64
[    0.860738] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.860742] pci 0000:00:1c.1: setting latency timer to 64
[    0.860752] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.860756] pci 0000:00:1c.2: setting latency timer to 64
[    0.860766] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.860770] pci 0000:00:1c.3: setting latency timer to 64
[    0.860777] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.860782] pci 0000:00:1c.4: setting latency timer to 64
[    0.860789] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.860793] pci 0000:00:1c.5: setting latency timer to 64
[    0.860800] pci 0000:00:1e.0: setting latency timer to 64
[    0.860805] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.860807] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.860809] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.860812] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.860814] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    0.860817] pci_bus 0000:01: resource 1 [mem 0xd0000000-0xd2ffffff]
[    0.860821] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.860824] pci_bus 0000:02: resource 0 [io  0x6000-0x6fff]
[    0.860827] pci_bus 0000:02: resource 1 [mem 0xde000000-0xdeffffff]
[    0.860830] pci_bus 0000:02: resource 2 [mem 0xd3000000-0xd3ffffff 64bit pref]
[    0.860834] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.860837] pci_bus 0000:03: resource 1 [mem 0xdd000000-0xddffffff]
[    0.860840] pci_bus 0000:03: resource 2 [mem 0xd4000000-0xd4ffffff 64bit pref]
[    0.860843] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.860846] pci_bus 0000:04: resource 1 [mem 0xdc000000-0xdcffffff]
[    0.860849] pci_bus 0000:04: resource 2 [mem 0xd5000000-0xd5ffffff 64bit pref]
[    0.860853] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.860856] pci_bus 0000:05: resource 1 [mem 0xdb000000-0xdbffffff]
[    0.860859] pci_bus 0000:05: resource 2 [mem 0xd6000000-0xd6ffffff 64bit pref]
[    0.860862] pci_bus 0000:06: resource 0 [io  0x2000-0x2fff]
[    0.860865] pci_bus 0000:06: resource 1 [mem 0xda000000-0xdaffffff]
[    0.860868] pci_bus 0000:06: resource 2 [mem 0xd7000000-0xd7ffffff 64bit pref]
[    0.860872] pci_bus 0000:07: resource 0 [io  0x1000-0x1fff]
[    0.860875] pci_bus 0000:07: resource 1 [mem 0xd9000000-0xd9ffffff]
[    0.860878] pci_bus 0000:07: resource 2 [mem 0xd8000000-0xd8ffffff 64bit pref]
[    0.860881] pci_bus 0000:0a: resource 4 [io  0x0000-0x0cf7]
[    0.860884] pci_bus 0000:0a: resource 5 [io  0x0d00-0xffff]
[    0.860887] pci_bus 0000:0a: resource 6 [mem 0x000a0000-0x000bffff]
[    0.860890] pci_bus 0000:0a: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.860931] NET: Registered protocol family 2
[    0.861076] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.862136] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.865998] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.866500] TCP: Hash tables configured (established 524288 bind 65536)
[    0.866503] TCP reno registered
[    0.866514] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.866554] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.866709] NET: Registered protocol family 1
[    0.866741] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.866764] pci 0000:00:1a.0: PCI INT A disabled
[    0.866773] pci 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.866794] pci 0000:00:1a.1: PCI INT B disabled
[    0.866804] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.464014] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    2.464129] pci 0000:00:1a.7: PCI INT C disabled
[    2.464166] pci 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.464189] pci 0000:00:1d.0: PCI INT A disabled
[    2.464201] pci 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    2.464223] pci 0000:00:1d.1: PCI INT B disabled
[    2.464232] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.464253] pci 0000:00:1d.2: PCI INT C disabled
[    2.464261] pci 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.464281] pci 0000:00:1d.3: PCI INT D disabled
[    2.464291] pci 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.064025] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    4.064141] pci 0000:00:1d.7: PCI INT A disabled
[    4.064195] pci 0000:01:00.0: Boot video device
[    4.064229] PCI: CLS 64 bytes, default 64
[    4.064232] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    4.064235] Placing 64MB software IO TLB between ffff8800bbd6b000 - ffff8800bfd6b000
[    4.064237] software IO TLB at phys 0xbbd6b000 - 0xbfd6b000
[    4.064249] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    4.064251] Simple Boot Flag at 0x44 set to 0x1
[    4.064625] audit: initializing netlink socket (disabled)
[    4.064635] type=2000 audit(1380451086.060:1): initialized
[    4.086233] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    4.088635] VFS: Disk quotas dquot_6.5.2
[    4.088692] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    4.089232] fuse init (API version 7.17)
[    4.089331] msgmni has been set to 7898
[    4.089717] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    4.089748] io scheduler noop registered
[    4.089750] io scheduler deadline registered
[    4.089785] io scheduler cfq registered (default)
[    4.089903] pcieport 0000:00:01.0: setting latency timer to 64
[    4.089935] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    4.089986] pcieport 0000:00:1c.0: setting latency timer to 64
[    4.090038] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    4.090113] pcieport 0000:00:1c.1: setting latency timer to 64
[    4.090164] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    4.090241] pcieport 0000:00:1c.2: setting latency timer to 64
[    4.090293] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    4.090369] pcieport 0000:00:1c.3: setting latency timer to 64
[    4.090421] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    4.090497] pcieport 0000:00:1c.4: setting latency timer to 64
[    4.090551] pcieport 0000:00:1c.4: irq 45 for MSI/MSI-X
[    4.090628] pcieport 0000:00:1c.5: setting latency timer to 64
[    4.090680] pcieport 0000:00:1c.5: irq 46 for MSI/MSI-X
[    4.090775] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.090794] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.090874] efifb: probing for efifb
[    4.092731] efifb: framebuffer at 0xd1000000, mapped to 0xffffc90005100000, using 6892k, total 6890k
[    4.092734] efifb: mode is 1680x1050x32, linelength=6720, pages=1
[    4.092736] efifb: scrolling: redraw
[    4.092738] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    4.098378] Console: switching to colour frame buffer device 210x65
[    4.103838] fb0: EFI VGA frame buffer device
[    4.103846] intel_idle: MWAIT substates: 0x3122220
[    4.103848] intel_idle: does not run on family 6 model 23
[    4.244024] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.388031] ACPI: AC Adapter [AC] (on-line)
[    4.388125] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    4.388130] ACPI: Power Button [PWRB]
[    4.388174] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    4.388203] ACPI: Lid Switch [LID0]
[    4.388249] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    4.388252] ACPI: Sleep Button [SLPB]
[    4.388307] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    4.388310] ACPI: Power Button [PWRF]
[    4.404053] ACPI: Fan [FAN] (off)
[    4.404185] Monitor-Mwait will be used to enter C-1 state
[    4.404206] Monitor-Mwait will be used to enter C-2 state
[    4.404224] Monitor-Mwait will be used to enter C-3 state
[    4.404235] Marking TSC unstable due to TSC halts in idle
[    4.404249] ACPI: acpi_idle registered with cpuidle
[    4.616028] thermal LNXTHERM:00: registered as thermal_zone0
[    4.616030] ACPI: Thermal Zone [THRM] (29 C)
[    4.616048] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.616056] ACPI: Battery Slot [BAT0] (battery present)
[    4.616094] ERST: Table is not found!
[    4.616096] GHES: HEST is not enabled!
[    4.616175] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.708288] Linux agpgart interface v0.103
[    4.709971] brd: module loaded
[    4.710787] loop: module loaded
[    4.710917] ahci 0000:00:1f.2: version 3.0
[    4.710937] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.710987] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
[    4.711030] ahci: SSS flag set, parallel bus scan disabled
[    4.711068] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    4.711072] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ccc ems 
[    4.711078] ahci 0000:00:1f.2: setting latency timer to 64
[    4.732583] scsi0 : ahci
[    4.732678] scsi1 : ahci
[    4.732764] scsi2 : ahci
[    4.732847] scsi3 : ahci
[    4.732929] scsi4 : ahci
[    4.733008] scsi5 : ahci
[    4.733215] ata1: SATA max UDMA/133 abar m2048@0xdf004000 port 0xdf004100 irq 47
[    4.733219] ata2: SATA max UDMA/133 abar m2048@0xdf004000 port 0xdf004180 irq 47
[    4.733221] ata3: DUMMY
[    4.733223] ata4: DUMMY
[    4.733225] ata5: SATA max UDMA/133 abar m2048@0xdf004000 port 0xdf004300 irq 47
[    4.733228] ata6: SATA max UDMA/133 abar m2048@0xdf004000 port 0xdf004380 irq 47
[    4.733639] Fixed MDIO Bus: probed
[    4.733658] tun: Universal TUN/TAP device driver, 1.6
[    4.733659] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.733723] PPP generic driver version 2.4.2
[    4.733844] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.733861] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.733879] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.733883] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.733935] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.733970] ehci_hcd 0000:00:1a.7: debug port 1
[    4.737858] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    4.737873] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xdf004c00
[    4.752018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.752150] hub 1-0:1.0: USB hub found
[    4.752155] hub 1-0:1.0: 4 ports detected
[    4.752229] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.752245] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.752249] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.752296] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.752322] ehci_hcd 0000:00:1d.7: debug port 1
[    4.756203] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    4.756219] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdf004800
[    4.772018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.772141] hub 2-0:1.0: USB hub found
[    4.772145] hub 2-0:1.0: 8 ports detected
[    4.772227] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.772243] uhci_hcd: USB Universal Host Controller Interface driver
[    4.772258] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.772266] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.772270] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.772313] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.772351] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000080e0
[    4.772481] hub 3-0:1.0: USB hub found
[    4.772485] hub 3-0:1.0: 2 ports detected
[    4.772557] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.772565] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.772568] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.772616] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.772651] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000080c0
[    4.772778] hub 4-0:1.0: USB hub found
[    4.772782] hub 4-0:1.0: 2 ports detected
[    4.772852] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.772860] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.772863] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.772916] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    4.772943] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000080a0
[    4.773071] hub 5-0:1.0: USB hub found
[    4.773078] hub 5-0:1.0: 2 ports detected
[    4.773148] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    4.773156] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.773159] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.773202] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.773237] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00008080
[    4.773370] hub 6-0:1.0: USB hub found
[    4.773378] hub 6-0:1.0: 2 ports detected
[    4.773449] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.773456] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.773460] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.773502] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.773529] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008060
[    4.773664] hub 7-0:1.0: USB hub found
[    4.773668] hub 7-0:1.0: 2 ports detected
[    4.773740] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.773748] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.773751] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.773796] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    4.773831] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00008040
[    4.773960] hub 8-0:1.0: USB hub found
[    4.773963] hub 8-0:1.0: 2 ports detected
[    4.774083] usbcore: registered new interface driver libusual
[    4.774124] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    4.814527] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.814533] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.814670] mousedev: PS/2 mouse device common for all mice
[    4.817667] rtc_cmos 00:03: RTC can wake from S4
[    4.817785] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.817814] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.817897] device-mapper: uevent: version 1.0.3
[    4.817968] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    4.818033] cpuidle: using governor ladder
[    4.818119] cpuidle: using governor menu
[    4.818122] EFI Variables Facility v0.08 2004-May-17
[    4.818364] TCP cubic registered
[    4.818472] NET: Registered protocol family 10
[    4.818934] NET: Registered protocol family 17
[    4.818939] Registering the dns_resolver key type
[    4.819125] PM: Hibernation image not present or could not be loaded.
[    4.819142] registered taskstats version 1
[    4.826399]   Magic number: 13:837:629
[    4.826527] rtc_cmos 00:03: setting system clock to 2013-09-29 10:38:07 UTC (1380451087)
[    4.826808] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.826810] EDD information not available.
[    4.857234] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    5.088065] usb 2-5: new high-speed USB device number 2 using ehci_hcd
[    5.228044] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.230406] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    5.230556] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.230633] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) succeeded
[    5.230638] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    5.230762] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.230895] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.233012] ata1.00: ATA-8: WDC WD3200BEVT-60ZCT0, 11.01A11, max UDMA/100
[    5.233016] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    5.235438] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    5.235586] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.235592] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    5.235718] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.235845] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.235935] ata1.00: configured for UDMA/100
[    5.236144] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-6 11.0 PQ: 0 ANSI: 5
[    5.236271] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    5.236280] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.236333] sd 0:0:0:0: [sda] Write Protect is off
[    5.236336] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.236367] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.323916]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 > sda3
[    5.324705] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.356161] ACPI: Battery Slot [BAT0] (battery present)
[    5.556119] ata2: SATA link down (SStatus 4 SControl 300)
[    6.048107] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.064380] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    6.066298] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) succeeded
[    6.068192] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) succeeded
[    6.068197] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    6.070095] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) succeeded
[    6.072045] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) succeeded
[    6.086617] ata5.00: ATAPI: TSSTcorp CDDVDW TS-L633L, 0400, max UDMA/100
[    6.102304] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    6.104283] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) succeeded
[    6.104755] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) succeeded
[    6.104760] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    6.105423] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) succeeded
[    6.119812] ata5.00: configured for UDMA/100
[    6.124386] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633L  0400 PQ: 0 ANSI: 5
[    6.130085] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.130089] cdrom: Uniform CD-ROM driver Revision: 3.20
[    6.130245] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    6.130350] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    6.448156] ata6: SATA link down (SStatus 0 SControl 300)
[    6.449783] Freeing unused kernel memory: 924k freed
[    6.450016] Write protecting the kernel read-only data: 12288k
[    6.455257] Freeing unused kernel memory: 1592k freed
[    6.459507] Freeing unused kernel memory: 1188k freed
[    6.476449] udevd[100]: starting version 175
[    6.813845] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    6.941053] sdhci: Secure Digital Host Controller Interface driver
[    6.941056] sdhci: Copyright(c) Pierre Ossman
[    6.945537] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    6.945563] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    6.945602] r8169 0000:05:00.0: setting latency timer to 64
[    6.945673] r8169 0000:05:00.0: irq 48 for MSI/MSI-X
[    6.946091] r8169 0000:05:00.0: eth0: RTL8168c/8111c at 0xffffc9000065a000, 00:1e:ec:83:68:bb, XID 1c4000c0 IRQ 48
[    6.946094] r8169 0000:05:00.0: eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    6.948341] acpi device:06: registered as cooling_device3
[    6.948502] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input5
[    6.948551] ACPI: Video Device [EVGA] (multi-head: yes  rom: no  post: no)
[    6.949203] firewire_ohci 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.949213] firewire_ohci 0000:06:00.0: setting latency timer to 64
[    7.012096] firewire_ohci: Added fw-ohci device 0000:06:00.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x10
[    7.012197] sdhci-pci 0000:06:00.1: SDHCI controller found [197b:2382] (rev 0)
[    7.012220] sdhci-pci 0000:06:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.012285] sdhci-pci 0000:06:00.1: setting latency timer to 64
[    7.012295] mmc0: no vmmc regulator found
[    7.012330] Registered led device: mmc0::
[    7.013362] mmc0: SDHCI controller on PCI [0000:06:00.1] using DMA
[    7.013375] sdhci-pci 0000:06:00.2: SDHCI controller found [197b:2381] (rev 0)
[    7.013391] sdhci-pci 0000:06:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.013400] sdhci-pci 0000:06:00.2: Refusing to bind to secondary interface.
[    7.013407] sdhci-pci 0000:06:00.2: PCI INT A disabled
[    7.512246] firewire_core: created device fw0: GUID 873f0200574f40d9, S400
[   13.387045] EXT3-fs (sda6): recovery required on readonly filesystem
[   13.387049] EXT3-fs (sda6): write access will be enabled during recovery
[   19.394804] kjournald starting.  Commit interval 5 seconds
[   19.394869] EXT3-fs (sda6): recovery complete
[   19.395382] EXT3-fs (sda6): mounted filesystem with ordered data mode
[   23.884622] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.946887] udevd[390]: starting version 175
[   25.047231] lp: driver loaded but no devices found
[   27.038201] wmi: Mapper loaded
[   27.239872] jmb38x_ms 0000:06:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.239881] jmb38x_ms 0000:06:00.3: setting latency timer to 64
[   28.293552] ene_ir: chip is 0x3926 - kbver = 0x00, rev = 0xc0
[   28.293556] ene_ir: PLL freq = 1406
[   28.293557] ene_ir: KB3926C detected
[   28.293573] ene_ir: Firmware regs: 00 00
[   28.293575] ene_ir: Hardware features:
[   28.293577] ene_ir: * Uses GPIO 40 for IR demodulated input
[   28.296272] input: HP WMI hotkeys as /devices/virtual/input/input6
[   28.308124] hp_accel: hardware type DV7 found
[   28.308698] lis3lv02d: 8 bits sensor found
[   28.348128] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
[   28.348256] Registered led device: hp::hddprotect
[   28.348275] hp_accel: driver loaded
[   28.569814] IR NEC protocol handler initialized
[   29.018930] IR RC5(x) protocol handler initialized
[   29.027059] IR RC6 protocol handler initialized
[   29.056035] Registered IR keymap rc-rc6-mce
[   29.056138] input: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0/input8
[   29.056234] rc0: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0
[   29.056500] ene_ir: driver has been successfully loaded
[   29.492074] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04751/0xa00000/0x20000
[   29.572368] IR JVC protocol handler initialized
[   29.627240] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   29.629323] IR Sony protocol handler initialized
[   29.650664] input: MCE IR Keyboard/Mouse (ene_ir) as /devices/virtual/input/input10
[   29.650757] IR MCE Keyboard/mouse protocol handler initialized
[   29.903101] lirc_dev: IR Remote Control driver registered, major 250 
[   29.904020] rc rc0: lirc_dev: driver ir-lirc-codec (ene_ir) registered at minor = 0
[   29.904023] IR LIRC bridge handler initialized
[   30.245594] cfg80211: Calling CRDA to update world regulatory domain
[   31.389176] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[   31.389186] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[   31.389195] snd_hda_intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   31.389279] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   31.389312] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   32.266247] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   32.266251] Copyright(c) 2003-2011 Intel Corporation
[   32.266309] iwlwifi 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.266318] iwlwifi 0000:02:00.0: setting latency timer to 64
[   32.266343] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   32.266346] iwlwifi 0000:02:00.0: pci_resource_base = ffffc9000066c000
[   32.266348] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[   32.266429] iwlwifi 0000:02:00.0: irq 50 for MSI/MSI-X
[   32.266471] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   32.266530] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   32.288372] iwlwifi 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   32.288375] iwlwifi 0000:02:00.0: Device SKU: 0Xf0
[   32.288388] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   32.367107] Linux video capture interface: v2.00
[   32.404633] uvcvideo: Found UVC 1.00 device HP Webcam  (046d:09b8)
[   32.410411] input: HP Webcam  as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input11
[   32.410483] usbcore: registered new interface driver uvcvideo
[   32.410485] USB Video Class driver (1.1.1)
[   32.987207] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
[   32.987416] Registered led device: phy0-led
[   32.987448] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   33.000588] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   33.000741] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   33.608178] nvidia: module license 'NVIDIA' taints kernel.
[   33.608182] Disabling lock debugging due to kernel taint
[   33.833476] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   33.833501] nvidia 0000:01:00.0: setting latency timer to 64
[   33.833513] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   33.834136] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.88  Wed Mar 27 14:26:46 PDT 2013
[   33.962541] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   33.962545] cfg80211: World regulatory domain updated:
[   33.962547] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   33.962550] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.962552] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   33.962555] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   33.962557] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.962560] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.974649] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   34.429560] type=1400 audit(1380465517.098:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=845 comm="apparmor_parser"
[   34.429570] type=1400 audit(1380465517.098:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=937 comm="apparmor_parser"
[   34.429978] type=1400 audit(1380465517.098:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=937 comm="apparmor_parser"
[   34.429986] type=1400 audit(1380465517.098:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=845 comm="apparmor_parser"
[   34.430211] type=1400 audit(1380465517.098:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=937 comm="apparmor_parser"
[   34.430221] type=1400 audit(1380465517.098:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=845 comm="apparmor_parser"
[   34.430659] type=1400 audit(1380465517.098:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=846 comm="apparmor_parser"
[   34.431257] type=1400 audit(1380465517.098:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=846 comm="apparmor_parser"
[   34.431496] type=1400 audit(1380465517.098:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=846 comm="apparmor_parser"
[   38.848209] EXT3-fs (sda6): using internal journal
[   39.277056] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   39.936641] init: failsafe main process (1074) killed by TERM signal
[   43.310013] type=1400 audit(1380465525.982:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1150 comm="apparmor_parser"
[   43.311984] type=1400 audit(1380465525.982:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1151 comm="apparmor_parser"
[   43.312342] type=1400 audit(1380465525.982:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1151 comm="apparmor_parser"
[   43.312662] type=1400 audit(1380465525.982:14): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1152 comm="apparmor_parser"
[   43.313184] type=1400 audit(1380465525.982:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1152 comm="apparmor_parser"
[   43.313422] type=1400 audit(1380465525.982:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1152 comm="apparmor_parser"
[   44.498398] type=1400 audit(1380465527.170:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1155 comm="apparmor_parser"
[   45.106732] type=1400 audit(1380465527.778:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/libvirt/virt-aa-helper" pid=1156 comm="apparmor_parser"
[   45.375693] type=1400 audit(1380465528.046:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1157 comm="apparmor_parser"
[   45.376194] type=1400 audit(1380465528.046:20): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1157 comm="apparmor_parser"
[   48.664032] init: kdm main process (1190) killed by TERM signal
[   49.020619] init: avahi-daemon main process (1192) terminated with status 127
[   49.020645] init: avahi-daemon main process ended, respawning
[   49.022113] ppdev: user-space parallel port driver
[   49.404367] audit_printk_skb: 48 callbacks suppressed
[   49.404369] type=1400 audit(1380465532.074:37): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1227 comm="apparmor_parser"
[   49.404876] type=1400 audit(1380465532.074:38): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1227 comm="apparmor_parser"
[   51.251732] Bluetooth: Core ver 2.16
[   51.251753] NET: Registered protocol family 31
[   51.251755] Bluetooth: HCI device and connection manager initialized
[   51.251758] Bluetooth: HCI socket layer initialized
[   51.251760] Bluetooth: L2CAP socket layer initialized
[   51.251773] Bluetooth: SCO socket layer initialized
[   51.754581] Bluetooth: RFCOMM TTY layer initialized
[   51.754586] Bluetooth: RFCOMM socket layer initialized
[   51.754588] Bluetooth: RFCOMM ver 1.11
[   51.878385] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   51.878388] Bluetooth: BNEP filters: protocol multicast
[   53.119052] init: gdm main process (1287) killed by TERM signal
[   53.123637] type=1400 audit(1380465535.790:39): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1334 comm="apparmor_parser"
[   55.462170] kvm: disabled by bios
[   55.472974] init: qemu-kvm pre-start process (1268) terminated with status 1
[   61.904115] usb 2-5: reset high-speed USB device number 2 using ehci_hcd
[   62.524490] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   62.527493] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   62.641082] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   62.644107] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   62.696390] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   62.696961] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   62.954113] r8169 0000:05:00.0: eth0: link down
[   62.954579] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   62.954839] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   63.971914] Bridge firewalling registered
[   65.767247] ip_tables: (C) 2000-2006 Netfilter Core Team
[   68.537957] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   70.337200] ADDRCONF(NETDEV_UP): virbr0: link is not ready
[   71.169338] wlan0: authenticate with c0:c1:c0:0d:a7:2d (try 1)
[   71.172072] wlan0: authenticated
[   71.173491] wlan0: associate with c0:c1:c0:0d:a7:2d (try 1)
[   71.177144] wlan0: RX AssocResp from c0:c1:c0:0d:a7:2d (capab=0x401 status=0 aid=3)
[   71.177147] wlan0: associated
[   71.182982] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   72.829206] vboxdrv: Found 2 processor cores.
[   72.829967] vboxdrv: fAsync=0 offMin=0x1a9 offMax=0xf71
[   72.830595] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   72.830598] vboxdrv: Successfully loaded version 4.2.10 (interface 0x001a0004).
[   73.184386] Ebtables v2.0 registered
[   73.361834] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   73.687064] NVRM: Your system is not currently configured to drive a VGA console
[   73.687068] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   73.687071] NVRM: requires the use of a text-mode VGA console. Use of other console
[   73.687073] NVRM: drivers including, but not limited to, vesafb, may result in
[   73.687075] NVRM: corruption and stability problems, and is not supported.
[   73.740697] vboxpci: IOMMU not found (not registered)
[   81.904055] wlan0: no IPv6 routers present
[   98.638950] init: plymouth-stop pre-start process (2793) terminated with status 1
[  192.536055] usb 2-5: reset high-speed USB device number 2 using ehci_hcd
[  299.692237] CE: hpet increased min_delta_ns to 20113 nsec
[  603.216081] usb 2-5: reset high-speed USB device number 2 using ehci_hcd
[ 2412.243995] sched: RT throttling activated

```

Fstab:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=60c6137e-445d-410c-8b24-5fdc9b317929 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=22210ddb-3acd-4414-bdd7-f4d0c5e7d298 none            swap    sw              0       0
/dev/sda1       /media/storagedrive ext4 user,exec 0 2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

Uname -a:
```

Linux Tyler-Linux 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:18:19 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

lsb_release -a:
```

LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:qt4-3.1-amd64:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

```

Not sure what other information would be useful.

---

### Post by Tyler_Dence on 2013-10-06
I tried another disk recorded today, and it doesn't give me any error dialog or anything. It doesn't recognize for some reason.

**Edit:** Blank CDs are still being recognized, so it doesn't appear to be a problem with the CD Drive. I'll test the recorded CD in a different computer to try and isolate the issue.
**Edit 2: **I tried another CD recorded by the same recorder, and it worked just fine. I'll post back with more details when I get home.
**Edit 3: **The CD that didn't work has audio on it, I can play it just fine in the recorder that recorded it. I think the problem is that the recording stopped at 79 minutes due to the CD being full. I'll post back again when I get the audio off of it.

---

### Post by Tyler_Dence on 2013-10-06
Ok, so the CD works in my windows vista (grrr) desktop. Any ideas of where to look? At least now I can get the audio off of the CD.

Dmesg still shows no signs of failure...

---

### Post by Yellow Pasque on 2013-10-06
Is it an audio CD or a data CD with audio files?

---

