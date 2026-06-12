---
title: "A bit of a head scratcher"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by booah on 2011-06-30
I've been having a strange wireless issue lately. I have successfully installed a usb wireless network adapter (LG-nortel) using ndiswrapper on my xbmc live machine. 
The problem is that sometimes when I boot up it just doesnt have any connection to the network. When I go into wicd-curses to investigate the wireless network is never found. The router is closeby and it is very reliable (never had an issue on my laptop). Ndiswrapper -l always shows the usb device is present and working ok. 
If I boot up and I get a connection then it is perfect for hours but if the connection drops it normally does not come back. 

I would guess there is a 70% chance when I boot up that I have a connection to the network.

I recently discovered the delights of FTP and telnet so when I turn on my pc and look forward to connecting remotely only to find it never got on the network in the first place is just not nice! ;)

Any ideas? 
I dont think this should matter but the usb device is connected to a 1 meter usb extension (i tested it without and different ports with same consequences).

Thanks for your time.

---

### Post by booah on 2011-06-30
[B]Here is the working connection :

lspci[/B]```

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a6f (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
02:00.5 Ethernet controller: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
```**lsusb**```

Bus 005 Device 002: ID 045e:006d Microsoft Corp. eHome Remote Control Keyboard keys
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05a4:1000 Ortek Technology, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1058:1021 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 157e:300e TRENDnet 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```[B]ifconfig
[/B]```
eth0      Link encap:Ethernet  HWaddr 80:ee:73:07:8b:07  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:f7:ca:80:51  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:f7ff:feca:8051/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7882610 (7.8 MB)  TX bytes:230026 (230.0 KB)
```[B]iwconfig
[/B]```
wlan0     Ralink STA  ESSID:"Cliff House"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:22:6B:F7:A0:48   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-56 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```[B]lsmod
[/B]```
Module                  Size  Used by
dm_crypt               11331  0 
snd_hda_codec_nvhdmi    12722  1 
snd_hda_codec_idt      54083  1 
rt2800usb               7220  0 
rt2800lib              28358  1 rt2800usb
rt2x00usb               9662  2 rt2800usb,rt2800lib
rt2x00lib              26746  2 rt2800lib,rt2x00usb
compat_firmware_class     6554  1 rt2x00lib
mac80211              232535  2 rt2x00usb,rt2x00lib
snd_hda_intel          20799  3 
snd_hda_codec          87096  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5668  1 snd_hda_codec
snd_pcm_oss            34603  0 
snd_mixer_oss          13929  1 snd_pcm_oss
snd_pcm                71646  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1498  0 
snd_seq_oss            27626  0 
snd_seq_midi            4621  0 
snd_rawmidi            19141  1 snd_seq_midi
ndiswrapper           184677  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
cfg80211              146764  2 rt2x00lib,mac80211
snd_seq                48042  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2870sta             399316  1 
snd_timer              18710  3 snd_pcm,snd_seq
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 36110  0 
lp                      7028  0 
snd                    56687  19 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms               7311  0 
crc_ccitt               1339  2 rt2800usb,rt2870sta
hid                    67032  1 usbhid
psmouse                63245  0 
serio_raw               3978  0 
parport                32635  1 lp
nvidia               9961216  37 
vga16fb                11385  0 
memstick                8237  1 jmb38x_ms
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  2 rt2x00lib,sdhci
jme                    27953  0 
mii                     4381  1 jme
soundcore               6620  1 snd
snd_page_alloc          7140  2 snd_hda_intel,snd_pcm
vgastate                8961  1 vga16fb
lirc_mceusb            12402  1 
lirc_dev                8884  3 lirc_mceusb
usb_storage            39553  1 
vesafb                  3542  0 
intel_agp              24375  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
video                  17375  0 
output                  1871  1 video
agpgart                31724  2 nvidia,intel_agp
ramzswap                6362  1 
xvmalloc                4074  1 ramzswap
lzo_decompress          2189  1 ramzswap
lzo_compress            1853  1 ramzswap
```**dmesg**
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-26-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 (Ubuntu 2.6.32-26.48-generic 2.6.32.24+drm33.11)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
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
[    0.000000]  modified: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  modified: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  modified: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 371d5000 - 37fef641
[    0.000000] Allocated new RAMDISK: 008e1000 - 016fb641
[    0.000000] Move RAMDISK from 00000000371d5000 - 0000000037fef640 to 008e1000 - 016fb640
[    0.000000] ACPI: RSDP 000f9eb0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 7ffb0100 00054 (v01 Shuttl Shuttle  20100728 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffb0290 000F4 (v04 072810 FACP1536 20100728 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffb05c0 06645 (v02  XS350  XS35V10 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 7ffbe000 00040
[    0.000000] ACPI: APIC 7ffb0390 0006C (v02 072810 APIC1536 20100728 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffb0400 0003C (v01 072810 OEMMCFG  20100728 MSFT 00000097)
[    0.000000] ACPI: SLIC 7ffb0440 00176 (v01 Shuttl Shuttle  20100728 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffbe040 00072 (v01 072810 OEMB1536 20100728 MSFT 00000097)
[    0.000000] ACPI: HPET 7ffba5c0 00038 (v01 072810 OEMHPET  20100728 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dced8]    TEXT DATA BSS ==> [0000100000 - 00008dced8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008dd000 - 00008e01ab]              BRK ==> [00008dd000 - 00008e01ab]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008e1000 - 00016fb641]      NEW RAMDISK ==> [00008e1000 - 00016fb641]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffb0
[    0.000000] On node 0 totalpages: 524095
[    0.000000] free_area_init_node: node 0, pgdat c079a760, node_mem_map c16fd200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294562 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2800000 s36056 r0 d21288 u1048576
[    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=5f9e13ad-a33a-4057-8b66-9e0e218e4784 ro quiet splash xbmc=autostart,nodiskmount loglevel=0 video=vesafb
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10483840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffb0)
[    0.000000] Memory: 2044956k/2096832k available (4682k kernel code, 50220k reserved, 2121k data, 656k init, 1187528k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc0849000   ( 656 kB)
[    0.000000]       .data : 0xc0592847 - 0xc07a4e68   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0592847   (4682 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.491 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.98 BogoMIPS (lpj=6649964)
[    0.004044] Security Framework initialized
[    0.004084] AppArmor: AppArmor initialized
[    0.004100] Mount-cache hash table entries: 512
[    0.004330] Initializing cgroup subsys ns
[    0.004340] Initializing cgroup subsys cpuacct
[    0.004350] Initializing cgroup subsys memory
[    0.004364] Initializing cgroup subsys devices
[    0.004370] Initializing cgroup subsys freezer
[    0.004376] Initializing cgroup subsys net_cls
[    0.004411] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004418] CPU: L2 cache: 512K
[    0.004423] CPU: Physical Processor ID: 0
[    0.004428] CPU: Processor Core ID: 0
[    0.004435] mce: CPU supports 5 MCE banks
[    0.004448] CPU0: Thermal monitoring enabled (TM1)
[    0.004456] using mwait in idle threads.
[    0.004467] Performance Events: Atom events, Intel PMU driver.
[    0.004484] ... version:                3
[    0.004488] ... bit width:              40
[    0.004492] ... generic registers:      2
[    0.004497] ... value mask:             000000ffffffffff
[    0.004502] ... max period:             000000007fffffff
[    0.004507] ... fixed-purpose events:   3
[    0.004511] ... event mask:             0000000700000003
[    0.004520] Checking 'hlt' instruction... OK.
[    0.020007] Disabling 4MB page tables to avoid TLB bug
[    0.024197] ACPI: Core revision 20090903
[    0.040017] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040028] ftrace: allocating 21794 entries in 43 pages
[    0.044103] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044434] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.085438] CPU0: Intel(R) Atom(TM) CPU D510   @ 1.66GHz stepping 0a
[    0.088001] Booting processor 1 APIC 0x2 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM1)
[    0.172071] CPU1: Intel(R) Atom(TM) CPU D510   @ 1.66GHz stepping 0a
[    0.172093] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.176001] Measured 10 cycles TSC warp between CPUs, turning off TSC clock.
[    0.176001] Marking TSC unstable due to check_tsc_sync_source failed
[    0.176187] Booting processor 2 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#2
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU2: Thermal monitoring enabled (TM1)
[    0.264108] CPU2: Intel(R) Atom(TM) CPU D510   @ 1.66GHz stepping 0a
[    0.264351] Booting processor 3 APIC 0x3 ip 0x6000
[    0.008000] Initializing CPU#3
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU3: Thermal monitoring enabled (TM1)
[    0.352133] CPU3: Intel(R) Atom(TM) CPU D510   @ 1.66GHz stepping 0a
[    0.352184] Brought up 4 CPUs
[    0.352191] Total of 4 processors activated (13196.51 BogoMIPS).
[    0.353578] CPU0 attaching sched-domain:
[    0.353587]  domain 0: span 0,2 level SIBLING
[    0.353593]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[    0.353606]   domain 1: span 0,2 level MC
[    0.353611]    groups: 0,2 (cpu_power = 1178)
[    0.353620]    domain 2: span 0-3 level CPU
[    0.353625]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    0.353641] CPU1 attaching sched-domain:
[    0.353646]  domain 0: span 1,3 level SIBLING
[    0.353651]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[    0.353663]   domain 1: span 1,3 level MC
[    0.353668]    groups: 1,3 (cpu_power = 1178)
[    0.353677]    domain 2: span 0-3 level CPU
[    0.353682]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    0.353695] CPU2 attaching sched-domain:
[    0.353700]  domain 0: span 0,2 level SIBLING
[    0.353705]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[    0.353716]   domain 1: span 0,2 level MC
[    0.353721]    groups: 0,2 (cpu_power = 1178)
[    0.353730]    domain 2: span 0-3 level CPU
[    0.353735]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    0.353748] CPU3 attaching sched-domain:
[    0.353753]  domain 0: span 1,3 level SIBLING
[    0.353758]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[    0.353770]   domain 1: span 1,3 level MC
[    0.353775]    groups: 1,3 (cpu_power = 1178)
[    0.353784]    domain 2: span 0-3 level CPU
[    0.353788]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    0.354145] devtmpfs: initialized
[    0.354145] regulator: core version 0.5
[    0.354145] Time: 17:39:27  Date: 06/30/11
[    0.354145] NET: Registered protocol family 16
[    0.354145] Trying to unpack rootfs image as initramfs...
[    0.354145] EISA bus registered
[    0.354145] ACPI: bus type pci registered
[    0.354145] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.354145] PCI: Not using MMCONFIG.
[    0.356081] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.356086] PCI: Using configuration type 1 for base access
[    0.357916] bio: create slab <bio-0> at 0
[    0.357916] ACPI: EC: Look up EC in DSDT
[    0.362105] ACPI Error: No handler for Region [ECRM] (f70119d8) [EmbeddedControl] (20090903/evregion-319)
[    0.362120] ACPI Error: Region EmbeddedControl(3) has no handler (20090903/exfldio-295)
[    0.362133] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._REG] (Node f7015390), AE_NOT_EXIST
[    0.362891] ACPI: Executed 1 blocks of module-level executable AML code
[    0.372083] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.840100] ACPI: Interpreter enabled
[    0.840110] ACPI: (supports S0 S3 S4 S5)
[    0.840156] ACPI: Using IOAPIC for interrupt routing
[    0.840248] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.843421] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.843428] PCI: Using MMCONFIG for extended config space
[    0.855995] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.856413] ACPI: No dock devices found.
[    0.856720] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.856894] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfcffc000-0xfcffffff]
[    0.856943] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.856951] pci 0000:00:1b.0: PME# disabled
[    0.857025] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.857032] pci 0000:00:1c.0: PME# disabled
[    0.857107] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.857114] pci 0000:00:1c.1: PME# disabled
[    0.857189] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.857195] pci 0000:00:1c.3: PME# disabled
[    0.857251] pci 0000:00:1d.0: reg 20 io port: [0xbc00-0xbc1f]
[    0.857308] pci 0000:00:1d.1: reg 20 io port: [0xb880-0xb89f]
[    0.857364] pci 0000:00:1d.2: reg 20 io port: [0xb800-0xb81f]
[    0.857420] pci 0000:00:1d.3: reg 20 io port: [0xb480-0xb49f]
[    0.857483] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfcffbc00-0xfcffbfff]
[    0.857539] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.857547] pci 0000:00:1d.7: PME# disabled
[    0.857728] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.857738] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.857747] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.857757] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.857766] pci 0000:00:1f.2: reg 20 io port: [0xff90-0xff9f]
[    0.857775] pci 0000:00:1f.2: reg 24 32bit mmio: [0x00fc00-0x00ffff]
[    0.857801] pci 0000:00:1f.2: PME# supported from D3hot
[    0.857808] pci 0000:00:1f.2: PME# disabled
[    0.857859] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.857939] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.857956] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.857974] pci 0000:01:00.0: reg 1c 64bit mmio pref: [0xce000000-0xcfffffff]
[    0.857985] pci 0000:01:00.0: reg 24 io port: [0xcc00-0xcc7f]
[    0.857997] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfe980000-0xfe9fffff]
[    0.858097] pci 0000:01:00.1: reg 10 32bit mmio: [0xfe97c000-0xfe97ffff]
[    0.858221] pci 0000:00:1c.0: bridge io port: [0xc000-0xcfff]
[    0.858229] pci 0000:00:1c.0: bridge 32bit mmio: [0xfd000000-0xfe9fffff]
[    0.858239] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xce000000-0xdfffffff]
[    0.858298] pci 0000:02:00.0: reg 10 32bit mmio: [0xfeaffc00-0xfeaffcff]
[    0.858445] pci 0000:02:00.2: reg 10 32bit mmio: [0xfeaff800-0xfeaff8ff]
[    0.858585] pci 0000:02:00.3: reg 10 32bit mmio: [0xfeaff400-0xfeaff4ff]
[    0.858727] pci 0000:02:00.5: reg 10 32bit mmio: [0xfeaf8000-0xfeafbfff]
[    0.858748] pci 0000:02:00.5: reg 18 io port: [0xdc00-0xdc7f]
[    0.858761] pci 0000:02:00.5: reg 1c io port: [0xd800-0xd8ff]
[    0.858826] pci 0000:02:00.5: PME# supported from D0 D3hot D3cold
[    0.858834] pci 0000:02:00.5: PME# disabled
[    0.858897] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.858904] pci 0000:00:1c.1: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.858964] pci 0000:03:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.858976] pci 0000:03:00.0: reg 14 32bit mmio: [0xfebfc000-0xfebfffff]
[    0.859047] pci 0000:03:00.0: supports D1 D2
[    0.859052] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[    0.859060] pci 0000:03:00.0: PME# disabled
[    0.859119] pci 0000:00:1c.3: bridge io port: [0xe000-0xefff]
[    0.859127] pci 0000:00:1c.3: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.859186] pci 0000:00:1e.0: transparent bridge
[    0.859217] pci_bus 0000:00: on NUMA node 0
[    0.859226] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.859422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.859558] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.859665] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.859808] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.877391] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.877603] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.877812] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.878020] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.878229] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.878439] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.878650] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.878862] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.879111] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.879122] vgaarb: loaded
[    0.879388] SCSI subsystem initialized
[    0.879425] libata version 3.00 loaded.
[    0.879425] usbcore: registered new interface driver usbfs
[    0.879425] usbcore: registered new interface driver hub
[    0.880033] usbcore: registered new device driver usb
[    0.880199] ACPI: WMI: Mapper loaded
[    0.880204] PCI: Using ACPI for IRQ routing
[    0.880304] pci 0000:00:1f.2: BAR 5: address space collision on of device [0x00fc00-0x00ffff]
[    0.880310] pci 0000:00:1f.2: BAR 5: can't allocate resource
[    0.880519] NetLabel: Initializing
[    0.880524] NetLabel:  domain hash size = 128
[    0.880527] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.880550] NetLabel:  unlabeled traffic allowed by default
[    0.880643] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.880654] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.892117] Switching to clocksource hpet
[    0.896062] AppArmor: AppArmor Filesystem Enabled
[    0.896102] pnp: PnP ACPI init
[    0.896139] ACPI: bus type pnp registered
[    0.900354] pnp: PnP ACPI: found 15 devices
[    0.900360] ACPI: ACPI bus type pnp unregistered
[    0.900368] PnPBIOS: Disabled by ACPI PNP
[    0.900395] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.900402] system 00:01: iomem range 0xfed90000-0xfed93fff has been reserved
[    0.900421] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.900428] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.900435] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.900442] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.900450] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.900464] system 00:0b: iomem range 0xffc00000-0xffefffff has been reserved
[    0.900477] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.900484] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.900497] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.900511] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.900518] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.900525] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.900532] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[    0.900539] system 00:0e: iomem range 0xfed90000-0xffffffff could not be reserved
[    0.935517] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.935525] pci 0000:00:1c.0:   IO window: 0xc000-0xcfff
[    0.935534] pci 0000:00:1c.0:   MEM window: 0xfd000000-0xfe9fffff
[    0.935542] pci 0000:00:1c.0:   PREFETCH window: 0x000000ce000000-0x000000dfffffff
[    0.935553] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.935559] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.935568] pci 0000:00:1c.1:   MEM window: 0xfea00000-0xfeafffff
[    0.935575] pci 0000:00:1c.1:   PREFETCH window: 0x00000080000000-0x000000801fffff
[    0.935586] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    0.935592] pci 0000:00:1c.3:   IO window: 0xe000-0xefff
[    0.935600] pci 0000:00:1c.3:   MEM window: 0xfeb00000-0xfebfffff
[    0.935608] pci 0000:00:1c.3:   PREFETCH window: 0x00000080200000-0x000000803fffff
[    0.935617] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.935622] pci 0000:00:1e.0:   IO window: disabled
[    0.935629] pci 0000:00:1e.0:   MEM window: disabled
[    0.935635] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.935658]   alloc irq_desc for 16 on node -1
[    0.935663]   alloc kstat_irqs on node -1
[    0.935675] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.935684] pci 0000:00:1c.0: setting latency timer to 64
[    0.935697]   alloc irq_desc for 17 on node -1
[    0.935701]   alloc kstat_irqs on node -1
[    0.935709] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.935717] pci 0000:00:1c.1: setting latency timer to 64
[    0.935788] pci 0000:00:1c.3: power state changed by ACPI to D0
[    0.935843] pci 0000:00:1c.3: power state changed by ACPI to D0
[    0.935854]   alloc irq_desc for 19 on node -1
[    0.935858]   alloc kstat_irqs on node -1
[    0.935867] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.935875] pci 0000:00:1c.3: setting latency timer to 64
[    0.935886] pci 0000:00:1e.0: setting latency timer to 64
[    0.935894] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.935900] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.935907] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.935913] pci_bus 0000:01: resource 1 mem: [0xfd000000-0xfe9fffff]
[    0.935919] pci_bus 0000:01: resource 2 pref mem [0xce000000-0xdfffffff]
[    0.935925] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.935931] pci_bus 0000:02: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.935937] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x801fffff]
[    0.935944] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.935949] pci_bus 0000:03: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.935955] pci_bus 0000:03: resource 2 pref mem [0x80200000-0x803fffff]
[    0.935962] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.935967] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.936067] NET: Registered protocol family 2
[    0.936273] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.936909] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.937855] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.938282] TCP: Hash tables configured (established 131072 bind 65536)
[    0.938288] TCP reno registered
[    0.938505] NET: Registered protocol family 1
[    0.938673] pci 0000:01:00.0: Boot video device
[    0.939284] cpufreq-nforce2: No nForce2 chipset.
[    0.939339] Scanning for low memory corruption every 60 seconds
[    0.939566] audit: initializing netlink socket (disabled)
[    0.939586] type=2000 audit(1309455566.936:1): initialized
[    0.956248] highmem bounce pool size: 64 pages
[    0.956261] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.959784] VFS: Disk quotas dquot_6.5.2
[    0.959920] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.961299] fuse init (API version 7.13)
[    0.961495] msgmni has been set to 1677
[    0.962083] alg: No test for stdrng (krng)
[    0.962231] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.962238] io scheduler noop registered
[    0.962242] io scheduler anticipatory registered
[    0.962247] io scheduler deadline registered
[    0.962343] io scheduler cfq registered (default)
[    0.962587]   alloc irq_desc for 24 on node -1
[    0.962592]   alloc kstat_irqs on node -1
[    0.962609] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.962621] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.962794]   alloc irq_desc for 25 on node -1
[    0.962799]   alloc kstat_irqs on node -1
[    0.962812] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.962824] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.962996]   alloc irq_desc for 26 on node -1
[    0.963000]   alloc kstat_irqs on node -1
[    0.963012] pcieport 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.963023] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.963176] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.963375] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.963577] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.963585] ACPI: Sleep Button [SLPB]
[    0.963682] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.963688] ACPI: Power Button [PWRB]
[    0.963788] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.963795] ACPI: Power Button [PWRF]
[    0.965135] processor LNXCPU:00: registered as cooling_device0
[    0.965937] processor LNXCPU:01: registered as cooling_device1
[    0.966729] processor LNXCPU:02: registered as cooling_device2
[    0.967533] processor LNXCPU:03: registered as cooling_device3
[    1.001179] thermal LNXTHERM:01: registered as thermal_zone0
[    1.001197] ACPI: Thermal Zone [TZ00] (50 C)
[    1.001525] isapnp: Scanning for PnP cards...
[    1.004889] efifb: probing for efifb
[    1.004979] efifb: framebuffer at 0xcf000000, mapped to 0xf8080000, using 1920k, total 1920k
[    1.004986] efifb: mode is 800x600x32, linelength=3200, pages=1
[    1.004990] efifb: scrolling: redraw
[    1.004997] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.005113] fb0: EFI VGA frame buffer device
[    1.005123] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.007982] brd: module loaded
[    1.009117] loop: module loaded
[    1.009315] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.009511] ata_piix 0000:00:1f.2: version 2.13
[    1.009534] ata_piix 0000:00:1f.2: enabling device (0005 -> 0007)
[    1.009546] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.009555] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.009616] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.009760] scsi0 : ata_piix
[    1.009953] scsi1 : ata_piix
[    1.012785] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
[    1.012792] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
[    1.013621] Fixed MDIO Bus: probed
[    1.013710] PPP generic driver version 2.4.2
[    1.013814] tun: Universal TUN/TAP device driver, 1.6
[    1.013819] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.014009] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.014050]   alloc irq_desc for 23 on node -1
[    1.014055]   alloc kstat_irqs on node -1
[    1.014068] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.014096] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.014102] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.014175] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.014208] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.014223] ehci_hcd 0000:00:1d.7: debug port 1
[    1.018128] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.018156] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfcffbc00
[    1.018682] Freeing initrd memory: 14441k freed
[    1.033025] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.033213] usb usb1: configuration #1 chosen from 1 choice
[    1.033277] hub 1-0:1.0: USB hub found
[    1.033295] hub 1-0:1.0: 8 ports detected
[    1.033420] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.033456] uhci_hcd: USB Universal Host Controller Interface driver
[    1.033522] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.033535] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.033542] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.033620] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.033656] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000bc00
[    1.033848] usb usb2: configuration #1 chosen from 1 choice
[    1.033908] hub 2-0:1.0: USB hub found
[    1.033923] hub 2-0:1.0: 2 ports detected
[    1.034008] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.034023] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.034029] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.034104] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.034149] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b880
[    1.034347] usb usb3: configuration #1 chosen from 1 choice
[    1.034406] hub 3-0:1.0: USB hub found
[    1.034421] hub 3-0:1.0: 2 ports detected
[    1.034519]   alloc irq_desc for 18 on node -1
[    1.034525]   alloc kstat_irqs on node -1
[    1.034536] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.034546] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.034552] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.034624] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.034667] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b800
[    1.034857] usb usb4: configuration #1 chosen from 1 choice
[    1.034917] hub 4-0:1.0: USB hub found
[    1.034932] hub 4-0:1.0: 2 ports detected
[    1.035015] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.035025] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.035031] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.035110] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.035153] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b480
[    1.035346] usb usb5: configuration #1 chosen from 1 choice
[    1.035406] hub 5-0:1.0: USB hub found
[    1.035421] hub 5-0:1.0: 2 ports detected
[    1.035612] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.038157] i8042.c: Detected active multiplexing controller, rev 1.0.
[    1.038965] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.038980] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.038991] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.039001] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.039011] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.039266] mice: PS/2 mouse device common for all mice
[    1.039552] rtc_cmos 00:03: RTC can wake from S4
[    1.039637] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.039672] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.039932] device-mapper: uevent: version 1.0.3
[    1.040197] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.040483] device-mapper: multipath: version 1.1.0 loaded
[    1.040491] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.040782] EISA: Probing bus 0 at eisa.0
[    1.040817] EISA: Detected 0 cards.
[    1.040999] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.042007] cpuidle: using governor ladder
[    1.042013] cpuidle: using governor menu
[    1.043006] TCP cubic registered
[    1.043368] NET: Registered protocol family 10
[    1.044381] lo: Disabled Privacy Extensions
[    1.045098] NET: Registered protocol family 17
[    1.045220] Using IPI No-Shortcut mode
[    1.045405] PM: Resume from disk failed.
[    1.045428] registered taskstats version 1
[    1.046016]   Magic number: 15:191:695
[    1.046074] pci 0000:00:00.0: hash matches
[    1.046143] rtc_cmos 00:03: setting system clock to 2011-06-30 17:39:27 UTC (1309455567)
[    1.046150] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.046154] EDD information not available.
[    1.233252] ata1.00: ATA-8: OCZ-VERTEX2, 1.11, max UDMA/133
[    1.233259] ata1.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.289257] ata1.00: configured for UDMA/133
[    1.343956] isapnp: No Plug & Play device found
[    1.344038] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.344212] scsi 0:0:0:0: Direct-Access     ATA      OCZ-VERTEX2      1.11 PQ: 0 ANSI: 5
[    1.344542] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.344564] sd 0:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.344702] sd 0:0:0:0: [sda] Write Protect is off
[    1.344709] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.344776] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.345173]  sda: sda1 sda2 < sda5 >
[    1.346327] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.346363] Freeing unused kernel memory: 656k freed
[    1.346883] Write protecting the kernel text: 4684k
[    1.346958] Write protecting the kernel read-only data: 1840k
[    1.393231] ramzswap: disk size set to 1030628 kB
[    1.404546] udev: starting version 151
[    1.450843] Adding 1030624k swap on /dev/ramzswap0.  Priority:100 extents:1 across:1030624k SS
[    1.505487] usb 1-1: configuration #1 chosen from 1 choice
[    1.561487] Linux agpgart interface v0.103
[    1.575878] Console: switching to colour frame buffer device 100x37
[    1.673037] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    1.809472] usb 1-5: configuration #1 chosen from 1 choice
[    1.900487] Initializing USB Mass Storage driver...
[    1.900837] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.901070] usb-storage: device found at 4
[    1.901076] usb-storage: waiting for device to settle before scanning
[    1.901114] usbcore: registered new interface driver usb-storage
[    1.901124] USB Mass Storage support registered.
[    2.160064] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    2.286051] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.341448] usb 3-2: configuration #1 chosen from 1 choice
[    2.584608] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    2.731230] Adding 2438136k swap on /dev/sda5.  Priority:-1 extents:1 across:2438136k SS
[    2.751045] udev: starting version 151
[    2.764533] usb 5-2: configuration #1 chosen from 1 choice
[    2.824299] lirc_dev: IR Remote Control driver registered, major 61 
[    2.869265] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[    2.869279] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[    2.932369] jme: JMicron JMC2XX ethernet driver version 1.0.5
[    2.932467] jme 0000:02:00.5: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.932494] jme 0000:02:00.5: setting latency timer to 64
[    2.934967] eth0: JMC260 Fast Ethernet ver:22 rev:2 macaddr:80:ee:73:07:8b:07
[    2.935258] sdhci: Secure Digital Host Controller Interface driver
[    2.935266] sdhci: Copyright(c) Pierre Ossman
[    2.979705] sdhci-pci 0000:02:00.0: SDHCI controller found [197b:2382] (rev 80)
[    2.979747] sdhci-pci 0000:02:00.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.979842] sdhci-pci 0000:02:00.0: setting latency timer to 64
[    2.979937] Registered led device: mmc0::
[    2.980076] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[    2.980146] mmc0: SDHCI controller on PCI [0000:02:00.0] using ADMA
[    2.980179] sdhci-pci 0000:02:00.2: SDHCI controller found [197b:2381] (rev 80)
[    2.980208] sdhci-pci 0000:02:00.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.980227] sdhci-pci 0000:02:00.2: Refusing to bind to secondary interface.
[    2.980243] sdhci-pci 0000:02:00.2: PCI INT B disabled
[    2.995152] vga16fb: initializing
[    2.995162] vga16fb: mapped to 0xc00a0000
[    2.995173] vga16fb: not registering due to another framebuffer present
[    3.135787] lirc_dev: lirc_register_driver: sample_rate: 0
[    3.143252] lirc_mceusb[2]: Microsoft Microsoft IR Transceiver on usb5:2
[    3.216623] nvidia: module license 'NVIDIA' taints kernel.
[    3.216632] Disabling lock debugging due to kernel taint
[    3.758305] usbcore: registered new interface driver lirc_mceusb
[    6.025434] jmb38x_ms 0000:02:00.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    6.025451] jmb38x_ms 0000:02:00.3: setting latency timer to 64
[    6.108054] usbcore: registered new interface driver hiddev
[    6.134864] input: ORtek Wireless Touchpad Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[    6.135099] generic-usb 0003:05A4:1000.0001: input,hidraw0: USB HID v1.10 Keyboard [ORtek Wireless Touchpad Keyboard] on usb-0000:00:1d.1-2/input0
[    6.137491]   alloc irq_desc for 27 on node -1
[    6.137499]   alloc kstat_irqs on node -1
[    6.137528] jme 0000:02:00.5: irq 27 for MSI/MSI-X
[    6.137874] eth0: Link is down.
[    6.138485] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.143661] rtusb init --->
[    6.144091] === pAd = f88ca000, size = 471320 ===
[    6.144099] <-- RTMPAllocAdapterBlock, Status=0
[    6.149781] usbcore: registered new interface driver rt2870
[    6.167457] input: ORtek Wireless Touchpad Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input6
[    6.167775] generic-usb 0003:05A4:1000.0002: input,hidraw1: USB HID v1.10 Mouse [ORtek Wireless Touchpad Keyboard] on usb-0000:00:1d.1-2/input1
[    6.167846] usbcore: registered new interface driver usbhid
[    6.167855] usbhid: v2.6:USB HID core driver
[    6.186623] lp: driver loaded but no devices found
[    6.214558] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.214581] nvidia 0000:01:00.0: setting latency timer to 64
[    6.214595] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    6.215345] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[    6.305104] usb 1-1: firmware: requesting rt2870.bin
[    6.382386] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[    6.545990] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.546005] hda_intel: codec_mask forced to 0xff
[    6.546091] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.617900] <-- RTMPAllocTxRxRingMemory, Status=0
[    6.619698] -->RTUSBVenderReset
[    6.619828] <--RTUSBVenderReset
[    6.901730] usb-storage: device scan complete
[    6.902074] 1. Phy Mode = 0
[    6.902080] 2. Phy Mode = 0
[    6.902634] scsi 2:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[    6.904423] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.909001] sd 2:0:0:0: [sdb] 3907024896 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    6.910242] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    6.910251] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.912238] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    6.912247] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.912263]  sdb: sdb1
[    6.934855] RTMPSetPhyMode: channel is out of range, use first channel=1 
[    6.936501] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    6.936543] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.936555] sd 2:0:0:0: [sdb] Attached SCSI disk
[    6.943590] 3. Phy Mode = 0
[    6.948462] MCS Set = 00 00 00 00 00
[    6.957675] <==== rt28xx_init, Status=0
[    6.959202] 0x1300 = 00073200
[    6.959890] cfg80211: Calling CRDA to update world regulatory domain
[    6.971550] cfg80211: World regulatory domain updated:
[    6.971560]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.971570]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.971578]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.971587]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.971595]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.971603]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.064128] usbcore: registered new interface driver rt2800usb
[    9.589018] ALSA hda_intel.c:712: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   10.593014] ALSA hda_intel.c:1420: Codec #1 probe error; disabling it...
[   11.629016] ALSA hda_intel.c:1420: Codec #2 probe error; disabling it...
[   12.664515] ALSA hda_intel.c:1420: Codec #3 probe error; disabling it...
[   12.726493] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   12.736667] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.736945] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.741486] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.741502] hda_intel: codec_mask forced to 0xf2
[   12.741604] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.792026] ALSA hda_intel.c:712: azx_get_response timeout, switching to polling mode: last cmd=0x400f0000
[   16.793037] ALSA hda_intel.c:1420: Codec #4 probe error; disabling it...
[   17.244016] wlan0: no IPv6 routers present
[   17.829023] ALSA hda_intel.c:1420: Codec #5 probe error; disabling it...
[   18.872028] ALSA hda_intel.c:1420: Codec #6 probe error; disabling it...
[   19.912025] ALSA hda_intel.c:1420: Codec #7 probe error; disabling it...
[   20.155223] usbcore: registered new interface driver ndiswrapper
[   20.950979] CPU0 attaching NULL sched-domain.
[   20.950996] CPU1 attaching NULL sched-domain.
[   20.951005] CPU2 attaching NULL sched-domain.
[   20.951013] CPU3 attaching NULL sched-domain.
[   20.985538] CPU0 attaching sched-domain:
[   20.985547]  domain 0: span 0,2 level SIBLING
[   20.985553]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[   20.985567]   domain 1: span 0,2 level MC
[   20.985572]    groups: 0,2 (cpu_power = 1178)
[   20.985582]    domain 2: span 0-3 level CPU
[   20.985587]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   20.985604] CPU1 attaching sched-domain:
[   20.985609]  domain 0: span 1,3 level SIBLING
[   20.985614]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[   20.985626]   domain 1: span 1,3 level MC
[   20.985631]    groups: 1,3 (cpu_power = 1178)
[   20.985641]    domain 2: span 0-3 level CPU
[   20.985646]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   20.985660] CPU2 attaching sched-domain:
[   20.985665]  domain 0: span 0,2 level SIBLING
[   20.985670]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[   20.985682]   domain 1: span 0,2 level MC
[   20.985687]    groups: 0,2 (cpu_power = 1178)
[   20.985696]    domain 2: span 0-3 level CPU
[   20.985701]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   20.985714] CPU3 attaching sched-domain:
[   20.985719]  domain 0: span 1,3 level SIBLING
[   20.985725]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   20.985736]   domain 1: span 1,3 level MC
[   20.985742]    groups: 1,3 (cpu_power = 1178)
[   20.985751]    domain 2: span 0-3 level CPU
[   20.985756]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   22.469618] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 177
[   23.318122] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   23.344576] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   24.120034] HDMI: detected monitor SONY TV
[   24.120039]      at connection type HDMI
[   24.120046] HDMI: available speakers: FL/FR
[   24.120054] ------------[ cut here ]------------
[   24.120066] WARNING: at /build/buildd/linux-2.6.32/lib/vsprintf.c:1100 vsnprintf+0x3f2/0x410()
[   24.120072] Hardware name: XS35
[   24.120076] Modules linked in: dm_crypt snd_hda_codec_nvhdmi snd_hda_codec_idt rt2800usb rt2800lib rt2x00usb rt2x00lib compat_firmware_class mac80211 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi ndiswrapper snd_seq_midi_event cfg80211 snd_seq rt2870sta snd_timer snd_seq_device usbhid lp snd jmb38x_ms crc_ccitt hid psmouse serio_raw parport nvidia(P) vga16fb memstick sdhci_pci sdhci led_class jme mii soundcore snd_page_alloc vgastate lirc_mceusb lirc_dev usb_storage vesafb intel_agp fbcon tileblit font bitblit softcursor video output agpgart ramzswap xvmalloc lzo_decompress lzo_compress
[   24.120182] Pid: 1013, comm: hd-audio1 Tainted: P           2.6.32-26-generic #48-Ubuntu
[   24.120187] Call Trace:
[   24.120199]  [<c014c7b2>] warn_slowpath_common+0x72/0xa0
[   24.120206]  [<c0353972>] ? vsnprintf+0x3f2/0x410
[   24.120213]  [<c0353972>] ? vsnprintf+0x3f2/0x410
[   24.120222]  [<c014c7fa>] warn_slowpath_null+0x1a/0x20
[   24.120229]  [<c0353972>] vsnprintf+0x3f2/0x410
[   24.120238]  [<c0353a1a>] snprintf+0x1a/0x20
[   24.120254]  [<f8a2a64d>] snd_print_pcm_bits+0x5d/0x80 [snd_hda_codec]
[   24.120271]  [<f8a337f7>] hdmi_show_short_audio_desc+0xf7/0x100 [snd_hda_codec]
[   24.120279]  [<c0353a1a>] ? snprintf+0x1a/0x20
[   24.120295]  [<f8a3385f>] snd_hdmi_show_eld+0x5f/0xa0 [snd_hda_codec]
[   24.120310]  [<f8a33b6c>] ? snd_hdmi_get_eld+0x29c/0x2d0 [snd_hda_codec]
[   24.120325]  [<f8a33b6c>] ? snd_hdmi_get_eld+0x29c/0x2d0 [snd_hda_codec]
[   24.120335]  [<f8516706>] hdmi_unsol_event+0x106/0x110 [snd_hda_codec_nvhdmi]
[   24.120345]  [<c013fb03>] ? finish_task_switch+0x43/0xc0
[   24.120359]  [<f8a2a106>] process_unsol_events+0x56/0x70 [snd_hda_codec]
[   24.120369]  [<c0163a3e>] run_workqueue+0x8e/0x150
[   24.120382]  [<f8a2a0b0>] ? process_unsol_events+0x0/0x70 [snd_hda_codec]
[   24.120391]  [<c0163b84>] worker_thread+0x84/0xe0
[   24.120399]  [<c0167b00>] ? autoremove_wake_function+0x0/0x50
[   24.120406]  [<c0163b00>] ? worker_thread+0x0/0xe0
[   24.120413]  [<c0167874>] kthread+0x74/0x80
[   24.120420]  [<c0167800>] ? kthread+0x0/0x80
[   24.120428]  [<c0104087>] kernel_thread_helper+0x7/0x10
[   24.120434] ---[ end trace adeaf3eea0334255 ]---
[   24.120439] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
[   25.795655] CPU0 attaching NULL sched-domain.
[   25.795667] CPU1 attaching NULL sched-domain.
[   25.795673] CPU2 attaching NULL sched-domain.
[   25.795678] CPU3 attaching NULL sched-domain.
[   25.820126] CPU0 attaching sched-domain:
[   25.820134]  domain 0: span 0,2 level SIBLING
[   25.820140]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[   25.820153]   domain 1: span 0,2 level MC
[   25.820159]    groups: 0,2 (cpu_power = 1178)
[   25.820168]    domain 2: span 0-3 level CPU
[   25.820173]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   25.820187] CPU1 attaching sched-domain:
[   25.820192]  domain 0: span 1,3 level SIBLING
[   25.820197]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[   25.820209]   domain 1: span 1,3 level MC
[   25.820214]    groups: 1,3 (cpu_power = 1178)
[   25.820223]    domain 2: span 0-3 level CPU
[   25.820228]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   25.820241] CPU2 attaching sched-domain:
[   25.820246]  domain 0: span 0,2 level SIBLING
[   25.820251]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[   25.820263]   domain 1: span 0,2 level MC
[   25.820268]    groups: 0,2 (cpu_power = 1178)
[   25.820277]    domain 2: span 0-3 level CPU
[   25.820282]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   25.820295] CPU3 attaching sched-domain:
[   25.820300]  domain 0: span 1,3 level SIBLING
[   25.820305]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   25.820317]   domain 1: span 1,3 level MC
[   25.820322]    groups: 1,3 (cpu_power = 1178)
[   25.820331]    domain 2: span 0-3 level CPU
[   25.820336]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   28.239137] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 177
[   28.652808] ---> RTMPFreeTxRxRingMemory
[   28.652867] <--- RTMPFreeTxRxRingMemory
[   28.934577] <-- RTMPAllocTxRxRingMemory, Status=0
[   28.936456] -->RTUSBVenderReset
[   28.936589] <--RTUSBVenderReset
[   29.212829] 1. Phy Mode = 0
[   29.212834] 2. Phy Mode = 0
[   29.252335] 3. Phy Mode = 0
[   29.257211] MCS Set = 00 00 00 00 00
[   29.266467] <==== rt28xx_init, Status=0
[   29.267963] 0x1300 = 00073200
[   29.568699] ---> RTMPFreeTxRxRingMemory
[   29.568747] <--- RTMPFreeTxRxRingMemory
[   29.602653] jme 0000:02:00.5: irq 27 for MSI/MSI-X
[   29.602996] eth0: Link is down.
[   29.603366] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.928346] <-- RTMPAllocTxRxRingMemory, Status=0
[   29.930222] -->RTUSBVenderReset
[   29.930332] <--RTUSBVenderReset
[   30.221959] 1. Phy Mode = 0
[   30.221966] 2. Phy Mode = 0
[   30.261456] 3. Phy Mode = 0
[   30.266336] MCS Set = 00 00 00 00 00
[   30.275706] <==== rt28xx_init, Status=0
[   30.277339] 0x1300 = 00073200
[   32.428180] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   37.515262] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 177
[   37.515521] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[   40.732018] wlan0: no IPv6 routers present
[  300.984661] ---> RTMPFreeTxRxRingMemory
[  300.984719] <--- RTMPFreeTxRxRingMemory
[  301.263172] <-- RTMPAllocTxRxRingMemory, Status=0
[  301.264934] -->RTUSBVenderReset
[  301.265061] <--RTUSBVenderReset
[  301.550952] 1. Phy Mode = 0
[  301.550958] 2. Phy Mode = 0
[  301.590474] 3. Phy Mode = 0
[  301.595359] MCS Set = 00 00 00 00 00
[  301.604606] <==== rt28xx_init, Status=0
[  301.606103] 0x1300 = 000a4200
[  301.911025] ---> RTMPFreeTxRxRingMemory
[  301.911087] <--- RTMPFreeTxRxRingMemory
[  301.943514] jme 0000:02:00.5: irq 27 for MSI/MSI-X
[  301.943855] eth0: Link is down.
[  301.944242] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  305.854900] <-- RTMPAllocTxRxRingMemory, Status=0
[  305.856731] -->RTUSBVenderReset
[  305.856856] <--RTUSBVenderReset
[  306.138745] 1. Phy Mode = 0
[  306.138752] 2. Phy Mode = 0
[  306.178287] 3. Phy Mode = 0
[  306.183151] MCS Set = 00 00 00 00 00
[  306.192398] <==== rt28xx_init, Status=0
[  306.193900] 0x1300 = 000a4200
[  307.852143] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 177
[  308.286917] ---> RTMPFreeTxRxRingMemory
[  308.286967] <--- RTMPFreeTxRxRingMemory
[  308.565947] <-- RTMPAllocTxRxRingMemory, Status=0
[  308.567707] -->RTUSBVenderReset
[  308.567833] <--RTUSBVenderReset
[  308.851101] 1. Phy Mode = 0
[  308.851108] 2. Phy Mode = 0
[  308.890626] 3. Phy Mode = 0
[  308.895502] MCS Set = 00 00 00 00 00
[  308.904601] <==== rt28xx_init, Status=0
[  308.906127] 0x1300 = 000a4200
[  308.998462] jme 0000:02:00.5: irq 27 for MSI/MSI-X
[  308.998816] eth0: Link is down.
[  308.999191] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  309.288432] ---> RTMPFreeTxRxRingMemory
[  309.288480] <--- RTMPFreeTxRxRingMemory
[  309.616005] <-- RTMPAllocTxRxRingMemory, Status=0
[  309.617983] -->RTUSBVenderReset
[  309.618112] <--RTUSBVenderReset
[  309.901254] 1. Phy Mode = 0
[  309.901261] 2. Phy Mode = 0
[  309.940776] 3. Phy Mode = 0
[  309.945652] MCS Set = 00 00 00 00 00
[  309.954906] <==== rt28xx_init, Status=0
[  309.956413] 0x1300 = 000a4200
[  312.092491] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  317.180162] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 177
[  317.180419] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  320.348019] wlan0: no IPv6 routers present

```

[B]iwlist scan
[/B]```
wlan0     Scan completed :
          Cell 01 - Address: 00:22:6B:F7:A0:48
                    Protocol:802.11b/g/n
                    ESSID:"Cliff House"
                    Mode:Managed
                    Channel:11
                    Quality:81/100  Signal level:-58 dBm  Noise level:-71 dBm
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
```

[B]lsb_release -d
[/B]```
Description:    Ubuntu 10.04.1 LTS - XBMCLive Dharma
```

**uname -mr**
```
2.6.32-26-generic i686
```

---

### Post by chili555 on 2011-06-30
If you don't mind, I'll scratch my gray beard. You seem to have two wireless devices. Do I assume the internal Realtek is what you're trying to drive with ndiswrapper? Why do you have two wireless devices? The USB can be made to work quite well with one change. 

I suspect ndiswrapper is not loading on boot; also fixed easily. Why two wireless cards?

---

### Post by booah on 2011-06-30
> **chili555 said:**
> If you don't mind, I'll scratch my gray beard. You seem to have two wireless devices. Do I assume the internal Realtek is what you're trying to drive with ndiswrapper? Why do you have two wireless devices? The USB can be made to work quite well with one change. 

I suspect ndiswrapper is not loading on boot; also fixed easily. Why two wireless cards?

Chilli555 thanks very much for the reply and belated congrats on 10k+ posts :)

Sorry I was putting this post together and my brother and his GF stole my xbmc machine to watch a movie. 

You're spot on there are two wireless devices. The wireless network card that came with my shuttle xs35gt is so bad that I had to buy a usb network adapter and I blacklisted the original, internal card:

**sudo nano /etc/modprobe.d/blacklist.conf**
```
#wireless networkcard (blocked in favour of usb controller)
blacklist rt1819xSE
blacklist r8192se_pci

#alternatite driver - ndiswrapper -l (i was testing this line at one point to see if it helped i left in it in case you think its useful)
#blacklist rt2800usb
```
is this the command you were talking about? This is my current /etc/modules

**sudo nano /etc/modules**
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
ndiswrapper
```

As it stands when I boot up my box if the network is found : great -> really fast speed, reliable, very low chance of cutting off (but i think if its cuts off it wont come back).

If I boot up and no network : it will never get a network connection unless I shutdown and restart.

I will get the output of the commands in the 2nd post now for when the machine is not connected to the network.

Thank you very much for looking at this, I have been struggling with this problem for weeks :p

---

### Post by booah on 2011-06-30
[B]Cant establish connection (from startup)

lspci
[/B]```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a6f (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
02:00.5 Ethernet controller: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
```

[B]lsusb
[/B]```
Bus 005 Device 002: ID 045e:006d Microsoft Corp. eHome Remote Control Keyboard keys
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05a4:1000 Ortek Technology, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1058:1021 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 157e:300e TRENDnet 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

[B]ifconfig
[/B]```
eth0      Link encap:Ethernet  HWaddr 80:ee:73:07:8b:07  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```

[B]iwconfig
[/B]```
wlan2     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

[B]lsmod
[/B]```
Module                  Size  Used by
dm_crypt               11331  0 
snd_hda_codec_nvhdmi    12722  1 
snd_hda_codec_idt      54083  1 
rt2800usb               7220  0 
rt2800lib              28358  1 rt2800usb
rt2x00usb               9662  2 rt2800usb,rt2800lib
rt2x00lib              26746  2 rt2800lib,rt2x00usb
compat_firmware_class     6554  1 rt2x00lib
mac80211              232535  2 rt2x00usb,rt2x00lib
cfg80211              146764  2 rt2x00lib,mac80211
snd_hda_intel          20799  3 
snd_hda_codec          87096  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5668  1 snd_hda_codec
snd_pcm_oss            34603  0 
snd_mixer_oss          13929  1 snd_pcm_oss
snd_pcm                71646  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
rt2870sta             399316  0 
snd_seq_dummy           1498  0 
snd_seq_oss            27626  0 
snd_seq_midi            4621  0 
snd_rawmidi            19141  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                48042  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lirc_mceusb            12402  1 
snd_timer              18710  3 snd_pcm,snd_seq
crc_ccitt               1339  2 rt2800usb,rt2870sta
lirc_dev                8884  3 lirc_mceusb
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           184677  0 
nvidia               9961216  37 
jmb38x_ms               7311  0 
snd                    56687  19 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci               5470  0 
jme                    27953  0 
mii                     4381  1 jme
sdhci                  15462  1 sdhci_pci
psmouse                63245  0 
serio_raw               3978  0 
memstick                8237  1 jmb38x_ms
led_class               2864  2 rt2x00lib,sdhci
vga16fb                11385  0 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7140  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  1 lp
usbhid                 36110  0 
hid                    67032  1 usbhid
usb_storage            39553  1 
vesafb                  3542  0 
intel_agp              24375  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
agpgart                31724  2 nvidia,intel_agp
video                  17375  0 
output                  1871  1 video
ramzswap                6362  1 
xvmalloc                4074  1 ramzswap
lzo_decompress          2189  1 ramzswap
lzo_compress            1853  1 ramzswap

```

[B]dmesg
[/B]```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-26-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 (Ubuntu 2.6.32-26.48-generic 2.6.32.24+drm33.11)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
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
[    0.000000]  modified: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  modified: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  modified: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 371d5000 - 37fef641
[    0.000000] Allocated new RAMDISK: 008e1000 - 016fb641
[    0.000000] Move RAMDISK from 00000000371d5000 - 0000000037fef640 to 008e1000 - 016fb640
[    0.000000] ACPI: RSDP 000f9eb0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 7ffb0100 00054 (v01 Shuttl Shuttle  20100728 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffb0290 000F4 (v04 072810 FACP1536 20100728 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffb05c0 06645 (v02  XS350  XS35V10 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 7ffbe000 00040
[    0.000000] ACPI: APIC 7ffb0390 0006C (v02 072810 APIC1536 20100728 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffb0400 0003C (v01 072810 OEMMCFG  20100728 MSFT 00000097)
[    0.000000] ACPI: SLIC 7ffb0440 00176 (v01 Shuttl Shuttle  20100728 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffbe040 00072 (v01 072810 OEMB1536 20100728 MSFT 00000097)
[    0.000000] ACPI: HPET 7ffba5c0 00038 (v01 072810 OEMHPET  20100728 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dced8]    TEXT DATA BSS ==> [0000100000 - 00008dced8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008dd000 - 00008e01ab]              BRK ==> [00008dd000 - 00008e01ab]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008e1000 - 00016fb641]      NEW RAMDISK ==> [00008e1000 - 00016fb641]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffb0
[    0.000000] On node 0 totalpages: 524095
[    0.000000] free_area_init_node: node 0, pgdat c079a760, node_mem_map c16fd200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294562 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2800000 s36056 r0 d21288 u1048576
[    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=5f9e13ad-a33a-4057-8b66-9e0e218e4784 ro quiet splash xbmc=autostart,nodiskmount loglevel=0 video=vesafb
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10483840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffb0)
[    0.000000] Memory: 2044956k/2096832k available (4682k kernel code, 50220k reserved, 2121k data, 656k init, 1187528k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc0849000   ( 656 kB)
[    0.000000]       .data : 0xc0592847 - 0xc07a4e68   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0592847   (4682 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.819 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.63 BogoMIPS (lpj=6651276)
[    0.004044] Security Framework initialized
[    0.004085] AppArmor: AppArmor initialized
[    0.004101] Mount-cache hash table entries: 512
[    0.004329] Initializing cgroup subsys ns
[    0.004340] Initializing cgroup subsys cpuacct
[    0.004350] Initializing cgroup subsys memory
[    0.004364] Initializing cgroup subsys devices
[    0.004370] Initializing cgroup subsys freezer
[    0.004375] Initializing cgroup subsys net_cls
[    0.004411] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004418] CPU: L2 cache: 512K
[    0.004423] CPU: Physical Processor ID: 0
[    0.004427] CPU: Processor Core ID: 0
[    0.004434] mce: CPU supports 5 MCE banks
[    0.004448] CPU0: Thermal monitoring enabled (TM1)
[    0.004456] using mwait in idle threads.
[    0.004466] Performance Events: Atom events, Intel PMU driver.
[    0.004483] ... version:                3
[    0.004487] ... bit width:              40
[    0.004492] ... generic registers:      2
[    0.004497] ... value mask:             000000ffffffffff
[    0.004502] ... max period:             000000007fffffff
[    0.004506] ... fixed-purpose events:   3
[    0.004511] ... event mask:             0000000700000003
[    0.004519] Checking 'hlt' instruction... OK.
[    0.020007] Disabling 4MB page tables to avoid TLB bug
[    0.024196] ACPI: Core revision 20090903
[    0.040017] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040028] ftrace: allocating 21794 entries in 43 pages
[    0.048102] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048434] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.091790] CPU0: Intel(R) Atom(TM) CPU D510   @ 1.66GHz stepping 0a
[    0.092001] Booting processor 1 APIC 0x2 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM1)
[    0.176134] CPU1: Intel(R) Atom(TM) CPU D510   @ 1.66GHz stepping 0a
[    0.176157] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.180187] Booting processor 2 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#2
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU2: Thermal monitoring enabled (TM1)
[    0.268078] CPU2: Intel(R) Atom(TM) CPU D510   @ 1.66GHz stepping 0a
[    0.268109] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.272211] Booting processor 3 APIC 0x3 ip 0x6000
[    0.008000] Initializing CPU#3
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU3: Thermal monitoring enabled (TM1)
[    0.360113] CPU3: Intel(R) Atom(TM) CPU D510   @ 1.66GHz stepping 0a
[    0.360139] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.364025] Brought up 4 CPUs
[    0.364032] Total of 4 processors activated (13300.51 BogoMIPS).
[    0.365419] CPU0 attaching sched-domain:
[    0.365428]  domain 0: span 0,2 level SIBLING
[    0.365434]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[    0.365447]   domain 1: span 0,2 level MC
[    0.365452]    groups: 0,2 (cpu_power = 1178)
[    0.365461]    domain 2: span 0-3 level CPU
[    0.365466]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    0.365482] CPU1 attaching sched-domain:
[    0.365487]  domain 0: span 1,3 level SIBLING
[    0.365492]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[    0.365504]   domain 1: span 1,3 level MC
[    0.365509]    groups: 1,3 (cpu_power = 1178)
[    0.365518]    domain 2: span 0-3 level CPU
[    0.365523]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    0.365536] CPU2 attaching sched-domain:
[    0.365541]  domain 0: span 0,2 level SIBLING
[    0.365546]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[    0.365558]   domain 1: span 0,2 level MC
[    0.365563]    groups: 0,2 (cpu_power = 1178)
[    0.365571]    domain 2: span 0-3 level CPU
[    0.365576]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    0.365589] CPU3 attaching sched-domain:
[    0.365594]  domain 0: span 1,3 level SIBLING
[    0.365599]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[    0.365611]   domain 1: span 1,3 level MC
[    0.365616]    groups: 1,3 (cpu_power = 1178)
[    0.365625]    domain 2: span 0-3 level CPU
[    0.365630]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    0.365987] devtmpfs: initialized
[    0.365987] regulator: core version 0.5
[    0.365987] Time: 18:51:47  Date: 06/30/11
[    0.365987] NET: Registered protocol family 16
[    0.365987] Trying to unpack rootfs image as initramfs...
[    0.365987] EISA bus registered
[    0.365987] ACPI: bus type pci registered
[    0.365987] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.365987] PCI: Not using MMCONFIG.
[    0.368075] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.368080] PCI: Using configuration type 1 for base access
[    0.369913] bio: create slab <bio-0> at 0
[    0.369913] ACPI: EC: Look up EC in DSDT
[    0.374111] ACPI Error: No handler for Region [ECRM] (f70119d8) [EmbeddedControl] (20090903/evregion-319)
[    0.374126] ACPI Error: Region EmbeddedControl(3) has no handler (20090903/exfldio-295)
[    0.374139] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_._REG] (Node f7015390), AE_NOT_EXIST
[    0.374896] ACPI: Executed 1 blocks of module-level executable AML code
[    0.384034] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.872101] ACPI: Interpreter enabled
[    0.872110] ACPI: (supports S0 S3 S4 S5)
[    0.872161] ACPI: Using IOAPIC for interrupt routing
[    0.872256] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.875444] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.875450] PCI: Using MMCONFIG for extended config space
[    0.888023] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.888453] ACPI: No dock devices found.
[    0.888756] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.888930] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfcffc000-0xfcffffff]
[    0.888980] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.888987] pci 0000:00:1b.0: PME# disabled
[    0.889063] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.889070] pci 0000:00:1c.0: PME# disabled
[    0.889144] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.889151] pci 0000:00:1c.1: PME# disabled
[    0.889225] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.889231] pci 0000:00:1c.3: PME# disabled
[    0.889287] pci 0000:00:1d.0: reg 20 io port: [0xbc00-0xbc1f]
[    0.889344] pci 0000:00:1d.1: reg 20 io port: [0xb880-0xb89f]
[    0.889400] pci 0000:00:1d.2: reg 20 io port: [0xb800-0xb81f]
[    0.889456] pci 0000:00:1d.3: reg 20 io port: [0xb480-0xb49f]
[    0.889518] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfcffbc00-0xfcffbfff]
[    0.889575] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.889583] pci 0000:00:1d.7: PME# disabled
[    0.889762] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.889772] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.889782] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.889792] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.889801] pci 0000:00:1f.2: reg 20 io port: [0xff90-0xff9f]
[    0.889810] pci 0000:00:1f.2: reg 24 32bit mmio: [0x00fc00-0x00ffff]
[    0.889836] pci 0000:00:1f.2: PME# supported from D3hot
[    0.889843] pci 0000:00:1f.2: PME# disabled
[    0.889899] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.889979] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.889996] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.890014] pci 0000:01:00.0: reg 1c 64bit mmio pref: [0xce000000-0xcfffffff]
[    0.890025] pci 0000:01:00.0: reg 24 io port: [0xcc00-0xcc7f]
[    0.890037] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfe980000-0xfe9fffff]
[    0.890137] pci 0000:01:00.1: reg 10 32bit mmio: [0xfe97c000-0xfe97ffff]
[    0.890261] pci 0000:00:1c.0: bridge io port: [0xc000-0xcfff]
[    0.890269] pci 0000:00:1c.0: bridge 32bit mmio: [0xfd000000-0xfe9fffff]
[    0.890279] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xce000000-0xdfffffff]
[    0.890334] pci 0000:02:00.0: reg 10 32bit mmio: [0xfeaffc00-0xfeaffcff]
[    0.890481] pci 0000:02:00.2: reg 10 32bit mmio: [0xfeaff800-0xfeaff8ff]
[    0.890622] pci 0000:02:00.3: reg 10 32bit mmio: [0xfeaff400-0xfeaff4ff]
[    0.890765] pci 0000:02:00.5: reg 10 32bit mmio: [0xfeaf8000-0xfeafbfff]
[    0.890786] pci 0000:02:00.5: reg 18 io port: [0xdc00-0xdc7f]
[    0.890798] pci 0000:02:00.5: reg 1c io port: [0xd800-0xd8ff]
[    0.890864] pci 0000:02:00.5: PME# supported from D0 D3hot D3cold
[    0.890872] pci 0000:02:00.5: PME# disabled
[    0.890935] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.890942] pci 0000:00:1c.1: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.891001] pci 0000:03:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.891014] pci 0000:03:00.0: reg 14 32bit mmio: [0xfebfc000-0xfebfffff]
[    0.891082] pci 0000:03:00.0: supports D1 D2
[    0.891087] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[    0.891095] pci 0000:03:00.0: PME# disabled
[    0.891158] pci 0000:00:1c.3: bridge io port: [0xe000-0xefff]
[    0.891165] pci 0000:00:1c.3: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.891225] pci 0000:00:1e.0: transparent bridge
[    0.891255] pci_bus 0000:00: on NUMA node 0
[    0.891265] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.891463] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.891599] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.891705] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.891847] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.909381] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.909592] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.909800] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.910007] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.910214] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.910424] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.910633] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.910844] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.911087] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.911099] vgaarb: loaded
[    0.911343] SCSI subsystem initialized
[    0.911382] libata version 3.00 loaded.
[    0.911382] usbcore: registered new interface driver usbfs
[    0.911382] usbcore: registered new interface driver hub
[    0.911382] usbcore: registered new device driver usb
[    0.912209] ACPI: WMI: Mapper loaded
[    0.912214] PCI: Using ACPI for IRQ routing
[    0.912315] pci 0000:00:1f.2: BAR 5: address space collision on of device [0x00fc00-0x00ffff]
[    0.912321] pci 0000:00:1f.2: BAR 5: can't allocate resource
[    0.912528] NetLabel: Initializing
[    0.912533] NetLabel:  domain hash size = 128
[    0.912537] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.912560] NetLabel:  unlabeled traffic allowed by default
[    0.912661] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.912673] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.920302] Switching to clocksource tsc
[    0.924110] AppArmor: AppArmor Filesystem Enabled
[    0.924142] pnp: PnP ACPI init
[    0.924173] ACPI: bus type pnp registered
[    0.928414] pnp: PnP ACPI: found 15 devices
[    0.928420] ACPI: ACPI bus type pnp unregistered
[    0.928429] PnPBIOS: Disabled by ACPI PNP
[    0.928454] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.928461] system 00:01: iomem range 0xfed90000-0xfed93fff has been reserved
[    0.928480] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.928487] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.928494] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.928501] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.928508] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.928523] system 00:0b: iomem range 0xffc00000-0xffefffff has been reserved
[    0.928536] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.928543] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.928556] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.928569] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.928576] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.928583] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.928590] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[    0.928597] system 00:0e: iomem range 0xfed90000-0xffffffff could not be reserved
[    0.963575] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.963584] pci 0000:00:1c.0:   IO window: 0xc000-0xcfff
[    0.963592] pci 0000:00:1c.0:   MEM window: 0xfd000000-0xfe9fffff
[    0.963600] pci 0000:00:1c.0:   PREFETCH window: 0x000000ce000000-0x000000dfffffff
[    0.963611] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.963617] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.963625] pci 0000:00:1c.1:   MEM window: 0xfea00000-0xfeafffff
[    0.963633] pci 0000:00:1c.1:   PREFETCH window: 0x00000080000000-0x000000801fffff
[    0.963642] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    0.963649] pci 0000:00:1c.3:   IO window: 0xe000-0xefff
[    0.963657] pci 0000:00:1c.3:   MEM window: 0xfeb00000-0xfebfffff
[    0.963664] pci 0000:00:1c.3:   PREFETCH window: 0x00000080200000-0x000000803fffff
[    0.963674] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.963678] pci 0000:00:1e.0:   IO window: disabled
[    0.963685] pci 0000:00:1e.0:   MEM window: disabled
[    0.963691] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.963715]   alloc irq_desc for 16 on node -1
[    0.963720]   alloc kstat_irqs on node -1
[    0.963732] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.963740] pci 0000:00:1c.0: setting latency timer to 64
[    0.963753]   alloc irq_desc for 17 on node -1
[    0.963757]   alloc kstat_irqs on node -1
[    0.963766] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.963774] pci 0000:00:1c.1: setting latency timer to 64
[    0.963844] pci 0000:00:1c.3: power state changed by ACPI to D0
[    0.963899] pci 0000:00:1c.3: power state changed by ACPI to D0
[    0.963909]   alloc irq_desc for 19 on node -1
[    0.963914]   alloc kstat_irqs on node -1
[    0.963923] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.963930] pci 0000:00:1c.3: setting latency timer to 64
[    0.963942] pci 0000:00:1e.0: setting latency timer to 64
[    0.963950] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.963956] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.963962] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.963968] pci_bus 0000:01: resource 1 mem: [0xfd000000-0xfe9fffff]
[    0.963974] pci_bus 0000:01: resource 2 pref mem [0xce000000-0xdfffffff]
[    0.963981] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.963986] pci_bus 0000:02: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.963992] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x801fffff]
[    0.963999] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.964005] pci_bus 0000:03: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.964011] pci_bus 0000:03: resource 2 pref mem [0x80200000-0x803fffff]
[    0.964017] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.964023] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.964096] NET: Registered protocol family 2
[    0.964302] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.964945] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.965869] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.966294] TCP: Hash tables configured (established 131072 bind 65536)
[    0.966300] TCP reno registered
[    0.966540] NET: Registered protocol family 1
[    0.966708] pci 0000:01:00.0: Boot video device
[    0.967361] cpufreq-nforce2: No nForce2 chipset.
[    0.967417] Scanning for low memory corruption every 60 seconds
[    0.967642] audit: initializing netlink socket (disabled)
[    0.967666] type=2000 audit(1309459907.966:1): initialized
[    0.984279] highmem bounce pool size: 64 pages
[    0.984291] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.987784] VFS: Disk quotas dquot_6.5.2
[    0.987914] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.989243] fuse init (API version 7.13)
[    0.989439] msgmni has been set to 1677
[    0.989979] alg: No test for stdrng (krng)
[    0.990120] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.990128] io scheduler noop registered
[    0.990132] io scheduler anticipatory registered
[    0.990136] io scheduler deadline registered
[    0.990235] io scheduler cfq registered (default)
[    0.990482]   alloc irq_desc for 24 on node -1
[    0.990488]   alloc kstat_irqs on node -1
[    0.990504] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.990517] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.990692]   alloc irq_desc for 25 on node -1
[    0.990697]   alloc kstat_irqs on node -1
[    0.990709] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.990721] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.990896]   alloc irq_desc for 26 on node -1
[    0.990901]   alloc kstat_irqs on node -1
[    0.990913] pcieport 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.990935] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.991097] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.991296] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.991491] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.991500] ACPI: Sleep Button [SLPB]
[    0.991596] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.991602] ACPI: Power Button [PWRB]
[    0.991703] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.991710] ACPI: Power Button [PWRF]
[    0.993031] processor LNXCPU:00: registered as cooling_device0
[    0.993836] processor LNXCPU:01: registered as cooling_device1
[    0.994637] processor LNXCPU:02: registered as cooling_device2
[    0.995460] processor LNXCPU:03: registered as cooling_device3
[    1.026940] Freeing initrd memory: 14441k freed
[    1.033196] thermal LNXTHERM:01: registered as thermal_zone0
[    1.033215] ACPI: Thermal Zone [TZ00] (56 C)
[    1.033737] isapnp: Scanning for PnP cards...
[    1.037352] efifb: probing for efifb
[    1.037447] efifb: framebuffer at 0xcf000000, mapped to 0xf8080000, using 1920k, total 1920k
[    1.037454] efifb: mode is 800x600x32, linelength=3200, pages=1
[    1.037458] efifb: scrolling: redraw
[    1.037465] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.037582] fb0: EFI VGA frame buffer device
[    1.037593] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.040538] brd: module loaded
[    1.041664] loop: module loaded
[    1.041873] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.042063] ata_piix 0000:00:1f.2: version 2.13
[    1.042086] ata_piix 0000:00:1f.2: enabling device (0005 -> 0007)
[    1.042098] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.042107] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.042169] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.042316] scsi0 : ata_piix
[    1.042495] scsi1 : ata_piix
[    1.045346] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
[    1.045353] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
[    1.046280] Fixed MDIO Bus: probed
[    1.046369] PPP generic driver version 2.4.2
[    1.046471] tun: Universal TUN/TAP device driver, 1.6
[    1.046476] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.046672] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.046711]   alloc irq_desc for 23 on node -1
[    1.046717]   alloc kstat_irqs on node -1
[    1.046730] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.046757] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.046764] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.046837] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.046869] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.046884] ehci_hcd 0000:00:1d.7: debug port 1
[    1.050763] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.050790] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfcffbc00
[    1.065018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.065198] usb usb1: configuration #1 chosen from 1 choice
[    1.065261] hub 1-0:1.0: USB hub found
[    1.065278] hub 1-0:1.0: 8 ports detected
[    1.065403] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.065437] uhci_hcd: USB Universal Host Controller Interface driver
[    1.065509] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.065522] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.065528] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.065606] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.065640] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000bc00
[    1.065834] usb usb2: configuration #1 chosen from 1 choice
[    1.065895] hub 2-0:1.0: USB hub found
[    1.065915] hub 2-0:1.0: 2 ports detected
[    1.065999] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.066011] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.066017] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.066088] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.066132] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b880
[    1.066324] usb usb3: configuration #1 chosen from 1 choice
[    1.066384] hub 3-0:1.0: USB hub found
[    1.066402] hub 3-0:1.0: 2 ports detected
[    1.066486]   alloc irq_desc for 18 on node -1
[    1.066491]   alloc kstat_irqs on node -1
[    1.066502] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.066513] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.066519] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.066605] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.066649] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b800
[    1.066842] usb usb4: configuration #1 chosen from 1 choice
[    1.066902] hub 4-0:1.0: USB hub found
[    1.066917] hub 4-0:1.0: 2 ports detected
[    1.067004] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.067015] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.067021] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.067098] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.067142] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b480
[    1.067333] usb usb5: configuration #1 chosen from 1 choice
[    1.067393] hub 5-0:1.0: USB hub found
[    1.067413] hub 5-0:1.0: 2 ports detected
[    1.067610] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.070150] i8042.c: Detected active multiplexing controller, rev 1.0.
[    1.070952] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.070971] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.070982] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.070992] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.071002] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.071234] mice: PS/2 mouse device common for all mice
[    1.071514] rtc_cmos 00:03: RTC can wake from S4
[    1.071600] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.071636] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.071890] device-mapper: uevent: version 1.0.3
[    1.072191] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.072459] device-mapper: multipath: version 1.1.0 loaded
[    1.072467] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.072757] EISA: Probing bus 0 at eisa.0
[    1.072792] EISA: Detected 0 cards.
[    1.073176] cpuidle: using governor ladder
[    1.073182] cpuidle: using governor menu
[    1.073191] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.074243] TCP cubic registered
[    1.074609] NET: Registered protocol family 10
[    1.075603] lo: Disabled Privacy Extensions
[    1.076333] NET: Registered protocol family 17
[    1.076454] Using IPI No-Shortcut mode
[    1.076652] PM: Resume from disk failed.
[    1.076674] registered taskstats version 1
[    1.077266]   Magic number: 15:503:899
[    1.077383] rtc_cmos 00:03: setting system clock to 2011-06-30 18:51:48 UTC (1309459908)
[    1.077390] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.077394] EDD information not available.
[    1.240224] ata1.00: ATA-8: OCZ-VERTEX2, 1.11, max UDMA/133
[    1.240231] ata1.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.296257] ata1.00: configured for UDMA/133
[    1.376021] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.386937] isapnp: No Plug & Play device found
[    1.387172] scsi 0:0:0:0: Direct-Access     ATA      OCZ-VERTEX2      1.11 PQ: 0 ANSI: 5
[    1.387462] sd 0:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.387508] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.387640] sd 0:0:0:0: [sda] Write Protect is off
[    1.387649] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.387732] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.388090]  sda: sda1 sda2 < sda5 >
[    1.389193] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.389236] Freeing unused kernel memory: 656k freed
[    1.389746] Write protecting the kernel text: 4684k
[    1.389818] Write protecting the kernel read-only data: 1840k
[    1.435983] ramzswap: disk size set to 1030628 kB
[    1.447190] udev: starting version 151
[    1.489708] Adding 1030624k swap on /dev/ramzswap0.  Priority:100 extents:1 across:1030624k SS
[    1.530164] usb 1-1: configuration #1 chosen from 1 choice
[    1.611081] Linux agpgart interface v0.103
[    1.620326] Console: switching to colour frame buffer device 100x37
[    1.697548] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    1.833384] usb 1-5: configuration #1 chosen from 1 choice
[    1.851887] Initializing USB Mass Storage driver...
[    1.852216] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.852438] usb-storage: device found at 4
[    1.852446] usb-storage: waiting for device to settle before scanning
[    1.852467] usbcore: registered new interface driver usb-storage
[    1.852477] USB Mass Storage support registered.
[    2.189035] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    2.372208] usb 3-2: configuration #1 chosen from 1 choice
[    2.412513] usbcore: registered new interface driver hiddev
[    2.426819] input: ORtek Wireless Touchpad Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[    2.427292] generic-usb 0003:05A4:1000.0001: input,hidraw0: USB HID v1.10 Keyboard [ORtek Wireless Touchpad Keyboard] on usb-0000:00:1d.1-2/input0
[    2.435331] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.458153] input: ORtek Wireless Touchpad Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input6
[    2.458479] generic-usb 0003:05A4:1000.0002: input,hidraw1: USB HID v1.10 Mouse [ORtek Wireless Touchpad Keyboard] on usb-0000:00:1d.1-2/input1
[    2.458553] usbcore: registered new interface driver usbhid
[    2.458561] usbhid: v2.6:USB HID core driver
[    2.617042] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    2.796118] usb 5-2: configuration #1 chosen from 1 choice
[    2.902999] Adding 2438136k swap on /dev/sda5.  Priority:-1 extents:1 across:2438136k SS
[    2.917546] udev: starting version 151
[    3.111977] lp: driver loaded but no devices found
[    3.113352] vga16fb: initializing
[    3.113482] vga16fb: mapped to 0xc00a0000
[    3.113493] vga16fb: not registering due to another framebuffer present
[    3.207589] sdhci: Secure Digital Host Controller Interface driver
[    3.207602] sdhci: Copyright(c) Pierre Ossman
[    3.214035] jme: JMicron JMC2XX ethernet driver version 1.0.5
[    3.214117] jme 0000:02:00.5: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.214142] jme 0000:02:00.5: setting latency timer to 64
[    3.216645] eth0: JMC260 Fast Ethernet ver:22 rev:2 macaddr:80:ee:73:07:8b:07
[    3.219275] sdhci-pci 0000:02:00.0: SDHCI controller found [197b:2382] (rev 80)
[    3.219315] sdhci-pci 0000:02:00.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    3.219395] sdhci-pci 0000:02:00.0: setting latency timer to 64
[    3.219487] Registered led device: mmc0::
[    3.219630] mmc0: SDHCI controller on PCI [0000:02:00.0] using ADMA
[    3.219663] sdhci-pci 0000:02:00.2: SDHCI controller found [197b:2381] (rev 80)
[    3.219692] sdhci-pci 0000:02:00.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    3.219709] sdhci-pci 0000:02:00.2: Refusing to bind to secondary interface.
[    3.219724] sdhci-pci 0000:02:00.2: PCI INT B disabled
[    3.351693] jmb38x_ms 0000:02:00.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    3.351710] jmb38x_ms 0000:02:00.3: setting latency timer to 64
[    3.437491] nvidia: module license 'NVIDIA' taints kernel.
[    3.437503] Disabling lock debugging due to kernel taint
[    6.216949] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[    6.226527] lirc_dev: IR Remote Control driver registered, major 61 
[    6.251010] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[    6.251020] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[    6.361068] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[    6.382183]   alloc irq_desc for 27 on node -1
[    6.382192]   alloc kstat_irqs on node -1
[    6.382220] jme 0000:02:00.5: irq 27 for MSI/MSI-X
[    6.382571] eth0: Link is down.
[    6.383187] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.423062] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.423082] nvidia 0000:01:00.0: setting latency timer to 64
[    6.423092] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    6.423561] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[    6.437466] rtusb init --->
[    6.522217] lirc_dev: lirc_register_driver: sample_rate: 0
[    6.530201] lirc_mceusb[2]: Microsoft Microsoft IR Transceiver on usb5:2
[    6.573658] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.573671] hda_intel: codec_mask forced to 0xff
[    6.573717] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.617032] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[    6.830132] ndiswrapper: driver rt2870 (LG-Nortel,07/28/2007, 1.00.04.0000) loaded
[    6.853704] usb-storage: device scan complete
[    6.854554] scsi 2:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[    6.856668] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.857639] sd 2:0:0:0: [sdb] 3907024896 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    6.858502] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    6.858510] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.862221] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    6.862233] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.862247]  sdb: sdb1
[    6.875630] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    6.875639] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.875649] sd 2:0:0:0: [sdb] Attached SCSI disk
[    7.142119] usbcore: registered new interface driver lirc_mceusb
[    7.230201] wlan0: ethernet device 00:13:f7:ca:80:51 using NDIS driver: rt2870, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11n Wireless Card.', 157E:300E.F.conf
[    7.231072] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[    7.231218] usbcore: registered new interface driver ndiswrapper
[    7.231240] usbcore: registered new interface driver rt2870
[    7.279606] cfg80211: Calling CRDA to update world regulatory domain
[    7.291463] cfg80211: World regulatory domain updated:
[    7.291473]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.291484]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.291493]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.291502]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.291511]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.291520]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.381170] usbcore: registered new interface driver rt2800usb
[    7.403646] ndiswrapper: changing interface name from 'wlan0' to 'wlan2'
[    7.403742] udev: renamed network interface wlan0 to wlan2
[    9.616512] ALSA hda_intel.c:712: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   10.620513] ALSA hda_intel.c:1420: Codec #1 probe error; disabling it...
[   11.665508] ALSA hda_intel.c:1420: Codec #2 probe error; disabling it...
[   12.701508] ALSA hda_intel.c:1420: Codec #3 probe error; disabling it...
[   12.763000] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   12.769653] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.769904] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.771351] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.771361] hda_intel: codec_mask forced to 0xf2
[   12.771490] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.825024] ALSA hda_intel.c:712: azx_get_response timeout, switching to polling mode: last cmd=0x400f0000
[   16.832023] ALSA hda_intel.c:1420: Codec #4 probe error; disabling it...
[   17.868022] ALSA hda_intel.c:1420: Codec #5 probe error; disabling it...
[   18.908022] ALSA hda_intel.c:1420: Codec #6 probe error; disabling it...
[   19.945026] ALSA hda_intel.c:1420: Codec #7 probe error; disabling it...
[   21.042611] CPU0 attaching NULL sched-domain.
[   21.042629] CPU1 attaching NULL sched-domain.
[   21.042638] CPU2 attaching NULL sched-domain.
[   21.042646] CPU3 attaching NULL sched-domain.
[   21.072256] CPU0 attaching sched-domain:
[   21.072268]  domain 0: span 0,2 level SIBLING
[   21.072277]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[   21.072297]   domain 1: span 0,2 level MC
[   21.072305]    groups: 0,2 (cpu_power = 1178)
[   21.072319]    domain 2: span 0-3 level CPU
[   21.072327]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   21.072351] CPU1 attaching sched-domain:
[   21.072359]  domain 0: span 1,3 level SIBLING
[   21.072367]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[   21.072385]   domain 1: span 1,3 level MC
[   21.072393]    groups: 1,3 (cpu_power = 1178)
[   21.072407]    domain 2: span 0-3 level CPU
[   21.072415]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   21.072436] CPU2 attaching sched-domain:
[   21.072443]  domain 0: span 0,2 level SIBLING
[   21.072451]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[   21.072469]   domain 1: span 0,2 level MC
[   21.072476]    groups: 0,2 (cpu_power = 1178)
[   21.072490]    domain 2: span 0-3 level CPU
[   21.072497]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   21.072519] CPU3 attaching sched-domain:
[   21.072527]  domain 0: span 1,3 level SIBLING
[   21.072534]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   21.072553]   domain 1: span 1,3 level MC
[   21.072560]    groups: 1,3 (cpu_power = 1178)
[   21.072574]    domain 2: span 0-3 level CPU
[   21.072582]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   23.425232] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   23.451760] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   24.244537] HDMI: detected monitor SONY TV
[   24.244542]      at connection type HDMI
[   24.244549] HDMI: available speakers: FL/FR
[   24.244556] ------------[ cut here ]------------
[   24.244569] WARNING: at /build/buildd/linux-2.6.32/lib/vsprintf.c:1100 vsnprintf+0x3f2/0x410()
[   24.244574] Hardware name: XS35
[   24.244578] Modules linked in: dm_crypt snd_hda_codec_nvhdmi snd_hda_codec_idt rt2800usb rt2800lib rt2x00usb rt2x00lib compat_firmware_class mac80211 cfg80211 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm rt2870sta snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq lirc_mceusb snd_timer crc_ccitt lirc_dev snd_seq_device ndiswrapper nvidia(P) jmb38x_ms snd sdhci_pci jme mii sdhci psmouse serio_raw memstick led_class vga16fb vgastate soundcore snd_page_alloc lp parport usbhid hid usb_storage vesafb intel_agp fbcon tileblit font bitblit softcursor agpgart video output ramzswap xvmalloc lzo_decompress lzo_compress
[   24.244685] Pid: 994, comm: hd-audio1 Tainted: P           2.6.32-26-generic #48-Ubuntu
[   24.244691] Call Trace:
[   24.244702]  [<c014c7b2>] warn_slowpath_common+0x72/0xa0
[   24.244710]  [<c0353972>] ? vsnprintf+0x3f2/0x410
[   24.244716]  [<c0353972>] ? vsnprintf+0x3f2/0x410
[   24.244725]  [<c014c7fa>] warn_slowpath_null+0x1a/0x20
[   24.244732]  [<c0353972>] vsnprintf+0x3f2/0x410
[   24.244741]  [<c0353a1a>] snprintf+0x1a/0x20
[   24.244757]  [<f861b64d>] snd_print_pcm_bits+0x5d/0x80 [snd_hda_codec]
[   24.244775]  [<f86247f7>] hdmi_show_short_audio_desc+0xf7/0x100 [snd_hda_codec]
[   24.244783]  [<c0353a1a>] ? snprintf+0x1a/0x20
[   24.244798]  [<f862485f>] snd_hdmi_show_eld+0x5f/0xa0 [snd_hda_codec]
[   24.244814]  [<f8624b6c>] ? snd_hdmi_get_eld+0x29c/0x2d0 [snd_hda_codec]
[   24.244829]  [<f8624b6c>] ? snd_hdmi_get_eld+0x29c/0x2d0 [snd_hda_codec]
[   24.244840]  [<f9b82706>] hdmi_unsol_event+0x106/0x110 [snd_hda_codec_nvhdmi]
[   24.244849]  [<c013fb03>] ? finish_task_switch+0x43/0xc0
[   24.244864]  [<f861b106>] process_unsol_events+0x56/0x70 [snd_hda_codec]
[   24.244873]  [<c0163a3e>] run_workqueue+0x8e/0x150
[   24.244887]  [<f861b0b0>] ? process_unsol_events+0x0/0x70 [snd_hda_codec]
[   24.244895]  [<c0163b84>] worker_thread+0x84/0xe0
[   24.244903]  [<c0167b00>] ? autoremove_wake_function+0x0/0x50
[   24.244911]  [<c0163b00>] ? worker_thread+0x0/0xe0
[   24.244918]  [<c0167874>] kthread+0x74/0x80
[   24.244925]  [<c0167800>] ? kthread+0x0/0x80
[   24.244933]  [<c0104087>] kernel_thread_helper+0x7/0x10
[   24.244939] ---[ end trace b2fd08ea86d65a94 ]---
[   24.244944] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
[   26.106262] CPU0 attaching NULL sched-domain.
[   26.106275] CPU1 attaching NULL sched-domain.
[   26.106281] CPU2 attaching NULL sched-domain.
[   26.106286] CPU3 attaching NULL sched-domain.
[   26.140109] CPU0 attaching sched-domain:
[   26.140116]  domain 0: span 0,2 level SIBLING
[   26.140123]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[   26.140136]   domain 1: span 0,2 level MC
[   26.140141]    groups: 0,2 (cpu_power = 1178)
[   26.140150]    domain 2: span 0-3 level CPU
[   26.140155]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   26.140170] CPU1 attaching sched-domain:
[   26.140175]  domain 0: span 1,3 level SIBLING
[   26.140180]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[   26.140192]   domain 1: span 1,3 level MC
[   26.140197]    groups: 1,3 (cpu_power = 1178)
[   26.140206]    domain 2: span 0-3 level CPU
[   26.140211]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   26.140224] CPU2 attaching sched-domain:
[   26.140229]  domain 0: span 0,2 level SIBLING
[   26.140234]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[   26.140246]   domain 1: span 0,2 level MC
[   26.140251]    groups: 0,2 (cpu_power = 1178)
[   26.140260]    domain 2: span 0-3 level CPU
[   26.140265]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   26.140278] CPU3 attaching sched-domain:
[   26.140283]  domain 0: span 1,3 level SIBLING
[   26.140288]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   26.140300]   domain 1: span 1,3 level MC
[   26.140305]    groups: 1,3 (cpu_power = 1178)
[   26.140314]    domain 2: span 0-3 level CPU
[   26.140319]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
```

[B]iwlist scan
[/B]```
wlan2     Scan completed :
          Cell 01 - Address: 00:22:6B:F7:A0:48
                    ESSID:"Cliff House"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
```

I notice in the **iwlist scan **that is seems to be able to see the home network. Hmm that is strange since it cant see a thing in wicd-curses. I am pretty sure I took this info when a connection was not established so I will re check right now.

---

### Post by booah on 2011-06-30
Something else which may effect things.
I did a ```
ndiswrapper -m
``` after I installed ndiswrapper

---

### Post by chili555 on 2011-06-30
You really don't need ndiswrapper for this device. Please do:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist ndiswrapper" >> /etc/modprobe.d/blacklist.conf
nano /etc/modules

```Amend it to:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
#ndiswrapper
```Reboot and tell me if rt2870sta isn't driving your device well. If so, we'll remove ndiswrapper a bit more carefully.

rt2800usb and rt2870sta conflict. That causes the trouble that makes many incorrectly turn to ndiswrapper and tranquilizers!

---

### Post by booah on 2011-06-30
> **chili555 said:**
> Reboot and tell me if rt2870sta isn't driving your device well. If so, we'll remove ndiswrapper a bit more carefully.

rt2800usb and rt2870sta conflict. That causes the trouble that makes many incorrectly turn to ndiswrapper and tranquilizers!

Oh wow... It works!!
Thank you so much Chili555, I am really amazed it got resolved so quickly and what looks like easily for you. I even booted up without the usb controller and pluged it in after a minute and it picked up the connection :P.

so rt2870sta is the driver that is connecting to the usb controller, this was the same driver that came with my original wireless network card? So if I installed a fresh OS and blacklisted the original card and rt2800usb it would just work? 
Sorry to trouble you more but I would just like to understand this bit since I kind of get the reasons for everything else.

Thank you SO MUCH again what a genius :)

---

### Post by chili555 on 2011-06-30
> this was the same driver that came with my original wireless network card? No; it is r8192se_pci.> #wireless networkcard (blocked in favour of usb controller)
[COLOR="Red"]blacklist rt1819xSE[/COLOR]
blacklist r8192se_pciBy the way, the part I've highlighted doesn't actually exist. It does no good and probably no harm. If you wanted to be OCD about it, like me, simply remove that line.

If you did a re-install, blacklist rt2800usb and r8192se_pci and enjoy. rt2870sta would take over and drive the USB device as expected. If you did a reinstall of a later version of Ubuntu, you might find that r8192se_pci works better, so try the internal before you give up and resort to the USB.

Now, let's remove the ndiswrapper stuff.```
ndiswrapper -l
```That's a lower-case L for list. When you find the driver version, rt2870 or some such, remove it with:```
sudo ndiswrapper -e rt2870
```Substitute the exact driver name you found with ndiswrapper -l. You should be all set.> I am really amazed it got resolved so quickly and what looks like easily for you. I'd love to look like some kind of super-genius, but I see rt2870sta vs. rt2800usb two or three times a *week*! When I saw this, I knew the answer:> [COLOR="Red"]rt2800usb[/COLOR]               7220  0 
rt2800lib              28358  1 rt2800usb
rt2x00usb               9662  2 rt2800usb,rt2800lib
rt2x00lib              26746  2 rt2800lib,rt2x00usb
compat_firmware_class     6554  1 rt2x00lib
mac80211              232535  2 rt2x00usb,rt2x00lib
cfg80211              146764  2 rt2x00lib,mac80211
[COLOR="Red"]rt2870sta[/COLOR]             399316  0 
[COLOR="Red"]ndiswrapper[/COLOR]           184677  0 This is to be fixed soon.

---

### Post by booah on 2011-06-30
> **chili555 said:**
> By the way, the part I've highlighted doesn't actually exist. It does no good and probably no harm. If you wanted to be OCD about it, like me, simply remove that line.


Yeah thats right as I remember thinking I had everything sorted until finally noticing the IP address was that of the built in NIC and it didnt get blacklisted until I added the second line.

> I'd love to look like some kind of super-genius
It must be that gray beard you are scratching - the fountain of all knowledge;).

Seriously amazing help I never would of gotten it working without you and it feels great now to have such a stable connection and cleaner code :D
Thank you!

---

### Post by booah on 2011-08-10
I did a clean install over a month ago and everything has been running perfectly since so thanks again Chilli555.

The only thing I had to do was install this driver and the wireless usb was picked up:

installing rt2870sta
--------------------

aptitude update
aptitude install firmware-ralink wireless-tools
modprobe rt2870sta
iwconfig
ifconfig wlan0 up

:popcorn:

---

