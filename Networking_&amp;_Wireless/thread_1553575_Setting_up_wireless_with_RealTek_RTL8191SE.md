---
title: "Setting up wireless with RealTek RTL8191SE"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by Serpentine Cougar on 2010-08-15
I have a **Toshiba Satellite L655-S5061** laptop and dual-boot Windows 7 and Kubuntu Lucid Lynx. Windows detects and connects to the wireless network just fine, but in Kubuntu it will detect the network but can't connect to it. Sometimes Network Manager will say it's connected, but Konqueror can't load any websites. Plugging in an ethernet cable doesn't give me access to the internet, either.

Here's the output of several commands:

$ lsb_release -d
```
Description:    Ubuntu 10.04 LTS
```$ uname -mr
```
2.6.32-21-generic-pae i686
```$ lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

```$ ifconfig
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                                  
          RX bytes:58400 (58.4 KB)  TX bytes:58400 (58.4 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:b2:dd:6e  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:feb2:dd6e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2072 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:663135 (663.1 KB)  TX bytes:6177 (6.1 KB)
          Interrupt:17 Memory:f8338000-f8338100 

```$ iwconfig
```
lo        no wireless extensions.

wlan0     802.11bg  ESSID:"Belkin_G_Wireless_F4BD5F"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1C:DF:F4:BD:5F   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-71 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```(notice "r8192se_pci": )   $ lsmod
```
Module                  Size  Used by
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22005  2 
snd_hda_codec          74201  1 snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
i915                  283218  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
drm_kms_helper         29297  1 i915
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm                   163143  3 i915,drm_kms_helper
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57022  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54148  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24473  2 i915
joydev                  8708  0 
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
agpgart                31788  2 drm,intel_agp
r8192se_pci           446788  0 
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  1 lp
usbhid                 36174  0 
hid                    67032  1 usbhid
usb_storage            39457  0 
ahci                   32040  2 

```(there's some stuff about rtl8192se at the bottom: )  $ dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic-pae (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 (Ubuntu 2.6.32-21.32-generic-pae 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b5aa1000 (usable)
[    0.000000]  BIOS-e820: 00000000b5aa1000 - 00000000b5aa7000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5aa7000 - 00000000b5bd0000 (usable)
[    0.000000]  BIOS-e820: 00000000b5bd0000 - 00000000b5c0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5c0f000 - 00000000b5d09000 (usable)
[    0.000000]  BIOS-e820: 00000000b5d09000 - 00000000b5f0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5f0f000 - 00000000b5f19000 (usable)
[    0.000000]  BIOS-e820: 00000000b5f19000 - 00000000b5f1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5f1f000 - 00000000b5f64000 (usable)
[    0.000000]  BIOS-e820: 00000000b5f64000 - 00000000b5f9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b5f9f000 - 00000000b5fdf000 (usable)
[    0.000000]  BIOS-e820: 00000000b5fdf000 - 00000000b5fff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b5fff000 - 00000000b6000000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   4 base 0B7E00000 mask FFFE00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000b7e00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000b5aa1000 (usable)
[    0.000000]  modified: 00000000b5aa1000 - 00000000b5aa7000 (reserved)
[    0.000000]  modified: 00000000b5aa7000 - 00000000b5bd0000 (usable)
[    0.000000]  modified: 00000000b5bd0000 - 00000000b5c0f000 (reserved)
[    0.000000]  modified: 00000000b5c0f000 - 00000000b5d09000 (usable)
[    0.000000]  modified: 00000000b5d09000 - 00000000b5f0f000 (reserved)
[    0.000000]  modified: 00000000b5f0f000 - 00000000b5f19000 (usable)
[    0.000000]  modified: 00000000b5f19000 - 00000000b5f1f000 (reserved)
[    0.000000]  modified: 00000000b5f1f000 - 00000000b5f64000 (usable)
[    0.000000]  modified: 00000000b5f64000 - 00000000b5f9f000 (ACPI NVS)
[    0.000000]  modified: 00000000b5f9f000 - 00000000b5fdf000 (usable)
[    0.000000]  modified: 00000000b5fdf000 - 00000000b5fff000 (ACPI data)
[    0.000000]  modified: 00000000b5fff000 - 00000000b6000000 (usable)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 7000-d000
[    0.000000] RAMDISK: 37864000 - 37fefd71
[    0.000000] Allocated new RAMDISK: 00938000 - 010c3d71
[    0.000000] Move RAMDISK from 0000000037864000 - 0000000037fefd70 to 00938000 - 010c3d70
[    0.000000] ACPI: RSDP 000f6a40 00024 (v02 TOSQCI)
[    0.000000] ACPI: XSDT b5ff32da 00074 (v01 TOSQCI TOSQCI00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP b5fe3000 000F4 (v03 T0SQCI TOSQCI00 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT b5fe4000 0B712 (v02 TOSQCI CANTIGA  06040000 INTL 20061109)
[    0.000000] ACPI: FACS b5f9efc0 00040
[    0.000000] ACPI: HPET b5ffed86 00038 (v01 TOSQCI TOSQCI00 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG b5ffedbe 0003C (v01 TOSQCI TOSQCI00 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC b5ffedfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT b5ffee62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC b5ffee8a 00176 (v01 TOSQCI TOSQCI00 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT b5ff3376 00196 (v01 SataRe SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT b5fe2000 00655 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT b5fe1000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT b5fe0000 0020F (v01  PmRef    ApTst 00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4230MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00009000 - 0000ff40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000092f7d8]    TEXT DATA BSS ==> [0000100000 - 000092f7d8]
[    0.000000]   #4 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #5 [0000930000 - 00009371b4]              BRK ==> [0000930000 - 00009371b4]
[    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #7 [0000938000 - 00010c3d71]      NEW RAMDISK ==> [0000938000 - 00010c3d71]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] found SMP MP-table at [c00f6b00] f6b00
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[10] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000b5aa1
[    0.000000]     0: 0x000b5aa7 -> 0x000b5bd0
[    0.000000]     0: 0x000b5c0f -> 0x000b5d09
[    0.000000]     0: 0x000b5f0f -> 0x000b5f19
[    0.000000]     0: 0x000b5f1f -> 0x000b5f64
[    0.000000]     0: 0x000b5f9f -> 0x000b5fdf
[    0.000000]     0: 0x000b5fff -> 0x000b6000
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1006831
[    0.000000] free_area_init_node: node 0, pgdat c07d4d20, node_mem_map c10c5000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8461 pages used for memmap
[    0.000000]   HighMem zone: 770633 pages, LIFO batch:31
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b6000000 (gap: b6000000:4a000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c3a00000 s39448 r0 d21992 u1048576
[    0.000000] pcpu-alloc: s39448 r0 d21992 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 996590
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=bc87096c-2efe-42b3-bb0b-5d29a39ee550 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 26214400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:00140000)
[    0.000000] Memory: 3942700k/5242880k available (4826k kernel code, 83724k reserved, 2211k data, 672k init, 3116376k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc07e0000 - 0xc0888000   ( 672 kB)
[    0.000000]       .data : 0xc05b6a1b - 0xc07df7a8   (2211 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05b6a1b   (4826 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2294.452 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4588.90 BogoMIPS (lpj=9177808)
[    0.004020] Security Framework initialized
[    0.004038] AppArmor: AppArmor initialized
[    0.004044] Mount-cache hash table entries: 512
[    0.004155] Initializing cgroup subsys ns
[    0.004159] Initializing cgroup subsys cpuacct
[    0.004163] Initializing cgroup subsys memory
[    0.004168] Initializing cgroup subsys devices
[    0.004170] Initializing cgroup subsys freezer
[    0.004172] Initializing cgroup subsys net_cls
[    0.004190] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004192] CPU: L2 cache: 1024K
[    0.004195] CPU: Physical Processor ID: 0
[    0.004196] CPU: Processor Core ID: 0
[    0.004199] mce: CPU supports 6 MCE banks
[    0.004207] CPU0: Thermal monitoring enabled (TM2)
[    0.004210] using mwait in idle threads.
[    0.004216] Performance Events: Core2 events, Intel PMU driver.
[    0.004221] ... version:                2
[    0.004222] ... bit width:              40
[    0.004224] ... generic registers:      2
[    0.004226] ... value mask:             000000ffffffffff
[    0.004227] ... max period:             000000007fffffff
[    0.004229] ... fixed-purpose events:   3
[    0.004230] ... event mask:             0000000700000003
[    0.004235] Checking 'hlt' instruction... OK.
[    0.022646] ACPI: Core revision 20090903
[    0.040010] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040015] ftrace: allocating 22402 entries in 44 pages
[    0.044052] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044396] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.085728] CPU0: Intel Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz stepping 0a
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 1024K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.172087] CPU1: Intel Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz stepping 0a
[    0.172098] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.176017] Brought up 2 CPUs
[    0.176020] Total of 2 processors activated (9177.81 BogoMIPS).
[    0.176368] CPU0 attaching sched-domain:
[    0.176371]  domain 0: span 0-1 level MC
[    0.176373]   groups: 0 1
[    0.176379] CPU1 attaching sched-domain:
[    0.176380]  domain 0: span 0-1 level MC
[    0.176382]   groups: 1 0
[    0.176467] devtmpfs: initialized
[    0.176467] regulator: core version 0.5
[    0.176467] Time:  6:31:56  Date: 08/15/10
[    0.176467] NET: Registered protocol family 16
[    0.176467] Trying to unpack rootfs image as initramfs...
[    0.176467] EISA bus registered
[    0.176467] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.176467] ACPI: bus type pci registered
[    0.176467] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.176467] PCI: Not using MMCONFIG.
[    0.176682] PCI: PCI BIOS revision 3.00 entry at 0xfdc51, last bus=10
[    0.176684] PCI: Using configuration type 1 for base access
[    0.180114] bio: create slab <bio-0> at 0
[    0.181517] ACPI: EC: Look up EC in DSDT
[    0.186654] ACPI: BIOS _OSI(Linux) query ignored
[    0.220109] ACPI: Interpreter enabled
[    0.220117] ACPI: (supports S0 S3 S4 S5)
[    0.220141] ACPI: Using IOAPIC for interrupt routing
[    0.220208] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.228559] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.228562] PCI: Using MMCONFIG for extended config space
[    0.237001] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.237430] ACPI: No dock devices found.
[    0.237960] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.238050] pci 0000:00:02.0: reg 10 64bit mmio: [0xf4000000-0xf43fffff]
[    0.238057] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.238062] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.238102] pci 0000:00:02.1: reg 10 64bit mmio: [0xf4400000-0xf44fffff]
[    0.238229] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
[    0.238328] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
[    0.238427] pci 0000:00:1a.2: reg 20 io port: [0x1860-0x187f]
[    0.238526] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf4904800-0xf4904bff]
[    0.238600] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.238605] pci 0000:00:1a.7: PME# disabled
[    0.238664] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf4700000-0xf4703fff]
[    0.238728] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.238732] pci 0000:00:1b.0: PME# disabled
[    0.238829] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.238833] pci 0000:00:1c.0: PME# disabled
[    0.238932] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.238936] pci 0000:00:1c.1: PME# disabled
[    0.239039] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.239043] pci 0000:00:1c.4: PME# disabled
[    0.239142] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.239146] pci 0000:00:1c.5: PME# disabled
[    0.239227] pci 0000:00:1d.0: reg 20 io port: [0x1880-0x189f]
[    0.239326] pci 0000:00:1d.1: reg 20 io port: [0x18a0-0x18bf]
[    0.239423] pci 0000:00:1d.2: reg 20 io port: [0x18c0-0x18df]
[    0.239521] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4904c00-0xf4904fff]
[    0.239594] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.239599] pci 0000:00:1d.7: PME# disabled
[    0.239861] pci 0000:00:1f.2: reg 10 io port: [0x1818-0x181f]
[    0.239869] pci 0000:00:1f.2: reg 14 io port: [0x180c-0x180f]
[    0.239876] pci 0000:00:1f.2: reg 18 io port: [0x1810-0x1817]
[    0.239884] pci 0000:00:1f.2: reg 1c io port: [0x1808-0x180b]
[    0.239891] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.239899] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf4904000-0xf49047ff]
[    0.239949] pci 0000:00:1f.2: PME# supported from D3hot
[    0.239954] pci 0000:00:1f.2: PME# disabled
[    0.240010] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.240030] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.240123] pci 0000:00:1c.0: bridge io port: [0x00-0xfff]
[    0.240127] pci 0000:00:1c.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.240135] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.240199] pci 0000:00:1c.1: bridge io port: [0x00-0xfff]
[    0.240204] pci 0000:00:1c.1: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.240212] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.240287] pci 0000:07:00.0: reg 10 64bit mmio: [0x000000-0x03ffff]
[    0.240298] pci 0000:07:00.0: reg 18 io port: [0x00-0x7f]
[    0.240385] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.240390] pci 0000:07:00.0: PME# disabled
[    0.240471] pci 0000:00:1c.4: bridge io port: [0x00-0xfff]
[    0.240476] pci 0000:00:1c.4: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.240484] pci 0000:00:1c.4: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.240552] pci 0000:08:00.0: reg 10 io port: [0x00-0xff]
[    0.240563] pci 0000:08:00.0: reg 14 32bit mmio: [0x000000-0x003fff]
[    0.240653] pci 0000:08:00.0: supports D1 D2
[    0.240655] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot
[    0.240661] pci 0000:08:00.0: PME# disabled
[    0.240741] pci 0000:00:1c.5: bridge io port: [0x00-0xfff]
[    0.240745] pci 0000:00:1c.5: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.240753] pci 0000:00:1c.5: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.240817] pci 0000:00:1e.0: transparent bridge
[    0.240862] pci_bus 0000:00: on NUMA node 0
[    0.240874] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.241045] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.241165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.241236] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.241322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.257533] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.257666] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.257794] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 *6 7 10 12 14 15)
[    0.257920] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.258043] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.258167] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.258290] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 *6 7 10 12 14 15)
[    0.258410] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.258531] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.258545] vgaarb: loaded
[    0.258648] SCSI subsystem initialized
[    0.258740] libata version 3.00 loaded.
[    0.258807] usbcore: registered new interface driver usbfs
[    0.258818] usbcore: registered new interface driver hub
[    0.258841] usbcore: registered new device driver usb
[    0.259018] ACPI: WMI: Mapper loaded
[    0.259020] PCI: Using ACPI for IRQ routing
[    0.259252] pci 0000:00:1c.0: BAR 13: can't allocate resource
[    0.259254] pci 0000:00:1c.0: BAR 14: can't allocate resource
[    0.259256] pci 0000:00:1c.0: BAR 15: can't allocate resource
[    0.259258] pci 0000:00:1c.1: BAR 13: can't allocate resource
[    0.259260] pci 0000:00:1c.1: BAR 14: can't allocate resource
[    0.259262] pci 0000:00:1c.1: BAR 15: can't allocate resource
[    0.259263] pci 0000:00:1c.4: BAR 13: can't allocate resource
[    0.259265] pci 0000:00:1c.4: BAR 14: can't allocate resource
[    0.259267] pci 0000:00:1c.4: BAR 15: can't allocate resource
[    0.259269] pci 0000:00:1c.5: BAR 13: can't allocate resource
[    0.259271] pci 0000:00:1c.5: BAR 14: can't allocate resource
[    0.259273] pci 0000:00:1c.5: BAR 15: can't allocate resource
[    0.259456] NetLabel: Initializing
[    0.259458] NetLabel:  domain hash size = 128
[    0.259460] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.259473] NetLabel:  unlabeled traffic allowed by default
[    0.259515] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.259520] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.264228] Switching to clocksource tsc
[    0.266110] AppArmor: AppArmor Filesystem Enabled
[    0.266127] pnp: PnP ACPI init
[    0.266150] ACPI: bus type pnp registered
[    0.267274] pnp 00:04: io resource (0x2e-0x2f) overlaps 0000:07:00.0 BAR 2 (0x0-0x7f), disabling
[    0.267278] pnp 00:04: io resource (0x4e-0x4f) overlaps 0000:07:00.0 BAR 2 (0x0-0x7f), disabling
[    0.267281] pnp 00:04: io resource (0x61-0x61) overlaps 0000:07:00.0 BAR 2 (0x0-0x7f), disabling
[    0.267283] pnp 00:04: io resource (0x63-0x63) overlaps 0000:07:00.0 BAR 2 (0x0-0x7f), disabling
[    0.267286] pnp 00:04: io resource (0x65-0x65) overlaps 0000:07:00.0 BAR 2 (0x0-0x7f), disabling
[    0.267289] pnp 00:04: io resource (0x67-0x67) overlaps 0000:07:00.0 BAR 2 (0x0-0x7f), disabling
[    0.267291] pnp 00:04: io resource (0x68-0x68) overlaps 0000:07:00.0 BAR 2 (0x0-0x7f), disabling
[    0.267294] pnp 00:04: io resource (0x6c-0x6c) overlaps 0000:07:00.0 BAR 2 (0x0-0x7f), disabling
[    0.267297] pnp 00:04: io resource (0x70-0x70) overlaps 0000:07:00.0 BAR 2 (0x0-0x7f), disabling
[    0.267301] pnp 00:04: io resource (0x2e-0x2f) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.267303] pnp 00:04: io resource (0x4e-0x4f) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.267306] pnp 00:04: io resource (0x61-0x61) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.267309] pnp 00:04: io resource (0x63-0x63) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.267311] pnp 00:04: io resource (0x65-0x65) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.267314] pnp 00:04: io resource (0x67-0x67) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.267317] pnp 00:04: io resource (0x68-0x68) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.267319] pnp 00:04: io resource (0x6c-0x6c) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.267322] pnp 00:04: io resource (0x70-0x70) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.267325] pnp 00:04: io resource (0x80-0x80) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.267327] pnp 00:04: io resource (0x92-0x92) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.267330] pnp 00:04: io resource (0xb2-0xb3) overlaps 0000:08:00.0 BAR 0 (0x0-0xff), disabling
[    0.272035] pnp 00:08: mem resource (0xff-0x3fe) overlaps 0000:00:1f.3 BAR 0 (0x0-0xff), disabling
[    0.272040] pnp 00:08: mem resource (0xff-0x3fe) overlaps 0000:07:00.0 BAR 0 (0x0-0x3ffff), disabling
[    0.272044] pnp 00:08: mem resource (0xff-0x3fe) overlaps 0000:08:00.0 BAR 1 (0x0-0x3fff), disabling
[    0.272832] pnp: PnP ACPI: found 10 devices
[    0.272835] ACPI: ACPI bus type pnp unregistered
[    0.272839] PnPBIOS: Disabled by ACPI PNP
[    0.272854] system 00:02: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.272862] system 00:04: ioport range 0x3e0-0x3e1 has been reserved
[    0.272865] system 00:04: ioport range 0x400-0x47f has been reserved
[    0.272868] system 00:04: ioport range 0x680-0x69f has been reserved
[    0.272870] system 00:04: ioport range 0x480-0x48f has been reserved
[    0.272873] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.272875] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.272878] system 00:04: ioport range 0x1180-0x11ff has been reserved
[    0.272880] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.272883] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.272892] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.272894] system 00:09: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.272897] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.272900] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.272955] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.272958] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.272960] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.272963] system 00:09: iomem range 0xff808000-0xff8080ff has been reserved
[    0.307921] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.307926] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.307932] pci 0000:00:1c.0:   MEM window: 0xb8000000-0xb81fffff
[    0.307938] pci 0000:00:1c.0:   PREFETCH window: 0x000000b8200000-0x000000b83fffff
[    0.307946] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.307949] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.307955] pci 0000:00:1c.1:   MEM window: 0xb8400000-0xb85fffff
[    0.307959] pci 0000:00:1c.1:   PREFETCH window: 0x000000b8600000-0x000000b87fffff
[    0.307981] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:07
[    0.307984] pci 0000:00:1c.4:   IO window: 0x4000-0x4fff
[    0.307990] pci 0000:00:1c.4:   MEM window: 0xb8800000-0xb89fffff
[    0.307995] pci 0000:00:1c.4:   PREFETCH window: 0x000000b8a00000-0x000000b8bfffff
[    0.308011] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.308014] pci 0000:00:1c.5:   IO window: 0x5000-0x5fff
[    0.308021] pci 0000:00:1c.5:   MEM window: 0xb8c00000-0xb8dfffff
[    0.308025] pci 0000:00:1c.5:   PREFETCH window: 0x000000b8e00000-0x000000b8ffffff
[    0.308033] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    0.308035] pci 0000:00:1e.0:   IO window: disabled
[    0.308041] pci 0000:00:1e.0:   MEM window: disabled
[    0.308045] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.308062] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.308070]   alloc irq_desc for 17 on node -1
[    0.308072]   alloc kstat_irqs on node -1
[    0.308079] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.308086] pci 0000:00:1c.0: setting latency timer to 64
[    0.308096] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.308099]   alloc irq_desc for 16 on node -1
[    0.308101]   alloc kstat_irqs on node -1
[    0.308104] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.308110] pci 0000:00:1c.1: setting latency timer to 64
[    0.308120] pci 0000:00:1c.4: enabling device (0000 -> 0003)
[    0.308124] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.308130] pci 0000:00:1c.4: setting latency timer to 64
[    0.308140] pci 0000:00:1c.5: enabling device (0000 -> 0003)
[    0.308144] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.308150] pci 0000:00:1c.5: setting latency timer to 64
[    0.308159] pci 0000:00:1e.0: setting latency timer to 64
[    0.308163] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.308165] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.308168] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.308170] pci_bus 0000:02: resource 1 mem: [0xb8000000-0xb81fffff]
[    0.308172] pci_bus 0000:02: resource 2 pref mem [0xb8200000-0xb83fffff]
[    0.308175] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]
[    0.308177] pci_bus 0000:03: resource 1 mem: [0xb8400000-0xb85fffff]
[    0.308179] pci_bus 0000:03: resource 2 pref mem [0xb8600000-0xb87fffff]
[    0.308181] pci_bus 0000:07: resource 0 io:  [0x4000-0x4fff]
[    0.308183] pci_bus 0000:07: resource 1 mem: [0xb8800000-0xb89fffff]
[    0.308185] pci_bus 0000:07: resource 2 pref mem [0xb8a00000-0xb8bfffff]
[    0.308188] pci_bus 0000:08: resource 0 io:  [0x5000-0x5fff]
[    0.308190] pci_bus 0000:08: resource 1 mem: [0xb8c00000-0xb8dfffff]
[    0.308192] pci_bus 0000:08: resource 2 pref mem [0xb8e00000-0xb8ffffff]
[    0.308194] pci_bus 0000:0a: resource 3 io:  [0x00-0xffff]
[    0.308196] pci_bus 0000:0a: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.308233] NET: Registered protocol family 2
[    0.308323] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.308613] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.309072] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.309343] TCP: Hash tables configured (established 131072 bind 65536)
[    0.309345] TCP reno registered
[    0.309446] NET: Registered protocol family 1
[    0.309467] pci 0000:00:02.0: Boot video device
[    0.309657] Simple Boot Flag at 0x36 set to 0x1
[    0.309813] cpufreq-nforce2: No nForce2 chipset.
[    0.309837] Scanning for low memory corruption every 60 seconds
[    0.309957] audit: initializing netlink socket (disabled)
[    0.309966] type=2000 audit(1281853916.307:1): initialized
[    0.319144] highmem bounce pool size: 64 pages
[    0.319149] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.320440] VFS: Disk quotas dquot_6.5.2
[    0.320501] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.321014] fuse init (API version 7.13)
[    0.321091] msgmni has been set to 1615
[    0.321287] alg: No test for stdrng (krng)
[    0.321343] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.321346] io scheduler noop registered
[    0.321347] io scheduler anticipatory registered
[    0.321349] io scheduler deadline registered
[    0.321383] io scheduler cfq registered (default)
[    0.321544]   alloc irq_desc for 24 on node -1
[    0.321546]   alloc kstat_irqs on node -1
[    0.321558] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.321569] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.321722]   alloc irq_desc for 25 on node -1
[    0.321724]   alloc kstat_irqs on node -1
[    0.321732] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.321743] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.321893]   alloc irq_desc for 26 on node -1
[    0.321895]   alloc kstat_irqs on node -1
[    0.321903] pcieport 0000:00:1c.4: irq 26 for MSI/MSI-X
[    0.321913] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.322060]   alloc irq_desc for 27 on node -1
[    0.322061]   alloc kstat_irqs on node -1
[    0.322070] pcieport 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.322080] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.322176] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.322336] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.323509] ACPI: AC Adapter [ACAD] (on-line)
[    0.323584] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.323587] ACPI: Power Button [PWRB]
[    0.323624] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.323909] ACPI: Lid Switch [LID]
[    0.323952] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.323955] ACPI: Power Button [PWRF]
[    0.324818] ACPI: SSDT b5f1aca0 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.325395] ACPI: SSDT b5f19620 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.327559] Monitor-Mwait will be used to enter C-1 state
[    0.327609] Monitor-Mwait will be used to enter C-2 state
[    0.327628] Monitor-Mwait will be used to enter C-3 state
[    0.327633] Marking TSC unstable due to TSC halts in idle
[    0.327694] processor LNXCPU:00: registered as cooling_device0
[    0.328152] ACPI: SSDT b5f1aa20 001CF (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.328614] ACPI: SSDT b5f1af20 0008D (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.329579] Switching to clocksource hpet
[    0.331870] processor LNXCPU:01: registered as cooling_device1
[    0.342987] thermal LNXTHERM:01: registered as thermal_zone0
[    0.342997] ACPI: Thermal Zone [THRM] (34 C)
[    0.344473] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.345707] brd: module loaded
[    0.346110] loop: module loaded
[    0.346203] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.346604] Fixed MDIO Bus: probed
[    0.346633] PPP generic driver version 2.4.2
[    0.346670] tun: Universal TUN/TAP device driver, 1.6
[    0.346672] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.346759] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.346785]   alloc irq_desc for 19 on node -1
[    0.346787]   alloc kstat_irqs on node -1
[    0.346793] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.346813] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.346817] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.346852] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.346881] ehci_hcd 0000:00:1a.7: debug port 1
[    0.349121] ACPI: Battery Slot [BAT1] (battery absent)
[    0.349136] isapnp: Scanning for PnP cards...
[    0.350771] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.350812] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf4904800
[    0.360044] Freeing initrd memory: 7727k freed
[    0.399574] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.399725] usb usb1: configuration #1 chosen from 1 choice
[    0.399754] hub 1-0:1.0: USB hub found
[    0.399764] hub 1-0:1.0: 6 ports detected
[    0.399833]   alloc irq_desc for 23 on node -1
[    0.399835]   alloc kstat_irqs on node -1
[    0.399842] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.399864] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.399867] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.399902] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.399930] ehci_hcd 0000:00:1d.7: debug port 1
[    0.403809] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.403824] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4904c00
[    0.451432] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.451512] usb usb2: configuration #1 chosen from 1 choice
[    0.451534] hub 2-0:1.0: USB hub found
[    0.451540] hub 2-0:1.0: 6 ports detected
[    0.451595] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.451612] uhci_hcd: USB Universal Host Controller Interface driver
[    0.451648] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.451655] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.451659] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.451687] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.451722] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    0.451806] usb usb3: configuration #1 chosen from 1 choice
[    0.451827] hub 3-0:1.0: USB hub found
[    0.451834] hub 3-0:1.0: 2 ports detected
[    0.451874]   alloc irq_desc for 21 on node -1
[    0.451876]   alloc kstat_irqs on node -1
[    0.451880] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.451887] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.451890] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.451916] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.451949] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.452051] usb usb4: configuration #1 chosen from 1 choice
[    0.452073] hub 4-0:1.0: USB hub found
[    0.452079] hub 4-0:1.0: 2 ports detected
[    0.452121] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.452127] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.452131] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.452162] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.452187] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    0.452263] usb usb5: configuration #1 chosen from 1 choice
[    0.452285] hub 5-0:1.0: USB hub found
[    0.452291] hub 5-0:1.0: 2 ports detected
[    0.452335] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.452341] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.452345] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.452372] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.452403] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    0.452520] usb usb6: configuration #1 chosen from 1 choice
[    0.452541] hub 6-0:1.0: USB hub found
[    0.452547] hub 6-0:1.0: 2 ports detected
[    0.452590] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.452597] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.452600] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.452627] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.452653] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    0.452732] usb usb7: configuration #1 chosen from 1 choice
[    0.452754] hub 7-0:1.0: USB hub found
[    0.452760] hub 7-0:1.0: 2 ports detected
[    0.452802]   alloc irq_desc for 18 on node -1
[    0.452804]   alloc kstat_irqs on node -1
[    0.452808] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.452814] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.452818] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.452850] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.452882] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    0.452958] usb usb8: configuration #1 chosen from 1 choice
[    0.452982] hub 8-0:1.0: USB hub found
[    0.452990] hub 8-0:1.0: 2 ports detected
[    0.453077] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.454995] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.457190] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.457195] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.457220] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.457241] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.457260] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.457362] mice: PS/2 mouse device common for all mice
[    0.457489] rtc_cmos 00:05: RTC can wake from S4
[    0.457524] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.457567] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.457807] device-mapper: uevent: version 1.0.3
[    0.460638] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.460702] device-mapper: multipath: version 1.1.0 loaded
[    0.460704] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.460803] EISA: Probing bus 0 at eisa.0
[    0.460809] Cannot allocate resource for EISA slot 1
[    0.460812] Cannot allocate resource for EISA slot 2
[    0.460814] Cannot allocate resource for EISA slot 3
[    0.460815] Cannot allocate resource for EISA slot 4
[    0.460817] Cannot allocate resource for EISA slot 5
[    0.460831] EISA: Detected 0 cards.
[    0.460948] cpuidle: using governor ladder
[    0.461058] cpuidle: using governor menu
[    0.461469] TCP cubic registered
[    0.461597] NET: Registered protocol family 10
[    0.461999] lo: Disabled Privacy Extensions
[    0.462295] NET: Registered protocol family 17
[    0.462909] Using IPI No-Shortcut mode
[    0.462983] PM: Resume from disk failed.
[    0.462993] registered taskstats version 1
[    0.463470]   Magic number: 6:251:519
[    0.463550] rtc_cmos 00:05: setting system clock to 2010-08-15 06:31:57 UTC (1281853917)
[    0.463553] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.463554] EDD information not available.
[    0.485796] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.716028] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.719178] isapnp: No Plug & Play device found
[    0.719192] Freeing unused kernel memory: 672k freed
[    0.719512] Write protecting the kernel text: 4828k
[    0.719584] Write protecting the kernel read-only data: 1876k
[    0.735784] udev: starting version 151
[    0.807173] ahci 0000:00:1f.2: version 3.0
[    0.807192] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.807239]   alloc irq_desc for 28 on node -1
[    0.807241]   alloc kstat_irqs on node -1
[    0.807253] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.807500] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.807504] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pio slum part ccc ems sxs 
[    0.807510] ahci 0000:00:1f.2: setting latency timer to 64
[    0.842556] scsi0 : ahci
[    0.850494] scsi1 : ahci
[    0.850637] scsi2 : ahci
[    0.850732] scsi3 : ahci
[    0.850825] scsi4 : ahci
[    0.850913] scsi5 : ahci
[    0.851082] ata1: SATA max UDMA/133 abar m2048@0xf4904000 port 0xf4904100 irq 28
[    0.851086] ata2: SATA max UDMA/133 abar m2048@0xf4904000 port 0xf4904180 irq 28
[    0.851088] ata3: DUMMY
[    0.851089] ata4: DUMMY
[    0.851092] ata5: SATA max UDMA/133 abar m2048@0xf4904000 port 0xf4904300 irq 28
[    0.851095] ata6: SATA max UDMA/133 abar m2048@0xf4904000 port 0xf4904380 irq 28
[    1.096889] usb 1-1: configuration #1 chosen from 1 choice
[    1.107806] Initializing USB Mass Storage driver...
[    1.107926] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.108043] usbcore: registered new interface driver usb-storage
[    1.108045] USB Mass Storage support registered.
[    1.108063] usb-storage: device found at 2
[    1.108064] usb-storage: waiting for device to settle before scanning
[    1.168057] ata2: SATA link down (SStatus 0 SControl 300)
[    1.168094] ata6: SATA link down (SStatus 0 SControl 300)
[    1.168134] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.168139] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.168615] ACPI Warning for \_SB_.PCI0.SAT0.PRT0._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    1.168622] ata1.00: _GTF unexpected object type 0x1
[    1.173098] ACPI Warning for \_SB_.PCI0.SAT0.PRT4._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    1.173104] ata5.00: _GTF unexpected object type 0x1
[    1.173925] ata5.00: ATAPI: TEAC    DV-W28S-VT, M.8C, max UDMA/100, ATAPI AN
[    1.179740] ata5.00: _GTF unexpected object type 0x1
[    1.180578] ata5.00: configured for UDMA/100
[    1.219090] ata1.00: ATA-8: TOSHIBA MK3265GSX, GJ003M, max UDMA/100
[    1.219092] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.219893] ata1.00: _GTF unexpected object type 0x1
[    1.220120] ata1.00: configured for UDMA/100
[    1.220235] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3265GS GJ00 PQ: 0 ANSI: 5
[    1.220387] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.220498] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.220538] sd 0:0:0:0: [sda] Write Protect is off
[    1.220541] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.220562] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.220681]  sda:
[    1.224179] scsi 4:0:0:0: CD-ROM            TEAC     DV-W28S-VT       M.8C PQ: 0 ANSI: 5
[    1.233104] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.233107] Uniform CD-ROM driver Revision: 3.20
[    1.233196] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.233249] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.268072] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    1.271265]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.310960] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.429143] usb 2-4: configuration #1 chosen from 1 choice
[    1.672055] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    1.851318] usb 5-1: configuration #1 chosen from 1 choice
[    1.863456] usbcore: registered new interface driver hiddev
[    1.886541] input: Primax HP Wireless Eco-Comfort Mobile Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input5
[    1.886678] generic-usb 0003:0461:4D63.0001: input,hiddev96,hidraw0: USB HID v1.11 Mouse [Primax HP Wireless Eco-Comfort Mobile Mouse] on usb-0000:00:1a.2-1/input0
[    1.886701] usbcore: registered new interface driver usbhid
[    1.886703] usbhid: v2.6:USB HID core driver
[    2.062744] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    6.108461] usb-storage: device scan complete
[    6.111064] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    6.111584] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.116144] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    7.912384] udev: starting version 151
[    7.951376] lp: driver loaded but no devices found
[    8.045083] Adding 8589304k swap on /dev/sda6.  Priority:-1 extents:1 across:8589304k 
[    8.416533] rtllib_crypt: registered algorithm 'NULL'
[    8.416536] rtllib_crypt: registered algorithm 'TKIP'
[    8.416538] rtllib_crypt: registered algorithm 'CCMP'
[    8.416540] rtllib_crypt: registered algorithm 'WEP'
[    8.416541] 
[    8.416542] Linux kernel driver for RTL8192 based WLAN cards
[    8.416543] Copyright (c) 2007-2008, Realsil Wlan Driver
[    8.416584] rtl819xSE 0000:08:00.0: enabling device (0000 -> 0003)
[    8.416593] rtl819xSE 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.416603] rtl819xSE 0000:08:00.0: setting latency timer to 64
[    8.446848] Linux agpgart interface v0.103
[    8.448758] Adapter(8192SE) is found - DeviceID=8172
[    8.449632] agpgart-intel 0000:00:00.0: Intel Mobile IntelÂ® GM45 Express Chipset
[    8.450073] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[    8.515729] Linux video capture interface: v2.00
[    8.519028] type=1505 audit(1281871925.552:2):  operation="profile_load" pid=663 name="/sbin/dhclient3"
[    8.519641] type=1505 audit(1281871925.552:3):  operation="profile_load" pid=663 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    8.519954] uvcvideo: Found UVC 1.00 device CNF9055 (04f2:b1d6)
[    8.519965] type=1505 audit(1281871925.552:4):  operation="profile_load" pid=663 name="/usr/lib/connman/scripts/dhclient-script"
[    8.533171] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    8.534887] input: CNF9055 as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input6
[    8.534951] usbcore: registered new interface driver uvcvideo
[    8.534954] USB Video Class driver (v0.1.0)
[    8.572451] [drm] Initialized drm 1.1.0 20060810
[    8.604232] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.604237] i915 0000:00:02.0: setting latency timer to 64
[    8.613643]   alloc irq_desc for 29 on node -1
[    8.613646]   alloc kstat_irqs on node -1
[    8.613655] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[    8.613661] [drm] set up 127M of stolen space
[    8.683375] type=1505 audit(1281871925.716:5):  operation="profile_replace" pid=774 name="/sbin/dhclient3"
[    8.683976] type=1505 audit(1281871925.716:6):  operation="profile_replace" pid=774 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    8.684300] type=1505 audit(1281871925.720:7):  operation="profile_replace" pid=774 name="/usr/lib/connman/scripts/dhclient-script"
[    8.686010] type=1505 audit(1281871925.720:8):  operation="profile_load" pid=775 name="/usr/lib/cups/backend/cups-pdf"
[    8.686719] type=1505 audit(1281871925.720:9):  operation="profile_load" pid=775 name="/usr/sbin/cupsd"
[    8.688892] type=1505 audit(1281871925.724:10):  operation="profile_load" pid=776 name="/usr/sbin/mysqld-akonadi"
[    8.690669] type=1505 audit(1281871925.724:11):  operation="profile_load" pid=777 name="/usr/sbin/tcpdump"
[    8.974578] rtl819xSE 0000:08:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[    9.212346] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[    9.222393] ===>rtllib_start_scan()
[    9.236270] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.247654] fb0: inteldrmfb frame buffer device
[    9.247657] registered panic notifier
[    9.276548] acpi device:01: registered as cooling_device2
[    9.277363] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    9.277537] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.277836] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.278113]   alloc irq_desc for 22 on node -1
[    9.278116]   alloc kstat_irqs on node -1
[    9.278123] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.278165] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.280756] vga16fb: initializing
[    9.280760] vga16fb: mapped to 0xc00a0000
[    9.280764] vga16fb: not registering due to another framebuffer present
[    9.310156] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[    9.310161] synaptics: Toshiba Satellite L655 detected, limiting rate to 40pps.
[    9.352981] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[    9.543790] Console: switching to colour frame buffer device 170x48
[   16.224056] ----------->rtl8192se_check_hw_scan()
[   16.224059] FW Scan long time without stop, stop hw scan
[   16.225059] <-----------rtl8192se_check_hw_scan()
[   23.240055] ----------->rtl8192se_check_hw_scan()
[   23.240058] FW Scan long time without stop, stop hw scan
[   23.241057] <-----------rtl8192se_check_hw_scan()
[   37.084322] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   44.092054] ----------->rtl8192se_check_hw_scan()
[   44.092058] FW Scan long time without stop, stop hw scan
[   44.093058] <-----------rtl8192se_check_hw_scan()
[   67.084830] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   74.092064] ----------->rtl8192se_check_hw_scan()
[   74.092067] FW Scan long time without stop, stop hw scan
[   74.093066] <-----------rtl8192se_check_hw_scan()
[  107.082942] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  114.092065] ----------->rtl8192se_check_hw_scan()
[  114.092068] FW Scan long time without stop, stop hw scan
[  114.093067] <-----------rtl8192se_check_hw_scan()
[  157.084966] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  164.092065] ----------->rtl8192se_check_hw_scan()
[  164.092069] FW Scan long time without stop, stop hw scan
[  164.093069] <-----------rtl8192se_check_hw_scan()
[  164.471695] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[  177.462023] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  184.476041] ----------->rtl8192se_check_hw_scan()
[  184.476046] FW Scan long time without stop, stop hw scan
[  184.477050] <-----------rtl8192se_check_hw_scan()
[  184.477374] Linking with Belkin_G_Wireless_F4BD5F,channel:6, qos:1, myHT:1, networkHT:0, mode:6 cur_net.flags:0x40e
[  184.477393] Linking with Belkin_G_Wireless_F4BD5F,channel:6, qos:1, myHT:1, networkHT:0, mode:6 cur_net.flags:0x40e
[  184.477478] ===>rtllib_associate_procedure_wq(), chan:6
[  184.477482] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  184.487575] rtllib_authentication_req():auth->algorithm is OPEN
[  184.490567] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  184.500136] Associated successfully
[  184.500139] normal associate
[  184.500151] Using G rates:108
[  184.500154] Successfully associated, ht not enabled(0, 0)
[  184.501519] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  184.964151] DHCP pkt src port:68, dest port:67!!
[  185.220301] dm_check_edca_turbo():iot peer is unknown, bssid:00:1c:df:f4:bd:5f
[  194.860055] wlan0: no IPv6 routers present
[  216.967655] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  223.980067] ----------->rtl8192se_check_hw_scan()
[  223.980072] FW Scan long time without stop, stop hw scan
[  223.981075] <-----------rtl8192se_check_hw_scan()
[  263.964082] ----------->rtl8192se_check_hw_scan()
[  263.964087] FW Scan long time without stop, stop hw scan
[  263.965090] <-----------rtl8192se_check_hw_scan()
[  323.964082] ----------->rtl8192se_check_hw_scan()
[  323.964087] FW Scan long time without stop, stop hw scan
[  323.965090] <-----------rtl8192se_check_hw_scan()
[  403.964066] ----------->rtl8192se_check_hw_scan()
[  403.964071] FW Scan long time without stop, stop hw scan
[  403.965074] <-----------rtl8192se_check_hw_scan()
[  471.888079] usb 1-6: new high speed USB device using ehci_hcd and address 4
[  472.021085] usb 1-6: configuration #1 chosen from 1 choice
[  472.021735] scsi7 : SCSI emulation for USB Mass Storage devices
[  472.021949] usb-storage: device found at 4
[  472.021953] usb-storage: waiting for device to settle before scanning
[  477.020265] usb-storage: device scan complete
[  477.020729] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer           8.02 PQ: 0 ANSI: 0 CCS
[  477.021788] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  477.027748] sd 7:0:0:0: [sdc] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[  477.028327] sd 7:0:0:0: [sdc] Write Protect is off
[  477.028331] sd 7:0:0:0: [sdc] Mode Sense: 45 00 00 08
[  477.028333] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  477.031778] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  477.031786]  sdc: sdc1
[  477.035705] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  477.035712] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  503.964066] ----------->rtl8192se_check_hw_scan()
[  503.964071] FW Scan long time without stop, stop hw scan
[  503.965074] <-----------rtl8192se_check_hw_scan()
[  623.964080] ----------->rtl8192se_check_hw_scan()
[  623.964085] FW Scan long time without stop, stop hw scan
[  623.965088] <-----------rtl8192se_check_hw_scan()
[  743.964080] ----------->rtl8192se_check_hw_scan()
[  743.964085] FW Scan long time without stop, stop hw scan
[  743.965087] <-----------rtl8192se_check_hw_scan()
[  863.964079] ----------->rtl8192se_check_hw_scan()
[  863.964085] FW Scan long time without stop, stop hw scan
[  863.965087] <-----------rtl8192se_check_hw_scan()
[  983.964081] ----------->rtl8192se_check_hw_scan()
[  983.964086] FW Scan long time without stop, stop hw scan
[  983.965089] <-----------rtl8192se_check_hw_scan()
[ 1103.964083] ----------->rtl8192se_check_hw_scan()
[ 1103.964089] FW Scan long time without stop, stop hw scan
[ 1103.965092] <-----------rtl8192se_check_hw_scan()
[ 1223.964083] ----------->rtl8192se_check_hw_scan()
[ 1223.964089] FW Scan long time without stop, stop hw scan
[ 1223.965093] <-----------rtl8192se_check_hw_scan()
[ 1343.964067] ----------->rtl8192se_check_hw_scan()
[ 1343.964072] FW Scan long time without stop, stop hw scan
[ 1343.965075] <-----------rtl8192se_check_hw_scan()
[ 1463.964064] ----------->rtl8192se_check_hw_scan()
[ 1463.964070] FW Scan long time without stop, stop hw scan
[ 1463.965072] <-----------rtl8192se_check_hw_scan()
[ 1583.964064] ----------->rtl8192se_check_hw_scan()
[ 1583.964070] FW Scan long time without stop, stop hw scan
[ 1583.965071] <-----------rtl8192se_check_hw_scan()
[ 1703.964089] ----------->rtl8192se_check_hw_scan()
[ 1703.964094] FW Scan long time without stop, stop hw scan
[ 1703.965097] <-----------rtl8192se_check_hw_scan()

```$ sudo lshw -C network
```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:07:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd cap_list
       configuration: latency=0
       resources: memory:b8800000-b883ffff ioport:4000(size=128)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:b2:dd:6e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 ip=192.168.2.4 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:17 ioport:5000(size=256) memory:b8c00000-b8c03fff

```$ iwlist scan
```
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:DF:F4:BD:5F
                    ESSID:"Belkin_G_Wireless_F4BD5F"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality=93/100  Signal level=-68 dBm  Noise level=-116 dBm
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Extra: Last beacon: 5ms ago
          Cell 02 - Address: 00:0F:66:57:F6:AA
                    ESSID:"linksys"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=62/100  Signal level=-68 dBm  Noise level=-101 dBm
                    Extra: Last beacon: 0ms ago
          Cell 03 - Address: 00:11:95:41:71:57
                    ESSID:"default"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality=48/100  Signal level=-68 dBm  Noise level=-94 dBm
                    Extra: Last beacon: 2ms ago
          Cell 04 - Address: 00:13:10:E3:D0:09
                    ESSID:"Home Base"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=48/100  Signal level=-68 dBm  Noise level=-94 dBm
                    Extra: Last beacon: 35ms ago
          Cell 05 - Address: 00:12:17:CF:E2:98
                    ESSID:"0123456789"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=48/100  Signal level=-68 dBm  Noise level=-94 dBm
                    Extra: Last beacon: 141ms ago
          Cell 06 - Address: 00:18:F8:78:97:86
                    ESSID:"money"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=48/100  Signal level=-73 dBm  Noise level=-94 dBm
                    Extra: Last beacon: 667ms ago
          Cell 07 - Address: 00:22:A4:0E:78:69
                    ESSID:"2WIRE303"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=48/100  Signal level=-73 dBm  Noise level=-94 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Extra: Last beacon: 759ms ago

```$ sudo /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                                               Ignoring unknown interface wlan0=wlan0.
                                                                                              [ OK ]

```$ nm-tool
```
NetworkManager Tool

State: connected

- Device: wlan0  [belk2] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xSE
  State:             connected
  Default:           yes
  HW Address:        70:F1:A1:B2:DD:6E

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    2WIRE303:        Infra, 00:22:A4:0E:78:69, Freq 2442 MHz, Rate 54 Mb/s, Strength 48 WPA
    Home Base:       Infra, 00:13:10:E3:D0:09, Freq 2437 MHz, Rate 54 Mb/s, Strength 48
    default:         Infra, 00:11:95:41:71:57, Freq 2437 MHz, Rate 54 Mb/s, Strength 48
    linksys:         Infra, 00:0F:66:57:F6:AA, Freq 2437 MHz, Rate 54 Mb/s, Strength 63
    money:           Infra, 00:18:F8:78:97:86, Freq 2437 MHz, Rate 54 Mb/s, Strength 48 WEP
    0123456789:      Infra, 00:12:17:CF:E2:98, Freq 2437 MHz, Rate 54 Mb/s, Strength 48 WEP
    *Belkin_G_Wireless_F4BD5F: Infra, 00:1C:DF:F4:BD:5F, Freq 2437 MHz, Rate 54 Mb/s, Strength 93

  IPv4 Settings:
    Address:         192.168.2.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


```$ sudo dhclient wlan0
```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/70:f1:a1:b2:dd:6e
Sending on   LPF/wlan0/70:f1:a1:b2:dd:6e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```$ cat /etc/resolv.conf
```
# Generated by NetworkManager
```I also tried pinging:
```
$ ping -c 4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.026 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.031 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.028 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.026/0.030/0.037/0.006 ms


$ ping -c 4 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.4 icmp_seq=1 Destination Host Unreachable
From 192.168.2.4 icmp_seq=2 Destination Host Unreachable
From 192.168.2.4 icmp_seq=3 Destination Host Unreachable
From 192.168.2.4 icmp_seq=4 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3015ms
, pipe 3


~$ ping -c 4 74.125.227.19
PING 74.125.227.19 (74.125.227.19) 56(84) bytes of data.
From 192.168.2.4 icmp_seq=1 Destination Host Unreachable
From 192.168.2.4 icmp_seq=2 Destination Host Unreachable
From 192.168.2.4 icmp_seq=3 Destination Host Unreachable
From 192.168.2.4 icmp_seq=4 Destination Host Unreachable

--- 74.125.227.19 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3015ms
, pipe 3


```Router Information (when I go to 192.168.2.1 on a different Windows computer in the same network):
```
Version Info
   Firmware Version: 4.00.05
   Boot Version: 0.03
   Hardware: F5D7234-4 v4 (01)
   Serial No.: 12918723413521
          
LAN Settings
   LAN/WLAN MAC: 00-1C-DF-F4-BD-5F
   IP Address: 192.168.2.1
   Subnet mask: 255.255.255.0
   DHCP Server : Enabled

Internet Settings
   WAN MAC Address: 00-1C-DF-F4-BD-60
   Connection Type: Dynamic
   Subnet mask: 255.255.248.0
   WAN IP: [my IP according to whatismyip.com]
   Default Gateway: [some numbers]
   DNS Address: [some numbers]
          
Features
   Firewall: Enabled
   SSID: Belkin_G_Wireless_F4BD5F
   Security: Disabled
   UPnP: Enabled
   Remote Management: Disabled
   WPS: Enabled
   Guest Access: Disabled
```Can anyone help me figure out why I can't get to any website, please?

---

### Post by homebound on 2010-08-23
Hi,

I have the exact same model and having the same problem as you. However, I'm new to linux/ubuntu and don't know most of the commands you typed earlier. Essentially, ifconfig does not show the ethernet adapter but lshw does.


The problem is also addressed in [http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697). I followed these steps as recommended by the thread:

1. hooked up a USB netgear wireless adapter
1.1 apt-get update then apt-get upgrade

2. downloaded compat-wireless-2.6.tar.bz2 and ran:
sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
3. after reboot, the ethernet adapter vboxnet0 does show up on ifconfig but still no link
4. lshw -C network shows the adapter as DISABLED, i enabled it :
  ifconfig vboxnet0 up
5. then ran dhclient vboxnet0
6. the adapter shows up in ifconfig :
vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          inet6 addr: fe80::800:27ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:810 (810.0 B)

7.

still no link. 

Also, after a reboot, the adapter goes back to disabled.


I hope that will help you a little further than me. If you get either ethernet or wifi or both to work, can you please post it back on this thread.

thanks,
Mohammed


ps: the fan on this laptop is always loud and running. do u have the same issue??

---

### Post by canucked on 2010-12-09
Have you tried using the drivers from Realtek's website?

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2262](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2262)

You would have to compile the driver each time you install a new linux kernel.

I recently configured a Toshiba Satellite L655-S5115 laptop for a friend.  That laptop uses Realtek RTL8188CE.  Apparently the linux driver on Realtek's website works for this wireless card, but I came across a PPA which makes installation far more convenient:

[https://launchpad.net/~lexical/+archive/hwe-wireless](https://launchpad.net/~lexical/+archive/hwe-wireless)

Installing rtl8192ce-dkms worked for the Toshiba I configured.  You could contact the PPA author, Keng-Yü Lin, and ask him to provide a deb for your Realtek model.

Also, you can check on the Realtek 819x linux kernel status here:
[http://linuxwireless.org/en/users/Drivers/rtl819x](http://linuxwireless.org/en/users/Drivers/rtl819x)

And in case you have audio issues with your Toshiba L655, I created a thread about the troublesome Toshiba I configured here:
[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

Hope this helps.

---

