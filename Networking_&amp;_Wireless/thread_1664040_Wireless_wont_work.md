---
title: "Wireless wont work"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by sevic33 on 2011-01-10
I cant get wireless work on my laptop with Ubuntu 10.10
 Machine Brand and Model (PC/Laptop): Forcebook
Her some outputs:
```
$ lspci
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

$lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:d0:e6:07:1c  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fee6:71c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66575434 (66.5 MB)  TX bytes:3519172 (3.5 MB)
          Interrupt:23 Base address:0x4400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15342 (15.3 KB)  TX bytes:15342 (15.3 KB)

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

```
iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

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
rt2500usb              17708  0 
arc4                    1165  2 
rt73usb                21976  0 
crc_itu_t               1383  1 rt73usb
rt2x00usb               9704  2 rt2500usb,rt73usb
rt2x00lib              29492  3 rt2500usb,rt73usb,rt2x00usb
led_class               2633  1 rt2x00lib
mac80211              235315  2 rt2x00usb,rt2x00lib
snd_hda_codec_realtek   218227  1 
joydev                  8767  0 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
cfg80211              142680  2 rt2x00lib,mac80211
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
psmouse                59033  0 
lp                      7342  0 
serio_raw               4022  0 
shpchp                 29886  0 
i2c_viapro              5777  0 
parport                31492  3 parport_pc,ppdev,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
usbhid                 36882  0 
video                  18712  0 
hid                    67742  1 usbhid
output                  1883  1 video
via_agp                 5322  1 
pata_via                7332  0 
via_rhine              19038  0 
sata_via                7344  2 
mii                     4425  1 via_rhine
agpgart                32011  2 drm,via_agp
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
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1828.696 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3657.39 BogoMIPS (lpj=7314784)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004039] Security Framework initialized
[    0.004064] AppArmor: AppArmor initialized
[    0.004067] Yama: becoming mindful.
[    0.004136] Mount-cache hash table entries: 512
[    0.004315] Initializing cgroup subsys ns
[    0.004320] Initializing cgroup subsys cpuacct
[    0.004326] Initializing cgroup subsys memory
[    0.004336] Initializing cgroup subsys devices
[    0.004339] Initializing cgroup subsys freezer
[    0.004342] Initializing cgroup subsys net_cls
[    0.004379] CPU: Physical Processor ID: 0
[    0.004381] CPU: Processor Core ID: 0
[    0.004385] mce: CPU supports 6 MCE banks
[    0.004396] CPU0: Thermal monitoring enabled (TM2)
[    0.004402] using mwait in idle threads.
[    0.004412] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.004420] PEBS disabled due to CPU errata.
[    0.004428] ... version:                2
[    0.004430] ... bit width:              40
[    0.004432] ... generic registers:      2
[    0.004435] ... value mask:             000000ffffffffff
[    0.004437] ... max period:             000000007fffffff
[    0.004439] ... fixed-purpose events:   3
[    0.004441] ... event mask:             0000000700000003
[    0.008933] ACPI: Core revision 20100428
[    0.016030] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.016040] ftrace: allocating 21756 entries in 43 pages
[    0.020072] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.020593] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.024000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.024000] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.024000] ..... (found apic 0 pin 0) ...
[    0.067124] ....... works.
[    0.067126] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.068000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.156019] Brought up 2 CPUs
[    0.156022] Total of 2 processors activated (7315.15 BogoMIPS).
[    0.156623] devtmpfs: initialized
[    0.157131] regulator: core version 0.5
[    0.157173] Time: 17:26:33  Date: 01/10/11
[    0.157219] NET: Registered protocol family 16
[    0.157245] Trying to unpack rootfs image as initramfs...
[    0.157368] EISA bus registered
[    0.157378] ACPI: bus type pci registered
[    0.157470] PCI: MMCONFIG for domain 0000 [bus 00-06] at [mem 0xe0000000-0xe06fffff] (base 0xe0000000)
[    0.157475] PCI: MMCONFIG at [mem 0xe0000000-0xe06fffff] reserved in E820
[    0.157477] PCI: Using MMCONFIG for extended config space
[    0.157479] PCI: Using configuration type 1 for base access
[    0.164124] bio: create slab <bio-0> at 0
[    0.165374] ACPI: EC: Look up EC in DSDT
[    0.171203] ACPI: SSDT 6fe8f786 0023A (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.171542] ACPI: Dynamic OEM Table Load:
[    0.171546] ACPI: SSDT (null) 0023A (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.172053] ACPI: SSDT 6fe8f1e9 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.172453] ACPI: Dynamic OEM Table Load:
[    0.172457] ACPI: SSDT (null) 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.173105] ACPI: SSDT 6fe8f9c0 000C3 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.173439] ACPI: Dynamic OEM Table Load:
[    0.173443] ACPI: SSDT (null) 000C3 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.173768] ACPI: SSDT 6fe8f701 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.174090] ACPI: Dynamic OEM Table Load:
[    0.174094] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.174387] ACPI: Interpreter enabled
[    0.174394] ACPI: (supports S0 S3 S4 S5)
[    0.174418] ACPI: Using IOAPIC for interrupt routing
[    0.180925] ACPI: EC: GPE = 0x5, I/O: command/status = 0x66, data = 0x62
[    0.181151] ACPI: No dock devices found.
[    0.181156] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.181275] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.181490] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.181494] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.181497] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.181500] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000c3fff] (ignored)
[    0.181504] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff] (ignored)
[    0.181507] pci_root PNP0A03:00: host bridge window [mem 0x000c8000-0x000cbfff] (ignored)
[    0.181510] pci_root PNP0A03:00: host bridge window [mem 0x000cc000-0x000cffff] (ignored)
[    0.181513] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xfff7ffff] (ignored)
[    0.181553] pci 0000:00:00.0: reg 10: [mem 0xc0000000-0xc7ffffff pref]
[    0.182233] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.182238] pci 0000:00:02.0: PME# disabled
[    0.182353] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.182358] pci 0000:00:03.0: PME# disabled
[    0.182441] pci 0000:00:0f.0: reg 10: [io  0x4cb0-0x4cb7]
[    0.182450] pci 0000:00:0f.0: reg 14: [io  0x4ca4-0x4ca7]
[    0.182459] pci 0000:00:0f.0: reg 18: [io  0x4ca8-0x4caf]
[    0.182468] pci 0000:00:0f.0: reg 1c: [io  0x4ca0-0x4ca3]
[    0.182477] pci 0000:00:0f.0: reg 20: [io  0x4c80-0x4c8f]
[    0.182486] pci 0000:00:0f.0: reg 24: [io  0x4400-0x44ff]
[    0.182579] pci 0000:00:0f.1: reg 20: [io  0x4c90-0x4c9f]
[    0.182687] pci 0000:00:10.0: reg 20: [io  0x4c00-0x4c1f]
[    0.182723] pci 0000:00:10.0: supports D1 D2
[    0.182725] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.182731] pci 0000:00:10.0: PME# disabled
[    0.182791] pci 0000:00:10.1: reg 20: [io  0x4c20-0x4c3f]
[    0.182826] pci 0000:00:10.1: supports D1 D2
[    0.182828] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.182834] pci 0000:00:10.1: PME# disabled
[    0.182893] pci 0000:00:10.2: reg 20: [io  0x4c40-0x4c5f]
[    0.182928] pci 0000:00:10.2: supports D1 D2
[    0.182930] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.182936] pci 0000:00:10.2: PME# disabled
[    0.182995] pci 0000:00:10.3: reg 20: [io  0x4c60-0x4c7f]
[    0.183030] pci 0000:00:10.3: supports D1 D2
[    0.183033] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.183038] pci 0000:00:10.3: PME# disabled
[    0.183078] pci 0000:00:10.4: reg 10: [mem 0xcb300000-0xcb3000ff]
[    0.183137] pci 0000:00:10.4: supports D1 D2
[    0.183139] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.183145] pci 0000:00:10.4: PME# disabled
[    0.183365] pci 0000:00:12.0: reg 10: [io  0x4800-0x48ff]
[    0.183374] pci 0000:00:12.0: reg 14: [mem 0xcb300400-0xcb3004ff]
[    0.183428] pci 0000:00:12.0: supports D1 D2
[    0.183431] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.183436] pci 0000:00:12.0: PME# disabled
[    0.183701] pci 0000:01:00.0: reg 10: [mem 0xa0000000-0xbfffffff pref]
[    0.183709] pci 0000:01:00.0: reg 14: [mem 0xc9000000-0xc9ffffff]
[    0.183736] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.183761] pci 0000:01:00.0: supports D1 D2
[    0.183814] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.183820] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.183826] pci 0000:00:01.0:   bridge window [mem 0xc9000000-0xc9ffffff]
[    0.183831] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xbfffffff pref]
[    0.183897] pci 0000:00:02.0: PCI bridge to [bus 02-03]
[    0.183902] pci 0000:00:02.0:   bridge window [io  0x5000-0x6fff]
[    0.183907] pci 0000:00:02.0:   bridge window [mem 0xca000000-0xca7fffff]
[    0.183916] pci 0000:00:02.0:   bridge window [mem 0xc8000000-0xc87fffff 64bit pref]
[    0.183991] pci 0000:00:03.0: PCI bridge to [bus 04-05]
[    0.184006] pci 0000:00:03.0:   bridge window [io  0x7000-0x8fff]
[    0.184012] pci 0000:00:03.0:   bridge window [mem 0xca800000-0xcaffffff]
[    0.184021] pci 0000:00:03.0:   bridge window [mem 0xc8800000-0xc8ffffff 64bit pref]
[    0.184099] pci 0000:06:01.0: reg 10: [mem 0xcb000000-0xcb003fff 64bit]
[    0.184156] pci 0000:06:01.0: PME# supported from D0 D3hot D3cold
[    0.184161] pci 0000:06:01.0: PME# disabled
[    0.184177] pci 0000:06:01.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.184229] pci 0000:00:13.0: PCI bridge to [bus 06-06]
[    0.184234] pci 0000:00:13.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.184240] pci 0000:00:13.0:   bridge window [mem 0xcb000000-0xcb0fffff]
[    0.184248] pci 0000:00:13.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.184342] pci 0000:00:13.1: PCI bridge to [bus 07-07] (subtractive decode)
[    0.184348] pci 0000:00:13.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.184353] pci 0000:00:13.1:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.184361] pci 0000:00:13.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.184365] pci 0000:00:13.1:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.184368] pci 0000:00:13.1:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.184400] pci_bus 0000:00: on NUMA node 0
[    0.184405] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.184844] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGC._PRT]
[    0.184915] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE0C._PRT]
[    0.185056] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SP2P._PRT]
[    0.185178] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PE._PRT]
[    0.201868] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
[    0.201983] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
[    0.202087] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *11, disabled.
[    0.202185] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *3, disabled.
[    0.202323] ACPI: PCI Interrupt Link [LNKA] (IRQs *9 10 11 12)
[    0.202463] ACPI: PCI Interrupt Link [LNKB] (IRQs 9 *10 11 12)
[    0.202596] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11 12)
[    0.202728] ACPI: PCI Interrupt Link [LNKD] (IRQs 9 10 11 12) *3
[    0.202782] HEST: Table is not found!
[    0.202898] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.202902] vgaarb: loaded
[    0.203108] SCSI subsystem initialized
[    0.203232] libata version 3.00 loaded.
[    0.203300] usbcore: registered new interface driver usbfs
[    0.203315] usbcore: registered new interface driver hub
[    0.203343] usbcore: registered new device driver usb
[    0.203498] ACPI: WMI: Mapper loaded
[    0.203501] PCI: Using ACPI for IRQ routing
[    0.203504] PCI: pci_cache_line_size set to 64 bytes
[    0.203645] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.203649] reserve RAM buffer: 000000006fe80000 - 000000006fffffff 
[    0.203763] NetLabel: Initializing
[    0.203765] NetLabel:  domain hash size = 128
[    0.203767] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.203782] NetLabel:  unlabeled traffic allowed by default
[    0.203843] Switching to clocksource tsc
[    0.217627] AppArmor: AppArmor Filesystem Enabled
[    0.217655] pnp: PnP ACPI init
[    0.217707] ACPI: bus type pnp registered
[    0.220043] pnp: PnP ACPI: found 10 devices
[    0.220046] ACPI: ACPI bus type pnp unregistered
[    0.220052] PnPBIOS: Disabled by ACPI PNP
[    0.220069] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.220073] system 00:01: [mem 0xf0012000-0xf0012fff] has been reserved
[    0.220077] system 00:01: [mem 0xf0013000-0xf0013fff] has been reserved
[    0.220086] system 00:06: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.220090] system 00:06: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.220094] system 00:06: [mem 0xfff00000-0xffffffff] has been reserved
[    0.220098] system 00:06: [mem 0xffee0000-0xffefffff] has been reserved
[    0.220102] system 00:06: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.220105] system 00:06: [mem 0xfee00000-0xfee0ffff] could not be reserved
[    0.220112] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.220116] system 00:07: [io  0xfe10-0xfe11] has been reserved
[    0.220119] system 00:07: [io  0xfe00] has been reserved
[    0.220122] system 00:07: [io  0x4000-0x407f] has been reserved
[    0.220125] system 00:07: [io  0x4100-0x411f] has been reserved
[    0.220129] system 00:07: [io  0x0378] has been reserved
[    0.220132] system 00:07: [io  0x037c] has been reserved
[    0.220135] system 00:07: [mem 0xffb00000-0xffedefff] has been reserved
[    0.256556] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x10000)
[    0.256561] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.256564] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.256572] pci 0000:00:01.0:   bridge window [mem 0xc9000000-0xc9ffffff]
[    0.256578] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xbfffffff pref]
[    0.256586] pci 0000:00:02.0: PCI bridge to [bus 02-03]
[    0.256590] pci 0000:00:02.0:   bridge window [io  0x5000-0x6fff]
[    0.256596] pci 0000:00:02.0:   bridge window [mem 0xca000000-0xca7fffff]
[    0.256602] pci 0000:00:02.0:   bridge window [mem 0xc8000000-0xc87fffff 64bit pref]
[    0.256610] pci 0000:00:03.0: PCI bridge to [bus 04-05]
[    0.256614] pci 0000:00:03.0:   bridge window [io  0x7000-0x8fff]
[    0.256622] pci 0000:00:03.0:   bridge window [mem 0xca800000-0xcaffffff]
[    0.256628] pci 0000:00:03.0:   bridge window [mem 0xc8800000-0xc8ffffff 64bit pref]
[    0.256638] pci 0000:00:13.0: PCI bridge to [bus 06-06]
[    0.256640] pci 0000:00:13.0:   bridge window [io  disabled]
[    0.256647] pci 0000:00:13.0:   bridge window [mem 0xcb000000-0xcb0fffff]
[    0.256654] pci 0000:00:13.0:   bridge window [mem pref disabled]
[    0.256663] pci 0000:00:13.1: PCI bridge to [bus 07-07]
[    0.256665] pci 0000:00:13.1:   bridge window [io  disabled]
[    0.256671] pci 0000:00:13.1:   bridge window [mem disabled]
[    0.256676] pci 0000:00:13.1:   bridge window [mem pref disabled]
[    0.256702] pci 0000:00:01.0: setting latency timer to 64
[    0.256719]   alloc irq_desc for 27 on node -1
[    0.256722]   alloc kstat_irqs on node -1
[    0.256733] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.256738] pci 0000:00:02.0: setting latency timer to 64
[    0.256750]   alloc irq_desc for 31 on node -1
[    0.256752]   alloc kstat_irqs on node -1
[    0.256757] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
[    0.256763] pci 0000:00:03.0: setting latency timer to 64
[    0.256773] pci 0000:00:13.0: setting latency timer to 64
[    0.256783] pci 0000:00:13.1: setting latency timer to 64
[    0.256788] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.256791] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.256794] pci_bus 0000:01: resource 1 [mem 0xc9000000-0xc9ffffff]
[    0.256797] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xbfffffff pref]
[    0.256800] pci_bus 0000:02: resource 0 [io  0x5000-0x6fff]
[    0.256803] pci_bus 0000:02: resource 1 [mem 0xca000000-0xca7fffff]
[    0.256806] pci_bus 0000:02: resource 2 [mem 0xc8000000-0xc87fffff 64bit pref]
[    0.256809] pci_bus 0000:04: resource 0 [io  0x7000-0x8fff]
[    0.256812] pci_bus 0000:04: resource 1 [mem 0xca800000-0xcaffffff]
[    0.256815] pci_bus 0000:04: resource 2 [mem 0xc8800000-0xc8ffffff 64bit pref]
[    0.256818] pci_bus 0000:06: resource 1 [mem 0xcb000000-0xcb0fffff]
[    0.256821] pci_bus 0000:07: resource 4 [io  0x0000-0xffff]
[    0.256824] pci_bus 0000:07: resource 5 [mem 0x00000000-0xffffffff]
[    0.256883] NET: Registered protocol family 2
[    0.256975] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.257307] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.258003] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.258349] TCP: Hash tables configured (established 131072 bind 65536)
[    0.258352] TCP reno registered
[    0.258359] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.258376] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.258494] NET: Registered protocol family 1
[    0.258517] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.258547] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.258681] pci 0000:01:00.0: Boot video device
[    0.258689] PCI: CLS 32 bytes, default 64
[    0.258959] cpufreq-nforce2: No nForce2 chipset.
[    0.259002] Scanning for low memory corruption every 60 seconds
[    0.259159] audit: initializing netlink socket (disabled)
[    0.259180] type=2000 audit(1294680393.252:1): initialized
[    0.271413] highmem bounce pool size: 64 pages
[    0.271421] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.273202] VFS: Disk quotas dquot_6.5.2
[    0.273280] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.273982] fuse init (API version 7.14)
[    0.274087] msgmni has been set to 1683
[    0.276266] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.276270] io scheduler noop registered
[    0.276272] io scheduler deadline registered
[    0.276289] io scheduler cfq registered (default)
[    0.276456] pcieport 0000:00:02.0: setting latency timer to 64
[    0.276610] pcieport 0000:00:03.0: setting latency timer to 64
[    0.276783] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.276862] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.277433] vesafb: framebuffer at 0xa0000000, mapped to 0xf8080000, using 3072k, total 3072k
[    0.277437] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.277439] vesafb: scrolling: redraw
[    0.277443] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    0.307189] Console: switching to colour frame buffer device 128x48
[    0.337088] fb0: VESA VGA frame buffer device
[    0.337163] intel_idle: MWAIT substates: 0x22220
[    0.337166] intel_idle: does not run on family 6 model 15
[    0.456162] ACPI: AC Adapter [AC] (on-line)
[    0.456283] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.456297] ACPI: Sleep Button [SBTN]
[    0.456349] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.456544] ACPI: Lid Switch [LID]
[    0.456612] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.456616] ACPI: Power Button [PWRF]
[    0.456969] ACPI: acpi_idle registered with cpuidle
[    0.460672] Monitor-Mwait will be used to enter C-1 state
[    0.461010] Monitor-Mwait will be used to enter C-2 state
[    0.461034] Monitor-Mwait will be used to enter C-3 state
[    0.461041] Marking TSC unstable due to TSC halts in idle
[    0.462034] Switching to clocksource acpi_pm
[    0.472626] thermal LNXTHERM:01: registered as thermal_zone0
[    0.472637] ACPI: Thermal Zone [TZ0] (66 C)
[    0.472751] ERST: Table is not found!
[    0.472932] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.474733] brd: module loaded
[    0.475398] loop: module loaded
[    0.475670]   alloc irq_desc for 21 on node -1
[    0.475673]   alloc kstat_irqs on node -1
[    0.475682] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.475736] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.475797] pata_acpi 0000:00:0f.1: power state changed by ACPI to D0
[    0.475832] pata_acpi 0000:00:0f.1: power state changed by ACPI to D0
[    0.476253] Fixed MDIO Bus: probed
[    0.476292] PPP generic driver version 2.4.2
[    0.476343] tun: Universal TUN/TAP device driver, 1.6
[    0.476345] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.476438] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.476461] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.476484] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.476524] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.476580] ehci_hcd 0000:00:10.4: irq 21, io mem 0xcb300000
[    0.476713] isapnp: Scanning for PnP cards...
[    0.525284] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.525490] hub 1-0:1.0: USB hub found
[    0.525497] hub 1-0:1.0: 8 ports detected
[    0.525610] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.525632] uhci_hcd: USB Universal Host Controller Interface driver
[    0.525696]   alloc irq_desc for 20 on node -1
[    0.525699]   alloc kstat_irqs on node -1
[    0.525708] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.525720] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.525765] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.525806] uhci_hcd 0000:00:10.0: irq 20, io base 0x00004c00
[    0.525947] hub 2-0:1.0: USB hub found
[    0.525953] hub 2-0:1.0: 2 ports detected
[    0.526029]   alloc irq_desc for 22 on node -1
[    0.526032]   alloc kstat_irqs on node -1
[    0.526057] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.526064] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.526131] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.526168] uhci_hcd 0000:00:10.1: irq 22, io base 0x00004c20
[    0.526301] hub 3-0:1.0: USB hub found
[    0.526306] hub 3-0:1.0: 2 ports detected
[    0.526387] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.526394] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.526431] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.526454] uhci_hcd 0000:00:10.2: irq 21, io base 0x00004c40
[    0.526588] hub 4-0:1.0: USB hub found
[    0.526593] hub 4-0:1.0: 2 ports detected
[    0.526667]   alloc irq_desc for 23 on node -1
[    0.526670]   alloc kstat_irqs on node -1
[    0.526675] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.526682] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.526720] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.526756] uhci_hcd 0000:00:10.3: irq 23, io base 0x00004c60
[    0.526890] hub 5-0:1.0: USB hub found
[    0.526895] hub 5-0:1.0: 2 ports detected
[    0.527046] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.529650] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.530638] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.530644] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.530677] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.530705] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.530742] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.530869] mice: PS/2 mouse device common for all mice
[    0.531035] rtc_cmos 00:04: RTC can wake from S4
[    0.531081] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.531116] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.531241] device-mapper: uevent: version 1.0.3
[    0.556649] Freeing initrd memory: 13860k freed
[    0.566344] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.566428] device-mapper: multipath: version 1.1.1 loaded
[    0.566432] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.566601] EISA: Probing bus 0 at eisa.0
[    0.566625] Cannot allocate resource for EISA slot 4
[    0.566630] Cannot allocate resource for EISA slot 5
[    0.566632] Cannot allocate resource for EISA slot 6
[    0.566635] Cannot allocate resource for EISA slot 7
[    0.566637] Cannot allocate resource for EISA slot 8
[    0.566640] EISA: Detected 0 cards.
[    0.566819] cpuidle: using governor ladder
[    0.566947] cpuidle: using governor menu
[    0.567359] TCP cubic registered
[    0.567514] NET: Registered protocol family 10
[    0.567988] lo: Disabled Privacy Extensions
[    0.568284] NET: Registered protocol family 17
[    0.569710] Using IPI No-Shortcut mode
[    0.569840] PM: Resume from disk failed.
[    0.569854] registered taskstats version 1
[    0.570205]   Magic number: 11:895:440
[    0.570341] rtc_cmos 00:04: setting system clock to 2011-01-10 17:26:34 UTC (1294680394)
[    0.570344] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.570346] EDD information not available.
[    0.573170] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.622435] ACPI: Battery Slot [BAT0] (battery present)
[    0.788109] isapnp: No Plug & Play device found
[    0.788137] Freeing unused kernel memory: 688k freed
[    0.788517] Write protecting the kernel text: 4932k
[    0.788579] Write protecting the kernel read-only data: 1980k
[    0.810115] ramzswap: module is from the staging directory, the quality is unknown, you have been warned.
[    0.811022] ramzswap: num_devices not specified. Using default: 1
[    0.811024] ramzswap: Creating 1 devices ...
[    0.816503] udev[91]: starting version 163
[    0.893052] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    0.907958] sata_via 0000:00:0f.0: version 2.6
[    0.907976] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.908027] sata_via 0000:00:0f.0: routed to hard irq line 10
[    0.923556] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    0.924360] Linux agpgart interface v0.103
[    0.932741] scsi0 : sata_via
[    0.932952] scsi1 : sata_via
[    0.933000] ata1: SATA max UDMA/133 cmd 0x4cb0 ctl 0x4ca4 bmdma 0x4c80 irq 21
[    0.933004] ata2: SATA max UDMA/133 cmd 0x4ca8 ctl 0x4ca0 bmdma 0x4c88 irq 21
[    0.933094] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.938054] eth0: VIA Rhine II at 0xcb300400, 00:40:d0:e6:07:1c, IRQ 23.
[    0.938766] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
[    0.938787] pata_via 0000:00:0f.1: version 0.3.4
[    0.938860] pata_via 0000:00:0f.1: power state changed by ACPI to D0
[    0.938896] pata_via 0000:00:0f.1: power state changed by ACPI to D0
[    0.939086] scsi2 : pata_via
[    0.939157] scsi3 : pata_via
[    0.940164] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4c90 irq 14
[    0.940168] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4c98 irq 15
[    0.940253] agpgart: Detected VIA P4M900 chipset
[    0.969116] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xc0000000
[    1.136049] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.302117] ata1.00: ATA-8: SAMSUNG HM250JI, HS100-08, max UDMA7
[    1.302124] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.318135] ata1.00: configured for UDMA/133
[    1.318296] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM250JI  HS10 PQ: 0 ANSI: 5
[    1.318484] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.318584] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.318645] sd 0:0:0:0: [sda] Write Protect is off
[    1.318649] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.318675] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.318846]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.378405] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.464047] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    1.520051] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.693527] ata4.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.60, max UDMA/33
[    1.708400] ata4.00: configured for UDMA/33
[    1.710708] scsi 3:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.60 PQ: 0 ANSI: 5
[    1.715391] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.715398] Uniform CD-ROM driver Revision: 3.20
[    1.715614] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.715690] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.729100] usbcore: registered new interface driver hiddev
[    1.729550] acpi device:18: registered as cooling_device2
[    1.729697] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:17/LNXVIDEO:00/input/input4
[    1.729759] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[    1.743996] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/input/input5
[    1.744189] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:10.0-2/input0
[    1.744215] usbcore: registered new interface driver usbhid
[    1.744217] usbhid: USB HID core driver
[    3.830684] xor: automatically using best checksumming function: pIII_sse
[    3.848003]    pIII_sse  :  6718.000 MB/sec
[    3.848006] xor: using function: pIII_sse (6718.000 MB/sec)
[    3.860207] device-mapper: dm-raid45: initialized v0.2594b
[    4.057153] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    4.057161] EXT4-fs (sda5): write access will be enabled during recovery
[    4.480383] EXT4-fs (sda5): orphan cleanup on readonly fs
[    4.480394] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 703951
[    4.480435] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 703947
[    4.480448] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 692526
[    4.480460] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 692525
[    4.480471] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 692523
[    4.480480] EXT4-fs (sda5): 5 orphan inodes deleted
[    4.480484] EXT4-fs (sda5): recovery complete
[    5.002337] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   22.881088] udev[438]: starting version 163
[   22.949608] Adding 899604k swap on /dev/sda6.  Priority:-1 extents:1 across:899604k 
[   23.047213] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.163169] lp: driver loaded but no devices found
[   23.304559] type=1400 audit(1294676817.230:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=721 comm="apparmor_parser"
[   23.305367] type=1400 audit(1294676817.230:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=721 comm="apparmor_parser"
[   23.305802] type=1400 audit(1294676817.230:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=721 comm="apparmor_parser"
[   23.426198] cfg80211: Calling CRDA to update world regulatory domain
[   23.442095] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   23.614250] type=1400 audit(1294676817.538:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=889 comm="apparmor_parser"
[   23.630354] type=1400 audit(1294676817.554:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=911 comm="apparmor_parser"
[   23.631178] type=1400 audit(1294676817.554:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=911 comm="apparmor_parser"
[   23.631621] type=1400 audit(1294676817.554:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=911 comm="apparmor_parser"
[   23.637393] type=1400 audit(1294676817.562:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=914 comm="apparmor_parser"
[   23.637709] type=1400 audit(1294676817.562:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=912 comm="apparmor_parser"
[   23.638389] type=1400 audit(1294676817.562:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=914 comm="apparmor_parser"
[   23.826115] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   23.878319]   alloc irq_desc for 17 on node -1
[   23.878323]   alloc kstat_irqs on node -1
[   23.878333] HDA Intel 0000:06:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.878394] HDA Intel 0000:06:01.0: setting latency timer to 64
[   23.878400] HDA Intel 0000:06:01.0: PCI: Disallowing DAC for device
[   23.882162] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0/0x0
[   23.891583] cfg80211: World regulatory domain updated:
[   23.891589]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.891593]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.891597]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.891600]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.891603]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.891606]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.921411] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input6
[   23.993837] hda_codec: ALC268: BIOS auto-probing.
[   25.095545] phy0: Selected rate control algorithm 'minstrel'
[   25.096419] Registered led device: rt73usb-phy0::radio
[   25.096446] Registered led device: rt73usb-phy0::assoc
[   25.096471] Registered led device: rt73usb-phy0::quality
[   25.097376] usbcore: registered new interface driver rt73usb
[   25.320271] usbcore: registered new interface driver rt2500usb
[   25.676183] phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
[   26.902704] ppdev: user-space parallel port driver
[   34.832036] eth0: no IPv6 routers present
[   38.940870] [drm] Initialized drm 1.1.0 20060810
[   43.892211] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   52.517779] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   53.765785] audit_printk_skb: 18 callbacks suppressed
[   53.765789] type=1400 audit(1294676847.692:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2034 comm="apparmor_parser"
[   83.856785] type=1400 audit(1294676877.781:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2123 comm="apparmor_parser"
[  113.972331] type=1400 audit(1294676907.898:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2213 comm="apparmor_parser"
[  144.079251] type=1400 audit(1294676938.003:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2294 comm="apparmor_parser"
[  174.186821] type=1400 audit(1294676968.112:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2375 comm="apparmor_parser"
[  204.295616] type=1400 audit(1294676998.221:23): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2465 comm="apparmor_parser"
[  234.405793] type=1400 audit(1294677028.333:24): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2544 comm="apparmor_parser"
[  264.519000] type=1400 audit(1294677058.445:25): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2631 comm="apparmor_parser"
[  294.618720] type=1400 audit(1294677088.545:26): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2710 comm="apparmor_parser"
[  324.730003] type=1400 audit(1294677118.653:27): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2926 comm="apparmor_parser"
[  354.823220] type=1400 audit(1294677148.745:28): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3063 comm="apparmor_parser"
[  384.926776] type=1400 audit(1294677178.853:29): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3199 comm="apparmor_parser"
[  415.039704] type=1400 audit(1294677208.965:30): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3280 comm="apparmor_parser"
[  445.153383] type=1400 audit(1294677239.081:31): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3363 comm="apparmor_parser"
[  475.264808] type=1400 audit(1294677269.189:32): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3444 comm="apparmor_parser"
[  505.371551] type=1400 audit(1294677299.297:33): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3523 comm="apparmor_parser"
[  535.491841] type=1400 audit(1294677329.417:34): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3635 comm="apparmor_parser"
[  565.682071] type=1400 audit(1294677359.609:35): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3714 comm="apparmor_parser"
[  595.833578] type=1400 audit(1294677389.757:36): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3793 comm="apparmor_parser"
[  625.962756] type=1400 audit(1294677419.889:37): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3896 comm="apparmor_parser"
[  656.067737] type=1400 audit(1294677449.989:38): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3983 comm="apparmor_parser"
[  686.175562] type=1400 audit(1294677480.097:39): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4062 comm="apparmor_parser"
[  716.282651] type=1400 audit(1294677510.209:40): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4141 comm="apparmor_parser"
[  746.389869] type=1400 audit(1294677540.313:41): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4220 comm="apparmor_parser"
[  776.496919] type=1400 audit(1294677570.421:42): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4307 comm="apparmor_parser"
[  806.604987] type=1400 audit(1294677600.529:43): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4386 comm="apparmor_parser"
[  836.700640] type=1400 audit(1294677630.625:44): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4542 comm="apparmor_parser"
[  866.821788] type=1400 audit(1294677660.749:45): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4630 comm="apparmor_parser"
[  896.921850] type=1400 audit(1294677690.845:46): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4726 comm="apparmor_parser"
[  927.027561] type=1400 audit(1294677720.949:47): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4810 comm="apparmor_parser"
[  957.135856] type=1400 audit(1294677751.057:48): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4889 comm="apparmor_parser"
[  963.662248] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  986.680866] lo: Disabled Privacy Extensions
[  987.237954] type=1400 audit(1294677781.165:49): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4984 comm="apparmor_parser"
[  998.096527] lo: Disabled Privacy Extensions
[ 1017.357745] type=1400 audit(1294677811.285:50): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5119 comm="apparmor_parser"
[ 1047.479712] type=1400 audit(1294677841.405:51): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5203 comm="apparmor_parser"
[ 1077.599757] type=1400 audit(1294677871.525:52): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5292 comm="apparmor_parser"
[ 1107.710933] type=1400 audit(1294677901.633:53): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5371 comm="apparmor_parser"
[ 1137.820447] type=1400 audit(1294677931.745:54): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5450 comm="apparmor_parser"
[ 1167.928186] type=1400 audit(1294677961.853:55): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5533 comm="apparmor_parser"
[ 1198.036224] type=1400 audit(1294677991.961:56): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5614 comm="apparmor_parser"
[ 1228.151711] type=1400 audit(1294678022.077:57): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5697 comm="apparmor_parser"
[ 1258.257543] type=1400 audit(1294678052.181:58): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5776 comm="apparmor_parser"
[ 1288.360162] type=1400 audit(1294678082.285:59): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5872 comm="apparmor_parser"
[ 1318.465215] type=1400 audit(1294678112.393:60): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5953 comm="apparmor_parser"
[ 1348.563857] type=1400 audit(1294678142.485:61): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6035 comm="apparmor_parser"
[ 1378.675489] type=1400 audit(1294678172.601:62): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6114 comm="apparmor_parser"
[ 1408.776969] type=1400 audit(1294678202.697:63): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6193 comm="apparmor_parser"
[ 1438.875850] type=1400 audit(1294678232.797:64): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6272 comm="apparmor_parser"
[ 1468.973616] type=1400 audit(1294678262.897:65): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6351 comm="apparmor_parser"
[ 1499.079466] type=1400 audit(1294678293.001:66): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6459 comm="apparmor_parser"
[ 1529.185832] type=1400 audit(1294678323.113:67): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6538 comm="apparmor_parser"
[ 1559.325944] type=1400 audit(1294678353.249:68): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6619 comm="apparmor_parser"
[ 1589.439046] type=1400 audit(1294678383.365:69): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6699 comm="apparmor_parser"
[ 1619.590700] type=1400 audit(1294678413.517:70): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6782 comm="apparmor_parser"
[ 1649.704884] type=1400 audit(1294678443.629:71): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6864 comm="apparmor_parser"
[ 1679.811579] type=1400 audit(1294678473.733:72): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6943 comm="apparmor_parser"
[ 1709.926959] type=1400 audit(1294678503.853:73): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7033 comm="apparmor_parser"
[ 1740.038351] type=1400 audit(1294678533.961:74): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7116 comm="apparmor_parser"
[ 1770.151518] type=1400 audit(1294678564.073:75): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7196 comm="apparmor_parser"
[ 1800.261772] type=1400 audit(1294678594.185:76): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7276 comm="apparmor_parser"
[ 1830.373900] type=1400 audit(1294678624.301:77): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7356 comm="apparmor_parser"
[ 1860.483462] type=1400 audit(1294678654.405:78): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7437 comm="apparmor_parser"
[ 1890.590982] type=1400 audit(1294678684.513:79): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7517 comm="apparmor_parser"
[ 1920.691967] type=1400 audit(1294678714.613:80): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7612 comm="apparmor_parser"
[ 1950.840782] type=1400 audit(1294678744.761:81): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7714 comm="apparmor_parser"
[ 1980.939389] type=1400 audit(1294678774.861:82): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7793 comm="apparmor_parser"
[ 2011.037479] type=1400 audit(1294678804.961:83): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7892 comm="apparmor_parser"
[ 2041.144976] type=1400 audit(1294678835.069:84): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7982 comm="apparmor_parser"
[ 2071.241824] type=1400 audit(1294678865.165:85): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8061 comm="apparmor_parser"
[ 2101.345205] type=1400 audit(1294678895.269:86): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8141 comm="apparmor_parser"
[ 2131.460690] type=1400 audit(1294678925.385:87): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8220 comm="apparmor_parser"
[ 2161.563965] type=1400 audit(1294678955.489:88): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8300 comm="apparmor_parser"
[ 2191.667918] type=1400 audit(1294678985.589:89): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8381 comm="apparmor_parser"
[ 2221.767118] type=1400 audit(1294679015.689:90): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8460 comm="apparmor_parser"
[ 2251.866204] type=1400 audit(1294679045.793:91): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8539 comm="apparmor_parser"
[ 2281.980046] type=1400 audit(1294679075.905:92): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8618 comm="apparmor_parser"
[ 2312.089431] type=1400 audit(1294679106.017:93): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8697 comm="apparmor_parser"
[ 2342.206093] type=1400 audit(1294679136.133:94): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8776 comm="apparmor_parser"
[ 2372.328006] type=1400 audit(1294679166.253:95): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8855 comm="apparmor_parser"
[ 2402.433292] type=1400 audit(1294679196.357:96): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=8934 comm="apparmor_parser"
[ 2432.535549] type=1400 audit(1294679226.457:97): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9014 comm="apparmor_parser"
[ 2462.641614] type=1400 audit(1294679256.565:98): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9093 comm="apparmor_parser"
[ 2492.747999] type=1400 audit(1294679286.669:99): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9172 comm="apparmor_parser"
[ 2522.732209] lo: Disabled Privacy Extensions
[ 2522.883611] type=1400 audit(1294679316.805:100): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9279 comm="apparmor_parser"
[ 2553.030378] type=1400 audit(1294679346.957:101): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9377 comm="apparmor_parser"
[ 2583.169664] type=1400 audit(1294679377.097:102): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9456 comm="apparmor_parser"
[ 2613.306310] type=1400 audit(1294679407.233:103): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9535 comm="apparmor_parser"
[ 2643.442969] type=1400 audit(1294679437.365:104): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9616 comm="apparmor_parser"
[ 2673.568633] type=1400 audit(1294679467.493:105): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9695 comm="apparmor_parser"
[ 2703.689069] type=1400 audit(1294679497.617:106): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9774 comm="apparmor_parser"
[ 2733.812939] type=1400 audit(1294679527.737:107): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9864 comm="apparmor_parser"
[ 2763.935456] type=1400 audit(1294679557.857:108): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=9949 comm="apparmor_parser"
[ 2794.046246] type=1400 audit(1294679587.969:109): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10035 comm="apparmor_parser"
[ 2824.155513] type=1400 audit(1294679618.077:110): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10128 comm="apparmor_parser"
[ 2854.270167] type=1400 audit(1294679648.197:111): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10219 comm="apparmor_parser"
[ 2884.379415] type=1400 audit(1294679678.305:112): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10298 comm="apparmor_parser"
[ 2914.488036] type=1400 audit(1294679708.413:113): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10377 comm="apparmor_parser"
[ 2944.597478] type=1400 audit(1294679738.525:114): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10457 comm="apparmor_parser"
[ 2974.717019] type=1400 audit(1294679768.641:115): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10561 comm="apparmor_parser"
[ 3004.826118] type=1400 audit(1294679798.753:116): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10642 comm="apparmor_parser"
[ 3034.958942] type=1400 audit(1294679828.881:117): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10730 comm="apparmor_parser"
[ 3065.076461] type=1400 audit(1294679859.001:118): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10809 comm="apparmor_parser"
[ 3095.184918] type=1400 audit(1294679889.109:119): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10888 comm="apparmor_parser"
[ 3125.293340] type=1400 audit(1294679919.217:120): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10967 comm="apparmor_parser"
[ 3155.400358] type=1400 audit(1294679949.325:121): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11046 comm="apparmor_parser"
[ 3185.510160] type=1400 audit(1294679979.433:122): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11125 comm="apparmor_parser"
[ 3215.616947] type=1400 audit(1294680009.541:123): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11223 comm="apparmor_parser"
[ 3245.743090] type=1400 audit(1294680039.665:124): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11320 comm="apparmor_parser"
[ 3275.874121] type=1400 audit(1294680069.801:125): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11425 comm="apparmor_parser"
[ 3306.007891] type=1400 audit(1294680099.933:126): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11505 comm="apparmor_parser"
[ 3336.118152] type=1400 audit(1294680130.041:127): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11593 comm="apparmor_parser"
[ 3366.223100] type=1400 audit(1294680160.145:128): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11672 comm="apparmor_parser"
[ 3396.324725] type=1400 audit(1294680190.249:129): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11751 comm="apparmor_parser"
[ 3426.429510] type=1400 audit(1294680220.357:130): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11830 comm="apparmor_parser"
[ 3456.549760] type=1400 audit(1294680250.473:131): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11909 comm="apparmor_parser"
[ 3486.681394] type=1400 audit(1294680280.605:132): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=11991 comm="apparmor_parser"
[ 3516.795422] type=1400 audit(1294680310.721:133): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12071 comm="apparmor_parser"
[ 3546.893304] type=1400 audit(1294680340.817:134): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12150 comm="apparmor_parser"
[ 3576.997895] type=1400 audit(1294680370.925:135): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12231 comm="apparmor_parser"
[ 3607.097411] type=1400 audit(1294680401.021:136): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12316 comm="apparmor_parser"
[ 3637.206245] type=1400 audit(1294680431.129:137): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12400 comm="apparmor_parser"
[ 3667.314224] type=1400 audit(1294680461.237:138): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12484 comm="apparmor_parser"
[ 3697.415717] type=1400 audit(1294680491.341:139): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12564 comm="apparmor_parser"
[ 3727.514600] type=1400 audit(1294680521.437:140): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=12644 comm="apparmor_parser"

```

```
sudo lshw -C network
PCI (sysfs)  

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
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.2 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:4800(size=256) memory:cb300400-cb3004ff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:10:60:9b:31:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.35-24-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

```

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

```

```
iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

```

```
 lsb_release -d
Description:	Ubuntu 10.10

```

```
 uname -mr
2.6.35-24-generic i686

```

```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                                                            Ignoring unknown interface eth0=eth0.

```

---

### Post by sevic33 on 2011-01-10
Bump
No one to help?

---

### Post by grahammechanical on 2011-01-10
There are messages in the listings that you provide that confirm what you already know - that wireless is not working. The question is why is it not working?

Enter in a terminal rfkill list. You want to see Soft blocked: no and Hard Blocked: no. If you see a yes in either place then you will know that the wireless adapter has been switched off either by software or in hardware or in both.

Does the network icon have a red exclamation mark against it? When you right click the icon is there a tick mark against Enable Networking and Enable wireless? If not, then select and click each line. Do you need to turn wireless on by pressing a key combination? Do not forget to try a reboot to activate the changes.

Regards.

---

### Post by sevic33 on 2011-01-10
```
rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Right click show Enable wireless checked
Left lick show in grey 'Wireless Networks device not ready(firmware missing)'

And there is key combination,its always on,its work normal on windows wich is dual booted with ubuntu

---

### Post by sevic33 on 2011-01-11
I solved problem with using ndisgtk and Windows Drivers

---

### Post by mhgsys on 2011-01-11
Hi, read your email to late... Good you have it working though.

 btw.. you wrote something about me having a post somewhere mentioning this card??
because I sure can't find it. 

Ah; in case you google mhgsys rt73 you will see a dutch ubuntu page mentioning rt73 in the same topic..(it's jesse2314 sig)  but the topic was about the sis 671/771.. and my name is nivasys there.. the dutch account I actually never use..

---

