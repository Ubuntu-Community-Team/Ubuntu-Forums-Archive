---
title: "Wireless wont work (part 2)"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by sevic33 on 2011-01-12
I finaly manage to get my wireless card work and i get another problem right away.	
I canot connect to wireless AP if is not protected.If he protected with WEP or WPA i can connect smoothly

I tried to connect with Wicd and this is output:

```
Connection failed:Unable to get IP adress
```

If i go to properties and assigne static IP then i got this error:

```
Connectio failed:Could not contact the wireless access point
```

Access Point is Air Live WL-5460AP v2

Her some outputs from my card:

First,i got laptop,brand:Forcebook.

```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
06:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```

```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:d0:e6:07:1c  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fee6:71c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1541 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:930852 (930.8 KB)  TX bytes:210904 (210.9 KB)
          Interrupt:23 Base address:0x400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57517 (57.5 KB)  TX bytes:57517 (57.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:10:60:9b:31:a5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
 lsmod
Module                  Size  Used by
via                    37920  0 
drm                   168092  1 via
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
joydev                  8767  0 
snd_hda_codec_realtek   218227  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           184207  0 
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
psmouse                59033  0 
i2c_viapro              5777  0 
serio_raw               4022  0 
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
usbhid                 36882  0 
video                  18712  0 
hid                    67742  1 usbhid
output                  1883  1 video
via_agp                 5322  1 
via_rhine              19038  0 
agpgart                32011  2 drm,via_agp
pata_via                7332  0 
mii                     4425  1 via_rhine
sata_via                7344  2 
ramzswap                9555  0 
lzo_compress            1865  1 ramzswap

```

```
 dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-24-generic (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 (Ubuntu 2.6.35-24.42-generic 2.6.35.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fe80000 (usable)
[    0.000000]  BIOS-e820: 000000006fe80000 - 000000006fe94000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fe94000 - 000000006ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x6fe80 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 06FF00000 mask FFFF00000 uncachable
[    0.000000]   2 base 070000000 mask FF0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000006fe80000 (usable)
[    0.000000]  modified: 000000006fe80000 - 000000006fe94000 (ACPI data)
[    0.000000]  modified: 000000006fe94000 - 000000006ff00000 (ACPI NVS)
[    0.000000]  modified: 000000006ff00000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f85c0] f85c0
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 37267000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a7000 - 0172fbd7
[    0.000000] Move RAMDISK from 0000000037267000 - 0000000037fefbd6 to 009a7000 - 0172fbd6
[    0.000000] ACPI: RSDP 000f8510 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 6fe8dace 00054 (v01 PTLTD  ? XSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 6fe93e66 000F4 (v03 VN896  PTLTW    06040000 PTL_ 000F4240)
[    0.000000] ACPI: DSDT 6fe8fe7c 03F76 (v01  VIA   PTL_ACPI 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS 6fe94fc0 00040
[    0.000000] ACPI: APIC 6fe93f5a 0006A (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 6fe93fc4 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 6fe8ef8a 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 6fe8eee4 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 6fe8db22 013C2 (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 902MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0006fe80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0006fe80
[    0.000000] On node 0 totalpages: 458255
[    0.000000] free_area_init_node: node 0, pgdat c07ffd00, node_mem_map c1731200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1806 pages used for memmap
[    0.000000]   HighMem zone: 229236 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ10 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2800000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454673
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=02984b38-6ec8-408e-a2aa-6e4ab2707a59 ro splash quiet vga=0x318
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9167040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (50 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a2adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a3000 - 00009a6170]             BRK
[    0.000000]   #4 [00000f85d0 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f85c0 - 00000f85d0]    MP-table mpf
[    0.000000]   #6 [000009f800 - 000009fd71]   BIOS reserved
[    0.000000]   #7 [000009fead - 00000f85c0]   BIOS reserved
[    0.000000]   #8 [000009fd71 - 000009fead]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a7000 - 0001730000]     NEW RAMDISK
[    0.000000]   #13 [0001730000 - 0001731000]         BOOTMEM
[    0.000000]   #14 [0001731000 - 0002531000]         BOOTMEM
[    0.000000]   #15 [0002531000 - 0002531004]         BOOTMEM
[    0.000000]   #16 [0002531040 - 0002531100]         BOOTMEM
[    0.000000]   #17 [0002531100 - 0002531154]         BOOTMEM
[    0.000000]   #18 [0002531180 - 0002534180]         BOOTMEM
[    0.000000]   #19 [0002534180 - 00025341d8]         BOOTMEM
[    0.000000]   #20 [0002534200 - 0002537200]         BOOTMEM
[    0.000000]   #21 [0002537200 - 000253724e]         BOOTMEM
[    0.000000]   #22 [0002537280 - 00025373ec]         BOOTMEM
[    0.000000]   #23 [0002537400 - 0002537440]         BOOTMEM
[    0.000000]   #24 [0002537440 - 0002537480]         BOOTMEM
[    0.000000]   #25 [0002537480 - 00025374c0]         BOOTMEM
[    0.000000]   #26 [00025374c0 - 0002537500]         BOOTMEM
[    0.000000]   #27 [0002537500 - 0002537540]         BOOTMEM
[    0.000000]   #28 [0002537540 - 0002537580]         BOOTMEM
[    0.000000]   #29 [0002537580 - 00025375c0]         BOOTMEM
[    0.000000]   #30 [00025375c0 - 0002537600]         BOOTMEM
[    0.000000]   #31 [0002537600 - 0002537640]         BOOTMEM
[    0.000000]   #32 [0002537640 - 0002537680]         BOOTMEM
[    0.000000]   #33 [0002537680 - 00025376c0]         BOOTMEM
[    0.000000]   #34 [00025376c0 - 0002537700]         BOOTMEM
[    0.000000]   #35 [0002537700 - 0002537710]         BOOTMEM
[    0.000000]   #36 [0002537740 - 00025377b4]         BOOTMEM
[    0.000000]   #37 [00025377c0 - 0002537834]         BOOTMEM
[    0.000000]   #38 [0002800000 - 000280e000]         BOOTMEM
[    0.000000]   #39 [0002a00000 - 0002a0e000]         BOOTMEM
[    0.000000]   #40 [0002539840 - 0002539844]         BOOTMEM
[    0.000000]   #41 [0002539880 - 0002539884]         BOOTMEM
[    0.000000]   #42 [00025398c0 - 00025398c8]         BOOTMEM
[    0.000000]   #43 [0002539900 - 0002539908]         BOOTMEM
[    0.000000]   #44 [0002539940 - 00025399e8]         BOOTMEM
[    0.000000]   #45 [0002539a00 - 0002539a68]         BOOTMEM
[    0.000000]   #46 [0002539a80 - 000253da80]         BOOTMEM
[    0.000000]   #47 [000253da80 - 00025bda80]         BOOTMEM
[    0.000000]   #48 [00025bda80 - 00025fda80]         BOOTMEM
[    0.000000]   #49 [0002a0e000 - 00032cc0c0]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0006fe80)
[    0.000000] Memory: 1786052k/1833472k available (4931k kernel code, 46968k reserved, 2333k data, 688k init, 924168k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c5000   ( 688 kB)
[    0.000000]       .data : 0xc05d0ebe - 0xc08184e8   (2333 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d0ebe   (4931 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1828.735 MHz processor.
[    0.008006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3657.47 BogoMIPS (lpj=7314940)
[    0.008012] pid_max: default: 32768 minimum: 301
[    0.008040] Security Framework initialized
[    0.008062] AppArmor: AppArmor initialized
[    0.008064] Yama: becoming mindful.
[    0.008122] Mount-cache hash table entries: 512
[    0.008258] Initializing cgroup subsys ns
[    0.008263] Initializing cgroup subsys cpuacct
[    0.008268] Initializing cgroup subsys memory
[    0.008278] Initializing cgroup subsys devices
[    0.008280] Initializing cgroup subsys freezer
[    0.008283] Initializing cgroup subsys net_cls
[    0.008314] CPU: Physical Processor ID: 0
[    0.008316] CPU: Processor Core ID: 0
[    0.008319] mce: CPU supports 6 MCE banks
[    0.008329] CPU0: Thermal monitoring enabled (TM2)
[    0.008333] using mwait in idle threads.
[    0.008339] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.008346] PEBS disabled due to CPU errata.
[    0.008353] ... version:                2
[    0.008355] ... bit width:              40
[    0.008357] ... generic registers:      2
[    0.008360] ... value mask:             000000ffffffffff
[    0.008362] ... max period:             000000007fffffff
[    0.008364] ... fixed-purpose events:   3
[    0.008367] ... event mask:             0000000700000003
[    0.014096] ACPI: Core revision 20100428
[    0.024030] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.024040] ftrace: allocating 21756 entries in 43 pages
[    0.028071] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.028591] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.032000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.032000] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.032000] ..... (found apic 0 pin 0) ...
[    0.075343] ....... works.
[    0.075346] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.076000] Booting Node   0, Processors  #1 Ok.
[    0.012000] Initializing CPU#1
[    0.164019] Brought up 2 CPUs
[    0.164023] Total of 2 processors activated (7315.24 BogoMIPS).
[    0.164623] devtmpfs: initialized
[    0.165132] regulator: core version 0.5
[    0.165174] Time: 15:15:54  Date: 01/12/11
[    0.165220] NET: Registered protocol family 16
[    0.165247] Trying to unpack rootfs image as initramfs...
[    0.165370] EISA bus registered
[    0.165380] ACPI: bus type pci registered
[    0.165474] PCI: MMCONFIG for domain 0000 [bus 00-06] at [mem 0xe0000000-0xe06fffff] (base 0xe0000000)
[    0.165479] PCI: MMCONFIG at [mem 0xe0000000-0xe06fffff] reserved in E820
[    0.165481] PCI: Using MMCONFIG for extended config space
[    0.165483] PCI: Using configuration type 1 for base access
[    0.172124] bio: create slab <bio-0> at 0
[    0.173362] ACPI: EC: Look up EC in DSDT
[    0.179195] ACPI: SSDT 6fe8f786 0023A (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.179535] ACPI: Dynamic OEM Table Load:
[    0.179539] ACPI: SSDT (null) 0023A (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.180047] ACPI: SSDT 6fe8f1e9 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.180442] ACPI: Dynamic OEM Table Load:
[    0.180446] ACPI: SSDT (null) 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.181095] ACPI: SSDT 6fe8f9c0 000C3 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.181428] ACPI: Dynamic OEM Table Load:
[    0.181432] ACPI: SSDT (null) 000C3 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.181756] ACPI: SSDT 6fe8f701 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.182077] ACPI: Dynamic OEM Table Load:
[    0.182081] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.182376] ACPI: Interpreter enabled
[    0.182382] ACPI: (supports S0 S3 S4 S5)
[    0.182405] ACPI: Using IOAPIC for interrupt routing
[    0.188911] ACPI: EC: GPE = 0x5, I/O: command/status = 0x66, data = 0x62
[    0.189137] ACPI: No dock devices found.
[    0.189143] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.189263] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.189481] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.189484] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.189488] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.189491] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000c3fff] (ignored)
[    0.189494] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff] (ignored)
[    0.189498] pci_root PNP0A03:00: host bridge window [mem 0x000c8000-0x000cbfff] (ignored)
[    0.189501] pci_root PNP0A03:00: host bridge window [mem 0x000cc000-0x000cffff] (ignored)
[    0.189504] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xfff7ffff] (ignored)
[    0.189544] pci 0000:00:00.0: reg 10: [mem 0xc0000000-0xc7ffffff pref]
[    0.190227] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.190232] pci 0000:00:02.0: PME# disabled
[    0.190346] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.190352] pci 0000:00:03.0: PME# disabled
[    0.190435] pci 0000:00:0f.0: reg 10: [io  0x4cb0-0x4cb7]
[    0.190444] pci 0000:00:0f.0: reg 14: [io  0x4ca4-0x4ca7]
[    0.190452] pci 0000:00:0f.0: reg 18: [io  0x4ca8-0x4caf]
[    0.190461] pci 0000:00:0f.0: reg 1c: [io  0x4ca0-0x4ca3]
[    0.190470] pci 0000:00:0f.0: reg 20: [io  0x4c80-0x4c8f]
[    0.190479] pci 0000:00:0f.0: reg 24: [io  0x4400-0x44ff]
[    0.190572] pci 0000:00:0f.1: reg 20: [io  0x4c90-0x4c9f]
[    0.190680] pci 0000:00:10.0: reg 20: [io  0x4c00-0x4c1f]
[    0.190716] pci 0000:00:10.0: supports D1 D2
[    0.190719] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.190724] pci 0000:00:10.0: PME# disabled
[    0.190784] pci 0000:00:10.1: reg 20: [io  0x4c20-0x4c3f]
[    0.190819] pci 0000:00:10.1: supports D1 D2
[    0.190822] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.190827] pci 0000:00:10.1: PME# disabled
[    0.190886] pci 0000:00:10.2: reg 20: [io  0x4c40-0x4c5f]
[    0.190922] pci 0000:00:10.2: supports D1 D2
[    0.190924] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.190930] pci 0000:00:10.2: PME# disabled
[    0.190989] pci 0000:00:10.3: reg 20: [io  0x4c60-0x4c7f]
[    0.191024] pci 0000:00:10.3: supports D1 D2
[    0.191027] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.191032] pci 0000:00:10.3: PME# disabled
[    0.191069] pci 0000:00:10.4: reg 10: [mem 0xcb300000-0xcb3000ff]
[    0.191130] pci 0000:00:10.4: supports D1 D2
[    0.191133] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.191138] pci 0000:00:10.4: PME# disabled
[    0.191358] pci 0000:00:12.0: reg 10: [io  0x4800-0x48ff]
[    0.191367] pci 0000:00:12.0: reg 14: [mem 0xcb300400-0xcb3004ff]
[    0.191421] pci 0000:00:12.0: supports D1 D2
[    0.191423] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.191429] pci 0000:00:12.0: PME# disabled
[    0.191694] pci 0000:01:00.0: reg 10: [mem 0xa0000000-0xbfffffff pref]
[    0.191702] pci 0000:01:00.0: reg 14: [mem 0xc9000000-0xc9ffffff]
[    0.191729] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.191754] pci 0000:01:00.0: supports D1 D2
[    0.191807] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.191813] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.191819] pci 0000:00:01.0:   bridge window [mem 0xc9000000-0xc9ffffff]
[    0.191824] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xbfffffff pref]
[    0.191890] pci 0000:00:02.0: PCI bridge to [bus 02-03]
[    0.191895] pci 0000:00:02.0:   bridge window [io  0x5000-0x6fff]
[    0.191901] pci 0000:00:02.0:   bridge window [mem 0xca000000-0xca7fffff]
[    0.191909] pci 0000:00:02.0:   bridge window [mem 0xc8000000-0xc87fffff 64bit pref]
[    0.191984] pci 0000:00:03.0: PCI bridge to [bus 04-05]
[    0.191990] pci 0000:00:03.0:   bridge window [io  0x7000-0x8fff]
[    0.192005] pci 0000:00:03.0:   bridge window [mem 0xca800000-0xcaffffff]
[    0.192014] pci 0000:00:03.0:   bridge window [mem 0xc8800000-0xc8ffffff 64bit pref]
[    0.192093] pci 0000:06:01.0: reg 10: [mem 0xcb000000-0xcb003fff 64bit]
[    0.192150] pci 0000:06:01.0: PME# supported from D0 D3hot D3cold
[    0.192155] pci 0000:06:01.0: PME# disabled
[    0.192170] pci 0000:06:01.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.192222] pci 0000:00:13.0: PCI bridge to [bus 06-06]
[    0.192228] pci 0000:00:13.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.192233] pci 0000:00:13.0:   bridge window [mem 0xcb000000-0xcb0fffff]
[    0.192241] pci 0000:00:13.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.192335] pci 0000:00:13.1: PCI bridge to [bus 07-07] (subtractive decode)
[    0.192341] pci 0000:00:13.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.192346] pci 0000:00:13.1:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.192355] pci 0000:00:13.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.192358] pci 0000:00:13.1:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.192361] pci 0000:00:13.1:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.192393] pci_bus 0000:00: on NUMA node 0
[    0.192399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.192837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGC._PRT]
[    0.192909] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE0C._PRT]
[    0.193052] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SP2P._PRT]
[    0.193175] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PE._PRT]
[    0.209857] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
[    0.209969] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
[    0.210077] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *11, disabled.
[    0.210176] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *3, disabled.
[    0.210314] ACPI: PCI Interrupt Link [LNKA] (IRQs *9 10 11 12)
[    0.210454] ACPI: PCI Interrupt Link [LNKB] (IRQs 9 *10 11 12)
[    0.210588] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11 12)
[    0.210720] ACPI: PCI Interrupt Link [LNKD] (IRQs 9 10 11 12) *3
[    0.210776] HEST: Table is not found!
[    0.210894] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.210898] vgaarb: loaded
[    0.211105] SCSI subsystem initialized
[    0.211233] libata version 3.00 loaded.
[    0.211301] usbcore: registered new interface driver usbfs
[    0.211316] usbcore: registered new interface driver hub
[    0.211343] usbcore: registered new device driver usb
[    0.211497] ACPI: WMI: Mapper loaded
[    0.211500] PCI: Using ACPI for IRQ routing
[    0.211504] PCI: pci_cache_line_size set to 64 bytes
[    0.211644] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.211648] reserve RAM buffer: 000000006fe80000 - 000000006fffffff 
[    0.211763] NetLabel: Initializing
[    0.211765] NetLabel:  domain hash size = 128
[    0.211767] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.211782] NetLabel:  unlabeled traffic allowed by default
[    0.211841] Switching to clocksource tsc
[    0.225634] AppArmor: AppArmor Filesystem Enabled
[    0.225668] pnp: PnP ACPI init
[    0.225715] ACPI: bus type pnp registered
[    0.228217] pnp: PnP ACPI: found 10 devices
[    0.228220] ACPI: ACPI bus type pnp unregistered
[    0.228225] PnPBIOS: Disabled by ACPI PNP
[    0.228241] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.228245] system 00:01: [mem 0xf0012000-0xf0012fff] has been reserved
[    0.228249] system 00:01: [mem 0xf0013000-0xf0013fff] has been reserved
[    0.228258] system 00:06: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.228261] system 00:06: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.228265] system 00:06: [mem 0xfff00000-0xffffffff] has been reserved
[    0.228269] system 00:06: [mem 0xffee0000-0xffefffff] has been reserved
[    0.228272] system 00:06: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.228276] system 00:06: [mem 0xfee00000-0xfee0ffff] could not be reserved
[    0.228283] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.228287] system 00:07: [io  0xfe10-0xfe11] has been reserved
[    0.228290] system 00:07: [io  0xfe00] has been reserved
[    0.228293] system 00:07: [io  0x4000-0x407f] has been reserved
[    0.228297] system 00:07: [io  0x4100-0x411f] has been reserved
[    0.228300] system 00:07: [io  0x0378] has been reserved
[    0.228303] system 00:07: [io  0x037c] has been reserved
[    0.228307] system 00:07: [mem 0xffb00000-0xffedefff] has been reserved
[    0.264744] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x10000)
[    0.264750] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.264752] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.264761] pci 0000:00:01.0:   bridge window [mem 0xc9000000-0xc9ffffff]
[    0.264767] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xbfffffff pref]
[    0.264774] pci 0000:00:02.0: PCI bridge to [bus 02-03]
[    0.264778] pci 0000:00:02.0:   bridge window [io  0x5000-0x6fff]
[    0.264785] pci 0000:00:02.0:   bridge window [mem 0xca000000-0xca7fffff]
[    0.264791] pci 0000:00:02.0:   bridge window [mem 0xc8000000-0xc87fffff 64bit pref]
[    0.264799] pci 0000:00:03.0: PCI bridge to [bus 04-05]
[    0.264803] pci 0000:00:03.0:   bridge window [io  0x7000-0x8fff]
[    0.264811] pci 0000:00:03.0:   bridge window [mem 0xca800000-0xcaffffff]
[    0.264817] pci 0000:00:03.0:   bridge window [mem 0xc8800000-0xc8ffffff 64bit pref]
[    0.264826] pci 0000:00:13.0: PCI bridge to [bus 06-06]
[    0.264828] pci 0000:00:13.0:   bridge window [io  disabled]
[    0.264835] pci 0000:00:13.0:   bridge window [mem 0xcb000000-0xcb0fffff]
[    0.264840] pci 0000:00:13.0:   bridge window [mem pref disabled]
[    0.264848] pci 0000:00:13.1: PCI bridge to [bus 07-07]
[    0.264850] pci 0000:00:13.1:   bridge window [io  disabled]
[    0.264856] pci 0000:00:13.1:   bridge window [mem disabled]
[    0.264861] pci 0000:00:13.1:   bridge window [mem pref disabled]
[    0.264886] pci 0000:00:01.0: setting latency timer to 64
[    0.264904]   alloc irq_desc for 27 on node -1
[    0.264907]   alloc kstat_irqs on node -1
[    0.264918] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.264923] pci 0000:00:02.0: setting latency timer to 64
[    0.264935]   alloc irq_desc for 31 on node -1
[    0.264937]   alloc kstat_irqs on node -1
[    0.264942] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
[    0.264948] pci 0000:00:03.0: setting latency timer to 64
[    0.264958] pci 0000:00:13.0: setting latency timer to 64
[    0.264967] pci 0000:00:13.1: setting latency timer to 64
[    0.264974] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.264977] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.264980] pci_bus 0000:01: resource 1 [mem 0xc9000000-0xc9ffffff]
[    0.264983] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xbfffffff pref]
[    0.264986] pci_bus 0000:02: resource 0 [io  0x5000-0x6fff]
[    0.264989] pci_bus 0000:02: resource 1 [mem 0xca000000-0xca7fffff]
[    0.264992] pci_bus 0000:02: resource 2 [mem 0xc8000000-0xc87fffff 64bit pref]
[    0.264995] pci_bus 0000:04: resource 0 [io  0x7000-0x8fff]
[    0.264998] pci_bus 0000:04: resource 1 [mem 0xca800000-0xcaffffff]
[    0.265001] pci_bus 0000:04: resource 2 [mem 0xc8800000-0xc8ffffff 64bit pref]
[    0.265004] pci_bus 0000:06: resource 1 [mem 0xcb000000-0xcb0fffff]
[    0.265007] pci_bus 0000:07: resource 4 [io  0x0000-0xffff]
[    0.265009] pci_bus 0000:07: resource 5 [mem 0x00000000-0xffffffff]
[    0.265069] NET: Registered protocol family 2
[    0.265174] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.265520] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.266181] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.266528] TCP: Hash tables configured (established 131072 bind 65536)
[    0.266532] TCP reno registered
[    0.266538] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.266556] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.266674] NET: Registered protocol family 1
[    0.266695] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.266726] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.266866] pci 0000:01:00.0: Boot video device
[    0.266874] PCI: CLS 32 bytes, default 64
[    0.267136] cpufreq-nforce2: No nForce2 chipset.
[    0.267185] Scanning for low memory corruption every 60 seconds
[    0.267350] audit: initializing netlink socket (disabled)
[    0.267367] type=2000 audit(1294845353.260:1): initialized
[    0.279595] highmem bounce pool size: 64 pages
[    0.279603] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.281372] VFS: Disk quotas dquot_6.5.2
[    0.281452] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.282155] fuse init (API version 7.14)
[    0.282260] msgmni has been set to 1683
[    0.284435] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.284439] io scheduler noop registered
[    0.284441] io scheduler deadline registered
[    0.284458] io scheduler cfq registered (default)
[    0.284624] pcieport 0000:00:02.0: setting latency timer to 64
[    0.284782] pcieport 0000:00:03.0: setting latency timer to 64
[    0.284955] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.285033] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.285609] vesafb: framebuffer at 0xa0000000, mapped to 0xf8080000, using 3072k, total 3072k
[    0.285613] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.285615] vesafb: scrolling: redraw
[    0.285619] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    0.315355] Console: switching to colour frame buffer device 128x48
[    0.345245] fb0: VESA VGA frame buffer device
[    0.345323] intel_idle: MWAIT substates: 0x22220
[    0.345326] intel_idle: does not run on family 6 model 15
[    0.464136] ACPI: AC Adapter [AC] (on-line)
[    0.464259] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.464273] ACPI: Sleep Button [SBTN]
[    0.464325] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.464518] ACPI: Lid Switch [LID]
[    0.464587] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.464592] ACPI: Power Button [PWRF]
[    0.464943] ACPI: acpi_idle registered with cpuidle
[    0.468617] Monitor-Mwait will be used to enter C-1 state
[    0.468955] Monitor-Mwait will be used to enter C-2 state
[    0.468980] Monitor-Mwait will be used to enter C-3 state
[    0.468987] Marking TSC unstable due to TSC halts in idle
[    0.469992] Switching to clocksource acpi_pm
[    0.480641] thermal LNXTHERM:01: registered as thermal_zone0
[    0.480651] ACPI: Thermal Zone [TZ0] (62 C)
[    0.480765] ERST: Table is not found!
[    0.480938] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.482736] brd: module loaded
[    0.483401] loop: module loaded
[    0.483673]   alloc irq_desc for 21 on node -1
[    0.483676]   alloc kstat_irqs on node -1
[    0.483685] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.483747] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.483803] pata_acpi 0000:00:0f.1: power state changed by ACPI to D0
[    0.483836] pata_acpi 0000:00:0f.1: power state changed by ACPI to D0
[    0.484257] Fixed MDIO Bus: probed
[    0.484296] PPP generic driver version 2.4.2
[    0.484346] tun: Universal TUN/TAP device driver, 1.6
[    0.484349] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.484441] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.484467] ehci_hcd 0000:00:10.4: BAR 0: set to [mem 0xcb300000-0xcb3000ff] (PCI address [0xcb300000-0xcb3000ff]
[    0.484474] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.484497] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.484537] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.484599] ehci_hcd 0000:00:10.4: irq 21, io mem 0xcb300000
[    0.484715] isapnp: Scanning for PnP cards...
[    0.533200] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.533407] hub 1-0:1.0: USB hub found
[    0.533415] hub 1-0:1.0: 8 ports detected
[    0.533528] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.533550] uhci_hcd: USB Universal Host Controller Interface driver
[    0.533618]   alloc irq_desc for 20 on node -1
[    0.533620]   alloc kstat_irqs on node -1
[    0.533630] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.533642] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.533686] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.533729] uhci_hcd 0000:00:10.0: irq 20, io base 0x00004c00
[    0.533869] hub 2-0:1.0: USB hub found
[    0.533875] hub 2-0:1.0: 2 ports detected
[    0.533951]   alloc irq_desc for 22 on node -1
[    0.533953]   alloc kstat_irqs on node -1
[    0.533959] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.533967] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.534011] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.534068] uhci_hcd 0000:00:10.1: irq 22, io base 0x00004c20
[    0.534223] hub 3-0:1.0: USB hub found
[    0.534228] hub 3-0:1.0: 2 ports detected
[    0.534309] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.534316] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.534353] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.534376] uhci_hcd 0000:00:10.2: irq 21, io base 0x00004c40
[    0.534509] hub 4-0:1.0: USB hub found
[    0.534514] hub 4-0:1.0: 2 ports detected
[    0.534589]   alloc irq_desc for 23 on node -1
[    0.534591]   alloc kstat_irqs on node -1
[    0.534597] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.534604] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.534641] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.534677] uhci_hcd 0000:00:10.3: irq 23, io base 0x00004c60
[    0.534812] hub 5-0:1.0: USB hub found
[    0.534817] hub 5-0:1.0: 2 ports detected
[    0.534967] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.537618] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.538963] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.538970] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.539003] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.539031] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.539067] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.539196] mice: PS/2 mouse device common for all mice
[    0.539363] rtc_cmos 00:04: RTC can wake from S4
[    0.539409] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.539444] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.539568] device-mapper: uevent: version 1.0.3
[    0.564974] Freeing initrd memory: 13860k freed
[    0.574669] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.574753] device-mapper: multipath: version 1.1.1 loaded
[    0.574757] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.574927] EISA: Probing bus 0 at eisa.0
[    0.574952] Cannot allocate resource for EISA slot 4
[    0.574957] Cannot allocate resource for EISA slot 5
[    0.574959] Cannot allocate resource for EISA slot 6
[    0.574962] Cannot allocate resource for EISA slot 7
[    0.574964] Cannot allocate resource for EISA slot 8
[    0.574966] EISA: Detected 0 cards.
[    0.575148] cpuidle: using governor ladder
[    0.575277] cpuidle: using governor menu
[    0.575691] TCP cubic registered
[    0.575845] NET: Registered protocol family 10
[    0.576318] lo: Disabled Privacy Extensions
[    0.576614] NET: Registered protocol family 17
[    0.578040] Using IPI No-Shortcut mode
[    0.578171] PM: Resume from disk failed.
[    0.578185] registered taskstats version 1
[    0.578567]   Magic number: 11:180:285
[    0.578614] acpi PNP0C04:00: hash matches
[    0.578667] rtc_cmos 00:04: setting system clock to 2011-01-12 15:15:54 UTC (1294845354)
[    0.578671] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.578673] EDD information not available.
[    0.583638] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.634328] ACPI: Battery Slot [BAT0] (battery present)
[    0.796355] isapnp: No Plug & Play device found
[    0.796383] Freeing unused kernel memory: 688k freed
[    0.796760] Write protecting the kernel text: 4932k
[    0.796821] Write protecting the kernel read-only data: 1980k
[    0.818456] ramzswap: module is from the staging directory, the quality is unknown, you have been warned.
[    0.819362] ramzswap: num_devices not specified. Using default: 1
[    0.819365] ramzswap: Creating 1 devices ...
[    0.824797] udev[91]: starting version 163
[    0.901071] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    0.902716] sata_via 0000:00:0f.0: version 2.6
[    0.902733] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.902778] sata_via 0000:00:0f.0: routed to hard irq line 10
[    0.957075] scsi0 : sata_via
[    0.963702] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    0.971426] Linux agpgart interface v0.103
[    0.972081] scsi1 : sata_via
[    0.972152] ata1: SATA max UDMA/133 cmd 0x4cb0 ctl 0x4ca4 bmdma 0x4c80 irq 21
[    0.972156] ata2: SATA max UDMA/133 cmd 0x4ca8 ctl 0x4ca0 bmdma 0x4c88 irq 21
[    0.972198] pata_via 0000:00:0f.1: version 0.3.4
[    0.972278] pata_via 0000:00:0f.1: power state changed by ACPI to D0
[    0.972316] pata_via 0000:00:0f.1: power state changed by ACPI to D0
[    0.974249] scsi2 : pata_via
[    0.974395] scsi3 : pata_via
[    0.975333] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4c90 irq 14
[    0.975337] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4c98 irq 15
[    0.975393] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.981308] eth0: VIA Rhine II at 0xcb300400, 00:40:d0:e6:07:1c, IRQ 23.
[    0.982021] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[    0.982875] agpgart: Detected VIA P4M900 chipset
[    0.989751] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xc0000000
[    1.176064] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.343121] ata1.00: ATA-8: SAMSUNG HM250JI, HS100-08, max UDMA7
[    1.343130] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.358163] ata1.00: configured for UDMA/133
[    1.358411] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM250JI  HS10 PQ: 0 ANSI: 5
[    1.358650] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.358758] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.358819] sd 0:0:0:0: [sda] Write Protect is off
[    1.358823] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.358849] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.359016]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.423017] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.472044] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    1.560041] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.732472] ata4.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.60, max UDMA/33
[    1.748402] ata4.00: configured for UDMA/33
[    1.750720] scsi 3:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.60 PQ: 0 ANSI: 5
[    1.755908] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.755915] Uniform CD-ROM driver Revision: 3.20
[    1.756163] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.756281] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.767162] usbcore: registered new interface driver hiddev
[    1.770503] acpi device:18: registered as cooling_device2
[    1.770644] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:17/LNXVIDEO:00/input/input4
[    1.770714] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[    1.781134] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input5
[    1.781293] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:10.1-2/input0
[    1.781318] usbcore: registered new interface driver usbhid
[    1.781321] usbhid: USB HID core driver
[    3.631218] xor: automatically using best checksumming function: pIII_sse
[    3.648015]    pIII_sse  :  6743.000 MB/sec
[    3.648018] xor: using function: pIII_sse (6743.000 MB/sec)
[    3.672085] device-mapper: dm-raid45: initialized v0.2594b
[    3.887915] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   20.298376] udev[394]: starting version 163
[   20.358063] Adding 899604k swap on /dev/sda6.  Priority:-1 extents:1 across:899604k 
[   20.407321] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.470355] lp: driver loaded but no devices found
[   20.652244] Disabling lock debugging due to kernel taint
[   20.714662] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   20.792192] type=1400 audit(1294841774.708:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=683 comm="apparmor_parser"
[   20.792210] type=1400 audit(1294841774.708:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=670 comm="apparmor_parser"
[   20.793043] type=1400 audit(1294841774.708:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=683 comm="apparmor_parser"
[   20.793052] type=1400 audit(1294841774.712:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=670 comm="apparmor_parser"
[   20.793480] type=1400 audit(1294841774.712:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=683 comm="apparmor_parser"
[   20.793499] type=1400 audit(1294841774.712:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=670 comm="apparmor_parser"
[   20.892294]   alloc irq_desc for 17 on node -1
[   20.892299]   alloc kstat_irqs on node -1
[   20.892310] HDA Intel 0000:06:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.892378] HDA Intel 0000:06:01.0: setting latency timer to 64
[   20.892383] HDA Intel 0000:06:01.0: PCI: Disallowing DAC for device
[   20.895648] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   20.964685] hda_codec: ALC268: BIOS auto-probing.
[   20.993055] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[   21.299337] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0/0x0
[   21.336387] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input6
[   21.488613] ndiswrapper: driver rt73 (Ralink,07/28/2007, 1.02.02.0000) loaded
[   21.611794] type=1400 audit(1294841775.528:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1024 comm="apparmor_parser"
[   21.612816] type=1400 audit(1294841775.528:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1024 comm="apparmor_parser"
[   21.620380] type=1400 audit(1294841775.536:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1024 comm="apparmor_parser"
[   21.623054] type=1400 audit(1294841775.540:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1025 comm="apparmor_parser"
[   21.936176] eth0: link down
[   21.936401] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.072992] wlan0: ethernet device 00:10:60:9b:31:a5 using NDIS driver: rt73, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 148F:2573.F.conf
[   22.073513] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   22.073739] usbcore: registered new interface driver ndiswrapper
[   22.085441] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.800221] ppdev: user-space parallel port driver
[   38.157578] [drm] Initialized drm 1.1.0 20060810
[   40.847646] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   45.987276] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   51.860622] audit_printk_skb: 33 callbacks suppressed
[   51.860626] type=1400 audit(1294841805.780:23): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1997 comm="apparmor_parser"
[   81.939681] type=1400 audit(1294841835.856:24): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2095 comm="apparmor_parser"
[  112.041405] type=1400 audit(1294841865.960:25): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2192 comm="apparmor_parser"
[  142.149601] type=1400 audit(1294841896.068:26): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2283 comm="apparmor_parser"
[  172.256690] type=1400 audit(1294841926.172:27): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2374 comm="apparmor_parser"
[  202.360732] type=1400 audit(1294841956.280:28): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2481 comm="apparmor_parser"
[  232.498177] type=1400 audit(1294841986.416:29): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2612 comm="apparmor_parser"
[  262.608795] type=1400 audit(1294842016.524:30): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2727 comm="apparmor_parser"
[  292.720243] type=1400 audit(1294842046.640:31): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2822 comm="apparmor_parser"
[  322.828747] type=1400 audit(1294842076.744:32): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2923 comm="apparmor_parser"
[  352.936292] type=1400 audit(1294842106.856:33): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3060 comm="apparmor_parser"
[  372.219174] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  372.527487] eth0: link down
[  372.528367] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  372.606866] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  374.659027] type=1400 audit(1294842128.576:34): apparmor="DENIED" operation="open" parent=3149 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=3165 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[  383.043260] type=1400 audit(1294842136.960:35): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3191 comm="apparmor_parser"
[  413.160902] type=1400 audit(1294842167.080:36): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3283 comm="apparmor_parser"
[  435.603451] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  435.802254] eth0: link down
[  435.802646] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  443.268766] type=1400 audit(1294842197.188:37): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3408 comm="apparmor_parser"
[  473.377991] type=1400 audit(1294842227.296:38): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3507 comm="apparmor_parser"
[  503.485300] type=1400 audit(1294842257.404:39): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3606 comm="apparmor_parser"
[  533.593520] type=1400 audit(1294842287.512:40): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3705 comm="apparmor_parser"
[  563.700821] type=1400 audit(1294842317.620:41): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3804 comm="apparmor_parser"
[  593.811245] type=1400 audit(1294842347.728:42): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3905 comm="apparmor_parser"
[  623.920318] type=1400 audit(1294842377.840:43): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4004 comm="apparmor_parser"
[  654.026931] type=1400 audit(1294842407.944:44): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4104 comm="apparmor_parser"
[  684.133752] type=1400 audit(1294842438.052:45): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4203 comm="apparmor_parser"
[  714.240972] type=1400 audit(1294842468.160:46): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4302 comm="apparmor_parser"
[  744.341225] type=1400 audit(1294842498.260:47): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4430 comm="apparmor_parser"
[  774.435136] type=1400 audit(1294842528.352:48): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4530 comm="apparmor_parser"
[  804.530419] type=1400 audit(1294842558.448:49): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4629 comm="apparmor_parser"
[  834.628536] type=1400 audit(1294842588.544:50): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4828 comm="apparmor_parser"
[  864.725435] type=1400 audit(1294842618.644:51): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6206 comm="apparmor_parser"
[  894.830926] type=1400 audit(1294842648.748:52): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6354 comm="apparmor_parser"
[  924.938125] type=1400 audit(1294842678.856:53): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6453 comm="apparmor_parser"
[  955.045135] type=1400 audit(1294842708.964:54): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6552 comm="apparmor_parser"
[  985.152449] type=1400 audit(1294842739.072:55): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6651 comm="apparmor_parser"
[ 1015.260729] type=1400 audit(1294842769.180:56): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6750 comm="apparmor_parser"
[ 1045.375275] type=1400 audit(1294842799.292:57): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6849 comm="apparmor_parser"
[ 1075.480820] type=1400 audit(1294842829.400:58): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6948 comm="apparmor_parser"
[ 1105.592736] type=1400 audit(1294842859.508:59): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7047 comm="apparmor_parser"
[ 1135.702477] type=1400 audit(1294842889.620:60): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7146 comm="apparmor_parser"
[ 1165.812710] type=1400 audit(1294842919.732:61): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7245 comm="apparmor_parser"
[ 1195.926457] type=1400 audit(1294842949.844:62): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7348 comm="apparmor_parser"
[ 1226.031736] type=1400 audit(1294842979.948:63): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7448 comm="apparmor_parser"
[ 1256.143712] type=1400 audit(1294843010.060:64): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7547 comm="apparmor_parser"
[ 1286.253902] type=1400 audit(1294843040.172:65): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7646 comm="apparmor_parser"
[ 1316.362922] type=1400 audit(1294843070.280:66): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7745 comm="apparmor_parser"
[ 1346.470428] type=1400 audit(1294843100.388:67): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7846 comm="apparmor_parser"
[ 1376.583312] type=1400 audit(1294843130.500:68): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7945 comm="apparmor_parser"
[ 1406.690232] type=1400 audit(1294843160.608:69): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8052 comm="apparmor_parser"
[ 1436.799090] type=1400 audit(1294843190.716:70): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8151 comm="apparmor_parser"
[ 1466.906960] type=1400 audit(1294843220.824:71): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8269 comm="apparmor_parser"
[ 1497.014023] type=1400 audit(1294843250.932:72): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8368 comm="apparmor_parser"
[ 1527.121834] type=1400 audit(1294843281.040:73): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8467 comm="apparmor_parser"
[ 1557.230032] type=1400 audit(1294843311.148:74): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8566 comm="apparmor_parser"
[ 1587.338333] type=1400 audit(1294843341.256:75): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8665 comm="apparmor_parser"
[ 1605.842384] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1606.059282] eth0: link down
[ 1606.059676] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1606.133942] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1617.452834] type=1400 audit(1294843371.368:76): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8804 comm="apparmor_parser"
[ 1647.563592] type=1400 audit(1294843401.480:77): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8909 comm="apparmor_parser"
[ 1648.703483] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1648.895298] eth0: link down
[ 1648.895694] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1677.674112] type=1400 audit(1294843431.592:78): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9037 comm="apparmor_parser"
[ 1707.784520] type=1400 audit(1294843461.704:79): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9138 comm="apparmor_parser"
[ 1737.897433] type=1400 audit(1294843491.816:80): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9252 comm="apparmor_parser"
[ 1768.001473] type=1400 audit(1294843521.920:81): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9355 comm="apparmor_parser"
[ 1798.107801] type=1400 audit(1294843552.024:82): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9456 comm="apparmor_parser"
[ 1828.213919] type=1400 audit(1294843582.132:83): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9558 comm="apparmor_parser"
[ 1858.320820] type=1400 audit(1294843612.240:84): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9660 comm="apparmor_parser"
[ 1888.424329] type=1400 audit(1294843642.344:85): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9761 comm="apparmor_parser"
[ 1918.529034] type=1400 audit(1294843672.448:86): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9862 comm="apparmor_parser"
[ 1948.640428] type=1400 audit(1294843702.556:87): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9963 comm="apparmor_parser"
[ 1978.751955] type=1400 audit(1294843732.668:88): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10064 comm="apparmor_parser"
[ 2008.862891] type=1400 audit(1294843762.780:89): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10167 comm="apparmor_parser"
[ 2038.969561] type=1400 audit(1294843792.888:90): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10268 comm="apparmor_parser"
[ 2069.076719] type=1400 audit(1294843822.996:91): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10369 comm="apparmor_parser"
[ 2099.180417] type=1400 audit(1294843853.100:92): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10470 comm="apparmor_parser"
[ 2129.290842] type=1400 audit(1294843883.208:93): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10571 comm="apparmor_parser"
[ 2159.393571] type=1400 audit(1294843913.312:94): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10676 comm="apparmor_parser"
[ 2189.504911] type=1400 audit(1294843943.420:95): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10777 comm="apparmor_parser"
[ 2219.609539] type=1400 audit(1294843973.528:96): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10878 comm="apparmor_parser"
[ 2249.715149] type=1400 audit(1294844003.632:97): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10981 comm="apparmor_parser"
[ 2279.822609] type=1400 audit(1294844033.740:98): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11082 comm="apparmor_parser"
[ 2309.929683] type=1400 audit(1294844063.848:99): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11183 comm="apparmor_parser"
[ 2340.037257] type=1400 audit(1294844093.956:100): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11284 comm="apparmor_parser"
[ 2370.145099] type=1400 audit(1294844124.064:101): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11385 comm="apparmor_parser"
[ 2400.252811] type=1400 audit(1294844154.172:102): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11486 comm="apparmor_parser"
[ 2430.362160] type=1400 audit(1294844184.280:103): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11590 comm="apparmor_parser"
[ 2460.469550] type=1400 audit(1294844214.388:104): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11691 comm="apparmor_parser"
[ 2490.578129] type=1400 audit(1294844244.496:105): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11792 comm="apparmor_parser"
[ 2520.686363] type=1400 audit(1294844274.604:106): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11893 comm="apparmor_parser"
[ 2550.795763] type=1400 audit(1294844304.712:107): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11996 comm="apparmor_parser"
[ 2580.902746] type=1400 audit(1294844334.820:108): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12097 comm="apparmor_parser"
[ 2611.009507] type=1400 audit(1294844364.928:109): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12198 comm="apparmor_parser"
[ 2616.840097] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 2616.840472] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2627.680044] eth0: no IPv6 routers present
[ 2641.112506] type=1400 audit(1294844472.122:110): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12378 comm="apparmor_parser"
[ 2659.458355] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 2662.801561] lo: Disabled Privacy Extensions
[ 2671.227393] type=1400 audit(1294844502.234:111): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12523 comm="apparmor_parser"
[ 2701.335595] type=1400 audit(1294844532.342:112): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12623 comm="apparmor_parser"
[ 2731.441786] type=1400 audit(1294844562.450:113): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12722 comm="apparmor_parser"
[ 2761.562160] type=1400 audit(1294844592.570:114): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12819 comm="apparmor_parser"
[ 2791.671456] type=1400 audit(1294844622.678:115): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12914 comm="apparmor_parser"
[ 2821.779223] type=1400 audit(1294844652.786:116): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13006 comm="apparmor_parser"
[ 2851.891891] type=1400 audit(1294844682.898:117): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13099 comm="apparmor_parser"
[ 2882.006432] type=1400 audit(1294844713.014:118): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13192 comm="apparmor_parser"
[ 2912.115078] type=1400 audit(1294844743.122:119): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13313 comm="apparmor_parser"
[ 2942.222344] type=1400 audit(1294844773.230:120): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13406 comm="apparmor_parser"
[ 2972.329624] type=1400 audit(1294844803.338:121): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13518 comm="apparmor_parser"
[ 3002.447508] type=1400 audit(1294844833.454:122): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13608 comm="apparmor_parser"
[ 3032.563859] type=1400 audit(1294844863.570:123): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13699 comm="apparmor_parser"
[ 3062.677279] type=1400 audit(1294844893.686:124): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13790 comm="apparmor_parser"
[ 3092.785818] type=1400 audit(1294844923.794:125): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13881 comm="apparmor_parser"
[ 3122.896416] type=1400 audit(1294844953.902:126): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13979 comm="apparmor_parser"
[ 3153.002318] type=1400 audit(1294844984.010:127): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=14068 comm="apparmor_parser"

```

```
sudo lshw -C network
[sudo] password for sevic33: 
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:40:d0:e6:07:1c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.5 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:4800(size=256) memory:cb300400-cb3004ff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:10:60:9b:31:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.56+Ralink,07/28/2007, 1.02.02. link=no multicast=yes wireless=IEEE 802.11g

```

```
 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:4F:62:0A:37:9F
                    ESSID:"SkyGate5"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:100/100  Signal level:-24 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```
```
 uname -mr
2.6.35-24-generic i686

```

---

### Post by PatchesTheCaveman on 2011-01-13
Try using the official native Linux driver from Ralink instead of using ndiswrapper:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Also, remember to disable ndiswrapper before installing and activating that driver:
```
sudo modprobe -r ndiswrapper
sudo bash -c "echo ndiswrapper >> /etc/modprobe.d/blacklist.conf"
```

---

### Post by sevic33 on 2011-01-13
> **PatchesTheCaveman said:**
> Try using the official native Linux driver from Ralink instead of using ndiswrapper:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Also, remember to disable ndiswrapper before installing and activating that driver:
```
sudo modprobe -r ndiswrapper
sudo bash -c "echo ndiswrapper >> /etc/modprobe.d/blacklist.conf"
```

I tried to boot live backtrack 4 CD witch alrady have my wireless card suported and i have exactly the same problem,so i think the problem must be somewhere else

---

### Post by PatchesTheCaveman on 2011-01-13
There are problems with the built-in kernel driver for Ralink cards.  Installing the official one I linked to might help.

---

### Post by sevic33 on 2011-01-13
> **PatchesTheCaveman said:**
> There are problems with the built-in kernel driver for Ralink cards.  Installing the official one I linked to might help.

Ok i will try with original drivers and post result.

---

