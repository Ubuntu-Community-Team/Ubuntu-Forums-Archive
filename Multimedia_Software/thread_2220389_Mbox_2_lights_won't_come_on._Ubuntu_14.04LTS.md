---
title: "Mbox 2 lights won't come on. Ubuntu 14.04LTS"
date: 2014-04-27
forum: Multimedia Software
---

### Post by paul-logston on 2014-04-27
Hello,

I am trying to get Ubuntu 14.04 LTS to recognize my Mbox 2. From what I have read, the drivers for the Mbox 2 were integrated into ALSA just before the linux kernal version 3.8 was released. I believe that Ubuntu 14.04 LTS uses the 3.18 linux kernal. I thought that my Mbox 2 would be recognized by my computer by simply plugging the Mbox 2 into my computer via USB. The Mbox 2 was not recognized. None of the lights on the front of the Mbox 2 came on. After reading many blogs and forums, I have executed a few command line commands and gotten some clue as to what is going on. I have listed the commands I have run at the command line and their output below.

```

paul@GX620:~$ lsusb
Bus 001 Device 005: ID 1058:0704 Western Digital Technologies, Inc. Passport External HDD
Bus 001 Device 004: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 0dba:3000  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
I believe Bus 005 Device 004: ID 0dba:3000   is my Mbox 2.

```

paul@GX620:~$ lspci -v | grep -A7 -i "audio"
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
    Subsystem: Dell OptiPlex GX620
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ec00 [size=256]
    I/O ports at e8c0 [size=64]
    Memory at febffa00 (32-bit, non-prefetchable) [size=512]
    Memory at febff900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

```

```

paul@GX620:~$ pactl stat
Currently in use: 1 blocks containing 64.0 KiB bytes total.
Allocated during whole lifetime: 1543816 blocks containing 2.6 GiB bytes total.
Sample cache size: 0 B
Server String: unix:/run/user/1000/pulse/native
Library Protocol Version: 28
Server Protocol Version: 28
Is Local: yes
Client Index: 65
Tile Size: 65496
User Name: paul
Host Name: GX620
Server Name: pulseaudio
Server Version: 4.0
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1e.2.analog-stereo
Default Source: alsa_input.pci-0000_00_1e.2.analog-stereo
Cookie: 613b:2a9e

```

```

paul@GX620:~$ dmesg | grep -i .
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-24-generic (buildd@roseapple) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 (Ubuntu 3.13.0-24.46-generic 3.13.9)
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
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000dfe86bff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dfe86c00-0x00000000dfe88bff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000dfe88c00-0x00000000dfe8abff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dfe8ac00-0x00000000dfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed9ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000feefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: Dell Inc.                 OptiPlex GX620               /0FH884, BIOS A11 11/30/2006
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0xdfe86 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 0DFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3583MB, range: 1MB, type UC
[    0.000000] total RAM covered: 3583M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3583MB, range: 1MB, type UC
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000fe710-0x000fe71f] mapped at [c00fe710]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b88000, 0x01b88fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35af2000-0x36d70fff]
[    0.000000] ACPI: RSDP 000feb00 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 000fd257 00005C (v01 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: FACP 000fd34f 0000F4 (v03 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: DSDT fffd4952 003DA4 (v01   DELL    dt_ex 00001000 INTL 20050309)
[    0.000000] ACPI: FACS dfe86c00 000040
[    0.000000] ACPI: SSDT fffd8815 0000AA (v01   DELL    st_ex 00001000 INTL 20050309)
[    0.000000] ACPI: APIC 000fd443 000072 (v01 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: BOOT 000fd4b5 000028 (v01 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: ASF! 000fd4dd 000067 (v16 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: MCFG 000fd544 00003E (v01 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: HPET 000fd582 000038 (v01 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2690MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b89000, 0x01b89fff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0xdfe85fff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009ffff]
[    0.000000]   node   0: [mem 0x00100000-0xdfe85fff]
[    0.000000] On node 0 totalpages: 917029
[    0.000000] free_area_init_node: node 0, pgdat c1990a80, node_mem_map f3ef2020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3999 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 5382 pages used for memmap
[    0.000000]   HighMem zone: 688776 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] e820: [mem 0xe0000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb4000 s36096 r0 d21248 u57344
[    0.000000] pcpu-alloc: s36096 r0 d21248 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 915245
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7337000 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000dfe86)
[    0.000000] Memory: 3600348K/3668116K available (6507K kernel code, 641K rwdata, 2752K rodata, 872K init, 924K bss, 67768K reserved, 2755104K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19ae000 - 0xc1a88000   ( 872 kB)
[    0.000000]       .data : 0xc165b0b2 - 0xc19ad4c0   (3401 kB)
[    0.000000]       .text : 0xc1000000 - 0xc165b0b2   (6508 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f3808000 soft=f380a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3391.619 MHz processor
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6783.23 BogoMIPS (lpj=13566476)
[    0.004007] pid_max: default: 32768 minimum: 301
[    0.004046] Security Framework initialized
[    0.004070] AppArmor: AppArmor initialized
[    0.004073] Yama: becoming mindful.
[    0.004140] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004144] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004420] Initializing cgroup subsys memory
[    0.004429] Initializing cgroup subsys devices
[    0.004432] Initializing cgroup subsys freezer
[    0.004435] Initializing cgroup subsys blkio
[    0.004439] Initializing cgroup subsys perf_event
[    0.004444] Initializing cgroup subsys hugetlb
[    0.004486] CPU: Physical Processor ID: 0
[    0.004489] CPU: Processor Core ID: 0
[    0.004493] mce: CPU supports 4 MCE banks
[    0.004506] CPU0: Thermal monitoring enabled (TM1)
[    0.004522] Last level iTLB entries: 4KB 128, 2MB 128, 4MB 128
[    0.004522] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 64
[    0.004522] tlb_flushall_shift: 6
[    0.004960] Freeing SMP alternatives memory: 32K (c1a88000 - c1a90000)
[    0.008842] ACPI: Core revision 20131115
[    0.095353] ACPI: All ACPI Tables successfully acquired
[    0.095684] ftrace: allocating 27695 entries in 55 pages
[    0.108118] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.108506] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.150016] smpboot: CPU0: Intel(R) Pentium(R) D CPU 3.40GHz (fam: 0f, model: 06, stepping: 04)
[    0.152204] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.152214] ... version:                0
[    0.152217] ... bit width:              40
[    0.152219] ... generic registers:      18
[    0.152221] ... value mask:             000000ffffffffff
[    0.152223] ... max period:             0000007fffffffff
[    0.152225] ... fixed-purpose events:   0
[    0.152227] ... event mask:             000000000003ffff
[    0.154640] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.154771] CPU 1 irqstacks, hard=f3900000 soft=f3902000
[    0.154774] x86: Booting SMP configuration:
[    0.008000] Initializing CPU#1
[    0.154777] .... node  #0, CPUs:      #1
[    0.167855] x86: Booted up 1 node, 2 CPUs
[    0.167861] smpboot: Total of 2 processors activated (13566.47 BogoMIPS)
[    0.168160] devtmpfs: initialized
[    0.168291] EVM: security.selinux
[    0.168294] EVM: security.SMACK64
[    0.168296] EVM: security.ima
[    0.168298] EVM: security.capability
[    0.168334] PM: Registering ACPI NVS region [mem 0xdfe86c00-0xdfe88bff] (8192 bytes)
[    0.169487] pinctrl core: initialized pinctrl subsystem
[    0.169589] regulator-dummy: no parameters
[    0.169629] RTC time: 15:28:39, date: 04/27/14
[    0.169684] NET: Registered protocol family 16
[    0.169892] EISA bus registered
[    0.169896] cpuidle: using governor ladder
[    0.169899] cpuidle: using governor menu
[    0.169987] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.169991] ACPI: bus type PCI registered
[    0.169995] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.172096] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.172101] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.172103] PCI: Using MMCONFIG for extended config space
[    0.172105] PCI: Using configuration type 1 for base access
[    0.173667] bio: create slab <bio-0> at 0
[    0.173667] ACPI: Added _OSI(Module Device)
[    0.173667] ACPI: Added _OSI(Processor Device)
[    0.173667] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.173667] ACPI: Added _OSI(Processor Aggregator Device)
[    0.192923] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.203612] ACPI: Interpreter enabled
[    0.203642] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.203665] ACPI: (supports S0 S1 S3 S4 S5)
[    0.203668] ACPI: Using IOAPIC for interrupt routing
[    0.204079] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.207103] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.340039] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.340052] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.340068] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.372034] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.372041] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.372047] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.372052] acpi PNP0A03:00: host bridge window [mem 0x000c0000-0x000effff] (ignored)
[    0.372056] acpi PNP0A03:00: host bridge window [mem 0x000f0000-0x000fffff] (ignored)
[    0.372062] acpi PNP0A03:00: host bridge window [mem 0xdff00000-0xefffffff] (ignored)
[    0.372070] acpi PNP0A03:00: host bridge window [mem 0xf4000000-0xfebfffff] (ignored)
[    0.372073] acpi PNP0A03:00: host bridge window [mem 0xffa80800-0xffa80bff] (ignored)
[    0.372077] PCI: root bus 00: using default resources
[    0.372081] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.372819] PCI host bridge to bus 0000:00
[    0.372825] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.372829] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.372833] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]
[    0.372846] pci 0000:00:00.0: [8086:2770] type 00 class 0x060000
[    0.373240] pci 0000:00:01.0: [8086:2771] type 01 class 0x060400
[    0.373302] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.373620] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.373702] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.373789] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.374111] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.374164] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
[    0.374250] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.374573] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.374629] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.374679] pci 0000:00:1d.0: reg 0x20: [io  0xff80-0xff9f]
[    0.375013] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.375062] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.375112] pci 0000:00:1d.1: reg 0x20: [io  0xff60-0xff7f]
[    0.375447] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.375496] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.375545] pci 0000:00:1d.2: reg 0x20: [io  0xff40-0xff5f]
[    0.375883] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.375932] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.375981] pci 0000:00:1d.3: reg 0x20: [io  0xff20-0xff3f]
[    0.376317] pci 0000:00:1d.3: System wakeup disabled by ACPI
[    0.376375] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.376400] pci 0000:00:1d.7: reg 0x10: [mem 0xffa80800-0xffa80bff]
[    0.376497] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.376861] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.377230] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.377282] pci 0000:00:1e.2: [8086:27de] type 00 class 0x040100
[    0.377301] pci 0000:00:1e.2: reg 0x10: [io  0xec00-0xecff]
[    0.377312] pci 0000:00:1e.2: reg 0x14: [io  0xe8c0-0xe8ff]
[    0.377323] pci 0000:00:1e.2: reg 0x18: [mem 0xfebffa00-0xfebffbff]
[    0.377334] pci 0000:00:1e.2: reg 0x1c: [mem 0xfebff900-0xfebff9ff]
[    0.377385] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.377743] pci 0000:00:1f.0: [8086:27b8] type 00 class 0x060100
[    0.377836] pci 0000:00:1f.0: address space collision: [io  0x0800-0x087f] conflicts with ACPI CPU throttle [??? 0x00000810-0x00000815 flags 0x80000000]
[    0.377843] pci 0000:00:1f.0: quirk: [io  0x0880-0x08bf] claimed by ICH6 GPIO
[    0.377848] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0c00 (mask 007f)
[    0.377853] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 00e0 (mask 0007)
[    0.378234] pci 0000:00:1f.1: [8086:27df] type 00 class 0x01018a
[    0.378251] pci 0000:00:1f.1: reg 0x10: [io  0x01f0-0x01f7]
[    0.378263] pci 0000:00:1f.1: reg 0x14: [io  0x03f4-0x03f7]
[    0.378274] pci 0000:00:1f.1: reg 0x18: [io  0x0170-0x0177]
[    0.378286] pci 0000:00:1f.1: reg 0x1c: [io  0x0374-0x0377]
[    0.378297] pci 0000:00:1f.1: reg 0x20: [io  0xffa0-0xffaf]
[    0.378664] pci 0000:00:1f.2: [8086:27c0] type 00 class 0x01018f
[    0.378683] pci 0000:00:1f.2: reg 0x10: [io  0xfe00-0xfe07]
[    0.378694] pci 0000:00:1f.2: reg 0x14: [io  0xfe10-0xfe13]
[    0.378705] pci 0000:00:1f.2: reg 0x18: [io  0xfe20-0xfe27]
[    0.378715] pci 0000:00:1f.2: reg 0x1c: [io  0xfe30-0xfe33]
[    0.378725] pci 0000:00:1f.2: reg 0x20: [io  0xfea0-0xfeaf]
[    0.378769] pci 0000:00:1f.2: PME# supported from D3hot
[    0.379120] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.379180] pci 0000:00:1f.3: reg 0x20: [io  0xe8a0-0xe8bf]
[    0.379614] pci 0000:01:00.0: [1002:5b62] type 00 class 0x030000
[    0.379635] pci 0000:01:00.0: reg 0x10: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.379650] pci 0000:01:00.0: reg 0x18: [mem 0xfe9e0000-0xfe9effff 64bit]
[    0.379660] pci 0000:01:00.0: reg 0x20: [io  0xdc00-0xdcff]
[    0.379678] pci 0000:01:00.0: reg 0x30: [mem 0xfea00000-0xfea1ffff pref]
[    0.379719] pci 0000:01:00.0: supports D1 D2
[    0.379779] pci 0000:01:00.1: [1002:5b72] type 00 class 0x038000
[    0.379797] pci 0000:01:00.1: reg 0x10: [mem 0xfe9f0000-0xfe9fffff 64bit]
[    0.379866] pci 0000:01:00.1: supports D1 D2
[    0.384021] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.384029] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.384037] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.384047] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.384149] pci 0000:02:00.0: [14e4:1677] type 00 class 0x020000
[    0.384177] pci 0000:02:00.0: reg 0x10: [mem 0xfe8f0000-0xfe8fffff 64bit]
[    0.384315] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.392022] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.392033] pci 0000:00:1c.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.392117] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.392126] pci 0000:00:1c.1:   bridge window [mem 0xfe700000-0xfe7fffff]
[    0.392194] pci 0000:04:02.0: [104c:8024] type 00 class 0x0c0010
[    0.392217] pci 0000:04:02.0: reg 0x10: [mem 0xfe6fb800-0xfe6fbfff]
[    0.392230] pci 0000:04:02.0: reg 0x14: [mem 0xfe6fc000-0xfe6fffff]
[    0.392312] pci 0000:04:02.0: supports D1 D2
[    0.392315] pci 0000:04:02.0: PME# supported from D0 D1 D2 D3hot
[    0.392407] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.392415] pci 0000:00:1e.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.392423] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.392427] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.392455] pci_bus 0000:00: on NUMA node 0
[    0.406233] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.406743] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.407268] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.407830] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.408332] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.408867] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.409388] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.409888] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.410138] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.410149] ACPI: \_SB_.PCI0: notify handler is installed
[    0.410186] Found 1 acpi root devices
[    0.410296] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.410296] vgaarb: loaded
[    0.410296] vgaarb: bridge control possible 0000:01:00.0
[    0.410296] SCSI subsystem initialized
[    0.410296] libata version 3.00 loaded.
[    0.410296] ACPI: bus type USB registered
[    0.410296] usbcore: registered new interface driver usbfs
[    0.410296] usbcore: registered new interface driver hub
[    0.410296] usbcore: registered new device driver usb
[    0.410296] PCI: Using ACPI for IRQ routing
[    0.412810] PCI: pci_cache_line_size set to 64 bytes
[    0.412871] e820: reserve RAM buffer [mem 0xdfe86c00-0xdfffffff]
[    0.413001] NetLabel: Initializing
[    0.413004] NetLabel:  domain hash size = 128
[    0.413006] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.413026] NetLabel:  unlabeled traffic allowed by default
[    0.413047] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.413047] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.413047] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.414156] Switched to clocksource hpet
[    0.423045] AppArmor: AppArmor Filesystem Enabled
[    0.423086] pnp: PnP ACPI init
[    0.423107] ACPI: bus type PNP registered
[    0.425926] pnp 00:00: disabling [io  0x0800-0x085f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x0800-0x087f]
[    0.425932] pnp 00:00: disabling [io  0x0860-0x08ff] because it overlaps 0000:00:1f.0 BAR 13 [io  0x0800-0x087f]
[    0.425990] system 00:00: [io  0x0c00-0x0c7f] has been reserved
[    0.425997] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.426202] pnp 00:01: [dma 4]
[    0.426233] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.426433] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.426601] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.426778] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.435217] pnp 00:05: [dma 0 disabled]
[    0.436265] pnp 00:05: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.439260] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.496115] system 00:07: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.496121] system 00:07: [mem 0x00100000-0x00ffffff] could not be reserved
[    0.496125] system 00:07: [mem 0x01000000-0xdfe86bff] could not be reserved
[    0.496129] system 00:07: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.496133] system 00:07: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.496137] system 00:07: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.496141] system 00:07: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.496145] system 00:07: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.496149] system 00:07: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.496153] system 00:07: [mem 0xffc00000-0xffffffff] has been reserved
[    0.496158] system 00:07: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.499397] system 00:08: [io  0x0100-0x01fe] could not be reserved
[    0.499402] system 00:08: [io  0x0200-0x0277] has been reserved
[    0.499406] system 00:08: [io  0x0280-0x02e7] has been reserved
[    0.499409] system 00:08: [io  0x02f0-0x02f7] has been reserved
[    0.499413] system 00:08: [io  0x0300-0x0377] could not be reserved
[    0.499416] system 00:08: [io  0x0380-0x03bb] has been reserved
[    0.499420] system 00:08: [io  0x03c0-0x03e7] has been reserved
[    0.499424] system 00:08: [io  0x03f6-0x03f7] could not be reserved
[    0.499427] system 00:08: [io  0x0400-0x04cf] has been reserved
[    0.499431] system 00:08: [io  0x04d2-0x057f] has been reserved
[    0.499435] system 00:08: [io  0x0580-0x0677] has been reserved
[    0.499438] system 00:08: [io  0x0680-0x0777] has been reserved
[    0.499442] system 00:08: [io  0x0780-0x07bb] has been reserved
[    0.499445] system 00:08: [io  0x07c0-0x07ff] has been reserved
[    0.499449] system 00:08: [io  0x08e0-0x08ff] has been reserved
[    0.499453] system 00:08: [io  0x0900-0x09fe] has been reserved
[    0.499456] system 00:08: [io  0x0a00-0x0afe] has been reserved
[    0.499460] system 00:08: [io  0x0b00-0x0bfe] has been reserved
[    0.499463] system 00:08: [io  0x0c80-0x0caf] has been reserved
[    0.499467] system 00:08: [io  0x0cb0-0x0cbf] has been reserved
[    0.499471] system 00:08: [io  0x0cc0-0x0cf7] has been reserved
[    0.499474] system 00:08: [io  0x0d00-0x0dfe] has been reserved
[    0.499478] system 00:08: [io  0x0e00-0x0efe] has been reserved
[    0.499482] system 00:08: [io  0x0f00-0x0ffe] has been reserved
[    0.499486] system 00:08: [io  0x2000-0x20fe] has been reserved
[    0.499489] system 00:08: [io  0x2100-0x21fe] has been reserved
[    0.499493] system 00:08: [io  0x2200-0x22fe] has been reserved
[    0.499497] system 00:08: [io  0x2300-0x23fe] has been reserved
[    0.499500] system 00:08: [io  0x2400-0x24fe] has been reserved
[    0.499504] system 00:08: [io  0x2500-0x25fe] has been reserved
[    0.499508] system 00:08: [io  0x2600-0x26fe] has been reserved
[    0.499512] system 00:08: [io  0x2700-0x27fe] has been reserved
[    0.499515] system 00:08: [io  0x2800-0x28fe] has been reserved
[    0.499519] system 00:08: [io  0x2900-0x29fe] has been reserved
[    0.499523] system 00:08: [io  0x2a00-0x2afe] has been reserved
[    0.499527] system 00:08: [io  0x2b00-0x2bfe] has been reserved
[    0.499530] system 00:08: [io  0x2c00-0x2cfe] has been reserved
[    0.499534] system 00:08: [io  0x2d00-0x2dfe] has been reserved
[    0.499538] system 00:08: [io  0x2e00-0x2efe] has been reserved
[    0.499542] system 00:08: [io  0x2f00-0x2ffe] has been reserved
[    0.499546] system 00:08: [io  0x5000-0x50fe] has been reserved
[    0.499550] system 00:08: [io  0x5100-0x51fe] has been reserved
[    0.499553] system 00:08: [io  0x5200-0x52fe] has been reserved
[    0.499557] system 00:08: [io  0x5300-0x53fe] has been reserved
[    0.499561] system 00:08: [io  0x5400-0x54fe] has been reserved
[    0.499565] system 00:08: [io  0x5500-0x55fe] has been reserved
[    0.499569] system 00:08: [io  0x5600-0x56fe] has been reserved
[    0.499572] system 00:08: [io  0x5700-0x57fe] has been reserved
[    0.499576] system 00:08: [io  0x5800-0x58fe] has been reserved
[    0.499580] system 00:08: [io  0x5900-0x59fe] has been reserved
[    0.499584] system 00:08: [io  0x5a00-0x5afe] has been reserved
[    0.499588] system 00:08: [io  0x5b00-0x5bfe] has been reserved
[    0.499592] system 00:08: [io  0x5c00-0x5cfe] has been reserved
[    0.499602] system 00:08: [io  0x5d00-0x5dfe] has been reserved
[    0.499606] system 00:08: [io  0x5e00-0x5efe] has been reserved
[    0.499610] system 00:08: [io  0x5f00-0x5ffe] has been reserved
[    0.499614] system 00:08: [io  0x6000-0x60fe] has been reserved
[    0.499618] system 00:08: [io  0x6100-0x61fe] has been reserved
[    0.499622] system 00:08: [io  0x6200-0x62fe] has been reserved
[    0.499626] system 00:08: [io  0x6300-0x63fe] has been reserved
[    0.499631] system 00:08: [io  0x6400-0x64fe] has been reserved
[    0.499635] system 00:08: [io  0x6500-0x65fe] has been reserved
[    0.499639] system 00:08: [io  0x6600-0x66fe] has been reserved
[    0.499643] system 00:08: [io  0x6700-0x67fe] has been reserved
[    0.499647] system 00:08: [io  0x6800-0x68fe] has been reserved
[    0.499651] system 00:08: [io  0x6900-0x69fe] has been reserved
[    0.499656] system 00:08: [io  0x6a00-0x6afe] has been reserved
[    0.499660] system 00:08: [io  0x6b00-0x6bfe] has been reserved
[    0.499664] system 00:08: [io  0x6c00-0x6cfe] has been reserved
[    0.499668] system 00:08: [io  0x6d00-0x6dfe] has been reserved
[    0.499673] system 00:08: [io  0x6e00-0x6efe] has been reserved
[    0.499677] system 00:08: [io  0x6f00-0x6ffe] has been reserved
[    0.499682] system 00:08: [io  0xa000-0xa0fe] has been reserved
[    0.499686] system 00:08: [io  0xa100-0xa1fe] has been reserved
[    0.499691] system 00:08: [io  0xa200-0xa2fe] has been reserved
[    0.499695] system 00:08: [io  0xa300-0xa3fe] has been reserved
[    0.499699] system 00:08: [io  0xa400-0xa4fe] has been reserved
[    0.499704] system 00:08: [io  0xa500-0xa5fe] has been reserved
[    0.499708] system 00:08: [io  0xa600-0xa6fe] has been reserved
[    0.499713] system 00:08: [io  0xa700-0xa7fe] has been reserved
[    0.499718] system 00:08: [io  0xa800-0xa8fe] has been reserved
[    0.499722] system 00:08: [io  0xa900-0xa9fe] has been reserved
[    0.499727] system 00:08: [io  0xaa00-0xaafe] has been reserved
[    0.499732] system 00:08: [io  0xab00-0xabfe] has been reserved
[    0.499736] system 00:08: [io  0xac00-0xacfe] has been reserved
[    0.499741] system 00:08: [io  0xad00-0xadfe] has been reserved
[    0.499745] system 00:08: [io  0xae00-0xaefe] has been reserved
[    0.499750] system 00:08: [io  0xaf00-0xaffe] has been reserved
[    0.499755] system 00:08: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.499758] system 00:08: [mem 0xfeda0000-0xfedacfff] has been reserved
[    0.499763] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.499771] pnp: PnP ACPI: found 9 devices
[    0.499774] ACPI: bus type PNP unregistered
[    0.499779] PnPBIOS: Disabled by ACPI PNP
[    0.536656] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.536665] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.536677] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.536682] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.536699] pci 0000:00:1f.0: BAR 13: [io  0x0800-0x087f] has bogus alignment
[    0.536706] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.536710] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.536713] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.536717] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.536725] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf4000000-0xf41fffff 64bit pref]
[    0.536730] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf4200000-0xf43fffff 64bit pref]
[    0.536736] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.536743] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.536748] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.536753] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.536758] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.536763] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.536770] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.536774] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.536781] pci 0000:00:1c.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.536787] pci 0000:00:1c.0:   bridge window [mem 0xf4000000-0xf41fffff 64bit pref]
[    0.536794] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.536798] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.536805] pci 0000:00:1c.1:   bridge window [mem 0xfe700000-0xfe7fffff]
[    0.536810] pci 0000:00:1c.1:   bridge window [mem 0xf4200000-0xf43fffff 64bit pref]
[    0.536818] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.536825] pci 0000:00:1e.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.536836] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.536839] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.536843] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.536846] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfeafffff]
[    0.536849] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.536853] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.536856] pci_bus 0000:02: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.536859] pci_bus 0000:02: resource 2 [mem 0xf4000000-0xf41fffff 64bit pref]
[    0.536863] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.536866] pci_bus 0000:03: resource 1 [mem 0xfe700000-0xfe7fffff]
[    0.536869] pci_bus 0000:03: resource 2 [mem 0xf4200000-0xf43fffff 64bit pref]
[    0.536873] pci_bus 0000:04: resource 1 [mem 0xfe600000-0xfe6fffff]
[    0.536876] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
[    0.536879] pci_bus 0000:04: resource 5 [mem 0x00000000-0xfffffffff]
[    0.536926] NET: Registered protocol family 2
[    0.537122] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.537145] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.537179] TCP: Hash tables configured (established 8192 bind 8192)
[    0.537205] TCP: reno registered
[    0.537210] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.537220] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.537290] NET: Registered protocol family 1
[    0.540260] pci 0000:01:00.0: Boot video device
[    0.540274] PCI: CLS 64 bytes, default 64
[    0.540347] Trying to unpack rootfs image as initramfs...
[    1.008163] Freeing initrd memory: 18940K (f5af2000 - f6d71000)
[    1.008290] Simple Boot Flag at 0x7a set to 0x1
[    1.008435] microcode: CPU0 sig=0xf64, pf=0x4, revision=0x4
[    1.008450] microcode: CPU1 sig=0xf64, pf=0x4, revision=0x4
[    1.008568] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.008573] Scanning for low memory corruption every 60 seconds
[    1.008935] Initialise system trusted keyring
[    1.008989] audit: initializing netlink socket (disabled)
[    1.009003] type=2000 audit(1398612520.008:1): initialized
[    1.035376] bounce pool size: 64 pages
[    1.035399] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.037677] VFS: Disk quotas dquot_6.5.2
[    1.037743] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.038429] fuse init (API version 7.22)
[    1.038587] msgmni has been set to 1687
[    1.038666] Key type big_key registered
[    1.039323] Key type asymmetric registered
[    1.039327] Asymmetric key parser 'x509' registered
[    1.039393] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.039462] io scheduler noop registered
[    1.039467] io scheduler deadline registered (default)
[    1.039516] io scheduler cfq registered
[    1.039988] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.040383] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.040758] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    1.040866] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.040892] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.040959] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    1.040962] vesafb: scrolling: redraw
[    1.040965] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.041249] vesafb: framebuffer at 0xe0000000, mapped to 0xf8480000, using 3072k, total 3072k
[    1.105230] Console: switching to colour frame buffer device 128x48
[    1.169143] fb0: VESA VGA frame buffer device
[    1.169179] ipmi message handler version 39.2
[    1.169259] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.169267] ACPI: Power Button [VBTN]
[    1.169337] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.169342] ACPI: Power Button [PWRF]
[    1.169509] GHES: HEST is not enabled!
[    1.169589] isapnp: Scanning for PnP cards...
[    1.169636] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.190104] 00:06: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.191847] Linux agpgart interface v0.103
[    1.193928] brd: module loaded
[    1.194891] loop: module loaded
[    1.195053] ata_piix 0000:00:1f.1: version 2.13
[    1.195778] scsi0 : ata_piix
[    1.195861] scsi1 : ata_piix
[    1.195913] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.195917] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.196244] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.200239] ata2: port disabled--ignoring
[    1.356617] scsi2 : ata_piix
[    1.356695] scsi3 : ata_piix
[    1.356750] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 20
[    1.356754] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20
[    1.357239] libphy: Fixed MDIO Bus: probed
[    1.357400] tun: Universal TUN/TAP device driver, 1.6
[    1.357403] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.357580] PPP generic driver version 2.4.2
[    1.357641] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.357649] ehci-pci: EHCI PCI platform driver
[    1.358035] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.358044] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.358062] ehci-pci 0000:00:1d.7: debug port 1
[    1.361968] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.361998] ehci-pci 0000:00:1d.7: irq 21, io mem 0xffa80800
[    1.364352] ata1.00: ATAPI: Optiarc DVD+/-RW ND-3570A, 104B, max UDMA/33
[    1.372028] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.372126] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.372130] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.372134] usb usb1: Product: EHCI Host Controller
[    1.372137] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.372140] usb usb1: SerialNumber: 0000:00:1d.7
[    1.372389] hub 1-0:1.0: USB hub found
[    1.372462] hub 1-0:1.0: 8 ports detected
[    1.372738] ehci-platform: EHCI generic platform driver
[    1.372752] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.372755] ohci-pci: OHCI PCI platform driver
[    1.372771] ohci-platform: OHCI generic platform driver
[    1.372783] uhci_hcd: USB Universal Host Controller Interface driver
[    1.373116] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.373124] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.373150] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
[    1.373232] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.373236] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.373239] usb usb2: Product: UHCI Host Controller
[    1.373242] usb usb2: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
[    1.373244] usb usb2: SerialNumber: 0000:00:1d.0
[    1.373375] hub 2-0:1.0: USB hub found
[    1.373388] hub 2-0:1.0: 2 ports detected
[    1.373808] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.373817] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.373855] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[    1.373936] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.373940] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.373943] usb usb3: Product: UHCI Host Controller
[    1.373946] usb usb3: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
[    1.373949] usb usb3: SerialNumber: 0000:00:1d.1
[    1.374078] hub 3-0:1.0: USB hub found
[    1.374091] hub 3-0:1.0: 2 ports detected
[    1.374516] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.374524] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.374562] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    1.374634] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.374639] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.374642] usb usb4: Product: UHCI Host Controller
[    1.374644] usb usb4: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
[    1.374647] usb usb4: SerialNumber: 0000:00:1d.2
[    1.374779] hub 4-0:1.0: USB hub found
[    1.374790] hub 4-0:1.0: 2 ports detected
[    1.375200] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.375208] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.375246] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[    1.375314] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.375318] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.375321] usb usb5: Product: UHCI Host Controller
[    1.375324] usb usb5: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
[    1.375327] usb usb5: SerialNumber: 0000:00:1d.3
[    1.375450] hub 5-0:1.0: USB hub found
[    1.375461] hub 5-0:1.0: 2 ports detected
[    1.375663] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.378648] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.378657] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.378770] mousedev: PS/2 mouse device common for all mice
[    1.378922] rtc_cmos 00:04: RTC can wake from S4
[    1.379055] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.379084] rtc_cmos 00:04: alarms up to one day, 242 bytes nvram, hpet irqs
[    1.379180] device-mapper: uevent: version 1.0.3
[    1.379262] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.379291] platform eisa.0: Probing EISA bus 0
[    1.379296] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.379300] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.379303] platform eisa.0: Cannot allocate resource for EISA slot 2
[    1.379306] platform eisa.0: Cannot allocate resource for EISA slot 3
[    1.379314] platform eisa.0: Cannot allocate resource for EISA slot 5
[    1.379318] platform eisa.0: Cannot allocate resource for EISA slot 6
[    1.379331] platform eisa.0: EISA: Detected 0 cards
[    1.379340] cpufreq-nforce2: No nForce2 chipset.
[    1.379346] ledtrig-cpu: registered to indicate activity on CPUs
[    1.379528] TCP: cubic registered
[    1.379670] NET: Registered protocol family 10
[    1.379919] NET: Registered protocol family 17
[    1.379933] Key type dns_resolver registered
[    1.380277] ata1.00: configured for UDMA/33
[    1.380472] Using IPI No-Shortcut mode
[    1.380580] Loading compiled-in X.509 certificates
[    1.384598] Loaded X.509 cert 'Magrathea: Glacier signing key: 77d70e1df42996dc92b01d759d3e8562ea32a1c7'
[    1.384617] registered taskstats version 1
[    1.387951] Key type trusted registered
[    1.390636] Key type encrypted registered
[    1.393387] AppArmor: AppArmor sha1 policy hashing enabled
[    1.393392] IMA: No TPM chip found, activating TPM-bypass!
[    1.393686] regulator-dummy: disabling
[    1.393749]   Magic number: 10:533:488
[    1.393813] regulator regulator.0: hash matches
[    1.393849] rtc_cmos 00:04: setting system clock to 2014-04-27 15:28:40 UTC (1398612520)
[    1.393928] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.393931] EDD information not available.
[    1.393979] PM: Hibernation image not present or could not be loaded.
[    1.479299] isapnp: No Plug & Play device found
[    1.484657] scsi 0:0:0:0: CD-ROM            Optiarc  DVD+-RW ND-3570A 104B PQ: 0 ANSI: 5
[    1.486671] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.486677] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.486851] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.486985] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.520671] ata3.00: ATA-8: WDC WD800HLFS-75G6U1, 04.04V03, max UDMA/133
[    1.520678] ata3.00: 156250000 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.536706] ata3.00: configured for UDMA/133
[    1.536836] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800HLFS-75 04.0 PQ: 0 ANSI: 5
[    1.537014] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.537101] sd 2:0:0:0: [sda] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.537182] sd 2:0:0:0: [sda] Write Protect is off
[    1.537187] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.537222] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.545148]  sda: sda1 sda2 < sda5 >
[    1.545514] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.008023] tsc: Refined TSC clocksource calibration: 3391.588 MHz
[    2.204033] usb 1-5: new high-speed USB device number 4 using ehci-pci
[    2.337050] usb 1-5: New USB device found, idVendor=1058, idProduct=1100
[    2.337056] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.337061] usb 1-5: Product: My Book         
[    2.337065] usb 1-5: Manufacturer: Western Digital 
[    2.337070] usb 1-5: SerialNumber: 57442D574D41535530353737303336
[    2.448036] usb 1-6: new high-speed USB device number 5 using ehci-pci
[    2.581050] usb 1-6: New USB device found, idVendor=1058, idProduct=0704
[    2.581055] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.581060] usb 1-6: Product: External HDD    
[    2.581064] usb 1-6: Manufacturer: Western Digital 
[    2.581068] usb 1-6: SerialNumber: 5758453530384E5435373135
[    2.948031] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    3.008090] Switched to clocksource tsc
[    3.178070] usb 2-1: config 1 interface 2 has no altsetting 1
[    3.178076] usb 2-1: config 1 interface 3 has no altsetting 1
[    3.178080] usb 2-1: config 1 interface 4 has no altsetting 1
[    3.178084] usb 2-1: config 1 interface 5 has no altsetting 1
[    3.197049] usb 2-1: New USB device found, idVendor=0dba, idProduct=3000
[    3.197054] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.197058] usb 2-1: Product: Mbox 2 
[    3.197062] usb 2-1: Manufacturer: Digidesign
[    4.056028] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    4.854049] usb 2-2: New USB device found, idVendor=046d, idProduct=c52e
[    4.854055] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.854060] usb 2-2: Product: USB Receiver
[    4.854064] usb 2-2: Manufacturer: Logitech
[    5.548601] Freeing unused kernel memory: 872K (c19ae000 - c1a88000)
[    5.548662] Write protecting the kernel text: 6512k
[    5.548791] Write protecting the kernel read-only data: 2756k
[    5.548794] NX-protecting the kernel data: 5776k
[    5.569087] systemd-udevd[105]: starting version 204
[    5.609473] pps_core: LinuxPPS API ver. 1 registered
[    5.609478] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    5.629978] PTP clock support registered
[    5.630318] hidraw: raw HID events driver (C) Jiri Kosina
[    5.653848] tg3.c:v3.134 (Sep 16, 2013)
[    5.654731] usb-storage 1-5:1.0: USB Mass Storage device detected
[    5.664244] usbcore: registered new interface driver usbhid
[    5.664249] usbhid: USB HID core driver
[    5.664357] scsi4 : usb-storage 1-5:1.0
[    5.664461] usb-storage 1-6:1.0: USB Mass Storage device detected
[    5.664566] usb-storage 1-6:1.0: Quirks match for vid 1058 pid 0704: 8000
[    5.664714] scsi5 : usb-storage 1-6:1.0
[    5.664878] usbcore: registered new interface driver usb-storage
[    5.682044] tg3 0000:02:00.0 eth0: Tigon3 [partno(BCM5751PKFBG) rev 4001] (PCI Express) MAC address 00:14:22:43:03:c5
[    5.682051] tg3 0000:02:00.0 eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    5.682055] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    5.682058] tg3 0000:02:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    5.712061] firewire_ohci 0000:04:02.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    5.732834] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input6
[    5.733756] hid-generic 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-2/input0
[    5.735311] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input7
[    5.735687] hid-generic 0003:046D:C52E.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2/input1
[    5.767882] random: lvm urandom read with 39 bits of entropy available
[    5.818046] bio: create slab <bio-1> at 1
[    6.089837] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[    6.212155] firewire_core 0000:04:02.0: created device fw0: GUID 000108002004a1d8, S400
[    6.664848] scsi 4:0:0:0: Direct-Access     WD       5000AAV External 1.65 PQ: 0 ANSI: 4
[    6.664957] scsi 5:0:0:0: Direct-Access     WD       3200BMV External 1.05 PQ: 0 ANSI: 4
[    6.665294] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    6.665611] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    6.665820] sd 4:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    6.666188] sd 5:0:0:0: [sdc] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    6.666810] sd 4:0:0:0: [sdb] Write Protect is off
[    6.666817] sd 4:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    6.667434] sd 5:0:0:0: [sdc] Write Protect is off
[    6.667441] sd 5:0:0:0: [sdc] Mode Sense: 21 00 00 00
[    6.668063] sd 4:0:0:0: [sdb] No Caching mode page found
[    6.668068] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.668690] sd 5:0:0:0: [sdc] No Caching mode page found
[    6.668696] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    6.671059] sd 4:0:0:0: [sdb] No Caching mode page found
[    6.671065] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.671589]  sdb: sdb1
[    6.671777] sd 5:0:0:0: [sdc] No Caching mode page found
[    6.671784] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    6.674809] sd 4:0:0:0: [sdb] No Caching mode page found
[    6.674814] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.674819] sd 4:0:0:0: [sdb] Attached SCSI disk
[    7.037881]  sdc: sdc1
[    7.041190] sd 5:0:0:0: [sdc] No Caching mode page found
[    7.041197] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    7.041203] sd 5:0:0:0: [sdc] Attached SCSI disk
[    7.093464] random: nonblocking pool is initialized
[   17.055121] Adding 3665916k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:3665916k FS
[   17.126441] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.261301] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   17.299274] systemd-udevd[299]: starting version 204
[   17.444667] lp: driver loaded but no devices found
[   17.485054] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   17.486825] ppdev: user-space parallel port driver
[   17.496807] parport_pc 00:05: reported by Plug and Play ACPI
[   17.496867] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   17.510341] [drm] Initialized drm 1.1.0 20060810
[   17.520427] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   17.602925] intel_rng: Firmware space is locked read-only. If you can't or
[   17.602925] intel_rng: don't want to disable this in firmware setup, and if
[   17.602925] intel_rng: you are certain that your system has a functional
[   17.602925] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   17.641241] type=1400 audit(1398626936.745:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=380 comm="apparmor_parser"
[   17.641252] type=1400 audit(1398626936.745:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=380 comm="apparmor_parser"
[   17.641260] type=1400 audit(1398626936.745:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=380 comm="apparmor_parser"
[   17.641885] type=1400 audit(1398626936.745:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=380 comm="apparmor_parser"
[   17.641895] type=1400 audit(1398626936.745:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=380 comm="apparmor_parser"
[   17.642213] type=1400 audit(1398626936.745:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=380 comm="apparmor_parser"
[   17.653115] [drm] radeon kernel modesetting enabled.
[   17.653188] checking generic (e0000000 300000) vs hw (e0000000 10000000)
[   17.653191] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[   17.653220] Console: switching to colour dummy device 80x25
[   17.654017] [drm] initializing kernel modesetting (RV380 0x1002:0x5B62 0x1002:0x0B02).
[   17.654036] [drm] register mmio base: 0xFE9E0000
[   17.654039] [drm] register mmio size: 65536
[   17.654127] [drm] Generation 2 PCI interface, using max accessible memory
[   17.654136] radeon 0000:01:00.0: VRAM: 256M 0x00000000E0000000 - 0x00000000EFFFFFFF (256M used)
[   17.654140] radeon 0000:01:00.0: GTT: 512M 0x00000000C0000000 - 0x00000000DFFFFFFF
[   17.654154] [drm] Detected VRAM RAM=256M, BAR=256M
[   17.654157] [drm] RAM width 128bits DDR
[   17.654241] [TTM] Zone  kernel: Available graphics memory: 432544 kiB
[   17.654244] [TTM] Zone highmem: Available graphics memory: 1810096 kiB
[   17.654247] [TTM] Initializing pool allocator
[   17.654254] [TTM] Initializing DMA pool allocator
[   17.654279] [drm] radeon: 256M of VRAM memory ready
[   17.654282] [drm] radeon: 512M of GTT memory ready.
[   17.654300] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   17.655474] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   17.656735] [drm] PCIE GART of 512M enabled (table at 0x00000000E0040000).
[   17.659492] radeon 0000:01:00.0: WB enabled
[   17.659501] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000c0000000 and cpu addr 0xffcfb000
[   17.659505] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   17.659507] [drm] Driver supports precise vblank timestamp query.
[   17.659539] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
[   17.659558] radeon 0000:01:00.0: radeon: using MSI.
[   17.659587] [drm] radeon: irq initialized.
[   17.659602] [drm] Loading R300 Microcode
[   17.664989] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \GIC3 1 (20131115/utaddress-251)
[   17.665000] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \GIC2 2 (20131115/utaddress-251)
[   17.665006] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \GLBC 3 (20131115/utaddress-251)
[   17.665012] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \SACT 4 (20131115/utaddress-251)
[   17.665017] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \SSTS 5 (20131115/utaddress-251)
[   17.665022] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.665028] ACPI Warning: 0x000008b0-0x000008bf SystemIO conflicts with Region \GHI0 1 (20131115/utaddress-251)
[   17.665034] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.665036] ACPI Warning: 0x00000880-0x000008af SystemIO conflicts with Region \GIC1 1 (20131115/utaddress-251)
[   17.665042] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.665044] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.676221] lp0: using parport0 (interrupt-driven).
[   17.690954] leds_ss4200: no LED devices found
[   17.756754] [drm] radeon: ring at 0x00000000C0001000
[   17.756782] [drm] ring test succeeded in 1 usecs
[   17.756987] [drm] ib test succeeded in 0 usecs
[   17.784401] [drm] Radeon Display Connectors
[   17.784407] [drm] Connector 0:
[   17.784410] [drm]   DVI-I-1
[   17.784412] [drm]   HPD1
[   17.784415] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   17.784418] [drm]   Encoders:
[   17.784420] [drm]     CRT2: INTERNAL_DAC2
[   17.784422] [drm]     DFP1: INTERNAL_TMDS1
[   17.784424] [drm] Connector 1:
[   17.784426] [drm]   DVI-I-2
[   17.784428] [drm]   HPD2
[   17.784431] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   17.784433] [drm]   Encoders:
[   17.784435] [drm]     CRT1: INTERNAL_DAC1
[   17.784437] [drm]     DFP2: INTERNAL_DVO1
[   18.123413] kvm: disabled by bios
[   18.283957] Bluetooth: Core ver 2.17
[   18.283993] NET: Registered protocol family 31
[   18.283996] Bluetooth: HCI device and connection manager initialized
[   18.284044] Bluetooth: HCI socket layer initialized
[   18.284819] Bluetooth: L2CAP socket layer initialized
[   18.284829] Bluetooth: SCO socket layer initialized
[   18.285802] kvm: disabled by bios
[   18.305245] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.305250] Bluetooth: BNEP filters: protocol multicast
[   18.305261] Bluetooth: BNEP socket layer initialized
[   18.330833] Bluetooth: RFCOMM TTY layer initialized
[   18.330849] Bluetooth: RFCOMM socket layer initialized
[   18.330858] Bluetooth: RFCOMM ver 1.11
[   18.352451] type=1400 audit(1398626937.457:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=584 comm="apparmor_parser"
[   18.352463] type=1400 audit(1398626937.457:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=584 comm="apparmor_parser"
[   18.353082] type=1400 audit(1398626937.457:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=584 comm="apparmor_parser"
[   18.529189] [drm] fb mappable at 0xE00C0000
[   18.529195] [drm] vram apper at 0xE0000000
[   18.529197] [drm] size 8294400
[   18.529200] [drm] fb depth is 24
[   18.529202] [drm]    pitch is 7680
[   18.530783] fbcon: radeondrmfb (fb0) is primary device
[   18.765759] init: cups main process (588) killed by HUP signal
[   18.765775] init: cups main process ended, respawning
[   18.832829] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[   18.851914] Console: switching to colour frame buffer device 160x64
[   18.857488] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   18.857491] radeon 0000:01:00.0: registered panic notifier
[   18.857508] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
[   19.280939] intel8x0: white list rate for 1028:01ad is 48000
[   19.331004] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.338169] usb-audio: device not ready, resending boot sequence...
[   19.757109] init: failsafe main process (738) killed by TERM signal
[   19.842054] usb-audio: device not ready, resending boot sequence...
[   20.345057] usb-audio: device not ready, resending boot sequence...
[   20.850064] usb-audio: device not ready, resending boot sequence...
[   21.112143] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.112608] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.354557] usb-audio: device not ready, resending boot sequence...
[   21.786885] init: samba-ad-dc main process (876) terminated with status 1
[   21.858058] usb-audio: device not ready, resending boot sequence...
[   22.362060] usb-audio: device not ready, resending boot sequence...
[   22.374408] type=1400 audit(1398626941.477:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=923 comm="apparmor_parser"
[   22.866062] usb-audio: device not ready, resending boot sequence...
[   23.370220] usb-audio: device not ready, resending boot sequence...
[   23.504887] audit_printk_skb: 165 callbacks suppressed
[   23.504893] type=1400 audit(1398626942.609:67): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1151 comm="apparmor_parser"
[   23.874062] usb-audio: device not ready, resending boot sequence...
[   23.874070] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[   23.874086] snd-usb-audio: probe of 2-1:1.0 failed with error -5
[   23.874111] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[   24.303942] init: plymouth-upstart-bridge main process ended, respawning
[   24.331152] init: plymouth-upstart-bridge main process (1240) terminated with status 1
[   24.331177] init: plymouth-upstart-bridge main process ended, respawning
[   24.358558] tg3 0000:02:00.0 eth0: Link is up at 1000 Mbps, full duplex
[   24.358564] tg3 0000:02:00.0 eth0: Flow control is on for TX and on for RX
[   24.359639] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.378063] usb-audio: device not ready, resending boot sequence...
[   24.882055] usb-audio: device not ready, resending boot sequence...
[   25.386057] usb-audio: device not ready, resending boot sequence...
[   25.890065] usb-audio: device not ready, resending boot sequence...
[   26.394702] usb-audio: device not ready, resending boot sequence...
[   26.898062] usb-audio: device not ready, resending boot sequence...
[   27.402058] usb-audio: device not ready, resending boot sequence...
[   27.906057] usb-audio: device not ready, resending boot sequence...
[   28.440990] usb-audio: device not ready, resending boot sequence...
[   28.935249] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[   28.946100] usb-audio: device not ready, resending boot sequence...
[   28.946107] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[   28.946126] snd-usb-audio: probe of 2-1:1.1 failed with error -5
[   28.946156] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[   29.207823] UDF-fs: INFO Mounting volume '12-29-04 Backup', timestamp 2004/12/29 16:04 (1f10)
[   29.450056] usb-audio: device not ready, resending boot sequence...
[   29.954053] usb-audio: device not ready, resending boot sequence...
[   30.458063] usb-audio: device not ready, resending boot sequence...
[   30.962061] usb-audio: device not ready, resending boot sequence...
[   31.465055] usb-audio: device not ready, resending boot sequence...
[   31.970062] usb-audio: device not ready, resending boot sequence...
[   32.474066] usb-audio: device not ready, resending boot sequence...
[   32.978076] usb-audio: device not ready, resending boot sequence...
[   33.482077] usb-audio: device not ready, resending boot sequence...
[   33.985105] usb-audio: device not ready, resending boot sequence...
[   33.985114] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[   33.985134] snd-usb-audio: probe of 2-1:1.2 failed with error -5
[   33.985173] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[   34.489358] usb-audio: device not ready, resending boot sequence...
[   34.993608] usb-audio: device not ready, resending boot sequence...
[   35.497858] usb-audio: device not ready, resending boot sequence...
[   36.001110] usb-audio: device not ready, resending boot sequence...
[   36.505368] usb-audio: device not ready, resending boot sequence...
[   37.009619] usb-audio: device not ready, resending boot sequence...
[   37.513874] usb-audio: device not ready, resending boot sequence...
[   38.017117] usb-audio: device not ready, resending boot sequence...
[   38.521372] usb-audio: device not ready, resending boot sequence...
[   39.025630] usb-audio: device not ready, resending boot sequence...
[   39.025639] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[   39.025659] snd-usb-audio: probe of 2-1:1.3 failed with error -5
[   39.025696] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[   39.529880] usb-audio: device not ready, resending boot sequence...
[   40.033130] usb-audio: device not ready, resending boot sequence...
[   40.537388] usb-audio: device not ready, resending boot sequence...
[   41.041631] usb-audio: device not ready, resending boot sequence...
[   41.549895] usb-audio: device not ready, resending boot sequence...
[   42.054142] usb-audio: device not ready, resending boot sequence...
[   42.557393] usb-audio: device not ready, resending boot sequence...
[   43.061638] usb-audio: device not ready, resending boot sequence...
[   43.565941] usb-audio: device not ready, resending boot sequence...
[   44.069142] usb-audio: device not ready, resending boot sequence...
[   44.069149] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[   44.069165] snd-usb-audio: probe of 2-1:1.4 failed with error -5
[   44.069194] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[   44.573396] usb-audio: device not ready, resending boot sequence...
[   45.077644] usb-audio: device not ready, resending boot sequence...
[   45.581905] usb-audio: device not ready, resending boot sequence...
[   46.085157] usb-audio: device not ready, resending boot sequence...
[   46.589401] usb-audio: device not ready, resending boot sequence...
[   47.093652] usb-audio: device not ready, resending boot sequence...
[   47.597911] usb-audio: device not ready, resending boot sequence...
[   48.101156] usb-audio: device not ready, resending boot sequence...
[   48.563516] type=1400 audit(1398626967.664:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2118 comm="apparmor_parser"
[   48.563530] type=1400 audit(1398626967.664:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2118 comm="apparmor_parser"
[   48.564401] type=1400 audit(1398626967.668:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2118 comm="apparmor_parser"
[   48.605470] usb-audio: device not ready, resending boot sequence...
[   49.109690] usb-audio: device not ready, resending boot sequence...
[   49.109697] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[   49.109713] snd-usb-audio: probe of 2-1:1.5 failed with error -5
[   49.109742] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[   49.613916] usb-audio: device not ready, resending boot sequence...
[   50.117160] usb-audio: device not ready, resending boot sequence...
[   50.621413] usb-audio: device not ready, resending boot sequence...
[   51.125673] usb-audio: device not ready, resending boot sequence...
[   51.629923] usb-audio: device not ready, resending boot sequence...
[   52.134176] usb-audio: device not ready, resending boot sequence...
[   52.637421] usb-audio: device not ready, resending boot sequence...
[   53.141686] usb-audio: device not ready, resending boot sequence...
[   53.645935] usb-audio: device not ready, resending boot sequence...
[   54.149175] usb-audio: device not ready, resending boot sequence...
[   54.149182] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[   54.149201] snd-usb-audio: probe of 2-1:1.6 failed with error -5
[   54.152175] usbcore: registered new interface driver snd-usb-audio
[  743.391762] type=1400 audit(1398627662.492:71): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2657 comm="apparmor_parser"
[  743.391776] type=1400 audit(1398627662.492:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2657 comm="apparmor_parser"
[  743.393066] type=1400 audit(1398627662.496:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2657 comm="apparmor_parser"
[ 3321.813411] systemd-hostnamed[4153]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 6326.648094] usb 2-1: USB disconnect, device number 2
[ 6341.156145] usb 5-1: new full-speed USB device number 2 using uhci_hcd
[ 6341.387097] usb 5-1: config 1 interface 2 has no altsetting 1
[ 6341.387104] usb 5-1: config 1 interface 3 has no altsetting 1
[ 6341.387107] usb 5-1: config 1 interface 4 has no altsetting 1
[ 6341.387110] usb 5-1: config 1 interface 5 has no altsetting 1
[ 6341.406074] usb 5-1: New USB device found, idVendor=0dba, idProduct=3000
[ 6341.406081] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 6341.406084] usb 5-1: Product: Mbox 2 
[ 6341.406087] usb 5-1: Manufacturer: Digidesign
[ 6341.409139] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 6341.913068] usb-audio: device not ready, resending boot sequence...
[ 6342.418070] usb-audio: device not ready, resending boot sequence...
[ 6342.921066] usb-audio: device not ready, resending boot sequence...
[ 6343.425067] usb-audio: device not ready, resending boot sequence...
[ 6343.930072] usb-audio: device not ready, resending boot sequence...
[ 6344.433072] usb-audio: device not ready, resending boot sequence...
[ 6344.937066] usb-audio: device not ready, resending boot sequence...
[ 6345.442065] usb-audio: device not ready, resending boot sequence...
[ 6345.945074] usb-audio: device not ready, resending boot sequence...
[ 6346.449066] usb-audio: device not ready, resending boot sequence...
[ 6346.449075] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 6346.449094] snd-usb-audio: probe of 5-1:1.0 failed with error -5
[ 6346.452302] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 6346.957068] usb-audio: device not ready, resending boot sequence...
[ 6347.461070] usb-audio: device not ready, resending boot sequence...
[ 6347.966067] usb-audio: device not ready, resending boot sequence...
[ 6348.469064] usb-audio: device not ready, resending boot sequence...
[ 6348.973065] usb-audio: device not ready, resending boot sequence...
[ 6349.477066] usb-audio: device not ready, resending boot sequence...
[ 6349.982066] usb-audio: device not ready, resending boot sequence...
[ 6350.486068] usb-audio: device not ready, resending boot sequence...
[ 6350.989066] usb-audio: device not ready, resending boot sequence...
[ 6351.493067] usb-audio: device not ready, resending boot sequence...
[ 6351.493077] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 6351.493096] snd-usb-audio: probe of 5-1:1.1 failed with error -5
[ 6351.493195] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 6351.997065] usb-audio: device not ready, resending boot sequence...
[ 6352.501068] usb-audio: device not ready, resending boot sequence...
[ 6353.006068] usb-audio: device not ready, resending boot sequence...
[ 6353.510067] usb-audio: device not ready, resending boot sequence...
[ 6354.013065] usb-audio: device not ready, resending boot sequence...
[ 6354.518066] usb-audio: device not ready, resending boot sequence...
[ 6355.022066] usb-audio: device not ready, resending boot sequence...
[ 6355.525068] usb-audio: device not ready, resending boot sequence...
[ 6356.029067] usb-audio: device not ready, resending boot sequence...
[ 6356.533066] usb-audio: device not ready, resending boot sequence...
[ 6356.533075] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 6356.533095] snd-usb-audio: probe of 5-1:1.2 failed with error -5
[ 6356.533195] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 6357.037068] usb-audio: device not ready, resending boot sequence...
[ 6357.541066] usb-audio: device not ready, resending boot sequence...
[ 6358.046068] usb-audio: device not ready, resending boot sequence...
[ 6358.550068] usb-audio: device not ready, resending boot sequence...
[ 6359.053067] usb-audio: device not ready, resending boot sequence...
[ 6359.557066] usb-audio: device not ready, resending boot sequence...
[ 6360.061069] usb-audio: device not ready, resending boot sequence...
[ 6360.566068] usb-audio: device not ready, resending boot sequence...
[ 6361.069067] usb-audio: device not ready, resending boot sequence...
[ 6361.573070] usb-audio: device not ready, resending boot sequence...
[ 6361.573080] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 6361.573099] snd-usb-audio: probe of 5-1:1.3 failed with error -5
[ 6361.573199] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 6362.078069] usb-audio: device not ready, resending boot sequence...
[ 6362.582356] usb-audio: device not ready, resending boot sequence...
[ 6363.086072] usb-audio: device not ready, resending boot sequence...
[ 6363.589072] usb-audio: device not ready, resending boot sequence...
[ 6364.093072] usb-audio: device not ready, resending boot sequence...
[ 6364.598071] usb-audio: device not ready, resending boot sequence...
[ 6365.102075] usb-audio: device not ready, resending boot sequence...
[ 6365.606069] usb-audio: device not ready, resending boot sequence...
[ 6366.110112] usb-audio: device not ready, resending boot sequence...
[ 6366.614066] usb-audio: device not ready, resending boot sequence...
[ 6366.614074] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 6366.614093] snd-usb-audio: probe of 5-1:1.4 failed with error -5
[ 6366.614200] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 6367.117071] usb-audio: device not ready, resending boot sequence...
[ 6367.621066] usb-audio: device not ready, resending boot sequence...
[ 6368.125065] usb-audio: device not ready, resending boot sequence...
[ 6368.629067] usb-audio: device not ready, resending boot sequence...
[ 6369.134071] usb-audio: device not ready, resending boot sequence...
[ 6369.638071] usb-audio: device not ready, resending boot sequence...
[ 6370.142078] usb-audio: device not ready, resending boot sequence...
[ 6370.645069] usb-audio: device not ready, resending boot sequence...
[ 6371.149069] usb-audio: device not ready, resending boot sequence...
[ 6371.653069] usb-audio: device not ready, resending boot sequence...
[ 6371.653076] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 6371.653095] snd-usb-audio: probe of 5-1:1.5 failed with error -5
[ 6371.653201] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 6372.162064] usb-audio: device not ready, resending boot sequence...
[ 6372.665067] usb-audio: device not ready, resending boot sequence...
[ 6373.170071] usb-audio: device not ready, resending boot sequence...
[ 6373.674071] usb-audio: device not ready, resending boot sequence...
[ 6374.177069] usb-audio: device not ready, resending boot sequence...
[ 6374.682122] usb-audio: device not ready, resending boot sequence...
[ 6375.185084] usb-audio: device not ready, resending boot sequence...
[ 6375.690081] usb-audio: device not ready, resending boot sequence...
[ 6376.194070] usb-audio: device not ready, resending boot sequence...
[ 6376.697069] usb-audio: device not ready, resending boot sequence...
[ 6376.697077] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 6376.697095] snd-usb-audio: probe of 5-1:1.6 failed with error -5
[ 7603.249235] perf samples too long (2507 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 7971.880099] usb 5-1: USB disconnect, device number 2
[ 7978.488041] usb 5-2: new full-speed USB device number 3 using uhci_hcd
[ 7978.718087] usb 5-2: config 1 interface 2 has no altsetting 1
[ 7978.718096] usb 5-2: config 1 interface 3 has no altsetting 1
[ 7978.718101] usb 5-2: config 1 interface 4 has no altsetting 1
[ 7978.718105] usb 5-2: config 1 interface 5 has no altsetting 1
[ 7978.737057] usb 5-2: New USB device found, idVendor=0dba, idProduct=3000
[ 7978.737065] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 7978.737070] usb 5-2: Product: Mbox 2 
[ 7978.737074] usb 5-2: Manufacturer: Digidesign
[ 7978.740147] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 7979.245057] usb-audio: device not ready, resending boot sequence...
[ 7979.749054] usb-audio: device not ready, resending boot sequence...
[ 7980.253053] usb-audio: device not ready, resending boot sequence...
[ 7980.757057] usb-audio: device not ready, resending boot sequence...
[ 7981.261056] usb-audio: device not ready, resending boot sequence...
[ 7981.765051] usb-audio: device not ready, resending boot sequence...
[ 7982.269055] usb-audio: device not ready, resending boot sequence...
[ 7982.773056] usb-audio: device not ready, resending boot sequence...
[ 7983.277057] usb-audio: device not ready, resending boot sequence...
[ 7983.781053] usb-audio: device not ready, resending boot sequence...
[ 7983.781061] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 7983.781081] snd-usb-audio: probe of 5-2:1.0 failed with error -5
[ 7983.783122] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 7984.285055] usb-audio: device not ready, resending boot sequence...
[ 7984.789055] usb-audio: device not ready, resending boot sequence...
[ 7985.294054] usb-audio: device not ready, resending boot sequence...
[ 7985.797051] usb-audio: device not ready, resending boot sequence...
[ 7986.301056] usb-audio: device not ready, resending boot sequence...
[ 7986.805056] usb-audio: device not ready, resending boot sequence...
[ 7987.309053] usb-audio: device not ready, resending boot sequence...
[ 7987.813047] usb-audio: device not ready, resending boot sequence...
[ 7988.317054] usb-audio: device not ready, resending boot sequence...
[ 7988.821060] usb-audio: device not ready, resending boot sequence...
[ 7988.821069] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 7988.821090] snd-usb-audio: probe of 5-2:1.1 failed with error -5
[ 7988.821204] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 7989.325052] usb-audio: device not ready, resending boot sequence...
[ 7989.829053] usb-audio: device not ready, resending boot sequence...
[ 7990.333055] usb-audio: device not ready, resending boot sequence...
[ 7990.837058] usb-audio: device not ready, resending boot sequence...
[ 7991.341051] usb-audio: device not ready, resending boot sequence...
[ 7991.846057] usb-audio: device not ready, resending boot sequence...
[ 7992.349052] usb-audio: device not ready, resending boot sequence...
[ 7992.853058] usb-audio: device not ready, resending boot sequence...
[ 7993.357052] usb-audio: device not ready, resending boot sequence...
[ 7993.861057] usb-audio: device not ready, resending boot sequence...
[ 7993.861064] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 7993.861084] snd-usb-audio: probe of 5-2:1.2 failed with error -5
[ 7993.861199] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 7994.365056] usb-audio: device not ready, resending boot sequence...
[ 7994.869057] usb-audio: device not ready, resending boot sequence...
[ 7995.374057] usb-audio: device not ready, resending boot sequence...
[ 7995.877054] usb-audio: device not ready, resending boot sequence...
[ 7996.381051] usb-audio: device not ready, resending boot sequence...
[ 7996.886062] usb-audio: device not ready, resending boot sequence...
[ 7997.390058] usb-audio: device not ready, resending boot sequence...
[ 7997.894060] usb-audio: device not ready, resending boot sequence...
[ 7998.398062] usb-audio: device not ready, resending boot sequence...
[ 7998.902056] usb-audio: device not ready, resending boot sequence...
[ 7998.902065] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 7998.902085] snd-usb-audio: probe of 5-2:1.3 failed with error -5
[ 7998.902197] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 7999.405053] usb-audio: device not ready, resending boot sequence...
[ 7999.909050] usb-audio: device not ready, resending boot sequence...
[ 8000.413053] usb-audio: device not ready, resending boot sequence...
[ 8000.918058] usb-audio: device not ready, resending boot sequence...
[ 8001.421056] usb-audio: device not ready, resending boot sequence...
[ 8001.925056] usb-audio: device not ready, resending boot sequence...
[ 8002.430057] usb-audio: device not ready, resending boot sequence...
[ 8002.933056] usb-audio: device not ready, resending boot sequence...
[ 8003.437054] usb-audio: device not ready, resending boot sequence...
[ 8003.941050] usb-audio: device not ready, resending boot sequence...
[ 8003.941056] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8003.941076] snd-usb-audio: probe of 5-2:1.4 failed with error -5
[ 8003.941190] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8004.445049] usb-audio: device not ready, resending boot sequence...
[ 8004.949051] usb-audio: device not ready, resending boot sequence...
[ 8005.453052] usb-audio: device not ready, resending boot sequence...
[ 8005.957052] usb-audio: device not ready, resending boot sequence...
[ 8006.461052] usb-audio: device not ready, resending boot sequence...
[ 8006.965051] usb-audio: device not ready, resending boot sequence...
[ 8007.469053] usb-audio: device not ready, resending boot sequence...
[ 8007.973052] usb-audio: device not ready, resending boot sequence...
[ 8008.478059] usb-audio: device not ready, resending boot sequence...
[ 8008.982056] usb-audio: device not ready, resending boot sequence...
[ 8008.982066] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8008.982086] snd-usb-audio: probe of 5-2:1.5 failed with error -5
[ 8008.982200] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8009.485055] usb-audio: device not ready, resending boot sequence...
[ 8009.990052] usb-audio: device not ready, resending boot sequence...
[ 8010.493059] usb-audio: device not ready, resending boot sequence...
[ 8010.997058] usb-audio: device not ready, resending boot sequence...
[ 8011.501056] usb-audio: device not ready, resending boot sequence...
[ 8012.006067] usb-audio: device not ready, resending boot sequence...
[ 8012.510057] usb-audio: device not ready, resending boot sequence...
[ 8013.013059] usb-audio: device not ready, resending boot sequence...
[ 8013.517059] usb-audio: device not ready, resending boot sequence...
[ 8014.021057] usb-audio: device not ready, resending boot sequence...
[ 8014.021066] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8014.021086] snd-usb-audio: probe of 5-2:1.6 failed with error -5
[ 8014.021267] usb 5-2: USB disconnect, device number 3
[ 8014.780038] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[ 8015.010074] usb 3-1: config 1 interface 2 has no altsetting 1
[ 8015.010080] usb 3-1: config 1 interface 3 has no altsetting 1
[ 8015.010084] usb 3-1: config 1 interface 4 has no altsetting 1
[ 8015.010087] usb 3-1: config 1 interface 5 has no altsetting 1
[ 8015.029048] usb 3-1: New USB device found, idVendor=0dba, idProduct=3000
[ 8015.029055] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 8015.029059] usb 3-1: Product: Mbox 2 
[ 8015.029064] usb 3-1: Manufacturer: Digidesign
[ 8015.032159] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8015.537054] usb-audio: device not ready, resending boot sequence...
[ 8016.042047] usb-audio: device not ready, resending boot sequence...
[ 8016.546050] usb-audio: device not ready, resending boot sequence...
[ 8017.050193] usb-audio: device not ready, resending boot sequence...
[ 8017.554050] usb-audio: device not ready, resending boot sequence...
[ 8018.057050] usb-audio: device not ready, resending boot sequence...
[ 8018.562047] usb-audio: device not ready, resending boot sequence...
[ 8019.066051] usb-audio: device not ready, resending boot sequence...
[ 8019.570046] usb-audio: device not ready, resending boot sequence...
[ 8020.074050] usb-audio: device not ready, resending boot sequence...
[ 8020.074057] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8020.074078] snd-usb-audio: probe of 3-1:1.0 failed with error -5
[ 8020.077122] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8020.582049] usb-audio: device not ready, resending boot sequence...
[ 8021.086050] usb-audio: device not ready, resending boot sequence...
[ 8021.590044] usb-audio: device not ready, resending boot sequence...
[ 8022.093044] usb-audio: device not ready, resending boot sequence...
[ 8022.597048] usb-audio: device not ready, resending boot sequence...
[ 8023.102046] usb-audio: device not ready, resending boot sequence...
[ 8023.606054] usb-audio: device not ready, resending boot sequence...
[ 8024.109044] usb-audio: device not ready, resending boot sequence...
[ 8024.614051] usb-audio: device not ready, resending boot sequence...
[ 8025.117044] usb-audio: device not ready, resending boot sequence...
[ 8025.117051] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8025.117070] snd-usb-audio: probe of 3-1:1.1 failed with error -5
[ 8025.117186] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8025.621047] usb-audio: device not ready, resending boot sequence...
[ 8026.126046] usb-audio: device not ready, resending boot sequence...
[ 8026.630054] usb-audio: device not ready, resending boot sequence...
[ 8027.134051] usb-audio: device not ready, resending boot sequence...
[ 8027.638052] usb-audio: device not ready, resending boot sequence...
[ 8028.142052] usb-audio: device not ready, resending boot sequence...
[ 8028.646055] usb-audio: device not ready, resending boot sequence...
[ 8029.150052] usb-audio: device not ready, resending boot sequence...
[ 8029.654060] usb-audio: device not ready, resending boot sequence...
[ 8030.157049] usb-audio: device not ready, resending boot sequence...
[ 8030.157057] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8030.157077] snd-usb-audio: probe of 3-1:1.2 failed with error -5
[ 8030.157191] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8030.662054] usb-audio: device not ready, resending boot sequence...
[ 8031.166051] usb-audio: device not ready, resending boot sequence...
[ 8031.670049] usb-audio: device not ready, resending boot sequence...
[ 8032.174048] usb-audio: device not ready, resending boot sequence...
[ 8032.678054] usb-audio: device not ready, resending boot sequence...
[ 8033.182049] usb-audio: device not ready, resending boot sequence...
[ 8033.686053] usb-audio: device not ready, resending boot sequence...
[ 8034.190045] usb-audio: device not ready, resending boot sequence...
[ 8034.694050] usb-audio: device not ready, resending boot sequence...
[ 8035.197045] usb-audio: device not ready, resending boot sequence...
[ 8035.197051] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8035.197070] snd-usb-audio: probe of 3-1:1.3 failed with error -5
[ 8035.197186] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8035.702048] usb-audio: device not ready, resending boot sequence...
[ 8036.205047] usb-audio: device not ready, resending boot sequence...
[ 8036.710054] usb-audio: device not ready, resending boot sequence...
[ 8037.214046] usb-audio: device not ready, resending boot sequence...
[ 8037.717048] usb-audio: device not ready, resending boot sequence...
[ 8038.222052] usb-audio: device not ready, resending boot sequence...
[ 8038.726054] usb-audio: device not ready, resending boot sequence...
[ 8039.230053] usb-audio: device not ready, resending boot sequence...
[ 8039.733050] usb-audio: device not ready, resending boot sequence...
[ 8040.238053] usb-audio: device not ready, resending boot sequence...
[ 8040.238062] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8040.238082] snd-usb-audio: probe of 3-1:1.4 failed with error -5
[ 8040.238194] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8040.742053] usb-audio: device not ready, resending boot sequence...
[ 8041.245048] usb-audio: device not ready, resending boot sequence...
[ 8041.749049] usb-audio: device not ready, resending boot sequence...
[ 8042.254049] usb-audio: device not ready, resending boot sequence...
[ 8042.758050] usb-audio: device not ready, resending boot sequence...
[ 8043.262049] usb-audio: device not ready, resending boot sequence...
[ 8043.766049] usb-audio: device not ready, resending boot sequence...
[ 8044.270049] usb-audio: device not ready, resending boot sequence...
[ 8044.774050] usb-audio: device not ready, resending boot sequence...
[ 8045.278051] usb-audio: device not ready, resending boot sequence...
[ 8045.278060] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8045.278079] snd-usb-audio: probe of 3-1:1.5 failed with error -5
[ 8045.278195] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8045.782052] usb-audio: device not ready, resending boot sequence...
[ 8046.286053] usb-audio: device not ready, resending boot sequence...
[ 8046.790053] usb-audio: device not ready, resending boot sequence...
[ 8047.294051] usb-audio: device not ready, resending boot sequence...
[ 8047.798052] usb-audio: device not ready, resending boot sequence...
[ 8048.302054] usb-audio: device not ready, resending boot sequence...
[ 8048.806054] usb-audio: device not ready, resending boot sequence...
[ 8049.309048] usb-audio: device not ready, resending boot sequence...
[ 8049.813049] usb-audio: device not ready, resending boot sequence...
[ 8050.317048] usb-audio: device not ready, resending boot sequence...
[ 8050.317056] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8050.317074] snd-usb-audio: probe of 3-1:1.6 failed with error -5
[ 8089.680102] usb 3-1: USB disconnect, device number 2
[ 8106.936042] usb 5-1: new full-speed USB device number 4 using uhci_hcd
[ 8107.166094] usb 5-1: config 1 interface 2 has no altsetting 1
[ 8107.166103] usb 5-1: config 1 interface 3 has no altsetting 1
[ 8107.166108] usb 5-1: config 1 interface 4 has no altsetting 1
[ 8107.166112] usb 5-1: config 1 interface 5 has no altsetting 1
[ 8107.185060] usb 5-1: New USB device found, idVendor=0dba, idProduct=3000
[ 8107.185066] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 8107.185071] usb 5-1: Product: Mbox 2 
[ 8107.185075] usb 5-1: Manufacturer: Digidesign
[ 8107.188275] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8107.693061] usb-audio: device not ready, resending boot sequence...
[ 8108.197059] usb-audio: device not ready, resending boot sequence...
[ 8108.701064] usb-audio: device not ready, resending boot sequence...
[ 8109.205068] usb-audio: device not ready, resending boot sequence...
[ 8109.709059] usb-audio: device not ready, resending boot sequence...
[ 8110.213065] usb-audio: device not ready, resending boot sequence...
[ 8110.717064] usb-audio: device not ready, resending boot sequence...
[ 8111.221061] usb-audio: device not ready, resending boot sequence...
[ 8111.725058] usb-audio: device not ready, resending boot sequence...
[ 8112.229058] usb-audio: device not ready, resending boot sequence...
[ 8112.229064] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8112.229084] snd-usb-audio: probe of 5-1:1.0 failed with error -5
[ 8112.232259] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8112.737067] usb-audio: device not ready, resending boot sequence...
[ 8113.242062] usb-audio: device not ready, resending boot sequence...
[ 8113.745065] usb-audio: device not ready, resending boot sequence...
[ 8114.249059] usb-audio: device not ready, resending boot sequence...
[ 8114.753062] usb-audio: device not ready, resending boot sequence...
[ 8115.257059] usb-audio: device not ready, resending boot sequence...
[ 8115.761058] usb-audio: device not ready, resending boot sequence...
[ 8116.265061] usb-audio: device not ready, resending boot sequence...
[ 8116.769059] usb-audio: device not ready, resending boot sequence...
[ 8117.273061] usb-audio: device not ready, resending boot sequence...
[ 8117.273067] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8117.273087] snd-usb-audio: probe of 5-1:1.1 failed with error -5
[ 8117.273199] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8117.777060] usb-audio: device not ready, resending boot sequence...
[ 8118.281060] usb-audio: device not ready, resending boot sequence...
[ 8118.786064] usb-audio: device not ready, resending boot sequence...
[ 8119.289058] usb-audio: device not ready, resending boot sequence...
[ 8119.793060] usb-audio: device not ready, resending boot sequence...
[ 8120.297058] usb-audio: device not ready, resending boot sequence...
[ 8120.801062] usb-audio: device not ready, resending boot sequence...
[ 8121.305065] usb-audio: device not ready, resending boot sequence...
[ 8121.809061] usb-audio: device not ready, resending boot sequence...
[ 8122.313059] usb-audio: device not ready, resending boot sequence...
[ 8122.313066] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8122.313085] snd-usb-audio: probe of 5-1:1.2 failed with error -5
[ 8122.313200] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8122.817063] usb-audio: device not ready, resending boot sequence...
[ 8123.321062] usb-audio: device not ready, resending boot sequence...
[ 8123.825060] usb-audio: device not ready, resending boot sequence...
[ 8124.329058] usb-audio: device not ready, resending boot sequence...
[ 8124.833059] usb-audio: device not ready, resending boot sequence...
[ 8125.337059] usb-audio: device not ready, resending boot sequence...
[ 8125.841058] usb-audio: device not ready, resending boot sequence...
[ 8126.345060] usb-audio: device not ready, resending boot sequence...
[ 8126.849059] usb-audio: device not ready, resending boot sequence...
[ 8127.353061] usb-audio: device not ready, resending boot sequence...
[ 8127.353067] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8127.353087] snd-usb-audio: probe of 5-1:1.3 failed with error -5
[ 8127.353207] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8127.857059] usb-audio: device not ready, resending boot sequence...
[ 8128.361061] usb-audio: device not ready, resending boot sequence...
[ 8128.866066] usb-audio: device not ready, resending boot sequence...
[ 8129.369063] usb-audio: device not ready, resending boot sequence...
[ 8129.873061] usb-audio: device not ready, resending boot sequence...
[ 8130.377062] usb-audio: device not ready, resending boot sequence...
[ 8130.881063] usb-audio: device not ready, resending boot sequence...
[ 8131.385063] usb-audio: device not ready, resending boot sequence...
[ 8131.889060] usb-audio: device not ready, resending boot sequence...
[ 8132.393068] usb-audio: device not ready, resending boot sequence...
[ 8132.393077] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8132.393097] snd-usb-audio: probe of 5-1:1.4 failed with error -5
[ 8132.393213] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8132.898064] usb-audio: device not ready, resending boot sequence...
[ 8133.401065] usb-audio: device not ready, resending boot sequence...
[ 8133.905069] usb-audio: device not ready, resending boot sequence...
[ 8134.409066] usb-audio: device not ready, resending boot sequence...
[ 8134.913061] usb-audio: device not ready, resending boot sequence...
[ 8135.417062] usb-audio: device not ready, resending boot sequence...
[ 8135.921063] usb-audio: device not ready, resending boot sequence...
[ 8136.426061] usb-audio: device not ready, resending boot sequence...
[ 8136.929063] usb-audio: device not ready, resending boot sequence...
[ 8137.433062] usb-audio: device not ready, resending boot sequence...
[ 8137.433069] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8137.433089] snd-usb-audio: probe of 5-1:1.5 failed with error -5
[ 8137.433205] usb-audio: Sending Digidesign Mbox 2 boot sequence...
[ 8137.937063] usb-audio: device not ready, resending boot sequence...
[ 8138.442064] usb-audio: device not ready, resending boot sequence...
[ 8138.945067] usb-audio: device not ready, resending boot sequence...
[ 8139.449061] usb-audio: device not ready, resending boot sequence...
[ 8139.953062] usb-audio: device not ready, resending boot sequence...
[ 8140.458069] usb-audio: device not ready, resending boot sequence...
[ 8140.961067] usb-audio: device not ready, resending boot sequence...
[ 8141.465062] usb-audio: device not ready, resending boot sequence...
[ 8141.969062] usb-audio: device not ready, resending boot sequence...
[ 8142.473066] usb-audio: device not ready, resending boot sequence...
[ 8142.473075] usb-audio: Unknown bootresponse=1, or timed out, ignoring device.
[ 8142.473095] snd-usb-audio: probe of 5-1:1.6 failed with error -5
[ 8963.277486] systemd-hostnamed[6727]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!


```

From this information, can someone help me by telling me what software I need to install to get my Mbox 2 working as an audo IO device. 

Many Thanks.

---

### Post by bcschmerker on 2014-04-27
Actually, Ubuntu® 14.04.0-LTS uses LinUX Kernel 3.13.0 stock; as of April 2014, LinUX Kernel 3.18 is early in its development at the [LinUX Kernel Project](http://www.kernel.org/), and I do not know whether it will be available for the Utopic Unicorn&#8482; development cycle (starting with 14.06a1).  LinUX Kernel 3.14.0 is available through the Ubuntu® Kernel PPA&#8482;.  [ALSA&#8482; 1.0.26](http://www.alsa-project.org/) is standard in 14.04.0-LTS.

Also, from the [official Setup Guide](http://akmedia.digidesign.com/support/docs/Mbox_2_Setup_Guide_v80_56112.pdf) from M-Audio®, the Mbox 2 installation in Apple® Mac OS® X&#8482; 10.2-up is complicated; same with Microsoft® Windows® 6-up.  Furthermore, from the Setup Guide:
[quote=Mbox_2_Setup_Guide_v80_56112]If the USB LED on the front panel of the Mbox 2 does not illuminate, try unplugging the USB cable from the Mbox 2 USB port, and plugging it back in. If the USB LED still does not illuminate, shut down the computer, disconnect Mbox 2 and start the computer. Once the computer has fully restarted, reconnect Mbox 2.

Mbox 2 may not function properly if connected to a USB hub. If you need to use a hub for other USB peripherals, connect the hub to a separate USB port; Mbox 2 must be connected to a dedicated port on the computer in order to function properly.
[/quote]

---

### Post by dranockcir on 2015-03-03
Even though this thread is a year old I figured it would be stumbled upon by someone tryin to get an MBOX 2 working on Ubuntu as I did. I have Ubuntu 14.04.02 LTS installed. The problem ended up being the firmware on the MBOX 2 (which was given to me) was version 1.24 and I had read somewhere to upgrade the firmware. I had to use an old XP machine to do it but I got it upgraded to firmware 1.43 and it works great with Ubuntu and Audacity. 

Rick

---

### Post by ripper17 on 2015-08-13
> **dranockcir said:**
> Even though this thread is a year old I figured it would be stumbled upon by someone tryin to get an MBOX 2 working on Ubuntu as I did. I have Ubuntu 14.04.02 LTS installed. The problem ended up being the firmware on the MBOX 2 (which was given to me) was version 1.24 and I had read somewhere to upgrade the firmware. I had to use an old XP machine to do it but I got it upgraded to firmware 1.43 and it works great with Ubuntu and Audacity. 

Rick

I hope you're still reading this: Where did you get the firmware from and how did you upgrade your device? I've found

[http://secure.digidesign.com/services/avid/kb/downloads.cfm?digiArticleId=24364&localeCode=en](http://secure.digidesign.com/services/avid/kb/downloads.cfm?digiArticleId=24364&localeCode=en)

and tried to update from a Windows 7 machine. After installing some additional DLLs I started the updater, but it said that it could not download the firmware. After a couple of tries, the lights on my MBOX2 went out and even after re-installing the driver and rebooting several times the lights have not turned on again. I'm afraid I may have bricked the box :-(

---

