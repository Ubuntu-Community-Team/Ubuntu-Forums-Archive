---
title: "networking randomly stops and cannot be restarted"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by Sonic Boom on 2010-03-08
I recently installed xubuntu on my Acer Aspire 5532, and am enjoying the freedom away from microsoft :D However, a reocurring problem keeps on nagging me. I can use my computer problem free for several hours, but then my network just randomly disconnects, and then I cannot interact with the network button (hovering mouse over it brings no response, nor does right or left clicking). This occurrence brings upon more side effects, when it happens programs all over the place begin to crash, (e.g. terminal freezes upon being run so i cannot run any commands, and will not close unless i wait for xubuntu to bring up the option to forcibly kill it.) The strange thing is, that cpu and ram usage are normal. The only solution to this is rebooting, where after several hours it happens again. There are no external hardware drivers needed for my wireless card, and my system is up to date.

Response from lspci | grep Wireless
```
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

Response from lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Response from ifconfig
```
eth0      Link encap:Ethernet  HWaddr 70:5a:b6:01:36:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1820 (1.8 KB)  TX bytes:1820 (1.8 KB)

wlan0     Link encap:Ethernet  HWaddr 90:4c:e5:ba:ca:21  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::924c:e5ff:feba:ca21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6142050 (6.1 MB)  TX bytes:322794 (322.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 90-4C-E5-BA-CA-21-62-61-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Response from iwconfig wlan0
```
wlan0     IEEE 802.11bgn  ESSID:"Belkin_G_Plus_MIMO_01BB22"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:DF:01:BB:22   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=12/70  Signal level=-98 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Response from lsmod
```
Module                  Size  Used by
cbc                     3516  124 
aes_i586                8124  125 
aes_generic            27484  1 aes_i586
dm_crypt               12928  0 
ppdev                   6688  0 
joydev                 10240  0 
arc4                    1660  2 
ecb                     2524  3 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
psmouse                56500  0 
serio_raw               5280  0 
atl1c                  30880  0 
ath9k                 258744  0 
mac80211              181140  1 ath9k
ath                     8060  1 ath9k
cfg80211               93052  3 ath9k,mac80211,ath
fglrx                1989532  28 
agpgart                34988  1 fglrx
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  4 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  3 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
led_class               4096  1 ath9k
i2c_piix4               9932  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  3 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
k8temp                  4188  0 
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
video                  19380  0 
output                  2780  1 video

```

Response from dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 (Ubuntu 2.6.31-20.57-generic)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000ae60c000 (usable)
[    0.000000]  BIOS-e820: 00000000ae60c000 - 00000000ae80c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ae80c000 - 00000000afd70000 (usable)
[    0.000000]  BIOS-e820: 00000000afd70000 - 00000000afdbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000afdbf000 - 00000000afe92000 (usable)
[    0.000000]  BIOS-e820: 00000000afe92000 - 00000000afebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afebf000 - 00000000afee2000 (usable)
[    0.000000]  BIOS-e820: 00000000afee2000 - 00000000afef7000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afef7000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000f7000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.6 present.
[    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00A0000000 mask FFF0000000 write-back
[    0.000000]   3 base 00FFF00000 mask FFFFF00000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000ae60c000 (usable)
[    0.000000]  modified: 00000000ae60c000 - 00000000ae80c000 (ACPI NVS)
[    0.000000]  modified: 00000000ae80c000 - 00000000afd70000 (usable)
[    0.000000]  modified: 00000000afd70000 - 00000000afdbf000 (reserved)
[    0.000000]  modified: 00000000afdbf000 - 00000000afe92000 (usable)
[    0.000000]  modified: 00000000afe92000 - 00000000afebf000 (ACPI NVS)
[    0.000000]  modified: 00000000afebf000 - 00000000afee2000 (usable)
[    0.000000]  modified: 00000000afee2000 - 00000000afef7000 (ACPI data)
[    0.000000]  modified: 00000000afef7000 - 00000000aff00000 (usable)
[    0.000000]  modified: 00000000f7000000 - 00000000f8000000 (reserved)
[    0.000000]  modified: 00000000feb00000 - 00000000feb01000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37852000 - 37fef1f3
[    0.000000] Allocated new RAMDISK: 008b2000 - 0104f1f3
[    0.000000] Move RAMDISK from 0000000037852000 - 0000000037fef1f2 to 008b2000 - 0104f1f2
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT afef6120 0005C (v01 ACRSYS ACRPRDCT 00000003      01000013)
[    0.000000] ACPI: FACP afef5000 000F4 (v04 ACRSYS ACRPRDCT 00000003 1025 01000013)
[    0.000000] ACPI: DSDT afee9000 08E28 (v01 ACRSYS ACRPRDCT 00001000 1025 01000013)
[    0.000000] ACPI: FACS afe9c000 00040
[    0.000000] ACPI: HPET afef4000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC afef3000 00068 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG afef2000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT afee8000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC afee7000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SSDT afee6000 00115 (v01 AMD    PowerNow 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1927MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b126f]              BRK ==> [00008ae000 - 00008b126f]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008b2000 - 000104f1f3]      NEW RAMDISK ==> [00008b2000 - 000104f1f3]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000aff00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000ae60c
[    0.000000]     0: 0x000ae80c -> 0x000afd70
[    0.000000]     0: 0x000afdbf -> 0x000afe92
[    0.000000]     0: 0x000afebf -> 0x000afee2
[    0.000000]     0: 0x000afef7 -> 0x000aff00
[    0.000000] On node 0 totalpages: 719882
[    0.000000] free_area_init_node: node 0, pgdat c0788920, node_mem_map c1050000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3855 pages used for memmap
[    0.000000]   HighMem zone: 488802 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:47100000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c265a000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 714251
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=ece6e0bc-f2d0-42b6-9991-ad252d77508a ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 14412800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000aff00)
[    0.000000] Memory: 2825484k/2882560k available (4579k kernel code, 53256k reserved, 2145k data, 540k init, 1970628k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578c68 - 0xc0791448   (2145 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578c68   (4579 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1994.837 MHz processor.
[    0.000012] spurious 8259A interrupt: IRQ7.
[    0.001145] Console: colour VGA+ 80x25
[    0.001148] console [tty0] enabled
[    0.001492] hpet clockevent registered
[    0.001499]   alloc irq_desc for 24 on node 0
[    0.001507]   alloc kstat_irqs on node 0
[    0.001514] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.001520] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.67 BogoMIPS (lpj=7979348)
[    0.001541] Security Framework initialized
[    0.001555] AppArmor: AppArmor initialized
[    0.001562] Mount-cache hash table entries: 512
[    0.001689] Initializing cgroup subsys ns
[    0.001693] Initializing cgroup subsys cpuacct
[    0.001697] Initializing cgroup subsys memory
[    0.001703] Initializing cgroup subsys freezer
[    0.001706] Initializing cgroup subsys net_cls
[    0.001718] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.001721] CPU: L2 Cache: 256K (64 bytes/line)
[    0.001725] mce: CPU supports 5 MCE banks
[    0.001734] using C1E aware idle routine
[    0.001742] Performance Counters: AMD PMU driver.
[    0.001748] ... version:                 0
[    0.001750] ... bit width:               48
[    0.001752] ... generic counters:        4
[    0.001754] ... value mask:              0000ffffffffffff
[    0.001756] ... max period:              00007fffffffffff
[    0.001758] ... fixed-purpose counters:  0
[    0.001760] ... counter mask:            000000000000000f
[    0.001764] Checking 'hlt' instruction... OK.
[    0.016595] SMP alternatives: switching to UP code
[    0.022231] ACPI: Core revision 20090521
[    0.036437] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.079286] CPU0: AMD Athlon(tm) Processor TF-36 stepping 02
[    0.080001] Brought up 1 CPUs
[    0.080001] Total of 1 processors activated (3989.67 BogoMIPS).
[    0.080001] CPU0 attaching NULL sched-domain.
[    0.080001] Booting paravirtualized kernel on bare hardware
[    0.080001] regulator: core version 0.5
[    0.080001] Time: 18:48:23  Date: 03/08/10
[    0.080001] NET: Registered protocol family 16
[    0.080001] EISA bus registered
[    0.080001] ACPI: bus type pci registered
[    0.080001] PCI: MCFG configuration 0: base f7000000 segment 0 buses 0 - 15
[    0.080001] PCI: MCFG area at f7000000 reserved in E820
[    0.080001] PCI: Using MMCONFIG for extended config space
[    0.080001] PCI: Using configuration type 1 for base access
[    0.080001] bio: create slab <bio-0> at 0
[    0.080001] ACPI: EC: Look up EC in DSDT
[    0.083795] ACPI: BIOS _OSI(Linux) query ignored
[    0.087930] ACPI: Interpreter enabled
[    0.087935] ACPI: (supports S0 S1 S3 S4 S5)
[    0.087964] ACPI: Using IOAPIC for interrupt routing
[    0.094433] System has AMD C1E enabled
[    0.094446] Switch to broadcast mode on CPU0
[    0.094446] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.608004] ACPI: EC: missing confirmations, switch off interrupt mode.
[    0.960325] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.960328] ACPI: EC: driver started in poll mode
[    0.960570] ACPI: No dock devices found.
[    0.961503] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.961657] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.961661] pci 0000:00:04.0: PME# disabled
[    0.961703] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.961706] pci 0000:00:05.0: PME# disabled
[    0.961805] pci 0000:00:11.0: reg 10 io port: [0x8038-0x803f]
[    0.961813] pci 0000:00:11.0: reg 14 io port: [0x804c-0x804f]
[    0.961821] pci 0000:00:11.0: reg 18 io port: [0x8030-0x8037]
[    0.961829] pci 0000:00:11.0: reg 1c io port: [0x8048-0x804b]
[    0.961837] pci 0000:00:11.0: reg 20 io port: [0x8010-0x801f]
[    0.961845] pci 0000:00:11.0: reg 24 32bit mmio: [0xd2306000-0xd23063ff]
[    0.961907] pci 0000:00:12.0: reg 10 32bit mmio: [0xd2305000-0xd2305fff]
[    0.961969] pci 0000:00:12.1: reg 10 32bit mmio: [0xd2304000-0xd2304fff]
[    0.962050] pci 0000:00:12.2: reg 10 32bit mmio: [0xd2306400-0xd23064ff]
[    0.962109] pci 0000:00:12.2: supports D1 D2
[    0.962111] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.962116] pci 0000:00:12.2: PME# disabled
[    0.962256] pci 0000:00:14.2: reg 10 64bit mmio: [0xd2300000-0xd2303fff]
[    0.962304] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.962309] pci 0000:00:14.2: PME# disabled
[    0.962516] pci 0000:01:05.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
[    0.962521] pci 0000:01:05.0: reg 14 io port: [0x7000-0x70ff]
[    0.962526] pci 0000:01:05.0: reg 18 32bit mmio: [0xd2200000-0xd220ffff]
[    0.962535] pci 0000:01:05.0: reg 24 32bit mmio: [0xd2100000-0xd21fffff]
[    0.962551] pci 0000:01:05.0: supports D1 D2
[    0.962629] pci 0000:00:01.0: bridge io port: [0x7000-0x7fff]
[    0.962633] pci 0000:00:01.0: bridge 32bit mmio: [0xd2100000-0xd22fffff]
[    0.962638] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.962683] pci 0000:02:00.0: reg 10 64bit mmio: [0xd1100000-0xd110ffff]
[    0.962740] pci 0000:02:00.0: supports D1
[    0.962743] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.962747] pci 0000:02:00.0: PME# disabled
[    0.962818] pci 0000:00:04.0: bridge io port: [0x3000-0x6fff]
[    0.962822] pci 0000:00:04.0: bridge 32bit mmio: [0xd1100000-0xd20fffff]
[    0.962827] pci 0000:00:04.0: bridge 64bit mmio pref: [0xd0000000-0xd0ffffff]
[    0.962879] pci 0000:08:00.0: reg 10 64bit mmio: [0xd1000000-0xd103ffff]
[    0.962887] pci 0000:08:00.0: reg 18 io port: [0x2000-0x207f]
[    0.962947] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.962952] pci 0000:08:00.0: PME# disabled
[    0.963050] pci 0000:00:05.0: bridge io port: [0x2000-0x2fff]
[    0.963054] pci 0000:00:05.0: bridge 32bit mmio: [0xd1000000-0xd10fffff]
[    0.963119] pci 0000:00:14.4: transparent bridge
[    0.963124] pci 0000:00:14.4: bridge io port: [0x1000-0x1fff]
[    0.963145] pci_bus 0000:00: on NUMA node 0
[    0.963151] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.963286] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.963367] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.963447] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.963576] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.971255] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.971457] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.971619] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.971782] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.971945] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.972154] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.972352] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.972537] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.972769] SCSI subsystem initialized
[    0.972840] libata version 3.00 loaded.
[    0.972910] usbcore: registered new interface driver usbfs
[    0.972922] usbcore: registered new interface driver hub
[    0.972945] usbcore: registered new device driver usb
[    0.973139] ACPI: WMI: Mapper loaded
[    0.973141] PCI: Using ACPI for IRQ routing
[    0.973326] Bluetooth: Core ver 2.15
[    0.973356] NET: Registered protocol family 31
[    0.973358] Bluetooth: HCI device and connection manager initialized
[    0.973361] Bluetooth: HCI socket layer initialized
[    0.973363] NetLabel: Initializing
[    0.973364] NetLabel:  domain hash size = 128
[    0.973366] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.973380] NetLabel:  unlabeled traffic allowed by default
[    0.973444] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.973449] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.976027] hpet: hpet2 irq 24 for MSI
[    0.977562] pnp: PnP ACPI init
[    0.977583] ACPI: bus type pnp registered
[    0.980034] Switched to high resolution mode on CPU 0
[    1.172096] pnp: PnP ACPI: found 10 devices
[    1.172098] ACPI: ACPI bus type pnp unregistered
[    1.172102] PnPBIOS: Disabled by ACPI PNP
[    1.172114] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    1.172118] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.172121] system 00:01: iomem range 0xf7000000-0xf7ffffff has been reserved
[    1.172129] system 00:08: ioport range 0x400-0x4cf has been reserved
[    1.172132] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.172135] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    1.172138] system 00:08: ioport range 0x680-0x6ff has been reserved
[    1.172141] system 00:08: ioport range 0x77a-0x77a has been reserved
[    1.172145] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    1.172148] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    1.172151] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    1.172154] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    1.172157] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    1.172160] system 00:08: ioport range 0xcd0-0xcdb has been reserved
[    1.172163] system 00:08: ioport range 0xfd60-0xfd63 has been reserved
[    1.172169] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    1.172172] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
[    1.207046] AppArmor: AppArmor Filesystem Enabled
[    1.207111] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.207114] pci 0000:00:01.0:   IO window: 0x7000-0x7fff
[    1.207118] pci 0000:00:01.0:   MEM window: 0xd2100000-0xd22fffff
[    1.207122] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    1.207127] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    1.207130] pci 0000:00:04.0:   IO window: 0x3000-0x6fff
[    1.207134] pci 0000:00:04.0:   MEM window: 0xd1100000-0xd20fffff
[    1.207138] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000d0ffffff
[    1.207143] pci 0000:00:05.0: PCI bridge, secondary bus 0000:08
[    1.207146] pci 0000:00:05.0:   IO window: 0x2000-0x2fff
[    1.207150] pci 0000:00:05.0:   MEM window: 0xd1000000-0xd10fffff
[    1.207153] pci 0000:00:05.0:   PREFETCH window: disabled
[    1.207156] pci 0000:00:14.4: PCI bridge, secondary bus 0000:09
[    1.207194] pci 0000:00:14.4:   IO window: 0x1000-0x1fff
[    1.207200] pci 0000:00:14.4:   MEM window: disabled
[    1.207204] pci 0000:00:14.4:   PREFETCH window: disabled
[    1.207214] pci 0000:00:01.0: setting latency timer to 64
[    1.207222]   alloc irq_desc for 16 on node -1
[    1.207225]   alloc kstat_irqs on node -1
[    1.207231] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.207234] pci 0000:00:04.0: setting latency timer to 64
[    1.207239]   alloc irq_desc for 17 on node -1
[    1.207241]   alloc kstat_irqs on node -1
[    1.207245] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.207248] pci 0000:00:05.0: setting latency timer to 64
[    1.207257] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    1.207260] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    1.207263] pci_bus 0000:01: resource 0 io:  [0x7000-0x7fff]
[    1.207266] pci_bus 0000:01: resource 1 mem: [0xd2100000-0xd22fffff]
[    1.207269] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    1.207272] pci_bus 0000:02: resource 0 io:  [0x3000-0x6fff]
[    1.207275] pci_bus 0000:02: resource 1 mem: [0xd1100000-0xd20fffff]
[    1.207278] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xd0ffffff]
[    1.207281] pci_bus 0000:08: resource 0 io:  [0x2000-0x2fff]
[    1.207284] pci_bus 0000:08: resource 1 mem: [0xd1000000-0xd10fffff]
[    1.207287] pci_bus 0000:09: resource 0 io:  [0x1000-0x1fff]
[    1.207289] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    1.207292] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffff]
[    1.207331] NET: Registered protocol family 2
[    1.207422] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.207739] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.208639] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.209073] TCP: Hash tables configured (established 131072 bind 65536)
[    1.209076] TCP reno registered
[    1.209169] NET: Registered protocol family 1
[    1.209232] Trying to unpack rootfs image as initramfs...
[    1.426440] Freeing initrd memory: 7796k freed
[    1.432676] Simple Boot Flag at 0x44 set to 0x1
[    1.432799] cpufreq-nforce2: No nForce2 chipset.
[    1.432825] Scanning for low memory corruption every 60 seconds
[    1.432926] audit: initializing netlink socket (disabled)
[    1.432941] type=2000 audit(1268074104.432:1): initialized
[    1.442202] highmem bounce pool size: 64 pages
[    1.442208] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.443538] VFS: Disk quotas dquot_6.5.2
[    1.443593] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.444177] fuse init (API version 7.12)
[    1.444256] msgmni has been set to 1686
[    1.444514] alg: No test for stdrng (krng)
[    1.444526] io scheduler noop registered
[    1.444528] io scheduler anticipatory registered
[    1.444530] io scheduler deadline registered
[    1.444570] io scheduler cfq registered (default)
[    1.532077] pci 0000:01:05.0: Boot video device
[    1.532191]   alloc irq_desc for 25 on node -1
[    1.532193]   alloc kstat_irqs on node -1
[    1.532202] pcieport-driver 0000:00:04.0: irq 25 for MSI/MSI-X
[    1.532209] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.532309]   alloc irq_desc for 26 on node -1
[    1.532311]   alloc kstat_irqs on node -1
[    1.532316] pcieport-driver 0000:00:05.0: irq 26 for MSI/MSI-X
[    1.532322] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.532390] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.532459] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.660119] ACPI: AC Adapter [ACAD] (on-line)
[    1.660179] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.660183] ACPI: Power Button [PWRF]
[    1.660263] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.660266] ACPI: Power Button [PWRB]
[    1.660303] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.660306] ACPI: Sleep Button [SLPB]
[    1.660352] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0D:00/input/input3
[    1.924096] ACPI: Lid Switch [LID]
[    1.924406] ACPI: processor limited to max C-state 1
[    1.924430] processor LNXCPU:00: registered as cooling_device0
[    1.924434] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.244256] ACPI: Invalid active0 threshold
[    2.372103] thermal LNXTHERM:01: registered as thermal_zone0
[    2.372110] ACPI: Thermal Zone [THRM] (56 C)
[    2.372157] isapnp: Scanning for PnP cards...
[    2.756615] isapnp: No Plug & Play device found
[    2.757677] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.758846] brd: module loaded
[    2.759266] loop: module loaded
[    2.759348] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.759417] ahci 0000:00:11.0: version 3.0
[    2.759466]   alloc irq_desc for 22 on node -1
[    2.759468]   alloc kstat_irqs on node -1
[    2.759476] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.759517]   alloc irq_desc for 27 on node -1
[    2.759519]   alloc kstat_irqs on node -1
[    2.759530] ahci 0000:00:11.0: irq 27 for MSI/MSI-X
[    2.759715] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    2.759719] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.760767] scsi0 : ahci
[    2.760911] scsi1 : ahci
[    2.761004] scsi2 : ahci
[    2.761088] scsi3 : ahci
[    2.761179] scsi4 : ahci
[    2.761265] scsi5 : ahci
[    2.761449] ata1: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306100 irq 27
[    2.761453] ata2: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306180 irq 27
[    2.761457] ata3: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306200 irq 27
[    2.761461] ata4: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306280 irq 27
[    2.761466] ata5: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306300 irq 27
[    2.761470] ata6: SATA max UDMA/133 abar m1024@0xd2306000 port 0xd2306380 irq 27
[    2.762251] Fixed MDIO Bus: probed
[    2.762286] PPP generic driver version 2.4.2
[    2.762392] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.762449] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.762467] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    2.762471] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    2.762505] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    2.762545] ehci_hcd 0000:00:12.2: debug port 1
[    2.762564] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2306400
[    2.772056] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    2.772133] usb usb1: configuration #1 chosen from 1 choice
[    2.772166] hub 1-0:1.0: USB hub found
[    2.772175] hub 1-0:1.0: 6 ports detected
[    2.772272] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.772330] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.772349] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    2.772352] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.772386] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 2
[    2.772457] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2305000
[    2.832102] usb usb2: configuration #1 chosen from 1 choice
[    2.832129] hub 2-0:1.0: USB hub found
[    2.832173] hub 2-0:1.0: 3 ports detected
[    2.832217] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.832229] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    2.832233] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    2.832260] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 3
[    2.832278] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2304000
[    2.892099] usb usb3: configuration #1 chosen from 1 choice
[    2.892121] hub 3-0:1.0: USB hub found
[    2.892165] hub 3-0:1.0: 3 ports detected
[    2.892212] uhci_hcd: USB Universal Host Controller Interface driver
[    2.892293] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.914121] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.914127] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.914185] mice: PS/2 mouse device common for all mice
[    2.914329] rtc_cmos 00:04: RTC can wake from S4
[    2.914364] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.914391] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    2.914490] device-mapper: uevent: version 1.0.3
[    2.914627] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.914733] device-mapper: multipath: version 1.1.0 loaded
[    2.914736] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.914893] EISA: Probing bus 0 at eisa.0
[    2.914934] Cannot allocate resource for EISA slot 1
[    2.914936] Cannot allocate resource for EISA slot 2
[    2.914939] Cannot allocate resource for EISA slot 3
[    2.914941] Cannot allocate resource for EISA slot 4
[    2.914943] Cannot allocate resource for EISA slot 5
[    2.914945] Cannot allocate resource for EISA slot 6
[    2.914947] Cannot allocate resource for EISA slot 7
[    2.914949] Cannot allocate resource for EISA slot 8
[    2.914951] EISA: Detected 0 cards.
[    2.914993] cpuidle: using governor ladder
[    2.914996] cpuidle: using governor menu
[    2.915469] TCP cubic registered
[    2.915617] NET: Registered protocol family 10
[    2.916068] lo: Disabled Privacy Extensions
[    2.916358] NET: Registered protocol family 17
[    2.916378] Bluetooth: L2CAP ver 2.13
[    2.916380] Bluetooth: L2CAP socket layer initialized
[    2.916383] Bluetooth: SCO (Voice Link) ver 0.6
[    2.916384] Bluetooth: SCO socket layer initialized
[    2.916479] Bluetooth: RFCOMM TTY layer initialized
[    2.916503] Bluetooth: RFCOMM socket layer initialized
[    2.916505] Bluetooth: RFCOMM ver 1.11
[    2.916520] powernow-k8: Found 1 AMD Athlon(tm) Processor TF-36 processors (1 cpu cores) (version 2.20.00)
[    2.916567] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
[    2.916570] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x11
[    2.916573] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x12
[    2.916575] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[    2.916614] Using IPI No-Shortcut mode
[    2.916685] PM: Resume from disk failed.
[    2.916697] registered taskstats version 1
[    2.916797]   Magic number: 2:279:847
[    2.916928] rtc_cmos 00:04: setting system clock to 2010-03-08 18:48:26 UTC (1268074106)
[    2.916931] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.916933] EDD information not available.
[    2.933896] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.080074] ata4: SATA link down (SStatus 0 SControl 300)
[    3.080106] ata5: SATA link down (SStatus 0 SControl 300)
[    3.080136] ata6: SATA link down (SStatus 0 SControl 300)
[    3.080208] ata2: SATA link down (SStatus 0 SControl 300)
[    3.244075] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.244102] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.244992] ata1.00: ATA-8: Hitachi HTS545016B9A300, PBBOC60F, max UDMA/133
[    3.244996] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.246115] ata1.00: configured for UDMA/133
[    3.249244] ata3.00: ATAPI: Slimtype DVD A  DS8A4SH, CA91, max UDMA/100, ATAPI AN
[    3.251133] ata3.00: configured for UDMA/100
[    4.660150] ACPI: Battery Slot [BAT1] (battery present)
[    4.660377] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54501 PBBO PQ: 0 ANSI: 5
[    4.660497] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.660537] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    4.660580] sd 0:0:0:0: [sda] Write Protect is off
[    4.660583] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.660604] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.660716]  sda:
[    4.664510] scsi 2:0:0:0: CD-ROM            Slimtype DVD A  DS8A4SH   CA91 PQ: 0 ANSI: 5
[    4.674364] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.674367] Uniform CD-ROM driver Revision: 3.20
[    4.674444] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.674488] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    4.687018]  sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    4.738190] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.738207] Freeing unused kernel memory: 540k freed
[    4.738637] Write protecting the kernel text: 4580k
[    4.738675] Write protecting the kernel read-only data: 1840k
[    5.460262] acpi device:04: registered as cooling_device1
[    5.460408] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[    5.460448] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    6.172925] PM: Starting manual resume from disk
[    6.172931] PM: Resume from partition 8:7
[    6.172933] PM: Checking hibernation image.
[    6.173099] PM: Resume from disk failed.
[    6.194073] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    6.194079] EXT4-fs (sda6): write access will be enabled during recovery
[    6.205963] EXT4-fs (sda6): barriers enabled
[    8.694281] kjournald2 starting: pid 350, dev sda6:8, commit interval 5 seconds
[    8.694358] EXT4-fs (sda6): delayed allocation enabled
[    8.694362] EXT4-fs: file extents enabled
[    8.699565] EXT4-fs: mballoc enabled
[    8.699581] EXT4-fs (sda6): orphan cleanup on readonly fs
[    8.699590] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 132473
[    8.699782] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131790
[    8.699866] EXT4-fs (sda6): 2 orphan inodes deleted
[    8.699869] EXT4-fs (sda6): recovery complete
[    8.904818] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    9.632877] type=1505 audit(1268074113.215:2): operation="profile_load" pid=378 name=/sbin/dhclient3
[    9.633174] type=1505 audit(1268074113.215:3): operation="profile_load" pid=378 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.633341] type=1505 audit(1268074113.215:4): operation="profile_load" pid=378 name=/usr/lib/connman/scripts/dhclient-script
[    9.691096] type=1505 audit(1268074113.271:5): operation="profile_load" pid=379 name=/usr/bin/evince
[    9.696068] type=1505 audit(1268074113.279:6): operation="profile_load" pid=379 name=/usr/bin/evince-previewer
[    9.699025] type=1505 audit(1268074113.279:7): operation="profile_load" pid=379 name=/usr/bin/evince-thumbnailer
[    9.715635] type=1505 audit(1268074113.295:8): operation="profile_load" pid=381 name=/usr/lib/cups/backend/cups-pdf
[    9.716005] type=1505 audit(1268074113.295:9): operation="profile_load" pid=381 name=/usr/sbin/cupsd
[    9.731601] type=1505 audit(1268074113.311:10): operation="profile_load" pid=382 name=/usr/sbin/tcpdump
[   23.199356] udev: starting version 147
[   23.227912] Adding 1783172k swap on /dev/sda7.  Priority:-1 extents:1 across:1783172k 
[   23.291256] lp: driver loaded but no devices found
[   23.534075] EXT4-fs (sda6): internal journal on sda6:8
[   24.021849] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   24.021855] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   24.021881] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.033104] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   24.170966] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   24.174914] acer-wmi: Acer Laptop ACPI-WMI Extras
[   24.293119] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.293151] HDA Intel 0000:00:14.2: setting latency timer to 64
[   24.312180] acer-wmi: Unable to detect available WMID devices
[   24.373576] hda_codec: Unknown model for ALC272, trying auto-probe from BIOS...
[   24.374089] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
[   24.975441] Linux agpgart interface v0.103
[   24.996262] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   24.996267] Disabling lock debugging due to kernel taint
[   25.072709] [fglrx] Maximum main memory to use for locked dma buffers: 2627 MBytes.
[   25.072733] [fglrx]   vendor: 1002 device: 9612 count: 1
[   25.072898] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
[   25.072914]   alloc irq_desc for 18 on node -1
[   25.072917]   alloc kstat_irqs on node -1
[   25.072925] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   25.072930] pci 0000:01:05.0: setting latency timer to 64
[   25.073159] [fglrx] Kernel PAT support is enabled
[   25.073185] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[   25.090343] cfg80211: Calling CRDA to update world regulatory domain
[   25.138944] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.138956] ath9k 0000:02:00.0: setting latency timer to 64
[   25.567744] ath: EEPROM regdomain: 0x65
[   25.567747] ath: EEPROM indicates we should expect a direct regpair map
[   25.567751] ath: Country alpha2 being used: 00
[   25.567753] ath: Regpair used: 0x65
[   25.570807] atl1c 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.570819] atl1c 0000:08:00.0: setting latency timer to 64
[   25.570866] atl1c 0000:08:00.0: PME# disabled
[   25.570871] atl1c 0000:08:00.0: PME# disabled
[   25.656890] atl1c 0000:08:00.0: version 1.0.0.1-NAPI
[   25.714919] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.750543] cfg80211: World regulatory domain updated:
[   25.750548]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.750552]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.750555]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.750558]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.750561]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.750563]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.811759]   alloc irq_desc for 28 on node -1
[   25.811763]   alloc kstat_irqs on node -1
[   25.811779] atl1c 0000:08:00.0: irq 28 for MSI/MSI-X
[   25.812236] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.968380] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   25.969068] Registered led device: ath9k-phy0::radio
[   25.969086] Registered led device: ath9k-phy0::assoc
[   25.969104] Registered led device: ath9k-phy0::tx
[   25.969121] Registered led device: ath9k-phy0::rx
[   25.969134] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xf8980000, irq=16
[   26.069903] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.210583] type=1505 audit(1268092129.791:11): operation="profile_replace" pid=1094 name=/sbin/dhclient3
[   26.210883] type=1505 audit(1268092129.791:12): operation="profile_replace" pid=1094 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   26.211052] type=1505 audit(1268092129.791:13): operation="profile_replace" pid=1094 name=/usr/lib/connman/scripts/dhclient-script
[   26.215494] type=1505 audit(1268092129.795:14): operation="profile_replace" pid=1095 name=/usr/bin/evince
[   26.223069] type=1505 audit(1268092129.803:15): operation="profile_replace" pid=1095 name=/usr/bin/evince-previewer
[   26.227098] type=1505 audit(1268092129.807:16): operation="profile_replace" pid=1095 name=/usr/bin/evince-thumbnailer
[   26.232930] type=1505 audit(1268092129.815:17): operation="profile_replace" pid=1097 name=/usr/lib/cups/backend/cups-pdf
[   26.233302] type=1505 audit(1268092129.815:18): operation="profile_replace" pid=1097 name=/usr/sbin/cupsd
[   26.235364] type=1505 audit(1268092129.815:19): operation="profile_replace" pid=1098 name=/usr/sbin/tcpdump
[   26.245042] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   26.274056] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   27.095605] ppdev: user-space parallel port driver
[   29.789262] [fglrx] GART Table is not in FRAME_BUFFER range 
[   29.789463]   alloc irq_desc for 29 on node -1
[   29.789466]   alloc kstat_irqs on node -1
[   29.789477] fglrx_pci 0000:01:05.0: irq 29 for MSI/MSI-X
[   29.790118] [fglrx] Firegl kernel thread PID: 1583
[   29.983218] [fglrx] Gart USWC size:864 M.
[   29.983223] [fglrx] Gart cacheable size:342 M.
[   29.983229] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   29.983233] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   38.000067] Clocksource tsc unstable (delta = -83375935 ns)
[   48.389713] padlock: VIA PadLock not detected.
[   61.054800] wlan0: authenticate with AP 00:1c:df:01:bb:22
[   61.056985] wlan0: authenticated
[   61.056995] wlan0: associate with AP 00:1c:df:01:bb:22
[   61.059992] wlan0: RX AssocResp from 00:1c:df:01:bb:22 (capab=0x411 status=0 aid=3)
[   61.060004] wlan0: associated
[   61.065309] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.280071] wlan0: no IPv6 routers present

```

Response from lshw
```
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 90:4c:e5:ba:ca:21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.8 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:d1100000-d110ffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: 70:5a:b6:01:36:ef
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:d1000000-d103ffff ioport:2000(size=128)

```

Response from uname
```
2.6.31-20-generic i686

```

---

