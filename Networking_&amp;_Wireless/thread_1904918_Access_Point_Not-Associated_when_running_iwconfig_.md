---
title: "Access Point: Not-Associated when running iwconfig in Ubuntu 11.10"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by KrisDeniseRiley1 on 2012-01-05
I have a dell m1330 xps with ubuntu 11.10. I had a lot of issues with  wireless drivers and the such. I now have wireless connection, but when I  run the above command it outputs this:

```
lo        no wireless extensions.  eth0      no wireless extensions.  eth1      IEEE 802.11  Access Point: Not-Associated              Link Quality:5  Signal level:204  Noise level:199           Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```

```
M1330:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)

```

```
M1330:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
```

```
M1330:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:e5:fe:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:69:ab:0d:41  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:69ff:feab:d41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145871 errors:0 dropped:0 overruns:0 frame:3062
          TX packets:104261 errors:21 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:155249640 (155.2 MB)  TX bytes:10679114 (10.6 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11007 (11.0 KB)  TX bytes:11007 (11.0 KB)

```

```
M1330:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
michael_mic            12540  4 
arc4                   12473  2 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
dell_wmi               12601  0 
nvidia              10782577  44 
sparse_keymap          13658  1 dell_wmi
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
dell_laptop            13519  0 
videodev               85626  1 uvcvideo
snd_seq_midi           13132  0 
dcdbas                 14098  1 dell_laptop
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                63474  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
serio_raw              12990  0 
r592                   17808  0 
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
lib80211_crypt_tkip    17275  0 
mtd                    35662  2 sm_common,nand
memstick               15857  1 r592
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2646601  0 
wmi                    18744  1 dell_wmi
video                  18908  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
mmc_block              22393  2 
firewire_ohci          35846  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   132972  0 

```

```
M1330:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic-pae (buildd@palmer) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 (Ubuntu 3.0.0-14.23-generic-pae 3.0.9)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfe6d800 (usable)
[    0.000000]  BIOS-e820: 00000000dfe6d800 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100002000 - 0000000120000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Dell Inc. XPS M1330                       /0U8042, BIOS A15 12/26/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 100000000 mask FE0000000 write-back
[    0.000000]   4 base 0DFF00000 mask FFFF00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 512MB, type WB
[    0.000000] reg 4, base: 3583MB, range: 1MB, type UC
[    0.000000] total RAM covered: 4095M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3583MB, range: 1MB, type UC
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 4GB, range: 512MB, type WB
[    0.000000] e820 update range: 00000000dff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 365e6000 - 372eb000
[    0.000000] ACPI: RSDP 000fbc00 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT dfe6f200 0005C (v01 DELL    M08     27D80C1A ASL  00000061)
[    0.000000] ACPI: FACP dfe6f09c 000F4 (v04 DELL    M08     27D80C1A ASL  00000061)
[    0.000000] ACPI: DSDT dfe6f800 05733 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS dfe7e000 00040
[    0.000000] ACPI: HPET dfe6f300 00038 (v01 DELL    M08     00000001 ASL  00000061)
[    0.000000] ACPI: APIC dfe6f400 00068 (v01 DELL    M08     27D80C1A ASL  00000047)
[    0.000000] ACPI: MCFG dfe6f3c0 0003E (v16 DELL    M08     27D80C1A ASL  00000061)
[    0.000000] ACPI: SLIC dfe6f49c 00176 (v01 DELL    M08     27D80C1A ASL  00000061)
[    0.000000] ACPI: BOOT dfe6efc0 00028 (v01 DELL    M08     27D80C1A ASL  00000061)
[    0.000000] ACPI: SSDT dfe6d9bc 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 3716MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000dfe6d
[    0.000000]     0: 0x00100002 -> 0x00120000
[    0.000000] On node 0 totalpages: 1048058
[    0.000000] free_area_init_node: node 0, pgdat c17ee1c0, node_mem_map f41e6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 7433 pages used for memmap
[    0.000000]   HighMem zone: 812388 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:18000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u1048576
[    0.000000] pcpu-alloc: s29952 r0 d23296 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1038841
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic-pae root=UUID=42be878e-e34c-419d-a73a-b5cfa0b62aa0 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 18874112 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00120000)
[    0.000000] Memory: 4112776k/4718592k available (5499k kernel code, 79456k reserved, 2665k data, 720k init, 3279284k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17fa000 - 0xc18ae000   ( 720 kB)
[    0.000000]       .data : 0xc155efb0 - 0xc17f94c0   (2665 kB)
[    0.000000]       .text : 0xc1000000 - 0xc155efb0   (5499 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2093.764 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4187.52 BogoMIPS (lpj=8375056)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004029] Security Framework initialized
[    0.004046] AppArmor: AppArmor initialized
[    0.004048] Yama: becoming mindful.
[    0.004104] Mount-cache hash table entries: 512
[    0.004244] Initializing cgroup subsys cpuacct
[    0.004250] Initializing cgroup subsys memory
[    0.004258] Initializing cgroup subsys devices
[    0.004260] Initializing cgroup subsys freezer
[    0.004263] Initializing cgroup subsys net_cls
[    0.004265] Initializing cgroup subsys blkio
[    0.004272] Initializing cgroup subsys perf_event
[    0.004304] CPU: Physical Processor ID: 0
[    0.004306] CPU: Processor Core ID: 0
[    0.004309] mce: CPU supports 6 MCE banks
[    0.004318] CPU0: Thermal monitoring enabled (TM2)
[    0.004323] using mwait in idle threads.
[    0.008345] ACPI: Core revision 20110413
[    0.012014] ftrace: allocating 25575 entries in 51 pages
[    0.016052] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016432] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.056814] CPU0: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz stepping 06
[    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.060003] ... version:                2
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      2
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             000000007fffffff
[    0.060003] ... fixed-purpose events:   3
[    0.060003] ... event mask:             0000000700000003
[    0.060003] CPU 1 irqstacks, hard=f74ca000 soft=f74cc000
[    0.060003] Booting Node   0, Processors  #1 Ok.
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.148022] Brought up 2 CPUs
[    0.148025] Total of 2 processors activated (8375.80 BogoMIPS).
[    0.149354] devtmpfs: initialized
[    0.150046] print_constraints: dummy: 
[    0.150080] Time: 11:10:19  Date: 01/05/12
[    0.150124] NET: Registered protocol family 16
[    0.150154] Trying to unpack rootfs image as initramfs...
[    0.150260] EISA bus registered
[    0.152018] ACPI: bus type pci registered
[    0.152082] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.152086] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.152088] PCI: Using MMCONFIG for extended config space
[    0.152090] PCI: Using configuration type 1 for base access
[    0.152097] dmi type 0xB1 record - unknown flag
[    0.153190] bio: create slab <bio-0> at 0
[    0.154575] ACPI: EC: Look up EC in DSDT
[    0.164558] ACPI: SSDT dfe7e080 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.164860] ACPI: Dynamic OEM Table Load:
[    0.164863] ACPI: SSDT   (null) 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.165145] ACPI: SSDT dfe6e4f2 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.165463] ACPI: Dynamic OEM Table Load:
[    0.165467] ACPI: SSDT   (null) 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.165606] ACPI: SSDT dfe6de88 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.165906] ACPI: Dynamic OEM Table Load:
[    0.165909] ACPI: SSDT   (null) 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.166151] ACPI: SSDT dfe6e778 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.166461] ACPI: Dynamic OEM Table Load:
[    0.166464] ACPI: SSDT   (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.166563] ACPI: SSDT dfe6e46d 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.166864] ACPI: Dynamic OEM Table Load:
[    0.166867] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.167068] ACPI: Interpreter enabled
[    0.167074] ACPI: (supports S0 S3 S4 S5)
[    0.167094] ACPI: Using IOAPIC for interrupt routing
[    0.201451] ACPI: No dock devices found.
[    0.201455] HEST: Table not found.
[    0.201460] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.210657] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.229024] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.229027] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.229030] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.229033] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.229035] pci_root PNP0A03:00: host bridge window [mem 0xe0000000-0xf7ffffff]
[    0.229038] pci_root PNP0A03:00: host bridge window [mem 0xfc000000-0xfebfffff]
[    0.229040] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfecfffff]
[    0.229043] pci_root PNP0A03:00: host bridge window [mem 0xfed1c000-0xfed1ffff]
[    0.229045] pci_root PNP0A03:00: host bridge window [mem 0xfed90000-0xfed9ffff]
[    0.229048] pci_root PNP0A03:00: host bridge window [mem 0xfeda7000-0xfedfffff]
[    0.229051] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xff9fffff]
[    0.229053] pci_root PNP0A03:00: host bridge window [mem 0xffc00000-0xffdfffff]
[    0.229056] pci_root PNP0A03:00: host bridge window [mem 0x120000000-0x317ffffff]
[    0.229077] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
[    0.229127] pci 0000:00:01.0: [8086:2a01] type 1 class 0x000604
[    0.229165] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.229169] pci 0000:00:01.0: PME# disabled
[    0.229228] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
[    0.229288] pci 0000:00:1a.0: reg 20: [io  0x6f20-0x6f3f]
[    0.229330] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
[    0.229390] pci 0000:00:1a.1: reg 20: [io  0x6f00-0x6f1f]
[    0.229449] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
[    0.229475] pci 0000:00:1a.7: reg 10: [mem 0xfed1c400-0xfed1c7ff]
[    0.229570] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.229576] pci 0000:00:1a.7: PME# disabled
[    0.229607] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
[    0.229631] pci 0000:00:1b.0: reg 10: [mem 0xf6ffc000-0xf6ffffff 64bit]
[    0.229719] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.229724] pci 0000:00:1b.0: PME# disabled
[    0.229755] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
[    0.229848] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.229853] pci 0000:00:1c.0: PME# disabled
[    0.229886] pci 0000:00:1c.1: [8086:2841] type 1 class 0x000604
[    0.229977] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.229983] pci 0000:00:1c.1: PME# disabled
[    0.230017] pci 0000:00:1c.3: [8086:2845] type 1 class 0x000604
[    0.230111] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.230116] pci 0000:00:1c.3: PME# disabled
[    0.230151] pci 0000:00:1c.5: [8086:2849] type 1 class 0x000604
[    0.230242] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.230247] pci 0000:00:1c.5: PME# disabled
[    0.230281] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
[    0.230341] pci 0000:00:1d.0: reg 20: [io  0x6f80-0x6f9f]
[    0.230383] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
[    0.230444] pci 0000:00:1d.1: reg 20: [io  0x6f60-0x6f7f]
[    0.230486] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
[    0.230546] pci 0000:00:1d.2: reg 20: [io  0x6f40-0x6f5f]
[    0.230602] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
[    0.230627] pci 0000:00:1d.7: reg 10: [mem 0xfed1c000-0xfed1c3ff]
[    0.230722] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.230729] pci 0000:00:1d.7: PME# disabled
[    0.230754] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.230845] pci 0000:00:1f.0: [8086:2815] type 0 class 0x000601
[    0.230964] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.230971] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.230976] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.230982] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.231028] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
[    0.231047] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
[    0.231060] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
[    0.231073] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
[    0.231086] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
[    0.231098] pci 0000:00:1f.1: reg 20: [io  0x6fa0-0x6faf]
[    0.231147] pci 0000:00:1f.2: [8086:2828] type 0 class 0x000101
[    0.231169] pci 0000:00:1f.2: reg 10: [io  0x6eb0-0x6eb7]
[    0.231182] pci 0000:00:1f.2: reg 14: [io  0x6eb8-0x6ebb]
[    0.231195] pci 0000:00:1f.2: reg 18: [io  0x6ec0-0x6ec7]
[    0.231207] pci 0000:00:1f.2: reg 1c: [io  0x6ec8-0x6ecb]
[    0.231220] pci 0000:00:1f.2: reg 20: [io  0x6ee0-0x6eef]
[    0.231233] pci 0000:00:1f.2: reg 24: [io  0xeff0-0xefff]
[    0.231270] pci 0000:00:1f.2: PME# supported from D3hot
[    0.231275] pci 0000:00:1f.2: PME# disabled
[    0.231292] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
[    0.231310] pci 0000:00:1f.3: reg 10: [mem 0xf6ffbf00-0xf6ffbfff]
[    0.231354] pci 0000:00:1f.3: reg 20: [io  0x10c0-0x10df]
[    0.231448] pci 0000:01:00.0: [10de:0427] type 0 class 0x000300
[    0.231468] pci 0000:01:00.0: reg 10: [mem 0xf5000000-0xf5ffffff]
[    0.231490] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.231512] pci 0000:01:00.0: reg 1c: [mem 0xf2000000-0xf3ffffff 64bit]
[    0.231527] pci 0000:01:00.0: reg 24: [io  0xdf00-0xdf7f]
[    0.231541] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.231628] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.231632] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.231636] pci 0000:00:01.0:   bridge window [mem 0xf2000000-0xf6efffff]
[    0.231641] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.231705] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.231711] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.231717] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.231726] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.231821] pci 0000:0c:00.0: [14e4:4328] type 0 class 0x000280
[    0.231854] pci 0000:0c:00.0: reg 10: [mem 0xf1ffc000-0xf1ffffff 64bit]
[    0.231881] pci 0000:0c:00.0: reg 18: [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.232078] pci 0000:0c:00.0: supports D1 D2
[    0.232080] pci 0000:0c:00.0: PME# supported from D3hot D3cold
[    0.232086] pci 0000:0c:00.0: PME# disabled
[    0.240035] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.240041] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.240047] pci 0000:00:1c.1:   bridge window [mem 0xf1f00000-0xf1ffffff]
[    0.240056] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.240122] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.240127] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    0.240133] pci 0000:00:1c.3:   bridge window [mem 0xf1c00000-0xf1efffff]
[    0.240142] pci 0000:00:1c.3:   bridge window [mem 0xf0100000-0xf03fffff 64bit pref]
[    0.240282] pci 0000:09:00.0: [14e4:1713] type 0 class 0x000200
[    0.240355] pci 0000:09:00.0: reg 10: [mem 0xf1bf0000-0xf1bfffff 64bit]
[    0.240675] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.240687] pci 0000:09:00.0: PME# disabled
[    0.240834] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    0.240840] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    0.240845] pci 0000:00:1c.5:   bridge window [mem 0xf1b00000-0xf1bfffff]
[    0.240854] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.240905] pci 0000:03:01.0: [1180:0832] type 0 class 0x000c00
[    0.240930] pci 0000:03:01.0: reg 10: [mem 0xf1aff800-0xf1afffff]
[    0.241022] pci 0000:03:01.0: supports D1 D2
[    0.241024] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.241029] pci 0000:03:01.0: PME# disabled
[    0.241052] pci 0000:03:01.1: [1180:0822] type 0 class 0x000805
[    0.241076] pci 0000:03:01.1: reg 10: [mem 0xf1aff500-0xf1aff5ff]
[    0.241171] pci 0000:03:01.1: supports D1 D2
[    0.241173] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.241178] pci 0000:03:01.1: PME# disabled
[    0.241202] pci 0000:03:01.2: [1180:0592] type 0 class 0x000880
[    0.241226] pci 0000:03:01.2: reg 10: [mem 0xf1aff600-0xf1aff6ff]
[    0.241317] pci 0000:03:01.2: supports D1 D2
[    0.241319] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.241324] pci 0000:03:01.2: PME# disabled
[    0.241348] pci 0000:03:01.3: [1180:0852] type 0 class 0x000880
[    0.241371] pci 0000:03:01.3: reg 10: [mem 0xf1aff700-0xf1aff7ff]
[    0.241463] pci 0000:03:01.3: supports D1 D2
[    0.241465] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.241470] pci 0000:03:01.3: PME# disabled
[    0.241546] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.241552] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.241558] pci 0000:00:1e.0:   bridge window [mem 0xf1a00000-0xf1afffff]
[    0.241566] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.241569] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.241572] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.241575] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.241578] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.241581] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xf7ffffff] (subtractive decode)
[    0.241583] pci 0000:00:1e.0:   bridge window [mem 0xfc000000-0xfebfffff] (subtractive decode)
[    0.241586] pci 0000:00:1e.0:   bridge window [mem 0xfec10000-0xfecfffff] (subtractive decode)
[    0.241589] pci 0000:00:1e.0:   bridge window [mem 0xfed1c000-0xfed1ffff] (subtractive decode)
[    0.241592] pci 0000:00:1e.0:   bridge window [mem 0xfed90000-0xfed9ffff] (subtractive decode)
[    0.241594] pci 0000:00:1e.0:   bridge window [mem 0xfeda7000-0xfedfffff] (subtractive decode)
[    0.241597] pci 0000:00:1e.0:   bridge window [mem 0xfee10000-0xff9fffff] (subtractive decode)
[    0.241600] pci 0000:00:1e.0:   bridge window [mem 0xffc00000-0xffdfffff] (subtractive decode)
[    0.241603] pci 0000:00:1e.0:   bridge window [mem 0x120000000-0x317ffffff] (subtractive decode)
[    0.241640] pci_bus 0000:00: on NUMA node 0
[    0.241647] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.241963] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.242080] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.242129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.242187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.242246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.242303] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.242359]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.242362]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.242364] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.253047] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[    0.253124] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.253198] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.253271] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.253346] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.253424] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.253502] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.253567] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.253708] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.253715] vgaarb: loaded
[    0.253716] vgaarb: bridge control possible 0000:01:00.0
[    0.253957] SCSI subsystem initialized
[    0.254023] libata version 3.00 loaded.
[    0.254073] usbcore: registered new interface driver usbfs
[    0.254085] usbcore: registered new interface driver hub
[    0.254117] usbcore: registered new device driver usb
[    0.254216] PCI: Using ACPI for IRQ routing
[    0.256846] PCI: pci_cache_line_size set to 64 bytes
[    0.256987] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.256990] reserve RAM buffer: 00000000dfe6d800 - 00000000dfffffff 
[    0.257103] NetLabel: Initializing
[    0.257105] NetLabel:  domain hash size = 128
[    0.257106] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.257118] NetLabel:  unlabeled traffic allowed by default
[    0.257161] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.257168] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.257173] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.260069] Switching to clocksource hpet
[    0.263478] Switched to NOHz mode on CPU #0
[    0.263604] Switched to NOHz mode on CPU #1
[    0.268040] AppArmor: AppArmor Filesystem Enabled
[    0.268072] pnp: PnP ACPI init
[    0.268094] ACPI: bus type pnp registered
[    0.277327] pnp 00:00: [bus 00-ff]
[    0.277331] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.277333] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.277336] pnp 00:00: [io  0x0d00-0xffff window]
[    0.277338] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.277341] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.277343] pnp 00:00: [mem 0xe0000000-0xf7ffffff window]
[    0.277346] pnp 00:00: [mem 0xfc000000-0xfebfffff window]
[    0.277348] pnp 00:00: [mem 0xfec10000-0xfecfffff window]
[    0.277351] pnp 00:00: [mem 0xfed1c000-0xfed1ffff window]
[    0.277353] pnp 00:00: [mem 0xfed90000-0xfed9ffff window]
[    0.277356] pnp 00:00: [mem 0xfeda7000-0xfedfffff window]
[    0.277358] pnp 00:00: [mem 0xfee10000-0xff9fffff window]
[    0.277361] pnp 00:00: [mem 0xffc00000-0xffdfffff window]
[    0.277363] pnp 00:00: [mem 0x120000000-0x317ffffff window]
[    0.277463] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.277493] pnp 00:01: [irq 12]
[    0.277519] pnp 00:01: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.277537] pnp 00:02: [io  0x0060]
[    0.277539] pnp 00:02: [io  0x0064]
[    0.277541] pnp 00:02: [io  0x0062]
[    0.277543] pnp 00:02: [io  0x0066]
[    0.277549] pnp 00:02: [irq 1]
[    0.277574] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.277591] pnp 00:03: [io  0x0070-0x0071]
[    0.277596] pnp 00:03: [irq 8]
[    0.277598] pnp 00:03: [io  0x0072-0x0077]
[    0.277624] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.277646] pnp 00:04: [io  0x0061]
[    0.277648] pnp 00:04: [io  0x0063]
[    0.277650] pnp 00:04: [io  0x0065]
[    0.277652] pnp 00:04: [io  0x0067]
[    0.277679] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.277695] pnp 00:05: [io  0x0c80-0x0cff]
[    0.277759] system 00:05: [io  0x0c80-0x0cff] could not be reserved
[    0.277763] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.277782] pnp 00:06: [dma 4]
[    0.277785] pnp 00:06: [io  0x0000-0x000f]
[    0.277787] pnp 00:06: [io  0x0080-0x0085]
[    0.277789] pnp 00:06: [io  0x0087-0x008f]
[    0.277791] pnp 00:06: [io  0x00c0-0x00df]
[    0.277793] pnp 00:06: [io  0x0010-0x001f]
[    0.277795] pnp 00:06: [io  0x0090-0x0091]
[    0.277797] pnp 00:06: [io  0x0093-0x009f]
[    0.277825] pnp 00:06: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.277841] pnp 00:07: [io  0x00f0-0x00ff]
[    0.277847] pnp 00:07: [irq 13]
[    0.277875] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.277920] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    0.277973] system 00:08: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.277976] system 00:08: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.278129] pnp 00:09: [io  0x0900-0x097f]
[    0.278131] pnp 00:09: [io  0x0092]
[    0.278133] pnp 00:09: [io  0x00b2-0x00b3]
[    0.278135] pnp 00:09: [io  0x0020-0x0021]
[    0.278137] pnp 00:09: [io  0x00a0-0x00a1]
[    0.278140] pnp 00:09: [irq 0 disabled]
[    0.278142] pnp 00:09: [io  0x04d0-0x04d1]
[    0.278144] pnp 00:09: [io  0x1000-0x1005]
[    0.278146] pnp 00:09: [io  0x1008-0x100f]
[    0.278165] pnp 00:09: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.278169] pnp 00:09: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.278231] system 00:09: [io  0x0900-0x097f] has been reserved
[    0.278237] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.278241] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.278258] pnp 00:0a: [io  0xf400-0xf4fe]
[    0.278260] pnp 00:0a: [io  0x0086]
[    0.278263] pnp 00:0a: [io  0x1006-0x1007]
[    0.278265] pnp 00:0a: [io  0x100a-0x1059]
[    0.278267] pnp 00:0a: [io  0x1060-0x107f]
[    0.278269] pnp 00:0a: [io  0x1080-0x10bf]
[    0.278271] pnp 00:0a: [io  0x10c0-0x10df]
[    0.278273] pnp 00:0a: [io  0x1010-0x102f]
[    0.278275] pnp 00:0a: [io  0x0809]
[    0.278292] pnp 00:0a: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.278296] pnp 00:0a: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.278299] pnp 00:0a: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.278303] pnp 00:0a: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.278368] system 00:0a: [io  0xf400-0xf4fe] has been reserved
[    0.278372] system 00:0a: [io  0x1080-0x10bf] has been reserved
[    0.278375] system 00:0a: [io  0x10c0-0x10df] has been reserved
[    0.278377] system 00:0a: [io  0x0809] has been reserved
[    0.278381] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.289502] pnp 00:0b: [mem 0x00000000-0x0009efff]
[    0.289505] pnp 00:0b: [mem 0x0009f000-0x0009ffff]
[    0.289508] pnp 00:0b: [mem 0x000c0000-0x000cffff]
[    0.289510] pnp 00:0b: [mem 0x000e0000-0x000fffff]
[    0.289512] pnp 00:0b: [mem 0x00100000-0xdfe6d7ff]
[    0.289515] pnp 00:0b: [mem 0xdfe6d800-0xdfefffff]
[    0.289517] pnp 00:0b: [mem 0xdff00000-0xdfffffff]
[    0.289519] pnp 00:0b: [mem 0xdff00000-0xe06fffff]
[    0.289521] pnp 00:0b: [mem 0xffe00000-0xffffffff]
[    0.289523] pnp 00:0b: [mem 0xffa00000-0xffbfffff]
[    0.289526] pnp 00:0b: [mem 0xfec00000-0xfec0ffff]
[    0.289528] pnp 00:0b: [mem 0xfee00000-0xfee0ffff]
[    0.289530] pnp 00:0b: [mem 0xfed20000-0xfed8ffff]
[    0.289532] pnp 00:0b: [mem 0xfeda0000-0xfeda3fff]
[    0.289534] pnp 00:0b: [mem 0xfeda4000-0xfeda4fff]
[    0.289536] pnp 00:0b: [mem 0xfeda5000-0xfeda5fff]
[    0.289539] pnp 00:0b: [mem 0xfeda6000-0xfeda6fff]
[    0.289541] pnp 00:0b: [mem 0xfed18000-0xfed1bfff]
[    0.289543] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    0.289552] pnp 00:0b: disabling [mem 0xdff00000-0xe06fffff] because it overlaps 0000:00:01.0 BAR 15 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.289582] pnp 00:0b: disabling [mem 0xdff00000-0xe06fffff disabled] because it overlaps 0000:01:00.0 BAR 1 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.289669] system 00:0b: [mem 0x00000000-0x0009efff] could not be reserved
[    0.289673] system 00:0b: [mem 0x0009f000-0x0009ffff] could not be reserved
[    0.289676] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.289679] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.289682] system 00:0b: [mem 0x00100000-0xdfe6d7ff] could not be reserved
[    0.289685] system 00:0b: [mem 0xdfe6d800-0xdfefffff] has been reserved
[    0.289688] system 00:0b: [mem 0xdff00000-0xdfffffff] has been reserved
[    0.289691] system 00:0b: [mem 0xffe00000-0xffffffff] has been reserved
[    0.289694] system 00:0b: [mem 0xffa00000-0xffbfffff] has been reserved
[    0.289697] system 00:0b: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.289700] system 00:0b: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.289703] system 00:0b: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.289706] system 00:0b: [mem 0xfeda0000-0xfeda3fff] has been reserved
[    0.289709] system 00:0b: [mem 0xfeda4000-0xfeda4fff] has been reserved
[    0.289712] system 00:0b: [mem 0xfeda5000-0xfeda5fff] has been reserved
[    0.289715] system 00:0b: [mem 0xfeda6000-0xfeda6fff] has been reserved
[    0.289718] system 00:0b: [mem 0xfed18000-0xfed1bfff] has been reserved
[    0.289721] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.289725] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.289788] pnp: PnP ACPI: found 12 devices
[    0.289790] ACPI: ACPI bus type pnp unregistered
[    0.289793] PnPBIOS: Disabled by ACPI PNP
[    0.326070] PCI: max bus depth: 1 pci_try_num: 2
[    0.326152] pci 0000:00:1c.5: BAR 15: assigned [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.326158] pci 0000:00:1c.5: BAR 13: assigned [io  0x2000-0x2fff]
[    0.326162] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.326166] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0600000-0xf07fffff]
[    0.326170] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0800000-0xf09fffff 64bit pref]
[    0.326174] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.326178] pci 0000:01:00.0: BAR 6: assigned [mem 0xf4000000-0xf401ffff pref]
[    0.326182] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.326185] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.326189] pci 0000:00:01.0:   bridge window [mem 0xf2000000-0xf6efffff]
[    0.326193] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.326198] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.326202] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.326209] pci 0000:00:1c.0:   bridge window [mem 0xf0600000-0xf07fffff]
[    0.326214] pci 0000:00:1c.0:   bridge window [mem 0xf0800000-0xf09fffff 64bit pref]
[    0.326223] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.326226] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.326233] pci 0000:00:1c.1:   bridge window [mem 0xf1f00000-0xf1ffffff]
[    0.326239] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.326247] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.326251] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    0.326258] pci 0000:00:1c.3:   bridge window [mem 0xf1c00000-0xf1efffff]
[    0.326263] pci 0000:00:1c.3:   bridge window [mem 0xf0100000-0xf03fffff 64bit pref]
[    0.326272] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    0.326275] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.326282] pci 0000:00:1c.5:   bridge window [mem 0xf1b00000-0xf1bfffff]
[    0.326287] pci 0000:00:1c.5:   bridge window [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.326296] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.326298] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.326305] pci 0000:00:1e.0:   bridge window [mem 0xf1a00000-0xf1afffff]
[    0.326310] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.326341] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.326346] pci 0000:00:01.0: setting latency timer to 64
[    0.326354] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.326359] pci 0000:00:1c.0: setting latency timer to 64
[    0.326371] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.326377] pci 0000:00:1c.1: setting latency timer to 64
[    0.326388] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.326393] pci 0000:00:1c.3: setting latency timer to 64
[    0.326402] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.326407] pci 0000:00:1c.5: setting latency timer to 64
[    0.326416] pci 0000:00:1e.0: setting latency timer to 64
[    0.326421] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.326423] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.326426] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.326428] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.326431] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xf7ffffff]
[    0.326433] pci_bus 0000:00: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.326436] pci_bus 0000:00: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.326438] pci_bus 0000:00: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.326441] pci_bus 0000:00: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.326443] pci_bus 0000:00: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.326446] pci_bus 0000:00: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.326448] pci_bus 0000:00: resource 15 [mem 0xffc00000-0xffdfffff]
[    0.326451] pci_bus 0000:00: resource 16 [mem 0x120000000-0x317ffffff]
[    0.326454] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.326456] pci_bus 0000:01: resource 1 [mem 0xf2000000-0xf6efffff]
[    0.326459] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.326462] pci_bus 0000:0b: resource 0 [io  0x4000-0x4fff]
[    0.326464] pci_bus 0000:0b: resource 1 [mem 0xf0600000-0xf07fffff]
[    0.326467] pci_bus 0000:0b: resource 2 [mem 0xf0800000-0xf09fffff 64bit pref]
[    0.326470] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.326472] pci_bus 0000:0c: resource 1 [mem 0xf1f00000-0xf1ffffff]
[    0.326475] pci_bus 0000:0c: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.326478] pci_bus 0000:0d: resource 0 [io  0xc000-0xcfff]
[    0.326480] pci_bus 0000:0d: resource 1 [mem 0xf1c00000-0xf1efffff]
[    0.326483] pci_bus 0000:0d: resource 2 [mem 0xf0100000-0xf03fffff 64bit pref]
[    0.326485] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    0.326488] pci_bus 0000:09: resource 1 [mem 0xf1b00000-0xf1bfffff]
[    0.326490] pci_bus 0000:09: resource 2 [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.326493] pci_bus 0000:03: resource 1 [mem 0xf1a00000-0xf1afffff]
[    0.326496] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.326498] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.326501] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.326503] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.326506] pci_bus 0000:03: resource 8 [mem 0xe0000000-0xf7ffffff]
[    0.326508] pci_bus 0000:03: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.326511] pci_bus 0000:03: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.326513] pci_bus 0000:03: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.326516] pci_bus 0000:03: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.326518] pci_bus 0000:03: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.326521] pci_bus 0000:03: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.326523] pci_bus 0000:03: resource 15 [mem 0xffc00000-0xffdfffff]
[    0.326526] pci_bus 0000:03: resource 16 [mem 0x120000000-0x317ffffff]
[    0.326578] NET: Registered protocol family 2
[    0.326653] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.326915] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.327355] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.327572] TCP: Hash tables configured (established 131072 bind 65536)
[    0.327575] TCP reno registered
[    0.327578] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.327587] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.327668] NET: Registered protocol family 1
[    0.327873] pci 0000:01:00.0: Boot video device
[    0.327899] PCI: CLS 64 bytes, default 64
[    0.327907] Simple Boot Flag at 0x79 set to 0x1
[    0.328273] audit: initializing netlink socket (disabled)
[    0.328282] type=2000 audit(1325761819.324:1): initialized
[    0.358280] highmem bounce pool size: 64 pages
[    0.358286] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.374217] VFS: Disk quotas dquot_6.5.2
[    0.374294] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.375047] fuse init (API version 7.16)
[    0.375148] msgmni has been set to 1627
[    0.375493] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.375522] io scheduler noop registered
[    0.375524] io scheduler deadline registered
[    0.375540] io scheduler cfq registered (default)
[    0.375675] pcieport 0000:00:01.0: setting latency timer to 64
[    0.375711] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.375764] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.375822] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.375904] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.375961] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.376059] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.376117] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.376200] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.376258] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    0.376363] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.376391] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.376453] intel_idle: MWAIT substates: 0x3122220
[    0.376455] intel_idle: does not run on family 6 model 23
[    0.376524] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.376572] ACPI: AC Adapter [AC] (on-line)
[    0.376647] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.377169] ACPI: Lid Switch [LID]
[    0.377214] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.377218] ACPI: Power Button [PBTN]
[    0.377260] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.377264] ACPI: Sleep Button [SBTN]
[    0.377293] ACPI: acpi_idle registered with cpuidle
[    0.377462] Monitor-Mwait will be used to enter C-1 state
[    0.377491] Monitor-Mwait will be used to enter C-2 state
[    0.377518] Monitor-Mwait will be used to enter C-3 state
[    0.377523] Marking TSC unstable due to TSC halts in idle
[    0.397560] thermal LNXTHERM:00: registered as thermal_zone0
[    0.397564] ACPI: Thermal Zone [THM] (54 C)
[    0.397595] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.397639] ERST: Table is not found!
[    0.397739] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.408106] isapnp: Scanning for PnP cards...
[    0.535923] Freeing initrd memory: 13332k freed
[    0.576800] ACPI: Battery Slot [BAT0] (battery present)
[    0.787038] isapnp: No Plug & Play device found
[    0.793545] Linux agpgart interface v0.103
[    0.795098] brd: module loaded
[    0.795740] loop: module loaded
[    0.795931] ata_piix 0000:00:1f.1: version 2.13
[    0.795945] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.795991] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.796356] scsi0 : ata_piix
[    0.796451] scsi1 : ata_piix
[    0.796792] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.796795] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.796815] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.796822] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.796842] ata2: port disabled. ignoring.
[    0.952039] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.952542] scsi2 : ata_piix
[    0.952618] scsi3 : ata_piix
[    0.952946] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[    0.952953] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[    0.953340] Fixed MDIO Bus: probed
[    0.953366] PPP generic driver version 2.4.2
[    0.953406] tun: Universal TUN/TAP device driver, 1.6
[    0.953408] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.953504] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.953528] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.953542] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.953546] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.953584] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.953620] ehci_hcd 0000:00:1a.7: debug port 1
[    0.957521] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.957537] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.960527] ata1.00: ATAPI: HL-DT-ST DVD+/-RW GSA-S10N, A101, max UDMA/33
[    0.972020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.972145] hub 1-0:1.0: USB hub found
[    0.972150] hub 1-0:1.0: 4 ports detected
[    0.972234] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.972246] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.972249] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.972285] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.972315] ehci_hcd 0000:00:1d.7: debug port 1
[    0.976196] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.976457] ata1.00: configured for UDMA/33
[    0.976460] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.982762] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-S10N A101 PQ: 0 ANSI: 5
[    0.986603] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    0.986606] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.986700] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.986760] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.992019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.992133] hub 2-0:1.0: USB hub found
[    0.992137] hub 2-0:1.0: 6 ports detected
[    0.992221] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.992236] uhci_hcd: USB Universal Host Controller Interface driver
[    0.992261] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.992269] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.992272] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.992314] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.992344] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.992473] hub 3-0:1.0: USB hub found
[    0.992477] hub 3-0:1.0: 2 ports detected
[    0.992556] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.992563] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.992567] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.992602] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.992642] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.992770] hub 4-0:1.0: USB hub found
[    0.992774] hub 4-0:1.0: 2 ports detected
[    0.992849] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.992856] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.992860] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.992895] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.992923] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.993049] hub 5-0:1.0: USB hub found
[    0.993053] hub 5-0:1.0: 2 ports detected
[    0.993124] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.993131] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.993135] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.993170] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.993200] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.993326] hub 6-0:1.0: USB hub found
[    0.993330] hub 6-0:1.0: 2 ports detected
[    0.993404] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.993411] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.993415] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.993457] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.993485] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.993619] hub 7-0:1.0: USB hub found
[    0.993623] hub 7-0:1.0: 2 ports detected
[    0.993751] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.996783] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.996789] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.996907] mousedev: PS/2 mouse device common for all mice
[    0.997065] rtc_cmos 00:03: RTC can wake from S4
[    0.997180] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.997213] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.997300] device-mapper: uevent: version 1.0.3
[    0.997378] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.997412] EISA: Probing bus 0 at eisa.0
[    0.997415] EISA: Cannot allocate resource for mainboard
[    0.997417] Cannot allocate resource for EISA slot 1
[    0.997419] Cannot allocate resource for EISA slot 2
[    0.997421] Cannot allocate resource for EISA slot 3
[    0.997423] Cannot allocate resource for EISA slot 4
[    0.997425] Cannot allocate resource for EISA slot 5
[    0.997427] Cannot allocate resource for EISA slot 6
[    0.997428] Cannot allocate resource for EISA slot 7
[    0.997430] Cannot allocate resource for EISA slot 8
[    0.997432] EISA: Detected 0 cards.
[    0.997453] cpufreq-nforce2: No nForce2 chipset.
[    0.997520] cpuidle: using governor ladder
[    0.997622] cpuidle: using governor menu
[    0.997625] EFI Variables Facility v0.08 2004-May-17
[    0.997941] TCP cubic registered
[    0.998093] NET: Registered protocol family 10
[    0.998763] NET: Registered protocol family 17
[    0.998778] Registering the dns_resolver key type
[    0.998795] Using IPI No-Shortcut mode
[    0.998873] PM: Hibernation image not present or could not be loaded.
[    0.998885] registered taskstats version 1
[    1.006816] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.013893]   Magic number: 12:125:175
[    1.013898] misc network_throughput: hash matches
[    1.013944] acpi device:38: hash matches
[    1.013954] acpi device:0b: hash matches
[    1.014003] rtc_cmos 00:03: setting system clock to 2012-01-05 11:10:20 UTC (1325761820)
[    1.014895] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.014897] EDD information not available.
[    1.416102] usb 2-6: new high speed USB device number 3 using ehci_hcd
[    1.756180] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.756206] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.764516] ata3.00: ATA-8: Hitachi HTS723232A7A364, EC2OA60W, max UDMA/133
[    1.764522] ata3.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.780512] ata3.00: configured for UDMA/133
[    1.780746] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS72323 EC2O PQ: 0 ANSI: 5
[    1.780910] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.780915] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.780970] sd 2:0:0:0: [sda] Write Protect is off
[    1.780974] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.781039] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.792085] usb 7-1: new full speed USB device number 2 using uhci_hcd
[    1.842616]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    1.843234] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.300253] ata4.01: failed to resume link (SControl 0)
[    2.300307] ata4.00: SATA link down (SStatus 0 SControl 300)
[    2.300333] ata4.01: SATA link down (SStatus 0 SControl 0)
[    2.300539] Freeing unused kernel memory: 720k freed
[    2.300852] Write protecting the kernel text: 5500k
[    2.300939] Write protecting the kernel read-only data: 2240k
[    2.300941] NX-protecting the kernel data: 4740k
[    2.318383] udevd[94]: starting version 173
[    2.423708] tg3.c:v3.119 (May 18, 2011)
[    2.423733] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.423749] tg3 0000:09:00.0: setting latency timer to 64
[    2.455385] sdhci: Secure Digital Host Controller Interface driver
[    2.455388] sdhci: Copyright(c) Pierre Ossman
[    2.455635] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    2.455658] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.456707] mmc0: no vmmc regulator found
[    2.457731] Registered led device: mmc0::
[    2.458771] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    2.463501] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.481761] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:21:9b:e5:fe:8b
[    2.481766] tg3 0000:09:00.0: eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0], EEE[0])
[    2.481769] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[0]
[    2.481773] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.524130] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    2.567350] mmc0: new SDHC card at address e624
[    2.569241] mmcblk0: mmc0:e624 SD08G 7.40 GiB 
[    2.573045]  mmcblk0: p1
[    2.896929] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    3.024215] firewire_core: created device fw0: GUID 444fc000036e39e1, S400
[   18.236305] udevd[331]: starting version 173
[   18.284762] lp: driver loaded but no devices found
[   18.315167] lib80211: common routines for IEEE802.11 drivers
[   18.315171] lib80211_crypt: registered algorithm 'NULL'
[   18.336499] Adding 4191228k swap on /dev/sda6.  Priority:-1 extents:1 across:4191228k 
[   18.338455] wmi: Mapper loaded
[   18.354303] wl: module license 'MIXED/Proprietary' taints kernel.
[   18.354308] Disabling lock debugging due to kernel taint
[   18.382471] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.382481] wl 0000:0c:00.0: setting latency timer to 64
[   18.493458] lib80211_crypt: registered algorithm 'TKIP'
[   18.514724] eth1: Broadcom BCM4328 802.11 Hybrid Wireless Controller 5.100.82.38
[   18.518795] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.525401] r592: driver successfully loaded
[   18.542853] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr
[   18.552939] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.562247] r852: driver loaded successfully
[   18.563601] acpi device:31: registered as cooling_device2
[   18.567452] type=1400 audit(1325790638.047:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=605 comm="apparmor_parser"
[   18.567896] type=1400 audit(1325790638.047:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=605 comm="apparmor_parser"
[   18.567972] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input4
[   18.568186] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   18.568193] type=1400 audit(1325790638.051:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=605 comm="apparmor_parser"
[   18.568245] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   18.574134] mmcblk0: retrying using single block read
[   18.578246] mmcblk0: error -110 sending status command
[   18.578249] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.578253] end_request: I/O error, dev mmcblk0, sector 15523712
[   18.582495] mmcblk0: error -110 sending status command
[   18.582499] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.582503] end_request: I/O error, dev mmcblk0, sector 15523713
[   18.586693] mmcblk0: error -110 sending status command
[   18.586697] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.586700] end_request: I/O error, dev mmcblk0, sector 15523714
[   18.590782] mmcblk0: error -110 sending status command
[   18.590787] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.590790] end_request: I/O error, dev mmcblk0, sector 15523715
[   18.594901] mmcblk0: error -110 sending status command
[   18.594904] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.594908] end_request: I/O error, dev mmcblk0, sector 15523716
[   18.598998] mmcblk0: error -110 sending status command
[   18.599001] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.599004] end_request: I/O error, dev mmcblk0, sector 15523717
[   18.603058] mmcblk0: error -110 sending status command
[   18.603062] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.603065] end_request: I/O error, dev mmcblk0, sector 15523718
[   18.606130] mmcblk0: error -110 sending status command
[   18.606134] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.606137] end_request: I/O error, dev mmcblk0, sector 15523719
[   18.606141] Buffer I/O error on device mmcblk0, logical block 1940464
[   18.608224] mmcblk0: retrying using single block read
[   18.612303] mmcblk0: error -110 sending status command
[   18.612307] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.612311] end_request: I/O error, dev mmcblk0, sector 15523712
[   18.616419] mmcblk0: error -110 sending status command
[   18.616423] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.616426] end_request: I/O error, dev mmcblk0, sector 15523713
[   18.620646] mmcblk0: error -110 sending status command
[   18.620650] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.620653] end_request: I/O error, dev mmcblk0, sector 15523714
[   18.622766] mmcblk0: error -110 sending status command
[   18.622768] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.622771] end_request: I/O error, dev mmcblk0, sector 15523715
[   18.626931] mmcblk0: error -110 sending status command
[   18.626935] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.626938] end_request: I/O error, dev mmcblk0, sector 15523716
[   18.631010] mmcblk0: error -110 sending status command
[   18.631014] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x0
[   18.631017] end_request: I/O error, dev mmcblk0, sector 15523717
[   18.638248] Buffer I/O error on device mmcblk0, logical block 1940464
[   18.910913] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.267090] Linux video capture interface: v2.00
[   19.271197] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   19.272930] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   19.274020] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input5
[   19.274158] usbcore: registered new interface driver uvcvideo
[   19.274160] USB Video Class driver (v1.1.0)
[   19.353933] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   19.358287] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.358300] nvidia 0000:01:00.0: setting latency timer to 64
[   19.358306] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.368979] NVRM: loading NVIDIA UNIX x86 Kernel Module  290.10  Wed Nov 16 19:27:25 PST 2011
[   19.379745] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   19.379893] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   19.380056] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.445417] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04751/0xa00000/0x0
[   19.481277] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   19.664227] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   19.664324] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   19.664392] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   20.430389] type=1400 audit(1325790639.911:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=906 comm="apparmor_parser"
[   20.432246] type=1400 audit(1325790639.915:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=905 comm="apparmor_parser"
[   20.433140] type=1400 audit(1325790639.915:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=906 comm="apparmor_parser"
[   20.433422] type=1400 audit(1325790639.915:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=906 comm="apparmor_parser"
[   20.446750] type=1400 audit(1325790639.927:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=907 comm="apparmor_parser"
[   20.617656] vesafb: mode is 1280x800x32, linelength=5120, pages=0
[   20.617659] vesafb: scrolling: redraw
[   20.617662] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.617670] mtrr: type mismatch for f3000000,400000 old: write-back new: write-combining
[   20.617674] mtrr: type mismatch for f3000000,200000 old: write-back new: write-combining
[   20.617677] mtrr: type mismatch for f3000000,100000 old: write-back new: write-combining
[   20.617681] mtrr: type mismatch for f3000000,80000 old: write-back new: write-combining
[   20.617684] mtrr: type mismatch for f3000000,40000 old: write-back new: write-combining
[   20.617687] mtrr: type mismatch for f3000000,20000 old: write-back new: write-combining
[   20.617691] mtrr: type mismatch for f3000000,10000 old: write-back new: write-combining
[   20.617694] mtrr: type mismatch for f3000000,8000 old: write-back new: write-combining
[   20.617698] mtrr: type mismatch for f3000000,4000 old: write-back new: write-combining
[   20.617701] mtrr: type mismatch for f3000000,2000 old: write-back new: write-combining
[   20.617704] mtrr: type mismatch for f3000000,1000 old: write-back new: write-combining
[   20.618231] vesafb: framebuffer at 0xf3000000, mapped to 0xfae80000, using 4032k, total 4032k
[   20.618384] Console: switching to colour frame buffer device 160x50
[   20.618415] fb0: VESA VGA frame buffer device
[   20.661457] ppdev: user-space parallel port driver
[   20.731062] init: failsafe main process (854) killed by TERM signal
[   20.744265] init: apport pre-start process (996) terminated with status 1
[   20.777382] init: apport post-stop process (1040) terminated with status 1
[   20.828881] tg3 0000:09:00.0: irq 46 for MSI/MSI-X
[   20.878192] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.787741] Bluetooth: Core ver 2.16
[   21.787766] NET: Registered protocol family 31
[   21.787768] Bluetooth: HCI device and connection manager initialized
[   21.787770] Bluetooth: HCI socket layer initialized
[   21.787772] Bluetooth: L2CAP socket layer initialized
[   21.788597] Bluetooth: SCO socket layer initialized
[   21.792511] Bluetooth: RFCOMM TTY layer initialized
[   21.792517] Bluetooth: RFCOMM socket layer initialized
[   21.792519] Bluetooth: RFCOMM ver 1.11
[   21.801137] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.801140] Bluetooth: BNEP filters: protocol multicast
[   23.165223] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   27.098272] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   31.520056] eth1: no IPv6 routers present
[   61.440040] eth1: no IPv6 routers present
[ 1394.397530] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=600
[ 1536.425846] CE: hpet increased min_delta_ns to 20113 nsec
[ 6587.099231] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0

```

```
M1330:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```

```
M1330:~$ lsb_release -d
Description:    Ubuntu 11.10

```

```

```


I need to figure a way to get this to show all the right info. Its just  weird to me that I get a signal, but none of the info is being  collected. Also, I have been working on a conky script with version  1.8.1, and I am having a problem with getting the essid and bitrate to  show up which I have a feeling is due to the lack of info I have with  the code I embeded.... please help!!!!:wink:

---

