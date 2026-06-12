---
title: "USB microphone not detected"
date: 2011-06-19
forum: Multimedia Software
---

### Post by GodfreyPeck on 2011-06-19
Greetings,
I'm using Kubuntu 10.04.
I've got a Samson Q1U usb microphone I want to use in Audacity for recording.
Unfortunatly, the microphone isn't registering on my computer.
I can use a usb mouse on the usb port, so I think the port works and the microphone worked on my friends PC, so the mic is fine.
When I plug it in the light on the microphone goes on for about 10 seconds then goes off.

Here's some output:
jeff@jeff-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdfebc000 irq 16

and the following, showing my ports:
jeff@jeff-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The microphone is not showing up on either...
I would really appreciate any suggestions?

I was using the microphone fine a couple years ago with audacity, I think I was on Hardy Heron at the time (not that the upgrade to lucid was necessarily was what did it...) I haven't changed any hardware since then besides adding a little additional ram.

---

### Post by GodfreyPeck on 2011-06-19
on: [https://www.linuxquestions.org/questions/ubuntu-63/lucid-not-detecting-usb-mic-825414/](https://www.linuxquestions.org/questions/ubuntu-63/lucid-not-detecting-usb-mic-825414/)
some asked for output from 
lsmod | grep snd
so, here it is:
jeff@jeff-laptop:~$ sudo lsmod | grep snd
snd_hda_codec_idt      52010  1 
snd_hda_intel          22069  4 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  2 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  2 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54180  18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  2 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm

I'm not sure what this all is, but maybe it will help...

---

### Post by GodfreyPeck on 2011-06-19
Allright, there was one more output requested on there...
I've included it all of it, since I didn't know where the relevant information stopped, my apologies.
Hopefully this will help...

```
jeff@jeff-laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-31-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 (Ubuntu 2.6.32-31.61-generic 2.6.32.32+drm33.14)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f7d3800 (usable)
[    0.000000]  BIOS-e820: 000000005f7d3800 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x5f7d3 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FE0000000 write-back
[    0.000000]   2 base 05F800000 mask FFF800000 uncachable
[    0.000000]   3 base 0FEDA0000 mask FFFFE0000 write-through
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005f7d3800 (usable)
[    0.000000]  modified: 000000005f7d3800 - 0000000060000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37857000 - 37fef2a4
[    0.000000] Allocated new RAMDISK: 008e6000 - 0107e2a4
[    0.000000] Move RAMDISK from 0000000037857000 - 0000000037fef2a3 to 008e6000 - 0107e2a3
[    0.000000] ACPI: RSDP 000fc970 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 5f7d3fd3 0003C (v01 DELL    D05     27D6041B ASL  00000061)
[    0.000000] ACPI: FACP 5f7d4c00 00074 (v01 DELL    D05     27D6041B ASL  00000061)
[    0.000000] ACPI: DSDT 5f7d5800 0324F (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 5f7e4000 00040
[    0.000000] ACPI: APIC 5f7d5400 00068 (v01 DELL    D05     27D6041B ASL  00000047)
[    0.000000] ACPI: MCFG 5f7d53c0 0003E (v16 DELL    D05     27D6041B ASL  00000061)
[    0.000000] ACPI: SSDT 5f7d43e2 002C2 (v01  PmRef  Cpu0Ist 00003000 INTL 20030522)
[    0.000000] ACPI: SSDT 5f7d420a 001D8 (v01  PmRef  Cpu0Cst 00003001 INTL 20030522)
[    0.000000] ACPI: SSDT 5f7d400f 001FB (v01  PmRef    CpuPm 00003000 INTL 20030522)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e1ed8]    TEXT DATA BSS ==> [0000100000 - 00008e1ed8]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008e2000 - 00008e5188]              BRK ==> [00008e2000 - 00008e5188]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e6000 - 000107e2a4]      NEW RAMDISK ==> [00008e6000 - 000107e2a4]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0005f7d3
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005f7d3
[    0.000000] On node 0 totalpages: 391022
[    0.000000] free_area_init_node: node 0, pgdat c079c940, node_mem_map c1080000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1280 pages used for memmap
[    0.000000]   HighMem zone: 162517 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 60000000:80000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2000000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 387966
[    0.000000] Kernel command line: root=UUID=7557fb57-5794-4094-a4c5-2a307db4dda8 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7822460 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0005f7d3)
[    0.000000] Memory: 1526356k/1564492k available (4689k kernel code, 36700k reserved, 2121k data, 664k init, 655188k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a7000 - 0xc084d000   ( 664 kB)
[    0.000000]       .data : 0xc05947c7 - 0xc07a6f08   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05947c7   (4689 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1695.656 MHz processor.
[    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3391.31 BogoMIPS (lpj=6782624)
[    0.008035] Security Framework initialized
[    0.008070] AppArmor: AppArmor initialized
[    0.008082] Mount-cache hash table entries: 512
[    0.008282] Initializing cgroup subsys ns
[    0.008288] Initializing cgroup subsys cpuacct
[    0.008294] Initializing cgroup subsys memory
[    0.008304] Initializing cgroup subsys devices
[    0.008308] Initializing cgroup subsys freezer
[    0.008311] Initializing cgroup subsys net_cls
[    0.008344] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008348] CPU: L2 cache: 2048K
[    0.008354] mce: CPU supports 5 MCE banks
[    0.008368] CPU0: Thermal monitoring enabled (TM1)
[    0.008382] Performance Events: p6 PMU driver.
[    0.008392] ... version:                0
[    0.008395] ... bit width:              32
[    0.008397] ... generic registers:      2
[    0.008399] ... value mask:             00000000ffffffff
[    0.008402] ... max period:             000000007fffffff
[    0.008404] ... fixed-purpose events:   0
[    0.008407] ... event mask:             0000000000000003
[    0.008413] Checking 'hlt' instruction... OK.
[    0.025038] SMP alternatives: switching to UP code
[    0.033841] ACPI: Core revision 20090903
[    0.042361] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.042371] ftrace: allocating 21804 entries in 43 pages
[    0.044093] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044477] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.087010] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 08
[    0.088001] Brought up 1 CPUs
[    0.088001] Total of 1 processors activated (3391.31 BogoMIPS).
[    0.088001] CPU0 attaching NULL sched-domain.
[    0.088001] devtmpfs: initialized
[    0.088001] regulator: core version 0.5
[    0.088001] Time:  0:34:52  Date: 06/20/11
[    0.088001] NET: Registered protocol family 16
[    0.088001] EISA bus registered
[    0.088001] ACPI: bus type pci registered
[    0.088001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.088001] PCI: MCFG area at e0000000 reserved in E820
[    0.088001] PCI: Using MMCONFIG for extended config space
[    0.088001] PCI: Using configuration type 1 for base access
[    0.088001] bio: create slab <bio-0> at 0
[    0.088001] ACPI: EC: Look up EC in DSDT
[    0.105263] ACPI: Interpreter enabled
[    0.105268] ACPI: (supports S0 S3 S4 S5)
[    0.105291] ACPI: Using IOAPIC for interrupt routing
[    0.131884] ACPI: No dock devices found.
[    0.146341] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.146439] pci 0000:00:02.0: reg 10 32bit mmio: [0xdff00000-0xdff7ffff]
[    0.146445] pci 0000:00:02.0: reg 14 io port: [0xeff8-0xefff]
[    0.146451] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.146457] pci 0000:00:02.0: reg 1c 32bit mmio: [0xdfec0000-0xdfefffff]
[    0.146494] pci 0000:00:02.1: reg 10 32bit mmio: [0xdff80000-0xdfffffff]
[    0.146611] pci 0000:00:1b.0: reg 10 64bit mmio: [0xdfebc000-0xdfebffff]
[    0.146675] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.146680] pci 0000:00:1b.0: PME# disabled
[    0.146775] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.146780] pci 0000:00:1c.0: PME# disabled
[    0.146881] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.146886] pci 0000:00:1c.3: PME# disabled
[    0.146955] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.147022] pci 0000:00:1d.1: reg 20 io port: [0xbf60-0xbf7f]
[    0.147088] pci 0000:00:1d.2: reg 20 io port: [0xbf40-0xbf5f]
[    0.147155] pci 0000:00:1d.3: reg 20 io port: [0xbf20-0xbf3f]
[    0.147225] pci 0000:00:1d.7: reg 10 32bit mmio: [0xb0000000-0xb00003ff]
[    0.147289] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.147295] pci 0000:00:1d.7: PME# disabled
[    0.147457] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.147466] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.147471] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.147476] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0900-097f
[    0.147512] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.147521] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.147530] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.147538] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.147547] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
[    0.147703] pci 0000:00:1c.3: bridge io port: [0xd000-0xdfff]
[    0.147709] pci 0000:00:1c.3: bridge 32bit mmio: [0xdfc00000-0xdfdfffff]
[    0.147718] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xd0000000-0xd01fffff]
[    0.147763] pci 0000:02:00.0: reg 10 32bit mmio: [0xdfbfe000-0xdfbfffff]
[    0.147823] pci 0000:02:00.0: supports D1 D2
[    0.147825] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.147831] pci 0000:02:00.0: PME# disabled
[    0.147884] pci 0000:02:03.0: reg 10 32bit mmio: [0xdfbfd000-0xdfbfdfff]
[    0.147956] pci 0000:02:03.0: PME# supported from D0 D3hot D3cold
[    0.147962] pci 0000:02:03.0: PME# disabled
[    0.148031] pci 0000:00:1e.0: transparent bridge
[    0.148040] pci 0000:00:1e.0: bridge 32bit mmio: [0xdfb00000-0xdfbfffff]
[    0.148069] pci_bus 0000:00: on NUMA node 0
[    0.148074] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.148395] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.148515] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.148606] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.157945] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.158085] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.158222] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.158356] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[    0.158473] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.158594] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.158720] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.158850] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.158859] vgaarb: loaded
[    0.159015] SCSI subsystem initialized
[    0.159071] libata version 3.00 loaded.
[    0.159154] usbcore: registered new interface driver usbfs
[    0.159169] usbcore: registered new interface driver hub
[    0.159199] usbcore: registered new device driver usb
[    0.159351] ACPI: WMI: Mapper loaded
[    0.159353] PCI: Using ACPI for IRQ routing
[    0.159516] NetLabel: Initializing
[    0.159519] NetLabel:  domain hash size = 128
[    0.159521] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.159537] NetLabel:  unlabeled traffic allowed by default
[    0.159702] hpet clockevent registered
[    0.159708] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.159716] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.159722] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.164021] Switching to clocksource tsc
[    0.166388] AppArmor: AppArmor Filesystem Enabled
[    0.166403] pnp: PnP ACPI init
[    0.166418] ACPI: bus type pnp registered
[    0.198453] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.198458] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.198533] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.198537] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.198542] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.199446] pnp: PnP ACPI: found 11 devices
[    0.199449] ACPI: ACPI bus type pnp unregistered
[    0.199453] PnPBIOS: Disabled by ACPI PNP
[    0.199468] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.199472] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.199476] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.199480] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.199484] system 00:00: iomem range 0x100000-0x5f7d37ff could not be reserved
[    0.199488] system 00:00: iomem range 0x5f7d3800-0x5f7fffff has been reserved
[    0.199491] system 00:00: iomem range 0x5f800000-0x5fffffff has been reserved
[    0.199495] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.199499] system 00:00: iomem range 0xffb00000-0xffffffff has been reserved
[    0.199503] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.199506] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.199510] system 00:00: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.199514] system 00:00: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.199517] system 00:00: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.199521] system 00:00: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.199525] system 00:00: iomem range 0xf0006000-0xf0006fff has been reserved
[    0.199529] system 00:00: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.199532] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.199540] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.199547] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.199551] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.199555] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.199558] system 00:03: ioport range 0x10e0-0x10ff has been reserved
[    0.199566] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.199569] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.199573] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.199577] system 00:08: ioport range 0x930-0x93f has been reserved
[    0.199580] system 00:08: ioport range 0x940-0x97f has been reserved
[    0.234337] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.234342] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.234350] pci 0000:00:1c.0:   MEM window: 0x60000000-0x601fffff
[    0.234356] pci 0000:00:1c.0:   PREFETCH window: 0x00000060200000-0x000000603fffff
[    0.234366] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0c
[    0.234370] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.234377] pci 0000:00:1c.3:   MEM window: 0xdfc00000-0xdfdfffff
[    0.234383] pci 0000:00:1c.3:   PREFETCH window: 0x000000d0000000-0x000000d01fffff
[    0.234392] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.234395] pci 0000:00:1e.0:   IO window: disabled
[    0.234402] pci 0000:00:1e.0:   MEM window: 0xdfb00000-0xdfbfffff
[    0.234407] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.234428]   alloc irq_desc for 16 on node -1
[    0.234430]   alloc kstat_irqs on node -1
[    0.234437] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.234444] pci 0000:00:1c.0: setting latency timer to 64
[    0.234455]   alloc irq_desc for 19 on node -1
[    0.234457]   alloc kstat_irqs on node -1
[    0.234461] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.234467] pci 0000:00:1c.3: setting latency timer to 64
[    0.234476] pci 0000:00:1e.0: setting latency timer to 64
[    0.234482] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.234485] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.234489] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
[    0.234492] pci_bus 0000:0b: resource 1 mem: [0x60000000-0x601fffff]
[    0.234495] pci_bus 0000:0b: resource 2 pref mem [0x60200000-0x603fffff]
[    0.234499] pci_bus 0000:0c: resource 0 io:  [0xd000-0xdfff]
[    0.234502] pci_bus 0000:0c: resource 1 mem: [0xdfc00000-0xdfdfffff]
[    0.234505] pci_bus 0000:0c: resource 2 pref mem [0xd0000000-0xd01fffff]
[    0.234509] pci_bus 0000:02: resource 1 mem: [0xdfb00000-0xdfbfffff]
[    0.234512] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.234515] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.234552] NET: Registered protocol family 2
[    0.234658] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.235039] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.236208] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.236949] TCP: Hash tables configured (established 131072 bind 65536)
[    0.236953] TCP reno registered
[    0.237116] NET: Registered protocol family 1
[    0.237147] pci 0000:00:02.0: Boot video device
[    0.237477] cpufreq-nforce2: No nForce2 chipset.
[    0.237512] Scanning for low memory corruption every 60 seconds
[    0.237670] audit: initializing netlink socket (disabled)
[    0.237686] type=2000 audit(1308530091.235:1): initialized
[    0.250006] Trying to unpack rootfs image as initramfs...
[    0.264214] highmem bounce pool size: 64 pages
[    0.264222] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.272171] VFS: Disk quotas dquot_6.5.2
[    0.272260] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.273034] fuse init (API version 7.13)
[    0.273131] msgmni has been set to 1703
[    0.273387] alg: No test for stdrng (krng)
[    0.273454] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.273458] io scheduler noop registered
[    0.273462] io scheduler anticipatory registered
[    0.273464] io scheduler deadline registered
[    0.273512] io scheduler cfq registered (default)
[    0.273689]   alloc irq_desc for 24 on node -1
[    0.273692]   alloc kstat_irqs on node -1
[    0.273707] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.273719] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.273878]   alloc irq_desc for 25 on node -1
[    0.273880]   alloc kstat_irqs on node -1
[    0.273890] pcieport 0000:00:1c.3: irq 25 for MSI/MSI-X
[    0.273901] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.274017] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.274110] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.274539] ACPI: AC Adapter [AC] (on-line)
[    0.274657] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.275440] ACPI: Lid Switch [LID]
[    0.275493] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.275500] ACPI: Power Button [PBTN]
[    0.275551] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.275554] ACPI: Sleep Button [SBTN]
[    0.276111] Marking TSC unstable due to TSC halts in idle
[    0.276203] processor LNXCPU:00: registered as cooling_device0
[    0.280173] Switching to clocksource hpet
[    0.285910] thermal LNXTHERM:01: registered as thermal_zone0
[    0.285921] ACPI: Thermal Zone [THM] (60 C)
[    0.292257] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.293787] brd: module loaded
[    0.294341] loop: module loaded
[    0.294435] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.294550] ata_piix 0000:00:1f.1: version 2.13
[    0.294569] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.294620] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.294815] isapnp: Scanning for PnP cards...
[    0.308025] scsi0 : ata_piix
[    0.308140] scsi1 : ata_piix
[    0.380114] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.380119] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.380575] Fixed MDIO Bus: probed
[    0.380618] PPP generic driver version 2.4.2
[    0.380700] tun: Universal TUN/TAP device driver, 1.6
[    0.380703] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.380823] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.380860] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.380882] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.380887] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.380927] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.380968] ehci_hcd 0000:00:1d.7: debug port 1
[    0.384874] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.388818] ata2: port disabled. ignoring.
[    0.388855] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xb0000000
[    0.412413] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.412598] usb usb1: configuration #1 chosen from 1 choice
[    0.412642] hub 1-0:1.0: USB hub found
[    0.412656] hub 1-0:1.0: 8 ports detected
[    0.412750] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.412774] uhci_hcd: USB Universal Host Controller Interface driver
[    0.412846] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.412861] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.412866] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.412916] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.412949] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    0.413067] usb usb2: configuration #1 chosen from 1 choice
[    0.413097] hub 2-0:1.0: USB hub found
[    0.413106] hub 2-0:1.0: 2 ports detected
[    0.413159]   alloc irq_desc for 17 on node -1
[    0.413161]   alloc kstat_irqs on node -1
[    0.413170] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.413180] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.413184] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.413227] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.413267] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    0.413373] usb usb3: configuration #1 chosen from 1 choice
[    0.413401] hub 3-0:1.0: USB hub found
[    0.413409] hub 3-0:1.0: 2 ports detected
[    0.413457]   alloc irq_desc for 18 on node -1
[    0.413459]   alloc kstat_irqs on node -1
[    0.413464] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.413471] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.413475] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.413516] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.413552] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    0.413669] usb usb4: configuration #1 chosen from 1 choice
[    0.413698] hub 4-0:1.0: USB hub found
[    0.413706] hub 4-0:1.0: 2 ports detected
[    0.413754] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.413762] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.413766] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.413800] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.413838] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    0.413941] usb usb5: configuration #1 chosen from 1 choice
[    0.413970] hub 5-0:1.0: USB hub found
[    0.413979] hub 5-0:1.0: 2 ports detected
[    0.414101] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.414350] i8042.c: Warning: Keylock active.
[    0.415562] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.415577] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.420276] mice: PS/2 mouse device common for all mice
[    0.420454] rtc_cmos 00:06: RTC can wake from S4
[    0.420510] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.420563] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.420759] device-mapper: uevent: version 1.0.3
[    0.420937] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.421003] device-mapper: multipath: version 1.1.0 loaded
[    0.421006] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.421677] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.421881] EISA: Probing bus 0 at eisa.0
[    0.421890] Cannot allocate resource for EISA slot 1
[    0.421893] Cannot allocate resource for EISA slot 2
[    0.421918] EISA: Detected 0 cards.
[    0.424284] cpuidle: using governor ladder
[    0.424373] cpuidle: using governor menu
[    0.424853] TCP cubic registered
[    0.425050] NET: Registered protocol family 10
[    0.426280] lo: Disabled Privacy Extensions
[    0.426632] NET: Registered protocol family 17
[    0.596657] ata1.00: ATA-6: WDC WD400VE-75HDT1, 11.07D11, max UDMA/100
[    0.596663] ata1.00: 78140160 sectors, multi 8: LBA 
[    0.596712] ata1.01: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462C, DE06, max UDMA/33
[    0.604872] ata1.00: configured for UDMA/100
[    0.656653] ata1.01: configured for UDMA/33
[    0.657006] Using IPI No-Shortcut mode
[    0.657161] PM: Resume from disk failed.
[    0.657177] registered taskstats version 1
[    0.657481]   Magic number: 15:527:557
[    0.657578] acpi PNP0C01:03: hash matches
[    0.657625] rtc_cmos 00:06: setting system clock to 2011-06-20 00:34:52 UTC (1308530092)
[    0.657629] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.657631] EDD information not available.
[    0.662881] ACPI: Battery Slot [BAT0] (battery present)
[    0.850208] Freeing initrd memory: 7776k freed
[    0.945767] isapnp: No Plug & Play device found
[    0.946008] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400VE-75HD 11.0 PQ: 0 ANSI: 5
[    0.946263] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.947007] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    0.947068] sd 0:0:0:0: [sda] Write Protect is off
[    0.947072] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.947101] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.947219] scsi 0:0:1:0: CD-ROM            TSSTcorp CDRW/DVD TSL462C DE06 PQ: 0 ANSI: 5
[    0.948081]  sda: sda1 sda2 < sda5 >
[    1.016721] sr0: scsi3-mmc drive: 10x/24x writer cd/rw xa/form2 cdda tray
[    1.016725] Uniform CD-ROM driver Revision: 3.20
[    1.016813] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.016873] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.017005] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.017027] Freeing unused kernel memory: 664k freed
[    1.017595] Write protecting the kernel text: 4692k
[    1.017637] Write protecting the kernel read-only data: 1844k
[    1.036071] udev: starting version 151
[    1.152067] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    1.272124] usb 4-1: device descriptor read/64, error -71
[    1.312575] b44 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.372113] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    1.372260] b44.c:v2.0
[    1.392891] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:64:f7:f6
[    1.433191] kjournald starting.  Commit interval 5 seconds
[    1.433205] EXT3-fs: mounted filesystem with ordered data mode.
[    1.496041] usb 4-1: device descriptor read/64, error -71
[    1.712032] usb 4-1: new full speed USB device using uhci_hcd and address 3
[    1.832031] usb 4-1: device descriptor read/64, error -71
[    2.056033] usb 4-1: device descriptor read/64, error -71
[    2.272033] usb 4-1: new full speed USB device using uhci_hcd and address 4
[    2.680027] usb 4-1: device not accepting address 4, error -71
[    2.792029] usb 4-1: new full speed USB device using uhci_hcd and address 5
[    3.200172] usb 4-1: device not accepting address 5, error -71
[    3.200193] hub 4-0:1.0: unable to enumerate USB device on port 1
[   25.221211] Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1 across:1485972k 
[   25.237228] udev: starting version 151
[   25.413067] lp: driver loaded but no devices found
[   25.535573] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input5
[   25.535679] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.535743] ACPI Warning for \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) (20090903/nspredef-433)
[   25.535860] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input6
[   25.535933] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   25.750415] lib80211: common routines for IEEE802.11 drivers
[   25.750420] lib80211_crypt: registered algorithm 'NULL'
[   25.750454] Linux agpgart interface v0.103
[   25.816629] intel_rng: FWH not detected
[   25.858263] EXT3 FS on sda1, internal journal
[   25.916382] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   25.917498] [drm] Initialized drm 1.1.0 20060810
[   25.929968] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   25.929972] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   25.930314] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   25.930967] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   26.362503] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   26.407697] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   26.407702] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   26.407791] ipw2200 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.412046] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   26.412099] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[   26.439013] type=1505 audit(1308530118.278:2):  operation="profile_load" pid=588 name="/sbin/dhclient3"
[   26.439762] type=1505 audit(1308530118.278:3):  operation="profile_load" pid=588 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   26.440612] type=1505 audit(1308530118.282:4):  operation="profile_load" pid=588 name="/usr/lib/connman/scripts/dhclient-script"
[   26.571741] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.571749] i915 0000:00:02.0: setting latency timer to 64
[   26.589415] [drm] set up 7M of stolen space
[   26.692699] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x200000
[   26.759351] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   26.923034] [drm] initialized overlay support
[   27.380088] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   27.538234] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.550224] type=1505 audit(1308530119.390:5):  operation="profile_replace" pid=742 name="/sbin/dhclient3"
[   27.550985] type=1505 audit(1308530119.390:6):  operation="profile_replace" pid=742 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   27.551410] type=1505 audit(1308530119.390:7):  operation="profile_replace" pid=742 name="/usr/lib/connman/scripts/dhclient-script"
[   27.576508] type=1505 audit(1308530119.418:8):  operation="profile_load" pid=743 name="/usr/lib/firefox-3.6.17/firefox-*bin"
[   27.584693] type=1505 audit(1308530119.426:9):  operation="profile_load" pid=743 name="/usr/lib/firefox-3.6.17/firefox-*bin//firefox_java"
[   27.587114] type=1505 audit(1308530119.426:10):  operation="profile_load" pid=743 name="/usr/lib/firefox-3.6.17/firefox-*bin//firefox_openjdk"
[   27.601654] type=1505 audit(1308530119.442:11):  operation="profile_load" pid=747 name="/usr/lib/cups/backend/cups-pdf"
[   27.693271] dell-wmi: No known WMI GUID found
[   27.772763] apm: BIOS not found.
[   28.084041] fb0: inteldrmfb frame buffer device
[   28.084045] registered panic notifier
[   28.084057] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   28.084115] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.084145] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   28.095074] vga16fb: initializing
[   28.095079] vga16fb: mapped to 0xc00a0000
[   28.095085] vga16fb: not registering due to another framebuffer present
[   28.256190] Console: switching to colour frame buffer device 160x50
[   28.276477] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   28.276623] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   29.679815] ppdev: user-space parallel port driver
[   37.580017] eth1: no IPv6 routers present
[   47.184862] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[  105.775949] lib80211_crypt: registered algorithm 'CCMP'
[  105.968220] padlock: VIA PadLock not detected.
[  106.210489] lib80211_crypt: registered algorithm 'TKIP'
[  106.432631] __ratelimit: 9 callbacks suppressed
[  106.432638] qjackctl.bin[1671]: segfault at 0 ip 00370977 sp bfa8dd9c error 4 in libjack.so.0.0.28[36c000+f000]
[  312.820792] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  369.699348] lo: Disabled Privacy Extensions
[ 1863.812349] lo: Disabled Privacy Extensions
[ 2557.392104] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 2557.516074] usb 2-1: device descriptor read/64, error -71
[ 2557.744055] usb 2-1: device descriptor read/64, error -71
[ 2557.960072] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 2558.084066] usb 2-1: device descriptor read/64, error -71
[ 2558.312092] usb 2-1: device descriptor read/64, error -71
[ 2558.528070] usb 2-1: new full speed USB device using uhci_hcd and address 4
[ 2558.944077] usb 2-1: device not accepting address 4, error -71
[ 2559.056080] usb 2-1: new full speed USB device using uhci_hcd and address 5
[ 2559.472069] usb 2-1: device not accepting address 5, error -71
[ 2559.472108] hub 2-0:1.0: unable to enumerate USB device on port 1
[ 2997.852087] usb 4-1: new full speed USB device using uhci_hcd and address 6
[ 2997.976066] usb 4-1: device descriptor read/64, error -71
[ 2998.200071] usb 4-1: device descriptor read/64, error -71
[ 2998.416065] usb 4-1: new full speed USB device using uhci_hcd and address 7
[ 2998.536078] usb 4-1: device descriptor read/64, error -71
[ 2998.760077] usb 4-1: device descriptor read/64, error -71
[ 2998.976055] usb 4-1: new full speed USB device using uhci_hcd and address 8
[ 2999.392070] usb 4-1: device not accepting address 8, error -71
[ 2999.504077] usb 4-1: new full speed USB device using uhci_hcd and address 9
[ 2999.916129] usb 4-1: device not accepting address 9, error -71
[ 2999.916166] hub 4-0:1.0: unable to enumerate USB device on port 1
[ 4225.772060] usb 4-1: new full speed USB device using uhci_hcd and address 10
[ 4225.892097] usb 4-1: device descriptor read/64, error -71
[ 4226.116063] usb 4-1: device descriptor read/64, error -71
[ 4226.332087] usb 4-1: new full speed USB device using uhci_hcd and address 11
[ 4226.512097] usb 4-1: device descriptor read/64, error -71
[ 4226.736044] usb 4-1: device descriptor read/64, error -71
[ 4226.952088] usb 4-1: new full speed USB device using uhci_hcd and address 12
[ 4227.368071] usb 4-1: device not accepting address 12, error -71
[ 4227.480051] usb 4-1: new full speed USB device using uhci_hcd and address 13
[ 4227.888084] usb 4-1: device not accepting address 13, error -71
[ 4227.888111] hub 4-0:1.0: unable to enumerate USB device on port 1
[ 4371.676050] usb 2-1: new low speed USB device using uhci_hcd and address 6
[ 4371.845415] usb 2-1: configuration #1 chosen from 1 choice
[ 4372.002330] usbcore: registered new interface driver hiddev
[ 4372.018868] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input10
[ 4372.019113] generic-usb 0003:0461:4D0F.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[ 4372.019150] usbcore: registered new interface driver usbhid
[ 4372.024912] usbhid: v2.6:USB HID core driver
[ 4379.472083] usb 4-1: new full speed USB device using uhci_hcd and address 14
[ 4379.596084] usb 4-1: device descriptor read/64, error -71
[ 4379.824120] usb 4-1: device descriptor read/64, error -71
[ 4380.040125] usb 4-1: new full speed USB device using uhci_hcd and address 15
[ 4380.164062] usb 4-1: device descriptor read/64, error -71
[ 4380.388096] usb 4-1: device descriptor read/64, error -71
[ 4380.604070] usb 4-1: new full speed USB device using uhci_hcd and address 16
[ 4381.020073] usb 4-1: device not accepting address 16, error -71
[ 4381.133836] usb 4-1: new full speed USB device using uhci_hcd and address 17
[ 4381.544066] usb 4-1: device not accepting address 17, error -71
[ 4381.544107] hub 4-0:1.0: unable to enumerate USB device on port 1
```

---

### Post by GodfreyPeck on 2011-06-20
This thread: [http://ubuntuforums.org/showthread.php?t=970446](http://ubuntuforums.org/showthread.php?t=970446) shows similar read error (except I have "error -71 instead of error -110".

Apparently it "seems to only affect certain motherboards", but it did used to work on mine. I've seen several threads with related issues, none of which have been resolved yet.

> **Re: Device descriptor read/64, error -110**             
                                                                I have the same  problem on only one of four computers running Ubuntu 8.04 Hardy and  8.10 Intrepid. The problem has existed since at least Hardy and seems to  affect only certain motherboards. It is associated with the ehci_hcd  USB2.0 controller in the kernel.

I haven't found a solution yet, but one way round it is to disable the  onboard USB2.0 controller in the BIOS. Alternatively run the code

     Code:
     sudo modprobe -r ehci_hcd 
which will remove the USB2.0 controller from the kernel.

The down side to both these fixes is that USB interfaces will be only  USB 1.0/1.1, which will make transfers from large mass storage devices  very slow indeed.

I have spent hours reading post and bug reports, but the development team do not seem to acknowledge this a a valid bug.


---

