---
title: "Wireless Drops, Crash Report says &quot;Serious Kernel Error&quot;"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by ahamilton9 on 2009-10-27
I have Ubuntu 9.10 installed on kernel 2.6.31-14-generic x86_64 and completely up-to-date as of the time of this posting. 

My wireless card is recognized and does work for about 10 minutes at a time, but then it will drop connection, and I get a Crash Report as network-manager reconnects me. I'm really not sure if this is an issue with my card (it is listed as supported) or with another part of the OS but here is what I've got for details: 

Sager Notebooks/JFL92

Intel Corporation PRO/Wireless 4965 AG or AGN using iwlagn Driver (Default)

Grep Dump: 

0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)

lsmod Dump:

```

Module                  Size  Used by
cryptd                  8008  0 
aes_x86_64              8992  2 
aes_generic            28480  1 aes_x86_64
binfmt_misc            10220  1 
bridge                 56384  0 
stp                     3012  1 bridge
bnep                   15168  2 
ppdev                   8232  0 
snd_hda_codec_si3054     5856  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
arc4                    2144  2 
ecb                     3296  2 
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lp                     11908  0 
iwlagn                124832  0 
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               133248  1 iwlagn
uvcvideo               65260  0 
mac80211              210104  2 iwlagn,iwlcore
snd                    77096  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
lirc_ene0100            9444  0 
iptable_filter          3872  0 
led_class               5256  2 iwlcore,sdhci
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
compal_laptop           4840  0 
parport                40528  2 ppdev,lp
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
joydev                 13088  0 
ip_tables              21200  1 iptable_filter
psmouse                57124  0 
x_tables               25832  1 ip_tables
nvidia              10316904  39 
serio_raw               6596  0 
btusb                  14260  2 
lirc_dev               13928  1 lirc_ene0100
cfg80211              109144  3 iwlagn,iwlcore,mac80211
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
vesafb                  7176  1 
usbhid                 43968  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
tg3                   123748  0 
video                  23612  0 
output                  3680  1 video
intel_agp              32816  0 

```

dmesg Dump (Note, the error can be found in here MULTIPLE TIMES, my system has been on for a little while as of now): 

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=e5759109-c16d-4994-9615-13448fbb41c0 ro vga=792 splash quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfed0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfed0000 - 00000000bfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfee3000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbfed0 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfed0000 (usable)
[    0.000000]  modified: 00000000bfed0000 - 00000000bfee3000 (ACPI NVS)
[    0.000000]  modified: 00000000bfee3000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bfed0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bfed0000 page 4k
[    0.000000] kernel direct mapping tables up to bfed0000 @ 8000-d000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ b000-11000
[    0.000000] RAMDISK: 3786d000 - 37feffd2
[    0.000000] ACPI: RSDP 00000000000f7b40 00024 (v02 MIDERN)
[    0.000000] ACPI: XSDT 00000000bfed8622 0008C (v01 MIDERN MIDERN   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bfedfbd2 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 00000000bfed9b51 0600D (v02 MIDERN MIDERN   06040000 INTL 20061109)
[    0.000000] ACPI: FACS 00000000bfee2fc0 00040
[    0.000000] ACPI: APIC 00000000bfedfcc6 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 00000000bfedfd2e 00038 (v01 MIDERN MIDERN   06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 00000000bfedfd66 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 00000000bfedfda2 00032 (v01 Intel  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR 00000000bfedfdd4 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: SLIC 00000000bfedfdfa 00176 (v01 MIDERN MIDERN   06040000 TBD  00000001)
[    0.000000] ACPI: APIC 00000000bfedff70 00068 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bfedffd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 00000000bfed988c 002C5 (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000bfed8c3a 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000bfed8b94 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000bfed86ae 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000000000c000 - 0000000000010fff]
[    0.000000]   bootmap [0000000000011000 -  0000000000038fff] pages 28
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [003786d000 - 0037feffd2]          RAMDISK ==> [003786d000 - 0037feffd2]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e31a8]              BRK ==> [00019e3000 - 00019e31a8]
[    0.000000]   #6 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000]   #7 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000]
[    0.000000] found SMP MP-table at [ffff8800000f7bc0] f7bc0
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bfed0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048170
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 103 pages reserved
[    0.000000]   DMA zone: 3835 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767752 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bfed0000 - 00000000bfee3000
[    0.000000] PM: Registered nosave memory: 00000000bfee3000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ec00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030147
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=e5759109-c16d-4994-9615-13448fbb41c0 ro vga=792 splash quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4051076k/5242880k available (5313k kernel code, 1050200k absent, 141604k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 2493.735 MHz processor.
[    0.000025] Console: colour dummy device 80x25
[    0.000027] console [tty0] enabled
[    0.010000] allocated 41943040 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4987.47 BogoMIPS (lpj=24937350)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring handled by SMI
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.018760] Setting APIC routing to flat
[    0.019108] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.118666] CPU0: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz stepping 06
[    0.120000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 4987.47 BogoMIPS (lpj=24937372)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.271800] CPU1: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz stepping 06
[    0.271809] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.280023] Brought up 2 CPUs
[    0.280026] Total of 2 processors activated (9974.94 BogoMIPS).
[    0.280077] CPU0 attaching sched-domain:
[    0.280080]  domain 0: span 0-1 level MC
[    0.280082]   groups: 0 1
[    0.280086] CPU1 attaching sched-domain:
[    0.280088]  domain 0: span 0-1 level MC
[    0.280090]   groups: 1 0
[    0.280157] Booting paravirtualized kernel on bare hardware
[    0.280157] regulator: core version 0.5
[    0.280157] Time: 13:17:47  Date: 10/27/09
[    0.280157] NET: Registered protocol family 16
[    0.280187] ACPI: bus type pci registered
[    0.280249] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.280251] PCI: Not using MMCONFIG.
[    0.280252] PCI: Using configuration type 1 for base access
[    0.280923] bio: create slab <bio-0> at 0
[    0.280923] ACPI: EC: Look up EC in DSDT
[    0.282923] ACPI: BIOS _OSI(Linux) query ignored
[    0.283505] ACPI: Interpreter enabled
[    0.283508] ACPI: (supports S0 S3 S4 S5)
[    0.283524] ACPI: Using IOAPIC for interrupt routing
[    0.283558] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.300221] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.306323] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.320068] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.340492] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.340494] ACPI: EC: driver started in interrupt mode
[    0.340779] ACPI: No dock devices found.
[    0.341284] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.341375] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.341378] pci 0000:00:01.0: PME# disabled
[    0.341464] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.341537] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.341612] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf8404800-0xf8404bff]
[    0.341676] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.341682] pci 0000:00:1a.7: PME# disabled
[    0.341733] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf8400000-0xf8403fff]
[    0.341793] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.341797] pci 0000:00:1b.0: PME# disabled
[    0.341880] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.341884] pci 0000:00:1c.0: PME# disabled
[    0.341968] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.341972] pci 0000:00:1c.1: PME# disabled
[    0.342057] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.342061] pci 0000:00:1c.2: PME# disabled
[    0.342147] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.342151] pci 0000:00:1c.3: PME# disabled
[    0.342236] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.342240] pci 0000:00:1c.4: PME# disabled
[    0.342324] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.342329] pci 0000:00:1c.5: PME# disabled
[    0.342390] pci 0000:00:1d.0: reg 20 io port: [0x1840-0x185f]
[    0.342453] pci 0000:00:1d.1: reg 20 io port: [0x1860-0x187f]
[    0.342528] pci 0000:00:1d.2: reg 20 io port: [0x1880-0x189f]
[    0.342600] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf8404c00-0xf8404fff]
[    0.342663] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.342668] pci 0000:00:1d.7: PME# disabled
[    0.342828] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.342831] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.342835] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.342840] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
[    0.342844] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 1640 (mask 007f)
[    0.342892] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.342899] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.342906] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.342913] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.342921] pci 0000:00:1f.1: reg 20 io port: [0x18a0-0x18af]
[    0.342992] pci 0000:00:1f.2: reg 10 io port: [0x18d8-0x18df]
[    0.343000] pci 0000:00:1f.2: reg 14 io port: [0x18cc-0x18cf]
[    0.343007] pci 0000:00:1f.2: reg 18 io port: [0x18d0-0x18d7]
[    0.343014] pci 0000:00:1f.2: reg 1c io port: [0x18c8-0x18cb]
[    0.343022] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.343029] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf8404000-0xf84047ff]
[    0.343071] pci 0000:00:1f.2: PME# supported from D3hot
[    0.343075] pci 0000:00:1f.2: PME# disabled
[    0.343107] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.343131] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.350120] pci 0000:01:00.0: reg 10 32bit mmio: [0xc6000000-0xc6ffffff]
[    0.350158] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.350197] pci 0000:01:00.0: reg 1c 64bit mmio: [0xc4000000-0xc5ffffff]
[    0.350217] pci 0000:01:00.0: reg 24 io port: [0x2000-0x207f]
[    0.350237] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.350422] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.350425] pci 0000:00:01.0: bridge 32bit mmio: [0xc4000000-0xc6ffffff]
[    0.350428] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.350488] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
[    0.350493] pci 0000:00:1c.0: bridge 32bit mmio: [0xbc000000-0xbfffffff]
[    0.350500] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xcc000000-0xcdffffff]
[    0.350709] pci 0000:04:00.0: reg 10 64bit mmio: [0xf0000000-0xf000ffff]
[    0.350935] pci 0000:04:00.0: PME# supported from D3hot D3cold
[    0.350946] pci 0000:04:00.0: PME# disabled
[    0.351045] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.351050] pci 0000:00:1c.1: bridge 32bit mmio: [0xf0000000-0xf3ffffff]
[    0.351057] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xfa000000-0xfbffffff]
[    0.351112] pci 0000:00:1c.2: bridge io port: [0x5000-0x5fff]
[    0.351117] pci 0000:00:1c.2: bridge 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.351124] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xfc000000-0xfdffffff]
[    0.351185] pci 0000:00:1c.3: bridge io port: [0x6000-0x6fff]
[    0.351189] pci 0000:00:1c.3: bridge 32bit mmio: [0xb4000000-0xb7ffffff]
[    0.351196] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xc8000000-0xc9ffffff]
[    0.351393] pci 0000:0c:00.0: reg 10 64bit mmio: [0xf8000000-0xf8001fff]
[    0.351514] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.351527] pci 0000:0c:00.0: PME# disabled
[    0.351619] pci 0000:00:1c.5: bridge 32bit mmio: [0xf8000000-0xf80fffff]
[    0.351676] pci 0000:0e:06.0: reg 10 32bit mmio: [0xf8100000-0xf81007ff]
[    0.351733] pci 0000:0e:06.0: supports D1 D2
[    0.351735] pci 0000:0e:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.351739] pci 0000:0e:06.0: PME# disabled
[    0.351779] pci 0000:0e:06.1: reg 10 32bit mmio: [0xf8100800-0xf81008ff]
[    0.351836] pci 0000:0e:06.1: supports D1 D2
[    0.351837] pci 0000:0e:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.351842] pci 0000:0e:06.1: PME# disabled
[    0.351883] pci 0000:0e:06.2: reg 10 32bit mmio: [0xf8100c00-0xf8100cff]
[    0.351941] pci 0000:0e:06.2: supports D1 D2
[    0.351942] pci 0000:0e:06.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.351947] pci 0000:0e:06.2: PME# disabled
[    0.352005] pci 0000:00:1e.0: transparent bridge
[    0.352012] pci 0000:00:1e.0: bridge 32bit mmio: [0xf8100000-0xf81fffff]
[    0.352064] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.352244] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.352311] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.352371] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.352430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.352488] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.352547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.352606] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.352684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.353035] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.393961] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.394045] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.394128] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.394209] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.394291] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.394373] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.394454] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.394536] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.394667] SCSI subsystem initialized
[    0.394681] libata version 3.00 loaded.
[    0.394681] usbcore: registered new interface driver usbfs
[    0.394681] usbcore: registered new interface driver hub
[    0.394681] usbcore: registered new device driver usb
[    0.394681] ACPI: WMI: Mapper loaded
[    0.394681] PCI: Using ACPI for IRQ routing
[    0.394681] pci 0000:00:1c.0: BAR 14: address space collision on of bridge [0xbc000000-0xbfffffff]
[    0.394681] pci 0000:00:1c.0: BAR 14: can't allocate resource
[    0.394681] pci 0000:00:1c.3: BAR 14: address space collision on of bridge [0xb4000000-0xb7ffffff]
[    0.394681] pci 0000:00:1c.3: BAR 14: can't allocate resource
[    0.420005] Bluetooth: Core ver 2.15
[    0.420018] NET: Registered protocol family 31
[    0.420018] Bluetooth: HCI device and connection manager initialized
[    0.420018] Bluetooth: HCI socket layer initialized
[    0.420018] NetLabel: Initializing
[    0.420018] NetLabel:  domain hash size = 128
[    0.420018] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.420027] NetLabel:  unlabeled traffic allowed by default
[    0.420064] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.420068] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.460005] pnp: PnP ACPI init
[    0.460012] ACPI: bus type pnp registered
[    0.480125] pnp: PnP ACPI: found 11 devices
[    0.480127] ACPI: ACPI bus type pnp unregistered
[    0.480135] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.480137] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.480139] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.480142] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.480144] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.480146] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.480148] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.480151] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.480156] system 00:05: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.480161] system 00:07: ioport range 0x680-0x69f has been reserved
[    0.480163] system 00:07: ioport range 0x800-0x80f has been reserved
[    0.480165] system 00:07: ioport range 0x1000-0x107f has been reserved
[    0.480167] system 00:07: ioport range 0x1180-0x11bf has been reserved
[    0.480169] system 00:07: ioport range 0x1640-0x164f has been reserved
[    0.480171] system 00:07: ioport range 0xfe00-0xfe00 has been reserved
[    0.480174] system 00:07: ioport range 0xff00-0xff7f has been reserved
[    0.484812] AppArmor: AppArmor Filesystem Enabled
[    0.484899] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.484901] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.484904] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.484907] pci 0000:00:01.0:   MEM window: 0xc4000000-0xc6ffffff
[    0.484910] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.484914] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.484917] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.484922] pci 0000:00:1c.0:   MEM window: disabled
[    0.484926] pci 0000:00:1c.0:   PREFETCH window: 0x000000cc000000-0x000000cdffffff
[    0.484934] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.484936] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.484941] pci 0000:00:1c.1:   MEM window: 0xf0000000-0xf3ffffff
[    0.484946] pci 0000:00:1c.1:   PREFETCH window: 0x000000fa000000-0x000000fbffffff
[    0.484953] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.484956] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    0.484961] pci 0000:00:1c.2:   MEM window: 0xf4000000-0xf7ffffff
[    0.484965] pci 0000:00:1c.2:   PREFETCH window: 0x000000fc000000-0x000000fdffffff
[    0.484972] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:08
[    0.484975] pci 0000:00:1c.3:   IO window: 0x6000-0x6fff
[    0.484980] pci 0000:00:1c.3:   MEM window: disabled
[    0.484984] pci 0000:00:1c.3:   PREFETCH window: 0x000000c8000000-0x000000c9ffffff
[    0.484991] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0a
[    0.484992] pci 0000:00:1c.4:   IO window: disabled
[    0.484998] pci 0000:00:1c.4:   MEM window: disabled
[    0.485002] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.485006] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:0c
[    0.485007] pci 0000:00:1c.5:   IO window: disabled
[    0.485013] pci 0000:00:1c.5:   MEM window: 0xf8000000-0xf80fffff
[    0.485017] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.485021] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0e
[    0.485023] pci 0000:00:1e.0:   IO window: disabled
[    0.485028] pci 0000:00:1e.0:   MEM window: 0xf8100000-0xf81fffff
[    0.485032] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.485041]   alloc irq_desc for 16 on node 0
[    0.485043]   alloc kstat_irqs on node 0
[    0.485046] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.485049] pci 0000:00:01.0: setting latency timer to 64
[    0.485056]   alloc irq_desc for 17 on node 0
[    0.485057]   alloc kstat_irqs on node 0
[    0.485060] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.485064] pci 0000:00:1c.0: setting latency timer to 64
[    0.485072] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.485076] pci 0000:00:1c.1: setting latency timer to 64
[    0.485083]   alloc irq_desc for 18 on node 0
[    0.485084]   alloc kstat_irqs on node 0
[    0.485087] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.485091] pci 0000:00:1c.2: setting latency timer to 64
[    0.485098]   alloc irq_desc for 19 on node 0
[    0.485099]   alloc kstat_irqs on node 0
[    0.485101] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.485105] pci 0000:00:1c.3: setting latency timer to 64
[    0.485113] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.485117] pci 0000:00:1c.4: setting latency timer to 64
[    0.485124] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.485128] pci 0000:00:1c.5: setting latency timer to 64
[    0.485136] pci 0000:00:1e.0: setting latency timer to 64
[    0.485139] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.485141] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.485143] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.485144] pci_bus 0000:01: resource 1 mem: [0xc4000000-0xc6ffffff]
[    0.485146] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.485148] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.485150] pci_bus 0000:02: resource 1 mem: [0xbc000000-0xbfffffff]
[    0.485152] pci_bus 0000:02: resource 2 pref mem [0xcc000000-0xcdffffff]
[    0.485154] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    0.485155] pci_bus 0000:04: resource 1 mem: [0xf0000000-0xf3ffffff]
[    0.485157] pci_bus 0000:04: resource 2 pref mem [0xfa000000-0xfbffffff]
[    0.485159] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
[    0.485161] pci_bus 0000:06: resource 1 mem: [0xf4000000-0xf7ffffff]
[    0.485163] pci_bus 0000:06: resource 2 pref mem [0xfc000000-0xfdffffff]
[    0.485164] pci_bus 0000:08: resource 0 io:  [0x6000-0x6fff]
[    0.485166] pci_bus 0000:08: resource 1 mem: [0xb4000000-0xb7ffffff]
[    0.485168] pci_bus 0000:08: resource 2 pref mem [0xc8000000-0xc9ffffff]
[    0.485170] pci_bus 0000:0c: resource 1 mem: [0xf8000000-0xf80fffff]
[    0.485172] pci_bus 0000:0e: resource 1 mem: [0xf8100000-0xf81fffff]
[    0.485174] pci_bus 0000:0e: resource 3 io:  [0x00-0xffff]
[    0.485175] pci_bus 0000:0e: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.485200] NET: Registered protocol family 2
[    0.485328] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.486316] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.490100] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.490669] TCP: Hash tables configured (established 524288 bind 65536)
[    0.490671] TCP reno registered
[    0.490785] NET: Registered protocol family 1
[    0.490858] Trying to unpack rootfs image as initramfs...
[    0.501834] Switched to high resolution mode on CPU 1
[    0.510003] Switched to high resolution mode on CPU 0
[    0.639891] Freeing initrd memory: 7691k freed
[    0.643564] Simple Boot Flag at 0x38 set to 0x1
[    0.643731] Scanning for low memory corruption every 60 seconds
[    0.643872] audit: initializing netlink socket (disabled)
[    0.643889] type=2000 audit(1256649467.640:1): initialized
[    0.652080] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.653240] VFS: Disk quotas dquot_6.5.2
[    0.653287] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.653768] fuse init (API version 7.12)
[    0.653833] msgmni has been set to 7927
[    0.654017] alg: No test for stdrng (krng)
[    0.654030] io scheduler noop registered
[    0.654031] io scheduler anticipatory registered
[    0.654033] io scheduler deadline registered
[    0.654067] io scheduler cfq registered (default)
[    0.654243] pci 0000:01:00.0: Boot video device
[    0.654367]   alloc irq_desc for 24 on node 0
[    0.654369]   alloc kstat_irqs on node 0
[    0.654378] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.654383] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.654525]   alloc irq_desc for 25 on node 0
[    0.654526]   alloc kstat_irqs on node 0
[    0.654535] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.654545] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.654708]   alloc irq_desc for 26 on node 0
[    0.654709]   alloc kstat_irqs on node 0
[    0.654718] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.654728] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.654887]   alloc irq_desc for 27 on node 0
[    0.654889]   alloc kstat_irqs on node 0
[    0.654897] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.654907] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.655068]   alloc irq_desc for 28 on node 0
[    0.655069]   alloc kstat_irqs on node 0
[    0.655077] pcieport-driver 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.655087] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.655249]   alloc irq_desc for 29 on node 0
[    0.655251]   alloc kstat_irqs on node 0
[    0.655259] pcieport-driver 0000:00:1c.4: irq 29 for MSI/MSI-X
[    0.655269] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.655431]   alloc irq_desc for 30 on node 0
[    0.655432]   alloc kstat_irqs on node 0
[    0.655441] pcieport-driver 0000:00:1c.5: irq 30 for MSI/MSI-X
[    0.655451] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.655556] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.655716] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.850054] ACPI: AC Adapter [ACAD] (on-line)
[    0.850108] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.850112] ACPI: Power Button [PWRF]
[    0.850156] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.850189] ACPI: Lid Switch [LID0]
[    0.850225] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.850227] ACPI: Power Button [PWRB]
[    0.850845] ACPI: SSDT 00000000bfed9508 002BC (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.851249] ACPI: SSDT 00000000bfed8e99 005EA (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.853215] Monitor-Mwait will be used to enter C-1 state
[    0.853240] Monitor-Mwait will be used to enter C-2 state
[    0.853256] Monitor-Mwait will be used to enter C-3 state
[    0.853263] Marking TSC unstable due to TSC halts in idle
[    0.853279] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.853298] processor LNXCPU:00: registered as cooling_device0
[    0.853301] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.010199] ACPI: SSDT 00000000bfed97c4 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    1.010454] ACPI: SSDT 00000000bfed9483 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    1.150247] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.150262] processor LNXCPU:01: registered as cooling_device1
[    1.150265] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.331119] Linux agpgart interface v0.103
[    1.331128] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.332119] brd: module loaded
[    1.332481] loop: module loaded
[    1.332548] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.332639] ahci 0000:00:1f.2: version 3.0
[    1.332652] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.332688]   alloc irq_desc for 31 on node 0
[    1.332689]   alloc kstat_irqs on node 0
[    1.332698] ahci 0000:00:1f.2: irq 31 for MSI/MSI-X
[    1.332764] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.332766] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    1.332771] ahci 0000:00:1f.2: setting latency timer to 64
[    1.333074] scsi0 : ahci
[    1.333136] scsi1 : ahci
[    1.333176] scsi2 : ahci
[    1.333256] ata1: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404100 irq 31
[    1.333260] ata2: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404180 irq 31
[    1.333263] ata3: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404200 irq 31
[    1.333651] ACPI: Battery Slot [BAT1] (battery present)
[    1.333727] ata_piix 0000:00:1f.1: version 2.13
[    1.333734] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.333768] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.333842] scsi3 : ata_piix
[    1.333904] scsi4 : ata_piix
[    1.334381] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    1.334383] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    1.335031] Fixed MDIO Bus: probed
[    1.335058] PPP generic driver version 2.4.2
[    1.335122] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.335258] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.335267] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.335270] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.335309] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.339222] ehci_hcd 0000:00:1a.7: debug port 1
[    1.339228] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.339239] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8404800
[    1.370014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.370076] usb usb1: configuration #1 chosen from 1 choice
[    1.370101] hub 1-0:1.0: USB hub found
[    1.370108] hub 1-0:1.0: 4 ports detected
[    1.370183]   alloc irq_desc for 23 on node 0
[    1.370185]   alloc kstat_irqs on node 0
[    1.370189] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.370197] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.370200] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.370230] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.374134] ehci_hcd 0000:00:1d.7: debug port 1
[    1.374139] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.374151] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8404c00
[    1.390012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.390054] usb usb2: configuration #1 chosen from 1 choice
[    1.390076] hub 2-0:1.0: USB hub found
[    1.390083] hub 2-0:1.0: 6 ports detected
[    1.390138] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.390150] uhci_hcd: USB Universal Host Controller Interface driver
[    1.390209] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.390215] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.390218] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.390244] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.390278] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    1.390344] usb usb3: configuration #1 chosen from 1 choice
[    1.390363] hub 3-0:1.0: USB hub found
[    1.390369] hub 3-0:1.0: 2 ports detected
[    1.390441]   alloc irq_desc for 21 on node 0
[    1.390442]   alloc kstat_irqs on node 0
[    1.390445] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.390451] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.390454] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.390481] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.390513] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    1.390577] usb usb4: configuration #1 chosen from 1 choice
[    1.390596] hub 4-0:1.0: USB hub found
[    1.390601] hub 4-0:1.0: 2 ports detected
[    1.390667] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.390673] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.390676] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.390700] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.390727] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    1.390793] usb usb5: configuration #1 chosen from 1 choice
[    1.390812] hub 5-0:1.0: USB hub found
[    1.390817] hub 5-0:1.0: 2 ports detected
[    1.390885] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.390891] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.390894] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.390920] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.390952] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    1.391014] usb usb6: configuration #1 chosen from 1 choice
[    1.391035] hub 6-0:1.0: USB hub found
[    1.391040] hub 6-0:1.0: 2 ports detected
[    1.391105] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.391111] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.391114] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.391141] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.391167] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    1.391231] usb usb7: configuration #1 chosen from 1 choice
[    1.391253] hub 7-0:1.0: USB hub found
[    1.391258] hub 7-0:1.0: 2 ports detected
[    1.391332] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.436762] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.436767] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.436813] mice: PS/2 mouse device common for all mice
[    1.436899] rtc_cmos 00:08: RTC can wake from S4
[    1.436925] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.436955] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.437024] device-mapper: uevent: version 1.0.3
[    1.437082] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.437132] device-mapper: multipath: version 1.1.0 loaded
[    1.437135] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.437296] cpuidle: using governor ladder
[    1.439385] cpuidle: using governor menu
[    1.439688] TCP cubic registered
[    1.439787] NET: Registered protocol family 10
[    1.440162] lo: Disabled Privacy Extensions
[    1.440390] NET: Registered protocol family 17
[    1.440404] Bluetooth: L2CAP ver 2.13
[    1.440406] Bluetooth: L2CAP socket layer initialized
[    1.440409] Bluetooth: SCO (Voice Link) ver 0.6
[    1.440410] Bluetooth: SCO socket layer initialized
[    1.440437] Bluetooth: RFCOMM TTY layer initialized
[    1.440440] Bluetooth: RFCOMM socket layer initialized
[    1.440441] Bluetooth: RFCOMM ver 1.11
[    1.440951] PM: Resume from disk failed.
[    1.440960] registered taskstats version 1
[    1.441056]   Magic number: 13:152:282
[    1.441065] tty tty19: hash matches
[    1.441129] rtc_cmos 00:08: setting system clock to 2009-10-27 13:17:49 UTC (1256649469)
[    1.441131] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.441133] EDD information not available.
[    1.471820] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.530412] ata4.00: ATAPI: SlimtypeDVD A  DS8A1P, CX12, max UDMA/33
[    1.590296] ata4.00: configured for UDMA/33
[    1.680081] ata3: SATA link down (SStatus 0 SControl 300)
[    1.680107] ata2: SATA link down (SStatus 0 SControl 300)
[    1.680133] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.690277] ACPI Warning: \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer 20090521 nspredef-940
[    1.690282] ata1.00: _GTF unexpected object type 0x1
[    1.690291] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.760280] ata1.00: ATA-8: TOSHIBA MK2049GSY, LC000A, max UDMA/100
[    1.760282] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.772745] ata1.00: _GTF unexpected object type 0x1
[    1.790085] ata1.00: configured for UDMA/100
[    1.810217] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2049GS LC00 PQ: 0 ANSI: 5
[    1.810307] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.810335] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.810371] sd 0:0:0:0: [sda] Write Protect is off
[    1.810373] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.810393] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.810489]  sda:
[    1.812732] scsi 3:0:0:0: CD-ROM            Slimtype DVD A  DS8A1P    CX12 PQ: 0 ANSI: 5
[    1.823344] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.823348] Uniform CD-ROM driver Revision: 3.20
[    1.823460] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.823507] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.857660]  sda1 sda2 sda3 <
[    1.860617] usb 1-2: configuration #1 chosen from 1 choice
[    1.890061]  sda5 sda6 >
[    1.920508] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.920544] Freeing unused kernel memory: 660k freed
[    1.920783] Write protecting the kernel read-only data: 7580k
[    2.002515] Clocksource tsc unstable (delta = -206787930 ns)
[    2.025287] tg3.c:v3.99 (April 20, 2009)
[    2.025350] tg3 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.025364] tg3 0000:04:00.0: setting latency timer to 64
[    2.050225] tg3 0000:04:00.0: wake-up capability disabled by ACPI
[    2.050238] tg3 0000:04:00.0: PME# disabled
[    2.064902]   alloc irq_desc for 22 on node 0
[    2.064905]   alloc kstat_irqs on node 0
[    2.064911] ohci1394 0000:0e:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.132143] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8100000-f81007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.502550] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    2.691682] usb 4-1: configuration #1 chosen from 1 choice
[    2.760299] acpi device:05: registered as cooling_device2
[    2.760448] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input5
[    2.760470] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    2.972544] usb 4-2: new full speed USB device using uhci_hcd and address 3
[    3.163651] usb 4-2: configuration #1 chosen from 1 choice
[    3.440200] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    3.452670] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f84cd40021e]
[    3.621302] usb 7-2: configuration #1 chosen from 1 choice
[    3.629815] usbcore: registered new interface driver hiddev
[    3.631497] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input6
[    3.631545] generic-usb 0003:046D:C526.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2/input0
[    3.636357] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.1/input/input7
[    3.636432] generic-usb 0003:046D:C526.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-2/input1
[    3.636443] usbcore: registered new interface driver usbhid
[    3.636445] usbhid: v2.6:USB HID core driver
[    4.151290] eth0: Tigon3 [partno(none) rev b002] (PCI Express) MAC address 00:1b:38:e2:2c:b0
[    4.151293] eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    4.151295] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    4.151296] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.199885] vesafb: framebuffer at 0xc5000000, mapped to 0xffffc90011180000, using 3072k, total 3072k
[    4.199888] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    4.199889] vesafb: scrolling: redraw
[    4.199891] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    4.199922] fb0: VESA VGA frame buffer device
[    4.203684] Console: switching to colour frame buffer device 128x48
[    4.557810] PM: Starting manual resume from disk
[    4.557814] PM: Resume from partition 8:6
[    4.557815] PM: Checking hibernation image.
[    4.557927] PM: Resume from disk failed.
[    4.583364] EXT4-fs (sda5): barriers enabled
[    4.594977] kjournald2 starting: pid 460, dev sda5:8, commit interval 5 seconds
[    4.594985] EXT4-fs (sda5): delayed allocation enabled
[    4.594987] EXT4-fs: file extents enabled
[    4.596592] EXT4-fs: mballoc enabled
[    4.596603] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    5.642636] type=1505 audit(1256649473.699:2): operation="profile_load" pid=483 name=/usr/share/gdm/guest-session/Xsession
[    5.670298] type=1505 audit(1256649473.729:3): operation="profile_load" pid=484 name=/sbin/dhclient3
[    5.670852] type=1505 audit(1256649473.729:4): operation="profile_load" pid=484 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.671143] type=1505 audit(1256649473.729:5): operation="profile_load" pid=484 name=/usr/lib/connman/scripts/dhclient-script
[    5.723200] type=1505 audit(1256649473.779:6): operation="profile_load" pid=485 name=/usr/bin/evince
[    5.731408] type=1505 audit(1256649473.788:7): operation="profile_load" pid=485 name=/usr/bin/evince-previewer
[    5.736282] type=1505 audit(1256649473.788:8): operation="profile_load" pid=485 name=/usr/bin/evince-thumbnailer
[    5.760329] type=1505 audit(1256649473.819:9): operation="profile_load" pid=487 name=/usr/lib/cups/backend/cups-pdf
[    5.760964] type=1505 audit(1256649473.819:10): operation="profile_load" pid=487 name=/usr/sbin/cupsd
[    5.770305] type=1505 audit(1256649473.829:11): operation="profile_load" pid=488 name=/usr/sbin/tcpdump
[    6.930477] Adding 1799240k swap on /dev/sda6.  Priority:-1 extents:1 across:1799240k 
[    7.722551] EXT4-fs (sda5): internal journal on sda5:8
[    7.733823] udev: starting version 147
[    9.286285] lirc_dev: IR Remote Control driver registered, major 61 
[    9.287350] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    9.287450] usbcore: registered new interface driver btusb
[    9.470149] cfg80211: Calling CRDA to update world regulatory domain
[    9.615304] nvidia: module license 'NVIDIA' taints kernel.
[    9.615308] Disabling lock debugging due to kernel taint
[    9.792935] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.869413] nvidia 0000:01:00.0: power state changed by ACPI to D0
[    9.869429] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.869442] nvidia 0000:01:00.0: setting latency timer to 64
[    9.869721] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[    9.874488] Linux video capture interface: v2.00
[    9.878474] compal-laptop: Identified laptop model 'FL92/JFL92'.
[    9.878554] compal-laptop: driver 0.2.6 successfully loaded.
[    9.900501] lirc_dev: lirc_register_driver: sample_rate: 0
[    9.900581] enecir: device seems to be disabled
[    9.900582] enecir: send a mail to lirc-list@lists.sourceforge.net
[    9.900584] enecir: please attach output of acpidump
[    9.911023] sdhci: Secure Digital Host Controller Interface driver
[    9.911025] sdhci: Copyright(c) Pierre Ossman
[    9.912577] sdhci-pci 0000:0e:06.1: SDHCI controller found [1180:0822] (rev 22)
[    9.912594] sdhci-pci 0000:0e:06.1: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    9.913638] sdhci-pci 0000:0e:06.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    9.914666] Registered led device: mmc0::
[    9.915701] mmc0: SDHCI controller on PCI [0000:0e:06.1] using DMA
[   10.043349] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b018)
[   10.045326] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input8
[   10.045389] usbcore: registered new interface driver uvcvideo
[   10.045391] USB Video Class driver (v0.1.0)
[   10.260930] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   10.260932] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   10.263372] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.263402] iwlagn 0000:0c:00.0: setting latency timer to 64
[   10.263468] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   10.315576] iwlagn 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   10.315588] lp: driver loaded but no devices found
[   10.315653]   alloc irq_desc for 32 on node 0
[   10.315655]   alloc kstat_irqs on node 0
[   10.315677] iwlagn 0000:0c:00.0: irq 32 for MSI/MSI-X
[   10.369068] elantech.c: assuming hardware version 1, firmware version 2.4
[   10.401934] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.452830]   alloc irq_desc for 20 on node 0
[   10.452833]   alloc kstat_irqs on node 0
[   10.452838] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   10.452882] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.474711] elantech.c: Synaptics capabilities query result 0x10, 0x02, 0x64.
[   10.640601] cfg80211: World regulatory domain updated:
[   10.640604] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.640606] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.640608] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.640610] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.640612] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.640614] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.866638] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   11.240557] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input10
[   17.963680] tg3 0000:04:00.0: wake-up capability disabled by ACPI
[   17.963692] tg3 0000:04:00.0: PME# disabled
[   17.964153]   alloc irq_desc for 33 on node 0
[   17.964155]   alloc kstat_irqs on node 0
[   17.964184] tg3 0000:04:00.0: irq 33 for MSI/MSI-X
[   18.037857] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.072033] ppdev: user-space parallel port driver
[   18.423006] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   18.433402] iwlagn 0000:0c:00.0: loaded firmware version 228.61.2.24
[   18.453998] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.454000] Bluetooth: BNEP filters: protocol multicast
[   18.458224] Bridge firewalling registered
[   18.672664] Registered led device: iwl-phy0::radio
[   18.672692] Registered led device: iwl-phy0::assoc
[   18.672710] Registered led device: iwl-phy0::RX
[   18.672721] Registered led device: iwl-phy0::TX
[   18.800522] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.229620] cfg80211: Found new beacon on frequency: 5745 MHz (Ch 149) on phy0
[   22.524541] cfg80211: Found new beacon on frequency: 5805 MHz (Ch 161) on phy0
[   42.054960] cfg80211: Found new beacon on frequency: 5765 MHz (Ch 153) on phy0
[   54.309327] wlan0: authenticate with AP 00:22:90:92:f0:62
[   54.313881] wlan0: authenticated
[   54.313884] wlan0: associate with AP 00:22:90:92:f0:62
[   54.321364] wlan0: RX AssocResp from 00:22:90:92:f0:62 (capab=0x31 status=0 aid=103)
[   54.321368] wlan0: associated
[   54.335139] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   54.362989] cfg80211: Calling CRDA for country: US
[   54.364513] cfg80211: Received country IE:
[   54.364515] cfg80211: Regulatory domain: US
[   54.364516] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   54.364518] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   54.364520] cfg80211: CRDA thinks this should applied:
[   54.364521] cfg80211: Regulatory domain: US
[   54.364522] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   54.364524] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   54.364526] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   54.364528] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.364529] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.364531] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   54.364532] cfg80211: We intersect both of these and get:
[   54.364534] cfg80211: Regulatory domain: 98
[   54.364535] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   54.364537] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   54.364540] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[   54.364542] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[   54.364544] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[   54.364546] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[   54.364547] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[   54.364549] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[   54.364551] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[   54.364552] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[   54.364554] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule found in band on Country IE
[   54.364556] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule found in band on Country IE
[   54.364557] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule found in band on Country IE
[   54.364559] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule found in band on Country IE
[   54.364561] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule found in band on Country IE
[   54.364564] cfg80211: Current regulatory domain updated by AP to: US
[   54.364565] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   54.364567] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   55.370789] Intel AES-NI instructions are not detected.
[   55.463024] padlock: VIA PadLock not detected.
[   64.143817] iwlagn 0000:0c:00.0: iwl_tx_agg_start on ra = 00:22:90:92:f0:62 tid = 0
[   65.140043] wlan0: no IPv6 routers present
[   65.530075] CE: hpet increasing min_delta_ns to 15000 nsec
[   77.508037] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   77.522408] iwlagn 0000:0c:00.0: No space for Tx
[   77.522412] iwlagn 0000:0c:00.0: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[   77.522414] iwlagn 0000:0c:00.0: SENSITIVITY_CMD failed
[   77.738989] Registered led device: iwl-phy0::radio
[   77.739018] Registered led device: iwl-phy0::assoc
[   77.739040] Registered led device: iwl-phy0::RX
[   77.739053] Registered led device: iwl-phy0::TX
[   81.506919] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   81.860181] Registered led device: iwl-phy0::radio
[   81.860213] Registered led device: iwl-phy0::assoc
[   81.860227] Registered led device: iwl-phy0::RX
[   81.860242] Registered led device: iwl-phy0::TX
[   95.502964] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   95.521312] iwlagn 0000:0c:00.0: No space for Tx
[   95.521316] iwlagn 0000:0c:00.0: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[   95.521317] iwlagn 0000:0c:00.0: SENSITIVITY_CMD failed
[   95.740280] Registered led device: iwl-phy0::radio
[   95.740307] Registered led device: iwl-phy0::assoc
[   95.740320] Registered led device: iwl-phy0::RX
[   95.740334] Registered led device: iwl-phy0::TX
[  103.236584] wlan0: deauthenticated (Reason: 1)
[  103.236603] iwlagn 0000:0c:00.0: Stopping AGG while state not IWL_AGG_ON
[  103.236611] iwlagn 0000:0c:00.0: queue number out of range: 0, must be 7 to 14
[  103.236616] ------------[ cut here ]------------
[  103.236657] WARNING: at /build/buildd/linux-2.6.31/net/mac80211/agg-tx.c:145 ___ieee80211_stop_tx_ba_session+0x91/0xa0 [mac80211]()
[  103.236664] Hardware name: N/A                                            
[  103.236668] Modules linked in: cryptd aes_x86_64 aes_generic binfmt_misc bridge stp bnep ppdev snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel snd_hda_codec arc4 ecb snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq lp iwlagn snd_timer snd_seq_device iwlcore uvcvideo mac80211 snd sdhci_pci sdhci lirc_ene0100 iptable_filter led_class soundcore snd_page_alloc compal_laptop parport videodev v4l1_compat v4l2_compat_ioctl32 joydev ip_tables psmouse x_tables nvidia(P) serio_raw btusb lirc_dev cfg80211 fbcon tileblit font bitblit softcursor vesafb usbhid ohci1394 ieee1394 tg3 video output intel_agp
[  103.236784] Pid: 884, comm: phy0 Tainted: P           2.6.31-14-generic #48-Ubuntu
[  103.236790] Call Trace:
[  103.236807]  [<ffffffff8105e788>] warn_slowpath_common+0x78/0xb0
[  103.236816]  [<ffffffff8105e7cf>] warn_slowpath_null+0xf/0x20
[  103.236842]  [<ffffffffa0b3d2f1>] ___ieee80211_stop_tx_ba_session+0x91/0xa0 [mac80211]
[  103.236868]  [<ffffffffa0b3d48f>] __ieee80211_stop_tx_ba_session+0x7f/0x90 [mac80211]
[  103.236894]  [<ffffffffa0b3cf3f>] ieee80211_sta_tear_down_BA_sessions+0x1f/0x40 [mac80211]
[  103.236921]  [<ffffffffa0b404b4>] ieee80211_set_disassoc+0xb4/0x290 [mac80211]
[  103.236931]  [<ffffffff8106b933>] ? mod_timer+0x103/0x160
[  103.236957]  [<ffffffffa0b41171>] ieee80211_rx_mgmt_deauth+0x91/0xe0 [mac80211]
[  103.236983]  [<ffffffffa0b43d98>] ieee80211_sta_rx_queued_mgmt+0x98/0xe0 [mac80211]
[  103.237010]  [<ffffffffa0b43e6b>] ieee80211_sta_work+0x8b/0x200 [mac80211]
[  103.237035]  [<ffffffffa0b43de0>] ? ieee80211_sta_work+0x0/0x200 [mac80211]
[  103.237045]  [<ffffffff810737a5>] run_workqueue+0x95/0x170
[  103.237054]  [<ffffffff81073924>] worker_thread+0xa4/0x120
[  103.237063]  [<ffffffff81078b30>] ? autoremove_wake_function+0x0/0x40
[  103.237071]  [<ffffffff81073880>] ? worker_thread+0x0/0x120
[  103.237079]  [<ffffffff81078746>] kthread+0xa6/0xb0
[  103.237087]  [<ffffffff810130ea>] child_rip+0xa/0x20
[  103.237095]  [<ffffffff810786a0>] ? kthread+0x0/0xb0
[  103.237102]  [<ffffffff810130e0>] ? child_rip+0x0/0x20
[  103.237107] ---[ end trace d2aadccbc22e5b63 ]---
[  104.230081] wlan0: direct probe to AP 00:22:90:92:f0:62 try 1
[  104.233281] wlan0 direct probe responded
[  104.233283] wlan0: authenticate with AP 00:22:90:92:f0:62
[  104.237713] wlan0: authenticated
[  104.237714] wlan0: associate with AP 00:22:90:92:f0:62
[  104.242405] wlan0: RX ReassocResp from 00:22:90:92:f0:62 (capab=0x31 status=0 aid=103)
[  104.242407] wlan0: associated
[  109.929462] iwlagn 0000:0c:00.0: iwl_tx_agg_start on ra = 00:22:90:92:f0:62 tid = 0
[  115.641322] CE: hpet increasing min_delta_ns to 22500 nsec
[  158.720660] CE: hpet increasing min_delta_ns to 33750 nsec
[  351.445015] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  351.691066] Registered led device: iwl-phy0::radio
[  351.691108] Registered led device: iwl-phy0::assoc
[  351.691150] Registered led device: iwl-phy0::RX
[  351.691190] Registered led device: iwl-phy0::TX
[  391.442902] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  391.699634] Registered led device: iwl-phy0::radio
[  391.699679] Registered led device: iwl-phy0::assoc
[  391.699718] Registered led device: iwl-phy0::RX
[  391.699755] Registered led device: iwl-phy0::TX
[  413.436005] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  413.478871] iwlagn 0000:0c:00.0: No space for Tx
[  413.478882] iwlagn 0000:0c:00.0: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[  413.478888] iwlagn 0000:0c:00.0: SENSITIVITY_CMD failed
[  413.807466] Registered led device: iwl-phy0::radio
[  413.807480] Registered led device: iwl-phy0::assoc
[  413.807494] Registered led device: iwl-phy0::RX
[  413.807506] Registered led device: iwl-phy0::TX
[  419.435691] CE: hpet increasing min_delta_ns to 50624 nsec
[  476.341038] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  476.953142] Registered led device: iwl-phy0::radio
[  476.953165] Registered led device: iwl-phy0::assoc
[  476.953182] Registered led device: iwl-phy0::RX
[  476.953198] Registered led device: iwl-phy0::TX
[  480.427205] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  480.451874] iwlagn 0000:0c:00.0: No space for Tx
[  480.451884] iwlagn 0000:0c:00.0: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[  480.451890] iwlagn 0000:0c:00.0: SENSITIVITY_CMD failed
[  480.670119] Registered led device: iwl-phy0::radio
[  480.670149] Registered led device: iwl-phy0::assoc
[  480.670179] Registered led device: iwl-phy0::RX
[  480.670223] Registered led device: iwl-phy0::TX
[  494.852509] CE: hpet increasing min_delta_ns to 75936 nsec
[  497.424421] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  497.682508] Registered led device: iwl-phy0::radio
[  497.682551] Registered led device: iwl-phy0::assoc
[  497.682590] Registered led device: iwl-phy0::RX
[  497.682627] Registered led device: iwl-phy0::TX
[  534.625062] wlan0: disassociating by local choice (reason=3)
[  534.625083] iwlagn 0000:0c:00.0: Stopping AGG while state not IWL_AGG_ON
[  534.625091] iwlagn 0000:0c:00.0: queue number out of range: 0, must be 7 to 14
[  534.625097] ------------[ cut here ]------------
[  534.625139] WARNING: at /build/buildd/linux-2.6.31/net/mac80211/agg-tx.c:145 ___ieee80211_stop_tx_ba_session+0x91/0xa0 [mac80211]()
[  534.625146] Hardware name: N/A                                            
[  534.625150] Modules linked in: cryptd aes_x86_64 aes_generic binfmt_misc bridge stp bnep ppdev snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel snd_hda_codec arc4 ecb snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq lp iwlagn snd_timer snd_seq_device iwlcore uvcvideo mac80211 snd sdhci_pci sdhci lirc_ene0100 iptable_filter led_class soundcore snd_page_alloc compal_laptop parport videodev v4l1_compat v4l2_compat_ioctl32 joydev ip_tables psmouse x_tables nvidia(P) serio_raw btusb lirc_dev cfg80211 fbcon tileblit font bitblit softcursor vesafb usbhid ohci1394 ieee1394 tg3 video output intel_agp
[  534.625267] Pid: 1365, comm: wpa_supplicant Tainted: P        W  2.6.31-14-generic #48-Ubuntu
[  534.625273] Call Trace:
[  534.625290]  [<ffffffff8105e788>] warn_slowpath_common+0x78/0xb0
[  534.625299]  [<ffffffff8105e7cf>] warn_slowpath_null+0xf/0x20
[  534.625324]  [<ffffffffa0b3d2f1>] ___ieee80211_stop_tx_ba_session+0x91/0xa0 [mac80211]
[  534.625350]  [<ffffffffa0b3d48f>] __ieee80211_stop_tx_ba_session+0x7f/0x90 [mac80211]
[  534.625377]  [<ffffffffa0b3cf3f>] ieee80211_sta_tear_down_BA_sessions+0x1f/0x40 [mac80211]
[  534.625404]  [<ffffffffa0b404b4>] ieee80211_set_disassoc+0xb4/0x290 [mac80211]
[  534.625415]  [<ffffffff81526b1d>] ? printk+0x3c/0x3f
[  534.625441]  [<ffffffffa0b406e0>] ieee80211_sta_disassociate+0x50/0x60 [mac80211]
[  534.625468]  [<ffffffffa0b48393>] ieee80211_disassoc+0x33/0x50 [mac80211]
[  534.625494]  [<ffffffffa009e563>] cfg80211_wext_siwmlme+0xa3/0xf0 [cfg80211]
[  534.625504]  [<ffffffff8150a1fc>] ioctl_standard_iw_point+0x1bc/0x370
[  534.625525]  [<ffffffffa009e4c0>] ? cfg80211_wext_siwmlme+0x0/0xf0 [cfg80211]
[  534.625533]  [<ffffffff8150a3b0>] ? ioctl_standard_call+0x0/0xd0
[  534.625541]  [<ffffffff81509420>] ? ioctl_private_call+0x0/0xa0
[  534.625549]  [<ffffffff8150a461>] ioctl_standard_call+0xb1/0xd0
[  534.625559]  [<ffffffff814388b0>] ? __dev_get_by_name+0xa0/0xc0
[  534.625567]  [<ffffffff8150a3b0>] ? ioctl_standard_call+0x0/0xd0
[  534.625575]  [<ffffffff815095a9>] wireless_process_ioctl+0xd9/0x160
[  534.625582]  [<ffffffff8150a3b0>] ? ioctl_standard_call+0x0/0xd0
[  534.625590]  [<ffffffff8150969c>] wext_ioctl_dispatch+0x6c/0xb0
[  534.625597]  [<ffffffff81509420>] ? ioctl_private_call+0x0/0xa0
[  534.625605]  [<ffffffff81509811>] wext_handle_ioctl+0x41/0x90
[  534.625613]  [<ffffffff8143994e>] dev_ioctl+0x27e/0x290
[  534.625621]  [<ffffffff81426ac5>] sock_ioctl+0x95/0x280
[  534.625630]  [<ffffffff8112ddfd>] vfs_ioctl+0x1d/0xa0
[  534.625641]  [<ffffffff81220521>] ? security_file_permission+0x11/0x20
[  534.625648]  [<ffffffff8112e429>] do_vfs_ioctl+0x79/0x370
[  534.625657]  [<ffffffff8111f2e1>] ? vfs_read+0x181/0x1a0
[  534.625664]  [<ffffffff8112e7a1>] sys_ioctl+0x81/0xa0
[  534.625674]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
[  534.625680] ---[ end trace d2aadccbc22e5b64 ]---
[  534.683202] wlan0: direct probe to AP 00:22:90:92:f4:22 try 1
[  548.175814] wlan0: authenticate with AP 00:22:90:92:f0:62
[  548.182257] wlan0: authenticated
[  548.182266] wlan0: associate with AP 00:22:90:92:f0:62
[  548.186580] wlan0: RX AssocResp from 00:22:90:92:f0:62 (capab=0x31 status=0 aid=103)
[  548.186587] wlan0: associated
[  555.413199] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  555.444567] iwlagn 0000:0c:00.0: No space for Tx
[  555.444578] iwlagn 0000:0c:00.0: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[  555.444584] iwlagn 0000:0c:00.0: SENSITIVITY_CMD failed
[  555.778563] Registered led device: iwl-phy0::radio
[  555.778580] Registered led device: iwl-phy0::assoc
[  555.778596] Registered led device: iwl-phy0::RX
[  555.778610] Registered led device: iwl-phy0::TX
[  558.413329] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  558.647283] Registered led device: iwl-phy0::radio
[  558.647327] Registered led device: iwl-phy0::assoc
[  558.647415] Registered led device: iwl-phy0::RX
[  558.647453] Registered led device: iwl-phy0::TX
[  577.643277] iwlagn 0000:0c:00.0: iwl_tx_agg_start on ra = 00:22:90:92:f0:62 tid = 0
[  583.409085] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  583.427019] iwlagn 0000:0c:00.0: No space for Tx
[  583.427028] iwlagn 0000:0c:00.0: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[  583.427033] iwlagn 0000:0c:00.0: SENSITIVITY_CMD failed
[  583.661273] Registered led device: iwl-phy0::radio
[  583.661322] Registered led device: iwl-phy0::assoc
[  583.661376] Registered led device: iwl-phy0::RX
[  583.661415] Registered led device: iwl-phy0::TX
[  609.404820] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  609.637867] Registered led device: iwl-phy0::radio
[  609.637917] Registered led device: iwl-phy0::assoc
[  609.637958] Registered led device: iwl-phy0::RX
[  609.637997] Registered led device: iwl-phy0::TX
[  625.133930] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  625.377086] Registered led device: iwl-phy0::radio
[  625.377131] Registered led device: iwl-phy0::assoc
[  625.377171] Registered led device: iwl-phy0::RX
[  625.377207] Registered led device: iwl-phy0::TX
[  635.652387] iwlagn 0000:0c:00.0: Stopping AGG while state not IWL_AGG_ON
[  635.652398] iwlagn 0000:0c:00.0: queue number out of range: 0, must be 7 to 14
[  635.652403] ------------[ cut here ]------------
[  635.652442] WARNING: at /build/buildd/linux-2.6.31/net/mac80211/agg-tx.c:145 ___ieee80211_stop_tx_ba_session+0x91/0xa0 [mac80211]()
[  635.652449] Hardware name: N/A                                            
[  635.652453] Modules linked in: cryptd aes_x86_64 aes_generic binfmt_misc bridge stp bnep ppdev snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel snd_hda_codec arc4 ecb snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq lp iwlagn snd_timer snd_seq_device iwlcore uvcvideo mac80211 snd sdhci_pci sdhci lirc_ene0100 iptable_filter led_class soundcore snd_page_alloc compal_laptop parport videodev v4l1_compat v4l2_compat_ioctl32 joydev ip_tables psmouse x_tables nvidia(P) serio_raw btusb lirc_dev cfg80211 fbcon tileblit font bitblit softcursor vesafb usbhid ohci1394 ieee1394 tg3 video output intel_agp
[  635.652595] Pid: 1365, comm: wpa_supplicant Tainted: P        W  2.6.31-14-generic #48-Ubuntu
[  635.652601] Call Trace:
[  635.652619]  [<ffffffff8105e788>] warn_slowpath_common+0x78/0xb0
[  635.652628]  [<ffffffff8105e7cf>] warn_slowpath_null+0xf/0x20
[  635.652654]  [<ffffffffa0b3d2f1>] ___ieee80211_stop_tx_ba_session+0x91/0xa0 [mac80211]
[  635.652680]  [<ffffffffa0b3d48f>] __ieee80211_stop_tx_ba_session+0x7f/0x90 [mac80211]
[  635.652706]  [<ffffffffa0b3cf3f>] ieee80211_sta_tear_down_BA_sessions+0x1f/0x40 [mac80211]
[  635.652734]  [<ffffffffa0b404b4>] ieee80211_set_disassoc+0xb4/0x290 [mac80211]
[  635.652760]  [<ffffffffa0b44030>] ? ieee80211_sta_set_extra_ie+0x50/0x110 [mac80211]
[  635.652787]  [<ffffffffa0b40a4c>] ieee80211_sta_req_auth+0xac/0xd0 [mac80211]
[  635.652811]  [<ffffffffa0b38fbb>] ieee80211_ioctl_siwgenie+0x7b/0x90 [mac80211]
[  635.652821]  [<ffffffff8150a1fc>] ioctl_standard_iw_point+0x1bc/0x370
[  635.652845]  [<ffffffffa0b38f40>] ? ieee80211_ioctl_siwgenie+0x0/0x90 [mac80211]
[  635.652855]  [<ffffffff81426816>] ? sock_sendmsg+0x106/0x130
[  635.652863]  [<ffffffff8150a3b0>] ? ioctl_standard_call+0x0/0xd0
[  635.652871]  [<ffffffff81509420>] ? ioctl_private_call+0x0/0xa0
[  635.652879]  [<ffffffff8150a461>] ioctl_standard_call+0xb1/0xd0
[  635.652887]  [<ffffffff814388b0>] ? __dev_get_by_name+0xa0/0xc0
[  635.652895]  [<ffffffff8150a3b0>] ? ioctl_standard_call+0x0/0xd0
[  635.652902]  [<ffffffff815095a9>] wireless_process_ioctl+0xd9/0x160
[  635.652910]  [<ffffffff8150a3b0>] ? ioctl_standard_call+0x0/0xd0
[  635.652917]  [<ffffffff8150969c>] wext_ioctl_dispatch+0x6c/0xb0
[  635.652924]  [<ffffffff81509420>] ? ioctl_private_call+0x0/0xa0
[  635.652932]  [<ffffffff81509811>] wext_handle_ioctl+0x41/0x90
[  635.652940]  [<ffffffff8143994e>] dev_ioctl+0x27e/0x290
[  635.652947]  [<ffffffff81426ac5>] sock_ioctl+0x95/0x280
[  635.652956]  [<ffffffff8112ddfd>] vfs_ioctl+0x1d/0xa0
[  635.652963]  [<ffffffff8112e429>] do_vfs_ioctl+0x79/0x370
[  635.652970]  [<ffffffff8112e7a1>] sys_ioctl+0x81/0xa0
[  635.652980]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
[  635.652985] ---[ end trace d2aadccbc22e5b65 ]---
[  637.228547] wlan0: authenticate with AP 00:22:90:92:f4:22
[  637.231584] wlan0: authenticated
[  637.231593] wlan0: associate with AP 00:22:90:92:f4:22
[  637.235558] wlan0: RX ReassocResp from 00:22:90:92:f4:22 (capab=0x431 status=0 aid=26)
[  637.235565] wlan0: associated
[  641.822834] iwlagn 0000:0c:00.0: iwl_tx_agg_start on ra = 00:22:90:92:f4:22 tid = 0
[  777.363713] wlan0: authenticate with AP 00:22:90:92:f0:62
[  777.366500] wlan0: authenticated
[  777.366509] wlan0: associate with AP 00:22:90:92:f0:62
[  777.370254] wlan0: RX ReassocResp from 00:22:90:92:f0:62 (capab=0x431 status=0 aid=110)
[  777.370262] wlan0: associated
[  792.362594] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  792.721309] Registered led device: iwl-phy0::radio
[  792.721353] Registered led device: iwl-phy0::assoc
[  792.721392] Registered led device: iwl-phy0::RX
[  792.721429] Registered led device: iwl-phy0::TX
[  821.357712] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  821.386539] iwlagn 0000:0c:00.0: No space for Tx
[  821.386551] iwlagn 0000:0c:00.0: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[  821.386557] iwlagn 0000:0c:00.0: SENSITIVITY_CMD failed
[  821.609373] Registered led device: iwl-phy0::radio
[  821.609403] Registered led device: iwl-phy0::assoc
[  821.609421] Registered led device: iwl-phy0::RX
[  821.609433] Registered led device: iwl-phy0::TX
[  840.355106] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  840.386359] iwlagn 0000:0c:00.0: No space for Tx
[  840.386364] iwlagn 0000:0c:00.0: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[  840.386366] iwlagn 0000:0c:00.0: SENSITIVITY_CMD failed
[  840.607420] Registered led device: iwl-phy0::radio
[  840.607436] Registered led device: iwl-phy0::assoc
[  840.607449] Registered led device: iwl-phy0::RX
[  840.607461] Registered led device: iwl-phy0::TX
[  877.349322] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  877.588253] Registered led device: iwl-phy0::radio
[  877.588299] Registered led device: iwl-phy0::assoc
[  877.588346] Registered led device: iwl-phy0::RX
[  877.588390] Registered led device: iwl-phy0::TX
[  933.359164] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  933.598383] Registered led device: iwl-phy0::radio
[  933.598428] Registered led device: iwl-phy0::assoc
[  933.598469] Registered led device: iwl-phy0::RX
[  933.598508] Registered led device: iwl-phy0::TX
[  973.137937] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  973.379486] Registered led device: iwl-phy0::radio
[  973.379534] Registered led device: iwl-phy0::assoc
[  973.379579] Registered led device: iwl-phy0::RX
[  973.379625] Registered led device: iwl-phy0::TX
[ 1027.386147] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 1027.631549] Registered led device: iwl-phy0::radio
[ 1027.631580] Registered led device: iwl-phy0::assoc
[ 1027.631601] Registered led device: iwl-phy0::RX
[ 1027.631613] Registered led device: iwl-phy0::TX

```

---

