---
title: "Ubuntu 12.04 issues with Ralink RT2561/RT61 wireless adapter"
date: 2012-06-01
forum: Networking &amp; Wireless
---

### Post by ADeadCat on 2012-06-01
So, I recently installed Ubuntu 12.04 LTS on my Dell Dimension 5100 which had a Ralink RT2561 wireless adapter previously installed. After the installation, the wireless not only was not working, but the wlan0 interface doesn't even appear. Here is the output of some relevant commands:

```
$ lspci | grep Ralink
03:02.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
``````
$ lsusb | grep Wireless
Bus 005 Device 002: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
``````
$ lsmod
Module                  Size  Used by
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31418  0 
ntfs                  100171  0 
msdos                  17132  0 
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230896  0 
ext2                   67987  0 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  2 msdos,vfat
uas                    17828  0 
usb_storage            39646  1 
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  4 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_ca0106             39279  3 
snd_ac97_codec        106082  1 snd_ca0106
snd_hda_codec_idt      60251  1 
ac97_bus               12642  1 snd_ac97_codec
snd_hda_intel          32765  7 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  5 snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                729591  2 
snd                    62064  30 snd_ca0106,snd_ac97_codec,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
ttm                    65344  1 radeon
snd_page_alloc         14115  3 snd_ca0106,snd_hda_intel,snd_pcm
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
joydev                 17393  0 
dcdbas                 14098  0 
psmouse                87213  0 
mac_hid                13077  0 
serio_raw              13027  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_microsoft          12760  0 
e100                   36289  0 
usbhid                 41906  0 
hid                    77367  2 hid_microsoft,usbhid

``````
$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-24-generic (buildd@vernadsky) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #39-Ubuntu SMP Mon May 21 16:51:22 UTC 2012 (Ubuntu 3.2.0-24.39-generic 3.2.16)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afe88c00 (usable)
[    0.000000]  BIOS-e820: 00000000afe88c00 - 00000000afe8ac00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afe8ac00 - 00000000afe8cc00 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afe8cc00 - 00000000b0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Dell Inc.                 Dimension 5100               /0J8885, BIOS A01 05/25/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xafe88 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF0000000 write-back
[    0.000000]   3 base 0AFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2815MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2815M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2815MB, range: 1MB, type UC
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36502000 - 37279000
[    0.000000] ACPI: RSDP 000feb00 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 000fd26b 00074 (v01 DELL    5100    00000006 ASL  00000061)
[    0.000000] ACPI: FACP 000fd363 000F4 (v03 DELL    5100    00000006 ASL  00000061)
[    0.000000] ACPI: DSDT fffc6a22 02CA9 (v01   DELL    dt_ex 00001000 INTL 20050211)
[    0.000000] ACPI: FACS afe88c00 00040
[    0.000000] ACPI: SSDT fffc97e1 000A6 (v01   DELL    st_ex 00001000 INTL 20050211)
[    0.000000] ACPI: APIC 000fd457 00072 (v01 DELL    5100    00000006 ASL  00000061)
[    0.000000] ACPI: BOOT 000fd4c9 00028 (v01 DELL    5100    00000006 ASL  00000061)
[    0.000000] ACPI: ASF! 000fd4f1 00067 (v16 DELL    5100    00000006 ASL  00000061)
[    0.000000] ACPI: MCFG 000fd558 0003E (v01 DELL    5100    00000006 ASL  00000061)
[    0.000000] ACPI: HPET 000fd596 00038 (v01 DELL    5100    00000006 ASL  00000061)
[    0.000000] ACPI: SSDT afe88c40 00175 (v01 DpgPmm  Cpu0Ist 00000011 INTL 20050211)
[    0.000000] ACPI: SSDT afe89049 00175 (v01 DpgPmm  Cpu1Ist 00000011 INTL 20050211)
[    0.000000] ACPI: SSDT afe89452 00140 (v01 DpgPmm    CpuPm 00000010 INTL 20050211)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1926MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000afe88
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x000afe88
[    0.000000] On node 0 totalpages: 720408
[    0.000000] free_area_init_node: node 0, pgdat c1827880, node_mem_map f4f02200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3854 pages used for memmap
[    0.000000]   HighMem zone: 489340 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] disabled)
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
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b0000000 (gap: b0000000:40000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f4800000 s31616 r0 d21632 u1048576
[    0.000000] pcpu-alloc: s31616 r0 d21632 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 714778
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=400fe9a1-6728-4add-bef9-5fcd27f8c557 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 11528064 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000afe88)
[    0.000000] Memory: 2822956k/2882080k available (5628k kernel code, 58676k reserved, 2771k data, 712k init, 1972776k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1835000 - 0xc18e7000   ( 712 kB)
[    0.000000]       .data : 0xc157f204 - 0xc1834040   (2771 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157f204   (5628 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f380a000 soft=f380c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2992.312 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5984.62 BogoMIPS (lpj=11969248)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004043] Security Framework initialized
[    0.004070] AppArmor: AppArmor initialized
[    0.004073] Yama: becoming mindful.
[    0.004157] Mount-cache hash table entries: 512
[    0.004362] Initializing cgroup subsys cpuacct
[    0.004372] Initializing cgroup subsys memory
[    0.004384] Initializing cgroup subsys devices
[    0.004387] Initializing cgroup subsys freezer
[    0.004390] Initializing cgroup subsys blkio
[    0.004401] Initializing cgroup subsys perf_event
[    0.004446] CPU: Physical Processor ID: 0
[    0.004450] CPU: Processor Core ID: 0
[    0.004453] mce: CPU supports 4 MCE banks
[    0.004468] CPU0: Thermal monitoring enabled (TM1)
[    0.004474] using mwait in idle threads.
[    0.010439] ACPI: Core revision 20110623
[    0.078348] ftrace: allocating 25955 entries in 51 pages
[    0.080081] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.080469] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.120607] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[    0.124007] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.124007] ... version:                0
[    0.124007] ... bit width:              40
[    0.124007] ... generic registers:      18
[    0.124007] ... value mask:             000000ffffffffff
[    0.124007] ... max period:             0000007fffffffff
[    0.124007] ... fixed-purpose events:   0
[    0.124007] ... event mask:             000000000003ffff
[    0.124007] NMI watchdog enabled, takes one hw-pmu counter.
[    0.124007] CPU 1 irqstacks, hard=f38b2000 soft=f38b4000
[    0.124007] Booting Node   0, Processors  #1
[    0.124007] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.212058] NMI watchdog enabled, takes one hw-pmu counter.
[    0.212120] Brought up 2 CPUs
[    0.212126] Total of 2 processors activated (11969.57 BogoMIPS).
[    0.213857] devtmpfs: initialized
[    0.213857] EVM: security.selinux
[    0.213857] EVM: security.SMACK64
[    0.213857] EVM: security.capability
[    0.213857] PM: Registering ACPI NVS region at afe88c00 (8192 bytes)
[    0.216257] print_constraints: dummy: 
[    0.216297] RTC time: 19:45:38, date: 06/01/12
[    0.216354] NET: Registered protocol family 16
[    0.216455] Trying to unpack rootfs image as initramfs...
[    0.216631] EISA bus registered
[    0.216693] ACPI: bus type pci registered
[    0.216832] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xf0000000-0xffffffff] (base 0xf0000000)
[    0.216841] PCI: MMCONFIG at [mem 0xf0000000-0xffffffff] reserved in E820
[    0.216848] PCI: MMCONFIG for 0000 [bus00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000) (size reduced!)
[    0.216853] PCI: Using MMCONFIG for extended config space
[    0.216857] PCI: Using configuration type 1 for base access
[    0.232288] bio: create slab <bio-0> at 0
[    0.232351] ACPI: Added _OSI(Module Device)
[    0.232357] ACPI: Added _OSI(Processor Device)
[    0.232362] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.232367] ACPI: Added _OSI(Processor Aggregator Device)
[    0.233795] ACPI: EC: Look up EC in DSDT
[    0.268540] ACPI: Interpreter enabled
[    0.268564] ACPI: (supports S0 S1 S3 S4 S5)
[    0.268614] ACPI: Using IOAPIC for interrupt routing
[    0.350559] ACPI: No dock devices found.
[    0.350565] HEST: Table not found.
[    0.350576] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.380097] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.460088] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.460097] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.460103] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.460110] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000effff] (ignored)
[    0.460116] pci_root PNP0A03:00: host bridge window [mem 0x000f0000-0x000fffff] (ignored)
[    0.460122] pci_root PNP0A03:00: host bridge window [mem 0xaff00000-0xefffffff] (ignored)
[    0.460128] pci_root PNP0A03:00: host bridge window [mem 0xf4000000-0xfebfffff] (ignored)
[    0.460153] pci 0000:00:00.0: [8086:2770] type 0 class 0x000600
[    0.460239] pci 0000:00:01.0: [8086:2771] type 1 class 0x000604
[    0.460318] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.460326] pci 0000:00:01.0: PME# disabled
[    0.460398] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.460424] pci 0000:00:1b.0: reg 10: [mem 0xefffc000-0xefffffff 64bit]
[    0.460528] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.460536] pci 0000:00:1b.0: PME# disabled
[    0.460573] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.460684] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.460692] pci 0000:00:1c.0: PME# disabled
[    0.460732] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.460791] pci 0000:00:1d.0: reg 20: [io  0xff80-0xff9f]
[    0.460840] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.460899] pci 0000:00:1d.1: reg 20: [io  0xff60-0xff7f]
[    0.460949] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.461008] pci 0000:00:1d.2: reg 20: [io  0xff40-0xff5f]
[    0.461058] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.461124] pci 0000:00:1d.3: reg 20: [io  0xff20-0xff3f]
[    0.461186] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.461215] pci 0000:00:1d.7: reg 10: [mem 0xffa80800-0xffa80bff]
[    0.461331] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.461340] pci 0000:00:1d.7: PME# disabled
[    0.461368] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.461463] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
[    0.461575] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0c00 (mask 007f)
[    0.461585] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 00e0 (mask 0007)
[    0.461647] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.461671] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
[    0.461689] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
[    0.461705] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
[    0.461720] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
[    0.461736] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.461792] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
[    0.461815] pci 0000:00:1f.2: reg 10: [io  0xfe00-0xfe07]
[    0.461830] pci 0000:00:1f.2: reg 14: [io  0xfe10-0xfe13]
[    0.461844] pci 0000:00:1f.2: reg 18: [io  0xfe20-0xfe27]
[    0.461858] pci 0000:00:1f.2: reg 1c: [io  0xfe30-0xfe33]
[    0.461873] pci 0000:00:1f.2: reg 20: [io  0xfea0-0xfeaf]
[    0.461927] pci 0000:00:1f.2: PME# supported from D3hot
[    0.461935] pci 0000:00:1f.2: PME# disabled
[    0.461958] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.462027] pci 0000:00:1f.3: reg 20: [io  0xece0-0xecff]
[    0.462149] pci 0000:01:00.0: [1002:5b60] type 0 class 0x000300
[    0.462178] pci 0000:01:00.0: reg 10: [mem 0xec000000-0xedffffff 64bit pref]
[    0.462198] pci 0000:01:00.0: reg 18: [mem 0xefde0000-0xefdeffff 64bit]
[    0.462214] pci 0000:01:00.0: reg 20: [io  0xdc00-0xdcff]
[    0.462238] pci 0000:01:00.0: reg 30: [mem 0xefe00000-0xefe1ffff pref]
[    0.462290] pci 0000:01:00.0: supports D1 D2
[    0.462324] pci 0000:01:00.1: [1002:5b70] type 0 class 0x000380
[    0.462347] pci 0000:01:00.1: reg 10: [mem 0xefdf0000-0xefdfffff 64bit]
[    0.462432] pci 0000:01:00.1: supports D1 D2
[    0.462455] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.462473] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.462481] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.462488] pci 0000:00:01.0:   bridge window [mem 0xefd00000-0xefefffff]
[    0.462497] pci 0000:00:01.0:   bridge window [mem 0xec000000-0xedffffff 64bit pref]
[    0.462559] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.462570] pci 0000:00:1c.0:   bridge window [mem 0xefc00000-0xefcfffff]
[    0.462630] pci 0000:03:02.0: [1814:0301] type 0 class 0x000280
[    0.462657] pci 0000:03:02.0: reg 10: [mem 0xefbf8000-0xefbfffff]
[    0.462790] pci 0000:03:03.0: [1102:0007] type 0 class 0x000401
[    0.462818] pci 0000:03:03.0: reg 10: [io  0xcca0-0xccbf]
[    0.462922] pci 0000:03:03.0: supports D1 D2
[    0.462955] pci 0000:03:08.0: [8086:27dc] type 0 class 0x000200
[    0.462982] pci 0000:03:08.0: reg 10: [mem 0xefbf7000-0xefbf7fff]
[    0.462998] pci 0000:03:08.0: reg 14: [io  0xccc0-0xccff]
[    0.463090] pci 0000:03:08.0: supports D1 D2
[    0.463095] pci 0000:03:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.463103] pci 0000:03:08.0: PME# disabled
[    0.463154] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.463163] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.463171] pci 0000:00:1e.0:   bridge window [mem 0xefb00000-0xefbfffff]
[    0.463183] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.463190] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.463213] pci_bus 0000:00: on NUMA node 0
[    0.463225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.463981] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    0.464498] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.464860] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.465256]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.465264]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.465269] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.235794] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    1.236282] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    1.236790] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.237255] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[    1.237736] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    1.238219] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.238681] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    1.239194] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[    1.239522] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.239534] vgaarb: loaded
[    1.239537] vgaarb: bridge control possible 0000:01:00.0
[    1.239822] i2c-core: driver [aat2870] using legacy suspend method
[    1.239827] i2c-core: driver [aat2870] using legacy resume method
[    1.240012] SCSI subsystem initialized
[    1.240123] libata version 3.00 loaded.
[    1.240248] usbcore: registered new interface driver usbfs
[    1.240287] usbcore: registered new interface driver hub
[    1.240347] usbcore: registered new device driver usb
[    1.240557] PCI: Using ACPI for IRQ routing
[    1.242613] PCI: pci_cache_line_size set to 64 bytes
[    1.242743] reserve RAM buffer: 00000000afe88c00 - 00000000afffffff 
[    1.242957] NetLabel: Initializing
[    1.242964] NetLabel:  domain hash size = 128
[    1.242969] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.242997] NetLabel:  unlabeled traffic allowed by default
[    1.243103] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    1.243112] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.243123] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.252185] Switching to clocksource hpet
[    1.270113] AppArmor: AppArmor Filesystem Enabled
[    1.270166] pnp: PnP ACPI init
[    1.270204] ACPI: bus type pnp registered
[    1.284644] Freeing initrd memory: 13788k freed
[    1.300080] pnp 00:00: [bus 00-ff]
[    1.300087] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.300091] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.300095] pnp 00:00: [io  0x0d00-0xffff window]
[    1.300099] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.300102] pnp 00:00: [mem 0x000c0000-0x000effff window]
[    1.300106] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.300110] pnp 00:00: [mem 0xaff00000-0xefffffff window]
[    1.300113] pnp 00:00: [mem 0xf4000000-0xfebfffff window]
[    1.300209] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.303721] pnp 00:01: [io  0x0060]
[    1.303726] pnp 00:01: [io  0x0064]
[    1.303729] pnp 00:01: [io  0x0062-0x0063]
[    1.303732] pnp 00:01: [io  0x0065-0x006f]
[    1.303735] pnp 00:01: [io  0x00e0-0x00ef]
[    1.303738] pnp 00:01: [io  0x0800-0x085f]
[    1.303741] pnp 00:01: [io  0x0c00-0x0c7f]
[    1.303744] pnp 00:01: [io  0x0860-0x08ff]
[    1.303836] system 00:01: [io  0x0800-0x085f] has been reserved
[    1.303841] system 00:01: [io  0x0c00-0x0c7f] has been reserved
[    1.303845] system 00:01: [io  0x0860-0x08ff] has been reserved
[    1.303851] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.304103] pnp 00:02: [io  0x0080-0x009f]
[    1.304107] pnp 00:02: [io  0x0000-0x001f]
[    1.304114] pnp 00:02: [io  0x00c0-0x00df]
[    1.304118] pnp 00:02: [dma 4]
[    1.304168] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.304316] pnp 00:03: [io  0x00f0-0x00ff]
[    1.304335] pnp 00:03: [irq 13]
[    1.304383] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.304523] pnp 00:04: [io  0x0061]
[    1.304573] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.304725] pnp 00:05: [io  0x0070-0x007f]
[    1.304734] pnp 00:05: [irq 8]
[    1.304786] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.327120] pnp 00:06: [mem 0x00000000-0x0009ffff]
[    1.327125] pnp 00:06: [mem 0x00100000-0x00ffffff]
[    1.327129] pnp 00:06: [mem 0x01000000-0xafe88bff]
[    1.327132] pnp 00:06: [mem 0x000f0000-0x000fffff]
[    1.327136] pnp 00:06: [mem 0x000c0000-0x000cffff]
[    1.327139] pnp 00:06: [mem 0xfec00000-0xfecfffff]
[    1.327143] pnp 00:06: [mem 0xfee00000-0xfeefffff]
[    1.327146] pnp 00:06: [mem 0xfed20000-0xfed9ffff]
[    1.327149] pnp 00:06: [mem 0xffb00000-0xffbfffff]
[    1.327153] pnp 00:06: [mem 0xffc00000-0xffffffff]
[    1.327256] system 00:06: [mem 0x00000000-0x0009ffff] could not be reserved
[    1.327261] system 00:06: [mem 0x00100000-0x00ffffff] could not be reserved
[    1.327266] system 00:06: [mem 0x01000000-0xafe88bff] could not be reserved
[    1.327270] system 00:06: [mem 0x000f0000-0x000fffff] could not be reserved
[    1.327274] system 00:06: [mem 0x000c0000-0x000cffff] could not be reserved
[    1.327278] system 00:06: [mem 0xfec00000-0xfecfffff] could not be reserved
[    1.327282] system 00:06: [mem 0xfee00000-0xfeefffff] has been reserved
[    1.327286] system 00:06: [mem 0xfed20000-0xfed9ffff] has been reserved
[    1.327290] system 00:06: [mem 0xffb00000-0xffbfffff] has been reserved
[    1.327294] system 00:06: [mem 0xffc00000-0xffffffff] has been reserved
[    1.327300] system 00:06: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.330159] pnp 00:07: [mem 0xf0000000-0xf3ffffff]
[    1.330163] pnp 00:07: [mem 0xfeda0000-0xfedacfff]
[    1.330167] pnp 00:07: [io  0x0100-0x01fe]
[    1.330170] pnp 00:07: [io  0x0200-0x0277]
[    1.330173] pnp 00:07: [io  0x0280-0x02e7]
[    1.330176] pnp 00:07: [io  0x02e8-0x02ef]
[    1.330179] pnp 00:07: [io  0x02f0-0x02f7]
[    1.330182] pnp 00:07: [io  0x02f8-0x02ff]
[    1.330185] pnp 00:07: [io  0x0300-0x0377]
[    1.330188] pnp 00:07: [io  0x0380-0x03bb]
[    1.330191] pnp 00:07: [io  0x03c0-0x03e7]
[    1.330194] pnp 00:07: [io  0x03f6-0x03f7]
[    1.330197] pnp 00:07: [io  0x0400-0x04cf]
[    1.330200] pnp 00:07: [io  0x04d2-0x057f]
[    1.330203] pnp 00:07: [io  0x0580-0x0677]
[    1.330206] pnp 00:07: [io  0x0680-0x0777]
[    1.330209] pnp 00:07: [io  0x0780-0x07bb]
[    1.330212] pnp 00:07: [io  0x07c0-0x07ff]
[    1.330215] pnp 00:07: [io  0x08e0-0x08ff]
[    1.330218] pnp 00:07: [io  0x0900-0x09fe]
[    1.330221] pnp 00:07: [io  0x0a00-0x0afe]
[    1.330224] pnp 00:07: [io  0x0b00-0x0bfe]
[    1.330227] pnp 00:07: [io  0x0c80-0x0caf]
[    1.330231] pnp 00:07: [io  0x0cb0-0x0cbf]
[    1.330234] pnp 00:07: [io  0x0cc0-0x0cf7]
[    1.330237] pnp 00:07: [io  0x0d00-0x0dfe]
[    1.330240] pnp 00:07: [io  0x0e00-0x0efe]
[    1.330243] pnp 00:07: [io  0x0f00-0x0ffe]
[    1.330246] pnp 00:07: [io  0x2000-0x20fe]
[    1.330249] pnp 00:07: [io  0x2100-0x21fe]
[    1.330252] pnp 00:07: [io  0x2200-0x22fe]
[    1.330255] pnp 00:07: [io  0x2300-0x23fe]
[    1.330258] pnp 00:07: [io  0x2400-0x24fe]
[    1.330261] pnp 00:07: [io  0x2500-0x25fe]
[    1.330264] pnp 00:07: [io  0x2600-0x26fe]
[    1.330267] pnp 00:07: [io  0x2700-0x27fe]
[    1.330270] pnp 00:07: [io  0x2800-0x28fe]
[    1.330273] pnp 00:07: [io  0x2900-0x29fe]
[    1.330276] pnp 00:07: [io  0x2a00-0x2afe]
[    1.330279] pnp 00:07: [io  0x2b00-0x2bfe]
[    1.330282] pnp 00:07: [io  0x2c00-0x2cfe]
[    1.330285] pnp 00:07: [io  0x2d00-0x2dfe]
[    1.330288] pnp 00:07: [io  0x2e00-0x2efe]
[    1.330291] pnp 00:07: [io  0x2f00-0x2ffe]
[    1.330294] pnp 00:07: [io  0x5000-0x50fe]
[    1.330297] pnp 00:07: [io  0x5100-0x51fe]
[    1.330300] pnp 00:07: [io  0x5200-0x52fe]
[    1.330303] pnp 00:07: [io  0x5300-0x53fe]
[    1.330306] pnp 00:07: [io  0x5400-0x54fe]
[    1.330309] pnp 00:07: [io  0x5500-0x55fe]
[    1.330312] pnp 00:07: [io  0x5600-0x56fe]
[    1.330315] pnp 00:07: [io  0x5700-0x57fe]
[    1.330318] pnp 00:07: [io  0x5800-0x58fe]
[    1.330321] pnp 00:07: [io  0x5900-0x59fe]
[    1.330325] pnp 00:07: [io  0x5a00-0x5afe]
[    1.330328] pnp 00:07: [io  0x5b00-0x5bfe]
[    1.330331] pnp 00:07: [io  0x5c00-0x5cfe]
[    1.330334] pnp 00:07: [io  0x5d00-0x5dfe]
[    1.330337] pnp 00:07: [io  0x5e00-0x5efe]
[    1.330340] pnp 00:07: [io  0x5f00-0x5ffe]
[    1.330343] pnp 00:07: [io  0x6000-0x60fe]
[    1.330346] pnp 00:07: [io  0x6100-0x61fe]
[    1.330349] pnp 00:07: [io  0x6200-0x62fe]
[    1.330352] pnp 00:07: [io  0x6300-0x63fe]
[    1.330355] pnp 00:07: [io  0x6400-0x64fe]
[    1.330358] pnp 00:07: [io  0x6500-0x65fe]
[    1.330361] pnp 00:07: [io  0x6600-0x66fe]
[    1.330364] pnp 00:07: [io  0x6700-0x67fe]
[    1.330367] pnp 00:07: [io  0x6800-0x68fe]
[    1.330370] pnp 00:07: [io  0x6900-0x69fe]
[    1.330373] pnp 00:07: [io  0x6a00-0x6afe]
[    1.330376] pnp 00:07: [io  0x6b00-0x6bfe]
[    1.330379] pnp 00:07: [io  0x6c00-0x6cfe]
[    1.330383] pnp 00:07: [io  0x6d00-0x6dfe]
[    1.330386] pnp 00:07: [io  0x6e00-0x6efe]
[    1.330389] pnp 00:07: [io  0x6f00-0x6ffe]
[    1.330392] pnp 00:07: [io  0xa000-0xa0fe]
[    1.330395] pnp 00:07: [io  0xa100-0xa1fe]
[    1.330398] pnp 00:07: [io  0xa200-0xa2fe]
[    1.330401] pnp 00:07: [io  0xa300-0xa3fe]
[    1.330404] pnp 00:07: [io  0xa400-0xa4fe]
[    1.330407] pnp 00:07: [io  0xa500-0xa5fe]
[    1.330410] pnp 00:07: [io  0xa600-0xa6fe]
[    1.330413] pnp 00:07: [io  0xa700-0xa7fe]
[    1.330416] pnp 00:07: [io  0xa800-0xa8fe]
[    1.330419] pnp 00:07: [io  0xa900-0xa9fe]
[    1.330422] pnp 00:07: [io  0xaa00-0xaafe]
[    1.330425] pnp 00:07: [io  0xab00-0xabfe]
[    1.330428] pnp 00:07: [io  0xac00-0xacfe]
[    1.330431] pnp 00:07: [io  0xad00-0xadfe]
[    1.330434] pnp 00:07: [io  0xae00-0xaefe]
[    1.330437] pnp 00:07: [io  0xaf00-0xaffe]
[    1.330783] system 00:07: [io  0x0100-0x01fe] could not be reserved
[    1.330788] system 00:07: [io  0x0200-0x0277] has been reserved
[    1.330792] system 00:07: [io  0x0280-0x02e7] has been reserved
[    1.330796] system 00:07: [io  0x02e8-0x02ef] has been reserved
[    1.330799] system 00:07: [io  0x02f0-0x02f7] has been reserved
[    1.330803] system 00:07: [io  0x02f8-0x02ff] has been reserved
[    1.330807] system 00:07: [io  0x0300-0x0377] could not be reserved
[    1.330811] system 00:07: [io  0x0380-0x03bb] has been reserved
[    1.330814] system 00:07: [io  0x03c0-0x03e7] has been reserved
[    1.330818] system 00:07: [io  0x03f6-0x03f7] could not be reserved
[    1.330822] system 00:07: [io  0x0400-0x04cf] has been reserved
[    1.330826] system 00:07: [io  0x04d2-0x057f] has been reserved
[    1.330829] system 00:07: [io  0x0580-0x0677] has been reserved
[    1.330833] system 00:07: [io  0x0680-0x0777] has been reserved
[    1.330837] system 00:07: [io  0x0780-0x07bb] has been reserved
[    1.330840] system 00:07: [io  0x07c0-0x07ff] has been reserved
[    1.330844] system 00:07: [io  0x08e0-0x08ff] has been reserved
[    1.330848] system 00:07: [io  0x0900-0x09fe] has been reserved
[    1.330851] system 00:07: [io  0x0a00-0x0afe] has been reserved
[    1.330855] system 00:07: [io  0x0b00-0x0bfe] has been reserved
[    1.330859] system 00:07: [io  0x0c80-0x0caf] has been reserved
[    1.330863] system 00:07: [io  0x0cb0-0x0cbf] has been reserved
[    1.330866] system 00:07: [io  0x0cc0-0x0cf7] has been reserved
[    1.330870] system 00:07: [io  0x0d00-0x0dfe] has been reserved
[    1.330874] system 00:07: [io  0x0e00-0x0efe] has been reserved
[    1.330877] system 00:07: [io  0x0f00-0x0ffe] has been reserved
[    1.330881] system 00:07: [io  0x2000-0x20fe] has been reserved
[    1.330885] system 00:07: [io  0x2100-0x21fe] has been reserved
[    1.330889] system 00:07: [io  0x2200-0x22fe] has been reserved
[    1.330893] system 00:07: [io  0x2300-0x23fe] has been reserved
[    1.330897] system 00:07: [io  0x2400-0x24fe] has been reserved
[    1.330901] system 00:07: [io  0x2500-0x25fe] has been reserved
[    1.330904] system 00:07: [io  0x2600-0x26fe] has been reserved
[    1.330908] system 00:07: [io  0x2700-0x27fe] has been reserved
[    1.330912] system 00:07: [io  0x2800-0x28fe] has been reserved
[    1.330916] system 00:07: [io  0x2900-0x29fe] has been reserved
[    1.330920] system 00:07: [io  0x2a00-0x2afe] has been reserved
[    1.330924] system 00:07: [io  0x2b00-0x2bfe] has been reserved
[    1.330928] system 00:07: [io  0x2c00-0x2cfe] has been reserved
[    1.330932] system 00:07: [io  0x2d00-0x2dfe] has been reserved
[    1.330936] system 00:07: [io  0x2e00-0x2efe] has been reserved
[    1.330940] system 00:07: [io  0x2f00-0x2ffe] has been reserved
[    1.330944] system 00:07: [io  0x5000-0x50fe] has been reserved
[    1.330948] system 00:07: [io  0x5100-0x51fe] has been reserved
[    1.330952] system 00:07: [io  0x5200-0x52fe] has been reserved
[    1.330956] system 00:07: [io  0x5300-0x53fe] has been reserved
[    1.330960] system 00:07: [io  0x5400-0x54fe] has been reserved
[    1.330964] system 00:07: [io  0x5500-0x55fe] has been reserved
[    1.330967] system 00:07: [io  0x5600-0x56fe] has been reserved
[    1.330971] system 00:07: [io  0x5700-0x57fe] has been reserved
[    1.330976] system 00:07: [io  0x5800-0x58fe] has been reserved
[    1.330980] system 00:07: [io  0x5900-0x59fe] has been reserved
[    1.330984] system 00:07: [io  0x5a00-0x5afe] has been reserved
[    1.330988] system 00:07: [io  0x5b00-0x5bfe] has been reserved
[    1.330992] system 00:07: [io  0x5c00-0x5cfe] has been reserved
[    1.330996] system 00:07: [io  0x5d00-0x5dfe] has been reserved
[    1.331000] system 00:07: [io  0x5e00-0x5efe] has been reserved
[    1.331004] system 00:07: [io  0x5f00-0x5ffe] has been reserved
[    1.331008] system 00:07: [io  0x6000-0x60fe] has been reserved
[    1.331012] system 00:07: [io  0x6100-0x61fe] has been reserved
[    1.331016] system 00:07: [io  0x6200-0x62fe] has been reserved
[    1.331020] system 00:07: [io  0x6300-0x63fe] has been reserved
[    1.331024] system 00:07: [io  0x6400-0x64fe] has been reserved
[    1.331028] system 00:07: [io  0x6500-0x65fe] has been reserved
[    1.331032] system 00:07: [io  0x6600-0x66fe] has been reserved
[    1.331036] system 00:07: [io  0x6700-0x67fe] has been reserved
[    1.331040] system 00:07: [io  0x6800-0x68fe] has been reserved
[    1.331044] system 00:07: [io  0x6900-0x69fe] has been reserved
[    1.331048] system 00:07: [io  0x6a00-0x6afe] has been reserved
[    1.331052] system 00:07: [io  0x6b00-0x6bfe] has been reserved
[    1.331056] system 00:07: [io  0x6c00-0x6cfe] has been reserved
[    1.331061] system 00:07: [io  0x6d00-0x6dfe] has been reserved
[    1.331065] system 00:07: [io  0x6e00-0x6efe] has been reserved
[    1.331069] system 00:07: [io  0x6f00-0x6ffe] has been reserved
[    1.331073] system 00:07: [io  0xa000-0xa0fe] has been reserved
[    1.331078] system 00:07: [io  0xa100-0xa1fe] has been reserved
[    1.331082] system 00:07: [io  0xa200-0xa2fe] has been reserved
[    1.331086] system 00:07: [io  0xa300-0xa3fe] has been reserved
[    1.331090] system 00:07: [io  0xa400-0xa4fe] has been reserved
[    1.331095] system 00:07: [io  0xa500-0xa5fe] has been reserved
[    1.331099] system 00:07: [io  0xa600-0xa6fe] has been reserved
[    1.331103] system 00:07: [io  0xa700-0xa7fe] has been reserved
[    1.331111] system 00:07: [io  0xa800-0xa8fe] has been reserved
[    1.331115] system 00:07: [io  0xa900-0xa9fe] has been reserved
[    1.331120] system 00:07: [io  0xaa00-0xaafe] has been reserved
[    1.331124] system 00:07: [io  0xab00-0xabfe] has been reserved
[    1.331128] system 00:07: [io  0xac00-0xacfe] has been reserved
[    1.331133] system 00:07: [io  0xad00-0xadfe] has been reserved
[    1.331137] system 00:07: [io  0xae00-0xaefe] has been reserved
[    1.331141] system 00:07: [io  0xaf00-0xaffe] has been reserved
[    1.331146] system 00:07: [mem 0xf0000000-0xf3ffffff] has been reserved
[    1.331150] system 00:07: [mem 0xfeda0000-0xfedacfff] has been reserved
[    1.331155] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.331165] pnp: PnP ACPI: found 8 devices
[    1.331168] ACPI: ACPI bus type pnp unregistered
[    1.331175] PnPBIOS: Disabled by ACPI PNP
[    1.370291] PCI: max bus depth: 1 pci_try_num: 2
[    1.370328] pci 0000:00:1c.0: BAR 15: assigned [mem 0xb0000000-0xb01fffff 64bit pref]
[    1.370334] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    1.370339] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.370344] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    1.370350] pci 0000:00:01.0:   bridge window [mem 0xefd00000-0xefefffff]
[    1.370355] pci 0000:00:01.0:   bridge window [mem 0xec000000-0xedffffff 64bit pref]
[    1.370362] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.370367] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    1.370374] pci 0000:00:1c.0:   bridge window [mem 0xefc00000-0xefcfffff]
[    1.370380] pci 0000:00:1c.0:   bridge window [mem 0xb0000000-0xb01fffff 64bit pref]
[    1.370389] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    1.370393] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    1.370400] pci 0000:00:1e.0:   bridge window [mem 0xefb00000-0xefbfffff]
[    1.370428] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.370435] pci 0000:00:01.0: setting latency timer to 64
[    1.370445] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.370450] pci 0000:00:1c.0: setting latency timer to 64
[    1.370459] pci 0000:00:1e.0: setting latency timer to 64
[    1.370465] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    1.370468] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    1.370472] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    1.370475] pci_bus 0000:01: resource 1 [mem 0xefd00000-0xefefffff]
[    1.370479] pci_bus 0000:01: resource 2 [mem 0xec000000-0xedffffff 64bit pref]
[    1.370483] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    1.370486] pci_bus 0000:02: resource 1 [mem 0xefc00000-0xefcfffff]
[    1.370490] pci_bus 0000:02: resource 2 [mem 0xb0000000-0xb01fffff 64bit pref]
[    1.370493] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    1.370496] pci_bus 0000:03: resource 1 [mem 0xefb00000-0xefbfffff]
[    1.370500] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    1.370503] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    1.370562] NET: Registered protocol family 2
[    1.370673] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.371082] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.371797] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.372129] TCP: Hash tables configured (established 131072 bind 65536)
[    1.372132] TCP reno registered
[    1.372137] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    1.372147] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    1.372255] NET: Registered protocol family 1
[    1.372311] pci 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.372333] pci 0000:00:1d.0: PCI INT A disabled
[    1.372350] pci 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.372369] pci 0000:00:1d.1: PCI INT B disabled
[    1.372385] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.372404] pci 0000:00:1d.2: PCI INT C disabled
[    1.372420] pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.372439] pci 0000:00:1d.3: PCI INT D disabled
[    1.372450] pci 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.372483] pci 0000:00:1d.7: PCI INT A disabled
[    1.372508] pci 0000:01:00.0: Boot video device
[    1.372535] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling
[    1.372545] PCI: CLS 64 bytes, default 64
[    1.372554] Simple Boot Flag at 0x7a set to 0x1
[    1.373128] audit: initializing netlink socket (disabled)
[    1.373142] type=2000 audit(1338579939.368:1): initialized
[    1.407335] highmem bounce pool size: 64 pages
[    1.407345] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.425664] VFS: Disk quotas dquot_6.5.2
[    1.425769] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.426707] fuse init (API version 7.17)
[    1.426874] msgmni has been set to 1687
[    1.427496] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.427546] io scheduler noop registered
[    1.427553] io scheduler deadline registered
[    1.427566] io scheduler cfq registered (default)
[    1.427755] pcieport 0000:00:01.0: setting latency timer to 64
[    1.427806] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.427882] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.427932] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.428086] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.428130] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.428363] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.428373] ACPI: Power Button [VBTN]
[    1.428458] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.428464] ACPI: Power Button [PWRF]
[    1.494768] ERST: Table is not found!
[    1.494772] GHES: HEST is not enabled!
[    1.494824] isapnp: Scanning for PnP cards...
[    1.494924] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.847990] isapnp: No Plug & Play device found
[    1.880619] Linux agpgart interface v0.103
[    1.883488] brd: module loaded
[    1.884852] loop: module loaded
[    1.885058] ata_piix 0000:00:1f.1: version 2.13
[    1.885076] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.885132] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.885643] scsi0 : ata_piix
[    1.885793] scsi1 : ata_piix
[    1.885874] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.885878] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.885927] ata_piix 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    1.885938] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.885994] ata2: port disabled--ignoring
[    2.040049] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.040601] scsi2 : ata_piix
[    2.040734] scsi3 : ata_piix
[    2.040824] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 20
[    2.040828] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20
[    2.041505] Fixed MDIO Bus: probed
[    2.041541] tun: Universal TUN/TAP device driver, 1.6
[    2.041544] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.041676] PPP generic driver version 2.4.2
[    2.041877] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.041900] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.041923] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.041928] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.042011] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.042037] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    2.042051] ehci_hcd 0000:00:1d.7: debug port 1
[    2.045933] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    2.045955] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800
[    2.048501] ata1.00: ATAPI: HP      DVD Writer 740b, FF24, max UDMA/33
[    2.060029] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.060247] hub 1-0:1.0: USB hub found
[    2.060255] hub 1-0:1.0: 8 ports detected
[    2.060385] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.060407] uhci_hcd: USB Universal Host Controller Interface driver
[    2.060434] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.060447] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.060451] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.060531] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.060560] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
[    2.060769] hub 2-0:1.0: USB hub found
[    2.060776] hub 2-0:1.0: 2 ports detected
[    2.060880] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    2.060891] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.060895] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.060974] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.061015] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[    2.061226] hub 3-0:1.0: USB hub found
[    2.061233] hub 3-0:1.0: 2 ports detected
[    2.061338] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.061349] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.061354] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.061436] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.061475] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    2.061685] hub 4-0:1.0: USB hub found
[    2.061692] hub 4-0:1.0: 2 ports detected
[    2.061794] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.061804] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.061809] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.061887] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.061926] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[    2.062136] hub 5-0:1.0: USB hub found
[    2.062142] hub 5-0:1.0: 2 ports detected
[    2.062332] usbcore: registered new interface driver libusual
[    2.062398] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.064320] ata1.00: configured for UDMA/33
[    2.065107] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.065119] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.065363] mousedev: PS/2 mouse device common for all mice
[    2.065702] rtc_cmos 00:05: RTC can wake from S4
[    2.065843] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.066055] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    2.066197] device-mapper: uevent: version 1.0.3
[    2.066319] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    2.066377] EISA: Probing bus 0 at eisa.0
[    2.066382] EISA: Cannot allocate resource for mainboard
[    2.066385] Cannot allocate resource for EISA slot 1
[    2.066388] Cannot allocate resource for EISA slot 2
[    2.066399] Cannot allocate resource for EISA slot 5
[    2.066402] Cannot allocate resource for EISA slot 6
[    2.066413] EISA: Detected 0 cards.
[    2.066425] cpufreq-nforce2: No nForce2 chipset.
[    2.066430] cpuidle: using governor ladder
[    2.066432] cpuidle: using governor menu
[    2.066435] EFI Variables Facility v0.08 2004-May-17
[    2.066941] TCP cubic registered
[    2.067137] NET: Registered protocol family 10
[    2.067682] scsi 0:0:0:0: CD-ROM            HP       DVD Writer 740b  FF24 PQ: 0 ANSI: 5
[    2.068214] NET: Registered protocol family 17
[    2.068250] Registering the dns_resolver key type
[    2.068290] Using IPI No-Shortcut mode
[    2.068473] PM: Hibernation image not present or could not be loaded.
[    2.068492] registered taskstats version 1
[    2.078652] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    2.078662] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.078971] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.079230] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.086475]   Magic number: 0:326:798
[    2.086583] rtc_cmos 00:05: setting system clock to 2012-06-01 19:45:40 UTC (1338579940)
[    2.087965] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.087970] EDD information not available.
[    2.204320] ata3.00: ATA-6: ST3160023AS, 8.12, max UDMA/133
[    2.204326] ata3.00: 312500000 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    2.220307] ata3.00: configured for UDMA/133
[    2.220498] scsi 2:0:0:0: Direct-Access     ATA      ST3160023AS      8.12 PQ: 0 ANSI: 5
[    2.220723] sd 2:0:0:0: [sda] 312500000 512-byte logical blocks: (160 GB/149 GiB)
[    2.220823] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.220857] sd 2:0:0:0: [sda] Write Protect is off
[    2.220865] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.220924] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.255854]  sda: sda1 sda2 < sda5 >
[    2.256460] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.372029] Refined TSC clocksource calibration: 2992.499 MHz.
[    2.372036] Switching to clocksource tsc
[    2.556025] usb 5-2: new low-speed USB device number 2 using uhci_hcd
[    6.228119] Freeing unused kernel memory: 712k freed
[    6.228652] Write protecting the kernel text: 5632k
[    6.228723] Write protecting the kernel read-only data: 2324k
[    6.254918] udevd[93]: starting version 175
[    6.402431] usbcore: registered new interface driver usbhid
[    6.402438] usbhid: USB HID core driver
[    6.416818] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    6.416826] e100: Copyright(c) 1999-2006 Intel Corporation
[    6.416896] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    6.442127] e100 0000:03:08.0: PME# disabled
[    6.443584] e100 0000:03:08.0: eth0: addr 0xefbf7000, irq 20, MAC addr 00:12:3f:92:f4:50
[    6.495757] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input2
[    6.495985] microsoft 0003:045E:00F9.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.3-2/input0
[    6.585997] microsoft 0003:045E:00F9.0002: fixing up Microsoft Wireless Receiver Model 1028 report descriptor
[    6.636311] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/input/input3
[    6.638106] microsoft 0003:045E:00F9.0002: input,hidraw1: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.3-2/input1
[    6.692243] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   11.338402] udevd[393]: starting version 175
[   11.364477] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.633811] Adding 2879484k swap on /dev/sda5.  Priority:-1 extents:1 across:2879484k 
[   12.600145] lp: driver loaded but no devices found
[   13.019734] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.021880] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.348837] [drm] Initialized drm 1.1.0 20060810
[   13.503821] intel_rng: Firmware space is locked read-only. If you can't or
[   13.503826] intel_rng: don't want to disable this in firmware setup, and if
[   13.503828] intel_rng: you are certain that your system has a functional
[   13.503831] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   14.008105] leds_ss4200: no LED devices found
[   14.087436] [drm] radeon defaulting to kernel modesetting.
[   14.087441] [drm] radeon kernel modesetting enabled.
[   14.087513] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.087523] radeon 0000:01:00.0: setting latency timer to 64
[   14.088223] [drm] initializing kernel modesetting (RV380 0x1002:0x5B60 0x1002:0x0602).
[   14.088261] [drm] register mmio base: 0xEFDE0000
[   14.088266] [drm] register mmio size: 65536
[   14.088435] [drm] Generation 2 PCI interface, using max accessible memory
[   14.088443] radeon 0000:01:00.0: VRAM: 32M 0x00000000EC000000 - 0x00000000EDFFFFFF (32M used)
[   14.088447] radeon 0000:01:00.0: GTT: 512M 0x00000000CC000000 - 0x00000000EBFFFFFF
[   14.088461] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.088465] [drm] Driver supports precise vblank timestamp query.
[   14.088518] radeon 0000:01:00.0: irq 42 for MSI/MSI-X
[   14.088526] radeon 0000:01:00.0: radeon: using MSI.
[   14.088555] [drm] radeon: irq initialized.
[   14.089961] [drm] Detected VRAM RAM=32M, BAR=32M
[   14.089968] [drm] RAM width 64bits DDR
[   14.090082] [TTM] Zone  kernel: Available graphics memory: 432340 kiB.
[   14.090085] [TTM] Zone highmem: Available graphics memory: 1418728 kiB.
[   14.090088] [TTM] Initializing pool allocator.
[   14.090126] [drm] radeon: 32M of VRAM memory ready
[   14.090129] [drm] radeon: 512M of GTT memory ready.
[   14.090160] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   14.091211] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   14.092616] [drm] PCIE GART of 512M enabled (table at 0x00000000EC040000).
[   14.092644] radeon 0000:01:00.0: WB enabled
[   14.092982] [drm] Loading R300 Microcode
[   14.222266] [drm] radeon: ring at 0x00000000CC001000
[   14.222291] [drm] ring test succeeded in 1 usecs
[   14.222574] [drm] radeon: ib pool ready.
[   14.222707] [drm] ib test succeeded in 0 usecs
[   14.226130] [drm] Radeon Display Connectors
[   14.226136] [drm] Connector 0:
[   14.226140] [drm]   VGA
[   14.226146] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   14.226149] [drm]   Encoders:
[   14.226153] [drm]     CRT1: INTERNAL_DAC1
[   14.226157] [drm] Connector 1:
[   14.226160] [drm]   DVI-I
[   14.226164] [drm]   HPD1
[   14.226168] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   14.226172] [drm]   Encoders:
[   14.226176] [drm]     CRT2: INTERNAL_DAC2
[   14.226179] [drm]     DFP1: INTERNAL_TMDS1
[   14.226183] [drm] Connector 2:
[   14.226187] [drm]   S-video
[   14.226190] [drm]   Encoders:
[   14.226193] [drm]     TV1: INTERNAL_DAC2
[   14.310534] [drm] fb mappable at 0xEC0C0000
[   14.310540] [drm] vram apper at 0xEC000000
[   14.310542] [drm] size 2076672
[   14.310545] [drm] fb depth is 8
[   14.310547] [drm]    pitch is 1920
[   14.310791] fbcon: radeondrmfb (fb0) is primary device
[   14.311024] Console: switching to colour frame buffer device 240x67
[   14.311126] fb0: radeondrmfb frame buffer device
[   14.311131] drm: registered panic notifier
[   14.311147] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[   14.963143] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.963224] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   14.963272] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   15.099568] type=1400 audit(1338579953.507:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=526 comm="apparmor_parser"
[   15.100524] type=1400 audit(1338579953.511:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=526 comm="apparmor_parser"
[   15.101047] type=1400 audit(1338579953.511:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=526 comm="apparmor_parser"
[   15.102077] type=1400 audit(1338579953.511:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=550 comm="apparmor_parser"
[   15.103044] type=1400 audit(1338579953.511:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=550 comm="apparmor_parser"
[   15.103565] type=1400 audit(1338579953.511:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=550 comm="apparmor_parser"
[   15.249194] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   15.249394] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   15.249571] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   15.249752] input: HDA Intel Speaker CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   15.249927] input: HDA Intel Speaker Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   15.250102] input: HDA Intel Speaker Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   15.589210] snd_ca0106 0000:03:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.589259] snd-ca0106: Model 1007 Rev 00000000 Serial 10071102
[   17.897594] init: failsafe main process (649) killed by TERM signal
[   18.357799] ppdev: user-space parallel port driver
[   18.845644] type=1400 audit(1338579957.255:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=757 comm="apparmor_parser"
[   18.846390] type=1400 audit(1338579957.255:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=757 comm="apparmor_parser"
[   19.621029] Bluetooth: Core ver 2.16
[   19.621068] NET: Registered protocol family 31
[   19.621073] Bluetooth: HCI device and connection manager initialized
[   19.621079] Bluetooth: HCI socket layer initialized
[   19.621083] Bluetooth: L2CAP socket layer initialized
[   19.621098] Bluetooth: SCO socket layer initialized
[   19.638549] type=1400 audit(1338579958.047:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=797 comm="apparmor_parser"
[   19.639167] type=1400 audit(1338579958.047:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=797 comm="apparmor_parser"
[   19.669732] Bluetooth: RFCOMM TTY layer initialized
[   19.669744] Bluetooth: RFCOMM socket layer initialized
[   19.669750] Bluetooth: RFCOMM ver 1.11
[   19.967281] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.967288] Bluetooth: BNEP filters: protocol multicast
[   20.228053] audit_printk_skb: 15 callbacks suppressed
[   20.228060] type=1400 audit(1338579958.639:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=798 comm="apparmor_parser"
[   20.235357] type=1400 audit(1338579958.643:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=798 comm="apparmor_parser"
[   20.236784] type=1400 audit(1338579958.647:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=798 comm="apparmor_parser"
[   20.237869] type=1400 audit(1338579958.647:20): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=798 comm="apparmor_parser"
[   20.242132] type=1400 audit(1338579958.651:21): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=798 comm="apparmor_parser"
[   20.243286] type=1400 audit(1338579958.651:22): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//sanitized_helper" pid=798 comm="apparmor_parser"
[   20.244129] type=1400 audit(1338579958.655:23): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=798 comm="apparmor_parser"
[   20.246879] type=1400 audit(1338579958.655:24): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer//sanitized_helper" pid=798 comm="apparmor_parser"
[   20.561305] NET4: DECnet for Linux: V.2.5.68s (C) 1995-2003 Linux DECnet Project Team
[   20.561632] DECnet: Routing cache hash table of 1024 buckets, 8Kbytes
[   20.561647] NET: Registered protocol family 12
[   20.617982] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.216871] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.305320] init: plymouth-stop pre-start process (1397) terminated with status 1
[   96.808149] e100 0000:03:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[   96.808372] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   97.008429] eth0: IPv6 duplicate address fe80::a800:4ff:fe00:a04 detected!
[  113.552036] usb 1-7: new high-speed USB device number 3 using ehci_hcd
[  113.736141] Initializing USB Mass Storage driver...
[  113.736395] scsi4 : usb-storage 1-7:1.0
[  113.736576] usbcore: registered new interface driver usb-storage
[  113.736582] USB Mass Storage support registered.
[  113.778243] usbcore: registered new interface driver uas
[  114.737040] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer           1.20 PQ: 0 ANSI: 5
[  114.738158] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  114.741796] sd 4:0:0:0: [sdb] 31266816 512-byte logical blocks: (16.0 GB/14.9 GiB)
[  114.743659] sd 4:0:0:0: [sdb] Write Protect is off
[  114.743671] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  114.744652] sd 4:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  114.764122]  sdb: sdb1
[  114.767031] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  254.509195] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  254.512170] e100 0000:03:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[  254.512509] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  255.296433] eth0: IPv6 duplicate address fe80::a800:4ff:fe00:a04 detected!
[  256.157273] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  256.160168] e100 0000:03:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[  256.160435] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  256.268265] eth0: IPv6 duplicate address fe80::a800:4ff:fe00:a04 detected!
[  363.905317] sdb: detected capacity change from 16008609792 to 0
[  376.557859] usb 1-7: USB disconnect, device number 3
[  379.624028] usb 1-7: new high-speed USB device number 4 using ehci_hcd
[  379.773952] scsi5 : usb-storage 1-7:1.0
[  380.773761] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[  380.774954] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  380.779362] sd 5:0:0:0: [sdb] 3913728 512-byte logical blocks: (2.00 GB/1.86 GiB)
[  380.780211] sd 5:0:0:0: [sdb] Write Protect is off
[  380.780220] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  380.780990] sd 5:0:0:0: [sdb] No Caching mode page present
[  380.781000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  380.784858] sd 5:0:0:0: [sdb] No Caching mode page present
[  380.784864] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  380.878221]  sdb: sdb1
[  380.880746] sd 5:0:0:0: [sdb] No Caching mode page present
[  380.880753] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  380.880758] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 1797.852363] eth0: IPv6 duplicate address fe80::a800:4ff:fe00:a04 detected!
[ 1798.324408] eth0: IPv6 duplicate address fe80::a800:4ff:fe00:a04 detected!
[ 1887.004317] e100 0000:03:08.0: eth0: NIC Link is Down
[ 1891.270837] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1893.382104] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1893.762089] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1904.004151] e100 0000:03:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[ 1904.004388] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1904.161060] eth0: IPv6 duplicate address fe80::a800:4ff:fe00:a04 detected!
[ 1904.449163] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1904.452169] e100 0000:03:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[ 1904.452796] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1904.713165] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1904.716175] e100 0000:03:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[ 1904.716568] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1905.684418] eth0: IPv6 duplicate address fe80::a800:4ff:fe00:a04 detected!
[ 5280.386156] type=1400 audit(1338585219.558:25): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=14262 comm="apparmor_parser"
[ 5280.386782] type=1400 audit(1338585219.558:26): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=14262 comm="apparmor_parser"
[ 5280.568496] type=1400 audit(1338585219.742:27): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=14309 comm="apparmor_parser"
[ 5280.569203] type=1400 audit(1338585219.742:28): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=14309 comm="apparmor_parser"
[ 5306.194714] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 5306.199000] SGI XFS Quota Management subsystem
[ 5306.220161] JFS: nTxBlock = 8192, nTxLock = 65536
[ 5306.237398] NTFS driver 2.1.30 [Flags: R/O MODULE].
[ 5306.259367] QNX4 filesystem 0.2.3 registered.
[ 5306.306564] Btrfs loaded
``````
$ sudo lshw -C network
  *-network:0 UNCLAIMED
       description: Network controller
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:efbf8000-efbfffff
  *-network:1
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: aa:00:04:00:0a:04
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=10.42.0.42 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:efbf7000-efbf7fff ioport:ccc0(size=64)
``````
$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.



``````
$ iwlist scan lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


``````
$ rfkill list all
```(this is not a mistake; it displays no output)
```
$ lsb_release -d
Description:    Ubuntu 12.04 LTS
``````
$ uname -mr
3.2.0-24-generic i686
``````
$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
   ...done.

```

---

### Post by praseodym on 2012-06-01
Load the driver by hand:

```
sudo modprobe -v rt61pci
```

---

### Post by ADeadCat on 2012-06-01
This is the output of the command (if it matters):```
$ sudo modprobe -v rt61pci
insmod /lib/modules/3.2.0-24-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/lib/crc-itu-t.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
```So it seems to have installed correctly, but the wireless still doesn't work; Network Manager just says "device not ready"

---

### Post by praseodym on 2012-06-02
Now uninstall the package "resolvconf" and check:

```
sudo apt-get remove --purge resolvconf
sudo /etc/init.d/networking restart
iwconfig
rfkill list
dmesg | grep rt6
iwlist chan
sudo iwlist scan
```

---

### Post by ADeadCat on 2012-06-02
The wireless still says "device not ready", even after removing resolvconf```
$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
``````
$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
``````
$ dmesg | grep rt6
[   13.580873] rt61pci 0000:03:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.536290] Registered led device: rt61pci-phy0::radio
[   14.536348] Registered led device: rt61pci-phy0::assoc
[   24.592053] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 3 (-16).
[   24.592061] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 4 (-5).
[   26.424029] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 3 (-16).
[   26.424036] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 4 (-5).
[   28.032385] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 3 (-16).
[   28.032392] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 4 (-5).
[   36.212055] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 3 (-16).
[   36.212063] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 4 (-5).
[   42.904045] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 3 (-16).
[   42.904052] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 4 (-5).
[   44.524032] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 3 (-16).
[   44.524041] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 4 (-5).
[  120.608021] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 3 (-16).
[  120.608030] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 4 (-5).
[  129.252023] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 3 (-16).
[  129.252031] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 4 (-5).
[  268.428043] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 3 (-16).
[  268.428055] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 4 (-5).

``````
$ iwlist chan
lo        no frequency information.


wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
eth0      no frequency information.
``````
$ sudo iwlist scan
lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


eth0      Interface doesn't support scanning.

```

---

### Post by praseodym on 2012-06-02
The card is off:

```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="Red"]0 dBm[/COLOR]   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
Button/switch/key/key combination? BIOS checked? Maybe resetting the BIOS settings to default?!

---

### Post by ADeadCat on 2012-06-02
And how might I go about checking/doing that? (A clean install is not out of the question, btw)

---

### Post by praseodym on 2012-06-03
If you reboot, some key is shown to enter the setup of the BIOS. Press F9 to reset and F10 to save&exit

---

### Post by Oropher8598 on 2012-07-03
RT61-based cards are a *pain*. There's a F/OSS driver for them that's included with Ubuntu, but then you need to add proprietary firmware on top of that. The firmware *used* to be in Ubuntu but has been dropped (no idea why) - that's why RT61 cards worked out-of-the-box in older Ubuntus but don't any more.

These are my notes from getting mine to work with Ubuntu Server - I'm not sure how much help they'll be because I didn't document the process in much detail, but here you go anyway.

[LIST]
[*]Get the firmware from debian-nonfree, package ralink-firmware.
[*]ifconfig & iwconfig to check card is recognised
[*]bring card up
[*]scan for networks
[*]generate wpa passphrase
[*]put info in /etc/network/interfaces
[*]restart networking
[*]ifconfig & iwconfig should show card connected

[/LIST]

For getting the firmware, I think I was able to just download the .deb file and install that. Can't remember much of the rest of the process. It was all stuff I pulled together off various networking and ralink pages on the Ubuntu wiki, so most of the information should still be out there.

If anyone's still reading this thread and having difficulty, post back and I'll see what I can dig up ;)

---

### Post by far on 2012-07-03
Hi Oropher8598,

I've just started looking for a solution to a problem that has been bothering me for some time now, and I stumbled upon you post!

Where did you get the firmware? I can't find it...

there seems to be a bug in the kernel and It has been fixed in the new mainline, which has not been released yet:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/929244](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/929244)

In the mean time, I'd really appreciate your help!

---

### Post by Oropher8598 on 2012-08-12
> **far said:**
> Hi Oropher8598,

I've just started looking for a solution to a problem that has been bothering me for some time now, and I stumbled upon you post!

Where did you get the firmware? I can't find it...

there seems to be a bug in the kernel and It has been fixed in the new mainline, which has not been released yet:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/929244](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/929244)

In the mean time, I'd really appreciate your help!
Hi - really sorry about taking more than a month to spot this! I had set it to notify me, but seem to have missed it... Sorry.

Anyway, the firmware I used is in Debian's debian-nonfree repository, eg [http://packages.debian.org/sid/firmware-ralink](). Since this is Ubuntu,  I've linked to the Unstable version rather than Debian Stable; you can find a choice if you want: [http://packages.debian.org/search?keywords=firmware-ralink](http://packages.debian.org/search?keywords=firmware-ralink). There's a download link in the 'Download firmware-ralink' section, which should get you to the .deb package. You can install that as usual on your Ubuntu.

Hope that helps!

---

### Post by far on 2012-09-01
Thank you very much for your reply! Better late than never ;)

I'll try that soon as I can and I'll post the outcome on this thread.

---

