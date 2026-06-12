---
title: "Wierd 10.04.1 Wireless behavior"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by FullMetalManiac on 2010-10-05
Okay.  First off, let me share something,
Right now, I am using the LiveCD version of 10.04.1 LTS [Lucid].  That's the only way I can get online with Wireless (i.e.: If I boot up to Ubuntu from HDD, it'll detect wireless but won't connect).

Now, I'll post stuff.

1. Machine Make and Model
HP pavilion a706n

2. Wireless Card Brand Model and Chipset
```
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

3. Wireless Interface Status
```
(ifconfig)
      wlan0     Link encap:Ethernet  HWaddr 00:18:e7:63:19:91  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
      -----
      (iwconfig)
      wlan0     IEEE 802.11bg  ESSID:"Belkin_G_Wireless_3F849F"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

4. Modules
```
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
snd_usb_audio          75765  1 
snd_via82xx            20058  2 
snd_via82xx_modem       8486  0 
snd_seq_dummy           1338  0 
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  2 snd_via82xx,snd_via82xx_modem
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_seq_oss            26726  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  5 snd_usb_audio,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_usb_lib            15801  1 snd_usb_audio
snd_seq_midi            4557  0 
snd_mpu401_uart         5617  1 snd_via82xx
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
joydev                  8708  0 
snd_rawmidi            19056  3 snd_usb_lib,snd_seq_midi,snd_mpu401_uart
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1153  2 
snd_timer              19098  2 snd_pcm,snd_seq
usbhid                 36110  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_hwdep               5412  1 snd_usb_audio
nvidia               7087672  34 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
rtl8180                26346  0 
snd                    54148  20 snd_usb_audio,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,snd_hwdep
gspca_zc3xx            45189  0 
ppdev                   5259  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
gspca_main             21199  1 gspca_zc3xx
mac80211              205146  1 rtl8180
eeprom_93cx6            1333  1 rtl8180
usb_storage            39425  1 
hid                    67032  1 usbhid
videodev               34361  1 gspca_main
v4l1_compat            13251  1 videodev
via_agp                 5310  1 
parport_pc             25962  1 
soundcore               6620  1 snd
i2c_viapro              5573  0 
snd_page_alloc          7076  3 snd_via82xx,snd_via82xx_modem,snd_pcm
lp                      7028  0 
cfg80211              126517  2 rtl8180,mac80211
shpchp                 28820  0 
agpgart                31724  2 nvidia,via_agp
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
via_rhine              19154  0 
floppy                 53016  0 
mii                     4381  1 via_rhine
ieee1394               81181  1 ohci1394
sata_via                6945  0 
pata_via                7272  2 
```

5. Kernel Boot Messages
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 (Ubuntu 2.6.32-24.42-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 0E0000000 mask FFC000000 write-combining
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
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  modified: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
[    0.000000]  modified: 000000002fff3000 - 0000000030000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000002fff0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 002fc00000 page 2M
[    0.000000]  002fc00000 - 002fff0000 page 4k
[    0.000000] kernel direct mapping tables up to 2fff0000 @ 10000-15000
[    0.000000] RAMDISK: 2389b000 - 24033b1a
[    0.000000] ACPI: RSDP 000f7b70 00014 (v00 KM400 )
[    0.000000] ACPI: RSDT 2fff3000 0002C (v01 KM400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 2fff3040 00074 (v01 KM400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 2fff30c0 0518F (v01 KM400  AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 2fff0000 00040
[    0.000000] ACPI: APIC 2fff8280 0005A (v01 KM400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2fff0000
[    0.000000]   low ram: 0 - 2fff0000
[    0.000000]   node 0 low ram: 00000000 - 2fff0000
[    0.000000]   node 0 bootmap 00011000 - 00017000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
[    0.000000]   #4 [002389b000 - 0024033b1a]          RAMDISK ==> [002389b000 - 0024033b1a]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008de000 - 00008e1146]              BRK ==> [00008de000 - 00008e1146]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000017000]          BOOTMAP ==> [0000011000 - 0000017000]
[    0.000000] found SMP MP-table at [c00f6040] f6040
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002fff0
[    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0002fff0
[    0.000000] On node 0 totalpages: 196479
[    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1504 pages used for memmap
[    0.000000]   Normal zone: 190992 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 30000000:cec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194943
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=3fecceb6-6e28-4ef2-9051-f22ec046e4a8 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3931520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 758816k/786368k available (4679k kernel code, 26728k reserved, 2124k data, 660k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf07f0000 - 0xff7fe000   ( 240 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2100.033 MHz processor.
[    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4200.06 BogoMIPS (lpj=8400132)
[    0.008033] Security Framework initialized
[    0.008073] AppArmor: AppArmor initialized
[    0.008083] Mount-cache hash table entries: 512
[    0.008262] Initializing cgroup subsys ns
[    0.008268] Initializing cgroup subsys cpuacct
[    0.008273] Initializing cgroup subsys memory
[    0.008285] Initializing cgroup subsys devices
[    0.008289] Initializing cgroup subsys freezer
[    0.008292] Initializing cgroup subsys net_cls
[    0.008319] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008322] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008328] mce: CPU supports 4 MCE banks
[    0.008352] Performance Events: AMD PMU driver.
[    0.008362] ... version:                0
[    0.008364] ... bit width:              48
[    0.008366] ... generic registers:      4
[    0.008368] ... value mask:             0000ffffffffffff
[    0.008371] ... max period:             00007fffffffffff
[    0.008373] ... fixed-purpose events:   0
[    0.008375] ... event mask:             000000000000000f
[    0.008381] Checking 'hlt' instruction... OK.
[    0.024619] SMP alternatives: switching to UP code
[    0.031371] Freeing SMP alternatives: 19k freed
[    0.031413] ACPI: Core revision 20090903
[    0.044046] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044066] ftrace: allocating 21780 entries in 43 pages
[    0.048184] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.049265] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.091085] CPU0: AMD Athlon(tm) XP 3000+ stepping 00
[    0.092001] Brought up 1 CPUs
[    0.092001] Total of 1 processors activated (4200.06 BogoMIPS).
[    0.092001] CPU0 attaching NULL sched-domain.
[    0.092001] devtmpfs: initialized
[    0.092001] regulator: core version 0.5
[    0.092001] Time:  8:33:48  Date: 10/05/10
[    0.092001] NET: Registered protocol family 16
[    0.092001] EISA bus registered
[    0.092001] ACPI: bus type pci registered
[    0.097085] PCI: PCI BIOS revision 2.10 entry at 0xfbcc0, last bus=1
[    0.097088] PCI: Using configuration type 1 for base access
[    0.098157] bio: create slab <bio-0> at 0
[    0.098862] ACPI: EC: Look up EC in DSDT
[    0.106683] ACPI: Interpreter enabled
[    0.106701] ACPI: (supports S0 S1 S3 S4 S5)
[    0.106740] ACPI: Using IOAPIC for interrupt routing
[    0.113455] ACPI: No dock devices found.
[    0.113579] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.113636] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe3ffffff]
[    0.113713] pci 0000:00:01.0: supports D1
[    0.113746] pci 0000:00:09.0: reg 10 io port: [0xa000-0xa0ff]
[    0.113753] pci 0000:00:09.0: reg 14 32bit mmio: [0xe6000000-0xe60003ff]
[    0.113784] pci 0000:00:09.0: supports D1 D2
[    0.113787] pci 0000:00:09.0: PME# supported from D1 D2 D3hot D3cold
[    0.113792] pci 0000:00:09.0: PME# disabled
[    0.113819] pci 0000:00:0a.0: reg 10 32bit mmio: [0xe6001000-0xe60010ff]
[    0.113826] pci 0000:00:0a.0: reg 14 io port: [0xa400-0xa407]
[    0.113832] pci 0000:00:0a.0: reg 18 io port: [0xa800-0xa8ff]
[    0.113860] pci 0000:00:0a.0: supports D2
[    0.113862] pci 0000:00:0a.0: PME# supported from D2 D3hot D3cold
[    0.113866] pci 0000:00:0a.0: PME# disabled
[    0.113894] pci 0000:00:0b.0: reg 10 32bit mmio: [0xe6002000-0xe60027ff]
[    0.113901] pci 0000:00:0b.0: reg 14 io port: [0xac00-0xac7f]
[    0.113933] pci 0000:00:0b.0: supports D2
[    0.113935] pci 0000:00:0b.0: PME# supported from D2 D3hot D3cold
[    0.113939] pci 0000:00:0b.0: PME# disabled
[    0.113970] pci 0000:00:0f.0: reg 10 io port: [0xb000-0xb007]
[    0.113976] pci 0000:00:0f.0: reg 14 io port: [0xb400-0xb403]
[    0.113983] pci 0000:00:0f.0: reg 18 io port: [0xb800-0xb807]
[    0.113989] pci 0000:00:0f.0: reg 1c io port: [0xbc00-0xbc03]
[    0.113995] pci 0000:00:0f.0: reg 20 io port: [0xc000-0xc00f]
[    0.114002] pci 0000:00:0f.0: reg 24 io port: [0xc400-0xc4ff]
[    0.114064] pci 0000:00:0f.1: reg 20 io port: [0xc800-0xc80f]
[    0.114130] pci 0000:00:10.0: reg 20 io port: [0xcc00-0xcc1f]
[    0.114151] pci 0000:00:10.0: supports D1 D2
[    0.114153] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.114157] pci 0000:00:10.0: PME# disabled
[    0.114197] pci 0000:00:10.1: reg 20 io port: [0xd000-0xd01f]
[    0.114217] pci 0000:00:10.1: supports D1 D2
[    0.114220] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.114224] pci 0000:00:10.1: PME# disabled
[    0.114263] pci 0000:00:10.2: reg 20 io port: [0xd400-0xd41f]
[    0.114284] pci 0000:00:10.2: supports D1 D2
[    0.114286] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.114290] pci 0000:00:10.2: PME# disabled
[    0.114329] pci 0000:00:10.3: reg 20 io port: [0xd800-0xd81f]
[    0.114350] pci 0000:00:10.3: supports D1 D2
[    0.114352] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.114356] pci 0000:00:10.3: PME# disabled
[    0.114383] pci 0000:00:10.4: reg 10 32bit mmio: [0xe6003000-0xe60030ff]
[    0.114417] pci 0000:00:10.4: supports D1 D2
[    0.114419] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.114423] pci 0000:00:10.4: PME# disabled
[    0.114475] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.114481] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
[    0.114525] pci 0000:00:11.5: reg 10 io port: [0xdc00-0xdcff]
[    0.114561] pci 0000:00:11.5: supports D1 D2
[    0.114591] pci 0000:00:11.6: reg 10 io port: [0xe000-0xe0ff]
[    0.114654] pci 0000:00:12.0: reg 10 io port: [0xe400-0xe4ff]
[    0.114660] pci 0000:00:12.0: reg 14 32bit mmio: [0xe6004000-0xe60040ff]
[    0.114692] pci 0000:00:12.0: supports D1 D2
[    0.114694] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.114698] pci 0000:00:12.0: PME# disabled
[    0.114743] pci 0000:01:00.0: reg 10 32bit mmio: [0xe4000000-0xe4ffffff]
[    0.114749] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.114764] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.114807] pci 0000:00:01.0: bridge 32bit mmio: [0xe4000000-0xe5ffffff]
[    0.114813] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.114820] pci_bus 0000:00: on NUMA node 0
[    0.114826] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.158053] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.158252] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.158454] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.158655] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 6 7 10 11 12)
[    0.158822] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.158980] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.159139] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.159298] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.159482] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.159672] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.159886] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.160084] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[    0.160235] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.160238] vgaarb: loaded
[    0.160408] SCSI subsystem initialized
[    0.160543] libata version 3.00 loaded.
[    0.160647] usbcore: registered new interface driver usbfs
[    0.160670] usbcore: registered new interface driver hub
[    0.160709] usbcore: registered new device driver usb
[    0.160879] ACPI: WMI: Mapper loaded
[    0.160882] PCI: Using ACPI for IRQ routing
[    0.161062] NetLabel: Initializing
[    0.161065] NetLabel:  domain hash size = 128
[    0.161067] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.161087] NetLabel:  unlabeled traffic allowed by default
[    0.161154] Switching to clocksource tsc
[    0.163825] AppArmor: AppArmor Filesystem Enabled
[    0.163864] pnp: PnP ACPI init
[    0.163910] ACPI: bus type pnp registered
[    0.166925] pnp: PnP ACPI: found 12 devices
[    0.166928] ACPI: ACPI bus type pnp unregistered
[    0.166934] PnPBIOS: Disabled by ACPI PNP
[    0.166953] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[    0.166957] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.166960] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.166964] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.166968] system 00:00: iomem range 0x2fff0000-0x2fffffff could not be reserved
[    0.166972] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.166975] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.166979] system 00:00: iomem range 0x100000-0x2ffeffff could not be reserved
[    0.166982] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.166986] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.166989] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.166998] system 00:02: ioport range 0x4000-0x407f has been reserved
[    0.167001] system 00:02: ioport range 0x5000-0x500f has been reserved
[    0.167008] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.167011] system 00:03: ioport range 0x294-0x297 has been reserved
[    0.167014] system 00:03: ioport range 0x290-0x297 could not be reserved
[    0.201773] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.201776] pci 0000:00:01.0:   IO window: disabled
[    0.201783] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe5ffffff
[    0.201788] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.201806] pci 0000:00:01.0: setting latency timer to 64
[    0.201812] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.201816] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.201819] pci_bus 0000:01: resource 1 mem: [0xe4000000-0xe5ffffff]
[    0.201822] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.201872] NET: Registered protocol family 2
[    0.201991] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.202567] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.204748] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.205858] TCP: Hash tables configured (established 131072 bind 65536)
[    0.205862] TCP reno registered
[    0.206027] NET: Registered protocol family 1
[    0.206061] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.206157] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    0.206175] pci 0000:01:00.0: Boot video device
[    0.206509] cpufreq-nforce2: No nForce2 chipset.
[    0.206547] Scanning for low memory corruption every 60 seconds
[    0.206696] audit: initializing netlink socket (disabled)
[    0.206717] type=2000 audit(1286267628.202:1): initialized
[    0.216138] Trying to unpack rootfs image as initramfs...
[    0.227150] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.235017] VFS: Disk quotas dquot_6.5.2
[    0.235179] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.235984] fuse init (API version 7.13)
[    0.236082] msgmni has been set to 1482
[    0.236414] alg: No test for stdrng (krng)
[    0.236457] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.236461] io scheduler noop registered
[    0.236464] io scheduler anticipatory registered
[    0.236466] io scheduler deadline registered
[    0.236509] io scheduler cfq registered (default)
[    0.236672] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.236700] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.236852] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.236858] ACPI: Power Button [PWRB]
[    0.236939] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.236942] ACPI: Power Button [PWRF]
[    0.237002] fan PNP0C0B:00: registered as cooling_device0
[    0.237009] ACPI: Fan [FAN] (on)
[    0.237402] processor LNXCPU:00: registered as cooling_device1
[    0.242498] thermal LNXTHERM:01: registered as thermal_zone0
[    0.242507] ACPI: Thermal Zone [THRM] (68 C)
[    0.247134] isapnp: Scanning for PnP cards...
[    0.259281] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.259407] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.259825] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.261216] brd: module loaded
[    0.261855] loop: module loaded
[    0.261981] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.262625] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.262628] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.262636]   alloc irq_desc for 20 on node -1
[    0.262639]   alloc kstat_irqs on node -1
[    0.262650] pata_acpi 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.262751] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.262774] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.306390] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    0.306763] Fixed MDIO Bus: probed
[    0.306830] PPP generic driver version 2.4.2
[    0.306891] tun: Universal TUN/TAP device driver, 1.6
[    0.306894] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.306999] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.307324] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[    0.307328] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    0.307331]   alloc irq_desc for 21 on node -1
[    0.307333]   alloc kstat_irqs on node -1
[    0.307338] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.307363] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.307406] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.307479] ehci_hcd 0000:00:10.4: irq 21, io mem 0xe6003000
[    0.318873] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.319115] usb usb1: configuration #1 chosen from 1 choice
[    0.319159] hub 1-0:1.0: USB hub found
[    0.319182] hub 1-0:1.0: 8 ports detected
[    0.319274] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.319302] uhci_hcd: USB Universal Host Controller Interface driver
[    0.319411] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.319426] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.319479] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.319508] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000cc00
[    0.319645] usb usb2: configuration #1 chosen from 1 choice
[    0.319676] hub 2-0:1.0: USB hub found
[    0.319691] hub 2-0:1.0: 2 ports detected
[    0.319742] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.319750] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.319806] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.319827] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d000
[    0.319950] usb usb3: configuration #1 chosen from 1 choice
[    0.319979] hub 3-0:1.0: USB hub found
[    0.319996] hub 3-0:1.0: 2 ports detected
[    0.320045] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.320051] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.320105] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.320125] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d400
[    0.320270] usb usb4: configuration #1 chosen from 1 choice
[    0.320300] hub 4-0:1.0: USB hub found
[    0.320315] hub 4-0:1.0: 2 ports detected
[    0.320374] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.320380] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.320418] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.320438] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d800
[    0.320561] usb usb5: configuration #1 chosen from 1 choice
[    0.320600] hub 5-0:1.0: USB hub found
[    0.320614] hub 5-0:1.0: 2 ports detected
[    0.320718] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.320722] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.320926] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.321070] mice: PS/2 mouse device common for all mice
[    0.321225] rtc_cmos 00:05: RTC can wake from S4
[    0.321288] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.321342] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.321438] device-mapper: uevent: version 1.0.3
[    0.323205] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.326398] device-mapper: multipath: version 1.1.0 loaded
[    0.326405] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.326648] EISA: Probing bus 0 at eisa.0
[    0.326670] Cannot allocate resource for EISA slot 4
[    0.326672] Cannot allocate resource for EISA slot 5
[    0.326685] EISA: Detected 0 cards.
[    0.331031] cpuidle: using governor ladder
[    0.331037] cpuidle: using governor menu
[    0.331626] TCP cubic registered
[    0.331804] NET: Registered protocol family 10
[    0.332317] lo: Disabled Privacy Extensions
[    0.332648] NET: Registered protocol family 17
[    0.332706] powernow-k8: Processor cpuid 6a0 not supported
[    0.332776] Using IPI No-Shortcut mode
[    0.332925] PM: Resume from disk failed.
[    0.332948] registered taskstats version 1
[    0.333266]   Magic number: 14:275:573
[    0.333443] rtc_cmos 00:05: setting system clock to 2010-10-05 08:33:48 UTC (1286267628)
[    0.333447] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.333449] EDD information not available.
[    0.348685] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.753690] Freeing initrd memory: 7778k freed
[    0.856314] isapnp: No Plug & Play device found
[    0.856337] Freeing unused kernel memory: 660k freed
[    0.857621] Write protecting the kernel text: 4680k
[    0.857654] Write protecting the kernel read-only data: 1844k
[    0.882451] udev: starting version 151
[    1.141616] sata_via 0000:00:0f.0: version 2.4
[    1.141652] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.141743] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.155418] scsi0 : sata_via
[    1.164157] scsi1 : sata_via
[    1.166287] ata1: SATA max UDMA/133 cmd 0xb000 ctl 0xb400 bmdma 0xc000 irq 20
[    1.166291] ata2: SATA max UDMA/133 cmd 0xb800 ctl 0xbc00 bmdma 0xc008 irq 20
[    1.166384] pata_via 0000:00:0f.1: version 0.3.4
[    1.166410] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.171276] scsi2 : pata_via
[    1.171536] scsi3 : pata_via
[    1.173948] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xc800 irq 14
[    1.173952] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xc808 irq 15
[    1.178526] Floppy drive(s): fd0 is 1.44M
[    1.195879] FDC 0 is a post-1991 82077
[    1.220035] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.344454] ata3.01: ATA-7: SAMSUNG SP1604N, TM100-24, max UDMA/133
[    1.344458] ata3.01: 312581808 sectors, multi 16: LBA48 
[    1.352305] ata3.01: configured for UDMA/133
[    1.368014] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.397532] usb 2-1: configuration #1 chosen from 1 choice
[    1.399696] hub 2-1:1.0: USB hub found
[    1.401375] hub 2-1:1.0: 4 ports detected
[    1.580023] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.590669] scsi 2:0:1:0: Direct-Access     ATA      SAMSUNG SP1604N  TM10 PQ: 0 ANSI: 5
[    1.590885] sd 2:0:1:0: Attached scsi generic sg0 type 0
[    1.591312] sd 2:0:1:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.591381] sd 2:0:1:0: [sda] Write Protect is off
[    1.591384] sd 2:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.591418] sd 2:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.591613]  sda: sda1 sda2 < sda5 >
[    1.620844] sd 2:0:1:0: [sda] Attached SCSI disk
[    1.644021] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    1.760337] ata4.00: ATAPI: ARTEC   WRR-52X           1.15 20030107, 1.15, max UDMA/33
[    1.760373] ata4.01: ATAPI: HL-DT-ST RW/DVD GCC-4481B, 1.07, max UDMA/33
[    1.776228] ata4.00: configured for UDMA/33
[    1.792217] ata4.01: configured for UDMA/33
[    1.799382] scsi 3:0:0:0: CD-ROM            ARTEC    WRR-52X          1.15 PQ: 0 ANSI: 5
[    1.812750] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    1.812754] Uniform CD-ROM driver Revision: 3.20
[    1.812892] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.812978] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.813714] scsi 3:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4481B 1.07 PQ: 0 ANSI: 5
[    1.815568] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.815817] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    1.815951] sr 3:0:1:0: Attached scsi generic sg2 type 5
[    1.819810] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.829689] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[    1.829696] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    1.829706]   alloc irq_desc for 23 on node -1
[    1.829709]   alloc kstat_irqs on node -1
[    1.829722] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    1.830582] eth0: VIA Rhine II at 0xe6004000, 00:11:2f:ac:11:2a, IRQ 23.
[    1.831292] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    1.831346]   alloc irq_desc for 19 on node -1
[    1.831348]   alloc kstat_irqs on node -1
[    1.831353] ohci1394 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.831611] usb 3-1: configuration #1 chosen from 1 choice
[    1.890087] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[e6002000-e60027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.072034] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    2.164049] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.251763] usb 4-1: configuration #1 chosen from 1 choice
[    2.492028] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    2.665868] usb 5-1: configuration #1 chosen from 1 choice
[    3.164233] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000a72b17]
[   12.784722] Adding 2245624k swap on /dev/sda5.  Priority:-1 extents:1 across:2245624k 
[   12.805728] udev: starting version 151
[   13.076699] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.077711] Linux agpgart interface v0.103
[   13.409986] agpgart: Detected VIA KM400/KM400A chipset
[   13.418870] parport_pc 00:0a: reported by Plug and Play ACPI
[   13.418993] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   13.426355] cfg80211: Calling CRDA to update world regulatory domain
[   13.448420] Linux video capture interface: v2.00
[   13.496821] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   13.532792] lp0: using parport0 (interrupt-driven).
[   13.553211] cfg80211: World regulatory domain updated:
[   13.553216] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.553220] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.553224] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.553227] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.553230] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.553233] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.581554] Initializing USB Mass Storage driver...
[   13.607126] scsi4 : SCSI emulation for USB Mass Storage devices
[   13.615264] type=1505 audit(1286267641.778:2):  operation="profile_load" pid=541 name="/sbin/dhclient3"
[   13.615604] type=1505 audit(1286267641.778:3):  operation="profile_load" pid=541 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.615802] type=1505 audit(1286267641.778:4):  operation="profile_load" pid=541 name="/usr/lib/connman/scripts/dhclient-script"
[   13.620184] usbcore: registered new interface driver usb-storage
[   13.620191] USB Mass Storage support registered.
[   13.620756] usb-storage: device found at 2
[   13.620758] usb-storage: waiting for device to settle before scanning
[   13.653891] vga16fb: initializing
[   13.653900] vga16fb: mapped to 0xc00a0000
[   13.654012] fb0: VGA16 VGA frame buffer device
[   13.661793] ppdev: user-space parallel port driver
[   13.661894] gspca: main v2.7.0 registered
[   13.674132] gspca: probing 046d:089d
[   13.674142] zc3xx: Sensor MC501CB
[   13.678504] gspca: probe ok
[   13.678530] gspca: probing 046d:089d
[   13.678544] gspca: probing 046d:089d
[   13.678576] usbcore: registered new interface driver zc3xx
[   13.678580] zc3xx: registered
[   13.695926]   alloc irq_desc for 17 on node -1
[   13.695931]   alloc kstat_irqs on node -1
[   13.695943] rtl8180 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.111112] Console: switching to colour frame buffer device 80x30
[   14.416265] nvidia: module license 'NVIDIA' taints kernel.
[   14.416273] Disabling lock debugging due to kernel taint
[   15.301228] usbcore: registered new interface driver hiddev
[   15.324059] input: Primax Kensington SlimBlade Presenter Mouse as /devices/pci0000:00/0000:00:10.2/usb4/4-1/4-1:1.0/input/input4
[   15.324262] generic-usb 0003:047D:1077.0001: input,hidraw0: USB HID v1.11 Mouse [Primax Kensington SlimBlade Presenter Mouse] on usb-0000:00:10.2-1/input0
[   15.324311] usbcore: registered new interface driver usbhid
[   15.324316] usbhid: v2.6:USB HID core driver
[   15.334527] phy0: Selected rate control algorithm 'minstrel'
[   15.335417] phy0: hwaddr 00:18:e7:63:19:91, RTL8185vD + rtl8225z2
[   15.472415] type=1505 audit(1286267643.638:5):  operation="profile_load" pid=711 name="/usr/share/gdm/guest-session/Xsession"
[   15.483180] type=1505 audit(1286267643.646:6):  operation="profile_replace" pid=720 name="/sbin/dhclient3"
[   15.483565] type=1505 audit(1286267643.646:7):  operation="profile_replace" pid=720 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.483790] type=1505 audit(1286267643.646:8):  operation="profile_replace" pid=720 name="/usr/lib/connman/scripts/dhclient-script"
[   15.584465] type=1505 audit(1286267643.750:9):  operation="profile_load" pid=726 name="/usr/bin/evince"
[   15.631152] type=1505 audit(1286267643.794:10):  operation="profile_load" pid=726 name="/usr/bin/evince-previewer"
[   15.658348] type=1505 audit(1286267643.822:11):  operation="profile_load" pid=726 name="/usr/bin/evince-thumbnailer"
[   15.668559] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   15.669027] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   15.669031] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   15.669038]   alloc irq_desc for 22 on node -1
[   15.669041]   alloc kstat_irqs on node -1
[   15.669052] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   15.773497] usbcore: registered new interface driver snd-usb-audio
[   15.971640]   alloc irq_desc for 16 on node -1
[   15.971646]   alloc kstat_irqs on node -1
[   15.971658] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.974145] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
[   16.420077] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   16.924274] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   16.924307] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   16.924617] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   16.924776] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   17.916823] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   17.916843] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   17.916910] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   18.621762] usb-storage: device scan complete
[   18.624656] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   18.629289] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   18.632672] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   18.635629] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   18.639104] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   18.639280] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   18.639447] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   18.639599] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   18.894364] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   18.899467] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   18.931373] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   18.936369] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   20.044426] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.047268] eth0: link down
[   20.047586] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.864071] usb 1-6: new high speed USB device using ehci_hcd and address 6
[   31.998549] usb 1-6: configuration #1 chosen from 1 choice
[   32.024853] scsi5 : SCSI emulation for USB Mass Storage devices
[   32.040145] usb-storage: device found at 6
[   32.040149] usb-storage: waiting for device to settle before scanning
[   37.040323] usb-storage: device scan complete
[   37.040797] scsi 5:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
[   37.048254] sd 5:0:0:0: Attached scsi generic sg7 type 0
[   37.053147] sd 5:0:0:0: [sdf] 7823296 512-byte logical blocks: (4.00 GB/3.72 GiB)
[   37.053631] sd 5:0:0:0: [sdf] Write Protect is off
[   37.053635] sd 5:0:0:0: [sdf] Mode Sense: 65 44 09 30
[   37.053638] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[   37.066634] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[   37.066645]  sdf: sdf1
[   37.071011] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[   37.071021] sd 5:0:0:0: [sdf] Attached SCSI removable disk
[  169.064104] wlan0: deauthenticating from 94:44:52:3f:84:9f by local choice (reason=3)
[  169.128036] wlan0: direct probe to AP 94:44:52:3f:84:9f (try 1)
[  169.328046] wlan0: direct probe to AP 94:44:52:3f:84:9f (try 2)
[  169.528047] wlan0: direct probe to AP 94:44:52:3f:84:9f (try 3)
[  169.728041] wlan0: direct probe to AP 94:44:52:3f:84:9f timed out
[  188.896041] wlan0: direct probe to AP 94:44:52:3f:84:9f (try 1)
[  189.096050] wlan0: direct probe to AP 94:44:52:3f:84:9f (try 2)
[  189.296061] wlan0: direct probe to AP 94:44:52:3f:84:9f (try 3)
[  189.496211] wlan0: direct probe to AP 94:44:52:3f:84:9f timed out
[  215.292040] wlan0: direct probe to AP 94:44:52:3f:84:9f (try 1)
[  215.492068] wlan0: direct probe to AP 94:44:52:3f:84:9f (try 2)
[  215.692101] wlan0: direct probe to AP 94:44:52:3f:84:9f (try 3)
[  215.892051] wlan0: direct probe to AP 94:44:52:3f:84:9f timed out
```

6. Network Configuration
```
  *-network:0             
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wlan0
       version: 20
       serial: 00:18:e7:63:19:91
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=32 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 ioport:a000(size=256) memory:e6000000-e60003ff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:11:2f:ac:11:2a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:e400(size=256) memory:e6004000-e60040ff

```

7. Scan for Networks
```
wlan0     No scan results
```

8. Ubuntu Version
```
Description:	Ubuntu 10.04.1 LTS
```

9. Kernel/Architecture
```
2.6.32-24-generic i686
```

10. Restarting Network
Did not help.

---

### Post by FullMetalManiac on 2010-10-05
Come on...anybody?  Surely there's someone who can help me...

---

### Post by TBABill on 2010-10-05
Does the Realtek require a proprietary driver? Mine are Broadcom and they do require it. Have you plugged into a router and allowed the system to update and find a driver for your card? I'm assuming it needs one because I am unfamiliar with Realtek. Disregard if not required.

---

### Post by FullMetalManiac on 2010-10-05
Not sure...lemme find out here...not entirely?  Has kernel 2.6 compatible drivers

---

