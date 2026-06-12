---
title: "Network crashes shell"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by Jack_Simth on 2010-02-11
Hey all,
I've got an Aspire One Netbook (Acer, model number KAV60) on which I've installed Ubuntu - and the wireless network seems to be locking up the shell (taking a lot of programs down with it, including the network - which makes the automated reporting software ... rather difficult to use) after a while (if I start scp from the local network, I get about 150 MiB downloaded).  I'm pretty sure it's not the hardware, as the Windows XP partition I've left on the box until I've got Ubuntu working reliably doesn't have this problem.  Obviously, I can't run any particular tests once the shell has crashed, so all the info below is from prior to the regularly-scheduled network crash.  What all do you need from me to troubleshoot?

Oh, and per the "HOWTO post a Wireless issue (ticket)" thread ([http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)), some answers:
```

1) Machine Brand / Model: Acer, model number KAV60, Netbook (very small laptop)
2 ) Wireless Brand, Model and Wireless Chipset:
lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b084 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

3 ) check interface:
ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:26:22:5a:ee:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 0c:60:76:0b:06:05  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe0b:605/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16303 (16.3 KB)  TX bytes:6914 (6.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 0C-60-76-0B-06-05-30-62-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig:
wlan0     IEEE 802.11bgn  ESSID:"Phule"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:DF:4F:9F:D4   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4 ) Check for modules:
lsmod
Module                  Size  Used by
cbc                     3516  165 
aes_i586                8124  166 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
dm_crypt               12928  0 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1660  2 
snd_seq_dummy           2656  0 
ecb                     2524  3 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               59080  0 
ath9k                 258744  0 
mac80211              181140  1 ath9k
ath                     8060  1 ath9k
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               4096  1 ath9k
psmouse                56500  0 
serio_raw               5280  0 
atl1c                  30880  0 
cfg80211               93052  3 ath9k,mac80211,ath
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
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

5 ) Kernel boot messages
dmesg: 
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
[    0.000000] RAMDISK: 2f0ba000 - 2f858646
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
[    0.000000]   #4 [002f0ba000 - 002f858646]          RAMDISK ==> [002f0ba000 - 002f858646]
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
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=053abf82-0b6e-46f2-bb5b-aa6855a8f652 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5196800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f700)
[    0.000000] Memory: 1007960k/1039360k available (4567k kernel code, 29816k reserved, 2141k data, 540k init, 129368k highmem)
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
[    0.000000] Detected 1595.872 MHz processor.
[    0.001885] Console: colour VGA+ 80x25
[    0.001891] console [tty0] enabled
[    0.002143] hpet clockevent registered
[    0.002151] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002162] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.74 BogoMIPS (lpj=6383488)
[    0.002199] Security Framework initialized
[    0.002239] AppArmor: AppArmor initialized
[    0.002253] Mount-cache hash table entries: 512
[    0.002487] Initializing cgroup subsys ns
[    0.002496] Initializing cgroup subsys cpuacct
[    0.002505] Initializing cgroup subsys memory
[    0.002519] Initializing cgroup subsys freezer
[    0.002524] Initializing cgroup subsys net_cls
[    0.002550] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.002556] CPU: L2 cache: 512K
[    0.002561] CPU: Physical Processor ID: 0
[    0.002565] CPU: Processor Core ID: 0
[    0.002573] mce: CPU supports 5 MCE banks
[    0.002587] CPU0: Thermal monitoring enabled (TM2)
[    0.002595] using mwait in idle threads.
[    0.002607] Performance Counters: Atom events, Intel PMU driver.
[    0.002622] ... version:                 3
[    0.002626] ... bit width:               40
[    0.002630] ... generic counters:        2
[    0.002635] ... value mask:              000000ffffffffff
[    0.002639] ... max period:              000000007fffffff
[    0.002644] ... fixed-purpose counters:  3
[    0.002648] ... counter mask:            0000000700000003
[    0.002658] Checking 'hlt' instruction... OK.
[    0.020015] ACPI: Core revision 20090521
[    0.040506] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.082257] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3191.92 BogoMIPS (lpj=6383857)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.169005] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.169040] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.172051] Brought up 2 CPUs
[    0.172058] Total of 2 processors activated (6383.67 BogoMIPS).
[    0.172125] CPU0 attaching sched-domain:
[    0.172132]  domain 0: span 0-1 level SIBLING
[    0.172138]   groups: 0 1
[    0.172148] CPU1 attaching sched-domain:
[    0.172153]  domain 0: span 0-1 level SIBLING
[    0.172159]   groups: 1 0
[    0.172312] Booting paravirtualized kernel on bare hardware
[    0.172478] regulator: core version 0.5
[    0.172478] Time: 17:56:09  Date: 02/11/10
[    0.172478] NET: Registered protocol family 16
[    0.172478] EISA bus registered
[    0.172478] ACPI: bus type pci registered
[    0.172598] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.172605] PCI: MCFG area at e0000000 reserved in E820
[    0.172609] PCI: Using MMCONFIG for extended config space
[    0.172614] PCI: Using configuration type 1 for base access
[    0.176983] bio: create slab <bio-0> at 0
[    0.177880] ACPI: EC: Look up EC in DSDT
[    0.215622] ACPI: BIOS _OSI(Linux) query ignored
[    0.216673] ACPI: Interpreter enabled
[    0.216682] ACPI: (supports S0 S3 S4 S5)
[    0.216734] ACPI: Using IOAPIC for interrupt routing
[    0.248054] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.361053] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.361059] ACPI: EC: driver started in interrupt mode
[    0.361212] ACPI: Power Resource [FN00] (on)
[    0.361704] ACPI: No dock devices found.
[    0.362954] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.362970] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.362988] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.363047] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.363199] pci 0000:00:02.0: reg 10 32bit mmio: [0x58280000-0x582fffff]
[    0.363210] pci 0000:00:02.0: reg 14 io port: [0x60f0-0x60f7]
[    0.363219] pci 0000:00:02.0: reg 18 32bit mmio: [0x40000000-0x4fffffff]
[    0.363229] pci 0000:00:02.0: reg 1c 32bit mmio: [0x58300000-0x5833ffff]
[    0.363283] pci 0000:00:02.1: reg 10 32bit mmio: [0x58200000-0x5827ffff]
[    0.363424] pci 0000:00:1b.0: reg 10 64bit mmio: [0x58340000-0x58343fff]
[    0.363497] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.363507] pci 0000:00:1b.0: PME# disabled
[    0.363611] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.363620] pci 0000:00:1c.0: PME# disabled
[    0.363726] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.363735] pci 0000:00:1c.1: PME# disabled
[    0.363841] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.363850] pci 0000:00:1c.2: PME# disabled
[    0.363956] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.363964] pci 0000:00:1c.3: PME# disabled
[    0.364063] pci 0000:00:1d.0: reg 20 io port: [0x60a0-0x60bf]
[    0.364143] pci 0000:00:1d.1: reg 20 io port: [0x6080-0x609f]
[    0.364223] pci 0000:00:1d.2: reg 20 io port: [0x6060-0x607f]
[    0.364302] pci 0000:00:1d.3: reg 20 io port: [0x6040-0x605f]
[    0.364386] pci 0000:00:1d.7: reg 10 32bit mmio: [0x58344400-0x583447ff]
[    0.364461] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.364470] pci 0000:00:1d.7: PME# disabled
[    0.364671] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.364680] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.364691] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)
[    0.364700] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
[    0.364793] pci 0000:00:1f.2: reg 10 io port: [0x60d8-0x60df]
[    0.364805] pci 0000:00:1f.2: reg 14 io port: [0x60fc-0x60ff]
[    0.364818] pci 0000:00:1f.2: reg 18 io port: [0x60d0-0x60d7]
[    0.364830] pci 0000:00:1f.2: reg 1c io port: [0x60f8-0x60fb]
[    0.364843] pci 0000:00:1f.2: reg 20 io port: [0x6020-0x602f]
[    0.364855] pci 0000:00:1f.2: reg 24 32bit mmio: [0x58344000-0x583443ff]
[    0.364901] pci 0000:00:1f.2: PME# supported from D3hot
[    0.364909] pci 0000:00:1f.2: PME# disabled
[    0.364987] pci 0000:00:1f.3: reg 20 io port: [0x6000-0x601f]
[    0.365116] pci 0000:01:00.0: reg 10 64bit mmio: [0x57100000-0x5710ffff]
[    0.365218] pci 0000:01:00.0: supports D1
[    0.365224] pci 0000:01:00.0: PME# supported from D0 D1 D3hot
[    0.365233] pci 0000:01:00.0: PME# disabled
[    0.365329] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]
[    0.365338] pci 0000:00:1c.0: bridge 32bit mmio: [0x57100000-0x581fffff]
[    0.365351] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x50000000-0x50ffffff]
[    0.365425] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.365434] pci 0000:00:1c.1: bridge 32bit mmio: [0x56100000-0x570fffff]
[    0.365447] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x51000000-0x51ffffff]
[    0.365533] pci 0000:03:00.0: reg 10 64bit mmio: [0x55000000-0x5503ffff]
[    0.365549] pci 0000:03:00.0: reg 18 io port: [0x2000-0x207f]
[    0.365644] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.365654] pci 0000:03:00.0: PME# disabled
[    0.365743] pci 0000:00:1c.2: bridge io port: [0x2000-0x3fff]
[    0.365752] pci 0000:00:1c.2: bridge 32bit mmio: [0x55000000-0x560fffff]
[    0.365765] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x52000000-0x52ffffff]
[    0.365838] pci 0000:00:1c.3: bridge io port: [0x1000-0x1fff]
[    0.365847] pci 0000:00:1c.3: bridge 32bit mmio: [0x54000000-0x54ffffff]
[    0.365860] pci 0000:00:1c.3: bridge 64bit mmio pref: [0x53000000-0x53ffffff]
[    0.365937] pci 0000:00:1e.0: transparent bridge
[    0.365990] pci_bus 0000:00: on NUMA node 0
[    0.366002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.366397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.366640] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.366820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.367002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.367372] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.367387] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.377382] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.377640] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.377893] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.378144] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.378397] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.378654] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.378908] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.379162] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.379588] SCSI subsystem initialized
[    0.379670] libata version 3.00 loaded.
[    0.379670] usbcore: registered new interface driver usbfs
[    0.379670] usbcore: registered new interface driver hub
[    0.380040] usbcore: registered new device driver usb
[    0.380246] ACPI: WMI: Mapper loaded
[    0.380252] PCI: Using ACPI for IRQ routing
[    0.392022] Bluetooth: Core ver 2.15
[    0.392067] NET: Registered protocol family 31
[    0.392067] Bluetooth: HCI device and connection manager initialized
[    0.392067] Bluetooth: HCI socket layer initialized
[    0.392067] NetLabel: Initializing
[    0.392067] NetLabel:  domain hash size = 128
[    0.392067] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.392081] NetLabel:  unlabeled traffic allowed by default
[    0.392152] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.392165] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.412027] pnp: PnP ACPI init
[    0.412067] ACPI: bus type pnp registered
[    0.476763] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.3 BAR 13 (0x1000-0x1fff), disabling
[    0.478517] pnp: PnP ACPI: found 9 devices
[    0.478523] ACPI: ACPI bus type pnp unregistered
[    0.478531] PnPBIOS: Disabled by ACPI PNP
[    0.478554] system 00:01: ioport range 0x200-0x20f has been reserved
[    0.478562] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.478569] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.478576] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.478583] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.478591] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.478598] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[    0.478607] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.478615] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.478622] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.478630] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.478638] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.478646] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.478653] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.501085] Switched to high resolution mode on CPU 1
[    0.504003] Switched to high resolution mode on CPU 0
[    0.513530] AppArmor: AppArmor Filesystem Enabled
[    0.513625] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.513633] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    0.513644] pci 0000:00:1c.0:   MEM window: 0x57100000-0x581fffff
[    0.513653] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff
[    0.513667] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.513675] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.513685] pci 0000:00:1c.1:   MEM window: 0x56100000-0x570fffff
[    0.513694] pci 0000:00:1c.1:   PREFETCH window: 0x00000051000000-0x00000051ffffff
[    0.513708] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.513715] pci 0000:00:1c.2:   IO window: 0x2000-0x3fff
[    0.513725] pci 0000:00:1c.2:   MEM window: 0x55000000-0x560fffff
[    0.513734] pci 0000:00:1c.2:   PREFETCH window: 0x00000052000000-0x00000052ffffff
[    0.513747] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.513754] pci 0000:00:1c.3:   IO window: 0x1000-0x1fff
[    0.513765] pci 0000:00:1c.3:   MEM window: 0x54000000-0x54ffffff
[    0.513774] pci 0000:00:1c.3:   PREFETCH window: 0x00000053000000-0x00000053ffffff
[    0.513787] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.513791] pci 0000:00:1e.0:   IO window: disabled
[    0.513800] pci 0000:00:1e.0:   MEM window: disabled
[    0.513808] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.513832]   alloc irq_desc for 16 on node -1
[    0.513838]   alloc kstat_irqs on node -1
[    0.513849] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.513859] pci 0000:00:1c.0: setting latency timer to 64
[    0.513874] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.513881]   alloc irq_desc for 17 on node -1
[    0.513886]   alloc kstat_irqs on node -1
[    0.513894] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.513905] pci 0000:00:1c.1: setting latency timer to 64
[    0.513919]   alloc irq_desc for 18 on node -1
[    0.513923]   alloc kstat_irqs on node -1
[    0.513931] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.513940] pci 0000:00:1c.2: setting latency timer to 64
[    0.513954] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.513961]   alloc irq_desc for 19 on node -1
[    0.513966]   alloc kstat_irqs on node -1
[    0.513974] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.513984] pci 0000:00:1c.3: setting latency timer to 64
[    0.513998] pci 0000:00:1e.0: setting latency timer to 64
[    0.514008] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.514014] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.514021] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff]
[    0.514028] pci_bus 0000:01: resource 1 mem: [0x57100000-0x581fffff]
[    0.514034] pci_bus 0000:01: resource 2 pref mem [0x50000000-0x50ffffff]
[    0.514041] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.514047] pci_bus 0000:02: resource 1 mem: [0x56100000-0x570fffff]
[    0.514053] pci_bus 0000:02: resource 2 pref mem [0x51000000-0x51ffffff]
[    0.514060] pci_bus 0000:03: resource 0 io:  [0x2000-0x3fff]
[    0.514066] pci_bus 0000:03: resource 1 mem: [0x55000000-0x560fffff]
[    0.514072] pci_bus 0000:03: resource 2 pref mem [0x52000000-0x52ffffff]
[    0.514079] pci_bus 0000:04: resource 0 io:  [0x1000-0x1fff]
[    0.514085] pci_bus 0000:04: resource 1 mem: [0x54000000-0x54ffffff]
[    0.514092] pci_bus 0000:04: resource 2 pref mem [0x53000000-0x53ffffff]
[    0.514098] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.514104] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.514179] NET: Registered protocol family 2
[    0.514384] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.515045] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.516077] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.516529] TCP: Hash tables configured (established 131072 bind 65536)
[    0.516536] TCP reno registered
[    0.516759] NET: Registered protocol family 1
[    0.516909] Trying to unpack rootfs image as initramfs...
[    0.892203] Freeing initrd memory: 7801k freed
[    0.899518] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.899528] Simple Boot Flag at 0x44 set to 0x1
[    0.899938] cpufreq-nforce2: No nForce2 chipset.
[    0.899997] Scanning for low memory corruption every 60 seconds
[    0.900261] audit: initializing netlink socket (disabled)
[    0.900288] type=2000 audit(1265910968.900:1): initialized
[    0.917701] highmem bounce pool size: 64 pages
[    0.917714] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.920909] VFS: Disk quotas dquot_6.5.2
[    0.921046] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.922298] fuse init (API version 7.12)
[    0.922479] msgmni has been set to 1732
[    0.922971] alg: No test for stdrng (krng)
[    0.923004] io scheduler noop registered
[    0.923009] io scheduler anticipatory registered
[    0.923014] io scheduler deadline registered
[    0.923117] io scheduler cfq registered (default)
[    0.923141] pci 0000:00:02.0: Boot video device
[    0.923584]   alloc irq_desc for 24 on node -1
[    0.923590]   alloc kstat_irqs on node -1
[    0.923611] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.923628] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.923846]   alloc irq_desc for 25 on node -1
[    0.923851]   alloc kstat_irqs on node -1
[    0.923866] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.923882] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.924154]   alloc irq_desc for 26 on node -1
[    0.924159]   alloc kstat_irqs on node -1
[    0.924174] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.924190] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.924404]   alloc irq_desc for 27 on node -1
[    0.924409]   alloc kstat_irqs on node -1
[    0.924424] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.924439] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.924615] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.924838] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.924854] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.925135] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.925149] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.925406] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.925420] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.925673] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.925687] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.925979] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.925993] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.926249] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.926263] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.926516] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.926531] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.926783] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.926797] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a80), AE_ALREADY_EXISTS
[    0.926899] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.988182] ACPI: AC Adapter [AC] (off-line)
[    0.988336] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.988345] ACPI: Power Button [PWRF]
[    0.988446] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.988453] ACPI: Power Button [PWRB]
[    0.988550] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.988635] ACPI: Lid Switch [LID0]
[    0.988738] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    0.988745] ACPI: Sleep Button [SLPB]
[    0.989057] fan PNP0C0B:00: registered as cooling_device0
[    0.989074] ACPI: Fan [FAN] (on)
[    0.990445] ACPI: SSDT 3f5b7c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.991265] ACPI: SSDT 3f5b6e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.992963] Marking TSC unstable due to TSC halts in idle
[    0.993006] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.993061] processor LNXCPU:00: registered as cooling_device1
[    0.993070] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.993804] ACPI: SSDT 3f5b7f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.994527] ACPI: SSDT 3f5b5f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.996362] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.996418] processor LNXCPU:01: registered as cooling_device2
[    0.996428] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.063412] thermal LNXTHERM:01: registered as thermal_zone0
[    1.063431] ACPI: Thermal Zone [THRM] (27 C)
[    1.063571] isapnp: Scanning for PnP cards...
[    1.417978] isapnp: No Plug & Play device found
[    1.740212] ACPI: Battery Slot [BAT0] (battery present)
[    1.740519] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.743146] brd: module loaded
[    1.744195] loop: module loaded
[    1.744377] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.744555] ahci 0000:00:1f.2: version 3.0
[    1.744586] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.744648]   alloc irq_desc for 28 on node -1
[    1.744653]   alloc kstat_irqs on node -1
[    1.744673] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    1.744736] ahci: SSS flag set, parallel bus scan disabled
[    1.744786] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.744794] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
[    1.744804] ahci 0000:00:1f.2: setting latency timer to 64
[    1.745184] scsi0 : ahci
[    1.745422] scsi1 : ahci
[    1.745561] scsi2 : ahci
[    1.745714] scsi3 : ahci
[    1.746090] ata1: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344100 irq 28
[    1.746097] ata2: DUMMY
[    1.746103] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 28
[    1.746109] ata4: DUMMY
[    1.748188] Fixed MDIO Bus: probed
[    1.748274] PPP generic driver version 2.4.2
[    1.748486] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.748536] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.748569] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.748576] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.748688] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.752621] ehci_hcd 0000:00:1d.7: debug port 1
[    1.752633] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.752668] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58344400
[    1.768032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.768197] usb usb1: configuration #1 chosen from 1 choice
[    1.768268] hub 1-0:1.0: USB hub found
[    1.768284] hub 1-0:1.0: 8 ports detected
[    1.768418] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.768459] uhci_hcd: USB Universal Host Controller Interface driver
[    1.768530] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.768545] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.768553] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.768644] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.768686] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000060a0
[    1.768882] usb usb2: configuration #1 chosen from 1 choice
[    1.768946] hub 2-0:1.0: USB hub found
[    1.768963] hub 2-0:1.0: 2 ports detected
[    1.769058] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.769070] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.769077] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.769145] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.769197] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006080
[    1.769367] usb usb3: configuration #1 chosen from 1 choice
[    1.769428] hub 3-0:1.0: USB hub found
[    1.769443] hub 3-0:1.0: 2 ports detected
[    1.769537] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.769549] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.769556] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.769625] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.769675] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006060
[    1.769846] usb usb4: configuration #1 chosen from 1 choice
[    1.769908] hub 4-0:1.0: USB hub found
[    1.769923] hub 4-0:1.0: 2 ports detected
[    1.770017] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.770029] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.770036] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.770113] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.770163] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006040
[    1.770339] usb usb5: configuration #1 chosen from 1 choice
[    1.770401] hub 5-0:1.0: USB hub found
[    1.770416] hub 5-0:1.0: 2 ports detected
[    1.770610] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.797894] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.797910] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.798075] mice: PS/2 mouse device common for all mice
[    1.798359] rtc_cmos 00:03: RTC can wake from S4
[    1.798452] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.798501] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.798755] device-mapper: uevent: version 1.0.3
[    1.798976] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.799163] device-mapper: multipath: version 1.1.0 loaded
[    1.799169] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.799461] EISA: Probing bus 0 at eisa.0
[    1.799473] Cannot allocate resource for EISA slot 1
[    1.799478] Cannot allocate resource for EISA slot 2
[    1.799483] Cannot allocate resource for EISA slot 3
[    1.799488] Cannot allocate resource for EISA slot 4
[    1.799493] Cannot allocate resource for EISA slot 5
[    1.799498] Cannot allocate resource for EISA slot 6
[    1.799513] EISA: Detected 0 cards.
[    1.799905] cpuidle: using governor ladder
[    1.800186] cpuidle: using governor menu
[    1.801308] TCP cubic registered
[    1.801666] NET: Registered protocol family 10
[    1.802658] lo: Disabled Privacy Extensions
[    1.803368] NET: Registered protocol family 17
[    1.803414] Bluetooth: L2CAP ver 2.13
[    1.803419] Bluetooth: L2CAP socket layer initialized
[    1.803425] Bluetooth: SCO (Voice Link) ver 0.6
[    1.803428] Bluetooth: SCO socket layer initialized
[    1.803525] Bluetooth: RFCOMM TTY layer initialized
[    1.803532] Bluetooth: RFCOMM socket layer initialized
[    1.803536] Bluetooth: RFCOMM ver 1.11
[    1.805468] Using IPI No-Shortcut mode
[    1.805634] PM: Resume from disk failed.
[    1.805659] registered taskstats version 1
[    1.805885]   Magic number: 14:494:946
[    1.805920] tty tty3: hash matches
[    1.806020] rtc_cmos 00:03: setting system clock to 2010-02-11 17:56:10 UTC (1265910970)
[    1.806029] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.806033] EDD information not available.
[    1.818437] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.000123] Clocksource tsc unstable (delta = -178224818 ns)
[    2.064190] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.065509] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.065728] ata1.00: ATA-8: Hitachi HTS543216L9SA00, FB2OC40C, max UDMA/133
[    2.065743] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.067307] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.067598] ata1.00: configured for UDMA/133
[    2.080163] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    2.080453] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
[    2.080765] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.080889] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.081046] sd 0:0:0:0: [sda] Write Protect is off
[    2.081053] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.081123] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.081479]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.155481] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.386349] usb 1-2: configuration #1 chosen from 1 choice
[    2.400094] ata3: SATA link down (SStatus 0 SControl 300)
[    2.416247] Freeing unused kernel memory: 540k freed
[    2.416756] Write protecting the kernel text: 4568k
[    2.416839] Write protecting the kernel read-only data: 1836k
[    2.752578] Linux agpgart interface v0.103
[    2.811269] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    2.811607] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    2.814677] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    3.077648] acpi device:1d: registered as cooling_device3
[    3.078109] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/input/input6
[    3.078222] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[    3.123823] [drm] Initialized drm 1.1.0 20060810
[    3.154149] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.154165] i915 0000:00:02.0: setting latency timer to 64
[    3.383476] [drm] fb0: inteldrmfb frame buffer device
[    3.383500] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.710292] [drm] LVDS-8: set mode 1024x600 e
[    4.140120] Console: switching to colour frame buffer device 128x37
[    4.772210] PM: Starting manual resume from disk
[    4.772219] PM: Resume from partition 8:6
[    4.772223] PM: Checking hibernation image.
[    4.772528] PM: Resume from disk failed.
[    4.804709] EXT4-fs (sda5): barriers enabled
[    4.820618] kjournald2 starting: pid 363, dev sda5:8, commit interval 5 seconds
[    4.820650] EXT4-fs (sda5): delayed allocation enabled
[    4.820658] EXT4-fs: file extents enabled
[    4.849783] EXT4-fs: mballoc enabled
[    4.849824] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    5.617179] type=1505 audit(1265910974.310:2): operation="profile_load" pid=390 name=/usr/share/gdm/guest-session/Xsession
[    5.621727] type=1505 audit(1265910974.314:3): operation="profile_load" pid=391 name=/sbin/dhclient3
[    5.622312] type=1505 audit(1265910974.314:4): operation="profile_load" pid=391 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.622649] type=1505 audit(1265910974.314:5): operation="profile_load" pid=391 name=/usr/lib/connman/scripts/dhclient-script
[    5.679827] type=1505 audit(1265910974.370:6): operation="profile_load" pid=392 name=/usr/bin/evince
[    5.689178] type=1505 audit(1265910974.382:7): operation="profile_load" pid=392 name=/usr/bin/evince-previewer
[    5.694851] type=1505 audit(1265910974.386:8): operation="profile_load" pid=392 name=/usr/bin/evince-thumbnailer
[    5.722072] type=1505 audit(1265910974.414:9): operation="profile_load" pid=394 name=/usr/lib/cups/backend/cups-pdf
[    5.722801] type=1505 audit(1265910974.414:10): operation="profile_load" pid=394 name=/usr/sbin/cupsd
[    5.741389] type=1505 audit(1265910974.434:11): operation="profile_load" pid=395 name=/usr/sbin/tcpdump
[   14.405842] Adding 2980016k swap on /dev/sda6.  Priority:-1 extents:1 across:2980016k 
[   14.410851] udev: starting version 147
[   14.454390] lp: driver loaded but no devices found
[   14.585161] EXT4-fs (sda5): internal journal on sda5:8
[   15.317415] atl1c 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.317441] atl1c 0000:03:00.0: setting latency timer to 64
[   15.317532] atl1c 0000:03:00.0: PME# disabled
[   15.317546] atl1c 0000:03:00.0: PME# disabled
[   15.349628] intel_rng: FWH not detected
[   15.393872] Linux video capture interface: v2.00
[   15.400529] cfg80211: Calling CRDA to update world regulatory domain
[   15.491121] atl1c 0000:03:00.0: version 1.0.0.1-NAPI
[   15.504378]   alloc irq_desc for 29 on node -1
[   15.504389]   alloc kstat_irqs on node -1
[   15.504421] atl1c 0000:03:00.0: irq 29 for MSI/MSI-X
[   15.505317] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.563719] cfg80211: World regulatory domain updated:
[   15.563731]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.563742]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.563752]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.563761]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.563770]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.563780]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.663339] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.663366] ath9k 0000:01:00.0: setting latency timer to 64
[   15.671294] acer-wmi: Acer Laptop ACPI-WMI Extras
[   15.681930] uvcvideo: Found UVC 1.00 device Webcam (04f2:b084)
[   15.744762] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.745401] input: Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
[   15.745535] usbcore: registered new interface driver uvcvideo
[   15.745544] USB Video Class driver (v0.1.0)
[   15.909215] acer-wmi: Unable to detect available WMID devices
[   16.102658] ath: EEPROM regdomain: 0x65
[   16.102668] ath: EEPROM indicates we should expect a direct regpair map
[   16.102679] ath: Country alpha2 being used: 00
[   16.102686] ath: Regpair used: 0x65
[   16.229382] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.231659] Registered led device: ath9k-phy0::radio
[   16.231721] Registered led device: ath9k-phy0::assoc
[   16.231784] Registered led device: ath9k-phy0::tx
[   16.231842] Registered led device: ath9k-phy0::rx
[   16.231881] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xf8860000, irq=16
[   16.426295] type=1505 audit(1265939785.118:12): operation="profile_replace" pid=884 name=/usr/share/gdm/guest-session/Xsession
[   16.430810] type=1505 audit(1265939785.122:13): operation="profile_replace" pid=885 name=/sbin/dhclient3
[   16.431675] type=1505 audit(1265939785.122:14): operation="profile_replace" pid=885 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   16.432178] type=1505 audit(1265939785.126:15): operation="profile_replace" pid=885 name=/usr/lib/connman/scripts/dhclient-script
[   16.445579] type=1505 audit(1265939785.138:16): operation="profile_replace" pid=886 name=/usr/bin/evince
[   16.472364] type=1505 audit(1265939785.166:17): operation="profile_replace" pid=886 name=/usr/bin/evince-previewer
[   16.479243] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.479312] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.487372] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.507081] type=1505 audit(1265939785.198:18): operation="profile_replace" pid=886 name=/usr/bin/evince-thumbnailer
[   16.550123] type=1505 audit(1265939785.242:19): operation="profile_replace" pid=894 name=/usr/lib/cups/backend/cups-pdf
[   16.551202] type=1505 audit(1265939785.242:20): operation="profile_replace" pid=894 name=/usr/sbin/cupsd
[   16.557065] type=1505 audit(1265939785.250:21): operation="profile_replace" pid=896 name=/usr/sbin/tcpdump
[   16.619482] hda_codec: Unknown model for ALC272, trying auto-probe from BIOS...
[   16.620570] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   16.787452] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[   16.874180] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   18.189707] ppdev: user-space parallel port driver
[   19.047939] CPU0 attaching NULL sched-domain.
[   19.047954] CPU1 attaching NULL sched-domain.
[   19.064189] CPU0 attaching sched-domain:
[   19.064201]  domain 0: span 0-1 level SIBLING
[   19.064210]   groups: 0 1
[   19.064224]   domain 1: span 0-1 level MC
[   19.064232]    groups: 0-1 (__cpu_power = 2048)
[   19.064248] CPU1 attaching sched-domain:
[   19.064256]  domain 0: span 0-1 level SIBLING
[   19.064264]   groups: 1 0
[   19.064276]   domain 1: span 0-1 level MC
[   19.064284]    groups: 0-1 (__cpu_power = 2048)
[   20.988929] CPU0 attaching NULL sched-domain.
[   20.988944] CPU1 attaching NULL sched-domain.
[   21.004174] CPU0 attaching sched-domain:
[   21.004186]  domain 0: span 0-1 level SIBLING
[   21.004195]   groups: 0 1
[   21.004210]   domain 1: span 0-1 level MC
[   21.004218]    groups: 0-1 (__cpu_power = 2048)
[   21.004234] CPU1 attaching sched-domain:
[   21.004242]  domain 0: span 0-1 level SIBLING
[   21.004251]   groups: 1 0
[   21.004264]   domain 1: span 0-1 level MC
[   21.004272]    groups: 0-1 (__cpu_power = 2048)
[   39.126469] padlock: VIA PadLock not detected.
[   49.566928] wlan0: authenticate with AP 00:1c:df:4f:9f:d4
[   49.576082] wlan0: authenticated
[   49.576094] wlan0: associate with AP 00:1c:df:4f:9f:d4
[   49.588117] wlan0: RX AssocResp from 00:1c:df:4f:9f:d4 (capab=0x411 status=0 aid=1)
[   49.588129] wlan0: associated
[   49.589663] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.008114] wlan0: no IPv6 routers present

6 ) Network configuration
 sudo lshw -C network:
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 0c:60:76:0b:06:05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.4 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:57100000-5710ffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:5a:ee:5e
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:55000000-5503ffff ioport:2000(size=128)

7 ) Scan for networks:
 iwlist scan:
wlan0     Scan completed :
          Cell 01 - Address: 00:1C:DF:4F:9F:D4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Phule"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fb304d1a30
                    Extra: Last beacon: 13816ms ago
                    IE: Unknown: 00055068756C65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD950050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD001CDF4F9FD41021000544796E65781023000E44582D57475254522D763130303010240007575053303030311042000E32303831354458475230323735351054000800060050F20400011011002044582D5747525452000000000000000000000000000000000000000000000000100800020084
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

8 ) Ubuntu Version: 
Description:    Ubuntu 9.10

9 ) Kernel/architecture (including 32 vs. 64 bit): 
 uname -mr:
2.6.31-19-generic i686

10 ) Restarting the network:
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
   ...done.

```Edit:
Oh, and apparently the forums really, really hate you if you've got javascript turned off.  Blech.

---

### Post by RedSingularity on 2010-02-11
Whoa, can you wrap that in "code" format to make it readable?

---

### Post by Jack_Simth on 2010-02-11
> **RedSingularity said:**
> Whoa, can you wrap that in "code" format to make it readable?
Sorry, the forums were stripping out my line breaks.  Took me a while to figure out that it was objecting to the lack of javascript, which is off by default due to NoScript in my browser.

Edit:
And per a suggestions on [A slightly similar problem someone else was having]("http://ubuntuforums.org/showthread.php?t=1405092")

sudo apt-get install linux-backports-modules-wireless-karmic-generic

- then rebooting, seems to have dealt with it - 2.5 GiB (and climbing - the download will run around 20 GiB), vs. the approx. 160 MiB before lockup previously.

Edit 2: Oh, hey, that's interesting - the network stats loop after a while on the "total received" - huh.  I'm up to ten GiB....

---

