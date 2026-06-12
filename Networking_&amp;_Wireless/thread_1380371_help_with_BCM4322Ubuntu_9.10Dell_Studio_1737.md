---
title: "help with BCM4322/Ubuntu 9.10/Dell Studio 1737"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by mlchris2 on 2010-01-13
Just a for-warning... I am a total Ubuntu/Linux newb. I am very technical, just spent the last 10 years in the Windows world and figured I'd plunge into Linux. So I did some research and chose Ubuntu 9.10

It installed flawless, except for the wireless. Everything else to my knowledge works.

I connected it to the wired network and ran "Update Manager". I downloaded 150MB worth of updates. I then ran "Hardware Drivers" and I loaded the Broadcom STA wireless driver. But afterwards it states "This driver is activated but not currently in use".

HELP!!!!

So I ran a few commands and here is the output.

```
mark@mark-laptop:~$ lspci

04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
``````
mark@mark-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:19:e9:a4:eb  
          inet addr:192.168.100.106  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fee9:a4eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:205061 (205.0 KB)  TX bytes:26423 (26.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

mark@mark-laptop:~$
``````

mark@mark-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                 10240  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      8964  0 
dell_wmi                2564  0 
sdhci_pci               7100  0 
dell_laptop             8128  0 
sdhci                  17504  1 sdhci_pci
snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  7292  1 dell_laptop
soundcore               7264  1 snd
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
parport                35340  2 ppdev,lp
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
psmouse                56500  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
v4l1_compat            14496  2 uvcvideo,videodev
led_class               4096  1 sdhci
serio_raw               5280  0 
x_tables               16544  1 ip_tables
usbhid                 38208  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
tg3                   109600  0 
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
mark@mark-laptop:~$ 
``````

mark@mark-laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 (Ubuntu 2.6.31-17.54-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bbaa1000 (usable)
[    0.000000]  BIOS-e820: 00000000bbaa1000 - 00000000bbaa7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bbaa7000 - 00000000bbbc2000 (usable)
[    0.000000]  BIOS-e820: 00000000bbbc2000 - 00000000bbc0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bbc0f000 - 00000000bbd09000 (usable)
[    0.000000]  BIOS-e820: 00000000bbd09000 - 00000000bbf0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bbf0f000 - 00000000bbf19000 (usable)
[    0.000000]  BIOS-e820: 00000000bbf19000 - 00000000bbf1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bbf1f000 - 00000000bbf63000 (usable)
[    0.000000]  BIOS-e820: 00000000bbf63000 - 00000000bbf9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bbf9f000 - 00000000bbfe4000 (usable)
[    0.000000]  BIOS-e820: 00000000bbfe4000 - 00000000bbfff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bbfff000 - 00000000bc000000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbc000 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BE000000 mask FFE000000 uncachable
[    0.000000]   4 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   5 base 0BDE00000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009c400 (usable)
[    0.000000]  modified: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bbaa1000 (usable)
[    0.000000]  modified: 00000000bbaa1000 - 00000000bbaa7000 (reserved)
[    0.000000]  modified: 00000000bbaa7000 - 00000000bbbc2000 (usable)
[    0.000000]  modified: 00000000bbbc2000 - 00000000bbc0f000 (reserved)
[    0.000000]  modified: 00000000bbc0f000 - 00000000bbd09000 (usable)
[    0.000000]  modified: 00000000bbd09000 - 00000000bbf0f000 (reserved)
[    0.000000]  modified: 00000000bbf0f000 - 00000000bbf19000 (usable)
[    0.000000]  modified: 00000000bbf19000 - 00000000bbf1f000 (reserved)
[    0.000000]  modified: 00000000bbf1f000 - 00000000bbf63000 (usable)
[    0.000000]  modified: 00000000bbf63000 - 00000000bbf9f000 (ACPI NVS)
[    0.000000]  modified: 00000000bbf9f000 - 00000000bbfe4000 (usable)
[    0.000000]  modified: 00000000bbfe4000 - 00000000bbfff000 (ACPI data)
[    0.000000]  modified: 00000000bbfff000 - 00000000bc000000 (usable)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378a6000 - 37fef743
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff6743
[    0.000000] Move RAMDISK from 00000000378a6000 - 0000000037fef742 to 008ad000 - 00ff6742
[    0.000000] ACPI: RSDP 000f7900 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bbff7b67 0007C (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: FACP bbfe8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bbfe9000 06F6A (v02 Intel  CANTIGA  06040000 INTL 20050624)
[    0.000000] ACPI: FACS bbf9efc0 00040
[    0.000000] ACPI: HPET bbffed16 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bbffed4e 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bbffed8a 00068 (v01 PTLTD       APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bbffedf2 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bbffee1a 00176 (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: OSFR bbffef90 00070 (v01 DELL   DELL     06040000 ASL  00000061)
[    0.000000] ACPI: SSDT bbff7c0b 00039 (v01 BrtRef  DD01BRT 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT bbfe7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bbfe6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bbfe5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2120MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009c400 - 0000100000]    BIOS reserved ==> [000009c400 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac168]              BRK ==> [00008a9000 - 00008ac168]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000ff6743]      NEW RAMDISK ==> [00008ad000 - 0000ff6743]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f79b0] f79b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bc000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[9] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000bbaa1
[    0.000000]     0: 0x000bbaa7 -> 0x000bbbc2
[    0.000000]     0: 0x000bbc0f -> 0x000bbd09
[    0.000000]     0: 0x000bbf0f -> 0x000bbf19
[    0.000000]     0: 0x000bbf1f -> 0x000bbf63
[    0.000000]     0: 0x000bbf9f -> 0x000bbfe4
[    0.000000]     0: 0x000bbfff -> 0x000bc000
[    0.000000] On node 0 totalpages: 769250
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3960 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4241 pages used for memmap
[    0.000000]   HighMem zone: 537787 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bc000000 (gap: bc000000:44000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2790000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 763233
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=92444248-a688-499d-a7c8-c3b6eb1a7442 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 15400960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bc000)
[    0.000000] Memory: 3020612k/3080192k available (4566k kernel code, 55428k reserved, 2142k data, 540k init, 2168112k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575a64 - 0xc078d408   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575a64   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.126 MHz processor.
[    0.001330] Console: colour VGA+ 80x25
[    0.001333] console [tty0] enabled
[    0.001499] hpet clockevent registered
[    0.001504] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.001509] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.25 BogoMIPS (lpj=7980504)
[    0.001526] Security Framework initialized
[    0.001544] AppArmor: AppArmor initialized
[    0.001551] Mount-cache hash table entries: 512
[    0.001668] Initializing cgroup subsys ns
[    0.001672] Initializing cgroup subsys cpuacct
[    0.001676] Initializing cgroup subsys memory
[    0.001682] Initializing cgroup subsys freezer
[    0.001684] Initializing cgroup subsys net_cls
[    0.001697] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001700] CPU: L2 cache: 2048K
[    0.001702] CPU: Physical Processor ID: 0
[    0.001704] CPU: Processor Core ID: 0
[    0.001707] mce: CPU supports 6 MCE banks
[    0.001715] CPU0: Thermal monitoring enabled (TM2)
[    0.001718] using mwait in idle threads.
[    0.001724] Performance Counters: Core2 events, Intel PMU driver.
[    0.001732] ... version:                 2
[    0.001733] ... bit width:               40
[    0.001735] ... generic counters:        2
[    0.001737] ... value mask:              000000ffffffffff
[    0.001739] ... max period:              000000007fffffff
[    0.001740] ... fixed-purpose counters:  3
[    0.001742] ... counter mask:            0000000700000003
[    0.001747] Checking 'hlt' instruction... OK.
[    0.018698] ACPI: Core revision 20090521
[    0.032630] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075726] CPU0: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz stepping 0a
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3989.96 BogoMIPS (lpj=7979925)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.161510] CPU1: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz stepping 0a
[    0.161524] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164021] Brought up 2 CPUs
[    0.164023] Total of 2 processors activated (7980.21 BogoMIPS).
[    0.164070] CPU0 attaching sched-domain:
[    0.164073]  domain 0: span 0-1 level MC
[    0.164075]   groups: 0 1
[    0.164080] CPU1 attaching sched-domain:
[    0.164082]  domain 0: span 0-1 level MC
[    0.164085]   groups: 1 0
[    0.164157] Booting paravirtualized kernel on bare hardware
[    0.164202] regulator: core version 0.5
[    0.164202] Time: 12:46:38  Date: 01/13/10
[    0.164202] NET: Registered protocol family 16
[    0.164202] EISA bus registered
[    0.164209] ACPI: bus type pci registered
[    0.164273] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.164277] PCI: Not using MMCONFIG.
[    0.164640] PCI: PCI BIOS revision 3.00 entry at 0xfde11, last bus=9
[    0.164642] PCI: Using configuration type 1 for base access
[    0.172030] bio: create slab <bio-0> at 0
[    0.176945] ACPI: EC: Look up EC in DSDT
[    0.180658] ACPI: BIOS _OSI(Linux) query ignored
[    0.185904] ACPI: Interpreter enabled
[    0.185909] ACPI: (supports S0 S3 S4 S5)
[    0.185931] ACPI: Using IOAPIC for interrupt routing
[    0.185980] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.186827] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.192470] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.192470] PCI: Using MMCONFIG for extended config space
[    0.200385] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.200387] ACPI: EC: driver started in interrupt mode
[    0.200850] ACPI: No dock devices found.
[    0.201310] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.201404] pci 0000:00:02.0: reg 10 64bit mmio: [0xfc000000-0xfc3fffff]
[    0.201412] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.201417] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.201460] pci 0000:00:02.1: reg 10 64bit mmio: [0xfc400000-0xfc4fffff]
[    0.201585] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
[    0.201677] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
[    0.201785] pci 0000:00:1a.2: reg 20 io port: [0x1860-0x187f]
[    0.201887] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfc904800-0xfc904bff]
[    0.201959] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.201965] pci 0000:00:1a.7: PME# disabled
[    0.202020] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfc700000-0xfc703fff]
[    0.202086] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.202090] pci 0000:00:1b.0: PME# disabled
[    0.202182] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.202186] pci 0000:00:1c.0: PME# disabled
[    0.202279] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.202284] pci 0000:00:1c.1: PME# disabled
[    0.202381] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.202385] pci 0000:00:1c.3: PME# disabled
[    0.202474] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.202479] pci 0000:00:1c.5: PME# disabled
[    0.202563] pci 0000:00:1d.0: reg 20 io port: [0x1880-0x189f]
[    0.202659] pci 0000:00:1d.1: reg 20 io port: [0x18a0-0x18bf]
[    0.202758] pci 0000:00:1d.2: reg 20 io port: [0x18c0-0x18df]
[    0.202860] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfc904c00-0xfc904fff]
[    0.202933] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.202939] pci 0000:00:1d.7: PME# disabled
[    0.203192] pci 0000:00:1f.2: reg 10 io port: [0x1818-0x181f]
[    0.203200] pci 0000:00:1f.2: reg 14 io port: [0x180c-0x180f]
[    0.203209] pci 0000:00:1f.2: reg 18 io port: [0x1810-0x1817]
[    0.203217] pci 0000:00:1f.2: reg 1c io port: [0x1808-0x180b]
[    0.203225] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.203233] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfc904000-0xfc9047ff]
[    0.203285] pci 0000:00:1f.2: PME# supported from D3hot
[    0.203290] pci 0000:00:1f.2: PME# disabled
[    0.203333] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.203354] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.203443] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.203448] pci 0000:00:1c.0: bridge 32bit mmio: [0xf6000000-0xf7ffffff]
[    0.203457] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.204085] pci 0000:04:00.0: reg 10 64bit mmio: [0xf8000000-0xf8003fff]
[    0.204187] pci 0000:04:00.0: supports D1 D2
[    0.204189] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.204196] pci 0000:04:00.0: PME# disabled
[    0.204286] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    0.204291] pci 0000:00:1c.1: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
[    0.204299] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf2000000-0xf3ffffff]
[    0.204353] pci 0000:00:1c.3: bridge io port: [0x4000-0x4fff]
[    0.204358] pci 0000:00:1c.3: bridge 32bit mmio: [0xfa000000-0xfbffffff]
[    0.204367] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf4000000-0xf5ffffff]
[    0.204603] pci 0000:08:00.0: reg 10 64bit mmio: [0xfc500000-0xfc50ffff]
[    0.204705] pci 0000:08:00.0: PME# supported from D3hot D3cold
[    0.204711] pci 0000:08:00.0: PME# disabled
[    0.204791] pci 0000:00:1c.5: bridge 32bit mmio: [0xfc500000-0xfc5fffff]
[    0.204846] pci 0000:09:01.0: reg 10 32bit mmio: [0xfc600000-0xfc6007ff]
[    0.204914] pci 0000:09:01.0: supports D1 D2
[    0.204916] pci 0000:09:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.204922] pci 0000:09:01.0: PME# disabled
[    0.204969] pci 0000:09:01.1: reg 10 32bit mmio: [0xfc600800-0xfc6008ff]
[    0.205038] pci 0000:09:01.1: supports D1 D2
[    0.205040] pci 0000:09:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205045] pci 0000:09:01.1: PME# disabled
[    0.205093] pci 0000:09:01.2: reg 10 32bit mmio: [0xfc600c00-0xfc600cff]
[    0.205162] pci 0000:09:01.2: supports D1 D2
[    0.205164] pci 0000:09:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205170] pci 0000:09:01.2: PME# disabled
[    0.205217] pci 0000:09:01.3: reg 10 32bit mmio: [0xfc601000-0xfc6010ff]
[    0.205285] pci 0000:09:01.3: supports D1 D2
[    0.205287] pci 0000:09:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205293] pci 0000:09:01.3: PME# disabled
[    0.205363] pci 0000:00:1e.0: transparent bridge
[    0.205371] pci 0000:00:1e.0: bridge 32bit mmio: [0xfc600000-0xfc6fffff]
[    0.205411] pci_bus 0000:00: on NUMA node 0
[    0.205416] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.205559] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.205658] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.205733] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.205806] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.205867] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.218418] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.218525] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.218631] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.218735] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.218840] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.218946] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.219050] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.219154] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.219321] SCSI subsystem initialized
[    0.219341] libata version 3.00 loaded.
[    0.219341] usbcore: registered new interface driver usbfs
[    0.219341] usbcore: registered new interface driver hub
[    0.219341] usbcore: registered new device driver usb
[    0.219341] ACPI: WMI: Mapper loaded
[    0.219341] PCI: Using ACPI for IRQ routing
[    0.232007] Bluetooth: Core ver 2.15
[    0.232020] NET: Registered protocol family 31
[    0.232020] Bluetooth: HCI device and connection manager initialized
[    0.232020] Bluetooth: HCI socket layer initialized
[    0.232020] NetLabel: Initializing
[    0.232020] NetLabel:  domain hash size = 128
[    0.232020] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.232032] NetLabel:  unlabeled traffic allowed by default
[    0.232062] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.232067] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.248007] pnp: PnP ACPI init
[    0.248018] ACPI: bus type pnp registered
[    0.253654] pnp: PnP ACPI: found 10 devices
[    0.253657] ACPI: ACPI bus type pnp unregistered
[    0.253660] PnPBIOS: Disabled by ACPI PNP
[    0.253672] system 00:02: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.253679] system 00:04: ioport range 0x400-0x47f has been reserved
[    0.253682] system 00:04: ioport range 0x680-0x69f has been reserved
[    0.253685] system 00:04: ioport range 0x480-0x48f has been reserved
[    0.253688] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.253691] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.253694] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.253697] system 00:04: ioport range 0x1180-0x11ff has been reserved
[    0.253700] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.253702] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.253705] system 00:04: ioport range 0x900-0x97f has been reserved
[    0.253713] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.253716] system 00:09: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.253719] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.253722] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.253724] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.253727] system 00:09: iomem range 0xfeb00000-0xfeb03fff has been reserved
[    0.253730] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.253733] system 00:09: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.253736] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.288393] AppArmor: AppArmor Filesystem Enabled
[    0.288466] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.288470] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.288476] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
[    0.288482] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.288490] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.288494] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.288500] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
[    0.288505] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
[    0.288513] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
[    0.288517] pci 0000:00:1c.3:   IO window: 0x4000-0x4fff
[    0.288523] pci 0000:00:1c.3:   MEM window: 0xfa000000-0xfbffffff
[    0.288528] pci 0000:00:1c.3:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
[    0.288536] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.288538] pci 0000:00:1c.5:   IO window: disabled
[    0.288544] pci 0000:00:1c.5:   MEM window: 0xfc500000-0xfc5fffff
[    0.288549] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.288555] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.288557] pci 0000:00:1e.0:   IO window: disabled
[    0.288563] pci 0000:00:1e.0:   MEM window: 0xfc600000-0xfc6fffff
[    0.288568] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.288582]   alloc irq_desc for 17 on node -1
[    0.288584]   alloc kstat_irqs on node -1
[    0.288589] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.288595] pci 0000:00:1c.0: setting latency timer to 64
[    0.288603]   alloc irq_desc for 16 on node -1
[    0.288605]   alloc kstat_irqs on node -1
[    0.288608] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.288613] pci 0000:00:1c.1: setting latency timer to 64
[    0.288621]   alloc irq_desc for 19 on node -1
[    0.288622]   alloc kstat_irqs on node -1
[    0.288626] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.288631] pci 0000:00:1c.3: setting latency timer to 64
[    0.288640] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.288645] pci 0000:00:1c.5: setting latency timer to 64
[    0.288653] pci 0000:00:1e.0: setting latency timer to 64
[    0.288658] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.288661] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.288663] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.288666] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xf7ffffff]
[    0.288669] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.288671] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.288674] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xf9ffffff]
[    0.288676] pci_bus 0000:04: resource 2 pref mem [0xf2000000-0xf3ffffff]
[    0.288679] pci_bus 0000:06: resource 0 io:  [0x4000-0x4fff]
[    0.288681] pci_bus 0000:06: resource 1 mem: [0xfa000000-0xfbffffff]
[    0.288684] pci_bus 0000:06: resource 2 pref mem [0xf4000000-0xf5ffffff]
[    0.288687] pci_bus 0000:08: resource 1 mem: [0xfc500000-0xfc5fffff]
[    0.288689] pci_bus 0000:09: resource 1 mem: [0xfc600000-0xfc6fffff]
[    0.288692] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.288694] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffff]
[    0.288727] NET: Registered protocol family 2
[    0.288815] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.289121] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.289559] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.289776] TCP: Hash tables configured (established 131072 bind 65536)
[    0.289779] TCP reno registered
[    0.289843] NET: Registered protocol family 1
[    0.289897] Trying to unpack rootfs image as initramfs...
[    0.482641] Freeing initrd memory: 7461k freed
[    0.486388] Simple Boot Flag at 0x36 set to 0x1
[    0.486564] cpufreq-nforce2: No nForce2 chipset.
[    0.486590] Scanning for low memory corruption every 60 seconds
[    0.486690] audit: initializing netlink socket (disabled)
[    0.486706] type=2000 audit(1263386797.483:1): initialized
[    0.495326] highmem bounce pool size: 64 pages
[    0.495331] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.496756] VFS: Disk quotas dquot_6.5.2
[    0.496817] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.497345] fuse init (API version 7.12)
[    0.497427] msgmni has been set to 1681
[    0.497619] alg: No test for stdrng (krng)
[    0.497631] io scheduler noop registered
[    0.497633] io scheduler anticipatory registered
[    0.497635] io scheduler deadline registered
[    0.497674] io scheduler cfq registered (default)
[    0.497686] pci 0000:00:02.0: Boot video device
[    0.497978]   alloc irq_desc for 24 on node -1
[    0.497980]   alloc kstat_irqs on node -1
[    0.497993] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.498004] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.498161]   alloc irq_desc for 25 on node -1
[    0.498163]   alloc kstat_irqs on node -1
[    0.498172] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.498183] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.498339]   alloc irq_desc for 26 on node -1
[    0.498341]   alloc kstat_irqs on node -1
[    0.498350] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.498361] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.498515]   alloc irq_desc for 27 on node -1
[    0.498517]   alloc kstat_irqs on node -1
[    0.498526] pcieport-driver 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.498537] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.498644] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.498789] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.501531] Switched to high resolution mode on CPU 1
[    0.503982] Switched to high resolution mode on CPU 0
[    0.596073] ACPI: AC Adapter [ADP1] (on-line)
[    0.596129] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.596133] ACPI: Power Button [PWRF]
[    0.596195] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.596197] ACPI: Power Button [PWRB]
[    0.596237] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.596240] ACPI: Sleep Button [SLPB]
[    0.596283] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.597166] ACPI: Lid Switch [LID0]
[    0.597963] ACPI: SSDT bbf1aca0 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.598513] ACPI: SSDT bbf19620 00575 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.604763] Monitor-Mwait will be used to enter C-1 state
[    0.604787] Monitor-Mwait will be used to enter C-2 state
[    0.604807] Monitor-Mwait will be used to enter C-3 state
[    0.604814] Marking TSC unstable due to TSC halts in idle
[    0.604832] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.604856] processor LNXCPU:00: registered as cooling_device0
[    0.604860] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.605306] ACPI: SSDT bbf1aa20 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.605733] ACPI: SSDT bbf1af20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.610908] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.610928] processor LNXCPU:01: registered as cooling_device1
[    0.610931] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.618707] thermal LNXTHERM:01: registered as thermal_zone0
[    0.618715] ACPI: Thermal Zone [TZ00] (47 C)
[    0.621125] thermal LNXTHERM:02: registered as thermal_zone1
[    0.621134] ACPI: Thermal Zone [TZ01] (37 C)
[    0.623095] thermal LNXTHERM:03: registered as thermal_zone2
[    0.623102] ACPI: Thermal Zone [TZ02] (0 C)
[    0.623155] isapnp: Scanning for PnP cards...
[    0.711553] ACPI: Battery Slot [BAT0] (battery present)
[    0.977819] isapnp: No Plug & Play device found
[    0.978951] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.980234] brd: module loaded
[    0.980663] loop: module loaded
[    0.980728] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.980797] ahci 0000:00:1f.2: version 3.0
[    0.980810] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.980842]   alloc irq_desc for 28 on node -1
[    0.980844]   alloc kstat_irqs on node -1
[    0.980855] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.980939] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.980942] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pmp pio slum part 
[    0.980948] ahci 0000:00:1f.2: setting latency timer to 64
[    0.981211] scsi0 : ahci
[    0.981296] scsi1 : ahci
[    0.981350] scsi2 : ahci
[    0.981404] scsi3 : ahci
[    0.981460] scsi4 : ahci
[    0.981513] scsi5 : ahci
[    0.981555] ata1: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904100 irq 28
[    0.981559] ata2: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904180 irq 28
[    0.981561] ata3: DUMMY
[    0.981562] ata4: DUMMY
[    0.981565] ata5: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904300 irq 28
[    0.981569] ata6: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904380 irq 28
[    0.982471] Fixed MDIO Bus: probed
[    0.982505] PPP generic driver version 2.4.2
[    0.982586] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.982605] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.982616] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.982619] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.982663] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.986575] ehci_hcd 0000:00:1a.7: debug port 1
[    0.986582] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.986595] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfc904800
[    1.000017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.000086] usb usb1: configuration #1 chosen from 1 choice
[    1.000115] hub 1-0:1.0: USB hub found
[    1.000122] hub 1-0:1.0: 6 ports detected
[    1.000182]   alloc irq_desc for 23 on node -1
[    1.000184]   alloc kstat_irqs on node -1
[    1.000189] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.000198] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.000202] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.000230] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.004155] ehci_hcd 0000:00:1d.7: debug port 1
[    1.004162] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.004176] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc904c00
[    1.020017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.020088] usb usb2: configuration #1 chosen from 1 choice
[    1.020113] hub 2-0:1.0: USB hub found
[    1.020119] hub 2-0:1.0: 6 ports detected
[    1.020177] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.020193] uhci_hcd: USB Universal Host Controller Interface driver
[    1.020214] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.020220] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.020224] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.020256] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.020290] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    1.020368] usb usb3: configuration #1 chosen from 1 choice
[    1.020393] hub 3-0:1.0: USB hub found
[    1.020399] hub 3-0:1.0: 2 ports detected
[    1.020445]   alloc irq_desc for 21 on node -1
[    1.020447]   alloc kstat_irqs on node -1
[    1.020451] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.020457] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.020461] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.020490] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.020524] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    1.020596] usb usb4: configuration #1 chosen from 1 choice
[    1.020621] hub 4-0:1.0: USB hub found
[    1.020627] hub 4-0:1.0: 2 ports detected
[    1.020677] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.020684] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.020687] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.020715] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.020741] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    1.020815] usb usb5: configuration #1 chosen from 1 choice
[    1.020845] hub 5-0:1.0: USB hub found
[    1.020851] hub 5-0:1.0: 2 ports detected
[    1.020899] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.020906] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.020909] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.020937] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.020963] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    1.021035] usb usb6: configuration #1 chosen from 1 choice
[    1.021060] hub 6-0:1.0: USB hub found
[    1.021066] hub 6-0:1.0: 2 ports detected
[    1.021113] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.021120] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.021123] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.021150] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.021177] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    1.021258] usb usb7: configuration #1 chosen from 1 choice
[    1.021282] hub 7-0:1.0: USB hub found
[    1.021288] hub 7-0:1.0: 2 ports detected
[    1.021339]   alloc irq_desc for 18 on node -1
[    1.021341]   alloc kstat_irqs on node -1
[    1.021345] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.021351] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.021354] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.021383] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.021418] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    1.021493] usb usb8: configuration #1 chosen from 1 choice
[    1.021519] hub 8-0:1.0: USB hub found
[    1.021525] hub 8-0:1.0: 2 ports detected
[    1.021617] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.031062] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.031067] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.031121] mice: PS/2 mouse device common for all mice
[    1.031241] rtc_cmos 00:06: RTC can wake from S4
[    1.031272] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.031303] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.031396] device-mapper: uevent: version 1.0.3
[    1.031485] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.031565] device-mapper: multipath: version 1.1.0 loaded
[    1.031567] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.031680] EISA: Probing bus 0 at eisa.0
[    1.031686] Cannot allocate resource for EISA slot 1
[    1.031688] Cannot allocate resource for EISA slot 2
[    1.031690] Cannot allocate resource for EISA slot 3
[    1.031692] Cannot allocate resource for EISA slot 4
[    1.031711] EISA: Detected 0 cards.
[    1.031887] cpuidle: using governor ladder
[    1.032004] cpuidle: using governor menu
[    1.032481] TCP cubic registered
[    1.032628] NET: Registered protocol family 10
[    1.033068] lo: Disabled Privacy Extensions
[    1.033386] NET: Registered protocol family 17
[    1.033401] Bluetooth: L2CAP ver 2.13
[    1.033403] Bluetooth: L2CAP socket layer initialized
[    1.033405] Bluetooth: SCO (Voice Link) ver 0.6
[    1.033407] Bluetooth: SCO socket layer initialized
[    1.033441] Bluetooth: RFCOMM TTY layer initialized
[    1.033443] Bluetooth: RFCOMM socket layer initialized
[    1.033445] Bluetooth: RFCOMM ver 1.11
[    1.038182] Using IPI No-Shortcut mode
[    1.038238] PM: Resume from disk failed.
[    1.038250] registered taskstats version 1
[    1.038360]   Magic number: 10:452:784
[    1.038446] rtc_cmos 00:06: setting system clock to 2010-01-13 12:46:39 UTC (1263386799)
[    1.038449] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.038451] EDD information not available.
[    1.041870] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.308094] ata6: SATA link down (SStatus 0 SControl 300)
[    1.308099] ata5: SATA link down (SStatus 0 SControl 300)
[    1.313043] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    1.451498] usb 1-6: configuration #1 chosen from 1 choice
[    1.464091] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.472067] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.486577] ata2.00: ATAPI: Optiarc DVD+/-RW AD-7640S, HD18, max UDMA/100, ATAPI AN
[    1.491836] ata1.00: ATA-8: WDC WD3200BEVT-75ZCT2, 11.01A11, max UDMA/133
[    1.491841] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.494390] ata1.00: configured for UDMA/133
[    1.500037] Clocksource tsc unstable (delta = -375151420 ns)
[    1.502702] ata2.00: configured for UDMA/100
[    1.509185] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-7 11.0 PQ: 0 ANSI: 5
[    1.509301] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.509342] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.509386] sd 0:0:0:0: [sda] Write Protect is off
[    1.509389] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.509412] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.509536]  sda: sda1 sda2 sda3 <
[    1.522469] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7640S HD18 PQ: 0 ANSI: 5
[    1.527496] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    1.527500] Uniform CD-ROM driver Revision: 3.20
[    1.527615] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.527650] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.538130]  sda5 sda6 >
[    1.554791] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.554819] Freeing unused kernel memory: 540k freed
[    1.555137] Write protecting the kernel text: 4568k
[    1.555191] Write protecting the kernel read-only data: 1836k
[    1.663646] Linux agpgart interface v0.103
[    1.666501] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    1.667241] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    1.670877] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.730925] [drm] Initialized drm 1.1.0 20060810
[    1.763410] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.763415] i915 0000:00:02.0: setting latency timer to 64
[    1.770104] tg3.c:v3.99 (April 20, 2009)
[    1.770277] tg3 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.770290] tg3 0000:08:00.0: setting latency timer to 64
[    1.770949]   alloc irq_desc for 29 on node -1
[    1.770952]   alloc kstat_irqs on node -1
[    1.770960] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[    1.813520] tg3 0000:08:00.0: PME# disabled
[    1.816535] ohci1394 0000:09:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.874062] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fc600000-fc6007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.878430] [drm] i2c_init DPDDC-B
[    1.888225] [drm] i2c_init DPDDC-D
[    1.896083] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    2.008307] i2c-adapter i2c-2: unable to read EDID block.
[    2.008311] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    2.017980] [drm] fb0: inteldrmfb frame buffer device
[    2.019167] ACPI Warning: \_SB_.PCI0.GFX0.DD03._BCL: Return type mismatch - found Integer, expected Package 20090521 nspredef-940
[    2.019174] ACPI: Invalid _BCL data
[    2.019363] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input6
[    2.019390] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.019415] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.073080] usb 6-2: configuration #1 chosen from 1 choice
[    2.282232] usbcore: registered new interface driver hiddev
[    2.296230] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input7
[    2.296302] generic-usb 0003:046D:C045.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2/input0
[    2.296315] usbcore: registered new interface driver usbhid
[    2.296317] usbhid: v2.6:USB HID core driver
[    2.317405] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:22:19:e9:a4:eb
[    2.317409] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.317411] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.317413] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.337297] [drm] LVDS-8: set mode 1440x900 14
[    2.802908] Console: switching to colour frame buffer device 180x56
[    3.148278] PM: Starting manual resume from disk
[    3.148282] PM: Resume from partition 8:6
[    3.148284] PM: Checking hibernation image.
[    3.148465] PM: Resume from disk failed.
[    3.151543] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    3.151549] EXT4-fs (sda5): write access will be enabled during recovery
[    3.161401] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000000000000000]
[    3.176076] EXT4-fs (sda5): barriers enabled
[    4.452056] ACPI: EC: input buffer is not empty, aborting transaction
[    6.239635] kjournald2 starting: pid 423, dev sda5:8, commit interval 5 seconds
[    6.239670] EXT4-fs (sda5): delayed allocation enabled
[    6.239673] EXT4-fs: file extents enabled
[    6.240996] EXT4-fs: mballoc enabled
[    6.241021] EXT4-fs (sda5): orphan cleanup on readonly fs
[    6.241029] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 3452
[    6.241123] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 3154
[    6.241182] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 3150
[    6.241201] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 3145
[    6.241216] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 3141
[    6.241231] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 3137
[    6.241247] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 3135
[    6.241264] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 3124
[    6.241307] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1092
[    6.241323] EXT4-fs (sda5): 9 orphan inodes deleted
[    6.241327] EXT4-fs (sda5): recovery complete
[    6.705404] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    7.213129] type=1505 audit(1263386805.673:2): operation="profile_load" pid=446 name=/usr/share/gdm/guest-session/Xsession
[    7.215701] type=1505 audit(1263386805.673:3): operation="profile_load" pid=447 name=/sbin/dhclient3
[    7.216442] type=1505 audit(1263386805.673:4): operation="profile_load" pid=447 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.216835] type=1505 audit(1263386805.673:5): operation="profile_load" pid=447 name=/usr/lib/connman/scripts/dhclient-script
[    7.266474] type=1505 audit(1263386805.725:6): operation="profile_load" pid=448 name=/usr/bin/evince
[    7.278158] type=1505 audit(1263386805.738:7): operation="profile_load" pid=448 name=/usr/bin/evince-previewer
[    7.285030] type=1505 audit(1263386805.746:8): operation="profile_load" pid=448 name=/usr/bin/evince-thumbnailer
[    7.308826] type=1505 audit(1263386805.766:9): operation="profile_load" pid=450 name=/usr/lib/cups/backend/cups-pdf
[    7.309671] type=1505 audit(1263386805.770:10): operation="profile_load" pid=450 name=/usr/sbin/cupsd
[    7.312330] type=1505 audit(1263386805.770:11): operation="profile_load" pid=451 name=/usr/sbin/tcpdump
[    8.075921] Adding 923696k swap on /dev/sda6.  Priority:-1 extents:1 across:923696k 
[    8.298665] EXT4-fs (sda5): internal journal on sda5:8
[    8.692834] udev: starting version 147
[    9.324075] ACPI: EC: input buffer is not empty, aborting transaction
[   10.154208] Linux video capture interface: v2.00
[   10.196647] uvcvideo: Found UVC 1.00 device Integrated Webcam (05ca:18a0)
[   10.197926] input: Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input8
[   10.197980] usbcore: registered new interface driver uvcvideo
[   10.197983] USB Video Class driver (v0.1.0)
[   10.208540] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.295122] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   10.370044] sdhci: Secure Digital Host Controller Interface driver
[   10.370047] sdhci: Copyright(c) Pierre Ossman
[   10.448130] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 22)
[   10.448148] sdhci-pci 0000:09:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   10.450200] Registered led device: mmc0::
[   10.451226] mmc0: SDHCI controller on PCI [0000:09:01.1] using DMA
[   10.476901] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   10.594009] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
[   10.613990] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[   10.668217] lp: driver loaded but no devices found
[   11.445987]   alloc irq_desc for 22 on node -1
[   11.445990]   alloc kstat_irqs on node -1
[   11.445997] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.446034] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.545955] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
[   11.622349] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   11.622429] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   11.622491] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   14.208076] ACPI: EC: input buffer is not empty, aborting transaction
[   14.273674] tg3 0000:08:00.0: PME# disabled
[   14.274011]   alloc irq_desc for 30 on node -1
[   14.274014]   alloc kstat_irqs on node -1
[   14.274036] tg3 0000:08:00.0: irq 30 for MSI/MSI-X
[   14.420326] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.998230] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   15.998233] tg3: eth0: Flow control is off for TX and off for RX.
[   15.998423] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.873602] i2c-adapter i2c-2: unable to read EDID block.
[   17.873607] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   17.878011] i2c-adapter i2c-2: unable to read EDID block.
[   17.878014] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.061460] i2c-adapter i2c-2: unable to read EDID block.
[   18.061464] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.065879] i2c-adapter i2c-2: unable to read EDID block.
[   18.065882] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.072039] ACPI: EC: input buffer is not empty, aborting transaction
[   23.606409] i2c-adapter i2c-2: unable to read EDID block.
[   23.606414] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.610851] i2c-adapter i2c-2: unable to read EDID block.
[   23.610854] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.747546] i2c-adapter i2c-2: unable to read EDID block.
[   23.747550] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.752068] i2c-adapter i2c-2: unable to read EDID block.
[   23.752071] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.989067] ACPI: EC: input buffer is not empty, aborting transaction
[   23.995294] i2c-adapter i2c-2: unable to read EDID block.
[   23.995298] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.000038] i2c-adapter i2c-2: unable to read EDID block.
[   24.000041] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.416068] CE: hpet increasing min_delta_ns to 15000 nsec
[   26.001032] eth0: no IPv6 routers present
[   28.800047] ACPI: EC: input buffer is not empty, aborting transaction
[   33.660046] ACPI: EC: input buffer is not empty, aborting transaction
[   38.576115] ACPI: EC: input buffer is not empty, aborting transaction
[   42.842510] i2c-adapter i2c-2: unable to read EDID block.
[   42.842514] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   42.846931] i2c-adapter i2c-2: unable to read EDID block.
[   42.846934] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   42.984391] i2c-adapter i2c-2: unable to read EDID block.
[   42.984395] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   42.989050] i2c-adapter i2c-2: unable to read EDID block.
[   42.989053] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   43.127410] i2c-adapter i2c-2: unable to read EDID block.
[   43.127414] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   43.132153] i2c-adapter i2c-2: unable to read EDID block.
[   43.132156] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   43.505533] ACPI: EC: input buffer is not empty, aborting transaction
[   45.675483] i2c-adapter i2c-2: unable to read EDID block.
[   45.675487] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   45.679911] i2c-adapter i2c-2: unable to read EDID block.
[   45.679913] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   48.364040] ACPI: EC: input buffer is not empty, aborting transaction
[   53.228034] ACPI: EC: input buffer is not empty, aborting transaction
[   58.092059] ACPI: EC: input buffer is not empty, aborting transaction
[   62.952111] ACPI: EC: input buffer is not empty, aborting transaction
[   66.268956] ppdev: user-space parallel port driver
[   67.812463] ACPI: EC: input buffer is not empty, aborting transaction
[   72.672114] ACPI: EC: input buffer is not empty, aborting transaction
[   77.536052] ACPI: EC: input buffer is not empty, aborting transaction
[   82.396104] ACPI: EC: input buffer is not empty, aborting transaction
[   87.256085] ACPI: EC: input buffer is not empty, aborting transaction
[   92.116042] ACPI: EC: input buffer is not empty, aborting transaction
[   96.976070] ACPI: EC: input buffer is not empty, aborting transaction
[  101.840093] ACPI: EC: input buffer is not empty, aborting transaction
[  106.700098] ACPI: EC: input buffer is not empty, aborting transaction
[  111.564043] ACPI: EC: input buffer is not empty, aborting transaction
[  116.424098] ACPI: EC: input buffer is not empty, aborting transaction
[  121.284099] ACPI: EC: input buffer is not empty, aborting transaction
[  126.144112] ACPI: EC: input buffer is not empty, aborting transaction
[  131.008066] ACPI: EC: input buffer is not empty, aborting transaction
[  135.868109] ACPI: EC: input buffer is not empty, aborting transaction
[  140.728129] ACPI: EC: input buffer is not empty, aborting transaction
[  145.588119] ACPI: EC: input buffer is not empty, aborting transaction
[  150.448042] ACPI: EC: input buffer is not empty, aborting transaction
[  155.312076] ACPI: EC: input buffer is not empty, aborting transaction
[  160.172124] ACPI: EC: input buffer is not empty, aborting transaction
[  165.032047] ACPI: EC: input buffer is not empty, aborting transaction
[  169.896100] ACPI: EC: input buffer is not empty, aborting transaction
[  174.756049] ACPI: EC: input buffer is not empty, aborting transaction
[  179.616129] ACPI: EC: input buffer is not empty, aborting transaction
[  184.480119] ACPI: EC: input buffer is not empty, aborting transaction
[  189.340106] ACPI: EC: input buffer is not empty, aborting transaction
[  194.200076] ACPI: EC: input buffer is not empty, aborting transaction
[  199.064118] ACPI: EC: input buffer is not empty, aborting transaction
[  203.928121] ACPI: EC: input buffer is not empty, aborting transaction
[  208.789120] ACPI: EC: input buffer is not empty, aborting transaction
[  213.648130] ACPI: EC: input buffer is not empty, aborting transaction
[  218.508132] ACPI: EC: input buffer is not empty, aborting transaction
[  223.380125] ACPI: EC: input buffer is not empty, aborting transaction
[  228.244058] ACPI: EC: input buffer is not empty, aborting transaction
[  233.104088] ACPI: EC: input buffer is not empty, aborting transaction
[  237.964108] ACPI: EC: input buffer is not empty, aborting transaction
[  242.828100] ACPI: EC: input buffer is not empty, aborting transaction
[  247.688116] ACPI: EC: input buffer is not empty, aborting transaction
[  252.548074] ACPI: EC: input buffer is not empty, aborting transaction
[  257.416110] ACPI: EC: input buffer is not empty, aborting transaction
[  262.388126] ACPI: EC: input buffer is not empty, aborting transaction
[  267.264123] ACPI: EC: input buffer is not empty, aborting transaction
[  272.124061] ACPI: EC: input buffer is not empty, aborting transaction
[  276.984126] ACPI: EC: input buffer is not empty, aborting transaction
[  281.944103] ACPI: EC: input buffer is not empty, aborting transaction
[  286.836124] ACPI: EC: input buffer is not empty, aborting transaction
[  291.700134] ACPI: EC: input buffer is not empty, aborting transaction
[  296.648120] ACPI: EC: input buffer is not empty, aborting transaction
[  301.508126] ACPI: EC: input buffer is not empty, aborting transaction
[  306.368072] ACPI: EC: input buffer is not empty, aborting transaction
[  311.232096] ACPI: EC: input buffer is not empty, aborting transaction
[  316.148123] ACPI: EC: input buffer is not empty, aborting transaction
[  321.088124] ACPI: EC: input buffer is not empty, aborting transaction
[  326.048117] ACPI: EC: input buffer is not empty, aborting transaction
[  331.000155] ACPI: EC: input buffer is not empty, aborting transaction
[  335.948119] ACPI: EC: input buffer is not empty, aborting transaction
[  340.888030] ACPI: EC: input buffer is not empty, aborting transaction
[  345.748108] ACPI: EC: input buffer is not empty, aborting transaction
[  350.612122] ACPI: EC: input buffer is not empty, aborting transaction
[  355.472106] ACPI: EC: input buffer is not empty, aborting transaction
[  360.336044] ACPI: EC: input buffer is not empty, aborting transaction
[  365.196093] ACPI: EC: input buffer is not empty, aborting transaction
[  370.056115] ACPI: EC: input buffer is not empty, aborting transaction
[  374.916120] ACPI: EC: input buffer is not empty, aborting transaction
[  379.776122] ACPI: EC: input buffer is not empty, aborting transaction
[  384.640106] ACPI: EC: input buffer is not empty, aborting transaction
[  389.504055] ACPI: EC: input buffer is not empty, aborting transaction
[  394.364074] ACPI: EC: input buffer is not empty, aborting transaction
[  399.228113] ACPI: EC: input buffer is not empty, aborting transaction
[  404.084096] ACPI: EC: input buffer is not empty, aborting transaction
[  408.948098] ACPI: EC: input buffer is not empty, aborting transaction
[  413.808065] ACPI: EC: input buffer is not empty, aborting transaction
[  418.672107] ACPI: EC: input buffer is not empty, aborting transaction
[  423.532118] ACPI: EC: input buffer is not empty, aborting transaction
[  428.392054] ACPI: EC: input buffer is not empty, aborting transaction
[  433.252132] ACPI: EC: input buffer is not empty, aborting transaction
[  438.116112] ACPI: EC: input buffer is not empty, aborting transaction
[  442.976072] ACPI: EC: input buffer is not empty, aborting transaction
[  447.840120] ACPI: EC: input buffer is not empty, aborting transaction
[  452.700125] ACPI: EC: input buffer is not empty, aborting transaction
[  457.560095] ACPI: EC: input buffer is not empty, aborting transaction
[  462.420189] ACPI: EC: input buffer is not empty, aborting transaction
[  467.284062] ACPI: EC: input buffer is not empty, aborting transaction
[  472.144110] ACPI: EC: input buffer is not empty, aborting transaction
[  477.004114] ACPI: EC: input buffer is not empty, aborting transaction
[  481.868089] ACPI: EC: input buffer is not empty, aborting transaction
[  486.728138] ACPI: EC: input buffer is not empty, aborting transaction
[  491.592108] ACPI: EC: input buffer is not empty, aborting transaction
[  496.452122] ACPI: EC: input buffer is not empty, aborting transaction
[  501.316066] ACPI: EC: input buffer is not empty, aborting transaction
[  506.176128] ACPI: EC: input buffer is not empty, aborting transaction
[  511.036111] ACPI: EC: input buffer is not empty, aborting transaction
[  515.896065] ACPI: EC: input buffer is not empty, aborting transaction
[  520.756119] ACPI: EC: input buffer is not empty, aborting transaction
[  525.616119] ACPI: EC: input buffer is not empty, aborting transaction
[  530.488103] ACPI: EC: input buffer is not empty, aborting transaction
[  535.348053] ACPI: EC: input buffer is not empty, aborting transaction
[  540.208128] ACPI: EC: input buffer is not empty, aborting transaction
[  545.068115] ACPI: EC: input buffer is not empty, aborting transaction
[  549.928083] ACPI: EC: input buffer is not empty, aborting transaction
[  554.788083] ACPI: EC: input buffer is not empty, aborting transaction
[  559.652127] ACPI: EC: input buffer is not empty, aborting transaction
[  564.516098] ACPI: EC: input buffer is not empty, aborting transaction
[  569.376107] ACPI: EC: input buffer is not empty, aborting transaction
[  574.236092] ACPI: EC: input buffer is not empty, aborting transaction
[  579.096121] ACPI: EC: input buffer is not empty, aborting transaction
[  583.956087] ACPI: EC: input buffer is not empty, aborting transaction
[  588.820059] ACPI: EC: input buffer is not empty, aborting transaction
[  593.684129] ACPI: EC: input buffer is not empty, aborting transaction
[  598.544104] ACPI: EC: input buffer is not empty, aborting transaction
[  603.404083] ACPI: EC: input buffer is not empty, aborting transaction
[  608.264104] ACPI: EC: input buffer is not empty, aborting transaction
[  613.124137] ACPI: EC: input buffer is not empty, aborting transaction
[  617.988106] ACPI: EC: input buffer is not empty, aborting transaction
[  622.852132] ACPI: EC: input buffer is not empty, aborting transaction
[  627.712084] ACPI: EC: input buffer is not empty, aborting transaction
[  632.572114] ACPI: EC: input buffer is not empty, aborting transaction
[  637.436128] ACPI: EC: input buffer is not empty, aborting transaction
[  642.296102] ACPI: EC: input buffer is not empty, aborting transaction
[  647.160147] ACPI: EC: input buffer is not empty, aborting transaction
[  652.020129] ACPI: EC: input buffer is not empty, aborting transaction
[  656.880125] ACPI: EC: input buffer is not empty, aborting transaction
[  661.740113] ACPI: EC: input buffer is not empty, aborting transaction
[  666.600126] ACPI: EC: input buffer is not empty, aborting transaction
[  671.460120] ACPI: EC: input buffer is not empty, aborting transaction
[  676.324070] ACPI: EC: input buffer is not empty, aborting transaction
[  681.188122] ACPI: EC: input buffer is not empty, aborting transaction
[  686.048122] ACPI: EC: input buffer is not empty, aborting transaction
[  690.908099] ACPI: EC: input buffer is not empty, aborting transaction
[  695.772111] ACPI: EC: input buffer is not empty, aborting transaction
[  700.632122] ACPI: EC: input buffer is not empty, aborting transaction
[  705.492120] ACPI: EC: input buffer is not empty, aborting transaction
[  710.356082] ACPI: EC: input buffer is not empty, aborting transaction
[  715.216097] ACPI: EC: input buffer is not empty, aborting transaction
[  720.080140] ACPI: EC: input buffer is not empty, aborting transaction
[  724.940108] ACPI: EC: input buffer is not empty, aborting transaction
[  729.800127] ACPI: EC: input buffer is not empty, aborting transaction
[  734.660053] ACPI: EC: input buffer is not empty, aborting transaction
[  739.524126] ACPI: EC: input buffer is not empty, aborting transaction
[  744.384103] ACPI: EC: input buffer is not empty, aborting transaction
[  749.244115] ACPI: EC: input buffer is not empty, aborting transaction
[  754.104118] ACPI: EC: input buffer is not empty, aborting transaction
[  758.964129] ACPI: EC: input buffer is not empty, aborting transaction
[  763.828096] ACPI: EC: input buffer is not empty, aborting transaction
[  768.696130] ACPI: EC: input buffer is not empty, aborting transaction
[  773.556077] ACPI: EC: input buffer is not empty, aborting transaction
[  778.416119] ACPI: EC: input buffer is not empty, aborting transaction
[  783.276115] ACPI: EC: input buffer is not empty, aborting transaction
[  788.136092] ACPI: EC: input buffer is not empty, aborting transaction
[  793.000139] ACPI: EC: input buffer is not empty, aborting transaction
[  797.860071] ACPI: EC: input buffer is not empty, aborting transaction
[  802.720123] ACPI: EC: input buffer is not empty, aborting transaction
[  807.584097] ACPI: EC: input buffer is not empty, aborting transaction
[  812.444123] ACPI: EC: input buffer is not empty, aborting transaction
[  817.304052] ACPI: EC: input buffer is not empty, aborting transaction
[  822.168113] ACPI: EC: input buffer is not empty, aborting transaction
[  827.028112] ACPI: EC: input buffer is not empty, aborting transaction
[  831.892053] ACPI: EC: input buffer is not empty, aborting transaction
[  836.752123] ACPI: EC: input buffer is not empty, aborting transaction
[  841.612116] ACPI: EC: input buffer is not empty, aborting transaction
[  846.472110] ACPI: EC: input buffer is not empty, aborting transaction
[  851.336121] ACPI: EC: input buffer is not empty, aborting transaction
[  856.196109] ACPI: EC: input buffer is not empty, aborting transaction
[  861.064094] ACPI: EC: input buffer is not empty, aborting transaction
[  865.924065] ACPI: EC: input buffer is not empty, aborting transaction
[  870.784071] ACPI: EC: input buffer is not empty, aborting transaction
[  875.644114] ACPI: EC: input buffer is not empty, aborting transaction
[  880.504095] ACPI: EC: input buffer is not empty, aborting transaction
[  885.368058] ACPI: EC: input buffer is not empty, aborting transaction
[  890.276122] ACPI: EC: input buffer is not empty, aborting transaction
[  895.256121] ACPI: EC: input buffer is not empty, aborting transaction
[  900.172125] ACPI: EC: input buffer is not empty, aborting transaction
[  905.048116] ACPI: EC: input buffer is not empty, aborting transaction
[  909.944092] ACPI: EC: input buffer is not empty, aborting transaction
[  914.844113] ACPI: EC: input buffer is not empty, aborting transaction
[  919.724116] ACPI: EC: input buffer is not empty, aborting transaction
[  924.640104] ACPI: EC: input buffer is not empty, aborting transaction
[  929.504124] ACPI: EC: input buffer is not empty, aborting transaction
[  934.364134] ACPI: EC: input buffer is not empty, aborting transaction
[  939.228138] ACPI: EC: input buffer is not empty, aborting transaction
[  944.092136] ACPI: EC: input buffer is not empty, aborting transaction
[  948.956134] ACPI: EC: input buffer is not empty, aborting transaction
[  953.824119] ACPI: EC: input buffer is not empty, aborting transaction
[  958.684140] ACPI: EC: input buffer is not empty, aborting transaction
[  963.548161] ACPI: EC: input buffer is not empty, aborting transaction
[  968.408131] ACPI: EC: input buffer is not empty, aborting transaction
[  973.272073] ACPI: EC: input buffer is not empty, aborting transaction
[  978.184125] ACPI: EC: input buffer is not empty, aborting transaction
[  983.156131] ACPI: EC: input buffer is not empty, aborting transaction
[  988.072135] ACPI: EC: input buffer is not empty, aborting transaction
[  992.936138] ACPI: EC: input buffer is not empty, aborting transaction
[  997.796137] ACPI: EC: input buffer is not empty, aborting transaction
[ 1002.660139] ACPI: EC: input buffer is not empty, aborting transaction
[ 1007.528208] ACPI: EC: input buffer is not empty, aborting transaction
[ 1012.392141] ACPI: EC: input buffer is not empty, aborting transaction
[ 1017.252122] ACPI: EC: input buffer is not empty, aborting transaction
[ 1022.116143] ACPI: EC: input buffer is not empty, aborting transaction
[ 1026.980135] ACPI: EC: input buffer is not empty, aborting transaction
[ 1031.916139] ACPI: EC: input buffer is not empty, aborting transaction
[ 1036.884136] ACPI: EC: input buffer is not empty, aborting transaction
[ 1041.748142] ACPI: EC: input buffer is not empty, aborting transaction
[ 1046.608134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1051.472128] ACPI: EC: input buffer is not empty, aborting transaction
[ 1056.340138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1061.204135] ACPI: EC: input buffer is not empty, aborting transaction
[ 1066.064129] ACPI: EC: input buffer is not empty, aborting transaction
[ 1070.932066] ACPI: EC: input buffer is not empty, aborting transaction
[ 1075.796133] ACPI: EC: input buffer is not empty, aborting transaction
[ 1080.656142] ACPI: EC: input buffer is not empty, aborting transaction
[ 1085.520130] ACPI: EC: input buffer is not empty, aborting transaction
[ 1090.384134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1095.244142] ACPI: EC: input buffer is not empty, aborting transaction
[ 1100.116138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1104.976128] ACPI: EC: input buffer is not empty, aborting transaction
[ 1109.840135] ACPI: EC: input buffer is not empty, aborting transaction
[ 1114.704131] ACPI: EC: input buffer is not empty, aborting transaction
[ 1119.568733] ACPI: EC: input buffer is not empty, aborting transaction
[ 1124.428138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1129.292137] ACPI: EC: input buffer is not empty, aborting transaction
[ 1134.208126] ACPI: EC: input buffer is not empty, aborting transaction
[ 1139.144140] ACPI: EC: input buffer is not empty, aborting transaction
[ 1144.020147] ACPI: EC: input buffer is not empty, aborting transaction
[ 1149.020126] ACPI: EC: input buffer is not empty, aborting transaction
[ 1154.000032] ACPI: EC: input buffer is not empty, aborting transaction
[ 1158.864132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1163.728138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1168.588106] ACPI: EC: input buffer is not empty, aborting transaction
[ 1173.452067] ACPI: EC: input buffer is not empty, aborting transaction
[ 1178.316135] ACPI: EC: input buffer is not empty, aborting transaction
[ 1183.180137] ACPI: EC: input buffer is not empty, aborting transaction
[ 1188.048145] ACPI: EC: input buffer is not empty, aborting transaction
[ 1192.908132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1197.772138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1202.636135] ACPI: EC: input buffer is not empty, aborting transaction
[ 1207.496894] ACPI: EC: input buffer is not empty, aborting transaction
[ 1212.360133] ACPI: EC: input buffer is not empty, aborting transaction
[ 1217.224138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1222.088140] ACPI: EC: input buffer is not empty, aborting transaction
[ 1226.952139] ACPI: EC: input buffer is not empty, aborting transaction
[ 1231.816130] ACPI: EC: input buffer is not empty, aborting transaction
[ 1236.676134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1241.540137] ACPI: EC: input buffer is not empty, aborting transaction
[ 1246.404132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1251.272135] ACPI: EC: input buffer is not empty, aborting transaction
[ 1256.136135] ACPI: EC: input buffer is not empty, aborting transaction
[ 1260.996131] ACPI: EC: input buffer is not empty, aborting transaction
[ 1265.860132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1270.724134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1275.584133] ACPI: EC: input buffer is not empty, aborting transaction
[ 1280.452132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1285.312134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1290.180138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1295.044130] ACPI: EC: input buffer is not empty, aborting transaction
[ 1299.904140] ACPI: EC: input buffer is not empty, aborting transaction
[ 1304.768134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1309.636138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1314.496133] ACPI: EC: input buffer is not empty, aborting transaction
[ 1319.360123] ACPI: EC: input buffer is not empty, aborting transaction
[ 1324.224147] ACPI: EC: input buffer is not empty, aborting transaction
[ 1329.088123] ACPI: EC: input buffer is not empty, aborting transaction
[ 1333.948132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1338.820134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1343.680136] ACPI: EC: input buffer is not empty, aborting transaction
[ 1348.544138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1353.408145] ACPI: EC: input buffer is not empty, aborting transaction
[ 1358.272146] ACPI: EC: input buffer is not empty, aborting transaction
[ 1363.136141] ACPI: EC: input buffer is not empty, aborting transaction
[ 1368.000146] ACPI: EC: input buffer is not empty, aborting transaction
[ 1372.860129] ACPI: EC: input buffer is not empty, aborting transaction
[ 1377.724134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1382.588130] ACPI: EC: input buffer is not empty, aborting transaction
[ 1387.452132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1392.320122] ACPI: EC: input buffer is not empty, aborting transaction
[ 1397.184129] ACPI: EC: input buffer is not empty, aborting transaction
[ 1402.048119] ACPI: EC: input buffer is not empty, aborting transaction
[ 1406.912131] ACPI: EC: input buffer is not empty, aborting transaction
[ 1411.776137] ACPI: EC: input buffer is not empty, aborting transaction
[ 1416.636135] ACPI: EC: input buffer is not empty, aborting transaction
[ 1421.500119] ACPI: EC: input buffer is not empty, aborting transaction
[ 1426.364121] ACPI: EC: input buffer is not empty, aborting transaction
[ 1431.232145] ACPI: EC: input buffer is not empty, aborting transaction
[ 1436.096124] ACPI: EC: input buffer is not empty, aborting transaction
[ 1440.956025] ACPI: EC: input buffer is not empty, aborting transaction
[ 1445.820136] ACPI: EC: input buffer is not empty, aborting transaction
[ 1450.423767] tg3: eth0: Link is down.
[ 1450.684138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1455.548138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1460.412556] ACPI: EC: input buffer is not empty, aborting transaction
[ 1465.276868] ACPI: EC: input buffer is not empty, aborting transaction
[ 1470.136133] ACPI: EC: input buffer is not empty, aborting transaction
[ 1475.000145] ACPI: EC: input buffer is not empty, aborting transaction
[ 1479.864133] ACPI: EC: input buffer is not empty, aborting transaction
[ 1484.728133] ACPI: EC: input buffer is not empty, aborting transaction
[ 1489.596132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1494.456133] ACPI: EC: input buffer is not empty, aborting transaction
[ 1499.320134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1504.184132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1509.048123] ACPI: EC: input buffer is not empty, aborting transaction
[ 1513.912132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1518.776133] ACPI: EC: input buffer is not empty, aborting transaction
[ 1523.640130] ACPI: EC: input buffer is not empty, aborting transaction
[ 1528.504130] ACPI: EC: input buffer is not empty, aborting transaction
[ 1533.369441] ACPI: EC: input buffer is not empty, aborting transaction
[ 1538.232091] ACPI: EC: input buffer is not empty, aborting transaction
[ 1543.096105] ACPI: EC: input buffer is not empty, aborting transaction
[ 1548.128090] ACPI: EC: input buffer is not empty, aborting transaction
[ 1552.992134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1557.852138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1562.716139] ACPI: EC: input buffer is not empty, aborting transaction
[ 1567.580136] ACPI: EC: input buffer is not empty, aborting transaction
[ 1572.444131] ACPI: EC: input buffer is not empty, aborting transaction
[ 1577.312122] ACPI: EC: input buffer is not empty, aborting transaction
[ 1582.176127] ACPI: EC: input buffer is not empty, aborting transaction
[ 1587.040139] ACPI: EC: input buffer is not empty, aborting transaction
[ 1591.904132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1596.768143] ACPI: EC: input buffer is not empty, aborting transaction
[ 1601.628132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1606.492135] ACPI: EC: input buffer is not empty, aborting transaction
[ 1611.360134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1616.224086] ACPI: EC: input buffer is not empty, aborting transaction
[ 1621.088140] ACPI: EC: input buffer is not empty, aborting transaction
[ 1626.224107] ACPI: EC: input buffer is not empty, aborting transaction
[ 1631.252091] ACPI: EC: input buffer is not empty, aborting transaction
[ 1636.112122] ACPI: EC: input buffer is not empty, aborting transaction
[ 1640.980100] ACPI: EC: input buffer is not empty, aborting transaction
[ 1645.840095] ACPI: EC: input buffer is not empty, aborting transaction
[ 1650.704139] ACPI: EC: input buffer is not empty, aborting transaction
[ 1655.568109] ACPI: EC: input buffer is not empty, aborting transaction
[ 1660.472029] ACPI: EC: input buffer is not empty, aborting transaction
[ 1665.332133] ACPI: EC: input buffer is not empty, aborting transaction
[ 1670.204118] ACPI: EC: input buffer is not empty, aborting transaction
[ 1675.064098] ACPI: EC: input buffer is not empty, aborting transaction
[ 1679.928129] ACPI: EC: input buffer is not empty, aborting transaction
[ 1684.792132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1689.652142] ACPI: EC: input buffer is not empty, aborting transaction
[ 1694.516138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1699.380130] ACPI: EC: input buffer is not empty, aborting transaction
[ 1704.244128] ACPI: EC: input buffer is not empty, aborting transaction
[ 1709.108140] ACPI: EC: input buffer is not empty, aborting transaction
[ 1713.972132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1718.832134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1723.700135] ACPI: EC: input buffer is not empty, aborting transaction
[ 1728.564134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1733.424094] ACPI: EC: input buffer is not empty, aborting transaction
[ 1738.288140] ACPI: EC: input buffer is not empty, aborting transaction
[ 1743.152122] ACPI: EC: input buffer is not empty, aborting transaction
[ 1748.012120] ACPI: EC: input buffer is not empty, aborting transaction
[ 1752.876133] ACPI: EC: input buffer is not empty, aborting transaction
[ 1757.744149] ACPI: EC: input buffer is not empty, aborting transaction
[ 1762.608136] ACPI: EC: input buffer is not empty, aborting transaction
[ 1767.472136] ACPI: EC: input buffer is not empty, aborting transaction
[ 1772.332140] ACPI: EC: input buffer is not empty, aborting transaction
[ 1777.196137] ACPI: EC: input buffer is not empty, aborting transaction
[ 1782.060131] ACPI: EC: input buffer is not empty, aborting transaction
[ 1786.924139] ACPI: EC: input buffer is not empty, aborting transaction
[ 1791.788134] ACPI: EC: input buffer is not empty, aborting transaction
[ 1796.652153] ACPI: EC: input buffer is not empty, aborting transaction
[ 1801.516132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1806.376131] ACPI: EC: input buffer is not empty, aborting transaction
[ 1811.244132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1816.104139] ACPI: EC: input buffer is not empty, aborting transaction
[ 1820.976099] ACPI: EC: input buffer is not empty, aborting transaction
[ 1825.836137] ACPI: EC: input buffer is not empty, aborting transaction
[ 1830.768132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1835.632053] ACPI: EC: input buffer is not empty, aborting transaction
[ 1840.492099] ACPI: EC: input buffer is not empty, aborting transaction
[ 1845.356138] ACPI: EC: input buffer is not empty, aborting transaction
[ 1850.228020] ACPI: EC: input buffer is not empty, aborting transaction
[ 1855.084057] ACPI: EC: input buffer is not empty, aborting transaction
[ 1860.108076] ACPI: EC: input buffer is not empty, aborting transaction
[ 1865.056078] ACPI: EC: input buffer is not empty, aborting transaction
[ 1869.920068] ACPI: EC: input buffer is not empty, aborting transaction
[ 1874.780072] ACPI: EC: input buffer is not empty, aborting transaction
[ 1879.648081] ACPI: EC: input buffer is not empty, aborting transaction
[ 1884.415503] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1884.415509] tg3: eth0: Flow control is off for TX and off for RX.
[ 1884.508132] ACPI: EC: input buffer is not empty, aborting transaction
[ 1889.372070] ACPI: EC: input buffer is not empty, aborting transaction
[ 1894.236129] ACPI: EC: input buffer is not empty, aborting transaction
[ 1899.104150] ACPI: EC: input buffer is not empty, aborting transaction
[ 1903.968151] ACPI: EC: input buffer is not empty, aborting transaction
[ 1908.836117] ACPI: EC: input buffer is not empty, aborting transaction
[ 1913.704155] ACPI: EC: input buffer is not empty, aborting transaction
[ 1918.568131] ACPI: EC: input buffer is not empty, aborting transaction
[ 1923.432142] ACPI: EC: input buffer is not empty, aborting transaction
[ 1928.296207] ACPI: EC: input buffer is not empty, aborting transaction
[ 1933.164159] ACPI: EC: input buffer is not empty, aborting transaction
[ 1938.032151] ACPI: EC: input buffer is not empty, aborting transaction
[ 1942.896209] ACPI: EC: input buffer is not empty, aborting transaction
[ 1947.936137] ACPI: EC: input buffer is not empty, aborting transaction
[ 1952.908206] ACPI: EC: input buffer is not empty, aborting transaction
[ 1957.920152] ACPI: EC: input buffer is not empty, aborting transaction
[ 1962.788147] ACPI: EC: input buffer is not empty, aborting transaction
[ 1967.656164] ACPI: EC: input buffer is not empty, aborting transaction
[ 1972.608150] ACPI: EC: input buffer is not empty, aborting transaction
[ 1977.556204] ACPI: EC: input buffer is not empty, aborting transaction
[ 1982.552143] ACPI: EC: input buffer is not empty, aborting transaction
[ 1987.484145] ACPI: EC: input buffer is not empty, aborting transaction
[ 1992.384147] ACPI: EC: input buffer is not empty, aborting transaction
[ 1997.256133] ACPI: EC: input buffer is not empty, aborting transaction
[ 2002.120160] ACPI: EC: input buffer is not empty, aborting transaction
[ 2006.988120] ACPI: EC: input buffer is not empty, aborting transaction
[ 2011.852063] ACPI: EC: input buffer is not empty, aborting transaction
[ 2016.720124] ACPI: EC: input buffer is not empty, aborting transaction
[ 2021.672165] ACPI: EC: input buffer is not empty, aborting transaction
[ 2026.540137] ACPI: EC: input buffer is not empty, aborting transaction
[ 2031.512103] ACPI: EC: input buffer is not empty, aborting transaction
[ 2036.376094] ACPI: EC: input buffer is not empty, aborting transaction
[ 2041.260149] ACPI: EC: input buffer is not empty, aborting transaction
[ 2046.228154] ACPI: EC: input buffer is not empty, aborting transaction
[ 2051.164124] ACPI: EC: input buffer is not empty, aborting transaction
[ 2056.184148] ACPI: EC: input buffer is not empty, aborting transaction
[ 2061.184131] ACPI: EC: input buffer is not empty, aborting transaction
[ 2066.048147] ACPI: EC: input buffer is not empty, aborting transaction
[ 2071.064190] ACPI: EC: input buffer is not empty, aborting transaction
[ 2075.932127] ACPI: EC: input buffer is not empty, aborting transaction
[ 2080.900145] ACPI: EC: input buffer is not empty, aborting transaction
[ 2085.764173] ACPI: EC: input buffer is not empty, aborting transaction
[ 2090.788131] ACPI: EC: input buffer is not empty, aborting transaction
[ 2095.656168] ACPI: EC: input buffer is not empty, aborting transaction
[ 2100.552143] ACPI: EC: input buffer is not empty, aborting transaction
[ 2105.516167] ACPI: EC: input buffer is not empty, aborting transaction
[ 2110.572133] ACPI: EC: input buffer is not empty, aborting transaction
[ 2115.484150] ACPI: EC: input buffer is not empty, aborting transaction
[ 2120.456236] ACPI: EC: input buffer is not empty, aborting transaction
[ 2125.320151] ACPI: EC: input buffer is not empty, aborting transaction
[ 2130.280149] ACPI: EC: input buffer is not empty, aborting transaction
[ 2135.300122] ACPI: EC: input buffer is not empty, aborting transaction
[ 2140.168139] ACPI: EC: input buffer is not empty, aborting transaction
[ 2145.112144] ACPI: EC: input buffer is not empty, aborting transaction
[ 2149.984178] ACPI: EC: input buffer is not empty, aborting transaction
[ 2154.992149] ACPI: EC: input buffer is not empty, aborting transaction
[ 2159.872118] ACPI: EC: input buffer is not empty, aborting transaction
mark@mark-laptop:~$
```
```
mark@mark-laptop:~$ sudo lshw -C network
[sudo] password for mark: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:e9:a4:eb
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.17 ip=192.168.100.106 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:fc500000-fc50ffff
mark@mark-laptop:~$ 
```
```
mark@mark-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

mark@mark-laptop:~$
``````
mark@mark-laptop:~$ lsb_release -d
Description:    Ubuntu 9.10
mark@mark-laptop:~$ 
```
```
mark@mark-laptop:~$ uname -mr
2.6.31-17-generic i686
mark@mark-laptop:~$
```
```
mark@mark-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
mark@mark-laptop:~$ 
```
I hope I've offered enough data for someone to help. I've been reading on the forum for days and havent found anything that makes sense, let alone helps me out.

I do appriciate anyone who responds with some insight.

Mark

---

### Post by Ukko22 on 2010-01-13
I am having pretty much the same experience with my Dell Studio 1537. I too, am a total Linux newby but a long time Window/DOS user. I activated Broadcom STA driver - in my case it is reported as activated and currently in use. After doing this, on starting up I get a notice in upper right of screen that wireless is detected and I should click in the box to connect. I click and nothing happens. The box goes away in a few seconds. Here is what I get for info on the system:

jerry@dell-den:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth3
       version: 01
       serial: 00:23:4e:c2:a7:8b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:dc:d6:f0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.17 latency=0 multicast=yes
       resources: irq:30 memory:fc500000-fc50ffff
jerry@dell-den:~$ ^C
jerry@dell-den:~$ 


Any help would be greatly appreciated. Thanks.

---

### Post by drs305 on 2010-01-13
There was just a post I read today on the forums -something like "the definitive Broadcom guide".  It covered how to get the Broadcom wireless working via online or LiveCd. 

I'll post the link if someone else doesn't find it first.

**Added:** Here it is:

[ The Definitive 9.10 Broadcom Solution Guide  ]("http://ubuntuforums.org/showpost.php?p=8585890")

---

### Post by Ukko22 on 2010-01-13
Tried the suggestions in the Definitive 9.10 Broadcom Solution Guide but ti didn't work. No change.

---

### Post by drs305 on 2010-01-14
> **Ukko22 said:**
> Tried the suggestions in the Definitive 9.10 Broadcom Solution Guide but ti didn't work. No change.

That's disappointing. I would make a post in that thread just stating that the guide was unsuccessful for you and link them to this post. Double posting is discouraged but in this case there will be a lot more readers knowledgeable with similar situtations over there. Don't repeat your post, just link and ask for assistance.

Good luck.

---

### Post by Ukko22 on 2010-01-26
Problem solved (in a way). I installed PCLinuxOS 2009.2 KDE and Wifi was detected, everything works. I was even able to connect to the printer on one of my Windows machines over the lan (which I could not do with several other distros I had tried, including Ubuntu.)

---

### Post by wormite on 2010-04-07
Since no one is trying to answer the question here anymore. I thought I might try to answer it with my personal experience.
I have been using Dell laptop for 4 years, with ubuntu all the time, I played with Gentoo a little recently, and tried to compile the kernel module/driver for broadcom myself. That gave me the picture of the situation here.
google for gentoo broadcom to understand the 3 basic ways of solving the problem. None of them, currently, works with bcm4322, at least not for gentoo x86_64.
The most promising one is broadcom sta driver(provided by broadcom themselves). The shortcoming here is, for 5.10.xx it works partially, with wireless signal dropping to zero every several min, the new 5.60.xx is broken with bcm4322, can't even iwlist scan.
Ndiswrapper hangs for bcm4322.
The answer to the question is, wait for update from broadcom people, or sell the card and buy an intel one.

---

### Post by Nikos.Alexandris on 2010-04-18
> **wormite said:**
> Since no one is trying to answer the question here anymore. I thought I might try to answer it with my personal experience.
I have been using Dell laptop for 4 years, with ubuntu all the time, I played with Gentoo a little recently, and tried to compile the kernel module/driver for broadcom myself. That gave me the picture of the situation here.
google for gentoo broadcom to understand the 3 basic ways of solving the problem. None of them, currently, works with bcm4322, at least not for gentoo x86_64.
The most promising one is broadcom sta driver(provided by broadcom themselves). The shortcoming here is, for 5.10.xx it works partially, with wireless signal dropping to zero every several min, the new 5.60.xx is broken with bcm4322, can't even iwlist scan.
Ndiswrapper hangs for bcm4322.
The answer to the question is, wait for update from broadcom people, or sell the card and buy an intel one.

Too bad for people with notebooks then.

What I don't understand is why did this wireless card worked just fine before and now not anymore? Or did it not? I don't remember having significant problems (like frequent signal drops) last year... (?)

---

