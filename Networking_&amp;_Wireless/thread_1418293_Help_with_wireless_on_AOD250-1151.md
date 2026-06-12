---
title: "Help with wireless on AOD250-1151"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by raymonds0528 on 2010-02-28
[B]Description of problem:
[/B]Cannot seem to get the wireless  adapter in my netbook to play nice with ubuntu.  I am pretty much a noob  when it comes to linux, but I do know enough to get into trouble.  I  have been searching the net trying different things to attempt to  resolve this with no luck.  I believe at this point that I do have the  driver installed, and lspci does list the adapter, however, when i do  ifconfig it is not listed there.  I have tried to install the ndis-gtk  package and had no luck at all with it so I removed it.  At this point I  would just like my wireless to work and understand how to get it  working so that when upgrades to ubuntu happen I have and idea of how to  fix it.  Below is the Here is what we need stuff.  Any insight anyone  can provide on getting this working would be awesome.
[B]

1 )  Machine Brand and Model (PC/Laptop)[/B]:
     Code:
     Acer Aspire One AOD250-1151 
**2 ) Wireless Brand, Model and Wireless Chipset:**
     Code:
     $ lspci
01:00.0 Network Controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

$ lsusb
N/A

([COLOR=Red]hint[/COLOR]) use **grep** to get only  information about the Wireless
     Code:
     $ lspci -nn | grep 'Wireless Brand'
01:00.0 Network Controller: Broadcom Corporation BCM4312 802.11b/g [14e4:4315](rev 01)


**3 ) check interface:**
     Code:
     $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:51:4d:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:44026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11619 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:27294076 (27.2 MB)  TX bytes:921500 (921.5 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:568 (568.0 B)  TX bytes:568 (568.0 B)


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



**4 ) Check for modules:**
     Code:
     $ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
usb_storage            52576  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               4096  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
psmouse                56500  0 
serio_raw               5280  0 
atl1c                  30880  0 
ndiswrapper           185532  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp


([COLOR=Red]hint[/COLOR]) search for the Wireless module
     Code:
     $ lsmod | grep "wlan_module_name" 
**5 ) Kernel boot messages**
     Code:
     $ dmesg (sorry this part is so long... I dont know what I am looking for in here)
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-19-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 (Ubuntu 2.6.31-19.56-generic)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f576000 (usable)
[    0.000000]  BIOS-e820: 000000003f576000 - 000000003f5bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f66d000 (usable)
[    0.000000]  BIOS-e820: 000000003f66d000 - 000000003f6bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6bf000 - 000000003f6ee000 (usable)
[    0.000000]  BIOS-e820: 000000003f6ee000 - 000000003f6ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x3f700 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFF00000 mask 0FFF00000 write-protect
[    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable
[    0.000000]   2 base 000000000 mask 0E0000000 write-back
[    0.000000]   3 base 020000000 mask 0E0000000 write-back
[    0.000000]   4 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   5 base 03F700000 mask 0FFF00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f576000 (usable)
[    0.000000]  modified: 000000003f576000 - 000000003f5bf000 (reserved)
[    0.000000]  modified: 000000003f5bf000 - 000000003f66d000 (usable)
[    0.000000]  modified: 000000003f66d000 - 000000003f6bf000 (ACPI NVS)
[    0.000000]  modified: 000000003f6bf000 - 000000003f6ee000 (usable)
[    0.000000]  modified: 000000003f6ee000 - 000000003f6ff000 (ACPI data)
[    0.000000]  modified: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2f0cc000 - 2f8581c6
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 3f6fe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 3f6fc000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: DSDT 3f6f0000 070CA (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: FACS 3f688000 00040
[    0.000000] ACPI: SSDT 3f6fd000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: HPET 3f6fb000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 3f6fa000 00068 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 3f6f9000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: ASF! 3f6f8000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 3f6ef000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 3f6ee000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 127MB HIGHMEM available.
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
[    0.000000]   #4 [002f0cc000 - 002f8581c6]          RAMDISK ==> [002f0cc000 - 002f8581c6]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac178]              BRK ==> [00008a9000 - 00008ac178]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f700
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f576
[    0.000000]     0: 0x0003f5bf -> 0x0003f66d
[    0.000000]     0: 0x0003f6bf -> 0x0003f6ee
[    0.000000]     0: 0x0003f6ff -> 0x0003f700
[    0.000000] On node 0 totalpages: 259567
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32087 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
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
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257536
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5196800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f700)
[    0.000000] Memory: 1008088k/1039360k available (4567k kernel code, 29744k reserved, 2141k data, 540k init, 129368k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575c48 - 0xc078d408   (2141 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575c48   (4567 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.755 MHz processor.
[    0.001914] Console: colour VGA+ 80x25
[    0.001921] console [tty0] enabled
[    0.002176] hpet clockevent registered
[    0.002184] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002196] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.51 BogoMIPS (lpj=6383020)
[    0.002232] Security Framework initialized
[    0.002271] AppArmor: AppArmor initialized
[    0.002285] Mount-cache hash table entries: 512
[    0.002519] Initializing cgroup subsys ns
[    0.002529] Initializing cgroup subsys cpuacct
[    0.002537] Initializing cgroup subsys memory
[    0.002550] Initializing cgroup subsys freezer
[    0.002555] Initializing cgroup subsys net_cls
[    0.002580] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.002587] CPU: L2 cache: 512K
[    0.002592] CPU: Physical Processor ID: 0
[    0.002596] CPU: Processor Core ID: 0
[    0.002603] mce: CPU supports 5 MCE banks
[    0.002618] CPU0: Thermal monitoring enabled (TM2)
[    0.002626] using mwait in idle threads.
[    0.002638] Performance Counters: Atom events, Intel PMU driver.
[    0.002652] ... version:                 3
[    0.002656] ... bit width:               40
[    0.002660] ... generic counters:        2
[    0.002665] ... value mask:              000000ffffffffff
[    0.002670] ... max period:              000000007fffffff
[    0.002674] ... fixed-purpose counters:  3
[    0.002679] ... counter mask:            0000000700000003
[    0.002687] Checking 'hlt' instruction... OK.
[    0.020013] ACPI: Core revision 20090521
[    0.040500] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080256] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3191.93 BogoMIPS (lpj=6383869)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.168996] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.169032] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.172050] Brought up 2 CPUs
[    0.172058] Total of 2 processors activated (6383.44 BogoMIPS).
[    0.172125] CPU0 attaching sched-domain:
[    0.172131]  domain 0: span 0-1 level SIBLING
[    0.172137]   groups: 0 1
[    0.172148] CPU1 attaching sched-domain:
[    0.172153]  domain 0: span 0-1 level SIBLING
[    0.172158]   groups: 1 0
[    0.172311] Booting paravirtualized kernel on bare hardware
[    0.172477] regulator: core version 0.5
[    0.172477] Time:  9:09:19  Date: 02/27/10
[    0.172477] NET: Registered protocol family 16
[    0.172477] EISA bus registered
[    0.172477] ACPI: bus type pci registered
[    0.172591] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.172599] PCI: MCFG area at e0000000 reserved in E820
[    0.172603] PCI: Using MMCONFIG for extended config space
[    0.172608] PCI: Using configuration type 1 for base access
[    0.176960] bio: create slab <bio-0> at 0
[    0.177879] ACPI: EC: Look up EC in DSDT
[    0.215616] ACPI: BIOS _OSI(Linux) query ignored
[    0.216669] ACPI: Interpreter enabled
[    0.216679] ACPI: (supports S0 S3 S4 S5)
[    0.216731] ACPI: Using IOAPIC for interrupt routing
[    0.248055] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.361144] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.361151] ACPI: EC: driver started in interrupt mode
[    0.361297] ACPI: Power Resource [FN00] (on)
[    0.361793] ACPI: No dock devices found.
[    0.363039] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.363055] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.363073] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.363132] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.363286] pci 0000:00:02.0: reg 10 32bit mmio: [0x58280000-0x582fffff]
[    0.363297] pci 0000:00:02.0: reg 14 io port: [0x60f0-0x60f7]
[    0.363306] pci 0000:00:02.0: reg 18 32bit mmio: [0x40000000-0x4fffffff]
[    0.363316] pci 0000:00:02.0: reg 1c 32bit mmio: [0x58300000-0x5833ffff]
[    0.363371] pci 0000:00:02.1: reg 10 32bit mmio: [0x58200000-0x5827ffff]
[    0.363511] pci 0000:00:1b.0: reg 10 64bit mmio: [0x58340000-0x58343fff]
[    0.363585] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.363593] pci 0000:00:1b.0: PME# disabled
[    0.363698] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.363706] pci 0000:00:1c.0: PME# disabled
[    0.363814] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.363822] pci 0000:00:1c.1: PME# disabled
[    0.363929] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.363937] pci 0000:00:1c.2: PME# disabled
[    0.364059] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.364068] pci 0000:00:1c.3: PME# disabled
[    0.364149] pci 0000:00:1d.0: reg 20 io port: [0x60a0-0x60bf]
[    0.364229] pci 0000:00:1d.1: reg 20 io port: [0x6080-0x609f]
[    0.364308] pci 0000:00:1d.2: reg 20 io port: [0x6060-0x607f]
[    0.364388] pci 0000:00:1d.3: reg 20 io port: [0x6040-0x605f]
[    0.364473] pci 0000:00:1d.7: reg 10 32bit mmio: [0x58344400-0x583447ff]
[    0.364547] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.364556] pci 0000:00:1d.7: PME# disabled
[    0.364760] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.364769] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.364779] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)
[    0.364788] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
[    0.364881] pci 0000:00:1f.2: reg 10 io port: [0x60d8-0x60df]
[    0.364894] pci 0000:00:1f.2: reg 14 io port: [0x60fc-0x60ff]
[    0.364906] pci 0000:00:1f.2: reg 18 io port: [0x60d0-0x60d7]
[    0.364919] pci 0000:00:1f.2: reg 1c io port: [0x60f8-0x60fb]
[    0.364931] pci 0000:00:1f.2: reg 20 io port: [0x6020-0x602f]
[    0.364944] pci 0000:00:1f.2: reg 24 32bit mmio: [0x58344000-0x583443ff]
[    0.364990] pci 0000:00:1f.2: PME# supported from D3hot
[    0.364998] pci 0000:00:1f.2: PME# disabled
[    0.365078] pci 0000:00:1f.3: reg 20 io port: [0x6000-0x601f]
[    0.365337] pci 0000:01:00.0: reg 10 64bit mmio: [0x57100000-0x57103fff]
[    0.365567] pci 0000:01:00.0: supports D1 D2
[    0.365716] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]
[    0.365725] pci 0000:00:1c.0: bridge 32bit mmio: [0x57100000-0x581fffff]
[    0.365739] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x50000000-0x50ffffff]
[    0.365812] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.365821] pci 0000:00:1c.1: bridge 32bit mmio: [0x56100000-0x570fffff]
[    0.365834] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x51000000-0x51ffffff]
[    0.365920] pci 0000:03:00.0: reg 10 64bit mmio: [0x55000000-0x5503ffff]
[    0.365935] pci 0000:03:00.0: reg 18 io port: [0x2000-0x207f]
[    0.366030] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.366040] pci 0000:03:00.0: PME# disabled
[    0.366130] pci 0000:00:1c.2: bridge io port: [0x2000-0x3fff]
[    0.366139] pci 0000:00:1c.2: bridge 32bit mmio: [0x55000000-0x560fffff]
[    0.366151] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x52000000-0x52ffffff]
[    0.366225] pci 0000:00:1c.3: bridge io port: [0x1000-0x1fff]
[    0.366233] pci 0000:00:1c.3: bridge 32bit mmio: [0x54000000-0x54ffffff]
[    0.366246] pci 0000:00:1c.3: bridge 64bit mmio pref: [0x53000000-0x53ffffff]
[    0.366323] pci 0000:00:1e.0: transparent bridge
[    0.366376] pci_bus 0000:00: on NUMA node 0
[    0.366389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.366784] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.367027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.367208] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.367389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.367758] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.367773] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.377813] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.378071] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.378327] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.378580] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.378833] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.379087] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.379343] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.379600] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.380034] SCSI subsystem initialized
[    0.380115] libata version 3.00 loaded.
[    0.380128] usbcore: registered new interface driver usbfs
[    0.380128] usbcore: registered new interface driver hub
[    0.380141] usbcore: registered new device driver usb
[    0.380246] ACPI: WMI: Mapper loaded
[    0.380252] PCI: Using ACPI for IRQ routing
[    0.392022] Bluetooth: Core ver 2.15
[    0.392067] NET: Registered protocol family 31
[    0.392067] Bluetooth: HCI device and connection manager initialized
[    0.392067] Bluetooth: HCI socket layer initialized
[    0.392067] NetLabel: Initializing
[    0.392067] NetLabel:  domain hash size = 128
[    0.392067] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.392080] NetLabel:  unlabeled traffic allowed by default
[    0.392151] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.392164] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.412028] pnp: PnP ACPI init
[    0.412069] ACPI: bus type pnp registered
[    0.476777] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.3 BAR 13 (0x1000-0x1fff), disabling
[    0.478588] pnp: PnP ACPI: found 9 devices
[    0.478595] ACPI: ACPI bus type pnp unregistered
[    0.478603] PnPBIOS: Disabled by ACPI PNP
[    0.478626] system 00:01: ioport range 0x200-0x20f has been reserved
[    0.478635] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.478642] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.478649] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.478656] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.478663] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.478671] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[    0.478680] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.478688] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.478696] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.478703] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.478711] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.478719] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.478727] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.501086] Switched to high resolution mode on CPU 1
[    0.504012] Switched to high resolution mode on CPU 0
[    0.513608] AppArmor: AppArmor Filesystem Enabled
[    0.513702] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.513710] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    0.513721] pci 0000:00:1c.0:   MEM window: 0x57100000-0x581fffff
[    0.513731] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff
[    0.513744] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.513751] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.513761] pci 0000:00:1c.1:   MEM window: 0x56100000-0x570fffff
[    0.513771] pci 0000:00:1c.1:   PREFETCH window: 0x00000051000000-0x00000051ffffff
[    0.513784] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.513791] pci 0000:00:1c.2:   IO window: 0x2000-0x3fff
[    0.513801] pci 0000:00:1c.2:   MEM window: 0x55000000-0x560fffff
[    0.513811] pci 0000:00:1c.2:   PREFETCH window: 0x00000052000000-0x00000052ffffff
[    0.513823] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.513830] pci 0000:00:1c.3:   IO window: 0x1000-0x1fff
[    0.513840] pci 0000:00:1c.3:   MEM window: 0x54000000-0x54ffffff
[    0.513850] pci 0000:00:1c.3:   PREFETCH window: 0x00000053000000-0x00000053ffffff
[    0.513862] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.513867] pci 0000:00:1e.0:   IO window: disabled
[    0.513876] pci 0000:00:1e.0:   MEM window: disabled
[    0.513884] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.513907]   alloc irq_desc for 16 on node -1
[    0.513912]   alloc kstat_irqs on node -1
[    0.513924] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.513935] pci 0000:00:1c.0: setting latency timer to 64
[    0.513950] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.513958]   alloc irq_desc for 17 on node -1
[    0.513963]   alloc kstat_irqs on node -1
[    0.513971] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.513982] pci 0000:00:1c.1: setting latency timer to 64
[    0.513996]   alloc irq_desc for 18 on node -1
[    0.514000]   alloc kstat_irqs on node -1
[    0.514008] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.514017] pci 0000:00:1c.2: setting latency timer to 64
[    0.514031] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.514038]   alloc irq_desc for 19 on node -1
[    0.514043]   alloc kstat_irqs on node -1
[    0.514051] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.514061] pci 0000:00:1c.3: setting latency timer to 64
[    0.514075] pci 0000:00:1e.0: setting latency timer to 64
[    0.514085] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.514092] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.514099] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff]
[    0.514105] pci_bus 0000:01: resource 1 mem: [0x57100000-0x581fffff]
[    0.514112] pci_bus 0000:01: resource 2 pref mem [0x50000000-0x50ffffff]
[    0.514118] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.514124] pci_bus 0000:02: resource 1 mem: [0x56100000-0x570fffff]
[    0.514131] pci_bus 0000:02: resource 2 pref mem [0x51000000-0x51ffffff]
[    0.514137] pci_bus 0000:03: resource 0 io:  [0x2000-0x3fff]
[    0.514144] pci_bus 0000:03: resource 1 mem: [0x55000000-0x560fffff]
[    0.514150] pci_bus 0000:03: resource 2 pref mem [0x52000000-0x52ffffff]
[    0.514157] pci_bus 0000:04: resource 0 io:  [0x1000-0x1fff]
[    0.514163] pci_bus 0000:04: resource 1 mem: [0x54000000-0x54ffffff]
[    0.514169] pci_bus 0000:04: resource 2 pref mem [0x53000000-0x53ffffff]
[    0.514176] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.514182] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.514256] NET: Registered protocol family 2
[    0.514463] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.515124] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.516155] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.516606] TCP: Hash tables configured (established 131072 bind 65536)
[    0.516613] TCP reno registered
[    0.516841] NET: Registered protocol family 1
[    0.516987] Trying to unpack rootfs image as initramfs...
[    0.896320] Freeing initrd memory: 7728k freed
[    0.903565] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.903574] Simple Boot Flag at 0x44 set to 0x1
[    0.903985] cpufreq-nforce2: No nForce2 chipset.
[    0.904090] Scanning for low memory corruption every 60 seconds
[    0.904302] audit: initializing netlink socket (disabled)
[    0.904331] type=2000 audit(1267261758.904:1): initialized
[    0.921749] highmem bounce pool size: 64 pages
[    0.921762] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.924970] VFS: Disk quotas dquot_6.5.2
[    0.925105] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.926361] fuse init (API version 7.12)
[    0.926540] msgmni has been set to 1732
[    0.927033] alg: No test for stdrng (krng)
[    0.927066] io scheduler noop registered
[    0.927072] io scheduler anticipatory registered
[    0.927076] io scheduler deadline registered
[    0.927183] io scheduler cfq registered (default)
[    0.927209] pci 0000:00:02.0: Boot video device
[    0.927653]   alloc irq_desc for 24 on node -1
[    0.927659]   alloc kstat_irqs on node -1
[    0.927678] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.927695] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.927915]   alloc irq_desc for 25 on node -1
[    0.927920]   alloc kstat_irqs on node -1
[    0.927935] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.927951] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.928208]   alloc irq_desc for 26 on node -1
[    0.928213]   alloc kstat_irqs on node -1
[    0.928228] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.928243] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.928458]   alloc irq_desc for 27 on node -1
[    0.928463]   alloc kstat_irqs on node -1
[    0.928478] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.928493] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.928669] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.928894] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.928911] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.929185] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.929200] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.929452] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.929466] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.929718] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.929732] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.930021] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.930035] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.930287] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.930301] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.930551] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.930565] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.930815] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.930830] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.930932] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.992179] ACPI: AC Adapter [AC] (on-line)
[    0.992331] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.992339] ACPI: Power Button [PWRF]
[    0.992440] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.992447] ACPI: Power Button [PWRB]
[    0.992545] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.992633] ACPI: Lid Switch [LID0]
[    0.992736] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    0.992744] ACPI: Sleep Button [SLPB]
[    0.993054] fan PNP0C0B:00: registered as cooling_device0
[    0.993070] ACPI: Fan [FAN] (on)
[    0.994424] ACPI: SSDT 3f5b7c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.995237] ACPI: SSDT 3f5b6e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.996978] Marking TSC unstable due to TSC halts in idle
[    0.997015] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.997065] processor LNXCPU:00: registered as cooling_device1
[    0.997074] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.997823] ACPI: SSDT 3f5b7f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.998550] ACPI: SSDT 3f5b5f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    1.000425] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.000478] processor LNXCPU:01: registered as cooling_device2
[    1.000488] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.067455] thermal LNXTHERM:01: registered as thermal_zone0
[    1.067472] ACPI: Thermal Zone [THRM] (27 C)
[    1.067613] isapnp: Scanning for PnP cards...
[    1.422039] isapnp: No Plug & Play device found
[    1.748212] ACPI: Battery Slot [BAT0] (battery present)
[    1.748518] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.751153] brd: module loaded
[    1.752182] loop: module loaded
[    1.752363] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.752537] ahci 0000:00:1f.2: version 3.0
[    1.752566] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.752627]   alloc irq_desc for 28 on node -1
[    1.752633]   alloc kstat_irqs on node -1
[    1.752652] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    1.752714] ahci: SSS flag set, parallel bus scan disabled
[    1.752764] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.752772] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
[    1.752782] ahci 0000:00:1f.2: setting latency timer to 64
[    1.753157] scsi0 : ahci
[    1.753395] scsi1 : ahci
[    1.753535] scsi2 : ahci
[    1.753688] scsi3 : ahci
[    1.754061] ata1: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344100 irq 28
[    1.754069] ata2: DUMMY
[    1.754075] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 28
[    1.754080] ata4: DUMMY
[    1.756151] Fixed MDIO Bus: probed
[    1.756237] PPP generic driver version 2.4.2
[    1.756449] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.756499] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.756530] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.756538] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.756644] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.760590] ehci_hcd 0000:00:1d.7: debug port 1
[    1.760601] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.760634] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58344400
[    1.776031] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.776194] usb usb1: configuration #1 chosen from 1 choice
[    1.776264] hub 1-0:1.0: USB hub found
[    1.776281] hub 1-0:1.0: 8 ports detected
[    1.776416] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.776459] uhci_hcd: USB Universal Host Controller Interface driver
[    1.776533] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.776547] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.776555] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.776652] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.776694] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000060a0
[    1.776891] usb usb2: configuration #1 chosen from 1 choice
[    1.776954] hub 2-0:1.0: USB hub found
[    1.776969] hub 2-0:1.0: 2 ports detected
[    1.777065] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.777078] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.777085] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.777152] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.777204] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006080
[    1.777374] usb usb3: configuration #1 chosen from 1 choice
[    1.777435] hub 3-0:1.0: USB hub found
[    1.777450] hub 3-0:1.0: 2 ports detected
[    1.777542] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.777554] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.777561] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.777628] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.777678] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006060
[    1.777848] usb usb4: configuration #1 chosen from 1 choice
[    1.777910] hub 4-0:1.0: USB hub found
[    1.777925] hub 4-0:1.0: 2 ports detected
[    1.778019] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.778031] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.778038] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.778106] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.778154] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006040
[    1.778328] usb usb5: configuration #1 chosen from 1 choice
[    1.778390] hub 5-0:1.0: USB hub found
[    1.778406] hub 5-0:1.0: 2 ports detected
[    1.778604] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.803752] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.803769] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.803937] mice: PS/2 mouse device common for all mice
[    1.804245] rtc_cmos 00:03: RTC can wake from S4
[    1.804338] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.804387] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.804645] device-mapper: uevent: version 1.0.3
[    1.804872] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.805073] device-mapper: multipath: version 1.1.0 loaded
[    1.805081] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.805388] EISA: Probing bus 0 at eisa.0
[    1.805400] Cannot allocate resource for EISA slot 1
[    1.805405] Cannot allocate resource for EISA slot 2
[    1.805410] Cannot allocate resource for EISA slot 3
[    1.805415] Cannot allocate resource for EISA slot 4
[    1.805420] Cannot allocate resource for EISA slot 5
[    1.805425] Cannot allocate resource for EISA slot 6
[    1.805440] EISA: Detected 0 cards.
[    1.805803] cpuidle: using governor ladder
[    1.806004] cpuidle: using governor menu
[    1.807113] TCP cubic registered
[    1.807483] NET: Registered protocol family 10
[    1.808457] lo: Disabled Privacy Extensions
[    1.809153] NET: Registered protocol family 17
[    1.809199] Bluetooth: L2CAP ver 2.13
[    1.809203] Bluetooth: L2CAP socket layer initialized
[    1.809210] Bluetooth: SCO (Voice Link) ver 0.6
[    1.809213] Bluetooth: SCO socket layer initialized
[    1.809315] Bluetooth: RFCOMM TTY layer initialized
[    1.809325] Bluetooth: RFCOMM socket layer initialized
[    1.809331] Bluetooth: RFCOMM ver 1.11
[    1.811256] Using IPI No-Shortcut mode
[    1.811426] PM: Resume from disk failed.
[    1.811451] registered taskstats version 1
[    1.811674]   Magic number: 14:572:172
[    1.811806] rtc_cmos 00:03: setting system clock to 2010-02-27 09:09:20 UTC (1267261760)
[    1.811814] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.811819] EDD information not available.
[    1.824096] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.072106] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.073506] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.073716] ata1.00: ATA-8: Hitachi HTS543216L9SA00, FB2OC40C, max UDMA/133
[    2.073731] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.075380] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.075660] ata1.00: configured for UDMA/133
[    2.088090] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    2.088475] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
[    2.088783] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.088902] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.089063] sd 0:0:0:0: [sda] Write Protect is off
[    2.089071] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.089141] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.089494]  sda: sda1 sda2
[    2.110874] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.394482] usb 1-2: configuration #1 chosen from 1 choice
[    2.408092] ata3: SATA link down (SStatus 0 SControl 300)
[    2.424262] Freeing unused kernel memory: 540k freed
[    2.424841] Write protecting the kernel text: 4568k
[    2.424922] Write protecting the kernel read-only data: 1836k
[    2.770668] Linux agpgart interface v0.103
[    2.793200] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    2.793554] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    2.796622] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    3.037954] acpi device:1d: registered as cooling_device3
[    3.038268] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/input/input6
[    3.038348] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[    3.084165] [drm] Initialized drm 1.1.0 20060810
[    3.114724] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.114740] i915 0000:00:02.0: setting latency timer to 64
[    3.339038] [drm] fb0: inteldrmfb frame buffer device
[    3.339058] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.666161] [drm] LVDS-8: set mode 1024x600 e
[    4.072825] Console: switching to colour frame buffer device 128x37
[    4.860030] EXT4-fs (loop0): barriers enabled
[    4.884808] kjournald2 starting: pid 362, dev loop0:8, commit interval 5 seconds
[    4.884845] EXT4-fs (loop0): delayed allocation enabled
[    4.884853] EXT4-fs: file extents enabled
[    4.892660] EXT4-fs: mballoc enabled
[    4.892707] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    5.662410] type=1505 audit(1267261764.350:2): operation="profile_load" pid=386 name=/usr/share/gdm/guest-session/Xsession
[    5.666654] type=1505 audit(1267261764.352:3): operation="profile_load" pid=387 name=/sbin/dhclient3
[    5.667340] type=1505 audit(1267261764.352:4): operation="profile_load" pid=387 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.667677] type=1505 audit(1267261764.352:5): operation="profile_load" pid=387 name=/usr/lib/connman/scripts/dhclient-script
[    5.718736] type=1505 audit(1267261764.404:6): operation="profile_load" pid=388 name=/usr/bin/evince
[    5.728299] type=1505 audit(1267261764.416:7): operation="profile_load" pid=388 name=/usr/bin/evince-previewer
[    5.733991] type=1505 audit(1267261764.420:1): operation="profile_load" pid=388 name=/usr/bin/evince-thumbnailer
[    5.759841] type=1505 audit(1267261764.444:9): operation="profile_load" pid=390 name=/usr/lib/cups/backend/cups-pdf
[    5.760644] type=1505 audit(1267261764.448:10): operation="profile_load" pid=390 name=/usr/sbin/cupsd
[    5.777378] type=1505 audit(1267261764.464:11): operation="profile_load" pid=391 name=/usr/sbin/tcpdump
[   18.382820] udev: starting version 147
[   18.452449] lp: driver loaded but no devices found
[   18.969542] Disabling lock debugging due to kernel taint
[   18.993722] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   19.002412] atl1c 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.002439] atl1c 0000:03:00.0: setting latency timer to 64
[   19.002531] atl1c 0000:03:00.0: PME# disabled
[   19.002545] atl1c 0000:03:00.0: PME# disabled
[   19.024784] intel_rng: FWH not detected
[   19.169215] Linux video capture interface: v2.00
[   19.176530] atl1c 0000:03:00.0: version 1.0.0.1-NAPI
[   19.180187] uvcvideo: Found UVC 1.00 device Webcam (04f2:b084)
[   19.255907] input: Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
[   19.256039] usbcore: registered new interface driver uvcvideo
[   19.256049] USB Video Class driver (v0.1.0)
[   19.264861] acer-wmi: Acer Laptop ACPI-WMI Extras
[   19.464233] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.493825] acer-wmi: Unable to detect available WMID devices
[   19.662202] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.662257] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.708734] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   19.708760] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   19.708802] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   19.708832] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   19.708852] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   19.708873] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   19.708894] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   19.708915] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   19.708936] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   19.708967] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   19.709040] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   19.709063] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   19.709084] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   19.709116] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   19.709137] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   19.709163] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   19.709184] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   19.709206] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   19.709236] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   19.709258] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   19.709279] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   19.709302] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   19.709328] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   19.709349] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   19.709386] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   19.709419] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   19.709440] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   19.709461] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   19.709482] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   19.709544] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   19.709566] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   19.709587] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   19.709608] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   19.709629] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   19.709636] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwl6'
[   19.710813] ndiswrapper (load_wrap_driver:10): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   19.710973] usbcore: registered new interface driver ndiswrapper
[   19.752742] hda_codec: Unknown model for ALC272, trying auto-probe from BIOS...
[   19.753655] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   20.249322] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[   20.329481] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   26.881022] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[   26.983944] EXT4-fs (loop0): internal journal on loop0:8
[   27.464552]   alloc irq_desc for 29 on node -1
[   27.464562]   alloc kstat_irqs on node -1
[   27.464597] atl1c 0000:03:00.0: irq 29 for MSI/MSI-X
[   27.464715] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   27.681245] type=1505 audit(1267279786.368:12): operation="profile_replace" pid=884 name=/usr/share/gdm/guest-session/Xsession
[   27.686021] type=1505 audit(1267279786.372:13): operation="profile_replace" pid=889 name=/sbin/dhclient3
[   27.686890] type=1505 audit(1267279786.372:14): operation="profile_replace" pid=889 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   27.687377] type=1505 audit(1267279786.372:15): operation="profile_replace" pid=889 name=/usr/lib/connman/scripts/dhclient-script
[   27.702359] type=1505 audit(1267279786.388:16): operation="profile_replace" pid=892 name=/usr/bin/evince
[   27.716704] type=1505 audit(1267279786.404:17): operation="profile_replace" pid=892 name=/usr/bin/evince-previewer
[   27.723297] type=1505 audit(1267279786.408:1): operation="profile_replace" pid=892 name=/usr/bin/evince-thumbnailer
[   27.741335] type=1505 audit(1267279786.428:19): operation="profile_replace" pid=899 name=/usr/lib/cups/backend/cups-pdf
[   27.742389] type=1505 audit(1267279786.428:20): operation="profile_replace" pid=899 name=/usr/sbin/cupsd
[   27.755172] type=1505 audit(1267279786.440:21): operation="profile_replace" pid=902 name=/usr/sbin/tcpdump
[   29.072861] ppdev: user-space parallel port driver
[   29.776502] CPU0 attaching NULL sched-domain.
[   29.776513] CPU1 attaching NULL sched-domain.
[   29.804934] CPU0 attaching sched-domain:
[   29.804944]  domain 0: span 0-1 level SIBLING
[   29.804950]   groups: 0 1
[   29.804963] CPU1 attaching sched-domain:
[   29.804968]  domain 0: span 0-1 level SIBLING
[   29.804973]   groups: 1 0
[   31.840335] CPU0 attaching NULL sched-domain.
[   31.840347] CPU1 attaching NULL sched-domain.
[   31.865109] CPU0 attaching sched-domain:
[   31.865119]  domain 0: span 0-1 level SIBLING
[   31.865125]   groups: 0 1
[   31.865137] CPU1 attaching sched-domain:
[   31.865142]  domain 0: span 0-1 level SIBLING
[   31.865148]   groups: 1 0
[   38.180071] eth0: no IPv6 routers present
[ 1151.971034] CPU0 attaching NULL sched-domain.
[ 1151.971052] CPU1 attaching NULL sched-domain.
[ 1152.000912] CPU0 attaching sched-domain:
[ 1152.000924]  domain 0: span 0-1 level SIBLING
[ 1152.000932]   groups: 0 1
[ 1152.000944]   domain 1: span 0-1 level MC
[ 1152.000952]    groups: 0-1 (__cpu_power = 204)
[ 1152.000969] CPU1 attaching sched-domain:
[ 1152.000975]  domain 0: span 0-1 level SIBLING
[ 1152.000982]   groups: 1 0
[ 1152.000993]   domain 1: span 0-1 level MC
[ 1152.001000]    groups: 0-1 (__cpu_power = 204)
[ 1235.426710] CPU0 attaching NULL sched-domain.
[ 1235.426731] CPU1 attaching NULL sched-domain.
[ 1235.444213] CPU0 attaching sched-domain:
[ 1235.444230]  domain 0: span 0-1 level SIBLING
[ 1235.444243]   groups: 0 1
[ 1235.444265] CPU1 attaching sched-domain:
[ 1235.444275]  domain 0: span 0-1 level SIBLING
[ 1235.444287]   groups: 1 0
[ 1804.403385] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Down
[ 1810.847366] CPU0 attaching NULL sched-domain.
[ 1810.847387] CPU1 attaching NULL sched-domain.
[ 1810.861260] CPU0 attaching sched-domain:
[ 1810.861277]  domain 0: span 0-1 level SIBLING
[ 1810.861291]   groups: 0 1
[ 1810.861313] CPU1 attaching sched-domain:
[ 1810.861323]  domain 0: span 0-1 level SIBLING
[ 1810.861334]   groups: 1 0
[ 1811.970183] PM: Syncing filesystems ... done.
[ 1811.982340] PM: Preparing system for mem sleep
[ 1811.982349] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 1811.983944] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 1811.984163] PM: Entering mem sleep
[ 1811.984187] Suspending console(s) (use no_console_suspend to debug)
[ 1812.000109] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 1812.168312] sd 0:0:0:0: [sda] Stopping disk
[ 1813.236876] atl1c 0000:03:00.0: PME# disabled
[ 1813.236890] atl1c 0000:03:00.0: PCI INT A disabled
[ 1813.300095] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 1813.300118] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[ 1813.300136] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 1813.300154] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 1813.300172] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 1813.404466] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 1813.447466] i915 0000:00:02.0: PCI INT A disabled
[ 1813.460401] PM: suspend devices took 1.476 seconds
[ 1813.460876] ehci_hcd 0000:00:1d.7: PME# disabled
[ 1813.476522] ACPI: Preparing to enter system sleep state S3
[ 1813.476933] Disabling non-boot CPUs ...
[ 1813.580034] CPU 1 is now offline
[ 1813.580040] SMP alternatives: switching to UP code
[ 1813.585400] CPU0 attaching NULL sched-domain.
[ 1813.585407] CPU1 attaching NULL sched-domain.
[ 1813.585423] CPU0 attaching NULL sched-domain.
[ 1813.585933] CPU1 is down
[ 1813.585951] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 1813.585951] Back to C!
[ 1813.585951] CPU0: Thermal LVT vector (0xfa) already installed
[ 1813.585951] Enabling non-boot CPUs ...
[ 1813.585951] SMP alternatives: switching to SMP code
[ 1813.591496] Booting processor 1 APIC 0x1 ip 0x6000
[ 1813.585175] Initializing CPU#1
[ 1813.585175] Calibrating delay using timer specific routine.. 3191.97 BogoMIPS (lpj=6383953)
[ 1813.585175] CPU: L1 I cache: 32K, L1 D cache: 24K
[ 1813.585175] CPU: L2 cache: 512K
[ 1813.585175] CPU: Physical Processor ID: 0
[ 1813.585175] CPU: Processor Core ID: 0
[ 1813.585175] mce: CPU supports 5 MCE banks
[ 1813.585175] CPU1: Thermal monitoring enabled (TM2)
[ 1813.585175] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[ 1813.681004] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[ 1813.681148] CPU0 attaching NULL sched-domain.
[ 1813.685021] Switched to high resolution mode on CPU 1
[ 1813.696037] CPU0 attaching sched-domain:
[ 1813.696046]  domain 0: span 0-1 level SIBLING
[ 1813.696053]   groups: 0 1
[ 1813.696064] CPU1 attaching sched-domain:
[ 1813.696071]  domain 0: span 0-1 level SIBLING
[ 1813.696077]   groups: 1 0
[ 1813.700045] CPU1 is up
[ 1813.700053] ACPI: Waking up from system sleep state S3
[ 1813.700372] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0x58340004)
[ 1813.700389] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 1813.700449] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20005050, writing 0x5050)
[ 1813.700470] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 1813.700551] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20004040, writing 0x4040)
[ 1813.700573] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 1813.700662] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 1813.700741] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20001010, writing 0x1010)
[ 1813.700763] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 1813.700840] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 1813.700887] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 1813.700933] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 1813.700979] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 1813.701041] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 1813.701070] ehci_hcd 0000:00:1d.7: PME# disabled
[ 1813.701089] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
[ 1813.701108] pci 0000:00:1e.0: restoring config space at offset 0xa (was 0x0, writing 0xffffffff)
[ 1813.701224] ahci 0000:00:1f.2: restoring config space at offset 0x9 (was 0x58340000, writing 0x58344000)
[ 1813.701249] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 1814.500077] Clocksource tsc unstable (delta = -500005429 ns)
[ 1815.549199] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1815.549209] i915 0000:00:02.0: setting latency timer to 64
[ 1815.610488] [drm] LVDS-8: set mode 1024x600 e
[ 1815.630545] pci 0000:00:02.1: PME# disabled
[ 1815.630562] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1815.630573] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 1815.630617] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1815.630627] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1815.630656] usb usb2: root hub lost power or was reset
[ 1815.630683] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 1815.630693] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 1815.630721] usb usb3: root hub lost power or was reset
[ 1815.630747] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 1815.630757] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 1815.630786] usb usb4: root hub lost power or was reset
[ 1815.630812] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[ 1815.630822] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 1815.630851] usb usb5: root hub lost power or was reset
[ 1815.630877] ehci_hcd 0000:00:1d.7: PME# disabled
[ 1815.630885] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1815.630895] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 1815.630940] pci 0000:00:1e.0: setting latency timer to 64
[ 1815.630959] ahci 0000:00:1f.2: setting latency timer to 64
[ 1815.631094] pci 0000:01:00.0: PME# disabled
[ 1815.631107] atl1c 0000:03:00.0: PME# disabled
[ 1815.631116] atl1c 0000:03:00.0: PME# disabled
[ 1815.840873] sd 0:0:0:0: [sda] Starting disk
[ 1815.948093] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1815.949098] ata3: SATA link down (SStatus 0 SControl 300)
[ 1815.949500] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[ 1815.963754] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[ 1815.964138] ata1.00: configured for UDMA/133
[ 1816.116087] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[ 1816.389359] PM: resume devices took 2.688 seconds
[ 1816.389415] PM: Finishing wakeup.
[ 1816.389419] Restarting tasks ... done.
[ 1816.697167] atl1c 0000:03:00.0: irq 29 for MSI/MSI-X
[ 1816.697923] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1817.539953] CPU0 attaching NULL sched-domain.
[ 1817.539968] CPU1 attaching NULL sched-domain.
[ 1817.552233] CPU0 attaching sched-domain:
[ 1817.552246]  domain 0: span 0-1 level SIBLING
[ 1817.552256]   groups: 0 1
[ 1817.552273] CPU1 attaching sched-domain:
[ 1817.552280]  domain 0: span 0-1 level SIBLING
[ 1817.552289]   groups: 1 0
[ 2895.557790] CPU0 attaching NULL sched-domain.
[ 2895.557802] CPU1 attaching NULL sched-domain.
[ 2895.572216] CPU0 attaching sched-domain:
[ 2895.572233]  domain 0: span 0-1 level SIBLING
[ 2895.572246]   groups: 0 1
[ 2895.572267] CPU1 attaching sched-domain:
[ 2895.572277]  domain 0: span 0-1 level SIBLING
[ 2895.572288]   groups: 1 0
[ 2896.072210] PM: Syncing filesystems ... done.
[ 2896.083759] PM: Preparing system for mem sleep
[ 2896.083768] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 2896.085346] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 2896.085522] PM: Entering mem sleep
[ 2896.085546] Suspending console(s) (use no_console_suspend to debug)
[ 2896.104087] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2896.289170] sd 0:0:0:0: [sda] Stopping disk
[ 2897.357313] atl1c 0000:03:00.0: PME# disabled
[ 2897.420093] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 2897.420116] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[ 2897.420135] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 2897.420153] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 2897.420171] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 2897.524470] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 2897.555352] i915 0000:00:02.0: PCI INT A disabled
[ 2897.568398] PM: suspend devices took 1.484 seconds
[ 2897.568871] ehci_hcd 0000:00:1d.7: PME# disabled
[ 2897.584507] ACPI: Preparing to enter system sleep state S3
[ 2897.584912] Disabling non-boot CPUs ...
[ 2897.688035] CPU 1 is now offline
[ 2897.688041] SMP alternatives: switching to UP code
[ 2897.693362] CPU0 attaching NULL sched-domain.
[ 2897.693370] CPU1 attaching NULL sched-domain.
[ 2897.693383] CPU0 attaching NULL sched-domain.
[ 2897.693885] CPU1 is down
[ 2897.693904] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 2897.693904] Back to C!
[ 2897.693904] CPU0: Thermal LVT vector (0xfa) already installed
[ 2897.693904] Enabling non-boot CPUs ...
[ 2897.693904] SMP alternatives: switching to SMP code
[ 2897.699443] Booting processor 1 APIC 0x1 ip 0x6000
[ 2897.693139] Initializing CPU#1
[ 2897.693139] Calibrating delay using timer specific routine.. 3192.00 BogoMIPS (lpj=6384015)
[ 2897.693139] CPU: L1 I cache: 32K, L1 D cache: 24K
[ 2897.693139] CPU: L2 cache: 512K
[ 2897.693139] CPU: Physical Processor ID: 0
[ 2897.693139] CPU: Processor Core ID: 0
[ 2897.693139] mce: CPU supports 5 MCE banks
[ 2897.693139] CPU1: Thermal monitoring enabled (TM2)
[ 2897.693139] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[ 2897.789003] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[ 2897.789147] CPU0 attaching NULL sched-domain.
[ 2897.793021] Switched to high resolution mode on CPU 1
[ 2897.804037] CPU0 attaching sched-domain:
[ 2897.804045]  domain 0: span 0-1 level SIBLING
[ 2897.804052]   groups: 0 1
[ 2897.804064] CPU1 attaching sched-domain:
[ 2897.804070]  domain 0: span 0-1 level SIBLING
[ 2897.804077]   groups: 1 0
[ 2897.808040] CPU1 is up
[ 2897.808048] ACPI: Waking up from system sleep state S3
[ 2897.808365] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0x58340004)
[ 2897.808382] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 2897.808453] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 2897.808544] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 2897.808633] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 2897.808722] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 2897.808799] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 2897.808846] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 2897.808892] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 2897.808938] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 2897.808994] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 2897.809029] ehci_hcd 0000:00:1d.7: PME# disabled
[ 2897.809048] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
[ 2897.809067] pci 0000:00:1e.0: restoring config space at offset 0xa (was 0x0, writing 0xffffffff)
[ 2897.809182] ahci 0000:00:1f.2: restoring config space at offset 0x9 (was 0x58340000, writing 0x58344000)
[ 2897.809207] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 2899.656969] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2899.656979] i915 0000:00:02.0: setting latency timer to 64
[ 2899.718288] [drm] LVDS-8: set mode 1024x600 e
[ 2899.738409] pci 0000:00:02.1: PME# disabled
[ 2899.738427] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2899.738438] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 2899.738482] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2899.738493] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2899.738523] usb usb2: root hub lost power or was reset
[ 2899.738550] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2899.738560] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2899.738589] usb usb3: root hub lost power or was reset
[ 2899.738615] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 2899.738625] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 2899.738653] usb usb4: root hub lost power or was reset
[ 2899.738678] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[ 2899.738688] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 2899.738716] usb usb5: root hub lost power or was reset
[ 2899.738741] ehci_hcd 0000:00:1d.7: PME# disabled
[ 2899.738749] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2899.738759] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 2899.738804] pci 0000:00:1e.0: setting latency timer to 64
[ 2899.738823] ahci 0000:00:1f.2: setting latency timer to 64
[ 2899.738958] pci 0000:01:00.0: PME# disabled
[ 2899.738971] atl1c 0000:03:00.0: PME# disabled
[ 2899.738980] atl1c 0000:03:00.0: PME# disabled
[ 2899.949983] sd 0:0:0:0: [sda] Starting disk
[ 2900.056092] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2900.057098] ata3: SATA link down (SStatus 0 SControl 300)
[ 2900.057499] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[ 2900.068753] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[ 2900.069113] ata1.00: configured for UDMA/133
[ 2900.208086] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[ 2900.481360] PM: resume devices took 2.672 seconds
[ 2900.481413] PM: Finishing wakeup.
[ 2900.481417] Restarting tasks ... done.
[ 2900.613647] atl1c 0000:03:00.0: irq 29 for MSI/MSI-X
[ 2900.614418] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2901.525263] CPU0 attaching NULL sched-domain.
[ 2901.525280] CPU1 attaching NULL sched-domain.
[ 2901.545197] CPU0 attaching sched-domain:
[ 2901.545209]  domain 0: span 0-1 level SIBLING
[ 2901.545217]   groups: 0 1
[ 2901.545232]   domain 1: span 0-1 level MC
[ 2901.545240]    groups: 0-1 (__cpu_power = 204)
[ 2901.545255] CPU1 attaching sched-domain:
[ 2901.545262]  domain 0: span 0-1 level SIBLING
[ 2901.545270]   groups: 1 0
[ 2901.545282]   domain 1: span 0-1 level MC
[ 2901.545289]    groups: 0-1 (__cpu_power = 204)
[ 2902.091856] CPU0 attaching NULL sched-domain.
[ 2902.091869] CPU1 attaching NULL sched-domain.
[ 2902.108232] CPU0 attaching sched-domain:
[ 2902.108248]  domain 0: span 0-1 level SIBLING
[ 2902.108262]   groups: 0 1
[ 2902.108282]   domain 1: span 0-1 level MC
[ 2902.108293]    groups: 0-1 (__cpu_power = 204)
[ 2902.108317] CPU1 attaching sched-domain:
[ 2902.108328]  domain 0: span 0-1 level SIBLING
[ 2902.108340]   groups: 1 0
[ 2902.108359]   domain 1: span 0-1 level MC
[ 2902.108370]    groups: 0-1 (__cpu_power = 204)
[ 3343.731236] CPU0 attaching NULL sched-domain.
[ 3343.731248] CPU1 attaching NULL sched-domain.
[ 3343.745215] CPU0 attaching sched-domain:
[ 3343.745230]  domain 0: span 0-1 level SIBLING
[ 3343.745243]   groups: 0 1
[ 3343.745264] CPU1 attaching sched-domain:
[ 3343.745275]  domain 0: span 0-1 level SIBLING
[ 3343.745286]   groups: 1 0
[ 3344.091719] PM: Syncing filesystems ... done.
[ 3344.103542] PM: Preparing system for mem sleep
[ 3344.103551] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 3344.105111] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 3344.105289] PM: Entering mem sleep
[ 3344.105313] Suspending console(s) (use no_console_suspend to debug)
[ 3344.124090] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 3344.751411] sd 0:0:0:0: [sda] Stopping disk
[ 3345.821347] atl1c 0000:03:00.0: PME# disabled
[ 3345.884097] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 3345.884120] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[ 3345.884138] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 3345.884156] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 3345.884174] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 3345.988454] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 3346.017967] i915 0000:00:02.0: PCI INT A disabled
[ 3346.032400] PM: suspend devices took 1.928 seconds
[ 3346.032873] ehci_hcd 0000:00:1d.7: PME# disabled
[ 3346.048507] ACPI: Preparing to enter system sleep state S3
[ 3346.048913] Disabling non-boot CPUs ...
[ 3346.152034] CPU 1 is now offline
[ 3346.152040] SMP alternatives: switching to UP code
[ 3346.157373] CPU0 attaching NULL sched-domain.
[ 3346.157381] CPU1 attaching NULL sched-domain.
[ 3346.157394] CPU0 attaching NULL sched-domain.
[ 3346.157924] CPU1 is down
[ 3346.157943] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 3346.157943] Back to C!
[ 3346.157943] CPU0: Thermal LVT vector (0xfa) already installed
[ 3346.157943] Enabling non-boot CPUs ...
[ 3346.157943] SMP alternatives: switching to SMP code
[ 3346.163482] Booting processor 1 APIC 0x1 ip 0x6000
[ 3346.157145] Initializing CPU#1
[ 3346.157145] Calibrating delay using timer specific routine.. 3192.00 BogoMIPS (lpj=6384000)
[ 3346.157145] CPU: L1 I cache: 32K, L1 D cache: 24K
[ 3346.157145] CPU: L2 cache: 512K
[ 3346.157145] CPU: Physical Processor ID: 0
[ 3346.157145] CPU: Processor Core ID: 0
[ 3346.157145] mce: CPU supports 5 MCE banks
[ 3346.157145] CPU1: Thermal monitoring enabled (TM2)
[ 3346.157145] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[ 3346.253060] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[ 3346.253204] CPU0 attaching NULL sched-domain.
[ 3346.257021] Switched to high resolution mode on CPU 1
[ 3346.268038] CPU0 attaching sched-domain:
[ 3346.268046]  domain 0: span 0-1 level SIBLING
[ 3346.268053]   groups: 0 1
[ 3346.268065] CPU1 attaching sched-domain:
[ 3346.268071]  domain 0: span 0-1 level SIBLING
[ 3346.268078]   groups: 1 0
[ 3346.272040] CPU1 is up
[ 3346.272047] ACPI: Waking up from system sleep state S3
[ 3346.272368] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0x58340004)
[ 3346.272385] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 3346.272455] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 3346.272546] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 3346.272635] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 3346.272724] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 3346.272801] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 3346.272848] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 3346.272893] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 3346.272939] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 3346.272995] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 3346.273029] ehci_hcd 0000:00:1d.7: PME# disabled
[ 3346.273049] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
[ 3346.273068] pci 0000:00:1e.0: restoring config space at offset 0xa (was 0x0, writing 0xffffffff)
[ 3346.273183] ahci 0000:00:1f.2: restoring config space at offset 0x9 (was 0x58340000, writing 0x58344000)
[ 3346.273208] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 3348.121874] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3348.121883] i915 0000:00:02.0: setting latency timer to 64
[ 3348.183193] [drm] LVDS-8: set mode 1024x600 e
[ 3348.203340] pci 0000:00:02.1: PME# disabled
[ 3348.203357] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3348.203368] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 3348.203413] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3348.203423] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 3348.203454] usb usb2: root hub lost power or was reset
[ 3348.203482] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 3348.203492] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 3348.203519] usb usb3: root hub lost power or was reset
[ 3348.203544] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 3348.203554] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 3348.203584] usb usb4: root hub lost power or was reset
[ 3348.203609] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[ 3348.203619] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 3348.203647] usb usb5: root hub lost power or was reset
[ 3348.203672] ehci_hcd 0000:00:1d.7: PME# disabled
[ 3348.203680] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3348.203690] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 3348.203736] pci 0000:00:1e.0: setting latency timer to 64
[ 3348.203755] ahci 0000:00:1f.2: setting latency timer to 64
[ 3348.203890] pci 0000:01:00.0: PME# disabled
[ 3348.203903] atl1c 0000:03:00.0: PME# disabled
[ 3348.203913] atl1c 0000:03:00.0: PME# disabled
[ 3348.413407] sd 0:0:0:0: [sda] Starting disk
[ 3348.520093] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 3348.521098] ata3: SATA link down (SStatus 0 SControl 300)
[ 3348.521510] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[ 3348.539088] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[ 3348.539432] ata1.00: configured for UDMA/133
[ 3348.680085] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[ 3348.953481] PM: resume devices took 2.680 seconds
[ 3348.953535] PM: Finishing wakeup.
[ 3348.953539] Restarting tasks ... done.
[ 3349.122269] atl1c 0000:03:00.0: irq 29 for MSI/MSI-X
[ 3349.123025] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3349.974170] CPU0 attaching NULL sched-domain.
[ 3349.974184] CPU1 attaching NULL sched-domain.
[ 3349.993238] CPU0 attaching sched-domain:
[ 3349.993254]  domain 0: span 0-1 level SIBLING
[ 3349.993268]   groups: 0 1
[ 3349.993287]   domain 1: span 0-1 level MC
[ 3349.993298]    groups: 0-1 (__cpu_power = 204)
[ 3349.993320] CPU1 attaching sched-domain:
[ 3349.993330]  domain 0: span 0-1 level SIBLING
[ 3349.993341]   groups: 1 0
[ 3349.993358]   domain 1: span 0-1 level MC
[ 3349.993369]    groups: 0-1 (__cpu_power = 204)
[ 3382.592113] usb 1-1: new high speed USB device using ehci_hcd and address 3
[ 3382.725868] usb 1-1: configuration #1 chosen from 1 choice
[ 3383.211609] Initializing USB Mass Storage driver...
[ 3383.212493] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3383.212862] usb-storage: device found at 3
[ 3383.212869] usb-storage: waiting for device to settle before scanning
[ 3383.212901] usbcore: registered new interface driver usb-storage
[ 3383.212909] USB Mass Storage support registered.
[ 3388.208405] usb-storage: device scan complete
[ 3388.209318] scsi 4:0:0:0: Direct-Access     pqi      IntelligentStick 0.00 PQ: 0 ANSI: 2
[ 3388.211223] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 3388.225532] sd 4:0:0:0: [sdb] 7892040 512-byte logical blocks: (4.04 GB/3.76 GiB)
[ 3388.227630] sd 4:0:0:0: [sdb] Write Protect is off
[ 3388.227644] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3388.227652] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3388.236649] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3388.236668]  sdb:
[ 3388.889219] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3388.889248] sd 4:0:0:0: [sdb] Attached SCSI removable disk


([COLOR=Red]hint[/COLOR]) the same as in (4)

**6 ) Network configuration**
     Code:
     $ sudo lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:57100000-57103fff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:51:4d:42
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:55000000-5503ffff ioport:2000(size=12)


**7 ) Scan for networks:**
     Code:
     $ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.



([COLOR=Red]hint[/COLOR]) the same as in (3)
     Code:
     $ iwlist scan wlan0 
**8 ) Ubuntu Version: **
     Code:
     $ lsb_release -d 
**9 ) Kernel/architecture (including 32 vs. 64 bit): **
     Code:
     $ uname -mr
2.6.31-19-generic i686


**10 ) Restarting the network:**
     Code:
     $ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
   ...done.

---

