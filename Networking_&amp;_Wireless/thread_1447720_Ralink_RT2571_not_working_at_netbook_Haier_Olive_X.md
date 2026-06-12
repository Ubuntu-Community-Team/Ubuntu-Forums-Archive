---
title: "Ralink RT2571 not working at netbook Haier Olive X107B"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by Irwan on 2010-04-05
[FONT="Verdana"]lsusb
Bus 001 Device 005: ID 148f:2070 Ralink Technology, Corp.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:eb:01:00:fb:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:25 Base address:0x8000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
ppp0      Link encap: Point-to-Point Protocol  
          inet addr:10.13.62.7  P-t-P:10.20.4.12  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1467 errors:16 dropped:0 overruns:0 frame:0
          TX packets:1564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1682968 (1.6 MB)  TX bytes:177367 (177.3 KB)

iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=off   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
ppp0      no wireless extensions.


iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point:Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod
Module                  Size  Used by
ppp_deflate             4732  0 
zlib_deflate           20088  1 ppp_deflate
bsd_comp                5436  0 
ppp_async               8860  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
arc4                    1660  2 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ecb                     2524  2 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_filter          3100  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_timer              22276  2 snd_pcm,snd_seq
joydev                 10240  0 
cfg80211               93052  2 rt2x00lib,mac80211
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
crc_ccitt               1852  2 ppp_async,rt2800usb
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
option                 25216  2 
usbserial              36264  6 option
psmouse                57332  0 
serio_raw               5280  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
r8169                  32064  0 
mii                     5212  1 r8169
i915                  226120  4 
drm                   160032  4 i915
i2c_algo_bit            5760  1 i915
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

lsmod | grep rt2800usb
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
crc_ccitt               1852  2 ppp_async,rt2800usb

dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-21-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 (Ubuntu 2.6.31-21.59-generic)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7c0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7c0000 - 000000003f7ce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7ce000 - 000000003f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3f7c0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 base 03F800000 mask 0FF800000 uncachable
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
[    0.000000]  modified: 0000000000100000 - 000000003f7c0000 (usable)
[    0.000000]  modified: 000000003f7c0000 - 000000003f7ce000 (ACPI data)
[    0.000000]  modified: 000000003f7ce000 - 000000003f800000 (ACPI NVS)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 2f289000 - 2fa0f315
[    0.000000] ACPI: RSDP 000f98a0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3f7c0000 0003C (v01 041409 RSDT1354 20090414 MSFT 00000097)
[    0.000000] ACPI: FACP 3f7c0200 00084 (v02 041409 FACP1354 20090414 MSFT 00000097)
[    0.000000] ACPI: DSDT 3f7c0430 04DC1 (v01  9450F 9450F030 00000030 INTL 20051117)
[    0.000000] ACPI: FACS 3f7ce000 00040
[    0.000000] ACPI: APIC 3f7c0390 0005C (v01 041409 APIC1354 20090414 MSFT 00000097)
[    0.000000] ACPI: MCFG 3f7c03f0 0003C (v01 041409 OEMMCFG  20090414 MSFT 00000097)
[    0.000000] ACPI: OEMB 3f7ce040 00071 (v01 041409 OEMB1354 20090414 MSFT 00000097)
[    0.000000] ACPI: ASF! 3f7c5200 00075 (v32 LEGEND I865PASF 00000001 INTL 20051117)
[    0.000000] ACPI: SSDT 3f7cea00 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ae160]    TEXT DATA BSS ==> [0000100000 - 00008ae160]
[    0.000000]   #4 [002f289000 - 002fa0f315]          RAMDISK ==> [002f289000 - 002fa0f315]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008af000 - 00008b20fc]              BRK ==> [00008af000 - 00008b20fc]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f7c0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f7c0
[    0.000000] On node 0 totalpages: 259919
[    0.000000] free_area_init_node: node 0, pgdat c0788d40, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 256 pages used for memmap
[    0.000000]   HighMem zone: 32450 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf600000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257887
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic root=UUID=1a3bc045-5f90-4160-974a-a80f31aecf10 ro splash quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5200320 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f7c0)
[    0.000000] Memory: 1009484k/1040128k available (4583k kernel code, 29740k reserved, 2142k data, 544k init, 130824k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc081a000   ( 544 kB)
[    0.000000]       .data : 0xc0579d78 - 0xc0791848   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0579d78   (4583 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1600.139 MHz processor.
[    0.001792] Console: colour VGA+ 80x25
[    0.001798] console [tty0] enabled
[    0.001891] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.27 BogoMIPS (lpj=6400556)
[    0.001932] Security Framework initialized
[    0.001967] AppArmor: AppArmor initialized
[    0.001984] Mount-cache hash table entries: 512
[    0.002210] Initializing cgroup subsys ns
[    0.002221] Initializing cgroup subsys cpuacct
[    0.002229] Initializing cgroup subsys memory
[    0.002241] Initializing cgroup subsys devices
[    0.002247] Initializing cgroup subsys freezer
[    0.002252] Initializing cgroup subsys net_cls
[    0.002277] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.002283] CPU: L2 cache: 512K
[    0.002288] CPU: Physical Processor ID: 0
[    0.002292] CPU: Processor Core ID: 0
[    0.002298] mce: CPU supports 5 MCE banks
[    0.002312] CPU0: Thermal monitoring enabled (TM1)
[    0.002320] using mwait in idle threads.
[    0.002331] Performance Counters: Atom events, Intel PMU driver.
[    0.002345] ... version:                 3
[    0.002349] ... bit width:               40
[    0.002354] ... generic counters:        2
[    0.002358] ... value mask:              000000ffffffffff
[    0.002363] ... max period:              000000007fffffff
[    0.002367] ... fixed-purpose counters:  3
[    0.002371] ... counter mask:            0000000700000003
[    0.002380] Checking 'hlt' instruction... OK.
[    0.020014] ACPI: Core revision 20090521
[    0.032469] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074600] CPU0: Genuine Intel(R) CPU N270   @ 1.60GHz stepping 02
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6080.51 BogoMIPS (lpj=12161037)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.161044] CPU1: Genuine Intel(R) CPU N270   @ 1.60GHz stepping 02
[    0.161080] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164039] Brought up 2 CPUs
[    0.164046] Total of 2 processors activated (9280.79 BogoMIPS).
[    0.164109] CPU0 attaching sched-domain:
[    0.164116]  domain 0: span 0-1 level SIBLING
[    0.164121]   groups: 0 1
[    0.164132] CPU1 attaching sched-domain:
[    0.164137]  domain 0: span 0-1 level SIBLING
[    0.164142]   groups: 1 0
[    0.164301] Booting paravirtualized kernel on bare hardware
[    0.164468] regulator: core version 0.5
[    0.164468] Time:  6:47:59  Date: 04/05/10
[    0.164468] NET: Registered protocol family 16
[    0.164468] EISA bus registered
[    0.164468] ACPI: bus type pci registered
[    0.164583] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.164590] PCI: Not using MMCONFIG.
[    0.164879] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[    0.164884] PCI: Using configuration type 1 for base access
[    0.169294] bio: create slab <bio-0> at 0
[    0.169294] ACPI: EC: Look up EC in DSDT
[    0.181639] ACPI: Interpreter enabled
[    0.181656] ACPI: (supports S0 S1 S3 S4 S5)
[    0.181707] ACPI: Using IOAPIC for interrupt routing
[    0.181794] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.191227] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.191235] PCI: updated MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.191241] PCI: Using MMCONFIG for extended config space
[    0.202356] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.202363] ACPI: EC: driver started in poll mode
[    0.202736] ACPI: No dock devices found.
[    0.203043] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.203189] pci 0000:00:02.0: reg 10 32bit mmio: [0xfea80000-0xfeafffff]
[    0.203200] pci 0000:00:02.0: reg 14 io port: [0xdc80-0xdc87]
[    0.203209] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.203219] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfea40000-0xfea7ffff]
[    0.203274] pci 0000:00:02.1: reg 10 32bit mmio: [0xfe980000-0xfe9fffff]
[    0.203402] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfea38000-0xfea3bfff]
[    0.203469] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.203477] pci 0000:00:1b.0: PME# disabled
[    0.203570] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.203578] pci 0000:00:1c.0: PME# disabled
[    0.203658] pci 0000:00:1d.0: reg 20 io port: [0xdc00-0xdc1f]
[    0.203733] pci 0000:00:1d.1: reg 20 io port: [0xd880-0xd89f]
[    0.203808] pci 0000:00:1d.2: reg 20 io port: [0xd800-0xd81f]
[    0.203883] pci 0000:00:1d.3: reg 20 io port: [0xd480-0xd49f]
[    0.203964] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfea37c00-0xfea37fff]
[    0.204055] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.204064] pci 0000:00:1d.7: PME# disabled
[    0.204244] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.204255] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.204264] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.204274] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[    0.204349] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.204361] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.204372] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.204383] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.204395] pci 0000:00:1f.2: reg 20 io port: [0xffa0-0xffaf]
[    0.204433] pci 0000:00:1f.2: PME# supported from D3hot
[    0.204441] pci 0000:00:1f.2: PME# disabled
[    0.204512] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.204616] pci 0000:01:00.0: reg 10 io port: [0xec00-0xecff]
[    0.204645] pci 0000:01:00.0: reg 18 64bit mmio: [0xfdfff000-0xfdffffff]
[    0.204667] pci 0000:01:00.0: reg 20 64bit mmio: [0xfdfe0000-0xfdfeffff]
[    0.204681] pci 0000:01:00.0: reg 30 32bit mmio: [0xfebe0000-0xfebfffff]
[    0.204737] pci 0000:01:00.0: supports D1 D2
[    0.204742] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.204751] pci 0000:01:00.0: PME# disabled
[    0.204837] pci 0000:00:1c.0: bridge io port: [0xe000-0xefff]
[    0.204845] pci 0000:00:1c.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.204857] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.204929] pci 0000:00:1e.0: transparent bridge
[    0.204958] pci_bus 0000:00: on NUMA node 0
[    0.204969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.205231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.219957] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.220176] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.220375] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.220572] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.220768] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.220966] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.221170] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.221371] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.221766] SCSI subsystem initialized
[    0.221851] libata version 3.00 loaded.
[    0.221851] usbcore: registered new interface driver usbfs
[    0.221851] usbcore: registered new interface driver hub
[    0.221851] usbcore: registered new device driver usb
[    0.221851] ACPI: WMI: Mapper loaded
[    0.221851] PCI: Using ACPI for IRQ routing
[    0.232023] Bluetooth: Core ver 2.15
[    0.232067] NET: Registered protocol family 31
[    0.232067] Bluetooth: HCI device and connection manager initialized
[    0.232067] Bluetooth: HCI socket layer initialized
[    0.232067] NetLabel: Initializing
[    0.232067] NetLabel:  domain hash size = 128
[    0.232067] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.232080] NetLabel:  unlabeled traffic allowed by default
[    0.232299] hpet clockevent registered
[    0.232306] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.232316] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.232327] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.252027] pnp: PnP ACPI init
[    0.252068] ACPI: bus type pnp registered
[    0.255519] pnp: PnP ACPI: found 12 devices
[    0.255525] ACPI: ACPI bus type pnp unregistered
[    0.255533] PnPBIOS: Disabled by ACPI PNP
[    0.255558] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.255578] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.255585] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.255592] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.255600] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.255607] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.255615] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved
[    0.255628] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.255635] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.255647] system 00:0a: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.255660] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.255668] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.255675] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.255682] system 00:0b: iomem range 0x100000-0x3f7fffff could not be reserved
[    0.255690] system 00:0b: iomem range 0xfed90000-0xffffffff could not be reserved
[    0.290566] AppArmor: AppArmor Filesystem Enabled
[    0.290621] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.290629] pci 0000:00:1c.0:   IO window: 0xe000-0xefff
[    0.290639] pci 0000:00:1c.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.290648] pci 0000:00:1c.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.290660] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.290664] pci 0000:00:1e.0:   IO window: disabled
[    0.290673] pci 0000:00:1e.0:   MEM window: disabled
[    0.290680] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.290704]   alloc irq_desc for 16 on node -1
[    0.290709]   alloc kstat_irqs on node -1
[    0.290721] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.290731] pci 0000:00:1c.0: setting latency timer to 64
[    0.290744] pci 0000:00:1e.0: setting latency timer to 64
[    0.290753] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.290760] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.290766] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.290772] pci_bus 0000:01: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.290779] pci_bus 0000:01: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.290785] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.290791] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.290865] NET: Registered protocol family 2
[    0.291069] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.291715] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.292721] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.293189] TCP: Hash tables configured (established 131072 bind 65536)
[    0.293196] TCP reno registered
[    0.293425] NET: Registered protocol family 1
[    0.293557] Trying to unpack rootfs image as initramfs...
[    0.490742] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.667163] Freeing initrd memory: 7704k freed
[    0.674799] cpufreq-nforce2: No nForce2 chipset.
[    0.674868] Scanning for low memory corruption every 60 seconds
[    0.675089] audit: initializing netlink socket (disabled)
[    0.675130] type=2000 audit(1270450079.672:1): initialized
[    0.692448] highmem bounce pool size: 64 pages
[    0.692461] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.695711] VFS: Disk quotas dquot_6.5.2
[    0.695840] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.697139] fuse init (API version 7.12)
[    0.697336] msgmni has been set to 1732
[    0.697809] alg: No test for stdrng (krng)
[    0.697843] io scheduler noop registered
[    0.697849] io scheduler anticipatory registered
[    0.697853] io scheduler deadline registered
[    0.697965] io scheduler cfq registered (default)
[    0.697989] pci 0000:00:02.0: Boot video device
[    0.698291]   alloc irq_desc for 24 on node -1
[    0.698297]   alloc kstat_irqs on node -1
[    0.698316] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.698333] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.698508] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.698624] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.701185] ACPI: AC Adapter [AC0] (on-line)
[    0.701309] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.701317] ACPI: Power Button [PWRF]
[    0.701430] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.701437] ACPI: Power Button [PWRB]
[    0.701537] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.703727] ACPI: Lid Switch [LID0]
[    0.704953] ACPI: SSDT 3f7ce190 0023C (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.705826] ACPI: SSDT 3f7ce460 00594 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.706436] Monitor-Mwait will be used to enter C-1 state
[    0.706509] Monitor-Mwait will be used to enter C-2 state
[    0.706569] Monitor-Mwait will be used to enter C-3 state
[    0.706590] Marking TSC unstable due to TSC halts in idle
[    0.706639] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.706698] processor LNXCPU:00: registered as cooling_device0
[    0.707415] ACPI: SSDT 3f7ce0c0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.707954] ACPI: SSDT 3f7ce3d0 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.708752] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.708804] processor LNXCPU:01: registered as cooling_device1
[    0.710655] Switched to high resolution mode on CPU 1
[    0.710661] Switched to high resolution mode on CPU 0
[    0.713703] ACPI Warning: \_TZ_.THZN._PSL: Return Package type mismatch at index 0 - found Processor, expected Reference 20090521 nspredef-946
[    0.713724] ACPI: Expecting a [Reference] package element, found type C
[    0.713729] ACPI: Invalid passive threshold
[    0.715645] thermal LNXTHERM:01: registered as thermal_zone0
[    0.715663] ACPI: Thermal Zone [THZN] (37 C)
[    0.715776] isapnp: Scanning for PnP cards...
[    0.765624] ACPI: Battery Slot [BAT0] (battery present)
[    1.069550] isapnp: No Plug & Play device found
[    1.072129] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.074780] brd: module loaded
[    1.075801] loop: module loaded
[    1.075975] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.076249] ata_piix 0000:00:1f.2: version 2.13
[    1.076280]   alloc irq_desc for 19 on node -1
[    1.076286]   alloc kstat_irqs on node -1
[    1.076299] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.076309] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.076375] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.076539] scsi0 : ata_piix
[    1.076733] scsi1 : ata_piix
[    1.079596] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.079604] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.081636] Fixed MDIO Bus: probed
[    1.081723] PPP generic driver version 2.4.2
[    1.081939] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.081981]   alloc irq_desc for 23 on node -1
[    1.081987]   alloc kstat_irqs on node -1
[    1.082000] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.082028] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.082035] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.082102] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.082114] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.086039] ehci_hcd 0000:00:1d.7: debug port 1
[    1.086050] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.086079] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfea37c00
[    1.100028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.100200] usb usb1: configuration #1 chosen from 1 choice
[    1.100284] hub 1-0:1.0: USB hub found
[    1.100302] hub 1-0:1.0: 8 ports detected
[    1.100432] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.100476] uhci_hcd: USB Universal Host Controller Interface driver
[    1.100546] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.100560] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.100567] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.100657] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.100696] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000dc00
[    1.100874] usb usb2: configuration #1 chosen from 1 choice
[    1.100935] hub 2-0:1.0: USB hub found
[    1.100951] hub 2-0:1.0: 2 ports detected
[    1.101053] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.101066] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.101072] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.101149] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.101199] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d880
[    1.101369] usb usb3: configuration #1 chosen from 1 choice
[    1.101431] hub 3-0:1.0: USB hub found
[    1.101447] hub 3-0:1.0: 2 ports detected
[    1.101545]   alloc irq_desc for 18 on node -1
[    1.101550]   alloc kstat_irqs on node -1
[    1.101562] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.101574] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.101580] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.101651] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.101697] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    1.101862] usb usb4: configuration #1 chosen from 1 choice
[    1.101921] hub 4-0:1.0: USB hub found
[    1.101936] hub 4-0:1.0: 2 ports detected
[    1.102019] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.102031] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.102038] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.102101] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.102147] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d480
[    1.102313] usb usb5: configuration #1 chosen from 1 choice
[    1.102373] hub 5-0:1.0: USB hub found
[    1.102387] hub 5-0:1.0: 2 ports detected
[    1.102578] PNP: PS/2 Controller [PNP0303: PS2K,PNP0f03: PS2M] at 0x60,0x64 irq 1,12
[    1.109297] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.113206] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.113221] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.113231] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.113241] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.113251] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.113415] mice: PS/2 mouse device common for all mice
[    1.113688] rtc_cmos 00:03: RTC can wake from S4
[    1.113760] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.113800] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.114053] device-mapper: uevent: version 1.0.3
[    1.114284] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.114469] device-mapper: multipath: version 1.1.0 loaded
[    1.114476] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.114778] EISA: Probing bus 0 at eisa.0
[    1.114820] EISA: Detected 0 cards.
[    1.115200] cpuidle: using governor ladder
[    1.115452] cpuidle: using governor menu
[    1.116600] TCP cubic registered
[    1.116967] NET: Registered protocol family 10
[    1.117910] lo: Disabled Privacy Extensions
[    1.118617] NET: Registered protocol family 17
[    1.118671] Bluetooth: L2CAP ver 2.13
[    1.118676] Bluetooth: L2CAP socket layer initialized
[    1.118682] Bluetooth: SCO (Voice Link) ver 0.6
[    1.118686] Bluetooth: SCO socket layer initialized
[    1.118778] Bluetooth: RFCOMM TTY layer initialized
[    1.118786] Bluetooth: RFCOMM socket layer initialized
[    1.118790] Bluetooth: RFCOMM ver 1.11
[    1.119572] Using IPI No-Shortcut mode
[    1.119737] PM: Resume from disk failed.
[    1.119764] registered taskstats version 1
[    1.119980]   Magic number: 6:232:771
[    1.120125] rtc_cmos 00:03: setting system clock to 2010-04-05 06:48:00 UTC (1270450080)
[    1.120134] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.120138] EDD information not available.
[    1.135123] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.240382] ata1.00: ATA-8: FUJITSU MHZ2160BH G2, 00000009, max UDMA/100
[    1.240391] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.249408] ata1.00: configured for UDMA/100
[    1.249628] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2160B 0000 PQ: 0 ANSI: 5
[    1.249921] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.250032] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.250166] sd 0:0:0:0: [sda] Write Protect is off
[    1.250173] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.250244] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.250584]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    1.275593] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.275641] Freeing unused kernel memory: 544k freed
[    1.276201] Write protecting the kernel text: 4584k
[    1.276283] Write protecting the kernel read-only data: 1840k
[    1.481921] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.598765] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:18/input/input5
[    1.598877] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[    1.639549] Linux agpgart interface v0.103
[    1.720691] usb 1-4: configuration #1 chosen from 1 choice
[    1.734767] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.735088] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.738214] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.815623] [drm] Initialized drm 1.1.0 20060810
[    1.846689] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.846700] i915 0000:00:02.0: setting latency timer to 64
[    1.867004] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.867043] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.867100] r8169 0000:01:00.0: setting latency timer to 64
[    1.867164]   alloc irq_desc for 25 on node -1
[    1.867171]   alloc kstat_irqs on node -1
[    1.867196] r8169 0000:01:00.0: irq 25 for MSI/MSI-X
[    1.869612] eth0: RTL8102e at 0xf80fe000, 00:eb:01:00:fb:bc, XID 24c00000 IRQ 25
[    1.980075] usb 1-8: new high speed USB device using ehci_hcd and address 5
[    2.130598] usb 1-8: configuration #1 chosen from 1 choice
[    2.170462] [drm] fb0: inteldrmfb frame buffer device
[    2.170482] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.381045] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    2.505081] [drm] LVDS-8: set mode 1024x600 e
[    2.556964] usb 2-2: configuration #1 chosen from 1 choice
[    2.604144] usbcore: registered new interface driver hiddev
[    2.621540] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input6
[    2.621839] generic-usb 0003:1BCF:0007.0001: input,hiddev96,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-2/input0
[    2.621880] usbcore: registered new interface driver usbhid
[    2.621887] usbhid: v2.6:USB HID core driver
[    2.796047] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    2.859040] Console: switching to colour frame buffer device 128x37
[    2.962524] usb 5-1: configuration #1 chosen from 1 choice
[    3.167978] xor: automatically using best checksumming function: pIII_sse
[    3.184018]    pIII_sse  :  4795.000 MB/sec
[    3.184025] xor: using function: pIII_sse (4795.000 MB/sec)
[    3.190475] device-mapper: dm-raid45: initialized v0.2594b
[    3.551747] PM: Starting manual resume from disk
[    3.551758] PM: Resume from partition 8:8
[    3.551762] PM: Checking hibernation image.
[    3.552048] PM: Resume from disk failed.
[    3.592119] EXT4-fs (sda7): barriers enabled
[    3.605977] kjournald2 starting: pid 390, dev sda7:8, commit interval 5 seconds
[    3.606142] EXT4-fs (sda7): delayed allocation enabled
[    3.606152] EXT4-fs: file extents enabled
[    3.610264] EXT4-fs: mballoc enabled
[    3.610298] EXT4-fs (sda7): mounted filesystem with ordered data mode
[    4.295589] type=1505 audit(1270450083.673:2): operation="profile_load" pid=415 name=/sbin/dhclient3
[    4.296224] type=1505 audit(127045:0083.675:3): operation="profile_load" pid=415 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.296554] type=1505 audit(1270450083.675:4): operation="profile_load" pid=415 name=/usr/lib/connman/scripts/dhclient-script
[    4.355461] type=1505 audit(1270450083.731:5): operation="profile_load" pid=416 name=/usr/bin/evince
[    4.364809] type=1505 audit(1270450083.743:6): operation="profile_load" pid=416 name=/usr/bin/evince-previewer
[    4.370518] type=1505 audit(1270450083.747:7): operation="profile_load" pid=416 name=/usr/bin/evince-thumbnailer
[    4.392416] type=1505 audit(1270450083.771:8 ): operation="profile_load" pid=418 name=/usr/lib/cups/backend/cups-pdf
[    4.393167] type=1505 audit(1270450083.771:9): operation="profile_load" pid=418 name=/usr/sbin/cupsd
[   16.217211] Adding 1341388k swap on /dev/sda8.  Priority:-1 extents:1 across:1341388k 
[   16.228801] udev: starting version 147
[   16.275747] lp: driver loaded but no devices found
[   16.390280] EXT4-fs (sda7): internal journal on sda7:8
[   16.418195] intel_rng: FWH not detected
[   16.802204] usbcore: registered new interface driver usbserial
[   16.802253] USB Serial support registered for generic
[   16.802406] usbcore: registered new interface driver usbserial_generic
[   16.802414] usbserial: USB Serial Driver core
[   16.809127] USB Serial support registered for GSM modem (1-port)
[   16.809327] option 5-1:1.0: GSM modem (1-port) converter detected
[   16.809543] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
[   16.809620] option 5-1:1.1: GSM modem (1-port) converter detected
[   16.809787] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
[   16.809862] option 5-1:1.2: GSM modem (1-port) converter detected
[   16.810275] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB2
[   16.810349] usbcore: registered new interface driver option
[   16.810356] option: v0.7.2:USB Driver for GSM modems
[   16.841406] Linux video capture interface: v2.00
[   16.864666] uvcvideo: Found UVC 1.00 device Venus USB2.0 Camera (0ac8:3430)
[   16.915779] input: Venus USB2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input7
[   16.915954] usbcore: registered new interface driver uvcvideo
[   16.915966] USB Video Class driver (v0.1.0)
[   17.040213] cfg80211: Calling CRDA to update world regulatory domain
[   17.082104] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.098969] cfg80211: World regulatory domain updated:
[   17.098981] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.098992] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.099000] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.099008] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.099016] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.099025] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.602660] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.602718] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.615495] phy0: Selected rate control algorithm 'minstrel'
[   17.617758] Registered led device: rt2800usb-phy0::radio
[   17.617821] Registered led device: rt2800usb-phy0::assoc
[   17.617884] Registered led device: rt2800usb-phy0::quality
[   17.619505] usbcore: registered new interface driver rt2800usb
[   17.656976] r8169: eth0: link down
[   17.657578] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.680839] rt2800usb 1-8:1.0: firmware: requesting rt2870.bin
[   17.799949] hda_codec: Unknown model for ALC662 rev1, trying auto-probe from BIOS...
[   17.801025] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   17.819212] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa04000
[   17.907768] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
[   17.993004] input: rt2800usb as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input10
[   18.089208] __ratelimit: 3 callbacks suppressed
[   18.089218] type=1505 audit(1270421297.467:11): operation="profile_replace" pid=1002 name=/sbin/dhclient3
[   18.090077] type=1505 audit(1270421297.467:12): operation="profile_replace" pid=1002 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.090566] type=1505 audit(1270421297.467:13): operation="profile_replace" pid=1002 name=/usr/lib/connman/scripts/dhclient-script
[   18.127546] type=1505 audit(1270421297.503:14): operation="profile_replace" pid=1003 name=/usr/bin/evince
[   18.140759] type=1505 audit(1270421297.519:15): operation="profile_replace" pid=1003 name=/usr/bin/evince-previewer
[   18.176769] type=1505 audit(1270421297.555:16): operation="profile_replace" pid=1003 name=/usr/bin/evince-thumbnailer
[   18.211448] type=1505 audit(1270421297.587:17): operation="profile_replace" pid=1016 name=/usr/lib/cups/backend/cups-pdf
[   18.212514] type=1505 audit(1270421297.591:18 ): operation="profile_replace" pid=1016 name=/usr/sbin/cupsd
[   18.219839] type=1505 audit(1270421297.595:19): operation="profile_replace" pid=1018 name=/usr/sbin/tcpdump
[   18.547247] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.829989] ppdev: user-space parallel port driver
[   19.901012] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.667952] CPU0 attaching NULL sched-domain.
[   20.667965] CPU1 attaching NULL sched-domain.
[   20.681139] CPU0 attaching sched-domain:
[   20.681149]  domain 0: span 0-1 level SIBLING
[   20.681155]   groups: 0 1
[   20.681167] CPU1 attaching sched-domain:
[   20.681172]  domain 0: span 0-1 level SIBLING
[   20.681178]   groups: 1 0
[   20.979330] CPU0 attaching NULL sched-domain.
[   20.979343] CPU1 attaching NULL sched-domain.
[   20.996292] CPU0 attaching sched-domain:
[   20.996303]  domain 0: span 0-1 level SIBLING
[   20.996312]   groups: 0 1
[   20.996327] CPU1 attaching sched-domain:
[   20.996334]  domain 0: span 0-1 level SIBLING
[   20.996342]   groups: 1 0
[   23.101139] CPU0 attaching NULL sched-domain.
[   23.101151] CPU1 attaching NULL sched-domain.
[   23.144116] CPU0 attaching sched-domain:
[   23.144126]  domain 0: span 0-1 level SIBLING
[   23.144133]   groups: 0 1
[   23.144145] CPU1 attaching sched-domain:
[   23.144150]  domain 0: span 0-1 level SIBLING
[   23.144156]   groups: 1 0
[   23.416695] CPU0 attaching NULL sched-domain.
[   23.416711] CPU1 attaching NULL sched-domain.
[   23.429145] CPU0 attaching sched-domain:
[   23.429155]  domain 0: span 0-1 level SIBLING
[   23.429161]   groups: 0 1
[   23.429173] CPU1 attaching sched-domain:
[   23.429178]  domain 0: span 0-1 level SIBLING
[   23.429183]   groups: 1 0
[   25.486473] CPU0 attaching NULL sched-domain.
[   25.486487] CPU1 attaching NULL sched-domain.
[   25.505277] CPU0 attaching sched-domain:
[   25.505292]  domain 0: span 0-1 level SIBLING
[   25.505300]   groups: 0 1
[   25.505317] CPU1 attaching sched-domain:
[   25.505323]  domain 0: span 0-1 level SIBLING
[   25.505331]   groups: 1 0
[   29.263336] CPU0 attaching NULL sched-domain.
[   29.263353] CPU1 attaching NULL sched-domain.
[   29.280486] CPU0 attaching sched-domain:
[   29.280498]  domain 0: span 0-1 level SIBLING
[   29.280507]   groups: 0 1
[   29.280524] CPU1 attaching sched-domain:
[   29.280531]  domain 0: span 0-1 level SIBLING
[   29.280538]   groups: 1 0
[   40.412985] PPP BSD Compression module registered
[   40.456401] PPP Deflate Compression module registered


sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:eb:01:00:fb:bc
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:25 ioport:ec00(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:febe0000-febfffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e3:de:1f:79
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     No scan results
ppp0      Interface doesn't support scanning.


I'm using Ubuntu netbook remix 9.10 with kernel 2.6.31-21-generic i686, please help. thanks
[/FONT]

---

### Post by ba0547 on 2010-05-23
hello,

have the same problem using a gericom hummer 5600 notebook with ralink rt2571 based usb wlan adapter. hope someone can help us making this device work..

bye, harald.

---

