---
title: "Wireless internet will not transfer data yet says it is connected 9.04/9.10"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by 11010110 on 2009-11-06
Good afternoon everyone,

I had this problem a little bit in Jaunty but it worsened after upgrading to Karmic. When I boot up i automatically get logged into the network at my apartment and all is well for about 30 seconds. For some unknown reason I get logged off. Now the strange part is that the wireless says full bars in my panel and I can view all of the other connections just fine. When I disconnect and reconnect it works again for about 30 seconds or indefinitely (it is very random about when it wants to cut out and when it wants to work). Sometimes when I cannot browse the web through Opera or Firefox the torrents I have going still work fine as well. Also, when I boot up my Windows partition the internet works fine.

Here is a lot more information than anyone will probably need (more in the sig as well:

Wireless Brand, Model and Wireless Chipset:
```
eric@eric-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

Wireless Interface:
```
eric@eric-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"Two Penguins and an Apple"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:16:E3:9B:9E:85   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Modules:
```
eric@eric-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetadp             78344  0 
vboxnetflt             84840  0 
vboxdrv               121160  1 vboxnetflt
arc4                    1660  2 
ecb                     2524  2 
iwlagn                109052  0 
iwlcore               112508  1 iwlagn
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
joydev                 10272  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
pcmcia                 36808  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
uvcvideo               59080  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              181236  2 iwlagn,iwlcore
psmouse                56180  0 
videodev               36736  1 uvcvideo
ip_tables              11692  1 iptable_filter
lp                      8964  0 
v4l1_compat            14496  2 uvcvideo,videodev
soundcore               7264  1 snd
yenta_socket           24200  1 
tifm_7xx1               5372  0 
serio_raw               5280  0 
led_class               4096  2 iwlcore,sdhci
parport                35340  2 ppdev,lp
tifm_core               7832  1 tifm_7xx1
x_tables               16544  1 ip_tables
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211               93052  3 iwlagn,iwlcore,mac80211
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
sky2                   46560  0 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

```

Kernel Boot messages:
```
eric@eric-laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000097800 (usable)
[    0.000000]  BIOS-e820: 0000000000097800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6e3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7f6d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 07F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000097800 (usable)
[    0.000000]  modified: 0000000000097800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  modified: 000000007f6d0000 - 000000007f6e3000 (ACPI NVS)
[    0.000000]  modified: 000000007f6e3000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37867000 - 37fef301
[    0.000000] Allocated new RAMDISK: 008ad000 - 01035301
[    0.000000] Move RAMDISK from 0000000037867000 - 0000000037fef300 to 008ad000 - 01035300
[    0.000000] ACPI: RSDP 000f7da0 00024 (v02 TOSINV)
[    0.000000] ACPI: XSDT 7f6d79b1 0008C (v01 TOSINV TOSINV00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7f6dfbd2 000F4 (v03 TOSINV CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7f6d8d03 06E5B (v02 TOSINV CRESTLNE 06040000 INTL 20050624)
[    0.000000] ACPI: FACS 7f6e2fc0 00040
[    0.000000] ACPI: APIC 7f6dfcc6 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 7f6dfd2e 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7f6dfd66 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 7f6dfda2 00032 (v01 Intel   CRESTLN 06040000      00005A52)
[    0.000000] ACPI: TMOR 7f6dfdd4 00026 (v01 TOSINV          06040000 PTL  00000003)
[    0.000000] ACPI: APIC 7f6dfdfa 00068 (v01 TOSINV 	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: SLIC 7f6dfe62 00176 (v01 TOSINV TOSINV00 06040000  INV 00000000)
[    0.000000] ACPI: BOOT 7f6dffd8 00028 (v01 TOSINV $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7f6d8a1a 002E9 (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d7fc9 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d7f23 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d7a3d 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [0000097800 - 0000100000]    BIOS reserved ==> [0000097800 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac1a8]              BRK ==> [00008a9000 - 00008ac1a8]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 0001035301]      NEW RAMDISK ==> [00008ad000 - 0001035301]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f7dd0] f7dd0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f6d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000097
[    0.000000]     0: 0x00000100 -> 0x0007f6d0
[    0.000000] On node 0 totalpages: 521815
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1036200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3943 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292308 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
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
[    0.000000] PM: Registered nosave memory: 0000000000097000 - 0000000000098000
[    0.000000] PM: Registered nosave memory: 0000000000098000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2030000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517737
[    0.000000] Kernel command line: root=UUID=c0c7b980-a32f-4642-8653-43315f7e8ca3 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10438400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f6d0)
[    0.000000] Memory: 2043292k/2087744k available (4565k kernel code, 43056k reserved, 2143k data, 540k init, 1178440k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.581 MHz processor.
[    0.001374] Console: colour VGA+ 80x25
[    0.001378] console [tty0] enabled
[    0.001571] hpet clockevent registered
[    0.001574] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.001582] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.16 BogoMIPS (lpj=6650324)
[    0.001603] Security Framework initialized
[    0.001625] AppArmor: AppArmor initialized
[    0.001633] Mount-cache hash table entries: 512
[    0.001780] Initializing cgroup subsys ns
[    0.001785] Initializing cgroup subsys cpuacct
[    0.001790] Initializing cgroup subsys memory
[    0.001798] Initializing cgroup subsys freezer
[    0.001801] Initializing cgroup subsys net_cls
[    0.001817] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001820] CPU: L2 cache: 2048K
[    0.001824] CPU: Physical Processor ID: 0
[    0.001826] CPU: Processor Core ID: 0
[    0.001830] mce: CPU supports 6 MCE banks
[    0.001839] CPU0: Thermal monitoring handled by SMI
[    0.001843] using mwait in idle threads.
[    0.001850] Performance Counters: Core2 events, Intel PMU driver.
[    0.001861] ... version:                 2
[    0.001863] ... bit width:               40
[    0.001865] ... generic counters:        2
[    0.001867] ... value mask:              000000ffffffffff
[    0.001869] ... max period:              000000007fffffff
[    0.001871] ... fixed-purpose counters:  3
[    0.001873] ... counter mask:            0000000700000003
[    0.001878] Checking 'hlt' instruction... OK.
[    0.019005] ACPI: Core revision 20090521
[    0.036345] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076044] CPU0: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3325.01 BogoMIPS (lpj=6650033)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.165665] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
[    0.165682] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168024] Brought up 2 CPUs
[    0.168027] Total of 2 processors activated (6650.17 BogoMIPS).
[    0.168081] CPU0 attaching sched-domain:
[    0.168084]  domain 0: span 0-1 level MC
[    0.168087]   groups: 0 1
[    0.168094] CPU1 attaching sched-domain:
[    0.168097]  domain 0: span 0-1 level MC
[    0.168100]   groups: 1 0
[    0.168186] Booting paravirtualized kernel on bare hardware
[    0.168244] regulator: core version 0.5
[    0.168244] Time: 11:58:31  Date: 11/06/09
[    0.168244] NET: Registered protocol family 16
[    0.168250] EISA bus registered
[    0.168262] ACPI: bus type pci registered
[    0.168341] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.168344] PCI: MCFG area at e0000000 reserved in E820
[    0.168346] PCI: Using MMCONFIG for extended config space
[    0.168349] PCI: Using configuration type 1 for base access
[    0.169571] bio: create slab <bio-0> at 0
[    0.173176] ACPI: EC: Look up EC in DSDT
[    0.177016] ACPI: BIOS _OSI(Linux) query ignored
[    0.176020] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.192001] ACPI: Interpreter enabled
[    0.192001] ACPI: (supports S0 S3 S4 S5)
[    0.192001] ACPI: Using IOAPIC for interrupt routing
[    0.202853] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.202856] ACPI: EC: driver started in interrupt mode
[    0.202942] ACPI: Power Resource [FN00] (off)
[    0.203340] ACPI: No dock devices found.
[    0.204085] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.204200] pci 0000:00:02.0: reg 10 64bit mmio: [0xf5000000-0xf50fffff]
[    0.204210] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.204217] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.204270] pci 0000:00:02.1: reg 10 64bit mmio: [0xf5100000-0xf51fffff]
[    0.204398] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
[    0.204476] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
[    0.204559] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf5504800-0xf5504bff]
[    0.204631] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.204638] pci 0000:00:1a.7: PME# disabled
[    0.204702] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf5300000-0xf5303fff]
[    0.204774] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.204780] pci 0000:00:1b.0: PME# disabled
[    0.204880] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.204885] pci 0000:00:1c.0: PME# disabled
[    0.204989] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.204995] pci 0000:00:1c.1: PME# disabled
[    0.205098] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.205103] pci 0000:00:1c.2: PME# disabled
[    0.205206] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.205212] pci 0000:00:1c.3: PME# disabled
[    0.205315] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.205321] pci 0000:00:1c.4: PME# disabled
[    0.205394] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
[    0.205469] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
[    0.205544] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
[    0.205624] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf5504c00-0xf5504fff]
[    0.205698] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.205704] pci 0000:00:1d.7: PME# disabled
[    0.205892] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.205897] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.205903] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.205908] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[    0.205913] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
[    0.205918] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0400 (mask 003f)
[    0.205976] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.205986] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.205995] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.206004] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.206013] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.206098] pci 0000:00:1f.2: reg 10 io port: [0x1c00-0x1c07]
[    0.206108] pci 0000:00:1f.2: reg 14 io port: [0x18d4-0x18d7]
[    0.206117] pci 0000:00:1f.2: reg 18 io port: [0x18d8-0x18df]
[    0.206126] pci 0000:00:1f.2: reg 1c io port: [0x18d0-0x18d3]
[    0.206135] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.206145] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf5504000-0xf55047ff]
[    0.206195] pci 0000:00:1f.2: PME# supported from D3hot
[    0.206201] pci 0000:00:1f.2: PME# disabled
[    0.206239] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.206269] pci 0000:00:1f.3: reg 20 io port: [0x1c20-0x1c3f]
[    0.206391] pci 0000:02:00.0: reg 10 64bit mmio: [0xf0000000-0xf0003fff]
[    0.206404] pci 0000:02:00.0: reg 18 io port: [0x2000-0x20ff]
[    0.206503] pci 0000:02:00.0: supports D1 D2
[    0.206506] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206513] pci 0000:02:00.0: PME# disabled
[    0.206585] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.206592] pci 0000:00:1c.0: bridge 32bit mmio: [0xf0000000-0xf0ffffff]
[    0.206802] pci 0000:03:00.0: reg 10 64bit mmio: [0xf1000000-0xf1001fff]
[    0.207039] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.207066] pci 0000:03:00.0: PME# disabled
[    0.207175] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    0.207181] pci 0000:00:1c.1: bridge 32bit mmio: [0xf1000000-0xf1ffffff]
[    0.207253] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    0.207260] pci 0000:00:1c.2: bridge 32bit mmio: [0xf2000000-0xf2ffffff]
[    0.207332] pci 0000:00:1c.3: bridge io port: [0x5000-0x5fff]
[    0.207338] pci 0000:00:1c.3: bridge 32bit mmio: [0xf3000000-0xf3ffffff]
[    0.207411] pci 0000:00:1c.4: bridge io port: [0x6000-0x6fff]
[    0.207417] pci 0000:00:1c.4: bridge 32bit mmio: [0xf4000000-0xf4ffffff]
[    0.207488] pci 0000:08:06.0: reg 10 32bit mmio: [0xf5204000-0xf5204fff]
[    0.207518] pci 0000:08:06.0: supports D1 D2
[    0.207521] pci 0000:08:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.207527] pci 0000:08:06.0: PME# disabled
[    0.207579] pci 0000:08:06.1: reg 10 32bit mmio: [0xf5206000-0xf52067ff]
[    0.207590] pci 0000:08:06.1: reg 14 32bit mmio: [0xf5200000-0xf5203fff]
[    0.207661] pci 0000:08:06.1: supports D1 D2
[    0.207664] pci 0000:08:06.1: PME# supported from D0 D1 D2 D3hot
[    0.207671] pci 0000:08:06.1: PME# disabled
[    0.207721] pci 0000:08:06.2: reg 10 32bit mmio: [0xf5205000-0xf5205fff]
[    0.207792] pci 0000:08:06.2: supports D1 D2
[    0.207795] pci 0000:08:06.2: PME# supported from D0 D1 D2 D3hot
[    0.207801] pci 0000:08:06.2: PME# disabled
[    0.207852] pci 0000:08:06.3: reg 10 32bit mmio: [0xf5206800-0xf52068ff]
[    0.207924] pci 0000:08:06.3: supports D1 D2
[    0.207926] pci 0000:08:06.3: PME# supported from D0 D1 D2 D3hot
[    0.207933] pci 0000:08:06.3: PME# disabled
[    0.208007] pci 0000:00:1e.0: transparent bridge
[    0.208016] pci 0000:00:1e.0: bridge 32bit mmio: [0xf5200000-0xf52fffff]
[    0.208090] pci_bus 0000:00: on NUMA node 0
[    0.208096] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.208378] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.208472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.208564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.208655] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.208746] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.208874] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.222728] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.222854] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.222977] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.223100] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.223222] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.223345] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.223469] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.223592] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.223810] SCSI subsystem initialized
[    0.224021] libata version 3.00 loaded.
[    0.224053] usbcore: registered new interface driver usbfs
[    0.224053] usbcore: registered new interface driver hub
[    0.224055] usbcore: registered new device driver usb
[    0.224063] ACPI: WMI: Mapper loaded
[    0.224064] PCI: Using ACPI for IRQ routing
[    0.236009] Bluetooth: Core ver 2.15
[    0.236016] NET: Registered protocol family 31
[    0.236016] Bluetooth: HCI device and connection manager initialized
[    0.236019] Bluetooth: HCI socket layer initialized
[    0.236021] NetLabel: Initializing
[    0.236023] NetLabel:  domain hash size = 128
[    0.236025] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.236039] NetLabel:  unlabeled traffic allowed by default
[    0.236077] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.236084] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.253713] pnp: PnP ACPI init
[    0.253725] ACPI: bus type pnp registered
[    0.258303] pnp: PnP ACPI: found 10 devices
[    0.258306] ACPI: ACPI bus type pnp unregistered
[    0.258311] PnPBIOS: Disabled by ACPI PNP
[    0.258324] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.258329] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.258332] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.258336] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.258339] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.258343] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.258346] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.258350] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.258358] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.258366] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.258369] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.258373] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.258376] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.258380] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.258383] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    0.293070] AppArmor: AppArmor Filesystem Enabled
[    0.293170] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.293174] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.293182] pci 0000:00:1c.0:   MEM window: 0xf0000000-0xf0ffffff
[    0.293187] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.293193] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.293197] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.293205] pci 0000:00:1c.1:   MEM window: 0xf1000000-0xf1ffffff
[    0.293210] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.293216] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.293220] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    0.293227] pci 0000:00:1c.2:   MEM window: 0xf2000000-0xf2ffffff
[    0.293233] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.293238] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.293243] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
[    0.293250] pci 0000:00:1c.3:   MEM window: 0xf3000000-0xf3ffffff
[    0.293256] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.293262] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:06
[    0.293266] pci 0000:00:1c.4:   IO window: 0x6000-0x6fff
[    0.293274] pci 0000:00:1c.4:   MEM window: 0xf4000000-0xf4ffffff
[    0.293279] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.293287] pci 0000:08:06.0: CardBus bridge, secondary bus 0000:09
[    0.293290] pci 0000:08:06.0:   IO window: 0x007000-0x0070ff
[    0.293297] pci 0000:08:06.0:   IO window: 0x007400-0x0074ff
[    0.293304] pci 0000:08:06.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.293311] pci 0000:08:06.0:   MEM window: 0x88000000-0x8bffffff
[    0.293317] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    0.293321] pci 0000:00:1e.0:   IO window: 0x7000-0x7fff
[    0.293329] pci 0000:00:1e.0:   MEM window: 0xf5200000-0xf52fffff
[    0.293335] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.293350]   alloc irq_desc for 17 on node -1
[    0.293353]   alloc kstat_irqs on node -1
[    0.293359] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.293366] pci 0000:00:1c.0: setting latency timer to 64
[    0.293376]   alloc irq_desc for 16 on node -1
[    0.293378]   alloc kstat_irqs on node -1
[    0.293382] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.293388] pci 0000:00:1c.1: setting latency timer to 64
[    0.293397]   alloc irq_desc for 18 on node -1
[    0.293399]   alloc kstat_irqs on node -1
[    0.293404] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.293410] pci 0000:00:1c.2: setting latency timer to 64
[    0.293420]   alloc irq_desc for 19 on node -1
[    0.293422]   alloc kstat_irqs on node -1
[    0.293426] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.293432] pci 0000:00:1c.3: setting latency timer to 64
[    0.293443] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.293449] pci 0000:00:1c.4: setting latency timer to 64
[    0.293459] pci 0000:00:1e.0: setting latency timer to 64
[    0.293470] pci 0000:08:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.293478] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.293482] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.293485] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.293488] pci_bus 0000:02: resource 1 mem: [0xf0000000-0xf0ffffff]
[    0.293491] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]
[    0.293494] pci_bus 0000:03: resource 1 mem: [0xf1000000-0xf1ffffff]
[    0.293498] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    0.293501] pci_bus 0000:04: resource 1 mem: [0xf2000000-0xf2ffffff]
[    0.293504] pci_bus 0000:05: resource 0 io:  [0x5000-0x5fff]
[    0.293507] pci_bus 0000:05: resource 1 mem: [0xf3000000-0xf3ffffff]
[    0.293510] pci_bus 0000:06: resource 0 io:  [0x6000-0x6fff]
[    0.293513] pci_bus 0000:06: resource 1 mem: [0xf4000000-0xf4ffffff]
[    0.293516] pci_bus 0000:08: resource 0 io:  [0x7000-0x7fff]
[    0.293519] pci_bus 0000:08: resource 1 mem: [0xf5200000-0xf52fffff]
[    0.293522] pci_bus 0000:08: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.293525] pci_bus 0000:08: resource 3 io:  [0x00-0xffff]
[    0.293528] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffff]
[    0.293531] pci_bus 0000:09: resource 0 io:  [0x7000-0x70ff]
[    0.293534] pci_bus 0000:09: resource 1 io:  [0x7400-0x74ff]
[    0.293537] pci_bus 0000:09: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.293540] pci_bus 0000:09: resource 3 mem: [0x88000000-0x8bffffff]
[    0.293580] NET: Registered protocol family 2
[    0.293690] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.294072] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.294587] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.294844] TCP: Hash tables configured (established 131072 bind 65536)
[    0.294846] TCP reno registered
[    0.294930] NET: Registered protocol family 1
[    0.295002] Trying to unpack rootfs image as initramfs...
[    0.501707] Switched to high resolution mode on CPU 1
[    0.503990] Switched to high resolution mode on CPU 0
[    0.525398] Freeing initrd memory: 7712k freed
[    0.530135] Simple Boot Flag at 0x36 set to 0x1
[    0.530353] cpufreq-nforce2: No nForce2 chipset.
[    0.530386] Scanning for low memory corruption every 60 seconds
[    0.530505] audit: initializing netlink socket (disabled)
[    0.530524] type=2000 audit(1257508711.529:1): initialized
[    0.540786] highmem bounce pool size: 64 pages
[    0.540792] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.542581] VFS: Disk quotas dquot_6.5.2
[    0.542657] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.543297] fuse init (API version 7.12)
[    0.543396] msgmni has been set to 1706
[    0.543650] alg: No test for stdrng (krng)
[    0.543662] io scheduler noop registered
[    0.543664] io scheduler anticipatory registered
[    0.543667] io scheduler deadline registered
[    0.543715] io scheduler cfq registered (default)
[    0.543729] pci 0000:00:02.0: Boot video device
[    0.544066]   alloc irq_desc for 24 on node -1
[    0.544069]   alloc kstat_irqs on node -1
[    0.544083] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.544096] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.544279]   alloc irq_desc for 25 on node -1
[    0.544281]   alloc kstat_irqs on node -1
[    0.544291] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.544304] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.544484]   alloc irq_desc for 26 on node -1
[    0.544486]   alloc kstat_irqs on node -1
[    0.544497] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.544509] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.544691]   alloc irq_desc for 27 on node -1
[    0.544694]   alloc kstat_irqs on node -1
[    0.544704] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.544717] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.544897]   alloc irq_desc for 28 on node -1
[    0.544900]   alloc kstat_irqs on node -1
[    0.544910] pcieport-driver 0000:00:1c.4: irq 28 for MSI/MSI-X
[    0.544923] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.545062] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.545250] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.549279] ACPI: AC Adapter [ADP0] (on-line)
[    0.549350] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.549355] ACPI: Power Button [PWRF]
[    0.549434] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.550497] ACPI: Lid Switch [LID]
[    0.550550] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.550554] ACPI: Power Button [PWRB]
[    0.550697] fan PNP0C0B:00: registered as cooling_device0
[    0.550704] ACPI: Fan [FAN0] (off)
[    0.551498] ACPI: SSDT 7f6d8757 001FB (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.552087] ACPI: SSDT 7f6d8228 004AA (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.554714] Monitor-Mwait will be used to enter C-1 state
[    0.554739] Monitor-Mwait will be used to enter C-2 state
[    0.554762] Monitor-Mwait will be used to enter C-3 state
[    0.554771] Marking TSC unstable due to TSC halts in idle
[    0.554794] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.554818] processor LNXCPU:00: registered as cooling_device1
[    0.554823] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.555237] ACPI: SSDT 7f6d8952 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.555671] ACPI: SSDT 7f6d86d2 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.556772] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.556796] processor LNXCPU:01: registered as cooling_device2
[    0.556801] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.564033] thermal LNXTHERM:01: registered as thermal_zone0
[    0.564043] ACPI: Thermal Zone [TZ00] (75 C)
[    0.564738] ACPI: Invalid active1 threshold
[    0.565315] thermal LNXTHERM:02: registered as thermal_zone1
[    0.565327] ACPI: Thermal Zone [TZ01] (77 C)
[    0.565784] isapnp: Scanning for PnP cards...
[    0.578399] ACPI: Battery Slot [BAT0] (battery present)
[    0.926181] isapnp: No Plug & Play device found
[    0.927566] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.929155] brd: module loaded
[    0.929698] loop: module loaded
[    0.929777] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.929865] ahci 0000:00:1f.2: version 3.0
[    0.929881] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.929918]   alloc irq_desc for 29 on node -1
[    0.929920]   alloc kstat_irqs on node -1
[    0.929932] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.930006] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    0.930010] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    0.930017] ahci 0000:00:1f.2: setting latency timer to 64
[    0.930267] scsi0 : ahci
[    0.930372] scsi1 : ahci
[    0.930438] scsi2 : ahci
[    0.930564] ata1: SATA max UDMA/133 abar m2048@0xf5504000 port 0xf5504100 irq 29
[    0.930569] ata2: SATA max UDMA/133 abar m2048@0xf5504000 port 0xf5504180 irq 29
[    0.930573] ata3: SATA max UDMA/133 abar m2048@0xf5504000 port 0xf5504200 irq 29
[    0.930633] ata_piix 0000:00:1f.1: version 2.13
[    0.930643] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.930683] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.930758] scsi3 : ata_piix
[    0.930835] scsi4 : ata_piix
[    0.931526] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.931530] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.932633] Fixed MDIO Bus: probed
[    0.932674] PPP generic driver version 2.4.2
[    0.932777] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.932800] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.932812] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.932817] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.932875] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.936775] ehci_hcd 0000:00:1a.7: debug port 1
[    0.936784] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.936800] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf5504800
[    0.949016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.949106] usb usb1: configuration #1 chosen from 1 choice
[    0.949140] hub 1-0:1.0: USB hub found
[    0.949149] hub 1-0:1.0: 4 ports detected
[    0.949216]   alloc irq_desc for 23 on node -1
[    0.949219]   alloc kstat_irqs on node -1
[    0.949225] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.949236] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.949240] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.949276] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.953198] ehci_hcd 0000:00:1d.7: debug port 1
[    0.953206] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.953220] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf5504c00
[    0.968020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.968090] usb usb2: configuration #1 chosen from 1 choice
[    0.968121] hub 2-0:1.0: USB hub found
[    0.968132] hub 2-0:1.0: 6 ports detected
[    0.968205] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.968225] uhci_hcd: USB Universal Host Controller Interface driver
[    0.968252] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.968259] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.968263] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.968298] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.968338] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    0.968434] usb usb3: configuration #1 chosen from 1 choice
[    0.968466] hub 3-0:1.0: USB hub found
[    0.968473] hub 3-0:1.0: 2 ports detected
[    0.968529]   alloc irq_desc for 21 on node -1
[    0.968531]   alloc kstat_irqs on node -1
[    0.968537] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.968544] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.968549] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.968583] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.968622] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.968716] usb usb4: configuration #1 chosen from 1 choice
[    0.968747] hub 4-0:1.0: USB hub found
[    0.968755] hub 4-0:1.0: 2 ports detected
[    0.968812] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.968819] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.968823] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.968863] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.968892] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.968984] usb usb5: configuration #1 chosen from 1 choice
[    0.969026] hub 5-0:1.0: USB hub found
[    0.969034] hub 5-0:1.0: 2 ports detected
[    0.969089] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.969097] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.969101] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.969146] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.969184] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.969275] usb usb6: configuration #1 chosen from 1 choice
[    0.969305] hub 6-0:1.0: USB hub found
[    0.969312] hub 6-0:1.0: 2 ports detected
[    0.969367] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.969375] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.969379] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.969415] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.969446] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.969539] usb usb7: configuration #1 chosen from 1 choice
[    0.969570] hub 7-0:1.0: USB hub found
[    0.969577] hub 7-0:1.0: 2 ports detected
[    0.969698] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.971982] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.971988] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.972073] mice: PS/2 mouse device common for all mice
[    0.972205] rtc_cmos 00:07: RTC can wake from S4
[    0.972240] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.972274] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.972389] device-mapper: uevent: version 1.0.3
[    0.972482] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.972552] device-mapper: multipath: version 1.1.0 loaded
[    0.972555] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.972683] EISA: Probing bus 0 at eisa.0
[    0.972690] Cannot allocate resource for EISA slot 1
[    0.972693] Cannot allocate resource for EISA slot 2
[    0.972696] Cannot allocate resource for EISA slot 3
[    0.972698] Cannot allocate resource for EISA slot 4
[    0.972701] Cannot allocate resource for EISA slot 5
[    0.972703] Cannot allocate resource for EISA slot 6
[    0.972706] Cannot allocate resource for EISA slot 7
[    0.972713] EISA: Detected 0 cards.
[    0.972872] cpuidle: using governor ladder
[    0.973016] cpuidle: using governor menu
[    0.973602] TCP cubic registered
[    0.973784] NET: Registered protocol family 10
[    0.974330] lo: Disabled Privacy Extensions
[    0.974740] NET: Registered protocol family 17
[    0.974760] Bluetooth: L2CAP ver 2.13
[    0.974762] Bluetooth: L2CAP socket layer initialized
[    0.974765] Bluetooth: SCO (Voice Link) ver 0.6
[    0.974767] Bluetooth: SCO socket layer initialized
[    0.974809] Bluetooth: RFCOMM TTY layer initialized
[    0.974812] Bluetooth: RFCOMM socket layer initialized
[    0.974815] Bluetooth: RFCOMM ver 1.11
[    0.975428] Using IPI No-Shortcut mode
[    0.975498] PM: Resume from disk failed.
[    0.975512] registered taskstats version 1
[    0.975659]   Magic number: 1:90:984
[    0.975760] rtc_cmos 00:07: setting system clock to 2009-11-06 11:58:32 UTC (1257508712)
[    0.975764] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.975766] EDD information not available.
[    0.992663] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.109098] ata4.00: ATAPI: PIONEER DVD-RW DVR-K17LF, 4.53, max UDMA/33
[    1.140533] ata4.00: configured for UDMA/33
[    1.248079] ata2: SATA link down (SStatus 0 SControl 300)
[    1.248102] ata3: SATA link down (SStatus 0 SControl 300)
[    1.260073] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.406174] usb 1-2: configuration #1 chosen from 1 choice
[    1.416062] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.416806] ACPI Warning: \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer 20090521 nspredef-940
[    1.416815] ata1.00: _GTF unexpected object type 0x1
[    1.500045] Clocksource tsc unstable (delta = -287727587 ns)
[    1.766719] ata1.00: ATA-7: TOSHIBA MK2035GSS, DK020M, max UDMA/100
[    1.766724] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.768152] ata1.00: _GTF unexpected object type 0x1
[    1.768356] ata1.00: configured for UDMA/100
[    1.784203] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2035GS DK02 PQ: 0 ANSI: 5
[    1.784334] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.784379] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.784432] sd 0:0:0:0: [sda] Write Protect is off
[    1.784436] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.784464] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.784605]  sda:
[    1.794208] scsi 3:0:0:0: CD-ROM            PIONEER  DVD-RW DVR-K17LF 4.53 PQ: 0 ANSI: 5
[    1.825200] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.825204] Uniform CD-ROM driver Revision: 3.20
[    1.825299] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.825343] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.834860]  sda1 sda2 sda3 sda4 < sda5 >
[    1.868772] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.868804] Freeing unused kernel memory: 540k freed
[    1.869198] Write protecting the kernel text: 4568k
[    1.869265] Write protecting the kernel read-only data: 1836k
[    1.909029] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    2.007856] Linux agpgart interface v0.103
[    2.011371] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    2.012089] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    2.015424] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    2.112914] usb 4-1: configuration #1 chosen from 1 choice
[    2.119279] [drm] Initialized drm 1.1.0 20060810
[    2.134129] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.134136] i915 0000:00:02.0: setting latency timer to 64
[    2.136712]   alloc irq_desc for 30 on node -1
[    2.136716]   alloc kstat_irqs on node -1
[    2.136727] i915 0000:00:02.0: irq 30 for MSI/MSI-X
[    2.138912] sky2 driver version 1.23
[    2.138955] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.138970] sky2 0000:02:00.0: setting latency timer to 64
[    2.138993] sky2 0000:02:00.0: Yukon-2 FE chip revision 3
[    2.139105]   alloc irq_desc for 31 on node -1
[    2.139107]   alloc kstat_irqs on node -1
[    2.139123] sky2 0000:02:00.0: irq 31 for MSI/MSI-X
[    2.139922] sky2 eth0: addr 00:a0:d1:7b:c8:2b
[    2.210306] ohci1394 0000:08:06.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.268390] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f5206000-f52067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.625633] [drm] TV-14: set mode NTSC 480i 0
[    2.751477] [drm] fb0: inteldrmfb frame buffer device
[    2.757094] acpi device:0a: registered as cooling_device3
[    2.757355] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/input/input5
[    2.757386] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.757417] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.827187] [drm] LVDS-8: set mode 1280x800 17
[    3.060378] Console: switching to colour frame buffer device 160x50
[    3.248439] xor: automatically using best checksumming function: pIII_sse
[    3.268016]    pIII_sse  :  6100.000 MB/sec
[    3.268018] xor: using function: pIII_sse (6100.000 MB/sec)
[    3.270973] device-mapper: dm-raid45: initialized v0.2594b
[    3.632199] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d17bc82b]
[    3.702226] PM: Starting manual resume from disk
[    3.702231] PM: Resume from partition 8:5
[    3.702233] PM: Checking hibernation image.
[    3.702648] PM: Resume from disk failed.
[    3.749873] EXT4-fs (sda3): barriers enabled
[    3.764057] kjournald2 starting: pid 432, dev sda3:8, commit interval 5 seconds
[    3.764084] EXT4-fs (sda3): delayed allocation enabled
[    3.764089] EXT4-fs: file extents enabled
[    3.764317] EXT4-fs: mballoc enabled
[    3.764333] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    4.847303] type=1505 audit(1257508716.369:2): operation="profile_load" pid=455 name=/usr/share/gdm/guest-session/Xsession
[    4.870894] type=1505 audit(1257508716.393:3): operation="profile_load" pid=456 name=/sbin/dhclient3
[    4.871777] type=1505 audit(1257508716.393:4): operation="profile_load" pid=456 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.872257] type=1505 audit(1257508716.393:5): operation="profile_load" pid=456 name=/usr/lib/connman/scripts/dhclient-script
[    4.940185] type=1505 audit(1257508716.464:6): operation="profile_load" pid=457 name=/usr/bin/evince
[    4.953806] type=1505 audit(1257508716.476:7): operation="profile_load" pid=457 name=/usr/bin/evince-previewer
[    4.961841] type=1505 audit(1257508716.484:8): operation="profile_load" pid=457 name=/usr/bin/evince-thumbnailer
[    5.007200] type=1505 audit(1257508716.528:9): operation="profile_load" pid=459 name=/usr/lib/cups/backend/cups-pdf
[    6.938875] Adding 3140668k swap on /dev/sda5.  Priority:-1 extents:1 across:3140668k 
[    7.294561] EXT4-fs (sda3): internal journal on sda3:8
[    9.836406] udev: starting version 147
[   10.395017] __ratelimit: 6 callbacks suppressed
[   10.395021] type=1505 audit(1257526721.916:12): operation="profile_replace" pid=781 name=/usr/share/gdm/guest-session/Xsession
[   10.397129] type=1505 audit(1257526721.920:13): operation="profile_replace" pid=782 name=/sbin/dhclient3
[   10.398010] type=1505 audit(1257526721.920:14): operation="profile_replace" pid=782 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.398493] type=1505 audit(1257526721.920:15): operation="profile_replace" pid=782 name=/usr/lib/connman/scripts/dhclient-script
[   10.402854] type=1505 audit(1257526721.924:16): operation="profile_replace" pid=783 name=/usr/bin/evince
[   10.416754] type=1505 audit(1257526721.940:17): operation="profile_replace" pid=783 name=/usr/bin/evince-previewer
[   10.424859] type=1505 audit(1257526721.948:18): operation="profile_replace" pid=783 name=/usr/bin/evince-thumbnailer
[   10.436645] type=1505 audit(1257526721.960:19): operation="profile_replace" pid=789 name=/usr/lib/cups/backend/cups-pdf
[   10.437691] type=1505 audit(1257526721.960:20): operation="profile_replace" pid=789 name=/usr/sbin/cupsd
[   10.441174] type=1505 audit(1257526721.964:21): operation="profile_replace" pid=790 name=/usr/sbin/tcpdump
[   12.409086] cfg80211: Calling CRDA to update world regulatory domain
[   13.287220] tifm_7xx1 0000:08:06.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.289521] yenta_cardbus 0000:08:06.0: CardBus bridge found [1179:ff10]
[   13.289545] yenta_cardbus 0000:08:06.0: Enabling burst memory read transactions
[   13.289553] yenta_cardbus 0000:08:06.0: Using CSCINT to route CSC interrupts to PCI
[   13.289556] yenta_cardbus 0000:08:06.0: Routing CardBus interrupts to PCI
[   13.289563] yenta_cardbus 0000:08:06.0: TI: mfunc 0x01aa1b22, devctl 0x66
[   13.296043] lp: driver loaded but no devices found
[   13.430176] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.434035] Linux video capture interface: v2.00
[   13.520799] yenta_cardbus 0000:08:06.0: ISA IRQ mask 0x0ce8, PCI irq 18
[   13.520805] yenta_cardbus 0000:08:06.0: Socket status: 30000006
[   13.520809] pci_bus 0000:08: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[   13.520819] yenta_cardbus 0000:08:06.0: pcmcia: parent PCI bridge I/O window: 0x7000 - 0x7fff
[   13.520822] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: clean.
[   13.521120] yenta_cardbus 0000:08:06.0: pcmcia: parent PCI bridge Memory window: 0xf5200000 - 0xf52fffff
[   13.521123] yenta_cardbus 0000:08:06.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   13.667245] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   13.670729] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input6
[   13.670783] usbcore: registered new interface driver uvcvideo
[   13.670787] USB Video Class driver (v0.1.0)
[   13.746172] sdhci: Secure Digital Host Controller Interface driver
[   13.746175] sdhci: Copyright(c) Pierre Ossman
[   13.747701] sdhci-pci 0000:08:06.3: SDHCI controller found [104c:803c] (rev 0)
[   13.747721] sdhci-pci 0000:08:06.3: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.747792] Registered led device: mmc0::
[   13.747832] mmc0: SDHCI controller on PCI [0000:08:06.3] using DMA
[   14.083626] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04713/0x204000
[   14.083634] synaptics: Toshiba Satellite A205 detected, limiting rate to 40pps.
[   14.118750] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   14.537129] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   14.539304] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x427 0x4d0-0x4d7
[   14.540191] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   14.540944] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   14.541922] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.314963]   alloc irq_desc for 22 on node -1
[   15.314967]   alloc kstat_irqs on node -1
[   15.314976] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.315014] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.417418] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   15.417498] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   15.993804] cfg80211: World regulatory domain updated:
[   15.993808] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.993811] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.993815] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.993818] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.993821] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.993824] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.222974] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   16.222978] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   16.223096] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.223132] iwlagn 0000:03:00.0: setting latency timer to 64
[   16.223213] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   16.266002] iwlagn 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   16.266069]   alloc irq_desc for 32 on node -1
[   16.266072]   alloc kstat_irqs on node -1
[   16.266094] iwlagn 0000:03:00.0: irq 32 for MSI/MSI-X
[   16.276443] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   23.999025] sky2 eth0: enabling interface
[   23.999279] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.038450] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   24.118685] iwlagn 0000:03:00.0: loaded firmware version 228.61.2.24
[   24.336387] Registered led device: iwl-phy0::radio
[   24.336411] Registered led device: iwl-phy0::assoc
[   24.336433] Registered led device: iwl-phy0::RX
[   24.336454] Registered led device: iwl-phy0::TX
[   24.463793] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.888011] [drm] TV-14: set mode NTSC 480i 0
[   27.029442] [drm] TV-14: set mode NTSC 480i 0
[   27.451155] [drm] TV-14: set mode NTSC 480i 0
[   27.594861] [drm] TV-14: set mode NTSC 480i 0
[   28.908961] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   28.908965] vboxdrv: Successfully done.
[   28.908967] vboxdrv: Found 2 processor cores.
[   28.909066] vboxdrv: fAsync=0 offMin=0x1b8 offMax=0x6e0
[   28.909113] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   28.909117] vboxdrv: Successfully loaded version 3.0.10 (interface 0x000e0001).
[   31.823259] [drm] TV-14: set mode NTSC 480i 0
[   31.963302] [drm] TV-14: set mode NTSC 480i 0
[   32.225249] [drm] TV-14: set mode NTSC 480i 0
[   32.366123] [drm] TV-14: set mode NTSC 480i 0
[   32.679572] [drm] TV-14: set mode NTSC 480i 0
[   32.821873] [drm] TV-14: set mode NTSC 480i 0
[   33.177459] ppdev: user-space parallel port driver
[   45.506633] [drm] TV-14: set mode NTSC 480i 0
[   45.648573] [drm] TV-14: set mode NTSC 480i 0
[   45.935154] [drm] TV-14: set mode NTSC 480i 0
[   46.075253] [drm] TV-14: set mode NTSC 480i 0
[   46.349304] [drm] TV-14: set mode NTSC 480i 0
[   46.489963] [drm] TV-14: set mode NTSC 480i 0
[   68.045192] [drm] TV-14: set mode NTSC 480i 0
[   68.186614] [drm] TV-14: set mode NTSC 480i 0
[   70.272730] wlan0: authenticate with AP 00:16:e3:9b:9e:85
[   70.288503] wlan0: authenticated
[   70.288509] wlan0: associate with AP 00:16:e3:9b:9e:85
[   70.311898] wlan0: RX AssocResp from 00:16:e3:9b:9e:85 (capab=0x411 status=0 aid=15)
[   70.311903] wlan0: associated
[   70.332226] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   81.152036] wlan0: no IPv6 routers present
[  114.762615] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  115.048181] Registered led device: iwl-phy0::radio
[  115.048209] Registered led device: iwl-phy0::assoc
[  115.048231] Registered led device: iwl-phy0::RX
[  115.048251] Registered led device: iwl-phy0::TX
[  361.278120] wlan0: disassociating by local choice (reason=3)
[  363.292306] wlan0: authenticate with AP 00:16:e3:9b:9e:85
[  363.294370] wlan0: authenticated
[  363.294374] wlan0: associate with AP 00:16:e3:9b:9e:85
[  363.318904] wlan0: RX AssocResp from 00:16:e3:9b:9e:85 (capab=0x411 status=0 aid=3)
[  363.318909] wlan0: associated
[  706.921690] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  706.921695] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  706.921698] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[  964.233972] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  964.464943] Registered led device: iwl-phy0::radio
[  964.464967] Registered led device: iwl-phy0::assoc
[  964.464987] Registered led device: iwl-phy0::RX
[  964.465592] Registered led device: iwl-phy0::TX
[ 1133.998034] wlan0: disassociating by local choice (reason=3)
[ 1146.019784] wlan0: authenticate with AP 00:16:e3:9b:9e:85
[ 1146.022432] wlan0: authenticated
[ 1146.022436] wlan0: associate with AP 00:16:e3:9b:9e:85
[ 1146.046937] wlan0: RX AssocResp from 00:16:e3:9b:9e:85 (capab=0x411 status=0 aid=4)
[ 1146.046942] wlan0: associated
[ 1610.449262] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 1610.710852] Registered led device: iwl-phy0::radio
[ 1610.710876] Registered led device: iwl-phy0::assoc
[ 1610.710897] Registered led device: iwl-phy0::RX
[ 1610.710917] Registered led device: iwl-phy0::TX
eric@eric-laptop:~$ 

```

Network Scan Results:
```
eric@eric-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:16:E3:9B:9E:85
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Two Penguins and an Apple"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017db4cad97
                    Extra: Last beacon: 1404ms ago
                    IE: Unknown: 001954776F2050656E6775696E7320616E6420616E204170706C65
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD15000AF50A0262C000030103050E04FF000300110101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010F0003A4000027A4000042435E0062322F00

vboxnet0  Interface doesn't support scanning.

```

Kernel:
```
2.6.31-14-generic i686

```

That should be anything anyone needs. If I missed something let me know and I&#699;ll get it up as soon as possible. 

Thanks to everyone in advance.

---

### Post by t0mppa on 2009-11-06
> **11010110 said:**
> ```

[  114.762615] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  115.048181] Registered led device: iwl-phy0::radio
[  115.048209] Registered led device: iwl-phy0::assoc
[  115.048231] Registered led device: iwl-phy0::RX
[  115.048251] Registered led device: iwl-phy0::TX
[  361.278120] wlan0: disassociating by local choice (reason=3)
[  363.292306] wlan0: authenticate with AP 00:16:e3:9b:9e:85
[  363.294370] wlan0: authenticated
[  363.294374] wlan0: associate with AP 00:16:e3:9b:9e:85
[  363.318904] wlan0: RX AssocResp from 00:16:e3:9b:9e:85 (capab=0x411 status=0 aid=3)
[  363.318909] wlan0: associated
[  706.921690] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  706.921695] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  706.921698] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[  964.233972] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  964.464943] Registered led device: iwl-phy0::radio
[  964.464967] Registered led device: iwl-phy0::assoc
[  964.464987] Registered led device: iwl-phy0::RX
[  964.465592] Registered led device: iwl-phy0::TX
[ 1133.998034] wlan0: disassociating by local choice (reason=3)
[ 1146.019784] wlan0: authenticate with AP 00:16:e3:9b:9e:85
[ 1146.022432] wlan0: authenticated
[ 1146.022436] wlan0: associate with AP 00:16:e3:9b:9e:85
[ 1146.046937] wlan0: RX AssocResp from 00:16:e3:9b:9e:85 (capab=0x411 status=0 aid=4)
[ 1146.046942] wlan0: associated
[ 1610.449262] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 1610.710852] Registered led device: iwl-phy0::radio
[ 1610.710876] Registered led device: iwl-phy0::assoc
[ 1610.710897] Registered led device: iwl-phy0::RX
[ 1610.710917] Registered led device: iwl-phy0::TX
eric@eric-laptop:~$ 

```

This is a pretty common bug that apparently derives from the driver and firmware versions and is affecting all Linux distributions across the board. You can find the Ubuntu bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/200509?comments=all"), which has numerous fixes suggested that have helped some people, so you might just get lucky trying them out.

---

