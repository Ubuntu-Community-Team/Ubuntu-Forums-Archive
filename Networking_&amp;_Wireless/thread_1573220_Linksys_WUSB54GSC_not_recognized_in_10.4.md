---
title: "Linksys WUSB54GSC not recognized in 10.4"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by SoFl W on 2010-09-12
First things first:

It is an old Dell Demension 8400, Pentium 4, 3.2 GHz and 1gig memory.

**LSPCI**
```
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:00.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
04:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
04:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
04:02.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
```**LSUSB**
```
Bus 005 Device 003: ID 046d:c509 Logitech, Inc. Cordless Keyboard & Mouse
Bus 005 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 006: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 1737:0075 Linksys 
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```**lspci -nn | grep 'Linksys'**
(nothing)

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:11:11:36:1b:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)
```**iwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.

**lsmod**
```
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
aes_i586                7268  679 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
snd_emu10k1_synth       5156  0 
snd_emux_synth         31695  1 snd_emu10k1_synth
snd_seq_virmidi         4213  1 snd_emux_synth
snd_seq_midi_emul       5492  1 snd_emux_synth
snd_emu10k1           130627  3 snd_emu10k1_synth
snd_ac97_codec        100646  1 snd_emu10k1
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  2 snd_emu10k1,snd_pcm
snd_util_mem            3106  2 snd_emux_synth,snd_emu10k1
snd_hwdep               5412  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      6003  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                47263  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          5700  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  17 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi                1793  0 
dcdbas                  5422  0 
usb_storage            39425  1 
serio_raw               3978  0 
lp                      7028  0 
soundcore               6620  1 snd
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
radeon                674135  3 
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
drm                   162471  5 radeon,ttm,drm_kms_helper
agpgart                31724  2 ttm,drm
floppy                 53016  0 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
i2c_algo_bit            5028  1 radeon
tg3                   109292  0
```**dmesg**
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe8cc00 (usable)
[    0.000000]  BIOS-e820: 000000003fe8cc00 - 000000003fe8ec00 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fe8ec00 - 000000003fe90c00 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fe90c00 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x3fe8c max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
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
[    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fe8cc00 (usable)
[    0.000000]  modified: 000000003fe8cc00 - 000000003fe8ec00 (ACPI NVS)
[    0.000000]  modified: 000000003fe8ec00 - 000000003fe90c00 (ACPI data)
[    0.000000]  modified: 000000003fe90c00 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2f29e000 - 2ff28bac
[    0.000000] ACPI: RSDP 000febf0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 000fcca7 0003C (v01 DELL    8400    00000006 ASL  00000061)
[    0.000000] ACPI: FACP 000fcce3 00074 (v01 DELL    8400    00000006 ASL  00000061)
[    0.000000] ACPI: DSDT fffc5c13 02ADC (v01   DELL    dt_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 3fe8cc00 00040
[    0.000000] ACPI: SSDT fffc882c 000BA (v01   DELL    st_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: APIC 000fcd57 00072 (v01 DELL    8400    00000006 ASL  00000061)
[    0.000000] ACPI: BOOT 000fcdc9 00028 (v01 DELL    8400    00000006 ASL  00000061)
[    0.000000] ACPI: MCFG 000fcdf1 0003E (v01 DELL    8400    00000006 ASL  00000061)
[    0.000000] ACPI: HPET 000fce2f 00038 (v01 DELL    8400    00000006 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 134MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [002f29e000 - 002ff28bac]          RAMDISK ==> [002f29e000 - 002ff28bac]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd164]              BRK ==> [00008da000 - 00008dd164]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003fe8c
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0003fe8c
[    0.000000] On node 0 totalpages: 261672
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 270 pages used for memmap
[    0.000000]   HighMem zone: 34176 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36024 r0 d21320 u1048576
[    0.000000] pcpu-alloc: s36024 r0 d21320 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259626
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=5c23aa5e-4d93-42ac-868c-afb7525b0d68 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5235440 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003fe8c)
[    0.000000] Memory: 1010536k/1047088k available (4673k kernel code, 35284k reserved, 2122k data, 656k init, 137784k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3192.361 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 6384.72 BogoMIPS (lpj=12769444)
[    0.004026] Security Framework initialized
[    0.004048] AppArmor: AppArmor initialized
[    0.004058] Mount-cache hash table entries: 512
[    0.008151] Initializing cgroup subsys ns
[    0.008156] Initializing cgroup subsys cpuacct
[    0.008161] Initializing cgroup subsys memory
[    0.008170] Initializing cgroup subsys devices
[    0.008173] Initializing cgroup subsys freezer
[    0.008176] Initializing cgroup subsys net_cls
[    0.008205] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.008209] CPU: L2 cache: 1024K
[    0.008212] CPU: Physical Processor ID: 0
[    0.008214] CPU: Processor Core ID: 0
[    0.008218] mce: CPU supports 4 MCE banks
[    0.008231] CPU0: Thermal monitoring enabled (TM1)
[    0.008237] using mwait in idle threads.
[    0.008244] Performance Events: no PMU driver, software events only.
[    0.008252] Checking 'hlt' instruction... OK.
[    0.027684] ACPI: Core revision 20090903
[    0.072756] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.072762] ftrace: allocating 21771 entries in 43 pages
[    0.076067] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.076385] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.119189] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
[    0.120001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.008000] CPU: L2 cache: 1024K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM1)
[    0.204132] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
[    0.204150] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.208024] Brought up 2 CPUs
[    0.208029] Total of 2 processors activated (12768.71 BogoMIPS).
[    0.208342] CPU0 attaching sched-domain:
[    0.208348]  domain 0: span 0-1 level SIBLING
[    0.208351]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.208359]   domain 1: span 0-1 level MC
[    0.208362]    groups: 0-1 (cpu_power = 1178)
[    0.208370] CPU1 attaching sched-domain:
[    0.208373]  domain 0: span 0-1 level SIBLING
[    0.208375]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.208382]   domain 1: span 0-1 level MC
[    0.208385]    groups: 0-1 (cpu_power = 1178)
[    0.208530] devtmpfs: initialized
[    0.208530] regulator: core version 0.5
[    0.208530] Time: 23:15:06  Date: 09/11/10
[    0.208530] NET: Registered protocol family 16
[    0.208530] Trying to unpack rootfs image as initramfs...
[    0.208530] EISA bus registered
[    0.208530] ACPI: bus type pci registered
[    0.208530] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.208530] PCI: MCFG area at e0000000 reserved in E820
[    0.208530] PCI: Using MMCONFIG for extended config space
[    0.208530] PCI: Using configuration type 1 for base access
[    0.210557] bio: create slab <bio-0> at 0
[    0.212728] ACPI: EC: Look up EC in DSDT
[    0.239864] ACPI: Interpreter enabled
[    0.240020] ACPI: (supports S0 S1 S3 S4 S5)
[    0.240068] ACPI: Using IOAPIC for interrupt routing
[    0.274315] ACPI: No dock devices found.
[    0.277402] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.277575] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.277582] pci 0000:00:01.0: PME# disabled
[    0.277698] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.277706] pci 0000:00:1c.0: PME# disabled
[    0.277802] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.277809] pci 0000:00:1c.1: PME# disabled
[    0.277878] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    0.277943] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    0.278007] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]
[    0.278071] pci 0000:00:1d.3: reg 20 io port: [0xff20-0xff3f]
[    0.278143] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80800-0xffa80bff]
[    0.278216] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.278224] pci 0000:00:1d.7: PME# disabled
[    0.278367] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.278375] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH6 GPIO
[    0.278381] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0c00-0c7f
[    0.278387] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 00e0-00ef
[    0.278420] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.278430] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.278440] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.278450] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.278460] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.278515] pci 0000:00:1f.2: reg 10 io port: [0xfe00-0xfe07]
[    0.278526] pci 0000:00:1f.2: reg 14 io port: [0xfe10-0xfe13]
[    0.278535] pci 0000:00:1f.2: reg 18 io port: [0xfe20-0xfe27]
[    0.278544] pci 0000:00:1f.2: reg 1c io port: [0xfe30-0xfe33]
[    0.278553] pci 0000:00:1f.2: reg 20 io port: [0xfea0-0xfeaf]
[    0.278562] pci 0000:00:1f.2: reg 24 32bit mmio: [0xdffffc00-0xdfffffff]
[    0.278590] pci 0000:00:1f.2: PME# supported from D3hot
[    0.278596] pci 0000:00:1f.2: PME# disabled
[    0.278664] pci 0000:00:1f.3: reg 20 io port: [0xece0-0xecff]
[    0.278734] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.278744] pci 0000:01:00.0: reg 14 io port: [0xdc00-0xdcff]
[    0.278753] pci 0000:01:00.0: reg 18 32bit mmio: [0xdfde0000-0xdfdeffff]
[    0.278776] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xdfe00000-0xdfe1ffff]
[    0.278803] pci 0000:01:00.0: supports D1 D2
[    0.278845] pci 0000:01:00.1: reg 10 32bit mmio: [0xdfdf0000-0xdfdfffff]
[    0.278897] pci 0000:01:00.1: supports D1 D2
[    0.278958] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.278965] pci 0000:00:01.0: bridge 32bit mmio: [0xdfd00000-0xdfefffff]
[    0.278972] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.279048] pci 0000:02:00.0: reg 10 64bit mmio: [0xdfcf0000-0xdfcfffff]
[    0.279142] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.279150] pci 0000:02:00.0: PME# disabled
[    0.279214] pci 0000:00:1c.0: bridge 32bit mmio: [0xdfc00000-0xdfcfffff]
[    0.279277] pci 0000:00:1c.1: bridge 32bit mmio: [0xdfb00000-0xdfbfffff]
[    0.279332] pci 0000:04:00.0: reg 10 32bit mmio: [0xdfafa000-0xdfafafff]
[    0.279344] pci 0000:04:00.0: reg 14 io port: [0xcc00-0xccff]
[    0.279403] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.279410] pci 0000:04:00.0: PME# disabled
[    0.279455] pci 0000:04:01.0: reg 10 io port: [0xc8c0-0xc8ff]
[    0.279515] pci 0000:04:01.0: supports D1 D2
[    0.279563] pci 0000:04:01.2: reg 10 32bit mmio: [0xdfaf9800-0xdfaf9fff]
[    0.279575] pci 0000:04:01.2: reg 14 32bit mmio: [0xdfafc000-0xdfafffff]
[    0.279636] pci 0000:04:01.2: supports D1 D2
[    0.279642] pci 0000:04:01.2: PME# supported from D0 D1 D2 D3hot
[    0.279649] pci 0000:04:01.2: PME# disabled
[    0.279703] pci 0000:04:02.0: reg 10 32bit mmio: [0xdfafb000-0xdfafbfff]
[    0.279763] pci 0000:04:02.0: supports D1 D2
[    0.279767] pci 0000:04:02.0: PME# supported from D0 D1 D2 D3hot
[    0.279775] pci 0000:04:02.0: PME# disabled
[    0.279833] pci 0000:00:1e.0: transparent bridge
[    0.279840] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
[    0.279847] pci 0000:00:1e.0: bridge 32bit mmio: [0xdfa00000-0xdfafffff]
[    0.279876] pci_bus 0000:00: on NUMA node 0
[    0.279884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.280306] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.280770] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.280999] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI3._PRT]
[    0.281231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    0.555853] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.556323] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.556703] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[    0.557080] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.557467] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.557855] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.558247] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.558635] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.558875] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.558888] vgaarb: loaded
[    0.559101] SCSI subsystem initialized
[    0.559253] libata version 3.00 loaded.
[    0.559380] usbcore: registered new interface driver usbfs
[    0.559404] usbcore: registered new interface driver hub
[    0.559450] usbcore: registered new device driver usb
[    0.559680] ACPI: WMI: Mapper loaded
[    0.559685] PCI: Using ACPI for IRQ routing
[    0.559954] NetLabel: Initializing
[    0.559958] NetLabel:  domain hash size = 128
[    0.559961] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.559982] NetLabel:  unlabeled traffic allowed by default
[    0.560075] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.560085] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.564111] Switching to clocksource tsc
[    0.567548] AppArmor: AppArmor Filesystem Enabled
[    0.567575] pnp: PnP ACPI init
[    0.567601] ACPI: bus type pnp registered
[    0.572422] pnp 00:01: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.572429] pnp 00:01: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.589562] pnp: PnP ACPI: found 10 devices
[    0.589568] ACPI: ACPI bus type pnp unregistered
[    0.589575] PnPBIOS: Disabled by ACPI PNP
[    0.589595] system 00:01: ioport range 0xc00-0xc7f has been reserved
[    0.589612] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[    0.589618] system 00:07: iomem range 0x100000-0xffffff could not be reserved
[    0.589624] system 00:07: iomem range 0x1000000-0x3fe8cbff could not be reserved
[    0.589629] system 00:07: iomem range 0xc0000-0xfffff could not be reserved
[    0.589635] system 00:07: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.589640] system 00:07: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.589646] system 00:07: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.589651] system 00:07: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.589657] system 00:07: iomem range 0xffc00000-0xffffffff has been reserved
[    0.589668] system 00:08: iomem range 0xe0000000-0xefffffff has been reserved
[    0.589674] system 00:08: iomem range 0xfeda0000-0xfedacfff has been reserved
[    0.624599] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.624606] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.624613] pci 0000:00:01.0:   MEM window: 0xdfd00000-0xdfefffff
[    0.624620] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xd7ffffff
[    0.624628] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.624635] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.624643] pci 0000:00:1c.0:   MEM window: 0xdfc00000-0xdfcfffff
[    0.624651] pci 0000:00:1c.0:   PREFETCH window: 0x00000040000000-0x000000401fffff
[    0.624661] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.624666] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
[    0.624674] pci 0000:00:1c.1:   MEM window: 0xdfb00000-0xdfbfffff
[    0.624682] pci 0000:00:1c.1:   PREFETCH window: 0x00000040200000-0x000000403fffff
[    0.624693] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.624700] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.624710] pci 0000:00:1e.0:   MEM window: 0xdfa00000-0xdfafffff
[    0.624719] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.624745]   alloc irq_desc for 16 on node -1
[    0.624750]   alloc kstat_irqs on node -1
[    0.624760] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.624767] pci 0000:00:01.0: setting latency timer to 64
[    0.624780] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.624787] pci 0000:00:1c.0: setting latency timer to 64
[    0.624799]   alloc irq_desc for 17 on node -1
[    0.624802]   alloc kstat_irqs on node -1
[    0.624809] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.624816] pci 0000:00:1c.1: setting latency timer to 64
[    0.624826] pci 0000:00:1e.0: setting latency timer to 64
[    0.624833] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.624838] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.624843] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.624848] pci_bus 0000:01: resource 1 mem: [0xdfd00000-0xdfefffff]
[    0.624853] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd7ffffff]
[    0.624858] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.624863] pci_bus 0000:02: resource 1 mem: [0xdfc00000-0xdfcfffff]
[    0.624868] pci_bus 0000:02: resource 2 pref mem [0x40000000-0x401fffff]
[    0.624873] pci_bus 0000:03: resource 0 io:  [0x2000-0x2fff]
[    0.624878] pci_bus 0000:03: resource 1 mem: [0xdfb00000-0xdfbfffff]
[    0.624883] pci_bus 0000:03: resource 2 pref mem [0x40200000-0x403fffff]
[    0.624888] pci_bus 0000:04: resource 0 io:  [0xc000-0xcfff]
[    0.624893] pci_bus 0000:04: resource 1 mem: [0xdfa00000-0xdfafffff]
[    0.624897] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.624902] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.624965] NET: Registered protocol family 2
[    0.625151] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.625734] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.626350] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.626707] TCP: Hash tables configured (established 131072 bind 65536)
[    0.626713] TCP reno registered
[    0.626891] NET: Registered protocol family 1
[    0.627032] pci 0000:01:00.0: Boot video device
[    0.627085] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    0.627090] Simple Boot Flag at 0x7a set to 0x1
[    0.627418] cpufreq-nforce2: No nForce2 chipset.
[    0.627470] Scanning for low memory corruption every 60 seconds
[    0.627660] audit: initializing netlink socket (disabled)
[    0.627675] type=2000 audit(1284246905.627:1): initialized
[    0.639126] highmem bounce pool size: 64 pages
[    0.639137] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.642122] VFS: Disk quotas dquot_6.5.2
[    0.642242] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.643435] fuse init (API version 7.13)
[    0.643608] msgmni has been set to 1706
[    0.643996] alg: No test for stdrng (krng)
[    0.644105] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.644111] io scheduler noop registered
[    0.644115] io scheduler anticipatory registered
[    0.644118] io scheduler deadline registered
[    0.644199] io scheduler cfq registered (default)
[    0.644445]   alloc irq_desc for 24 on node -1
[    0.644450]   alloc kstat_irqs on node -1
[    0.644463] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.644473] pcieport 0000:00:01.0: setting latency timer to 64
[    0.644620]   alloc irq_desc for 25 on node -1
[    0.644624]   alloc kstat_irqs on node -1
[    0.644636] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.644648] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.644825]   alloc irq_desc for 26 on node -1
[    0.644829]   alloc kstat_irqs on node -1
[    0.644842] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.644854] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.645006] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.645135] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.645291] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.645303] ACPI: Power Button [VBTN]
[    0.645397] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.645403] ACPI: Power Button [PWRF]
[    0.645954] processor LNXCPU:00: registered as cooling_device0
[    0.646025] processor LNXCPU:01: registered as cooling_device1
[    0.676627] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.677187] serial 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.677402] 0000:04:00.0: ttyS0 at I/O 0xcc08 (irq = 16) is a 16450
[    0.677528] 0000:04:00.0: ttyS1 at I/O 0xcc10 (irq = 16) is a 8250
[    0.677649] 0000:04:00.0: ttyS2 at I/O 0xcc18 (irq = 16) is a 16450
[    0.677777] 0000:04:00.0: ttyS3 at I/O 0xcc20 (irq = 16) is a 8250
[    0.677822] Couldn't register serial port 0000:04:00.0: -28
[    0.679570] isapnp: Scanning for PnP cards...
[    0.679768] brd: module loaded
[    0.680619] loop: module loaded
[    0.680768] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.680922] ata_piix 0000:00:1f.1: version 2.13
[    0.680939] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.680994] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.681101] scsi0 : ata_piix
[    0.681223] scsi1 : ata_piix
[    0.681279] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.681284] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.681314]   alloc irq_desc for 20 on node -1
[    0.681318]   alloc kstat_irqs on node -1
[    0.681326] ata_piix 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    0.681346] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.691671] ata1: port disabled. ignoring.
[    0.772427] ata2: port disabled. ignoring.
[    0.831250] Freeing initrd memory: 12842k freed
[    0.838913] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.839021] scsi2 : ata_piix
[    0.839133] scsi3 : ata_piix
[    0.839193] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 20
[    0.839199] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20
[    0.839869] Fixed MDIO Bus: probed
[    0.839934] PPP generic driver version 2.4.2
[    0.840028] tun: Universal TUN/TAP device driver, 1.6
[    0.840032] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.840184] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.840213]   alloc irq_desc for 21 on node -1
[    0.840217]   alloc kstat_irqs on node -1
[    0.840226] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.840246] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.840252] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.840312] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.840347] ehci_hcd 0000:00:1d.7: debug port 1
[    0.844242] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.844373] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800
[    0.859233] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.859378] usb usb1: configuration #1 chosen from 1 choice
[    0.859427] hub 1-0:1.0: USB hub found
[    0.859439] hub 1-0:1.0: 8 ports detected
[    0.859539] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.859565] uhci_hcd: USB Universal Host Controller Interface driver
[    0.859617] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.859628] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.859633] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.859685] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.859712] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
[    0.859859] usb usb2: configuration #1 chosen from 1 choice
[    0.859903] hub 2-0:1.0: USB hub found
[    0.859913] hub 2-0:1.0: 2 ports detected
[    0.859984]   alloc irq_desc for 22 on node -1
[    0.859989]   alloc kstat_irqs on node -1
[    0.859996] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.860007] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.860012] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.860062] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.860097] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[    0.860232] usb usb3: configuration #1 chosen from 1 choice
[    0.860278] hub 3-0:1.0: USB hub found
[    0.860288] hub 3-0:1.0: 2 ports detected
[    0.860353]   alloc irq_desc for 18 on node -1
[    0.860357]   alloc kstat_irqs on node -1
[    0.860363] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.860371] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.860376] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.860429] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.860464] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    0.860607] usb usb4: configuration #1 chosen from 1 choice
[    0.860654] hub 4-0:1.0: USB hub found
[    0.860664] hub 4-0:1.0: 2 ports detected
[    0.860730]   alloc irq_desc for 23 on node -1
[    0.860733]   alloc kstat_irqs on node -1
[    0.860740] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.860748] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.860752] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.860803] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.860841] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[    0.860986] usb usb5: configuration #1 chosen from 1 choice
[    0.861030] hub 5-0:1.0: USB hub found
[    0.861040] hub 5-0:1.0: 2 ports detected
[    0.861194] PNP: No PS/2 controller found. Probing ports directly.
[    1.032828] isapnp: No Plug & Play device found
[    1.886322] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.886463] mice: PS/2 mouse device common for all mice
[    1.886626] rtc_cmos 00:05: RTC can wake from S4
[    1.886678] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.886705] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    1.886847] device-mapper: uevent: version 1.0.3
[    1.886985] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.887117] device-mapper: multipath: version 1.1.0 loaded
[    1.887127] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.887281] EISA: Probing bus 0 at eisa.0
[    1.887288] Cannot allocate resource for EISA slot 1
[    1.887290] Cannot allocate resource for EISA slot 2
[    1.887310] EISA: Detected 0 cards.
[    1.887420] cpuidle: using governor ladder
[    1.887424] cpuidle: using governor menu
[    1.888024] TCP cubic registered
[    1.888190] NET: Registered protocol family 10
[    1.888849] lo: Disabled Privacy Extensions
[    1.889330] NET: Registered protocol family 17
[    1.889394] Using IPI No-Shortcut mode
[    1.889494] PM: Resume from disk failed.
[    1.889515] registered taskstats version 1
[    1.889889]   Magic number: 10:6:302
[    1.889912] tty tty31: hash matches
[    1.889961] rtc_cmos 00:05: setting system clock to 2010-09-11 23:15:07 UTC (1284246907)
[    1.889965] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.889967] EDD information not available.
[    2.030267] ata3.00: ATA-6: ST3160023AS, 8.05, max UDMA/133
[    2.030271] ata3.00: 312581808 sectors, multi 8: LBA48 
[    2.044452] ata3.00: configured for UDMA/133
[    2.044583] scsi 2:0:0:0: Direct-Access     ATA      ST3160023AS      8.05 PQ: 0 ANSI: 5
[    2.044763] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.044867] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.044935] sd 2:0:0:0: [sda] Write Protect is off
[    2.044939] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.044974] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.045157]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    2.097654] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.097670] Freeing unused kernel memory: 656k freed
[    2.098146] Write protecting the kernel text: 4676k
[    2.098201] Write protecting the kernel read-only data: 1840k
[    2.125124] udev: starting version 151
[    2.140119] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    2.272542] usb 1-3: configuration #1 chosen from 1 choice
[    2.272706] hub 1-3:1.0: USB hub found
[    2.272773] hub 1-3:1.0: 4 ports detected
[    2.274785] tg3.c:v3.102 (September 1, 2009)
[    2.274808] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.274822] tg3 0000:02:00.0: setting latency timer to 64
[    2.315894] eth0: Tigon3 [partno(BCM95751) rev 4001] (PCI Express) MAC address 00:11:11:36:1b:1e
[    2.315902] eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.315907] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.315912] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.318036] Floppy drive(s): fd0 is 1.44M
[    2.318215] ohci1394 0000:04:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.324558] Linux agpgart interface v0.103
[    2.351570] FDC 0 is a post-1991 82077
[    2.351817] [drm] Initialized drm 1.1.0 20060810
[    2.372599] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dfaf9800-dfaf9fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.372734] ohci1394 0000:04:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.384751] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    2.397492] [drm] radeon defaulting to kernel modesetting.
[    2.397497] [drm] radeon kernel modesetting enabled.
[    2.397548] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.397555] radeon 0000:01:00.0: setting latency timer to 64
[    2.399154] [drm] radeon: Initializing kernel modesetting.
[    2.399290] [drm] register mmio base: 0xDFDE0000
[    2.399293] [drm] register mmio size: 65536
[    2.399571] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[    2.399587] [drm] Generation 2 PCI interface, using max accessible memory
[    2.399590] [drm] radeon: VRAM 128M
[    2.399593] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[    2.399595] [drm] radeon: GTT 512M
[    2.399597] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[    2.399637]   alloc irq_desc for 27 on node -1
[    2.399640]   alloc kstat_irqs on node -1
[    2.399654] radeon 0000:01:00.0: irq 27 for MSI/MSI-X
[    2.399660] [drm] radeon: using MSI.
[    2.399686] [drm] radeon: irq initialized.
[    2.400076] [drm] Detected VRAM RAM=128M, BAR=128M
[    2.400082] [drm] RAM width 64bits DDR
[    2.400173] [TTM] Zone  kernel: Available graphics memory: 443558 kiB.
[    2.400176] [TTM] Zone highmem: Available graphics memory: 512450 kiB.
[    2.400194] [drm] radeon: 128M of VRAM memory ready
[    2.400197] [drm] radeon: 512M of GTT memory ready.
[    2.400218] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.400953] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[    2.400988] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[    2.401006] [drm] radeon: cp idle (0x10000C03)
[    2.401052] [drm] Loading R300 Microcode
[    2.401057] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[    2.404300] [drm] radeon: ring at 0x0000000020000000
[    2.404326] [drm] ring test succeeded in 1 usecs
[    2.404646] [drm] radeon: ib pool ready.
[    2.404773] [drm] ib test succeeded in 0 usecs
[    2.404941] [drm] Default TV standard: NTSC
[    2.404946] [drm] 27.000000000 MHz TV ref clk
[    2.404951] [drm] DFP table revision: 4
[    2.405055] [drm] Default TV standard: NTSC
[    2.405059] [drm] 27.000000000 MHz TV ref clk
[    2.405109] [drm] Radeon Display Connectors
[    2.405115] [drm] Connector 0:
[    2.405118] [drm]   VGA
[    2.405124] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    2.405128] [drm]   Encoders:
[    2.405131] [drm]     CRT1: INTERNAL_DAC1
[    2.405135] [drm] Connector 1:
[    2.405139] [drm]   DVI-I
[    2.405142] [drm]   HPD1
[    2.405147] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    2.405150] [drm]   Encoders:
[    2.405153] [drm]     CRT2: INTERNAL_DAC2
[    2.405156] [drm]     DFP1: INTERNAL_TMDS1
[    2.405159] [drm] Connector 2:
[    2.405162] [drm]   S-video
[    2.405165] [drm]   Encoders:
[    2.405168] [drm]     TV1: INTERNAL_DAC2
[    2.430028] ohci1394: fw-host1: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[dfafb000-dfafb7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    2.518884] usb 1-6: configuration #1 chosen from 1 choice
[    2.539275] [drm] fb mappable at 0xD00C0000
[    2.539279] [drm] vram apper at 0xD0000000
[    2.539281] [drm] size 5242880
[    2.539283] [drm] fb depth is 24
[    2.539285] [drm]    pitch is 5120
[    2.539386] fb0: radeondrmfb frame buffer device
[    2.539391] registered panic notifier
[    2.539400] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[    2.541774] vga16fb: initializing
[    2.541781] vga16fb: mapped to 0xc00a0000
[    2.541787] vga16fb: not registering due to another framebuffer present
[    2.606213] Console: switching to colour frame buffer device 160x64
[    2.700113] usb 1-3.4: new high speed USB device using ehci_hcd and address 6
[    2.808447] usb 1-3.4: configuration #1 chosen from 1 choice
[    2.808900] hub 1-3.4:1.0: USB hub found
[    2.808977] hub 1-3.4:1.0: 4 ports detected
[    3.048016] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    3.222738] usb 5-1: configuration #1 chosen from 1 choice
[    3.240040] usbcore: registered new interface driver hiddev
[    3.258111] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input3
[    3.258239] generic-usb 0003:046D:C50E.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.3-1/input0
[    3.258278] usbcore: registered new interface driver usbhid
[    3.258283] usbhid: v2.6:USB HID core driver
[    3.464022] usb 5-2: new low speed USB device using uhci_hcd and address 3
[    3.648319] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c041106c0ab]
[    3.649689] usb 5-2: configuration #1 chosen from 1 choice
[    3.666881] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input4
[    3.667000] generic-usb 0003:046D:C509.0002: input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.3-2/input0
[    3.674502] kjournald starting.  Commit interval 5 seconds
[    3.674516] EXT3-fs: mounted filesystem with ordered data mode.
[    3.700163] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/input/input5
[    3.700305] generic-usb 0003:046D:C509.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-2/input1
[    3.712209] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0000d1008007d1a7]
[   12.744098] usb 1-3.4.4: new high speed USB device using ehci_hcd and address 7
[   12.854645] usb 1-3.4.4: configuration #1 chosen from 1 choice
[   14.001284] Adding 1951736k swap on /dev/sda5.  Priority:-1 extents:1 across:1951736k 
[   14.141158] udev: starting version 151
[   14.343522] intel_rng: Firmware space is locked read-only. If you can't or
[   14.343525] intel_rng: don't want to disable this in firmware setup, and if
[   14.343528] intel_rng: you are certain that your system has a functional
[   14.343530] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   14.490915] type=1505 audit(1284261320.098:2):  operation="profile_load" pid=464 name="/sbin/dhclient3"
[   14.491709] type=1505 audit(1284261320.098:3):  operation="profile_load" pid=464 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.525135] type=1505 audit(1284261320.134:4):  operation="profile_load" pid=464 name="/usr/lib/connman/scripts/dhclient-script"
[   14.553999] EXT3 FS on sda6, internal journal
[   14.577442] lp: driver loaded but no devices found
[   14.600268] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.601795] dell-wmi: No known WMI GUID found
[   14.602448] Initializing USB Mass Storage driver...
[   14.620546] scsi4 : SCSI emulation for USB Mass Storage devices
[   14.624079] usbcore: registered new interface driver usb-storage
[   14.624087] USB Mass Storage support registered.
[   14.624386] usb-storage: device found at 7
[   14.624390] usb-storage: waiting for device to settle before scanning
[   14.764281] EMU10K1_Audigy 0000:04:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.768591] Installing spdif_bug patch: SB Audigy 2 ZS [SB0353]
[   15.462719] kjournald starting.  Commit interval 5 seconds
[   15.463063] EXT3 FS on sda7, internal journal
[   15.463070] EXT3-fs: mounted filesystem with ordered data mode.
[   16.006571] type=1505 audit(1284261321.614:5):  operation="profile_load" pid=716 name="/usr/share/gdm/guest-session/Xsession"
[   16.009777] type=1505 audit(1284261321.618:6):  operation="profile_replace" pid=718 name="/sbin/dhclient3"
[   16.010550] type=1505 audit(1284261321.618:7):  operation="profile_replace" pid=718 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.010965] type=1505 audit(1284261321.618:8):  operation="profile_replace" pid=718 name="/usr/lib/connman/scripts/dhclient-script"
[   16.017184] type=1505 audit(1284261321.626:9):  operation="profile_load" pid=719 name="/usr/bin/evince"
[   16.029187] type=1505 audit(1284261321.638:10):  operation="profile_load" pid=719 name="/usr/bin/evince-previewer"
[   16.035622] type=1505 audit(1284261321.642:11):  operation="profile_load" pid=719 name="/usr/bin/evince-thumbnailer"
[   16.136819] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.596987] ppdev: user-space parallel port driver
[   19.624874] usb-storage: device scan complete
[   19.625588] scsi 4:0:0:0: Direct-Access     JetFlash Transcend 8GB    8.07 PQ: 0 ANSI: 2
[   19.628569] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   19.633630] sd 4:0:0:0: [sdb] 15687680 512-byte logical blocks: (8.03 GB/7.48 GiB)
[   19.635782] sd 4:0:0:0: [sdb] Write Protect is off
[   19.635790] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   19.635795] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   19.638313] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   19.638320]  sdb: sdb1
[   20.182890] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   20.182901] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   26.623313] padlock: VIA PadLock not detected.
[   29.038392] end_request: I/O error, dev fd0, sector 0
[   29.136537] end_request: I/O error, dev fd0, sector 0
[  118.604144] uart_close: bad serial port count; tty->count is 1, port->count is 0
```
**sudo lshw -C network**
```
 *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:11:36:1b:1e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5751-v3.23a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:dfcf0000-dfcfffff
```
**iwlist scan**
(can't find the device)

**lsb_release -d**
Description:    Ubuntu 10.04 LTS

**uname -mr**
2.6.32-21-generic i686

**sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces... [ OK ]

  I am dual booting hoping to introduce my mother to Linux, and stop her  complaining about how slow Win XP has gotten.   The device works under XP with no problems. 
Ubuntu doesn't seem to recognize the USB stick.  The network manager icon does not list any wireless devices.  (I think it has a red no connection icon)  Before I purchased the device I did look to see if it was in the list, but I mis-read the last few letters and similar devices are listed.  The device is plugged into one of the rear USB ports.

I tried these two threads with no luck.
[http://ubuntuforums.org/showthread.php?t=687716](http://ubuntuforums.org/showthread.php?t=687716)
[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

Any suggestions on what to try next?  IMPORTANT:   There is not an easily accessible wired connection where the machine  needs to be.  I am transferring files from my PC to a USB stick to her machine.  


Thank you

---

### Post by JBAlaska on 2010-09-12
Put the Ubuntu LiveCD in your drive and go to: **System, Administration, Software sources** and check the box below **"Installable from CDROM"**. 
Then open a terminal and do:
```
sudo apt-get update
```

Then:
```
sudo apt-get install bcmwl-kernel-source

```
Now reboot and select the **BroadcomSTA driver**. in **System, Administration, Hardware Drivers** Restart again to enable the driver.

---

### Post by SoFl W on 2010-09-12
Thank you.  I tried what you said but it was missing too many dependencies.  I disconnected everything, lugged the machine here and ran the update manager to get everything up to date.

Received this error:
[COLOR=Blue]E: bcmwl-kernel-source: subprocess installed post-installation script returned error exit status 6[/COLOR]
[COLOR=Black]
Tried un-installing completely and re-installing, didn't work.  Kept giving me that error.  Un-installed it and just tried the regular bcmwl drivers, that installed fine but didn't find the usb stick.  [/COLOR]When I go into the hardware drivers there is nothing listed.
[COLOR=Black] 
Everything is up to date as of this posting, I will look for any other suggestions.   I will keep it on a wired connection for at least tonight.
[/COLOR]

---

### Post by SoFl W on 2010-09-12
Deleted by author.

---

### Post by SoFl W on 2010-09-14
Searching google for "WUSB54GSC linux" got me this [thread]("http://ubuntuforums.org/showthread.php?t=368931"), but searching the forums didn't.   I have tried it yet, but when I get the chance I will.

Anybody have any other suggestions?

---

### Post by SoFl W on 2010-09-16
a bump for the chump with the WUSB54GSC

---

### Post by GregIthaca on 2011-01-20
I'm having a related but different problem.  My WUSB54GSC is *recognized* but there is a kernel oops in the ndiswrapper that seems to prevent it from working.  I know that others have had the same problem, since I've seen the same kernel oops in their output, but people keep telling them to run ndiswrapper, lsusb, etc.
Oh, and I'm running 8.04 LTS.  Should I start a new thread for this, or is the WUSB54GSC enough of a connection?

---

### Post by GregIthaca on 2011-01-20
I'm having a related but different problem.  My WUSB54GSC is *recognized* but there is a kernel oops in the ndiswrapper that seems to prevent it from working.  I know that others have had the same problem, since I've seen the same kernel oops in their output, but people keep telling them to run ndiswrapper, lsusb, etc.
Oh, and I'm running 8.04 LTS.  Should I start a new thread for this, or is the WUSB54GSC enough of a connection?

---

### Post by GregIthaca on 2011-01-20
I'm having a related but different problem.  My WUSB54GSC is *recognized* but there is a kernel oops in the ndiswrapper that seems to prevent it from working.  I know that others have had the same problem, since I've seen the same kernel oops in their output, but people keep telling them to run ndiswrapper, lsusb, etc.
Oh, and I'm running 8.04 LTS.  Should I start a new thread for this, or is the WUSB54GSC enough of a connection?

---

