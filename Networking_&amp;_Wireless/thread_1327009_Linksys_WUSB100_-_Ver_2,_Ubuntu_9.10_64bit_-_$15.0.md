---
title: "Linksys WUSB100 - Ver 2, Ubuntu 9.10 64bit - $15.00 USD &quot;if&quot; works"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by churro on 2009-11-15
I'm new to linux setting up stuff. How can I get my Wireless Network USB Adaptor to work with Ubuntu 9.10 (64bit). Router too far to access via onboard motherboard NIC, So I have to use my Windows 7 64bit partition to log into the net via wireless.

I searched and all I found was 9.04 and previous generation Ubuntu's how too's. If someone could walk me through it via a reply on this board, I be willing to pay a small "tip" $ :KS via paypal "if" you can get this to work for me. $15.00 USD.

Please help my quest

I tried ( [http://ubunturt2870.pbworks.com/FrontPage](http://ubunturt2870.pbworks.com/FrontPage) ) And I got errors / warnings and nada.

---

### Post by peepingtom on 2009-11-15
This info is no longer relevant, a new driver has been released by Ralink. New guide HERE: [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

---

### Post by churro on 2009-11-15
Will try when I get home from work later tonight 9:00pm (Central Time) US.

Thanks peepingtom for replying :)

Yes This is a fresh install, Never updated via the internet, (I can't update it) Router is very far away from me.

---

### Post by churro on 2009-11-15
paint@jean:~$ lsusb
Bus 004 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1737:0078 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




paint@jean:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_via      35456  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3872  0 
snd_mixer_oss          18976  1 snd_pcm_oss
ip_tables              21200  1 iptable_filter
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26992  2 snd_seq,snd_pcm
psmouse                57124  0 
serio_raw               6596  0 
x_tables               25832  1 ip_tables
shpchp                 37756  0 
amd64_edac_mod         26688  0 
i2c_piix4              11728  0 
joydev                 13088  0 
snd                    77096  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
edac_core              48876  1 amd64_edac_mod
lp                     11908  0 
asus_atk0110            9472  0 
parport                40528  2 ppdev,lp
usbhid                 43968  0 
radeon                684512  1 
ttm                    43056  1 radeon
atl1e                  37780  0 
drm                   193856  3 radeon,ttm
floppy                 65192  0 
i2c_algo_bit            7076  1 radeon
ohci1394               33780  0 
ieee1394              100896  1 ohci1394






paint@jean:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=8ad90c12-0d5f-4596-afb1-45db7dc9b4a8 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  BIOS-e820: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffa8000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff90 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  modified: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  modified: 00000000cffa8000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff90000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff90000 page 4k
[    0.000000] kernel direct mapping tables up to cff90000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ 12000-14000
[    0.000000] RAMDISK: 37870000 - 37feffed
[    0.000000] ACPI: RSDP 00000000000fb880 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cff90000 00038 (v01 102809 RSDT1549 20091028 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff90200 00084 (v01 102809 FACP1549 20091028 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 20090521 tbfadt-558
[    0.000000] ACPI: DSDT 00000000cff90440 0E774 (v01  A1152 A1152000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cffa8000 00040
[    0.000000] ACPI: APIC 00000000cff90390 0006C (v01 102809 APIC1549 20091028 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff90400 0003C (v01 102809 OEMMCFG  20091028 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cffa8040 00072 (v01 102809 OEMB1549 20091028 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff9f440 00038 (v01 102809 OEMHPET  20091028 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000003bfff] pages 24
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0120000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [0037870000 - 0037feffed]          RAMDISK ==> [0037870000 - 0037feffed]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3290]              BRK ==> [00019e3000 - 00019e3290]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff880028600000-ffff88002bbfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cff90
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 982815
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3825 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833480 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff90000 - 00000000cffa8000
[    0.000000] PM: Registered nosave memory: 00000000cffa8000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ff00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff88002801f000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 966585
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=8ad90c12-0d5f-4596-afb1-45db7dc9b4a8 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 20000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 3791916k/4718592k available (5313k kernel code, 787332k absent, 139344k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3411.789 MHz processor.
[    0.000009] spurious 8259A interrupt: IRQ7.
[    0.000598] Console: colour VGA+ 80x25
[    0.000599] console [tty0] enabled
[    0.009721] allocated 39321600 bytes of page_cgroup
[    0.009723] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.009832] hpet clockevent registered
[    0.009838]   alloc irq_desc for 24 on node 0
[    0.009839]   alloc kstat_irqs on node 0
[    0.009845] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6823.56 BogoMIPS (lpj=34117840)
[    0.010019] Security Framework initialized
[    0.010034] AppArmor: AppArmor initialized
[    0.010224] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.011348] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011865] Mount-cache hash table entries: 256
[    0.011948] Initializing cgroup subsys ns
[    0.011951] Initializing cgroup subsys cpuacct
[    0.011953] Initializing cgroup subsys memory
[    0.011957] Initializing cgroup subsys freezer
[    0.011958] Initializing cgroup subsys net_cls
[    0.011966] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.011967] CPU: L2 Cache: 512K (64 bytes/line)
[    0.011969] CPU 0/0x0 -> Node 0
[    0.011971] tseg: 0000000000
[    0.011980] CPU: Physical Processor ID: 0
[    0.011981] CPU: Processor Core ID: 0
[    0.011983] mce: CPU supports 6 MCE banks
[    0.011989] using C1E aware idle routine
[    0.011990] Performance Counters: AMD PMU driver.
[    0.011993] ... version:                 0
[    0.011994] ... bit width:               48
[    0.011995] ... generic counters:        4
[    0.011996] ... value mask:              0000ffffffffffff
[    0.011997] ... max period:              00007fffffffffff
[    0.011998] ... fixed-purpose counters:  0
[    0.011999] ... counter mask:            000000000000000f
[    0.013047] ACPI: Core revision 20090521
[    0.030041] Setting APIC routing to flat
[    0.030330] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.133801] CPU0: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 6823.26 BogoMIPS (lpj=34116323)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.290832] CPU1: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.290837] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300041] Booting processor 2 APIC 0x2 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 6823.26 BogoMIPS (lpj=34116329)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 2/0x2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.460801] CPU2: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.460806] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.470044] Booting processor 3 APIC 0x3 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 6823.27 BogoMIPS (lpj=34116368)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 3/0x3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.630875] CPU3: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.630880] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.640007] Brought up 4 CPUs
[    0.640009] Total of 4 processors activated (27293.37 BogoMIPS).
[    0.640048] CPU0 attaching sched-domain:
[    0.640050]  domain 0: span 0-3 level MC
[    0.640051]   groups: 0 1 2 3
[    0.640055] CPU1 attaching sched-domain:
[    0.640056]  domain 0: span 0-3 level MC
[    0.640057]   groups: 1 2 3 0
[    0.640060] CPU2 attaching sched-domain:
[    0.640061]  domain 0: span 0-3 level MC
[    0.640062]   groups: 2 3 0 1
[    0.640065] CPU3 attaching sched-domain:
[    0.640066]  domain 0: span 0-3 level MC
[    0.640067]   groups: 3 0 1 2
[    0.640119] Booting paravirtualized kernel on bare hardware
[    0.640119] regulator: core version 0.5
[    0.640119] Time: 15:48:28  Date: 11/15/09
[    0.640119] NET: Registered protocol family 16
[    0.640130] node 0 link 0: io port [1000, ffffff]
[    0.640132] TOM: 00000000d0000000 aka 3328M
[    0.640134] Fam 10h mmconf [e0000000, efffffff]
[    0.640136] node 0 link 0: mmio [a0000, bffff]
[    0.640137] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.640139] node 0 link 0: mmio [f0000000, fbbfffff]
[    0.640141] node 0 link 0: mmio [fbc00000, fbdfffff]
[    0.640143] node 0 link 0: mmio [fbe00000, ffefffff]
[    0.640144] TOM2: 0000000130000000 aka 4864M
[    0.640145] bus: [00,07] on node 0 link 0
[    0.640147] bus: 00 index 0 io port: [0, ffff]
[    0.640148] bus: 00 index 1 mmio: [a0000, bffff]
[    0.640149] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.640151] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.640152] bus: 00 index 4 mmio: [130000000, fcffffffff]
[    0.640159] ACPI: bus type pci registered
[    0.640203] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.640205] PCI: Not using MMCONFIG.
[    0.640206] PCI: Using configuration type 1 for base access
[    0.640207] PCI: Using configuration type 1 for extended access
[    0.640227] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.640228] mtrr: probably your BIOS does not setup all CPUs.
[    0.640229] mtrr: corrected configuration.
[    0.640619] bio: create slab <bio-0> at 0
[    0.640619] ACPI: EC: Look up EC in DSDT
[    0.842501] ACPI: Interpreter enabled
[    0.842504] ACPI: (supports S0 S1 S3 S4 S5)
[    0.842520] ACPI: Using IOAPIC for interrupt routing
[    0.842565] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.846441] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.851624] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.857291] ACPI Warning: Incorrect checksum in table [OEMB] - AE, should be A5 20090521 tbutils-246
[    0.857369] ACPI: No dock devices found.
[    0.857479] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.857572] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.857575] pci 0000:00:06.0: PME# disabled
[    0.857598] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.857600] pci 0000:00:07.0: PME# disabled
[    0.857646] pci 0000:00:11.0: reg 10 io port: [0xb000-0xb007]
[    0.857652] pci 0000:00:11.0: reg 14 io port: [0xa000-0xa003]
[    0.857657] pci 0000:00:11.0: reg 18 io port: [0x9000-0x9007]
[    0.857663] pci 0000:00:11.0: reg 1c io port: [0x8000-0x8003]
[    0.857668] pci 0000:00:11.0: reg 20 io port: [0x7000-0x700f]
[    0.857674] pci 0000:00:11.0: reg 24 32bit mmio: [0xfbbffc00-0xfbbfffff]
[    0.857689] pci 0000:00:11.0: set SATA to AHCI mode
[    0.857730] pci 0000:00:12.0: reg 10 32bit mmio: [0xfbbfd000-0xfbbfdfff]
[    0.857778] pci 0000:00:12.1: reg 10 32bit mmio: [0xfbbfe000-0xfbbfefff]
[    0.857841] pci 0000:00:12.2: reg 10 32bit mmio: [0xfbbff800-0xfbbff8ff]
[    0.857886] pci 0000:00:12.2: supports D1 D2
[    0.857887] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.857891] pci 0000:00:12.2: PME# disabled
[    0.857918] pci 0000:00:13.0: reg 10 32bit mmio: [0xfbbfb000-0xfbbfbfff]
[    0.857965] pci 0000:00:13.1: reg 10 32bit mmio: [0xfbbfc000-0xfbbfcfff]
[    0.858027] pci 0000:00:13.2: reg 10 32bit mmio: [0xfbbff400-0xfbbff4ff]
[    0.858073] pci 0000:00:13.2: supports D1 D2
[    0.858074] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.858077] pci 0000:00:13.2: PME# disabled
[    0.858179] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.858184] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.858190] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.858195] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.858200] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.858257] pci 0000:00:14.2: reg 10 64bit mmio: [0xfbbf4000-0xfbbf7fff]
[    0.858295] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.858298] pci 0000:00:14.2: PME# disabled
[    0.858387] pci 0000:00:14.5: reg 10 32bit mmio: [0xfbbfa000-0xfbbfafff]
[    0.858493] pci 0000:01:05.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.858496] pci 0000:01:05.0: reg 14 io port: [0xc000-0xc0ff]
[    0.858499] pci 0000:01:05.0: reg 18 32bit mmio: [0xfbde0000-0xfbdeffff]
[    0.858504] pci 0000:01:05.0: reg 24 32bit mmio: [0xfbc00000-0xfbcfffff]
[    0.858512] pci 0000:01:05.0: supports D1 D2
[    0.858526] pci 0000:01:05.1: reg 10 32bit mmio: [0xfbdfc000-0xfbdfffff]
[    0.858541] pci 0000:01:05.1: supports D1 D2
[    0.858576] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.858577] pci 0000:00:01.0: bridge 32bit mmio: [0xfbc00000-0xfbdfffff]
[    0.858580] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.858619] pci 0000:02:00.0: reg 10 64bit mmio: [0xfbec0000-0xfbefffff]
[    0.858626] pci 0000:02:00.0: reg 18 io port: [0xdc00-0xdc7f]
[    0.858671] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.858674] pci 0000:02:00.0: PME# disabled
[    0.858724] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
[    0.858726] pci 0000:00:06.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
[    0.858787] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbfff800-0xfbffffff]
[    0.858795] pci 0000:03:00.0: reg 18 io port: [0xe800-0xe8ff]
[    0.858867] pci 0000:03:00.0: supports D2
[    0.858868] pci 0000:03:00.0: PME# supported from D2 D3hot D3cold
[    0.858873] pci 0000:03:00.0: PME# disabled
[    0.858931] pci 0000:00:07.0: bridge io port: [0xe000-0xefff]
[    0.858932] pci 0000:00:07.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.858985] pci 0000:00:14.4: transparent bridge
[    0.859004] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.859141] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.859192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.859230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.859286] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.861918] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 12 14 15)
[    0.862001] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.862082] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.862163] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.862244] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.862325] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.862406] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
[    0.862487] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.862582] SCSI subsystem initialized
[    0.862599] libata version 3.00 loaded.
[    0.862599] usbcore: registered new interface driver usbfs
[    0.862599] usbcore: registered new interface driver hub
[    0.862599] usbcore: registered new device driver usb
[    0.862599] ACPI: WMI: Mapper loaded
[    0.862599] PCI: Using ACPI for IRQ routing
[    0.900010] Bluetooth: Core ver 2.15
[    0.900026] NET: Registered protocol family 31
[    0.900026] Bluetooth: HCI device and connection manager initialized
[    0.900026] Bluetooth: HCI socket layer initialized
[    0.900026] NetLabel: Initializing
[    0.900026] NetLabel:  domain hash size = 128
[    0.900026] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.900026] NetLabel:  unlabeled traffic allowed by default
[    0.900151] PCI-DMA: Disabling AGP.
[    0.900214] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.900215] PCI-DMA: using GART IOMMU.
[    0.900217] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.901686] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.901691] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.910031] hpet: hpet2 irq 24 for MSI
[    0.930015] Switched to high resolution mode on CPU 0
[    0.930770] Switched to high resolution mode on CPU 2
[    0.930801] Switched to high resolution mode on CPU 1
[    0.930844] Switched to high resolution mode on CPU 3
[    0.950029] pnp: PnP ACPI init
[    0.950043] ACPI: bus type pnp registered
[    0.953439] pnp: PnP ACPI: found 14 devices
[    0.953441] ACPI: ACPI bus type pnp unregistered
[    0.953450] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.953452] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.953456] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.953458] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.953459] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.953461] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.953462] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.953464] system 00:08: ioport range 0xc50-0xc51 has been reserved
[    0.953465] system 00:08: ioport range 0xc52-0xc52 has been reserved
[    0.953467] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.953468] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.953470] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.953471] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.953473] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.953475] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.953476] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.953478] system 00:08: ioport range 0xb00-0xb3f has been reserved
[    0.953479] system 00:08: ioport range 0x800-0x89f has been reserved
[    0.953481] system 00:08: ioport range 0xb00-0xb0f has been reserved
[    0.953482] system 00:08: ioport range 0xb20-0xb3f has been reserved
[    0.953484] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.953486] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.953487] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[    0.953490] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.953491] system 00:08: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.953494] system 00:0b: ioport range 0x230-0x23f has been reserved
[    0.953497] system 00:0b: ioport range 0x290-0x29f has been reserved
[    0.953499] system 00:0b: ioport range 0xf40-0xf4f has been reserved
[    0.953500] system 00:0b: ioport range 0xa30-0xa3f has been reserved
[    0.953503] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.953506] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.953507] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    0.953509] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.953511] system 00:0d: iomem range 0x100000-0xcfffffff could not be reserved
[    0.953512] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.958123] AppArmor: AppArmor Filesystem Enabled
[    0.958145] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.958146] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.958148] pci 0000:00:01.0:   MEM window: 0xfbc00000-0xfbdfffff
[    0.958150] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.958153] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.958155] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
[    0.958157] pci 0000:00:06.0:   MEM window: 0xfbe00000-0xfbefffff
[    0.958159] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.958161] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.958162] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.958164] pci 0000:00:07.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.958166] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.958168] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04
[    0.958169] pci 0000:00:14.4:   IO window: disabled
[    0.958173] pci 0000:00:14.4:   MEM window: disabled
[    0.958176] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.958185]   alloc irq_desc for 18 on node 0
[    0.958186]   alloc kstat_irqs on node 0
[    0.958189] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.958191] pci 0000:00:06.0: setting latency timer to 64
[    0.958195]   alloc irq_desc for 19 on node 0
[    0.958196]   alloc kstat_irqs on node 0
[    0.958198] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.958200] pci 0000:00:07.0: setting latency timer to 64
[    0.958206] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.958208] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.958209] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.958211] pci_bus 0000:01: resource 1 mem: [0xfbc00000-0xfbdfffff]
[    0.958212] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.958214] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.958215] pci_bus 0000:02: resource 1 mem: [0xfbe00000-0xfbefffff]
[    0.958217] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.958218] pci_bus 0000:03: resource 1 mem: [0xfbf00000-0xfbffffff]
[    0.958220] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.958221] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.958244] NET: Registered protocol family 2
[    0.958341] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.958981] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.960870] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.961138] TCP: Hash tables configured (established 524288 bind 65536)
[    0.961140] TCP reno registered
[    0.961203] NET: Registered protocol family 1
[    0.961247] Trying to unpack rootfs image as initramfs...
[    1.067160] Freeing initrd memory: 7679k freed
[    1.069262] Scanning for low memory corruption every 60 seconds
[    1.069341] audit: initializing netlink socket (disabled)
[    1.069350] type=2000 audit(1258300109.060:1): initialized
[    1.074700] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.075495] VFS: Disk quotas dquot_6.5.2
[    1.075528] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.075858] fuse init (API version 7.12)
[    1.075902] msgmni has been set to 7421
[    1.076073] alg: No test for stdrng (krng)
[    1.076082] io scheduler noop registered
[    1.076084] io scheduler anticipatory registered
[    1.076085] io scheduler deadline registered
[    1.076105] io scheduler cfq registered (default)
[    1.240034] pci 0000:01:05.0: Boot video device
[    1.240170]   alloc irq_desc for 25 on node 0
[    1.240171]   alloc kstat_irqs on node 0
[    1.240176] pcieport-driver 0000:00:06.0: irq 25 for MSI/MSI-X
[    1.240180] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.240244]   alloc irq_desc for 26 on node 0
[    1.240245]   alloc kstat_irqs on node 0
[    1.240248] pcieport-driver 0000:00:07.0: irq 26 for MSI/MSI-X
[    1.240251] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.240289] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.240301] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.240365] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.240367] ACPI: Power Button [PWRF]
[    1.240399] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.240403] ACPI: Power Button [PWRB]
[    1.240642] processor LNXCPU:00: registered as cooling_device0
[    1.240644] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.240662] processor LNXCPU:01: registered as cooling_device1
[    1.240682] processor LNXCPU:02: registered as cooling_device2
[    1.240701] processor LNXCPU:03: registered as cooling_device3
[    1.243244] Linux agpgart interface v0.103
[    1.243250] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.243345] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.243545] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.244026] brd: module loaded
[    1.244232] loop: module loaded
[    1.244273] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.244353] ahci 0000:00:11.0: version 3.0
[    1.244362]   alloc irq_desc for 22 on node 0
[    1.244363]   alloc kstat_irqs on node 0
[    1.244366] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.244401]   alloc irq_desc for 27 on node 0
[    1.244402]   alloc kstat_irqs on node 0
[    1.244409] ahci 0000:00:11.0: irq 27 for MSI/MSI-X
[    1.244480] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.244482] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.244698] scsi0 : ahci
[    1.244752] scsi1 : ahci
[    1.244780] scsi2 : ahci
[    1.244809] scsi3 : ahci
[    1.244864] ata1: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffd00 irq 27
[    1.244867] ata2: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffd80 irq 27
[    1.244869] ata3: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffe00 irq 27
[    1.244872] ata4: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffe80 irq 27
[    1.245044]   alloc irq_desc for 16 on node 0
[    1.245045]   alloc kstat_irqs on node 0
[    1.245048] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.245066] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.245120] scsi4 : pata_atiixp
[    1.245149] scsi5 : pata_atiixp
[    1.246012] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.246013] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.246341] Fixed MDIO Bus: probed
[    1.246361] PPP generic driver version 2.4.2
[    1.246413] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.246456]   alloc irq_desc for 17 on node 0
[    1.246457]   alloc kstat_irqs on node 0
[    1.246460] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.246470] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.246496] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.246531] ehci_hcd 0000:00:12.2: debug port 1
[    1.246542] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbbff800
[    1.260020] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.260070] usb usb1: configuration #1 chosen from 1 choice
[    1.260086] hub 1-0:1.0: USB hub found
[    1.260091] hub 1-0:1.0: 6 ports detected
[    1.260164] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.260173] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.260190] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.260216] ehci_hcd 0000:00:13.2: debug port 1
[    1.260229] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbbff400
[    1.280020] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.280059] usb usb2: configuration #1 chosen from 1 choice
[    1.280072] hub 2-0:1.0: USB hub found
[    1.280076] hub 2-0:1.0: 6 ports detected
[    1.280123] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.280156] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.280166] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.280182] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.280200] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbbfd000
[    1.344072] usb usb3: configuration #1 chosen from 1 choice
[    1.344089] hub 3-0:1.0: USB hub found
[    1.344095] hub 3-0:1.0: 3 ports detected
[    1.344160] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.344169] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.344186] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.344199] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbbfe000
[    1.404075] usb usb4: configuration #1 chosen from 1 choice
[    1.404089] hub 4-0:1.0: USB hub found
[    1.404095] hub 4-0:1.0: 3 ports detected
[    1.404163] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.404173] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.404189] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.404208] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbbfb000
[    1.464080] usb usb5: configuration #1 chosen from 1 choice
[    1.464093] hub 5-0:1.0: USB hub found
[    1.464099] hub 5-0:1.0: 3 ports detected
[    1.464167] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.464175] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.464192] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.464205] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbbfc000
[    1.524068] usb usb6: configuration #1 chosen from 1 choice
[    1.524083] hub 6-0:1.0: USB hub found
[    1.524091] hub 6-0:1.0: 3 ports detected
[    1.524159] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.524169] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.524185] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.524198] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbbfa000
[    1.584071] usb usb7: configuration #1 chosen from 1 choice
[    1.584085] hub 7-0:1.0: USB hub found
[    1.584091] hub 7-0:1.0: 2 ports detected
[    1.584129] uhci_hcd: USB Universal Host Controller Interface driver
[    1.584180] PNP: No PS/2 controller found. Probing ports directly.
[    1.584482] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.584494] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.584550] mice: PS/2 mouse device common for all mice
[    1.584602] rtc_cmos 00:03: RTC can wake from S4
[    1.584621] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.584641] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.584706] device-mapper: uevent: version 1.0.3
[    1.584752] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.584828] device-mapper: multipath: version 1.1.0 loaded
[    1.584831] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.584984] cpuidle: using governor ladder
[    1.584985] cpuidle: using governor menu
[    1.585208] TCP cubic registered
[    1.585277] NET: Registered protocol family 10
[    1.585521] lo: Disabled Privacy Extensions
[    1.585677] NET: Registered protocol family 17
[    1.585687] Bluetooth: L2CAP ver 2.13
[    1.585688] Bluetooth: L2CAP socket layer initialized
[    1.585689] Bluetooth: SCO (Voice Link) ver 0.6
[    1.585690] Bluetooth: SCO socket layer initialized
[    1.585728] Bluetooth: RFCOMM TTY layer initialized
[    1.585730] Bluetooth: RFCOMM socket layer initialized
[    1.585731] Bluetooth: RFCOMM ver 1.11
[    1.585752] powernow-k8: Found 1 AMD Phenom(tm) II X4 965 Processor processors (4 cpu cores) (version 2.20.00)
[    1.585758] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.585759] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    1.585802] PM: Resume from disk failed.
[    1.585807] registered taskstats version 1
[    1.585884]   Magic number: 1:536:841
[    1.585935] rtc_cmos 00:03: setting system clock to 2009-11-15 15:48:29 UTC (1258300109)
[    1.585937] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.585938] EDD information not available.
[    1.591283] ata2: SATA link down (SStatus 0 SControl 300)
[    1.591344] ata4: SATA link down (SStatus 0 SControl 300)
[    1.770026] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.770047] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.770056] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    1.770733] ata3.00: ATAPI: ATAPI   DVD A  DH24AAL, ZP5A, max UDMA/100, ATAPI AN
[    1.771745] ata3.00: configured for UDMA/100
[    1.771751] ata1.00: ATA-8: WDC WD5000AAKS-00V1A0, 05.01D05, max UDMA/133
[    1.771753] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.772848] ata1.00: configured for UDMA/133
[    1.800874] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 05.0 PQ: 0 ANSI: 5
[    1.800938] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.800960] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.800980] sd 0:0:0:0: [sda] Write Protect is off
[    1.800981] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.800991] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.801048]  sda:
[    1.802201] scsi 2:0:0:0: CD-ROM            ATAPI    DVD A  DH24AAL   ZP5A PQ: 0 ANSI: 5
[    1.806990]  sda1 sda2 sda3 sda4
[    1.807658] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.807661] Uniform CD-ROM driver Revision: 3.20
[    1.807703] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.807725] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.823945] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.971133] Freeing unused kernel memory: 660k freed
[    1.971249] Write protecting the kernel read-only data: 7580k
[    1.982065] usb 4-2: configuration #1 chosen from 1 choice
[    2.058571] [drm] Initialized drm 1.1.0 20060810
[    2.062028] ATL1E 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.062037] ATL1E 0000:02:00.0: setting latency timer to 64
[    2.062078] ohci1394 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.062084] ohci1394 0000:03:00.0: setting latency timer to 64
[    2.066276] FDC 0 is a post-1991 82077
[    2.070209] [drm] radeon default to kernel modesetting DISABLED.
[    2.070580] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.070582] pci 0000:01:05.0: setting latency timer to 64
[    2.070667] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[    2.074261] usbcore: registered new interface driver hiddev
[    2.078155] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3
[    2.078191] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:12.1-2/input0
[    2.078200] usbcore: registered new interface driver usbhid
[    2.078202] usbhid: v2.6:USB HID core driver
[    2.132058] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fbfff800-fbffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.293783] usb 4-3: new low speed USB device using ohci_hcd and address 3
[    2.502049] usb 4-3: configuration #1 chosen from 1 choice
[    2.514129] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input4
[    2.514163] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:12.1-3/input0
[    2.530075] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input5
[    2.530102] generic-usb 0003:045E:00DD.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:12.1-3/input1
[    2.991193] PM: Starting manual resume from disk
[    2.991195] PM: Resume from partition 8:2
[    2.991196] PM: Checking hibernation image.
[    2.991324] PM: Resume from disk failed.
[    3.011130] EXT4-fs (sda1): barriers enabled
[    3.022956] kjournald2 starting: pid 428, dev sda1:8, commit interval 5 seconds
[    3.022968] EXT4-fs (sda1): delayed allocation enabled
[    3.022971] EXT4-fs: file extents enabled
[    3.030016] EXT4-fs: mballoc enabled
[    3.030023] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.344029] type=1505 audit(1258300111.257:2): operation="profile_load" pid=451 name=/usr/share/gdm/guest-session/Xsession
[    3.345277] type=1505 audit(1258300111.257:3): operation="profile_load" pid=452 name=/sbin/dhclient3
[    3.345444] type=1505 audit(1258300111.257:4): operation="profile_load" pid=452 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.345536] type=1505 audit(1258300111.257:5): operation="profile_load" pid=452 name=/usr/lib/connman/scripts/dhclient-script
[    3.383391] type=1505 audit(1258300111.287:6): operation="profile_load" pid=453 name=/usr/bin/evince
[    3.385981] type=1505 audit(1258300111.297:7): operation="profile_load" pid=453 name=/usr/bin/evince-previewer
[    3.387523] type=1505 audit(1258300111.297:8): operation="profile_load" pid=453 name=/usr/bin/evince-thumbnailer
[    3.409522] type=1505 audit(1258300111.317:9): operation="profile_load" pid=455 name=/usr/lib/cups/backend/cups-pdf
[    3.409726] type=1505 audit(1258300111.317:10): operation="profile_load" pid=455 name=/usr/sbin/cupsd
[    3.453832] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000ad6078]
[    4.027907] Adding 1020116k swap on /dev/sda2.  Priority:-1 extents:1 across:1020116k 
[    4.077184] udev: starting version 147
[    4.842212] lp: driver loaded but no devices found
[    4.856087] EDAC MC: Ver: 2.1.0 Oct 16 2009
[    4.908778] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    4.908780] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.908789] piix4_smbus: probe of 0000:00:14.0 failed with error -16
[    5.024357] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[    5.024584] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    5.024587] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    5.024589] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    5.024589]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    5.024590]     Might be a BIOS bug, if BIOS says ECC is enabled
[    5.024591]     Use of the override can cause unknown side effects.
[    5.024599] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    5.033822] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[    5.033824] shpchp 0000:00:01.0: Cannot reserve MMIO region
[    5.033844] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.368229] ip_tables: (C) 2000-2006 Netfilter Core Team
[    5.898587] EXT4-fs (sda1): internal journal on sda1:8
[    6.178860] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.391126] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    6.391155] HDA Intel 0000:01:05.1: setting latency timer to 64
[    6.711109] __ratelimit: 3 callbacks suppressed
[    6.711111] type=1505 audit(1258321714.616:12): operation="profile_replace" pid=849 name=/usr/share/gdm/guest-session/Xsession
[    6.711899] type=1505 audit(1258321714.616:13): operation="profile_replace" pid=850 name=/sbin/dhclient3
[    6.712068] type=1505 audit(1258321714.616:14): operation="profile_replace" pid=850 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.712162] type=1505 audit(1258321714.616:15): operation="profile_replace" pid=850 name=/usr/lib/connman/scripts/dhclient-script
[    6.713926] type=1505 audit(1258321714.626:16): operation="profile_replace" pid=851 name=/usr/bin/evince
[    6.716502] type=1505 audit(1258321714.626:17): operation="profile_replace" pid=851 name=/usr/bin/evince-previewer
[    6.718070] type=1505 audit(1258321714.626:18): operation="profile_replace" pid=851 name=/usr/bin/evince-thumbnailer
[    6.721000] type=1505 audit(1258321714.626:19): operation="profile_replace" pid=853 name=/usr/lib/cups/backend/cups-pdf
[    6.721204] type=1505 audit(1258321714.626:20): operation="profile_replace" pid=853 name=/usr/sbin/cupsd
[    6.722169] type=1505 audit(1258321714.626:21): operation="profile_replace" pid=854 name=/usr/sbin/tcpdump
[    8.093499] ppdev: user-space parallel port driver
[    9.100538]   alloc irq_desc for 28 on node 0
[    9.100540]   alloc kstat_irqs on node 0
[    9.100551] ATL1E 0000:02:00.0: irq 28 for MSI/MSI-X
[    9.100988] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.841820] usplash:391 freeing invalid memtype ffffffffd0000000-ffffffffd1000000
[   12.125371] [drm] Setting GART location based on new memory map
[   12.140652] [drm] Loading RS780/RS880 CP Microcode
[   12.141291] [drm] Loading RS780/RS880 PFP Microcode
[   12.156397] [drm] Resetting GPU
[   12.156453] [drm] writeback test succeeded in 1 usecs
[   14.390305] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   55.940019] usb 1-1: new high speed USB device using ehci_hcd and address 4
[   56.121746] usb 1-1: configuration #1 chosen from 1 choice

---

### Post by churro on 2009-11-15
Did all the steps in your "revised" post. Not working.

Do I have to download a driver? or will the config just work?

Just did fresh install 9.10 / 64bit, 10mins ago to see if any of my previous attempts was messing with the config you gave me and didn't work.

---

### Post by Leebo on 2009-11-15
You may want to try ndiswrapper to get the windows driver to work. I had to for my linksys wusb54gc. After using ndiswrapper and blacklisting a few modules. It worked like a charm.
Also granted this was for my laptop that was running 8.10 32bit at the time.
Just my 2 cents :)

---

### Post by peepingtom on 2009-11-15
The rt2870sta driver is included in 9.10. It might be that the USB ID (1737:0078 ) for your Linksys adapter isn't detected as an RT2870 chipset. In fact, maybe it isn't. However in dmesg I didn't see any reference to your wifi adapter, could you unplug it, wait 30 sec, plug it back in then give me the dmesg and lsmod outputs? Just the end of dmesg will do.

Additionally, ```
sudo modprobe rt2870sta
``` after it is plugged in and post the end of dmesg after having done that.

---

### Post by churro on 2009-11-15
> **Leebo said:**
> You may want to try ndiswrapper to get the windows driver to work. I had to for my linksys wusb54gc. After using ndiswrapper and blacklisting a few modules. It worked like a charm.
Also granted this was for my laptop that was running 8.10 32bit at the time.
Just my 2 cents :)

I tried that method, It gave me a message along the lines of cannot manage or configure. But adapter was present in the list. No wireless access though.

---

### Post by peepingtom on 2009-11-15
(I'm trying to remember where in the rt2870sta source I can find a list of USB IDs toat work with the driver, searching now)

Edit: According to USB_main_dev.c, the rt2870sta driver does not load when it detects your device's USB ID.

I'm no expert so maybe you can get by with that modprobe command I listed above, otherwise you will have to compile your own driver. Do you want to do that, or try NDISwrapper (using a windows driver under linux, not an optimal solution but slightly easier).

---

### Post by churro on 2009-11-16
> **peepingtom said:**
> The rt2870sta driver is included in 9.10. It might be that the USB ID (1737:0078 ) for your Linksys adapter isn't detected as an RT2870 chipset. In fact, maybe it isn't. However in dmesg I didn't see any reference to your wifi adapter, could you unplug it, wait 30 sec, plug it back in then give me the dmesg and lsmod outputs? Just the end of dmesg will do.

Additionally, ```
sudo modprobe rt2870sta
``` after it is plugged in and post the end of dmesg after having done that.

I don't exactly know where the last part begins, so I will post the whole output.  :popcorn:


paint@jean:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=8ad90c12-0d5f-4596-afb1-45db7dc9b4a8 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  BIOS-e820: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffa8000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff90 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  modified: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  modified: 00000000cffa8000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff90000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff90000 page 4k
[    0.000000] kernel direct mapping tables up to cff90000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ 12000-14000
[    0.000000] RAMDISK: 37870000 - 37feffed
[    0.000000] ACPI: RSDP 00000000000fb880 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cff90000 00038 (v01 102809 RSDT1549 20091028 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff90200 00084 (v01 102809 FACP1549 20091028 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 20090521 tbfadt-558
[    0.000000] ACPI: DSDT 00000000cff90440 0E774 (v01  A1152 A1152000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cffa8000 00040
[    0.000000] ACPI: APIC 00000000cff90390 0006C (v01 102809 APIC1549 20091028 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff90400 0003C (v01 102809 OEMMCFG  20091028 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cffa8040 00072 (v01 102809 OEMB1549 20091028 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff9f440 00038 (v01 102809 OEMHPET  20091028 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000003bfff] pages 24
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0120000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [0037870000 - 0037feffed]          RAMDISK ==> [0037870000 - 0037feffed]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3290]              BRK ==> [00019e3000 - 00019e3290]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff880028600000-ffff88002bbfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cff90
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 982815
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3825 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833480 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff90000 - 00000000cffa8000
[    0.000000] PM: Registered nosave memory: 00000000cffa8000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ff00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff88002801f000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 966585
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=8ad90c12-0d5f-4596-afb1-45db7dc9b4a8 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 20000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 3791916k/4718592k available (5313k kernel code, 787332k absent, 139344k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3412.182 MHz processor.
[    0.000009] spurious 8259A interrupt: IRQ7.
[    0.000598] Console: colour VGA+ 80x25
[    0.000600] console [tty0] enabled
[    0.009696] allocated 39321600 bytes of page_cgroup
[    0.009698] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.009808] hpet clockevent registered
[    0.009813]   alloc irq_desc for 24 on node 0
[    0.009815]   alloc kstat_irqs on node 0
[    0.009821] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6824.35 BogoMIPS (lpj=34121770)
[    0.010020] Security Framework initialized
[    0.010033] AppArmor: AppArmor initialized
[    0.010218] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.011340] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011853] Mount-cache hash table entries: 256
[    0.011936] Initializing cgroup subsys ns
[    0.011939] Initializing cgroup subsys cpuacct
[    0.011941] Initializing cgroup subsys memory
[    0.011945] Initializing cgroup subsys freezer
[    0.011947] Initializing cgroup subsys net_cls
[    0.011954] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.011956] CPU: L2 Cache: 512K (64 bytes/line)
[    0.011957] CPU 0/0x0 -> Node 0
[    0.011959] tseg: 0000000000
[    0.011968] CPU: Physical Processor ID: 0
[    0.011969] CPU: Processor Core ID: 0
[    0.011971] mce: CPU supports 6 MCE banks
[    0.011977] using C1E aware idle routine
[    0.011979] Performance Counters: AMD PMU driver.
[    0.011981] ... version:                 0
[    0.011982] ... bit width:               48
[    0.011983] ... generic counters:        4
[    0.011984] ... value mask:              0000ffffffffffff
[    0.011985] ... max period:              00007fffffffffff
[    0.011986] ... fixed-purpose counters:  0
[    0.011987] ... counter mask:            000000000000000f
[    0.013038] ACPI: Core revision 20090521
[    0.030043] Setting APIC routing to flat
[    0.030332] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.133829] CPU0: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 6823.25 BogoMIPS (lpj=34116291)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.290857] CPU1: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.290862] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300041] Booting processor 2 APIC 0x2 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 6823.26 BogoMIPS (lpj=34116346)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 2/0x2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.460850] CPU2: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.460856] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.470045] Booting processor 3 APIC 0x3 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 6823.26 BogoMIPS (lpj=34116303)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 3/0x3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.630848] CPU3: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.630853] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.640007] Brought up 4 CPUs
[    0.640009] Total of 4 processors activated (27294.14 BogoMIPS).
[    0.640056] CPU0 attaching sched-domain:
[    0.640058]  domain 0: span 0-3 level MC
[    0.640059]   groups: 0 1 2 3
[    0.640063] CPU1 attaching sched-domain:
[    0.640064]  domain 0: span 0-3 level MC
[    0.640065]   groups: 1 2 3 0
[    0.640068] CPU2 attaching sched-domain:
[    0.640069]  domain 0: span 0-3 level MC
[    0.640070]   groups: 2 3 0 1
[    0.640073] CPU3 attaching sched-domain:
[    0.640074]  domain 0: span 0-3 level MC
[    0.640075]   groups: 3 0 1 2
[    0.640127] Booting paravirtualized kernel on bare hardware
[    0.640127] regulator: core version 0.5
[    0.640127] Time: 22:46:48  Date: 11/15/09
[    0.640127] NET: Registered protocol family 16
[    0.640130] node 0 link 0: io port [1000, ffffff]
[    0.640132] TOM: 00000000d0000000 aka 3328M
[    0.640133] Fam 10h mmconf [e0000000, efffffff]
[    0.640135] node 0 link 0: mmio [a0000, bffff]
[    0.640136] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.640139] node 0 link 0: mmio [f0000000, fbbfffff]
[    0.640140] node 0 link 0: mmio [fbc00000, fbdfffff]
[    0.640142] node 0 link 0: mmio [fbe00000, ffefffff]
[    0.640143] TOM2: 0000000130000000 aka 4864M
[    0.640144] bus: [00,07] on node 0 link 0
[    0.640146] bus: 00 index 0 io port: [0, ffff]
[    0.640147] bus: 00 index 1 mmio: [a0000, bffff]
[    0.640148] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.640149] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.640151] bus: 00 index 4 mmio: [130000000, fcffffffff]
[    0.640158] ACPI: bus type pci registered
[    0.640201] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.640203] PCI: Not using MMCONFIG.
[    0.640204] PCI: Using configuration type 1 for base access
[    0.640205] PCI: Using configuration type 1 for extended access
[    0.640226] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.640227] mtrr: probably your BIOS does not setup all CPUs.
[    0.640228] mtrr: corrected configuration.
[    0.640617] bio: create slab <bio-0> at 0
[    0.640617] ACPI: EC: Look up EC in DSDT
[    0.842492] ACPI: Interpreter enabled
[    0.842495] ACPI: (supports S0 S1 S3 S4 S5)
[    0.842511] ACPI: Using IOAPIC for interrupt routing
[    0.842556] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.846431] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.851371] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.857042] ACPI Warning: Incorrect checksum in table [OEMB] - AE, should be A5 20090521 tbutils-246
[    0.857119] ACPI: No dock devices found.
[    0.857229] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.857323] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.857325] pci 0000:00:06.0: PME# disabled
[    0.857348] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.857350] pci 0000:00:07.0: PME# disabled
[    0.857396] pci 0000:00:11.0: reg 10 io port: [0xb000-0xb007]
[    0.857402] pci 0000:00:11.0: reg 14 io port: [0xa000-0xa003]
[    0.857407] pci 0000:00:11.0: reg 18 io port: [0x9000-0x9007]
[    0.857413] pci 0000:00:11.0: reg 1c io port: [0x8000-0x8003]
[    0.857418] pci 0000:00:11.0: reg 20 io port: [0x7000-0x700f]
[    0.857424] pci 0000:00:11.0: reg 24 32bit mmio: [0xfbbffc00-0xfbbfffff]
[    0.857440] pci 0000:00:11.0: set SATA to AHCI mode
[    0.857481] pci 0000:00:12.0: reg 10 32bit mmio: [0xfbbfd000-0xfbbfdfff]
[    0.857528] pci 0000:00:12.1: reg 10 32bit mmio: [0xfbbfe000-0xfbbfefff]
[    0.857591] pci 0000:00:12.2: reg 10 32bit mmio: [0xfbbff800-0xfbbff8ff]
[    0.857637] pci 0000:00:12.2: supports D1 D2
[    0.857638] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.857642] pci 0000:00:12.2: PME# disabled
[    0.857669] pci 0000:00:13.0: reg 10 32bit mmio: [0xfbbfb000-0xfbbfbfff]
[    0.857716] pci 0000:00:13.1: reg 10 32bit mmio: [0xfbbfc000-0xfbbfcfff]
[    0.857779] pci 0000:00:13.2: reg 10 32bit mmio: [0xfbbff400-0xfbbff4ff]
[    0.857825] pci 0000:00:13.2: supports D1 D2
[    0.857826] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.857829] pci 0000:00:13.2: PME# disabled
[    0.857931] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.857937] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.857942] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.857947] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.857953] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.858010] pci 0000:00:14.2: reg 10 64bit mmio: [0xfbbf4000-0xfbbf7fff]
[    0.858048] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.858051] pci 0000:00:14.2: PME# disabled
[    0.858141] pci 0000:00:14.5: reg 10 32bit mmio: [0xfbbfa000-0xfbbfafff]
[    0.858248] pci 0000:01:05.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.858250] pci 0000:01:05.0: reg 14 io port: [0xc000-0xc0ff]
[    0.858253] pci 0000:01:05.0: reg 18 32bit mmio: [0xfbde0000-0xfbdeffff]
[    0.858258] pci 0000:01:05.0: reg 24 32bit mmio: [0xfbc00000-0xfbcfffff]
[    0.858267] pci 0000:01:05.0: supports D1 D2
[    0.858280] pci 0000:01:05.1: reg 10 32bit mmio: [0xfbdfc000-0xfbdfffff]
[    0.858295] pci 0000:01:05.1: supports D1 D2
[    0.858329] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.858331] pci 0000:00:01.0: bridge 32bit mmio: [0xfbc00000-0xfbdfffff]
[    0.858334] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.858373] pci 0000:02:00.0: reg 10 64bit mmio: [0xfbec0000-0xfbefffff]
[    0.858379] pci 0000:02:00.0: reg 18 io port: [0xdc00-0xdc7f]
[    0.858425] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.858428] pci 0000:02:00.0: PME# disabled
[    0.858478] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
[    0.858480] pci 0000:00:06.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
[    0.858540] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbfff800-0xfbffffff]
[    0.858549] pci 0000:03:00.0: reg 18 io port: [0xe800-0xe8ff]
[    0.858620] pci 0000:03:00.0: supports D2
[    0.858621] pci 0000:03:00.0: PME# supported from D2 D3hot D3cold
[    0.858626] pci 0000:03:00.0: PME# disabled
[    0.858684] pci 0000:00:07.0: bridge io port: [0xe000-0xefff]
[    0.858686] pci 0000:00:07.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.858739] pci 0000:00:14.4: transparent bridge
[    0.858758] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.858894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.858945] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.858982] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.859039] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.861668] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 12 14 15)
[    0.861751] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.861832] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.861913] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.861993] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.862075] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.862156] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
[    0.862236] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.862332] SCSI subsystem initialized
[    0.862349] libata version 3.00 loaded.
[    0.862349] usbcore: registered new interface driver usbfs
[    0.862349] usbcore: registered new interface driver hub
[    0.862349] usbcore: registered new device driver usb
[    0.862349] ACPI: WMI: Mapper loaded
[    0.862349] PCI: Using ACPI for IRQ routing
[    0.900010] Bluetooth: Core ver 2.15
[    0.900026] NET: Registered protocol family 31
[    0.900026] Bluetooth: HCI device and connection manager initialized
[    0.900026] Bluetooth: HCI socket layer initialized
[    0.900026] NetLabel: Initializing
[    0.900026] NetLabel:  domain hash size = 128
[    0.900026] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.900026] NetLabel:  unlabeled traffic allowed by default
[    0.900151] PCI-DMA: Disabling AGP.
[    0.900214] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.900215] PCI-DMA: using GART IOMMU.
[    0.900217] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.901650] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.901655] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.910032] hpet: hpet2 irq 24 for MSI
[    0.940016] Switched to high resolution mode on CPU 0
[    0.940828] Switched to high resolution mode on CPU 3
[    0.940832] Switched to high resolution mode on CPU 2
[    0.940836] Switched to high resolution mode on CPU 1
[    0.960028] pnp: PnP ACPI init
[    0.960042] ACPI: bus type pnp registered
[    0.963443] pnp: PnP ACPI: found 14 devices
[    0.963445] ACPI: ACPI bus type pnp unregistered
[    0.963455] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.963457] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.963461] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.963463] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.963464] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.963466] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.963467] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.963469] system 00:08: ioport range 0xc50-0xc51 has been reserved
[    0.963470] system 00:08: ioport range 0xc52-0xc52 has been reserved
[    0.963472] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.963473] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.963475] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.963476] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.963478] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.963479] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.963481] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.963483] system 00:08: ioport range 0xb00-0xb3f has been reserved
[    0.963484] system 00:08: ioport range 0x800-0x89f has been reserved
[    0.963486] system 00:08: ioport range 0xb00-0xb0f has been reserved
[    0.963487] system 00:08: ioport range 0xb20-0xb3f has been reserved
[    0.963489] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.963491] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.963492] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[    0.963494] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.963496] system 00:08: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.963499] system 00:0b: ioport range 0x230-0x23f has been reserved
[    0.963502] system 00:0b: ioport range 0x290-0x29f has been reserved
[    0.963504] system 00:0b: ioport range 0xf40-0xf4f has been reserved
[    0.963505] system 00:0b: ioport range 0xa30-0xa3f has been reserved
[    0.963508] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.963511] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.963512] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    0.963514] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.963515] system 00:0d: iomem range 0x100000-0xcfffffff could not be reserved
[    0.963517] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.968129] AppArmor: AppArmor Filesystem Enabled
[    0.968150] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.968152] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.968154] pci 0000:00:01.0:   MEM window: 0xfbc00000-0xfbdfffff
[    0.968156] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.968159] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.968161] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
[    0.968163] pci 0000:00:06.0:   MEM window: 0xfbe00000-0xfbefffff
[    0.968164] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.968166] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.968168] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.968170] pci 0000:00:07.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.968172] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.968174] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04
[    0.968175] pci 0000:00:14.4:   IO window: disabled
[    0.968179] pci 0000:00:14.4:   MEM window: disabled
[    0.968182] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.968191]   alloc irq_desc for 18 on node 0
[    0.968192]   alloc kstat_irqs on node 0
[    0.968195] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.968197] pci 0000:00:06.0: setting latency timer to 64
[    0.968200]   alloc irq_desc for 19 on node 0
[    0.968201]   alloc kstat_irqs on node 0
[    0.968204] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.968206] pci 0000:00:07.0: setting latency timer to 64
[    0.968212] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.968213] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.968215] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.968216] pci_bus 0000:01: resource 1 mem: [0xfbc00000-0xfbdfffff]
[    0.968218] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.968219] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.968221] pci_bus 0000:02: resource 1 mem: [0xfbe00000-0xfbefffff]
[    0.968222] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.968223] pci_bus 0000:03: resource 1 mem: [0xfbf00000-0xfbffffff]
[    0.968225] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.968226] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.968250] NET: Registered protocol family 2
[    0.968347] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.968987] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.970869] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.971133] TCP: Hash tables configured (established 524288 bind 65536)
[    0.971134] TCP reno registered
[    0.971199] NET: Registered protocol family 1
[    0.971241] Trying to unpack rootfs image as initramfs...
[    1.077146] Freeing initrd memory: 7679k freed
[    1.079243] Scanning for low memory corruption every 60 seconds
[    1.079323] audit: initializing netlink socket (disabled)
[    1.079333] type=2000 audit(1258325208.070:1): initialized
[    1.084686] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.085512] VFS: Disk quotas dquot_6.5.2
[    1.085545] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.085891] fuse init (API version 7.12)
[    1.085937] msgmni has been set to 7421
[    1.086107] alg: No test for stdrng (krng)
[    1.086116] io scheduler noop registered
[    1.086118] io scheduler anticipatory registered
[    1.086119] io scheduler deadline registered
[    1.086140] io scheduler cfq registered (default)
[    1.250033] pci 0000:01:05.0: Boot video device
[    1.250169]   alloc irq_desc for 25 on node 0
[    1.250170]   alloc kstat_irqs on node 0
[    1.250175] pcieport-driver 0000:00:06.0: irq 25 for MSI/MSI-X
[    1.250179] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.250243]   alloc irq_desc for 26 on node 0
[    1.250244]   alloc kstat_irqs on node 0
[    1.250247] pcieport-driver 0000:00:07.0: irq 26 for MSI/MSI-X
[    1.250250] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.250288] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.250300] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.250364] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.250367] ACPI: Power Button [PWRF]
[    1.250398] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.250402] ACPI: Power Button [PWRB]
[    1.250640] processor LNXCPU:00: registered as cooling_device0
[    1.250642] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.250660] processor LNXCPU:01: registered as cooling_device1
[    1.250680] processor LNXCPU:02: registered as cooling_device2
[    1.250699] processor LNXCPU:03: registered as cooling_device3
[    1.253245] Linux agpgart interface v0.103
[    1.253250] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.253346] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.253546] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.254029] brd: module loaded
[    1.254235] loop: module loaded
[    1.254277] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.254357] ahci 0000:00:11.0: version 3.0
[    1.254365]   alloc irq_desc for 22 on node 0
[    1.254366]   alloc kstat_irqs on node 0
[    1.254370] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.254405]   alloc irq_desc for 27 on node 0
[    1.254406]   alloc kstat_irqs on node 0
[    1.254413] ahci 0000:00:11.0: irq 27 for MSI/MSI-X
[    1.254484] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.254487] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.254704] scsi0 : ahci
[    1.254756] scsi1 : ahci
[    1.254784] scsi2 : ahci
[    1.254814] scsi3 : ahci
[    1.254870] ata1: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffd00 irq 27
[    1.254872] ata2: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffd80 irq 27
[    1.254875] ata3: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffe00 irq 27
[    1.254877] ata4: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffe80 irq 27
[    1.255050]   alloc irq_desc for 16 on node 0
[    1.255051]   alloc kstat_irqs on node 0
[    1.255053] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.255071] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.255124] scsi4 : pata_atiixp
[    1.255154] scsi5 : pata_atiixp
[    1.256017] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.256019] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.256348] Fixed MDIO Bus: probed
[    1.256366] PPP generic driver version 2.4.2
[    1.256418] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.256462]   alloc irq_desc for 17 on node 0
[    1.256463]   alloc kstat_irqs on node 0
[    1.256466] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.256477] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.256503] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.256535] ehci_hcd 0000:00:12.2: debug port 1
[    1.256546] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbbff800
[    1.270019] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.270069] usb usb1: configuration #1 chosen from 1 choice
[    1.270085] hub 1-0:1.0: USB hub found
[    1.270089] hub 1-0:1.0: 6 ports detected
[    1.270163] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.270173] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.270189] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.270216] ehci_hcd 0000:00:13.2: debug port 1
[    1.270228] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbbff400
[    1.290019] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.290059] usb usb2: configuration #1 chosen from 1 choice
[    1.290072] hub 2-0:1.0: USB hub found
[    1.290076] hub 2-0:1.0: 6 ports detected
[    1.290122] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.290156] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.290166] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.290182] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.290200] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbbfd000
[    1.354072] usb usb3: configuration #1 chosen from 1 choice
[    1.354089] hub 3-0:1.0: USB hub found
[    1.354095] hub 3-0:1.0: 3 ports detected
[    1.354160] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.354169] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.354186] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.354199] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbbfe000
[    1.414075] usb usb4: configuration #1 chosen from 1 choice
[    1.414089] hub 4-0:1.0: USB hub found
[    1.414095] hub 4-0:1.0: 3 ports detected
[    1.414162] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.414172] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.414188] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.414207] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbbfb000
[    1.474079] usb usb5: configuration #1 chosen from 1 choice
[    1.474092] hub 5-0:1.0: USB hub found
[    1.474098] hub 5-0:1.0: 3 ports detected
[    1.474165] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.474174] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.474191] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.474203] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbbfc000
[    1.534067] usb usb6: configuration #1 chosen from 1 choice
[    1.534082] hub 6-0:1.0: USB hub found
[    1.534090] hub 6-0:1.0: 3 ports detected
[    1.534158] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.534167] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.534183] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.534196] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbbfa000
[    1.591269] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.594071] usb usb7: configuration #1 chosen from 1 choice
[    1.594085] hub 7-0:1.0: USB hub found
[    1.594091] hub 7-0:1.0: 2 ports detected
[    1.594130] uhci_hcd: USB Universal Host Controller Interface driver
[    1.594181] PNP: No PS/2 controller found. Probing ports directly.
[    1.594481] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.594491] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.594546] mice: PS/2 mouse device common for all mice
[    1.594598] rtc_cmos 00:03: RTC can wake from S4
[    1.594616] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.594637] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.594702] device-mapper: uevent: version 1.0.3
[    1.594748] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.594825] device-mapper: multipath: version 1.1.0 loaded
[    1.594828] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.594979] cpuidle: using governor ladder
[    1.594980] cpuidle: using governor menu
[    1.595203] TCP cubic registered
[    1.595272] NET: Registered protocol family 10
[    1.595515] lo: Disabled Privacy Extensions
[    1.595672] NET: Registered protocol family 17
[    1.595682] Bluetooth: L2CAP ver 2.13
[    1.595683] Bluetooth: L2CAP socket layer initialized
[    1.595684] Bluetooth: SCO (Voice Link) ver 0.6
[    1.595685] Bluetooth: SCO socket layer initialized
[    1.595724] Bluetooth: RFCOMM TTY layer initialized
[    1.595725] Bluetooth: RFCOMM socket layer initialized
[    1.595727] Bluetooth: RFCOMM ver 1.11
[    1.595748] powernow-k8: Found 1 AMD Phenom(tm) II X4 965 Processor processors (4 cpu cores) (version 2.20.00)
[    1.595754] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.595754] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    1.595798] PM: Resume from disk failed.
[    1.595804] registered taskstats version 1
[    1.595881]   Magic number: 1:728:805
[    1.595931] rtc_cmos 00:03: setting system clock to 2009-11-15 22:46:49 UTC (1258325209)
[    1.595933] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.595934] EDD information not available.
[    1.601282] ata2: SATA link down (SStatus 0 SControl 300)
[    1.601327] ata4: SATA link down (SStatus 0 SControl 300)
[    1.771689] usb 1-1: configuration #1 chosen from 1 choice
[    1.780025] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.780048] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.780717] ata3.00: ATAPI: ATAPI   DVD A  DH24AAL, ZP5A, max UDMA/100, ATAPI AN
[    1.781001] ata1.00: ATA-8: WDC WD5000AAKS-00V1A0, 05.01D05, max UDMA/133
[    1.781003] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.781727] ata3.00: configured for UDMA/100
[    1.782062] ata1.00: configured for UDMA/133
[    1.800085] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 05.0 PQ: 0 ANSI: 5
[    1.800149] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.800170] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.800189] sd 0:0:0:0: [sda] Write Protect is off
[    1.800190] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.800200] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.800258]  sda:
[    1.801210] scsi 2:0:0:0: CD-ROM            ATAPI    DVD A  DH24AAL   ZP5A PQ: 0 ANSI: 5
[    1.806597] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.806599] Uniform CD-ROM driver Revision: 3.20
[    1.806643] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.806665] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.814807]  sda1 sda2 sda3 sda4
[    1.826281] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.971137] Freeing unused kernel memory: 660k freed
[    1.971254] Write protecting the kernel read-only data: 7580k
[    2.048132] ATL1E 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.048142] ATL1E 0000:02:00.0: setting latency timer to 64
[    2.058258] [drm] Initialized drm 1.1.0 20060810
[    2.059693] ohci1394 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.059699] ohci1394 0000:03:00.0: setting latency timer to 64
[    2.065296] FDC 0 is a post-1991 82077
[    2.068049] [drm] radeon default to kernel modesetting DISABLED.
[    2.068422] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.068425] pci 0000:01:05.0: setting latency timer to 64
[    2.068509] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[    2.122059] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fbfff800-fbffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.203768] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    2.395939] usb 4-2: configuration #1 chosen from 1 choice
[    2.400622] usbcore: registered new interface driver hiddev
[    2.405019] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3
[    2.405056] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:12.1-2/input0
[    2.405064] usbcore: registered new interface driver usbhid
[    2.405065] usbhid: v2.6:USB HID core driver
[    2.723767] usb 4-3: new low speed USB device using ohci_hcd and address 3
[    2.931853] usb 4-3: configuration #1 chosen from 1 choice
[    2.943931] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input4
[    2.943962] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:12.1-3/input0
[    2.958872] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input5
[    2.958899] generic-usb 0003:045E:00DD.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:12.1-3/input1
[    3.026366] PM: Starting manual resume from disk
[    3.026369] PM: Resume from partition 8:2
[    3.026369] PM: Checking hibernation image.
[    3.026491] PM: Resume from disk failed.
[    3.043814] EXT4-fs (sda1): barriers enabled
[    3.055636] kjournald2 starting: pid 453, dev sda1:8, commit interval 5 seconds
[    3.055642] EXT4-fs (sda1): delayed allocation enabled
[    3.055645] EXT4-fs: file extents enabled
[    3.062676] EXT4-fs: mballoc enabled
[    3.062684] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.368353] type=1505 audit(1258325211.267:2): operation="profile_load" pid=476 name=/usr/share/gdm/guest-session/Xsession
[    3.369607] type=1505 audit(1258325211.267:3): operation="profile_load" pid=477 name=/sbin/dhclient3
[    3.369774] type=1505 audit(1258325211.267:4): operation="profile_load" pid=477 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.369869] type=1505 audit(1258325211.267:5): operation="profile_load" pid=477 name=/usr/lib/connman/scripts/dhclient-script
[    3.407689] type=1505 audit(1258325211.307:6): operation="profile_load" pid=478 name=/usr/bin/evince
[    3.410273] type=1505 audit(1258325211.307:7): operation="profile_load" pid=478 name=/usr/bin/evince-previewer
[    3.411838] type=1505 audit(1258325211.307:8): operation="profile_load" pid=478 name=/usr/bin/evince-thumbnailer
[    3.433812] type=1505 audit(1258325211.337:9): operation="profile_load" pid=480 name=/usr/lib/cups/backend/cups-pdf
[    3.434014] type=1505 audit(1258325211.337:10): operation="profile_load" pid=480 name=/usr/sbin/cupsd
[    3.443865] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000ad6078]
[    4.042956] Adding 1020116k swap on /dev/sda2.  Priority:-1 extents:1 across:1020116k 
[    4.348137] udev: starting version 147
[    4.882766] EXT4-fs (sda1): internal journal on sda1:8
[    5.324385] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    5.324388] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.324398] piix4_smbus: probe of 0000:00:14.0 failed with error -16
[    5.732769] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[    5.732772] shpchp 0000:00:01.0: Cannot reserve MMIO region
[    5.733027] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.734757] EDAC MC: Ver: 2.1.0 Oct 16 2009
[    5.735786] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[    5.739389] lp: driver loaded but no devices found
[    5.739909] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    5.739911] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    5.739913] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    5.739914]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    5.739914]     Might be a BIOS bug, if BIOS says ECC is enabled
[    5.739915]     Use of the override can cause unknown side effects.
[    5.740138] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    6.030816] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.460760] __ratelimit: 3 callbacks suppressed
[    6.460762] type=1505 audit(1258346814.357:12): operation="profile_replace" pid=850 name=/usr/share/gdm/guest-session/Xsession
[    6.461597] type=1505 audit(1258346814.357:13): operation="profile_replace" pid=851 name=/sbin/dhclient3
[    6.461767] type=1505 audit(1258346814.357:14): operation="profile_replace" pid=851 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.461861] type=1505 audit(1258346814.357:15): operation="profile_replace" pid=851 name=/usr/lib/connman/scripts/dhclient-script
[    6.463637] type=1505 audit(1258346814.357:16): operation="profile_replace" pid=852 name=/usr/bin/evince
[    6.466213] type=1505 audit(1258346814.367:17): operation="profile_replace" pid=852 name=/usr/bin/evince-previewer
[    6.467780] type=1505 audit(1258346814.367:18): operation="profile_replace" pid=852 name=/usr/bin/evince-thumbnailer
[    6.470650] type=1505 audit(1258346814.367:19): operation="profile_replace" pid=854 name=/usr/lib/cups/backend/cups-pdf
[    6.470854] type=1505 audit(1258346814.367:20): operation="profile_replace" pid=854 name=/usr/sbin/cupsd
[    6.471834] type=1505 audit(1258346814.367:21): operation="profile_replace" pid=855 name=/usr/sbin/tcpdump
[    6.777723] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.894969] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    6.894998] HDA Intel 0000:01:05.1: setting latency timer to 64
[    8.742209] ppdev: user-space parallel port driver
[    9.497402]   alloc irq_desc for 28 on node 0
[    9.497405]   alloc kstat_irqs on node 0
[    9.497416] ATL1E 0000:02:00.0: irq 28 for MSI/MSI-X
[    9.497825] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.773700] usplash:416 freeing invalid memtype ffffffffd0000000-ffffffffd1000000
[   12.179146] [drm] Setting GART location based on new memory map
[   12.194431] [drm] Loading RS780/RS880 CP Microcode
[   12.195081] [drm] Loading RS780/RS880 PFP Microcode
[   12.210183] [drm] Resetting GPU
[   12.210239] [drm] writeback test succeeded in 1 usecs
[   14.450801] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[  199.427665] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  199.429459] rtusb init --->
[  199.429479] usbcore: registered new interface driver rt2870

---

### Post by peepingtom on 2009-11-16
Well I'll confirm that your card is infact using an rt2780 chipset, but it looks like the driver is not detecting your USB device.
It detects ```
{USB_DEVICE(0x1737,0x0070)}, /* Linksys WUSB100 */
```

but of course your device is 0x0078.

---

### Post by churro on 2009-11-16
> **peepingtom said:**
> Well I'll confirm that your card is infact using an rt2780 chipset, but it looks like the driver is not detecting your USB device.
It detects ```
{USB_DEVICE(0x1737,0x0070)}, /* Linksys WUSB100 */
```

but of course your device is 0x0078.


Could it be because I have Version "2" of the adapter I am having these issues that normally rt2780 wouldn't have when using these howto's?

---

### Post by peepingtom on 2009-11-16
Yes that is exactly the problem, what a bad surprise! :D
Believe me, I will make sure this problem is not repeated in the next Ubuntu release!
A simple 1-line change will allow you to compile the driver using regular instructions. I don't have time to make a guide right now, so I'll post some links.

---

### Post by peepingtom on 2009-11-16
Ooo

---

### Post by gahoachma on 2009-11-16
> **peepingtom said:**
> If you're lucky, this will work. If not, there are troubleshooting instructions below.
(This is boilerplate, I was working on a tutorial yesterday!)

Since you don't have net access on that computer, I suggest you copy these commands to a text file and move them to your computer on a flash drive along with config.tar. All this stuff is cAsE sensitive, the capital W on "wireless" in the second command is meant to be there.

I attached a file called config.tar to this post. Download it and save it to your Ubuntu computer's Desktop.

On the main menu at the top of the screen:
Click Applications -> Accessories -> Terminal

Copy and paste is different in the terminal, you either do it by pressing SHIFT+CTRL+C/V or you can do it by right-clicking and selecting it from the context menu. (Shift is added there because CTRL+C is the command to kill a process in terminal).

Input the following commands, pressing enter after each one. 
When it asks for a password, type it and press enter. It will not be displayed as you type it.

```
sudo mkdir -p /etc/Wireless/RT2870STA
``````
cd /etc/Wireless/RT2870STA
``````
sudo tar xvf ~/Desktop/config.tar
```Those commands installed a configuration file that Karmic doesn't generate, i'll file a bug report about this. This rt2870 driver is made by the manufacturer of the chip in your Wifi Adapter, Ralink. It has some strange behaviours, but it works pretty well for most people. Now you'll "blacklist" some conflicting drivers that are made by a community project.

In terminal:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```add these lines to the end of the file:
```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```Save the file, then restart your computer. This most likely has your drivers working, if you have another problem it's likely related to NetworkManager.

I've subscribed to this thread using "thread tools" at the top of this page, i'll receive an email as soon as you reply to this.

Worked quick and easy for me. Im using a linksys dual band wireless-n usb adapter model #: wusb600n

Thanks alot! :p

---

### Post by peepingtom on 2009-11-16
This info is no longer pertinent, a new driver has been released by Ralink. New guide HERE: [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

---

### Post by churro on 2009-11-16
going to try what you said, just got home.

---

### Post by churro on 2009-11-16
paint@jean:~$ cd '/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0' 
paint@jean:~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0$ sudo make
[sudo] password for paint: 
make -C tools
make[1]: Entering directory `/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools'
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
make[2]: Warning: File `/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/config.mk' has modification time 1.8e+04 s in the future
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_aes.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1664 bytes is larger than 1024 bytes
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_UNWRAP’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_aes.c:2348: warning: the frame size of 1168 bytes is larger than 1024 bytes
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1408 bytes is larger than 1024 bytes
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1408 bytes is larger than 1024 bytes
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/mlme.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/mlme.c:838: warning: cast from pointer to integer of different size
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/mlme.c:838: warning: cast from pointer to integer of different size
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/mlme.c:4533: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/action.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_aes.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_wpa.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_wpa.c: In function ‘ConstructEapolKeyData’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_wpa.c:2909: warning: unused variable ‘pAd’
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/spectrum.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/spectrum.c:1910: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/rt_channel.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_profile.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_asic.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/auth.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/auth.c: In function ‘PeerAuthRspAtSeq2Action’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/auth.c:157: warning: unused variable ‘Element’
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sync.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sync.c: In function ‘MlmeScanReqAction’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sync.c:184: warning: unused variable ‘pHdr80211’
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sync.c:679: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sync.c:1503: warning: the frame size of 1456 bytes is larger than 1024 bytes
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sync.c:958: warning: the frame size of 1392 bytes is larger than 1024 bytes
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sync.c:548: warning: the frame size of 1088 bytes is larger than 1024 bytes
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/rtmp_data.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/rtmp_data.c: In function ‘STARxEAPOLFrameIndicate’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/rtmp_data.c:47: warning: unused variable ‘pRxD’
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxMgmtFrame’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/rtmp_data.c:676: warning: unused variable ‘pRxD’
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/rtmp_data.c: In function ‘STASendPacket’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/rtmp_data.c:1080: warning: unused variable ‘FlgIsIP’
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/connect.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/connect.c: In function ‘LinkDown’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/connect.c:1929: warning: unused variable ‘Cancelled’
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/connect.c:344: warning: the frame size of 1632 bytes is larger than 1024 bytes
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../sta/wpa.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:537: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:539: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:632: warning: assignment makes integer from pointer without a cast
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:654: warning: assignment makes integer from pointer without a cast
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:674: warning: assignment makes integer from pointer without a cast
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:912: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSIRQRequest’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1068: warning: unused variable ‘net_dev’
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSTaskAttach’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1282: warning: unused variable ‘pid_number’
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1057: warning: the frame size of 1088 bytes is larger than 1024 bytes
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_main_dev.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_main_dev.c: In function ‘RtmpPhyNetDevInit’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_main_dev.c:554: warning: assignment discards qualifiers from pointer target type
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/sta_ioctl.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/sta_ioctl.c:1908: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/sta_ioctl.c:1051: warning: the frame size of 1296 bytes is larger than 1024 bytes
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/sta_ioctl.c:7266: warning: the frame size of 1376 bytes is larger than 1024 bytes
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/sta_ioctl.c:7068: warning: the frame size of 1376 bytes is larger than 1024 bytes
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/sta_ioctl.c:2420: warning: the frame size of 1632 bytes is larger than 1024 bytes
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/ba_action.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/ba_action.c:1524: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/usb_main_dev.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_mac_usb.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/rtusb_io.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/rtusb_bulk.o
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/rtusb_bulk.c: In function ‘RTUSBInitRxDesc’:
/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/rtusb_bulk.c:134: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
include/linux/usb.h:1270: note: expected ‘usb_complete_t’ but argument is of type ‘USBHST_STATUS (*)(struct urb *, struct pt_regs *)’
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/rtusb_data.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/ee_prom.o
  CC [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.o
make[2]: warning:  Clock skew detected.  Your build may be incomplete.
  Building modules, stage 2.
make[2]: Warning: File `/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/config.mk' has modification time 1.8e+04 s in the future
  MODPOST 1 modules
  CC      /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.mod.o
  LD [M]  /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko
make[2]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
cp -f /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko /tftpboot
paint@jean:~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0$ sudo make install
make -C /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux'
make[1]: Warning: File `/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/config.mk' has modification time 1.8e+04 s in the future
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.31-14-generic
make[1]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: Leaving directory `/home/paint/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux'
paint@jean:~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0$

---

### Post by churro on 2009-11-16
not working, I haven't tried the added last line, Will restart and try that line.

---

### Post by churro on 2009-11-16
not working with additional "last step line" :-k

---

### Post by peepingtom on 2009-11-16
This info is no longer pertinent, a new driver has been released by Ralink. New guide HERE: [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

---

### Post by churro on 2009-11-16
[    6.358116] EXT4-fs (sda1): internal journal on sda1:8
[    6.434970] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.797023] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    6.797052] HDA Intel 0000:01:05.1: setting latency timer to 64
[    7.605527] __ratelimit: 3 callbacks suppressed
[    7.605529] type=1505 audit(1258416192.515:12): operation="profile_replace" pid=864 name=/usr/share/gdm/guest-session/Xsession
[    7.606360] type=1505 audit(1258416192.515:13): operation="profile_replace" pid=865 name=/sbin/dhclient3
[    7.606529] type=1505 audit(1258416192.515:14): operation="profile_replace" pid=865 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.606624] type=1505 audit(1258416192.515:15): operation="profile_replace" pid=865 name=/usr/lib/connman/scripts/dhclient-script
[    7.608381] type=1505 audit(1258416192.515:16): operation="profile_replace" pid=866 name=/usr/bin/evince
[    7.610967] type=1505 audit(1258416192.515:17): operation="profile_replace" pid=866 name=/usr/bin/evince-previewer
[    7.612519] type=1505 audit(1258416192.525:18): operation="profile_replace" pid=866 name=/usr/bin/evince-thumbnailer
[    7.615425] type=1505 audit(1258416192.525:19): operation="profile_replace" pid=868 name=/usr/lib/cups/backend/cups-pdf
[    7.615627] type=1505 audit(1258416192.525:20): operation="profile_replace" pid=868 name=/usr/sbin/cupsd
[    7.616609] type=1505 audit(1258416192.525:21): operation="profile_replace" pid=869 name=/usr/sbin/tcpdump
[    9.343237]   alloc irq_desc for 28 on node 0
[    9.343240]   alloc kstat_irqs on node 0
[    9.343250] ATL1E 0000:02:00.0: irq 28 for MSI/MSI-X
[    9.343678] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.807556] ppdev: user-space parallel port driver
[   11.393315] usplash:380 freeing invalid memtype ffffffffd0000000-ffffffffd1000000
[   12.532736] [drm] Setting GART location based on new memory map
[   12.548019] [drm] Loading RS780/RS880 CP Microcode
[   12.548663] [drm] Loading RS780/RS880 PFP Microcode
[   12.563772] [drm] Resetting GPU
[   12.563827] [drm] writeback test succeeded in 1 usecs
[   14.969586] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[  150.229211] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  150.230984] rtusb init --->
[  150.231005] usbcore: registered new interface driver rt2870
[ 1055.210029] usb 1-1: USB disconnect, address 2
[ 1066.220023] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 1066.401798] usb 1-1: configuration #1 chosen from 1 choice

---

### Post by churro on 2009-11-16
that was after sudo modprobe rt2870sta

Tried restarting, Unplugging/Plug adaptor, nothing yet.

---

### Post by peepingtom on 2009-11-16
I still need to know what happens when you do these things though, in chronological order.



Boot your computer without the USB device inserted 
Then after you are logged in and it is fully booted, insert the Wifi adapter.
Then run these commands within 30s of insertion and post the output.
```
dmesg
lsmod
modinfo rt2870sta

```

Don't do modprobe.

That last command will tell me if the module you compiled has built-in support for your adapter's USB Device ID, I hope it does!

---

### Post by churro on 2009-11-16
paint@jean:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=f1a41299-a303-4bb1-9fd7-1a6007ec7825 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  BIOS-e820: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffa8000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff90 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  modified: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  modified: 00000000cffa8000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff90000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff90000 page 4k
[    0.000000] kernel direct mapping tables up to cff90000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ 12000-14000
[    0.000000] RAMDISK: 3786d000 - 37fef78b
[    0.000000] ACPI: RSDP 00000000000fb880 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cff90000 00038 (v01 102809 RSDT1549 20091028 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff90200 00084 (v01 102809 FACP1549 20091028 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 20090521 tbfadt-558
[    0.000000] ACPI: DSDT 00000000cff90440 0E774 (v01  A1152 A1152000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cffa8000 00040
[    0.000000] ACPI: APIC 00000000cff90390 0006C (v01 102809 APIC1549 20091028 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff90400 0003C (v01 102809 OEMMCFG  20091028 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cffa8040 00072 (v01 102809 OEMB1549 20091028 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff9f440 00038 (v01 102809 OEMHPET  20091028 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000003bfff] pages 24
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0120000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [003786d000 - 0037fef78b]          RAMDISK ==> [003786d000 - 0037fef78b]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3290]              BRK ==> [00019e3000 - 00019e3290]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff880028600000-ffff88002bbfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cff90
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 982815
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3825 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833480 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff90000 - 00000000cffa8000
[    0.000000] PM: Registered nosave memory: 00000000cffa8000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ff00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff88002801f000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 966585
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=f1a41299-a303-4bb1-9fd7-1a6007ec7825 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 8034000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 3791904k/4718592k available (5313k kernel code, 787332k absent, 139356k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3411.770 MHz processor.
[    0.000009] spurious 8259A interrupt: IRQ7.
[    0.000600] Console: colour VGA+ 80x25
[    0.000602] console [tty0] enabled
[    0.009730] allocated 39321600 bytes of page_cgroup
[    0.009732] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.009842] hpet clockevent registered
[    0.009847]   alloc irq_desc for 24 on node 0
[    0.009849]   alloc kstat_irqs on node 0
[    0.009854] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6823.53 BogoMIPS (lpj=34117650)
[    0.010019] Security Framework initialized
[    0.010033] AppArmor: AppArmor initialized
[    0.010224] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.011350] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011865] Mount-cache hash table entries: 256
[    0.011948] Initializing cgroup subsys ns
[    0.011951] Initializing cgroup subsys cpuacct
[    0.011953] Initializing cgroup subsys memory
[    0.011958] Initializing cgroup subsys freezer
[    0.011959] Initializing cgroup subsys net_cls
[    0.011967] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.011968] CPU: L2 Cache: 512K (64 bytes/line)
[    0.011970] CPU 0/0x0 -> Node 0
[    0.011972] tseg: 0000000000
[    0.011981] CPU: Physical Processor ID: 0
[    0.011982] CPU: Processor Core ID: 0
[    0.011984] mce: CPU supports 6 MCE banks
[    0.011990] using C1E aware idle routine
[    0.011991] Performance Counters: AMD PMU driver.
[    0.011994] ... version:                 0
[    0.011995] ... bit width:               48
[    0.011996] ... generic counters:        4
[    0.011997] ... value mask:              0000ffffffffffff
[    0.011998] ... max period:              00007fffffffffff
[    0.011999] ... fixed-purpose counters:  0
[    0.012000] ... counter mask:            000000000000000f
[    0.013052] ACPI: Core revision 20090521
[    0.030043] Setting APIC routing to flat
[    0.030332] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.133866] CPU0: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 6823.26 BogoMIPS (lpj=34116309)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.290838] CPU1: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.290844] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300041] Booting processor 2 APIC 0x2 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 6823.26 BogoMIPS (lpj=34116338)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 2/0x2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.460911] CPU2: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.460916] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.470041] Booting processor 3 APIC 0x3 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 6823.26 BogoMIPS (lpj=34116314)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 3/0x3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.630883] CPU3: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.630888] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.640007] Brought up 4 CPUs
[    0.640009] Total of 4 processors activated (27293.32 BogoMIPS).
[    0.640051] CPU0 attaching sched-domain:
[    0.640053]  domain 0: span 0-3 level MC
[    0.640055]   groups: 0 1 2 3
[    0.640058] CPU1 attaching sched-domain:
[    0.640059]  domain 0: span 0-3 level MC
[    0.640060]   groups: 1 2 3 0
[    0.640063] CPU2 attaching sched-domain:
[    0.640064]  domain 0: span 0-3 level MC
[    0.640065]   groups: 2 3 0 1
[    0.640068] CPU3 attaching sched-domain:
[    0.640069]  domain 0: span 0-3 level MC
[    0.640070]   groups: 3 0 1 2
[    0.640122] Booting paravirtualized kernel on bare hardware
[    0.640122] regulator: core version 0.5
[    0.640122] Time: 19:20:15  Date: 11/16/09
[    0.640122] NET: Registered protocol family 16
[    0.640130] node 0 link 0: io port [1000, ffffff]
[    0.640132] TOM: 00000000d0000000 aka 3328M
[    0.640133] Fam 10h mmconf [e0000000, efffffff]
[    0.640135] node 0 link 0: mmio [a0000, bffff]
[    0.640137] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.640139] node 0 link 0: mmio [f0000000, fbbfffff]
[    0.640141] node 0 link 0: mmio [fbc00000, fbdfffff]
[    0.640142] node 0 link 0: mmio [fbe00000, ffefffff]
[    0.640143] TOM2: 0000000130000000 aka 4864M
[    0.640145] bus: [00,07] on node 0 link 0
[    0.640146] bus: 00 index 0 io port: [0, ffff]
[    0.640147] bus: 00 index 1 mmio: [a0000, bffff]
[    0.640148] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.640150] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.640151] bus: 00 index 4 mmio: [130000000, fcffffffff]
[    0.640158] ACPI: bus type pci registered
[    0.640202] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.640204] PCI: Not using MMCONFIG.
[    0.640205] PCI: Using configuration type 1 for base access
[    0.640206] PCI: Using configuration type 1 for extended access
[    0.640226] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.640227] mtrr: probably your BIOS does not setup all CPUs.
[    0.640228] mtrr: corrected configuration.
[    0.640617] bio: create slab <bio-0> at 0
[    0.640617] ACPI: EC: Look up EC in DSDT
[    0.842501] ACPI: Interpreter enabled
[    0.842505] ACPI: (supports S0 S1 S3 S4 S5)
[    0.842520] ACPI: Using IOAPIC for interrupt routing
[    0.842565] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.846443] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.851629] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.857302] ACPI Warning: Incorrect checksum in table [OEMB] - AE, should be A5 20090521 tbutils-246
[    0.857379] ACPI: No dock devices found.
[    0.857490] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.857583] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.857586] pci 0000:00:06.0: PME# disabled
[    0.857609] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.857611] pci 0000:00:07.0: PME# disabled
[    0.857657] pci 0000:00:11.0: reg 10 io port: [0xb000-0xb007]
[    0.857663] pci 0000:00:11.0: reg 14 io port: [0xa000-0xa003]
[    0.857669] pci 0000:00:11.0: reg 18 io port: [0x9000-0x9007]
[    0.857674] pci 0000:00:11.0: reg 1c io port: [0x8000-0x8003]
[    0.857680] pci 0000:00:11.0: reg 20 io port: [0x7000-0x700f]
[    0.857685] pci 0000:00:11.0: reg 24 32bit mmio: [0xfbbffc00-0xfbbfffff]
[    0.857701] pci 0000:00:11.0: set SATA to AHCI mode
[    0.857742] pci 0000:00:12.0: reg 10 32bit mmio: [0xfbbfd000-0xfbbfdfff]
[    0.857790] pci 0000:00:12.1: reg 10 32bit mmio: [0xfbbfe000-0xfbbfefff]
[    0.857853] pci 0000:00:12.2: reg 10 32bit mmio: [0xfbbff800-0xfbbff8ff]
[    0.857899] pci 0000:00:12.2: supports D1 D2
[    0.857901] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.857904] pci 0000:00:12.2: PME# disabled
[    0.857931] pci 0000:00:13.0: reg 10 32bit mmio: [0xfbbfb000-0xfbbfbfff]
[    0.857978] pci 0000:00:13.1: reg 10 32bit mmio: [0xfbbfc000-0xfbbfcfff]
[    0.858041] pci 0000:00:13.2: reg 10 32bit mmio: [0xfbbff400-0xfbbff4ff]
[    0.858087] pci 0000:00:13.2: supports D1 D2
[    0.858088] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.858092] pci 0000:00:13.2: PME# disabled
[    0.858194] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.858199] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.858204] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.858210] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.858215] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.858272] pci 0000:00:14.2: reg 10 64bit mmio: [0xfbbf4000-0xfbbf7fff]
[    0.858310] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.858313] pci 0000:00:14.2: PME# disabled
[    0.858404] pci 0000:00:14.5: reg 10 32bit mmio: [0xfbbfa000-0xfbbfafff]
[    0.858511] pci 0000:01:05.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.858513] pci 0000:01:05.0: reg 14 io port: [0xc000-0xc0ff]
[    0.858516] pci 0000:01:05.0: reg 18 32bit mmio: [0xfbde0000-0xfbdeffff]
[    0.858521] pci 0000:01:05.0: reg 24 32bit mmio: [0xfbc00000-0xfbcfffff]
[    0.858530] pci 0000:01:05.0: supports D1 D2
[    0.858543] pci 0000:01:05.1: reg 10 32bit mmio: [0xfbdfc000-0xfbdfffff]
[    0.858557] pci 0000:01:05.1: supports D1 D2
[    0.858593] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.858594] pci 0000:00:01.0: bridge 32bit mmio: [0xfbc00000-0xfbdfffff]
[    0.858597] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.858636] pci 0000:02:00.0: reg 10 64bit mmio: [0xfbec0000-0xfbefffff]
[    0.858642] pci 0000:02:00.0: reg 18 io port: [0xdc00-0xdc7f]
[    0.858688] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.858691] pci 0000:02:00.0: PME# disabled
[    0.858742] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
[    0.858744] pci 0000:00:06.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
[    0.858804] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbfff800-0xfbffffff]
[    0.858813] pci 0000:03:00.0: reg 18 io port: [0xe800-0xe8ff]
[    0.858884] pci 0000:03:00.0: supports D2
[    0.858885] pci 0000:03:00.0: PME# supported from D2 D3hot D3cold
[    0.858890] pci 0000:03:00.0: PME# disabled
[    0.858949] pci 0000:00:07.0: bridge io port: [0xe000-0xefff]
[    0.858951] pci 0000:00:07.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.859004] pci 0000:00:14.4: transparent bridge
[    0.859022] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.859160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.859210] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.859248] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.859304] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.861929] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 12 14 15)
[    0.862012] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.862093] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.862174] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.862255] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.862336] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.862417] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
[    0.862498] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.862594] SCSI subsystem initialized
[    0.862615] libata version 3.00 loaded.
[    0.862615] usbcore: registered new interface driver usbfs
[    0.862615] usbcore: registered new interface driver hub
[    0.862615] usbcore: registered new device driver usb
[    0.862615] ACPI: WMI: Mapper loaded
[    0.862615] PCI: Using ACPI for IRQ routing
[    0.900010] Bluetooth: Core ver 2.15
[    0.900026] NET: Registered protocol family 31
[    0.900026] Bluetooth: HCI device and connection manager initialized
[    0.900026] Bluetooth: HCI socket layer initialized
[    0.900026] NetLabel: Initializing
[    0.900026] NetLabel:  domain hash size = 128
[    0.900026] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.900026] NetLabel:  unlabeled traffic allowed by default
[    0.900152] PCI-DMA: Disabling AGP.
[    0.900215] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.900216] PCI-DMA: using GART IOMMU.
[    0.900218] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.901669] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.901674] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.910031] hpet: hpet2 irq 24 for MSI
[    0.930016] Switched to high resolution mode on CPU 0
[    0.930808] Switched to high resolution mode on CPU 1
[    0.930852] Switched to high resolution mode on CPU 3
[    0.930880] Switched to high resolution mode on CPU 2
[    0.950029] pnp: PnP ACPI init
[    0.950043] ACPI: bus type pnp registered
[    0.953446] pnp: PnP ACPI: found 14 devices
[    0.953448] ACPI: ACPI bus type pnp unregistered
[    0.953456] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.953458] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.953462] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.953464] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.953466] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.953467] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.953469] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.953470] system 00:08: ioport range 0xc50-0xc51 has been reserved
[    0.953472] system 00:08: ioport range 0xc52-0xc52 has been reserved
[    0.953473] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.953475] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.953477] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.953478] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.953480] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.953481] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.953483] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.953484] system 00:08: ioport range 0xb00-0xb3f has been reserved
[    0.953486] system 00:08: ioport range 0x800-0x89f has been reserved
[    0.953487] system 00:08: ioport range 0xb00-0xb0f has been reserved
[    0.953489] system 00:08: ioport range 0xb20-0xb3f has been reserved
[    0.953491] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.953492] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.953494] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[    0.953496] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.953498] system 00:08: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.953501] system 00:0b: ioport range 0x230-0x23f has been reserved
[    0.953504] system 00:0b: ioport range 0x290-0x29f has been reserved
[    0.953505] system 00:0b: ioport range 0xf40-0xf4f has been reserved
[    0.953507] system 00:0b: ioport range 0xa30-0xa3f has been reserved
[    0.953509] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.953512] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.953514] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    0.953515] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.953517] system 00:0d: iomem range 0x100000-0xcfffffff could not be reserved
[    0.953519] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.958131] AppArmor: AppArmor Filesystem Enabled
[    0.958152] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.958153] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.958156] pci 0000:00:01.0:   MEM window: 0xfbc00000-0xfbdfffff
[    0.958158] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.958161] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.958162] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
[    0.958164] pci 0000:00:06.0:   MEM window: 0xfbe00000-0xfbefffff
[    0.958166] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.958168] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.958169] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.958172] pci 0000:00:07.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.958173] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.958175] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04
[    0.958176] pci 0000:00:14.4:   IO window: disabled
[    0.958180] pci 0000:00:14.4:   MEM window: disabled
[    0.958183] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.958192]   alloc irq_desc for 18 on node 0
[    0.958194]   alloc kstat_irqs on node 0
[    0.958197] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.958199] pci 0000:00:06.0: setting latency timer to 64
[    0.958202]   alloc irq_desc for 19 on node 0
[    0.958203]   alloc kstat_irqs on node 0
[    0.958205] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.958207] pci 0000:00:07.0: setting latency timer to 64
[    0.958213] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.958215] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.958216] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.958218] pci_bus 0000:01: resource 1 mem: [0xfbc00000-0xfbdfffff]
[    0.958219] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.958221] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.958222] pci_bus 0000:02: resource 1 mem: [0xfbe00000-0xfbefffff]
[    0.958224] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.958225] pci_bus 0000:03: resource 1 mem: [0xfbf00000-0xfbffffff]
[    0.958226] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.958228] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.958251] NET: Registered protocol family 2
[    0.958348] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.958988] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.960898] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.961166] TCP: Hash tables configured (established 524288 bind 65536)
[    0.961168] TCP reno registered
[    0.961230] NET: Registered protocol family 1
[    0.961278] Trying to unpack rootfs image as initramfs...
[    1.066942] Freeing initrd memory: 7689k freed
[    1.069026] Scanning for low memory corruption every 60 seconds
[    1.069105] audit: initializing netlink socket (disabled)
[    1.069114] type=2000 audit(1258399215.060:1): initialized
[    1.074468] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.075261] VFS: Disk quotas dquot_6.5.2
[    1.075294] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.075626] fuse init (API version 7.12)
[    1.075670] msgmni has been set to 7421
[    1.075841] alg: No test for stdrng (krng)
[    1.075850] io scheduler noop registered
[    1.075851] io scheduler anticipatory registered
[    1.075852] io scheduler deadline registered
[    1.075873] io scheduler cfq registered (default)
[    1.240034] pci 0000:01:05.0: Boot video device
[    1.240170]   alloc irq_desc for 25 on node 0
[    1.240171]   alloc kstat_irqs on node 0
[    1.240176] pcieport-driver 0000:00:06.0: irq 25 for MSI/MSI-X
[    1.240180] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.240244]   alloc irq_desc for 26 on node 0
[    1.240245]   alloc kstat_irqs on node 0
[    1.240248] pcieport-driver 0000:00:07.0: irq 26 for MSI/MSI-X
[    1.240251] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.240290] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.240302] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.240365] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.240368] ACPI: Power Button [PWRF]
[    1.240399] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.240403] ACPI: Power Button [PWRB]
[    1.240643] processor LNXCPU:00: registered as cooling_device0
[    1.240645] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.240663] processor LNXCPU:01: registered as cooling_device1
[    1.240683] processor LNXCPU:02: registered as cooling_device2
[    1.240701] processor LNXCPU:03: registered as cooling_device3
[    1.243243] Linux agpgart interface v0.103
[    1.243249] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.243345] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.243546] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.244030] brd: module loaded
[    1.244236] loop: module loaded
[    1.244277] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.244357] ahci 0000:00:11.0: version 3.0
[    1.244366]   alloc irq_desc for 22 on node 0
[    1.244367]   alloc kstat_irqs on node 0
[    1.244370] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.244405]   alloc irq_desc for 27 on node 0
[    1.244406]   alloc kstat_irqs on node 0
[    1.244413] ahci 0000:00:11.0: irq 27 for MSI/MSI-X
[    1.244485] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.244487] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.244704] scsi0 : ahci
[    1.244757] scsi1 : ahci
[    1.244786] scsi2 : ahci
[    1.244815] scsi3 : ahci
[    1.244870] ata1: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffd00 irq 27
[    1.244872] ata2: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffd80 irq 27
[    1.244875] ata3: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffe00 irq 27
[    1.244877] ata4: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffe80 irq 27
[    1.245049]   alloc irq_desc for 16 on node 0
[    1.245050]   alloc kstat_irqs on node 0
[    1.245052] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.245069] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.245123] scsi4 : pata_atiixp
[    1.245152] scsi5 : pata_atiixp
[    1.246016] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.246018] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.246343] Fixed MDIO Bus: probed
[    1.246362] PPP generic driver version 2.4.2
[    1.246414] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.246460]   alloc irq_desc for 17 on node 0
[    1.246461]   alloc kstat_irqs on node 0
[    1.246463] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.246474] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.246499] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.246532] ehci_hcd 0000:00:12.2: debug port 1
[    1.246543] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbbff800
[    1.260020] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.260071] usb usb1: configuration #1 chosen from 1 choice
[    1.260086] hub 1-0:1.0: USB hub found
[    1.260091] hub 1-0:1.0: 6 ports detected
[    1.260165] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.260174] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.260191] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.260217] ehci_hcd 0000:00:13.2: debug port 1
[    1.260230] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbbff400
[    1.280020] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.280059] usb usb2: configuration #1 chosen from 1 choice
[    1.280072] hub 2-0:1.0: USB hub found
[    1.280076] hub 2-0:1.0: 6 ports detected
[    1.280122] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.280156] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.280166] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.280182] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.280200] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbbfd000
[    1.344073] usb usb3: configuration #1 chosen from 1 choice
[    1.344090] hub 3-0:1.0: USB hub found
[    1.344096] hub 3-0:1.0: 3 ports detected
[    1.344161] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.344170] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.344187] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.344200] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbbfe000
[    1.404072] usb usb4: configuration #1 chosen from 1 choice
[    1.404085] hub 4-0:1.0: USB hub found
[    1.404091] hub 4-0:1.0: 3 ports detected
[    1.404159] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.404168] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.404184] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.404204] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbbfb000
[    1.464080] usb usb5: configuration #1 chosen from 1 choice
[    1.464093] hub 5-0:1.0: USB hub found
[    1.464099] hub 5-0:1.0: 3 ports detected
[    1.464167] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.464176] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.464193] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.464206] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbbfc000
[    1.524068] usb usb6: configuration #1 chosen from 1 choice
[    1.524084] hub 6-0:1.0: USB hub found
[    1.524091] hub 6-0:1.0: 3 ports detected
[    1.524159] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.524169] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.524185] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.524198] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbbfa000
[    1.584071] usb usb7: configuration #1 chosen from 1 choice
[    1.584085] hub 7-0:1.0: USB hub found
[    1.584091] hub 7-0:1.0: 2 ports detected
[    1.584129] uhci_hcd: USB Universal Host Controller Interface driver
[    1.584181] PNP: No PS/2 controller found. Probing ports directly.
[    1.584486] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.584498] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.584554] mice: PS/2 mouse device common for all mice
[    1.584607] rtc_cmos 00:03: RTC can wake from S4
[    1.584626] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.584647] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.584712] device-mapper: uevent: version 1.0.3
[    1.584758] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.584835] device-mapper: multipath: version 1.1.0 loaded
[    1.584838] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.584991] cpuidle: using governor ladder
[    1.584992] cpuidle: using governor menu
[    1.585214] TCP cubic registered
[    1.585284] NET: Registered protocol family 10
[    1.585527] lo: Disabled Privacy Extensions
[    1.585683] NET: Registered protocol family 17
[    1.585693] Bluetooth: L2CAP ver 2.13
[    1.585694] Bluetooth: L2CAP socket layer initialized
[    1.585695] Bluetooth: SCO (Voice Link) ver 0.6
[    1.585696] Bluetooth: SCO socket layer initialized
[    1.585735] Bluetooth: RFCOMM TTY layer initialized
[    1.585736] Bluetooth: RFCOMM socket layer initialized
[    1.585737] Bluetooth: RFCOMM ver 1.11
[    1.585759] powernow-k8: Found 1 AMD Phenom(tm) II X4 965 Processor processors (4 cpu cores) (version 2.20.00)
[    1.585765] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.585765] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    1.585809] PM: Resume from disk failed.
[    1.585815] registered taskstats version 1
[    1.585893]   Magic number: 1:520:344
[    1.585900] tty tty61: hash matches
[    1.585945] rtc_cmos 00:03: setting system clock to 2009-11-16 19:20:16 UTC (1258399216)
[    1.585947] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.585948] EDD information not available.
[    1.591283] ata2: SATA link down (SStatus 0 SControl 300)
[    1.591344] ata4: SATA link down (SStatus 0 SControl 300)
[    1.770026] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.770047] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.770056] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    1.770736] ata3.00: ATAPI: ATAPI   DVD A  DH24AAL, ZP5A, max UDMA/100, ATAPI AN
[    1.770976] ata1.00: ATA-8: WDC WD5000AAKS-00V1A0, 05.01D05, max UDMA/133
[    1.770978] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.771745] ata3.00: configured for UDMA/100
[    1.772018] ata1.00: configured for UDMA/133
[    1.800806] ata3: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
[    1.800808] ata3: irq_stat 0x40000008
[    1.800860] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 05.0 PQ: 0 ANSI: 5
[    1.800924] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.800944] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.800964] sd 0:0:0:0: [sda] Write Protect is off
[    1.800965] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.800975] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.801033]  sda:
[    1.801987] scsi 2:0:0:0: CD-ROM            ATAPI    DVD A  DH24AAL   ZP5A PQ: 0 ANSI: 5
[    1.807632] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.807634] Uniform CD-ROM driver Revision: 3.20
[    1.807676] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.807698] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.810990]  sda1 sda2 sda3 sda4
[    1.823946] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.971134] Freeing unused kernel memory: 660k freed
[    1.971251] Write protecting the kernel read-only data: 7580k
[    1.982064] usb 4-2: configuration #1 chosen from 1 choice
[    2.036599] [drm] Initialized drm 1.1.0 20060810
[    2.045436] [drm] radeon default to kernel modesetting DISABLED.
[    2.045814] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.045817] pci 0000:01:05.0: setting latency timer to 64
[    2.045915] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[    2.056692] ATL1E 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.056702] ATL1E 0000:02:00.0: setting latency timer to 64
[    2.057869] ohci1394 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.057876] ohci1394 0000:03:00.0: setting latency timer to 64
[    2.059456] usbcore: registered new interface driver hiddev
[    2.063157] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3
[    2.063200] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:12.1-2/input0
[    2.063208] usbcore: registered new interface driver usbhid
[    2.063209] usbhid: v2.6:USB HID core driver
[    2.067509] FDC 0 is a post-1991 82077
[    2.122069] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fbfff800-fbffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.293776] usb 4-3: new low speed USB device using ohci_hcd and address 3
[    2.492050] usb 4-3: configuration #1 chosen from 1 choice
[    2.504125] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input4
[    2.504158] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:12.1-3/input0
[    2.519068] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input5
[    2.519097] generic-usb 0003:045E:00DD.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:12.1-3/input1
[    3.046681] PM: Starting manual resume from disk
[    3.046683] PM: Resume from partition 8:2
[    3.046684] PM: Checking hibernation image.
[    3.046802] PM: Resume from disk failed.
[    3.056842] EXT4-fs (sda1): barriers enabled
[    3.068638] kjournald2 starting: pid 441, dev sda1:8, commit interval 5 seconds
[    3.068644] EXT4-fs (sda1): delayed allocation enabled
[    3.068647] EXT4-fs: file extents enabled
[    3.075696] EXT4-fs: mballoc enabled
[    3.075703] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.391189] type=1505 audit(1258399218.297:2): operation="profile_load" pid=464 name=/usr/share/gdm/guest-session/Xsession
[    3.392402] type=1505 audit(1258399218.305:3): operation="profile_load" pid=465 name=/sbin/dhclient3
[    3.392570] type=1505 audit(1258399218.305:4): operation="profile_load" pid=465 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.392664] type=1505 audit(1258399218.305:5): operation="profile_load" pid=465 name=/usr/lib/connman/scripts/dhclient-script
[    3.422493] type=1505 audit(1258399218.327:6): operation="profile_load" pid=466 name=/usr/bin/evince
[    3.425073] type=1505 audit(1258399218.337:7): operation="profile_load" pid=466 name=/usr/bin/evince-previewer
[    3.426618] type=1505 audit(1258399218.337:8): operation="profile_load" pid=466 name=/usr/bin/evince-thumbnailer
[    3.443877] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000ad6078]
[    3.446848] type=1505 audit(1258399218.357:9): operation="profile_load" pid=468 name=/usr/lib/cups/backend/cups-pdf
[    3.447056] type=1505 audit(1258399218.357:10): operation="profile_load" pid=468 name=/usr/sbin/cupsd
[    4.364276] Adding 1020116k swap on /dev/sda2.  Priority:-1 extents:1 across:1020116k 
[    4.822654] udev: starting version 147
[    5.560429] EXT4-fs (sda1): internal journal on sda1:8
[    6.350478] lp: driver loaded but no devices found
[    6.555508] EDAC MC: Ver: 2.1.0 Oct 16 2009
[    6.625499] __ratelimit: 3 callbacks suppressed
[    6.625501] type=1505 audit(1258420821.537:12): operation="profile_replace" pid=812 name=/usr/share/gdm/guest-session/Xsession
[    6.626336] type=1505 audit(1258420821.537:13): operation="profile_replace" pid=813 name=/sbin/dhclient3
[    6.626505] type=1505 audit(1258420821.537:14): operation="profile_replace" pid=813 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.626599] type=1505 audit(1258420821.537:15): operation="profile_replace" pid=813 name=/usr/lib/connman/scripts/dhclient-script
[    6.628395] type=1505 audit(1258420821.537:16): operation="profile_replace" pid=814 name=/usr/bin/evince
[    6.630973] type=1505 audit(1258420821.537:17): operation="profile_replace" pid=814 name=/usr/bin/evince-previewer
[    6.632556] type=1505 audit(1258420821.537:18): operation="profile_replace" pid=814 name=/usr/bin/evince-thumbnailer
[    6.635384] type=1505 audit(1258420821.547:19): operation="profile_replace" pid=816 name=/usr/lib/cups/backend/cups-pdf
[    6.635588] type=1505 audit(1258420821.547:20): operation="profile_replace" pid=816 name=/usr/sbin/cupsd
[    6.636495] type=1505 audit(1258420821.547:21): operation="profile_replace" pid=817 name=/usr/sbin/tcpdump
[    6.645324] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[    6.646374] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[    6.646377] shpchp 0000:00:01.0: Cannot reserve MMIO region
[    6.646627] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    6.646629] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.646636] piix4_smbus: probe of 0000:00:14.0 failed with error -16
[    6.646857] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    6.646859] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    6.646860] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    6.646861]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    6.646862]     Might be a BIOS bug, if BIOS says ECC is enabled
[    6.646863]     Use of the override can cause unknown side effects.
[    6.646870] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    6.646942] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.944818] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.605341] ppdev: user-space parallel port driver
[    8.704522] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.825222] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    8.825250] HDA Intel 0000:01:05.1: setting latency timer to 64
[   10.136170]   alloc irq_desc for 28 on node 0
[   10.136173]   alloc kstat_irqs on node 0
[   10.136183] ATL1E 0000:02:00.0: irq 28 for MSI/MSI-X
[   10.136605] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.175013] usplash:404 freeing invalid memtype ffffffffd0000000-ffffffffd1000000
[   12.076699] [drm] Setting GART location based on new memory map
[   12.091979] [drm] Loading RS780/RS880 CP Microcode
[   12.092644] [drm] Loading RS780/RS880 PFP Microcode
[   12.107752] [drm] Resetting GPU
[   12.107808] [drm] writeback test succeeded in 1 usecs
[   15.053398] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[  330.050019] usb 1-1: new high speed USB device using ehci_hcd and address 4
[  330.231773] usb 1-1: configuration #1 chosen from 1 choice
paint@jean:~$ 











paint@jean:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_via      35456  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
ppdev                   8232  0 
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
psmouse                57124  0 
amd64_edac_mod         26688  0 
i2c_piix4              11728  0 
shpchp                 37756  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
x_tables               25832  1 ip_tables
edac_core              48876  1 amd64_edac_mod
lp                     11908  0 
serio_raw               6596  0 
asus_atk0110            9472  0 
joydev                 13088  0 
parport                40528  2 ppdev,lp
usbhid                 43968  0 
ohci1394               33780  0 
atl1e                  37780  0 
floppy                 65192  0 
ieee1394              100896  1 ohci1394
radeon                684512  1 
ttm                    43056  1 radeon
drm                   193856  3 radeon,ttm
i2c_algo_bit            7076  1 radeon
paint@jean:~$ 













paint@jean:~$ modinfo rt2870sta
filename:       /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        1.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     E5C45807808E721690B4101
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
staging:        Y
vermagic:       2.6.31-14-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
paint@jean:~$

---

### Post by peepingtom on 2009-11-16
Here's a workaround and an explanation.

Do THIS:
```
sudo insmod ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko
```


This will load the kernel module from the folder it was compiled in. 
If it DOES work, congrats, but you'll have to run that line every login unless you do the following. If it DOESN'T work, do the following :D

FIRST delete everything you downloaded onto your desktop. Act like you've never done anything. The follow the instructions here:
EXACTLY. MAKE SURE TO DOWNLOAD THAT NEW ATTACHMENT, DON'T USE THE OLD ONE.
[http://ubuntuforums.org/showpost.php?p=8329886&postcount=16](http://ubuntuforums.org/showpost.php?p=8329886&postcount=16) 
I've run these instructions twice on fresh Ubuntu 9.10 install snapshots in a Virtual Machine, they definitely work.


EXPLANATION:

```
modinfo rt2870sta
filename:       /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rt2870sta.ko
...
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*

```

Check out this line that I have and you don't. My kernel module would detect your USB device (note the 0078 ID), and I compiled it using the same instructions found in post #16.

There are 2 copies of this rt2870 driver on my machine, one in /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless  and another at /lib/modules/2.6.31-14-generic/kernel/drivers/staging. The one in the staging directory is the one that came with Ubuntu, which obviously doesn't work for you. 

So the custom kernel module replaced the default one on my machine after running "make install", but not on yours. I have no idea why it didn't work for you, but delete everything on your desktop and try again with the NEW FILE I UPLOADED (which might make a difference, I eliminated the need to run "make clean" I think).

---

### Post by churro on 2009-11-16
still nothing via original or mod

Question for you peepingtom, Would this work via 9.04 Ubuntu 64 you think?

I got this USB device because I had no net what so ever and the router was too far away and the wires around the house would be seriously in the way.

Windows 7 64bit works with the usb adaptor. Read around and saw there was linux drivers around so I figure it would work too sadly it has not worked out for me because of my version.

Sigh...

Thanks for all your help up til now, Greatly appreciated it and I know you tried hard to make this work for me, virtual stuff and everything.

I would think your almost out of ideas why mine doesn't work just like in your setup.

I sent the $15 even though it didn't work for me.
Your efforts were not of waste, We almost got there!

It's annoying to not have internet.  I use Windows for games and some adobe. I use Linux for everything else. I dare not surf the web with windows unless it's i trust the site alot.

I asked my ISP to do a install around my home and get my modem/router device inside my room instead of the living room, that way I can go via "wire".


Once again, Thank you! :)

---

### Post by peepingtom on 2009-11-16
I would say yes, try 9.04. You'll still have to compile a driver, but it won't have this patch. I'll gladly draw up a guide for you if you want, I basically have one. I've been working on trying to figure out some generic wording so I can make some "boilerplate" support material, I'd like to make a big guide for wireless issues since the transition to 9.10.

I really appreciate the money, your offer was extremely interesting! I've been trying to use these forums more, this kind of stuff gives me better skills!

Your other options are using NDISWrapper to load the drivers for Windows, i've never done that but I'm willing to learn. I have an adapter that uses the same driver, so it'd benefit me too.

Additionally, there is a package called "linux-backports-modules" which ports later driver revisions back to older kernels. It wouldn't help you right now, but it's something to be aware of.

I had my first wireless issue when Karmic came out, it's unpleasant stuff :D

Anyway I am pretty much out of ideas :D But if I think of anything I'll ping this thread. Good luck!

Here: INSTRUCTIONS FOR JAUNTY
Grab the latest RT2870USB driver from here:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

extract its contained folder to your desktop.

Edit
```
gedit ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/config.mk
```
Change
```
HAS_WPA_SUPPLICANT=n
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
```
to
```
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```
Save

Edit
```
gedit ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/usb_main_dev.c
```
Find         ```
{USB_DEVICE(0x1737,0x0070)}, /* Linksys WUSB100 */
```
add below it
```
{USB_DEVICE(0x1737,0x0078)}, /* Linksys WUSB100v2 */
```
Save.


```
cd ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0
sudo make
sudo make install
```

---

### Post by churro on 2009-11-17
:-s ISP Came over and while rewiring my home, They changed the router and inside the router box came a WG111v2 wifi USB adapter.

I'm now on wired... However, I was curious to see if the adapter would work on my pc.  Windows 7 64bit - not working (haven't looked for the driver)

Ubuntu 9.10 64bit (Working)! auto found it and connected to the net.
:popcorn::popcorn::popcorn::popcorn:

First time ever did I get something nice from my ISP ;)

---

### Post by peepingtom on 2009-11-17
That's great news, congrats!
I guess you can relax now :D

I was serious about getting that issue fixed for the next Ubuntu release, that was the kind of experience that sours people. I've contacted the ralink people, I'm going to get that USB device ID added by default hopefully.

If you have any more issues just post on the forums, they're useful sometimes!

I recommend getting a virtualmachine running, they're great for screwing around in when you don't want to break your running system
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
Add the repositories and it'll auto-update.
You can run any OS "in a window" using it.

---

### Post by vprasaj on 2009-11-30
Hi peepingtom.

I have exactly the same problem. Driver is installed.

But in "modinfo rt2870sta" there is no "usb:v1737p**_0078_**d*dc*dsc*dp*ic*isc*ip*". :?

How to make it work in 9.10? (I use linux mint 8 - the same thing.)

I am trying to make it work for some time now. I had problem installing this thing before I downloaded your version.

Do you have any suggestion? I'm willing to try anything.

---

### Post by peepingtom on 2009-11-30
Hi,

when you install the version of the module that you modified to add your USB Device ID, the old module isn't removed. The new one likely wasn't installed to the same place as the old one, and therefore didn't overwrite it. So, you probably have 2 versions of this module, and the modinfo/modprobe commands are loading the original one. So, you can remove the old one.

Post the "file:" line from modinfo rt2870sta, let's see if it's the old one. If it's in a staging directory, it is. I think I just deleted mine to get it working. Otherwise, you can run modprobe to run a module from a specific folder, such as 
```
modprobe /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rt2870sta.ko
``` 
which is where mine was installed to. You can check if the USB dev id is added for a specific module using for example:

```
modinfo /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rt2870sta.ko |grep 78
```

Anyway let me know your level of skill so I know how verbose I need to be :) , i'm really not very good at this stuff myself.

---

### Post by vprasaj on 2009-12-01
Big progress but still not working.
It was just like you said. System was trying to load that old module from that staging directory. I deleted that file, reinstalled the driver and tested. Module is loaded at start up, but not used... :? At least this how I understand this.

```
#dmesg
......
[   19.624817] ppdev: user-space parallel port driver
[   27.952014] eth0: no IPv6 routers present
[   42.776619] UDF-fs: No VRS found
[   42.776622] UDF-fs: No partition found (1)
[   42.837978] ISO 9660 Extensions: Microsoft Joliet Level 3
[   42.866531] ISO 9660 Extensions: RRIP_1991A
[   82.184027] Clocksource tsc unstable (delta = -262872289 ns)
[  282.940195] usb 1-5.3.4: new high speed USB device using ehci_hcd and address 8
[  283.075493] usb 1-5.3.4: configuration #1 chosen from 1 choice
[  283.119070] rtusb init --->
[  283.119403] 
[  283.119404] 
[  283.119406] === pAd = f8483000, size = 471912 ===
[  283.119407] 
[  283.119410] <-- RTMPAllocAdapterBlock, Status=0
[  283.120518] usbcore: registered new interface driver rt2870

#lsusb
......
Bus 001 Device 008: ID 1737:0078 Linksys
......

#modinfo rt2870sta:
filename:       /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rt2870sta.ko
version:        2.2.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     C800221A9FC392167CBBF96
......
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
......

#lsmod:
Module                  Size  ***[COLOR="Red"]Used by[/COLOR]***
rt2870sta             541708  **_[COLOR="Red"]0[/COLOR] _**
......
```

_Is this all right "Used by: 0"?_

And my skill? :-k Somewhere between newbie and below average... maybe ... I don't know. :lolflag: But I'm learning. Kind of...

One more thing. I have ndiswrapper installed. Just the program, not the windows driver. Should I remove it?

And I saw one post somewhere that maybe there is a good thing to add "auto ra0" in "/etc/network/interfaces". I don't know. I'll try this one.

_This thread is for 64bit version, but on Ralink site I saw only one version. I have 32bit system. I think this is not the problem._

What do you think about this? Suggestion(s)?

---

### Post by vprasaj on 2009-12-01
I was just playing a little around. Just a progress. It's not fixed yet.

In linux mint there is one tool called mintwifi. When I run this, my card comes alive and in lsmod shows
```
Module                  Size  **[COLOR="Red"]Used by[/COLOR]**
rt2870sta             541708  [COLOR="Red"]**1**[/COLOR]
```

Before I run mintwifi, "iwconfig" gives me:

```
~ $ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA
```

after I run mintwifi I get:

```
~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Just for info what mintwifi did:

```
~ $ mintwifi 
-------------------------
* I. scanning WIFI PCI devices...
-------------------------
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          
-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr 00:0f:ea:ea:a4:ce  
          inet addr:192.168.1.253  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:feea:a4ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111825 (111.8 KB)  TX bytes:30678 (30.6 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

-------------------------
* V. querying DHCP...
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/YY:YY:YY:YY:YY:YY   *_<---MAC addres (I erased this)_*
Sending on   LPF/ra0/YY:YY:YY:YY:YY:YY   *_<---MAC addres (I erased this)_*
Listening on LPF/eth0/XX:XX:XX:XX:XX:XX   *_<---MAC addres (I erased this)_*
Sending on   LPF/eth0/XX:XX:XX:XX:XX:XX   *_<---MAC addres (I erased this)_*
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST of 192.168.1.253 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.253 from 192.168.1.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 192.168.1.253 -- renewal in 18347 seconds.
-------------------------
* VI. querying nslookup google.com...
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	google.com
Address: 74.125.45.100
Name:	google.com
Address: 74.125.53.100
Name:	google.com
Address: 74.125.67.100
```

It looks like that driver is working. Now what? Now I'm in the dark. :frown:

---

### Post by peepingtom on 2009-12-03
You should remove everything exce[t ```
auto lo
iface lo inet loopback
``` from /etc/network/interfaces
unless you want to configure all your wifi stuff from the command line. I doubt you do :D

Well, then you should be able to use NetworkManager. It's an icon in the "notification area" aka system tray on the "panel" aka taskbar. Right click it, it should list your wifi adapter and networks it can connect to. Let me know if it says "disabled", "unmanaged" or anything like that.

---

### Post by vprasaj on 2009-12-03
I have the same "/etc/network/interfaces" as you. I was just testing that with "auto ra0". It didn't do any difference.

I had some mess after trying to fix this thing. I reinstalled the system and installed the driver rt2870sta.

My wifi adapter is not listed in there.

Module is loaded. "iwconfig" shows the "ra0". But that is all.

Before I reinstalled the system I got it twice in the gnome network manager. It was only, when I disabled LAN card in BIOS and configured it over "network-admin" tool. Wifi was connected to my router but configuration was wrong. "ifconfig" showed me some strange addresses.
After that I was trying to remove network-admin, because I installed it and it was showing me different settings then network manager. After that I get a mess and I simply reinstalled the system (my home partition is safe).

What should I do to get it in network manager? I really don't want to configure this thing over cli. :???:

---

### Post by peepingtom on 2009-12-03
The reason I asked about /etc/network/interfaces is because if there is anything in there other than what I listed, NetworkManager will not manage that interface. 

We've established that you need to compile a new driver to add your USB Device ID, yes?

please follow my tutorial in this thread:
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

it's more concise and has proper debugging instructions. If you need to debug, post in that thread. It's difficult for me to help you when you don't post the information I ask for, or make changes on your own. I'll check the thread in 24 hours if you want some help, i'm unsubscribing from this thread now.

---

### Post by vprasaj on 2009-12-03
Hi peepingtom,

I was trying to to fix some things on my own. Sorry for that.

I followed your guide in that thread but no luck for me. The same thing as I described in [_here_]("http://ubuntuforums.org/showpost.php?p=8418879&postcount=33").

But anyway BIG thanks for your help. :) If it's working with you, it should work here too. When I'll make some progress on this wifi, I'll let you know in your thread with tutorial.

---

