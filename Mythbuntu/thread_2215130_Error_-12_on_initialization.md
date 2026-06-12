---
title: "Error -12 on initialization"
date: 2014-04-04
forum: Mythbuntu
---

### Post by Richard_Butler on 2014-04-04
This is a new build with the following hardware.

[LIST]
[*]Abit KV8 pro motherboard
[*]AMD Athion 3400+ CPU
[*]2 gigs ram
[*]1 80 IDE HD
[*]1 1 TB sata HD
[*]1 Haupauge 1600 PCI /w Ir remote
[*]3 Haupauge 1600 PCI capture cards
[/LIST]
This error flashes 3 times on startup after the first Mythbubtu screen I know I have to allocate more memory, but I can't find the meminfo file. I am also not sure how to go about it. 
ioremap failed.  Can't get a window into CX23418 memory and register space
Each capyure card with a CX23418 needs 64 MB of vmalloc address space for the window
Check the output pg 'grep Vmallco /proc /meminfo'
Use the vmalloc" kernel command line option to set VmallocTotal to a larger value
Error -12 on initialization
Have you tried to "Use the vmalloc kernel command line option to set VmallocTotal to a larger value"?–

Yes I have it set now at 512 but have tried 256. I still get the error message if I have more then one capture card. 
Myth still doesn't recognize the capture cards correctly. The front end doesn't connect to the back end data base and I can't download programming. 
The mother board doesn't see the sata drive and neither does Ubuntu.–

I have tried an ATI and an Encore capture card also with no change.
I downloaded the CX18 driver and sudo make and install but with errors also.
All help is appreciated as I am just starting with ubuntu. 

ubuntu seems to run well on this mother board, I just can't get Myth to work.

---

### Post by blm-ubunet on 2014-04-05
I take it you are running 32bit kernel?

Did you change the **grub** boot command to add 
vmalloc=512M

[http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small)

Having 4 cards the same type can make unique identification (for udev rules) tricky.
You may need udev rules if the cards have differing input connections. 

Does the vmalloc cmd cause the mobo to not recognise the SATA HDD? or does that happen with more than 1 tuner card?

---

### Post by Richard_Butler on 2014-04-11
Yes I am runnung 32 bit kernel.
Yes I changed the grub boot command to vmalloc=512m.  I found the wiki page and used it to change my grub file. After I learned about the terminal, sudo command and installed gedit.
As far as the mobo it doesn't see the sata drive at all no matter what I have pluged in. I droped a different IDE drive in and loaded XP and it didn't see the sata drive either, but I didn't have the Mobo XP drivers downloaded. 
I have them now, I'll have to try XP again and install the drivers. Then I can test the mobo.
How would I mount the sata drive in ubuntu ?  Also where are the log files saved ?  I really need to look at them.
Thanks for the reply. I'll keep working on it. The biggest drawback is I only have a couple hours a week to trouble shoot the setup.

---

### Post by blm-ubunet on 2014-04-12
I would look for a BIOS update..this is very old h/w & very possible it will not work with new SATA HDD or HDD bigger than x.
That h/w has no real video update options.

I wouldn't use mythtv to debug if the capture cards are detected (& drivers loaded). There will be messages/warnings/errors reported in kernel logs &/or run:
```
dmesg
```

---

### Post by Richard_Butler on 2014-04-15
This is a copy of my dmesg command,  I am new to ubuntu so I don't know how to interpert most of this.  Any comments welcome.

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-38-generic (buildd@orlo) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #56~precise1-Ubuntu SMP Thu Mar 13 16:23:47 UTC 2014 (Ubuntu 3.8.0-38.56~precise1-generic 3.8.13.19)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffeffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007fff0000-0x000000007fff2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007fff3000-0x000000007fffffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffff0000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI:    /KV8 Pro (VIA K8T800P-8237), BIOS 6.00 PG 07/29/2004
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7fff0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-CFFFF uncachable
[    0.000000]   D0000-D7FFF write-back
[    0.000000]   D8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 00E0000000 mask FFF8000000 write-combining
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000f58b0-0x000f58bf] mapped at [c00f58b0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x1f3fdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1f1fffff] page 2M
[    0.000000]  [mem 0x1f200000-0x1f3fdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x1f3fdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x360ae000-0x3704efff]
[    0.000000] Allocated new RAMDISK: [mem 0x1e45d000-0x1f3fd2c4]
[    0.000000] Move RAMDISK from [mem 0x360ae000-0x3704e2c4] to [mem 0x1e45d000-0x1f3fd2c4]
[    0.000000] ACPI: RSDP 000f7360 00014 (v00 VIAK8T)
[    0.000000] ACPI: RSDT 7fff3000 00030 (v01 VIAK8T AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 7fff3040 00074 (v01 VIAK8T AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 7fff30c0 04C79 (v01 VIAK8T AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 7fff0000 00040
[    0.000000] ACPI: BOOT 7fff7d40 00028 (v01 VIAK8T AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 7fff7d80 0005A (v01 VIAK8T AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1547MB HIGHMEM available.
[    0.000000] 499MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1f3fe000
[    0.000000]   low ram: 0 - 1f3fe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x1f3fdfff]
[    0.000000]   HighMem  [mem 0x1f3fe000-0x7ffeffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7ffeffff]
[    0.000000] On node 0 totalpages: 524159
[    0.000000] free_area_init_node: node 0, pgdat c1932240, node_mem_map dd45c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 968 pages used for memmap
[    0.000000]   Normal zone: 122934 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3096 pages used for memmap
[    0.000000]   HighMem zone: 393178 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] e820: [mem 0x80000000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @dd443000 s34880 r0 d22464 u57344
[    0.000000] pcpu-alloc: s34880 r0 d22464 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520063
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-38-generic root=UUID=133343da-62aa-4e35-9d64-c02cb4080ee2 ro quiet splash vmalloc=512MB vt.handoff=7
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4194048 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (0001f3fe:0007fff0)
[    0.000000] Memory: 2048408k/2097088k available (6370k kernel code, 48228k reserved, 3094k data, 796k init, 1585096k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xdfbfe000 - 0xffbfe000   ( 512 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdf3fe000   ( 499 MB)
[    0.000000]       .init : 0xc193f000 - 0xc1a06000   ( 796 kB)
[    0.000000]       .data : 0xc1638a6d - 0xc193e540   (3094 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1638a6d   (6370 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=1.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=dc806000 soft=dc808000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: Fast TSC calibration failed
[    0.000000] tsc: PIT calibration matches PMTIMER. 1 loops
[    0.000000] tsc: Detected 2247.413 MHz processor
[    0.012003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4494.82 BogoMIPS (lpj=8989652)
[    0.012008] pid_max: default: 32768 minimum: 301
[    0.012064] Security Framework initialized
[    0.012079] AppArmor: AppArmor initialized
[    0.012080] Yama: becoming mindful.
[    0.012144] Mount-cache hash table entries: 512
[    0.012368] Initializing cgroup subsys cpuacct
[    0.012371] Initializing cgroup subsys memory
[    0.012380] Initializing cgroup subsys devices
[    0.012383] Initializing cgroup subsys freezer
[    0.012385] Initializing cgroup subsys blkio
[    0.012387] Initializing cgroup subsys perf_event
[    0.012391] Initializing cgroup subsys hugetlb
[    0.012420] mce: CPU supports 5 MCE banks
[    0.012439] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.012439] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.012439] tlb_flushall_shift: 4
[    0.022780] Freeing SMP alternatives: 24k freed
[    0.024946] ACPI: Core revision 20121018
[    0.032043] ftrace: allocating 28900 entries in 57 pages
[    0.044126] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.045205] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.084481] smpboot: CPU0: AMD Athlon(tm) 64 Processor 3400+ (fam: 0f, model: 04, stepping: 08)
[    0.088000] Performance Events: AMD PMU driver.
[    0.088000] ... version:                0
[    0.088000] ... bit width:              48
[    0.088000] ... generic registers:      4
[    0.088000] ... value mask:             0000ffffffffffff
[    0.088000] ... max period:             00007fffffffffff
[    0.088000] ... fixed-purpose events:   0
[    0.088000] ... event mask:             000000000000000f
[    0.088000] Brought up 1 CPUs
[    0.088000] smpboot: Total of 1 processors activated (4494.82 BogoMIPS)
[    0.088000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.088000] devtmpfs: initialized
[    0.088000] EVM: security.selinux
[    0.088000] EVM: security.SMACK64
[    0.088000] EVM: security.capability
[    0.088000] PM: Registering ACPI NVS region [mem 0x7fff0000-0x7fff2fff] (12288 bytes)
[    0.088000] regulator-dummy: no parameters
[    0.088000] NET: Registered protocol family 16
[    0.088000] EISA bus registered
[    0.088000] node 0 link 0: io port [1000, fffff]
[    0.088000] TOM: 0000000080000000 aka 2048M
[    0.088000] node 0 link 0: mmio [a0000, bffff]
[    0.088000] node 0 link 0: mmio [80000000, ff70ffff]
[    0.088000] bus: [bus 00-ff] on node 0 link 0
[    0.088000] bus: 00 [io  0x0000-0xffff]
[    0.088000] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.088000] bus: 00 [mem 0x80000000-0xfcffffffff]
[    0.088079] ACPI: bus type pci registered
[    0.095525] PCI : PCI BIOS area is rw and x. Use pci=nobios if you want it NX.
[    0.095529] PCI: PCI BIOS revision 2.10 entry at 0xfba50, last bus=1
[    0.095530] PCI: Using configuration type 1 for base access
[    0.096766] bio: create slab <bio-0> at 0
[    0.096873] ACPI: Added _OSI(Module Device)
[    0.096875] ACPI: Added _OSI(Processor Device)
[    0.096877] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.096879] ACPI: Added _OSI(Processor Aggregator Device)
[    0.097470] ACPI: EC: Look up EC in DSDT
[    0.100850] ACPI: Interpreter enabled
[    0.100860] ACPI: (supports S0 S1 S4 S5)
[    0.100878] ACPI: Using IOAPIC for interrupt routing
[    0.104040] ACPI: No dock devices found.
[    0.104046] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.104103] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.104106] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.104342] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.104346] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.104349] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.104351] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.104354] pci_root PNP0A03:00: host bridge window [mem 0x80100000-0xfebfffff] (ignored)
[    0.104356] PCI: root bus 00: hardware-probed resources
[    0.104362] pci_root PNP0A03:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.
[    0.104396] PCI host bridge to bus 0000:00
[    0.104399] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.104402] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.104405] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.104407] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfcffffffff]
[    0.104424] pci 0000:00:00.0: [1106:0282] type 00 class 0x060000
[    0.104434] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xe7ffffff pref]
[    0.104503] pci 0000:00:00.1: [1106:1282] type 00 class 0x060000
[    0.104537] pci 0000:00:00.2: [1106:2282] type 00 class 0x060000
[    0.104571] pci 0000:00:00.3: [1106:3282] type 00 class 0x060000
[    0.104604] pci 0000:00:00.4: [1106:4282] type 00 class 0x060000
[    0.104640] pci 0000:00:00.7: [1106:7282] type 00 class 0x060000
[    0.104675] pci 0000:00:01.0: [1106:b188] type 01 class 0x060400
[    0.104713] pci 0000:00:01.0: supports D1
[    0.104737] pci 0000:00:0c.0: [1131:7130] type 00 class 0x048000
[    0.104751] pci 0000:00:0c.0: reg 10: [mem 0xe8100000-0xe81003ff]
[    0.104805] pci 0000:00:0c.0: supports D1 D2
[    0.104820] pci 0000:00:0e.0: [1106:3119] type 00 class 0x020000
[    0.104832] pci 0000:00:0e.0: reg 10: [io  0xb000-0xb0ff]
[    0.104840] pci 0000:00:0e.0: reg 14: [mem 0xe8101000-0xe81010ff]
[    0.104887] pci 0000:00:0e.0: supports D1 D2
[    0.104890] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.104906] pci 0000:00:0f.0: [1106:3149] type 00 class 0x010400
[    0.104921] pci 0000:00:0f.0: reg 10: [io  0xb400-0xb407]
[    0.104929] pci 0000:00:0f.0: reg 14: [io  0xb800-0xb803]
[    0.104937] pci 0000:00:0f.0: reg 18: [io  0xbc00-0xbc07]
[    0.104946] pci 0000:00:0f.0: reg 1c: [io  0xc000-0xc003]
[    0.104954] pci 0000:00:0f.0: reg 20: [io  0xc400-0xc40f]
[    0.104962] pci 0000:00:0f.0: reg 24: [io  0xc800-0xc8ff]
[    0.105004] pci 0000:00:0f.1: [1106:0571] type 00 class 0x01018a
[    0.105041] pci 0000:00:0f.1: reg 20: [io  0xcc00-0xcc0f]
[    0.105096] pci 0000:00:10.0: [1106:3038] type 00 class 0x0c0300
[    0.105130] pci 0000:00:10.0: reg 20: [io  0xd000-0xd01f]
[    0.105160] pci 0000:00:10.0: supports D1 D2
[    0.105163] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105178] pci 0000:00:10.1: [1106:3038] type 00 class 0x0c0300
[    0.105212] pci 0000:00:10.1: reg 20: [io  0xd400-0xd41f]
[    0.105243] pci 0000:00:10.1: supports D1 D2
[    0.105246] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105262] pci 0000:00:10.2: [1106:3038] type 00 class 0x0c0300
[    0.105296] pci 0000:00:10.2: reg 20: [io  0xd800-0xd81f]
[    0.105327] pci 0000:00:10.2: supports D1 D2
[    0.105329] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105345] pci 0000:00:10.3: [1106:3038] type 00 class 0x0c0300
[    0.105378] pci 0000:00:10.3: reg 20: [io  0xdc00-0xdc1f]
[    0.105409] pci 0000:00:10.3: supports D1 D2
[    0.105412] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105427] pci 0000:00:10.4: [1106:3104] type 00 class 0x0c0320
[    0.105440] pci 0000:00:10.4: reg 10: [mem 0xe8102000-0xe81020ff]
[    0.105492] pci 0000:00:10.4: supports D1 D2
[    0.105495] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105514] pci 0000:00:11.0: [1106:3227] type 00 class 0x060100
[    0.105561] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.105601] pci 0000:00:11.5: [1106:3059] type 00 class 0x040100
[    0.105615] pci 0000:00:11.5: reg 10: [io  0xe000-0xe0ff]
[    0.105672] pci 0000:00:11.5: supports D1 D2
[    0.105689] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.105707] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.105721] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.105736] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.105782] pci 0000:01:00.0: [1002:95c6] type 00 class 0x030000
[    0.105797] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.105805] pci 0000:01:00.0: reg 14: [io  0xa000-0xa0ff]
[    0.105813] pci 0000:01:00.0: reg 18: [mem 0xe8020000-0xe802ffff]
[    0.105835] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.105865] pci 0000:01:00.0: supports D1 D2
[    0.105889] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.105894] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.105898] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xe80fffff]
[    0.105902] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.105909] pci_bus 0000:00: on NUMA node 0
[    0.105950]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.105953]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.107276] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
[    0.107352] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.107429] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[    0.107493] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.107561] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 *10 11 12)
[    0.107617] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.107682] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 *10 11 12)
[    0.107738] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.107831] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *11
[    0.107900] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[    0.107971] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[    0.108078] ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
[    0.108217] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.108219] vgaarb: loaded
[    0.108220] vgaarb: bridge control possible 0000:01:00.0
[    0.108486] SCSI subsystem initialized
[    0.108489] ACPI: bus type scsi registered
[    0.108543] libata version 3.00 loaded.
[    0.108566] ACPI: bus type usb registered
[    0.108589] usbcore: registered new interface driver usbfs
[    0.108602] usbcore: registered new interface driver hub
[    0.108626] usbcore: registered new device driver usb
[    0.108738] PCI: Using ACPI for IRQ routing
[    0.108741] PCI: pci_cache_line_size set to 64 bytes
[    0.108797] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.108800] e820: reserve RAM buffer [mem 0x7fff0000-0x7fffffff]
[    0.108903] NetLabel: Initializing
[    0.108905] NetLabel:  domain hash size = 128
[    0.108906] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.108918] NetLabel:  unlabeled traffic allowed by default
[    0.109024] Switching to clocksource refined-jiffies
[    0.116295] AppArmor: AppArmor Filesystem Enabled
[    0.116337] pnp: PnP ACPI init
[    0.116355] ACPI: bus type pnp registered
[    0.116600] system 00:00: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.116604] system 00:00: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.116607] system 00:00: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.116610] system 00:00: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.116613] system 00:00: [mem 0x80000000-0x800fffff] has been reserved
[    0.116616] system 00:00: [mem 0x7fff0000-0x7fffffff] could not be reserved
[    0.116619] system 00:00: [mem 0xffff0000-0xffffffff] has been reserved
[    0.116622] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.116625] system 00:00: [mem 0x00100000-0x7ffeffff] could not be reserved
[    0.116628] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.116631] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.116634] system 00:00: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.116639] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.116696] system 00:01: [io  0x4000-0x407f] has been reserved
[    0.116699] system 00:01: [io  0x5000-0x500f] has been reserved
[    0.116702] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.117148] system 00:02: [io  0x0b78-0x0b7b] has been reserved
[    0.117152] system 00:02: [io  0x0f78-0x0f7b] has been reserved
[    0.117155] system 00:02: [io  0x0a78-0x0a7b] has been reserved
[    0.117157] system 00:02: [io  0x0e78-0x0e7b] has been reserved
[    0.117160] system 00:02: [io  0x0bbc-0x0bbf] has been reserved
[    0.117163] system 00:02: [io  0x0fbc-0x0fbf] has been reserved
[    0.117166] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.117169] system 00:02: [io  0x0290-0x0297] has been reserved
[    0.117172] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.117185] pnp 00:03: [dma 4]
[    0.117210] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.117251] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.117278] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.117313] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.117412] pnp 00:07: [dma 2]
[    0.117450] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.117633] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.117974] pnp 00:09: [dma 3]
[    0.118027] pnp 00:09: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.118084] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.118104] pnp: PnP ACPI: found 11 devices
[    0.118106] ACPI: ACPI bus type pnp unregistered
[    0.118109] PnPBIOS: Disabled by ACPI PNP
[    0.154178] Switching to clocksource acpi_pm
[    0.154214] pci 0000:01:00.0: BAR 6: assigned [mem 0xe8000000-0xe801ffff pref]
[    0.154218] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.154222] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.154227] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xe80fffff]
[    0.154231] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.154243] pci 0000:00:01.0: setting latency timer to 64
[    0.154247] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.154249] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.154252] pci_bus 0000:00: resource 6 [mem 0x80000000-0xfcffffffff]
[    0.154255] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.154258] pci_bus 0000:01: resource 1 [mem 0xe8000000-0xe80fffff]
[    0.154260] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff pref]
[    0.154301] NET: Registered protocol family 2
[    0.154451] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[    0.154480] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[    0.154511] TCP: Hash tables configured (established 4096 bind 4096)
[    0.154565] TCP: reno registered
[    0.154568] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.154576] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.154629] NET: Registered protocol family 1
[    0.154649] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.154773] pci 0000:01:00.0: Boot video device
[    0.154777] PCI: CLS 32 bytes, default 64
[    0.154820] Trying to unpack rootfs image as initramfs...
[    0.512831] Freeing initrd memory: 16004k freed
[    0.525644] Simple Boot Flag at 0x37 set to 0x1
[    0.525896] Initialise module verification
[    0.525949] audit: initializing netlink socket (disabled)
[    0.525964] type=2000 audit(1397579146.523:1): initialized
[    0.552104] bounce pool size: 64 pages
[    0.552121] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.553762] VFS: Disk quotas dquot_6.5.2
[    0.553813] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.554395] fuse init (API version 7.20)
[    0.554479] msgmni has been set to 936
[    0.554781] Key type asymmetric registered
[    0.554783] Asymmetric key parser 'x509' registered
[    0.554823] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.554848] io scheduler noop registered
[    0.554850] io scheduler deadline registered (default)
[    0.554856] io scheduler cfq registered
[    0.554992] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.555012] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.555138] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.555144] ACPI: Power Button [PWRB]
[    0.555196] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.555199] ACPI: Power Button [PWRF]
[    0.555243] ACPI: processor limited to max C-state 1
[    0.558040] GHES: HEST is not enabled!
[    0.558110] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.578476] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.578511] isapnp: Scanning for PnP cards...
[    0.672438] Linux agpgart interface v0.103
[    0.672464] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0282]
[    0.676244] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    0.677593] brd: module loaded
[    0.678303] loop: module loaded
[    0.678784] libphy: Fixed MDIO Bus: probed
[    0.678870] tun: Universal TUN/TAP device driver, 1.6
[    0.678872] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.678909] PPP generic driver version 2.4.2
[    0.678948] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.678950] ehci-pci: EHCI PCI platform driver
[    0.678979] ehci-pci 0000:00:10.4: EHCI Host Controller
[    0.678986] ehci-pci 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.679049] ehci-pci 0000:00:10.4: irq 21, io mem 0xe8102000
[    0.722626] ehci-pci 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.722663] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.722666] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.722668] usb usb1: Product: EHCI Host Controller
[    0.722671] usb usb1: Manufacturer: Linux 3.8.0-38-generic ehci_hcd
[    0.722673] usb usb1: SerialNumber: 0000:00:10.4
[    0.722770] hub 1-0:1.0: USB hub found
[    0.722776] hub 1-0:1.0: 8 ports detected
[    0.722921] ehci-platform: EHCI generic platform driver
[    0.722932] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.722951] uhci_hcd: USB Universal Host Controller Interface driver
[    0.722970] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.722975] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.722994] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d000
[    0.723025] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.723028] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.723030] usb usb2: Product: UHCI Host Controller
[    0.723033] usb usb2: Manufacturer: Linux 3.8.0-38-generic uhci_hcd
[    0.723035] usb usb2: SerialNumber: 0000:00:10.0
[    0.723124] hub 2-0:1.0: USB hub found
[    0.723130] hub 2-0:1.0: 2 ports detected
[    0.723200] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.723206] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.723224] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d400
[    0.723254] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.723256] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.723259] usb usb3: Product: UHCI Host Controller
[    0.723261] usb usb3: Manufacturer: Linux 3.8.0-38-generic uhci_hcd
[    0.723264] usb usb3: SerialNumber: 0000:00:10.1
[    0.723349] hub 3-0:1.0: USB hub found
[    0.723353] hub 3-0:1.0: 2 ports detected
[    0.723426] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.723431] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.723450] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    0.723481] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.723484] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.723486] usb usb4: Product: UHCI Host Controller
[    0.723489] usb usb4: Manufacturer: Linux 3.8.0-38-generic uhci_hcd
[    0.723491] usb usb4: SerialNumber: 0000:00:10.2
[    0.723576] hub 4-0:1.0: USB hub found
[    0.723580] hub 4-0:1.0: 2 ports detected
[    0.723651] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.723656] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.723674] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000dc00
[    0.723704] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.723707] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.723709] usb usb5: Product: UHCI Host Controller
[    0.723712] usb usb5: Manufacturer: Linux 3.8.0-38-generic uhci_hcd
[    0.723714] usb usb5: SerialNumber: 0000:00:10.3
[    0.723800] hub 5-0:1.0: USB hub found
[    0.723804] hub 5-0:1.0: 2 ports detected
[    0.723932] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.723934] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.724618] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.768265] mousedev: PS/2 mouse device common for all mice
[    0.768374] rtc_cmos 00:04: RTC can wake from S4
[    0.768539] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.768589] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.768693] device-mapper: uevent: version 1.0.3
[    0.768751] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [email]dm-devel@redhat.com[/email]
[    0.768768] EISA: Probing bus 0 at eisa.0
[    0.768771] EISA: Cannot allocate resource for mainboard
[    0.768773] Cannot allocate resource for EISA slot 1
[    0.768775] Cannot allocate resource for EISA slot 2
[    0.768777] Cannot allocate resource for EISA slot 3
[    0.768779] Cannot allocate resource for EISA slot 4
[    0.768781] Cannot allocate resource for EISA slot 5
[    0.768783] Cannot allocate resource for EISA slot 6
[    0.768785] Cannot allocate resource for EISA slot 7
[    0.768786] Cannot allocate resource for EISA slot 8
[    0.768788] EISA: Detected 0 cards.
[    0.768797] cpufreq-nforce2: No nForce2 chipset.
[    0.768800] cpuidle: using governor ladder
[    0.768801] cpuidle: using governor menu
[    0.768804] ledtrig-cpu: registered to indicate activity on CPUs
[    0.768806] EFI Variables Facility v0.08 2004-May-17
[    0.769011] ashmem: initialized
[    0.769137] TCP: cubic registered
[    0.769252] NET: Registered protocol family 10
[    0.769440] NET: Registered protocol family 17
[    0.769455] Key type dns_resolver registered
[    0.769577] Using IPI No-Shortcut mode
[    0.769654] Loading module verification certificates
[    0.773891] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 9014eb7e6b13aa018a78e3591659db32cc75a94c'
[    0.773910] registered taskstats version 1
[    0.776416] Key type trusted registered
[    0.778268] Key type encrypted registered
[    0.910853] rtc_cmos 00:04: setting system clock to 2014-04-15 16:25:47 UTC (1397579147)
[    0.910914] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20121018/processor_perflib-376)
[    0.917634] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    0.917636] powernow-k8: Make sure that your BIOS is up to date and Cool'N'Quiet support is enabled in BIOS setup
[    0.917655] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20121018/processor_perflib-376)
[    0.917664] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.917666] EDD information not available.
[    0.961380] isapnp: No Plug & Play device found
[    0.961435] Freeing unused kernel memory: 796k freed
[    0.961978] Write protecting the kernel text: 6372k
[    0.962029] Write protecting the kernel read-only data: 2552k
[    0.962030] NX-protecting the kernel data: 5916k
[    0.964449] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.981530] udevd[89]: starting version 175
[    1.138544] pata_via 0000:00:0f.1: version 0.3.4
[    1.138721] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 11, using IRQ 20
[    1.138723] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    1.147655] scsi0 : pata_via
[    1.154638] scsi1 : pata_via
[    1.155392] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xcc00 irq 14
[    1.155395] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xcc08 irq 15
[    1.158327] sata_via 0000:00:0f.0: version 2.6
[    1.158393] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.164207] scsi2 : sata_via
[    1.167813] scsi3 : sata_via
[    1.167888] ata3: SATA max UDMA/133 cmd 0xb400 ctl 0xb800 bmdma 0xc400 irq 20
[    1.167891] ata4: SATA max UDMA/133 cmd 0xbc00 ctl 0xc000 bmdma 0xc408 irq 20
[    1.170523] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.15
[    1.170528] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
[    1.170530] Copyright (c) 2004 Red Hat Inc.
[    1.171364] eth0: VIA Networking Velocity Family Gigabit Ethernet Adapter
[    1.171367] eth0: Ethernet Address: 00:50:8d:5e:99:ed
[    1.189723] Floppy drive(s): fd0 is 1.44M
[    1.207824] FDC 0 is a post-1991 82077
[    1.312018] usb 3-1: new low-speed USB device number 2 using uhci_hcd
[    1.316470] ata1.00: ATA-6: WDC WD400BB-00JHC0, 05.01C05, max UDMA/100
[    1.316473] ata1.00: 78165360 sectors, multi 16: LBA 
[    1.316479] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.324316] ata1.00: configured for UDMA/33
[    1.324441] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-00JH 05.0 PQ: 0 ANSI: 5
[    1.324661] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.324710] sd 0:0:0:0: [sda] Write Protect is off
[    1.324714] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.324735] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.325008] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.360807]  sda: sda1 sda2 < sda5 >
[    1.361076] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.486137] usb 3-1: New USB device found, idVendor=0d62, idProduct=a100
[    1.486140] usb 3-1: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    1.486142] usb 3-1: Product: USB Optical Mouse
[    1.486145] usb 3-1: Manufacturer: Darfon
[    1.506744] ata2.00: ATAPI: LITE-ON DVDRW SOHW-1673S, JS02, max UDMA/66
[    1.506757] ata2.01: ATAPI: CD-540E, 1.0A, max UDMA/33
[    1.520223] ata2.00: configured for UDMA/66
[    1.520553] usbcore: registered new interface driver usbhid
[    1.520555] usbhid: USB HID core driver
[    1.526689] tsc: Refined TSC clocksource calibration: 2247.403 MHz
[    1.526697] Switching to clocksource tsc
[    1.528421] input: Darfon USB Optical Mouse as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input3
[    1.528622] hid-generic 0003:0D62:A100.0001: input,hidraw0: USB HID v1.10 Mouse [Darfon USB Optical Mouse] on usb-0000:00:10.1-1/input0
[    1.536271] ata2.01: configured for UDMA/33
[    1.545550] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1673S JS02 PQ: 0 ANSI: 5
[    1.547584] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.547587] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.547684] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.547808] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.548969] scsi 1:0:1:0: CD-ROM            TEAC     CD-540E          1.0A PQ: 0 ANSI: 5
[    1.555921] sr1: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[    1.556006] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.556124] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    6.264017] ata3: SATA link down 1.5 Gbps (SStatus 1 SControl 300)
[    6.476015] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    7.050298] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.669905] init: ureadahead main process (264) terminated with status 5
[   10.158755] Adding 2095100k swap on /dev/sda5.  Priority:-1 extents:1 across:2095100k 
[   11.494214] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.844560] udevd[340]: starting version 175
[   13.223438] lp: driver loaded but no devices found
[   13.663325] parport_pc 00:09: reported by Plug and Play ACPI
[   13.663439] parport0: PC-style at 0x378 (0x778), irq 7 [PCSPP,TRISTATE,EPP]
[   13.752286] lp0: using parport0 (interrupt-driven).
[   13.947531] ppdev: user-space parallel port driver
[   14.469067] microcode: AMD CPU family 0xf not supported
[   14.469827] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.690457] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.745016] Linux video capture interface: v2.00
[   14.993885] [drm] Initialized drm 1.1.0 20060810
[   15.503340] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[   15.503388] saa7130[0]: found at 0000:00:0c.0, rev: 1, irq: 20, latency: 32, mmio: 0xe8100000
[   15.503395] saa7130[0]: subsystem: 1131:2341, board: Encore ENLTV [card=106,autodetected]
[   15.503410] saa7130[0]: board init: gpio is 5d31ff
[   15.740013] Registered IR keymap rc-encore-enltv
[   15.740280] input: saa7134 IR (Encore ENLTV) as /devices/pci0000:00/0000:00:0c.0/rc/rc0/input4
[   15.740412] rc0: saa7134 IR (Encore ENLTV) as /devices/pci0000:00/0000:00:0c.0/rc/rc0
[   15.927466] saa7130[0]: i2c eeprom 00: 31 11 41 23 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   15.927478] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[   15.927487] saa7130[0]: i2c eeprom 20: 41 41 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927495] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927503] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927511] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927519] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927527] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927534] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927542] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927550] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927558] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927566] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927574] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927582] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.927590] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.939334] [drm] radeon defaulting to kernel modesetting.
[   15.939340] [drm] radeon kernel modesetting enabled.
[   15.939768] [drm] initializing kernel modesetting (RV620 0x1002:0x95C6 0x1787:0x0028).
[   15.939786] [drm] register mmio base: 0xE8020000
[   15.939788] [drm] register mmio size: 65536
[   15.940474] ATOM BIOS: RV620LE
[   15.940512] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   15.940526] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   15.940585] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[   15.940589] radeon 0000:01:00.0: GTT: 128M 0xE0000000 - 0xE7FFFFFF
[   15.940597] radeon 0000:01:00.0: VRAM: 512M 0xC0000000 - 0xDFFFFFFF (512M used)
[   15.940929] [drm] Detected VRAM RAM=512M, BAR=256M
[   15.940934] [drm] RAM width 64bits DDR
[   15.941019] [TTM] Zone  kernel: Available graphics memory: 240068 kiB
[   15.941021] [TTM] Zone highmem: Available graphics memory: 1032616 kiB
[   15.941022] [TTM] Initializing pool allocator
[   15.941028] [TTM] Initializing DMA pool allocator
[   15.941058] [drm] radeon: 512M of VRAM memory ready
[   15.941061] [drm] radeon: 128M of GTT memory ready.
[   15.941084] [drm] GART: num cpu pages 32768, num gpu pages 32768
[   15.942016] [drm] Loading RV620 Microcode
[   16.616009] All bytes are equal. It is not a TEA5767
[   16.616018] tuner 1-0060: Tuner -1 found with type(s) Radio TV.
[   16.821729] radeon 0000:01:00.0: WB disabled
[   16.821740] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000e0000004 and cpu addr 0xdfc4a004
[   16.821744] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x00000000e0000c0c and cpu addr 0xdfc4ac0c
[   16.821748] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.821749] [drm] Driver supports precise vblank timestamp query.
[   16.821798] [drm] radeon: irq initialized.
[   16.853904] tuner-simple 1-0060: creating new instance
[   16.853907] tuner-simple 1-0060: type set to 69 (Tena TNF 5335 and similar models)
[   16.854642] [drm] ring test on 0 succeeded in 1 usecs
[   16.854704] [drm] ring test on 3 succeeded in 1 usecs
[   16.854905] [drm] ib test on ring 0 succeeded in 0 usecs
[   16.854929] [drm] ib test on ring 3 succeeded in 1 usecs
[   16.855980] [drm] Radeon Display Connectors
[   16.855982] [drm] Connector 0:
[   16.855984] [drm]   DIN-1
[   16.855985] [drm]   Encoders:
[   16.855987] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   16.855988] [drm] Connector 1:
[   16.855990] [drm]   DVI-I-1
[   16.855991] [drm]   HPD2
[   16.855994] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   16.856016] [drm]   Encoders:
[   16.856018] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   16.856019] [drm]     DFP1: INTERNAL_UNIPHY
[   16.856021] [drm] Connector 2:
[   16.856022] [drm]   DVI-I-2
[   16.856023] [drm]   HPD1
[   16.856026] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   16.856027] [drm]   Encoders:
[   16.856028] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   16.856030] [drm]     DFP2: INTERNAL_KLDSCP_LVTMA
[   16.856076] [drm] Internal thermal controller without fan control
[   16.856166] [drm] radeon: power management initialized
[   16.903027] saa7130[0]: registered device video0 [v4l2]
[   16.903136] saa7130[0]: registered device vbi0
[   16.903230] saa7130[0]: registered device radio0
[   16.903508] snd_via82xx 0000:00:11.5: setting latency timer to 64
[   16.904413] type=1400 audit(1397579163.489:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=570 comm="apparmor_parser"
[   16.904878] type=1400 audit(1397579163.489:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=570 comm="apparmor_parser"
[   16.905146] type=1400 audit(1397579163.489:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=570 comm="apparmor_parser"
[   16.905659] type=1400 audit(1397579163.489:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=579 comm="apparmor_parser"
[   16.906122] type=1400 audit(1397579163.489:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=579 comm="apparmor_parser"
[   16.906386] type=1400 audit(1397579163.489:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=579 comm="apparmor_parser"
[   17.008155] [drm] fb mappable at 0xD0082000
[   17.008160] [drm] vram apper at 0xD0000000
[   17.008162] [drm] size 5242880
[   17.008164] [drm] fb depth is 24
[   17.008165] [drm]    pitch is 5120
[   17.008385] fbcon: radeondrmfb (fb0) is primary device
[   17.010470] saa7134 ALSA driver for DMA sound loaded
[   17.010472] saa7130[0]/alsa: Encore ENLTV doesn't support digital audio
[   17.087034] type=1400 audit(1397579163.673:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=642 comm="apparmor_parser"
[   17.087781] type=1400 audit(1397579163.673:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=643 comm="apparmor_parser"
[   17.208247] Console: switching to colour frame buffer device 160x64
[   17.285400] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   17.285401] radeon 0000:01:00.0: registered panic notifier
[   17.293384] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:00.0 on minor 0
[   19.623980] init: failsafe main process (693) killed by TERM signal
[   27.927411] type=1400 audit(1397579174.509:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=809 comm="apparmor_parser"
[   27.927792] type=1400 audit(1397579174.509:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=809 comm="apparmor_parser"
[   27.931637] type=1400 audit(1397579174.513:12): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=812 comm="apparmor_parser"
[   27.932356] type=1400 audit(1397579174.517:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=812 comm="apparmor_parser"
[   27.932622] type=1400 audit(1397579174.517:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=812 comm="apparmor_parser"
[   28.002759] type=1400 audit(1397579174.589:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=814 comm="apparmor_parser"
[   28.006348] type=1400 audit(1397579174.589:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=815 comm="apparmor_parser"
[   28.096447] type=1400 audit(1397579174.681:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=817 comm="apparmor_parser"
[   28.740105] lirc_dev: IR Remote Control driver registered, major 250 
[   28.915287] type=1400 audit(1397579175.497:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=916 comm="apparmor_parser"
[   28.958544] Velocity is AUTO mode
[   30.661487] eth0: Link auto-negotiation speed 100M bps full duplex
[   56.696423] init: mythtv-backend main process (1408) terminated with status 1
[   56.696456] init: mythtv-backend main process ended, respawning
[   56.806257] init: mythtv-backend main process (1912) terminated with status 1
[   56.806295] init: mythtv-backend main process ended, respawning
[   56.910283] init: mythtv-backend main process (1923) terminated with status 1
[   56.910322] init: mythtv-backend respawning too fast, stopped

---

### Post by blm-ubunet on 2014-04-16
The only thing that stands out (to me) is the re-spawning backend at startup.
The first attempt at backend start times out after 20sec.

Assuming you are using *buntu & upstart..
I would guess this is caused by failure of "network interface up test" in the mythtv-backend upstart script.

There is an example (latest version) of this script on mythtv wiki
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

Could try experimenting with disabling apparmor..
Check you have assigned a static IP address.
Check you're not trying to use IPv6.

---

### Post by Richard_Butler on 2014-04-27
Here's an update on my progress.  After a couple of months of studying, tweaking, pulling my hair out I managed to lock up the front end and could only continue if I interrupted the boot before the front end loaded.  I decided to start fresh and I am glad I did.
Pulled 3 of the capture cards out and left the one with the IR port.  The re install went with out a hitch and I could watch TV on that card.  I installed each card one at a time and the next two installed also. the last card gave me the vmallmoc error and it wouldn't change no matter what I set vmalloc to. Must be a problem on that card or maybe my hardware will only support 3 cards.  Will test it at a later date.
I have a working mythbox with 3 capture cards.
I had to edit the channel list XMlID to match my schedules direct list and manually download the mythfilldatabase to have the programs list correctly.

Things to do.
My Sata drive isn't working yet.        Need to update BIOS
The myth plugins need some work.     Weather,internet video,games
DVD doesn't play a dvd.
Remote control isn't working.

This posting can be **closed** if I can't make any progress I'll start a new one.
Thank you very much for all your help. I am learning a lot along the way.

---

