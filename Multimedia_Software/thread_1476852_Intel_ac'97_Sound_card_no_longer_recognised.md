---
title: "Intel ac'97 Sound card no longer recognised"
date: 2010-05-08
forum: Multimedia Software
---

### Post by debaser4 on 2010-05-08
Hello

This is my first post on ubuntu forums having sorted all my own problems out for 3 years now!

An upgrade during the last week seems to have caused my soundcard to no longer be recognised. It was ok on 10.04 (upgraded from 9.10) before the last few days. 
I have to admit I'm getting a little confused as there are so many posts about sound card issues. Nothing seems to work so i need some lateral thinking. 
I'm going to attach some outputs that I hope will be of use below.(I don't know how to insert these as scrolling code windows so forgive me)

debaser@debaser-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...

debaser@debaser-laptop:~$ lspci | grep audio
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

debaser@debaser-laptop:~$ groups debaser
debaser : debaser adm dialout cdrom audio video plugdev fuse lpadmin netdev admin sambashare shared vboxusers

debaser@debaser-laptop:~$ sudo alsamixer
cannot open mixer: No such file or directory

gksudo gedit /etc/modprobe.d/sound
alias snd-card-0 snd-intel8x0
alias sound-slot-0 snd-intel8x0
options snd-intel8x0 ac97_clock=48000
options snd slots=snd-intel8x0
# CvwD.FAMlirE10w6:82801AA AC'97 Audio Controller
alias snd-card-0 snd-intel8x0

debaser@debaser-laptop:~$ gksudo gedit /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

Dmesg>
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@iridium) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #34~kms1-Ubuntu SMP Thu May 6 06:29:51 UTC 2010 (Ubuntu 2.6.32-22.34~kms1-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffdfffc (usable)
[    0.000000]  BIOS-e820: 000000007ffdfffc - 000000007fffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fffffc0 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x7ffdf max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
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
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffdfffc (usable)
[    0.000000]  modified: 000000007ffdfffc - 000000007fffffc0 (ACPI data)
[    0.000000]  modified: 000000007fffffc0 - 0000000080000000 (ACPI NVS)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37857000 - 37fef0cc
[    0.000000] Allocated new RAMDISK: 008df000 - 010770cc
[    0.000000] Move RAMDISK from 0000000037857000 - 0000000037fef0cb to 008df000 - 010770cb
[    0.000000] ACPI: RSDP 000e5010 00014 (v00 TOSINV)
[    0.000000] ACPI: RSDT 7fff89f7 00034 (v01 INSYDE RSDT_000 00000100 ABCD 00010200)
[    0.000000] ACPI: FACP 7ffffb30 00074 (v01 TOSINV FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: DSDT 7fff9040 06AE5 (v01 TOSINV SONOMA   00001004 INTL 02002036)
[    0.000000] ACPI: FACS 7fffffc0 00040
[    0.000000] ACPI: MCFG 7ffffbc0 0003C (v01 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 7fff8be5 00237 (v01  PmRef  Cpu0Ist 00003000 INTL 20030522)
[    0.000000] ACPI: SSDT 7fff8a2b 001BA (v01  PmRef  Cpu0Cst 00003001 INTL 20030522)
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008daeb8]    TEXT DATA BSS ==> [0000100000 - 00008daeb8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008db000 - 00008de160]              BRK ==> [00008db000 - 00008de160]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008df000 - 00010770cc]      NEW RAMDISK ==> [00008df000 - 00010770cc]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffdf
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffdf
[    0.000000] On node 0 totalpages: 524154
[    0.000000] free_area_init_node: node 0, pgdat c0798740, node_mem_map c1079000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294609 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ff00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520058
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=4f71a023-6a74-4ce8-ae71-b71154fd39af ro nomodeset splash quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10485100 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffdf)
[    0.000000] Memory: 2052280k/2097020k available (4675k kernel code, 43388k reserved, 2119k data, 656k init, 1187716k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590fa3 - 0xc07a2e48   (2119 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590fa3   (4675 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.283 MHz processor.
[    0.008008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.56 BogoMIPS (lpj=6385132)
[    0.008034] Security Framework initialized
[    0.008072] AppArmor: AppArmor initialized
[    0.008082] Mount-cache hash table entries: 512
[    0.008259] Initializing cgroup subsys ns
[    0.008267] Initializing cgroup subsys cpuacct
[    0.008273] Initializing cgroup subsys memory
[    0.008286] Initializing cgroup subsys devices
[    0.008289] Initializing cgroup subsys freezer
[    0.008293] Initializing cgroup subsys net_cls
[    0.008324] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008327] CPU: L2 cache: 2048K
[    0.008333] mce: CPU supports 5 MCE banks
[    0.008355] Performance Events: 
[    0.008358] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.008361] no hardware sampling interrupt available.
[    0.008364] p6 PMU driver.
[    0.008372] ... version:                0
[    0.008374] ... bit width:              32
[    0.008376] ... generic registers:      2
[    0.008379] ... value mask:             00000000ffffffff
[    0.008382] ... max period:             000000007fffffff
[    0.008384] ... fixed-purpose events:   0
[    0.008387] ... event mask:             0000000000000003
[    0.008393] Checking 'hlt' instruction... OK.
[    0.025004] SMP alternatives: switching to UP code
[    0.033378] Freeing SMP alternatives: 19k freed
[    0.033389] ACPI: Core revision 20090903
[    0.044978] ACPI: setting ELCR to 0200 (from 0c20)
[    0.048030] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.048041] ftrace: allocating 21771 entries in 43 pages
[    0.052075] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.052080] weird, boot CPU (#0) not listed by the BIOS.
[    0.052083] SMP motherboard not detected.
[    0.052086] Local APIC not detected. Using dummy APIC emulation.
[    0.052089] SMP disabled
[    0.052215] Brought up 1 CPUs
[    0.052218] Total of 1 processors activated (3192.56 BogoMIPS).
[    0.056053] CPU0 attaching NULL sched-domain.
[    0.056204] devtmpfs: initialized
[    0.056627] regulator: core version 0.5
[    0.056659] Time:  9:37:30  Date: 05/08/10
[    0.056711] NET: Registered protocol family 16
[    0.056850] EISA bus registered
[    0.056860] ACPI: bus type pci registered
[    0.056943] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.056947] PCI: Not using MMCONFIG.
[    0.056995] PCI: PCI BIOS revision 2.10 entry at 0xea8f4, last bus=6
[    0.056997] PCI: Using configuration type 1 for base access
[    0.058135] bio: create slab <bio-0> at 0
[    0.059059] ACPI: EC: Look up EC in DSDT
[    0.072154] ACPI: Interpreter enabled
[    0.072164] ACPI: (supports S0 S3 S4 S5)
[    0.072192] ACPI: Using PIC for interrupt routing
[    0.072238] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.084169] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.084172] PCI: Using MMCONFIG for extended config space
[    0.103640] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.103702] ACPI: Power Resource [PUT2] (on)
[    0.103750] ACPI: Power Resource [PFA1] (off)
[    0.112196] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.112789] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.112905] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.112909] pci 0000:00:01.0: PME# disabled
[    0.113029] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.113034] pci 0000:00:1c.0: PME# disabled
[    0.113127] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.113133] pci 0000:00:1c.1: PME# disabled
[    0.113201] pci 0000:00:1d.0: reg 20 io port: [0x1200-0x121f]
[    0.113263] pci 0000:00:1d.1: reg 20 io port: [0x1220-0x123f]
[    0.113327] pci 0000:00:1d.2: reg 20 io port: [0x1240-0x125f]
[    0.113390] pci 0000:00:1d.3: reg 20 io port: [0x1260-0x127f]
[    0.113456] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4000000-0xf40003ff]
[    0.113517] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.113523] pci 0000:00:1d.7: PME# disabled
[    0.113634] pci 0000:00:1e.2: reg 10 io port: [0xe000-0xe0ff]
[    0.113643] pci 0000:00:1e.2: reg 14 io port: [0xe100-0xe13f]
[    0.113651] pci 0000:00:1e.2: reg 18 32bit mmio: [0xd0000000-0xd00001ff]
[    0.113660] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xd0000200-0xd00002ff]
[    0.113700] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.113705] pci 0000:00:1e.2: PME# disabled
[    0.113744] pci 0000:00:1e.3: reg 10 io port: [0xe200-0xe2ff]
[    0.113753] pci 0000:00:1e.3: reg 14 io port: [0xe300-0xe37f]
[    0.113802] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.113808] pci 0000:00:1e.3: PME# disabled
[    0.113898] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.113906] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.113911] pci 0000:00:1f.0: quirk: region 1300-133f claimed by ICH6 GPIO
[    0.113916] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0300-037f
[    0.113921] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 0110-011f
[    0.113964] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.113973] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.113981] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.113989] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.113998] pci 0000:00:1f.2: reg 20 io port: [0x1100-0x110f]
[    0.114033] pci 0000:00:1f.2: PME# supported from D3hot
[    0.114038] pci 0000:00:1f.2: PME# disabled
[    0.114079] pci 0000:01:00.0: reg 10 32bit mmio pref: [0x90000000-0x97ffffff]
[    0.114086] pci 0000:01:00.0: reg 14 io port: [0xc000-0xc0ff]
[    0.114093] pci 0000:01:00.0: reg 18 32bit mmio: [0xc0000000-0xc000ffff]
[    0.114109] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.114128] pci 0000:01:00.0: supports D1 D2
[    0.114183] pci 0000:00:01.0: bridge io port: [0xc000-0xdfff]
[    0.114187] pci 0000:00:01.0: bridge 32bit mmio: [0xc0000000-0xcfffffff]
[    0.114192] pci 0000:00:01.0: bridge 32bit mmio pref: [0x90000000-0x9fffffff]
[    0.114271] pci 0000:02:00.0: reg 10 64bit mmio: [0xbc000000-0xbc003fff]
[    0.114282] pci 0000:02:00.0: reg 18 io port: [0xa000-0xa0ff]
[    0.114367] pci 0000:02:00.0: supports D1 D2
[    0.114370] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.114377] pci 0000:02:00.0: PME# disabled
[    0.114439] pci 0000:00:1c.0: bridge io port: [0xa000-0xbfff]
[    0.114444] pci 0000:00:1c.0: bridge 32bit mmio: [0xbc000000-0xbfffffff]
[    0.114453] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x8c000000-0x8fffffff]
[    0.114510] pci 0000:00:1c.1: bridge io port: [0x8000-0x9fff]
[    0.114516] pci 0000:00:1c.1: bridge 32bit mmio: [0xb8000000-0xbbffffff]
[    0.114525] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x88000000-0x8bffffff]
[    0.114582] pci 0000:06:04.0: reg 10 32bit mmio: [0xb000b000-0xb000bfff]
[    0.114651] pci 0000:06:04.0: PME# supported from D0 D3hot D3cold
[    0.114657] pci 0000:06:04.0: PME# disabled
[    0.114708] pci 0000:06:06.0: reg 10 32bit mmio: [0x13000000-0x13000fff]
[    0.114736] pci 0000:06:06.0: supports D1 D2
[    0.114739] pci 0000:06:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.114745] pci 0000:06:06.0: PME# disabled
[    0.114796] pci 0000:06:06.2: reg 10 32bit mmio: [0xb0000000-0xb00007ff]
[    0.114806] pci 0000:06:06.2: reg 14 32bit mmio: [0xb0004000-0xb0007fff]
[    0.114871] pci 0000:06:06.2: supports D1 D2
[    0.114874] pci 0000:06:06.2: PME# supported from D0 D1 D2 D3hot
[    0.114880] pci 0000:06:06.2: PME# disabled
[    0.114928] pci 0000:06:06.3: reg 10 32bit mmio: [0xb0008000-0xb0009fff]
[    0.114997] pci 0000:06:06.3: supports D1 D2
[    0.114999] pci 0000:06:06.3: PME# supported from D0 D1 D2 D3hot
[    0.115006] pci 0000:06:06.3: PME# disabled
[    0.115054] pci 0000:06:06.4: reg 10 32bit mmio: [0xb000a000-0xb000a0ff]
[    0.115064] pci 0000:06:06.4: reg 14 32bit mmio: [0xb000a100-0xb000a1ff]
[    0.115075] pci 0000:06:06.4: reg 18 32bit mmio: [0xb000a200-0xb000a2ff]
[    0.115129] pci 0000:06:06.4: supports D1 D2
[    0.115132] pci 0000:06:06.4: PME# supported from D0 D1 D2 D3hot
[    0.115138] pci 0000:06:06.4: PME# disabled
[    0.115196] pci 0000:00:1e.0: transparent bridge
[    0.115201] pci 0000:00:1e.0: bridge io port: [0x6000-0x7fff]
[    0.115207] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0000000-0xb7ffffff]
[    0.115216] pci 0000:00:1e.0: bridge 64bit mmio pref: [0x80000000-0x87ffffff]
[    0.115263] pci_bus 0000:00: on NUMA node 0
[    0.115270] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.115576] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.115707] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.115834] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.116007] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.144320] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *11)
[    0.144442] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[    0.144562] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *11)
[    0.144680] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[    0.144798] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 11)
[    0.144915] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 10) *0, disabled.
[    0.145071] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *11
[    0.145189] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[    0.145316] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.145322] vgaarb: loaded
[    0.145462] SCSI subsystem initialized
[    0.145507] libata version 3.00 loaded.
[    0.145587] usbcore: registered new interface driver usbfs
[    0.145602] usbcore: registered new interface driver hub
[    0.145631] usbcore: registered new device driver usb
[    0.145776] ACPI: WMI: Mapper loaded
[    0.145779] PCI: Using ACPI for IRQ routing
[    0.145901] pci 0000:06:06.0: BAR 0: address space collision on of device [0x13000000-0x13000fff]
[    0.145904] pci 0000:06:06.0: BAR 0: can't allocate resource
[    0.146050] NetLabel: Initializing
[    0.146053] NetLabel:  domain hash size = 128
[    0.146055] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.146071] NetLabel:  unlabeled traffic allowed by default
[    0.146255] hpet clockevent registered
[    0.146260] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.146267] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.146273] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.148012] Switching to clocksource tsc
[    0.150351] AppArmor: AppArmor Filesystem Enabled
[    0.150364] pnp: PnP ACPI init
[    0.150375] ACPI: bus type pnp registered
[    0.157958] pnp: PnP ACPI: found 10 devices
[    0.157961] ACPI: ACPI bus type pnp unregistered
[    0.157965] PnPBIOS: Disabled by ACPI PNP
[    0.157978] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.157982] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.157986] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.157990] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.157994] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.157998] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.158002] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.158006] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.158014] system 00:05: ioport range 0x300-0x36f has been reserved
[    0.158018] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.158022] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.158026] system 00:05: ioport range 0x1300-0x133f has been reserved
[    0.158030] system 00:05: iomem range 0xe0000000-0xefffffff has been reserved
[    0.158034] system 00:05: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.158038] system 00:05: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.158042] system 00:05: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.158046] system 00:05: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.192788] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.192792] pci 0000:00:01.0:   IO window: 0xc000-0xdfff
[    0.192797] pci 0000:00:01.0:   MEM window: 0xc0000000-0xcfffffff
[    0.192801] pci 0000:00:01.0:   PREFETCH window: 0x90000000-0x9fffffff
[    0.192807] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.192811] pci 0000:00:1c.0:   IO window: 0xa000-0xbfff
[    0.192818] pci 0000:00:1c.0:   MEM window: 0xbc000000-0xbfffffff
[    0.192824] pci 0000:00:1c.0:   PREFETCH window: 0x0000008c000000-0x0000008fffffff
[    0.192833] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.192837] pci 0000:00:1c.1:   IO window: 0x8000-0x9fff
[    0.192844] pci 0000:00:1c.1:   MEM window: 0xb8000000-0xbbffffff
[    0.192850] pci 0000:00:1c.1:   PREFETCH window: 0x00000088000000-0x0000008bffffff
[    0.192869] pci 0000:06:06.0: CardBus bridge, secondary bus 0000:07
[    0.192873] pci 0000:06:06.0:   IO window: 0x006000-0x0060ff
[    0.192879] pci 0000:06:06.0:   IO window: 0x006400-0x0064ff
[    0.192885] pci 0000:06:06.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.192892] pci 0000:06:06.0:   MEM window: 0xb4000000-0xb7ffffff
[    0.192899] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.192903] pci 0000:00:1e.0:   IO window: 0x6000-0x7fff
[    0.192910] pci 0000:00:1e.0:   MEM window: 0xb0000000-0xb7ffffff
[    0.192916] pci 0000:00:1e.0:   PREFETCH window: 0x00000080000000-0x00000087ffffff
[    0.193109] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.193113] PCI: setting IRQ 11 as level-triggered
[    0.193120] pci 0000:00:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.193125] pci 0000:00:01.0: setting latency timer to 64
[    0.193303] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    0.193306] PCI: setting IRQ 10 as level-triggered
[    0.193313] pci 0000:00:1c.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    0.193319] pci 0000:00:1c.0: setting latency timer to 64
[    0.193331] pci 0000:00:1c.1: PCI INT B -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.193337] pci 0000:00:1c.1: setting latency timer to 64
[    0.193345] pci 0000:00:1e.0: setting latency timer to 64
[    0.193524] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.193528] pci 0000:06:06.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.193537] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.193540] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.193544] pci_bus 0000:01: resource 0 io:  [0xc000-0xdfff]
[    0.193547] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xcfffffff]
[    0.193551] pci_bus 0000:01: resource 2 pref mem [0x90000000-0x9fffffff]
[    0.193554] pci_bus 0000:02: resource 0 io:  [0xa000-0xbfff]
[    0.193558] pci_bus 0000:02: resource 1 mem: [0xbc000000-0xbfffffff]
[    0.193561] pci_bus 0000:02: resource 2 pref mem [0x8c000000-0x8fffffff]
[    0.193565] pci_bus 0000:03: resource 0 io:  [0x8000-0x9fff]
[    0.193568] pci_bus 0000:03: resource 1 mem: [0xb8000000-0xbbffffff]
[    0.193572] pci_bus 0000:03: resource 2 pref mem [0x88000000-0x8bffffff]
[    0.193576] pci_bus 0000:06: resource 0 io:  [0x6000-0x7fff]
[    0.193579] pci_bus 0000:06: resource 1 mem: [0xb0000000-0xb7ffffff]
[    0.193582] pci_bus 0000:06: resource 2 pref mem [0x80000000-0x87ffffff]
[    0.193586] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.193589] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.193593] pci_bus 0000:07: resource 0 io:  [0x6000-0x60ff]
[    0.193596] pci_bus 0000:07: resource 1 io:  [0x6400-0x64ff]
[    0.193599] pci_bus 0000:07: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.193603] pci_bus 0000:07: resource 3 mem: [0xb4000000-0xb7ffffff]
[    0.193638] NET: Registered protocol family 2
[    0.193739] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.194098] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.194961] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.195517] TCP: Hash tables configured (established 131072 bind 65536)
[    0.195521] TCP reno registered
[    0.195646] NET: Registered protocol family 1
[    0.195750] pci 0000:01:00.0: Boot video device
[    0.196032] cpufreq-nforce2: No nForce2 chipset.
[    0.196063] Scanning for low memory corruption every 60 seconds
[    0.196226] audit: initializing netlink socket (disabled)
[    0.196247] type=2000 audit(1273311450.195:1): initialized
[    0.209278] Trying to unpack rootfs image as initramfs...
[    0.224355] highmem bounce pool size: 64 pages
[    0.224363] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.232364] VFS: Disk quotas dquot_6.5.2
[    0.232451] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.233216] fuse init (API version 7.13)
[    0.233324] msgmni has been set to 1690
[    0.233567] alg: No test for stdrng (krng)
[    0.233639] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.233644] io scheduler noop registered
[    0.233646] io scheduler anticipatory registered
[    0.233649] io scheduler deadline registered
[    0.233702] io scheduler cfq registered (default)
[    0.233868]   alloc irq_desc for 16 on node -1
[    0.233871]   alloc kstat_irqs on node -1
[    0.233883] pcieport 0000:00:01.0: irq 16 for MSI/MSI-X
[    0.233890] pcieport 0000:00:01.0: setting latency timer to 64
[    0.234009]   alloc irq_desc for 17 on node -1
[    0.234012]   alloc kstat_irqs on node -1
[    0.234021] pcieport 0000:00:1c.0: irq 17 for MSI/MSI-X
[    0.234032] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.234185]   alloc irq_desc for 18 on node -1
[    0.234187]   alloc kstat_irqs on node -1
[    0.234196] pcieport 0000:00:1c.1: irq 18 for MSI/MSI-X
[    0.234207] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.234322] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.234434] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.236240] ACPI: AC Adapter [AC] (off-line)
[    0.236334] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.240112] ACPI: Lid Switch [LID0]
[    0.240177] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.240181] ACPI: Power Button [PWRB]
[    0.240253] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.240257] ACPI: Power Button [PWRF]
[    0.240391] fan PNP0C0B:00: registered as cooling_device0
[    0.240398] ACPI: Fan [FAN1] (off)
[    0.240867] Marking TSC unstable due to TSC halts in idle
[    0.240913] processor LNXCPU:00: registered as cooling_device1
[    0.246733] Switching to clocksource hpet
[    0.316626] thermal LNXTHERM:01: registered as thermal_zone0
[    0.316641] ACPI: Thermal Zone [TZCR] (39 C)
[    0.324232] thermal LNXTHERM:02: registered as thermal_zone1
[    0.324245] ACPI: Thermal Zone [TZVR] (19 C)
[    0.332506] thermal LNXTHERM:03: registered as thermal_zone2
[    0.332518] ACPI: Thermal Zone [TZVL] (19 C)
[    0.340265] thermal LNXTHERM:04: registered as thermal_zone3
[    0.340278] ACPI: Thermal Zone [TZCL] (18 C)
[    0.342136] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.342302] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.342871] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[    0.342875] PCI: setting IRQ 5 as level-triggered
[    0.342882] serial 0000:00:1e.3: PCI INT B -> Link[LNKE] -> GSI 5 (level, low) -> IRQ 5
[    0.342891] serial 0000:00:1e.3: PCI INT B disabled
[    0.348592] brd: module loaded
[    0.349170] loop: module loaded
[    0.349292] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.349433] ata_piix 0000:00:1f.2: version 2.13
[    0.349652] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.349657] ata_piix 0000:00:1f.2: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.349665] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.349733] isapnp: Scanning for PnP cards...
[    0.440346] ACPI: Battery Slot [BAT1] (battery present)
[    0.504340] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.508087] scsi0 : ata_piix
[    0.508249] scsi1 : ata_piix
[    0.509521] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    0.509525] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    0.510008] Fixed MDIO Bus: probed
[    0.510055] PPP generic driver version 2.4.2
[    0.510140] tun: Universal TUN/TAP device driver, 1.6
[    0.510142] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.510255] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.510282] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
[    0.510482] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    0.510488] ehci_hcd 0000:00:1d.7: PCI INT A -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    0.510512] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.510516] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.510557] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.510594] ehci_hcd 0000:00:1d.7: debug port 1
[    0.514480] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.520173] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[    0.540169] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.540360] usb usb1: configuration #1 chosen from 1 choice
[    0.540398] hub 1-0:1.0: USB hub found
[    0.540410] hub 1-0:1.0: 8 ports detected
[    0.540513] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.540536] uhci_hcd: USB Universal Host Controller Interface driver
[    0.540600] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    0.540612] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.540617] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.540669] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.540702] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[    0.540813] usb usb2: configuration #1 chosen from 1 choice
[    0.540844] hub 2-0:1.0: USB hub found
[    0.540853] hub 2-0:1.0: 2 ports detected
[    0.540909] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.540916] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.540920] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.540955] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.540984] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001220
[    0.541083] usb usb3: configuration #1 chosen from 1 choice
[    0.541114] hub 3-0:1.0: USB hub found
[    0.541121] hub 3-0:1.0: 2 ports detected
[    0.541175] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.541183] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.541187] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.541226] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.541253] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001240
[    0.541361] usb usb4: configuration #1 chosen from 1 choice
[    0.541392] hub 4-0:1.0: USB hub found
[    0.541400] hub 4-0:1.0: 2 ports detected
[    0.541453] uhci_hcd 0000:00:1d.3: PCI INT D -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.541460] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.541465] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.541501] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.541528] uhci_hcd 0000:00:1d.3: irq 11, io base 0x00001260
[    0.541628] usb usb5: configuration #1 chosen from 1 choice
[    0.541663] hub 5-0:1.0: USB hub found
[    0.541671] hub 5-0:1.0: 2 ports detected
[    0.541788] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.546169] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.554631] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.554646] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.560205] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.560254] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.560282] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.560449] mice: PS/2 mouse device common for all mice
[    0.560635] rtc_cmos 00:06: RTC can wake from S4
[    0.560687] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.560716] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.560878] device-mapper: uevent: version 1.0.3
[    0.561023] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.604674] device-mapper: multipath: version 1.1.0 loaded
[    0.604677] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.604832] EISA: Probing bus 0 at eisa.0
[    0.604840] Cannot allocate resource for EISA slot 1
[    0.604858] Cannot allocate resource for EISA slot 6
[    0.604861] Cannot allocate resource for EISA slot 7
[    0.604863] Cannot allocate resource for EISA slot 8
[    0.604866] EISA: Detected 0 cards.
[    0.606581] cpuidle: using governor ladder
[    0.606657] cpuidle: using governor menu
[    0.607203] TCP cubic registered
[    0.607404] NET: Registered protocol family 10
[    0.607937] lo: Disabled Privacy Extensions
[    0.608344] NET: Registered protocol family 17
[    0.608810] Using IPI No-Shortcut mode
[    0.608958] PM: Resume from disk failed.
[    0.608973] registered taskstats version 1
[    0.609273] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.609812]   Magic number: 10:128:626
[    0.609932] rtc_cmos 00:06: setting system clock to 2010-05-08 09:37:31 UTC (1273311451)
[    0.609936] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.609938] EDD information not available.
[    0.704209] ata2.01: NODEV after polling detection
[    0.712572] ata2.00: ATAPI: UJDA750 DVD/CDRW, 1.60, max UDMA/33
[    0.714147] Freeing initrd memory: 7776k freed
[    0.765156] ata1.00: ATA-6: FUJITSU MHT2060AT, 0022, max UDMA/100
[    0.765162] ata1.00: 117210240 sectors, multi 16: LBA 
[    0.765179] ata1.00: applying bridge limits
[    0.765722] ata2.00: configured for UDMA/33
[    0.896857] isapnp: No Plug & Play device found
[    0.896899] ata1.00: configured for UDMA/100
[    0.897108] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    0.897346] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.897575] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    0.897635] sd 0:0:0:0: [sda] Write Protect is off
[    0.897639] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.897669] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.897848]  sda:
[    0.898864] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA750 DVD/CDRW 1.60 PQ: 0 ANSI: 5
[    0.902043] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.902047] Uniform CD-ROM driver Revision: 3.20
[    0.902163] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.902223] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.924564]  sda1 sda2 < sda5 sda6 >
[    0.963456] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.963475] Freeing unused kernel memory: 656k freed
[    0.963962] Write protecting the kernel text: 4676k
[    0.964050] Write protecting the kernel read-only data: 1844k
[    0.998129] udev: starting version 151
[    1.104054] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.243993] sky2 driver version 1.25
[    1.244877] sky2 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.244894] sky2 0000:02:00.0: setting latency timer to 64
[    1.244927] sky2 0000:02:00.0: Yukon-2 EC chip revision 1
[    1.245036]   alloc irq_desc for 19 on node -1
[    1.245038]   alloc kstat_irqs on node -1
[    1.245056] sky2 0000:02:00.0: irq 19 for MSI/MSI-X
[    1.280919] usb 2-1: configuration #1 chosen from 1 choice
[    1.300170] usbcore: registered new interface driver hiddev
[    1.313273] input: Genius NetScroll + Mini Traveler as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input5
[    1.313513] generic-usb 0003:0458:0036.0001: input,hidraw0: USB HID v1.10 Mouse [Genius NetScroll + Mini Traveler] on usb-0000:00:1d.0-1/input0
[    1.313539] usbcore: registered new interface driver usbhid
[    1.313640] usbhid: v2.6:USB HID core driver
[    1.344078] sky2 0000:02:00.0: No interrupt generated using MSI, switching to INTx mode.
[    1.344923] sky2 eth0: addr 00:a0:d1:bc:49:3f
[    1.536120] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    8.553335] Adding 1084348k swap on /dev/sda6.  Priority:-1 extents:1 across:1084348k 
[    8.580476] udev: starting version 151
[    8.956333] Linux agpgart interface v0.103
[    9.018445] intel_rng: FWH not detected
[    9.097800] lib80211: common routines for IEEE802.11 drivers
[    9.097805] lib80211_crypt: registered algorithm 'NULL'
[    9.134337] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    9.134357] BUG: unable to handle kernel NULL pointer dereference at (null)
[    9.134481] IP: [<f81794b7>] agp_add_bridge+0x37/0x200 [agpgart]
[    9.134570] *pde = 7eb68067 
[    9.134648] Oops: 0000 [#1] SMP 
[    9.134763] last sysfs file: /sys/devices/virtual/block/loop0/uevent
[    9.134809] Modules linked in: intel_agp(+) tifm_core(+) led_class pcmcia_core lib80211 parport psmouse serio_raw i2c_algo_bit intel_rng(-) agpgart soundcore snd_page_alloc usbhid hid sky2
[    9.135487] 
[    9.135529] Pid: 359, comm: modprobe Not tainted (2.6.32-22-generic #34~kms1-Ubuntu) TECRA A4
[    9.135578] EIP: 0060:[<f81794b7>] EFLAGS: 00010286 CPU: 0
[    9.135625] EIP is at agp_add_bridge+0x37/0x200 [agpgart]
[    9.135670] EAX: f7081000 EBX: f54fba00 ECX: 00000000 EDX: 00000000
[    9.135716] ESI: ffffffed EDI: 00000000 EBP: f5dc1e18 ESP: f5dc1de8
[    9.135762]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[    9.135807] Process modprobe (pid: 359, ti=f5dc0000 task=f5f32670 task.ti=f5dc0000)
[    9.135854] Stack:
[    9.135894]  f7081058 f5dc1dfc c0362c31 f7081000 00000000 f5dc1e10 c0362c9d f54fba00
[    9.136016] <0> f7081000 f54fba00 f7081000 f7081058 f5dc1e4c f81e89f3 f81e9ae2 f81e9b53
[    9.136016] <0> f70b1810 f81e9bc6 f5dc1e38 f81e9bc6 f70b1810 0036437e f7081000 f81e9e80
[    9.136016] Call Trace:
[    9.136016]  [<c0362c31>] ? do_pci_enable_device+0x51/0x60
[    9.136016]  [<c0362c9d>] ? __pci_enable_device_flags+0x5d/0x70
[    9.136016]  [<f81e89f3>] ? agp_intel_probe+0x1bd/0x1d3 [intel_agp]
[    9.136016]  [<c03641d3>] ? local_pci_probe+0x13/0x20
[    9.136016]  [<c0364fd8>] ? pci_device_probe+0x68/0x90
[    9.136016]  [<c03e71dd>] ? really_probe+0x4d/0x140
[    9.136016]  [<c03edaee>] ? pm_runtime_barrier+0x4e/0xc0
[    9.136016]  [<c03e730c>] ? driver_probe_device+0x3c/0x60
[    9.136016]  [<c03e73b1>] ? __driver_attach+0x81/0x90
[    9.136016]  [<c03e67f3>] ? bus_for_each_dev+0x53/0x80
[    9.136016]  [<c03e70ae>] ? driver_attach+0x1e/0x20
[    9.136016]  [<c03e7330>] ? __driver_attach+0x0/0x90
[    9.136016]  [<c03e6a75>] ? bus_add_driver+0xd5/0x280
[    9.136016]  [<c0364f10>] ? pci_device_remove+0x0/0x40
[    9.136016]  [<c03e76aa>] ? driver_register+0x6a/0x130
[    9.136016]  [<c0365215>] ? __pci_register_driver+0x45/0xb0
[    9.136016]  [<f81ee025>] ? agp_intel_init+0x25/0x27 [intel_agp]
[    9.136016]  [<c0101131>] ? do_one_initcall+0x31/0x190
[    9.136016]  [<f81ee000>] ? agp_intel_init+0x0/0x27 [intel_agp]
[    9.136016]  [<c0182340>] ? sys_init_module+0xb0/0x210
[    9.136016]  [<c01033ec>] ? syscall_call+0x7/0xb
[    9.136016] Code: 89 7d fc 0f 1f 44 00 00 8b 3d 04 e5 17 f8 be ed ff ff ff 85 ff 89 c3 0f 85 83 00 00 00 8b 40 18 85 c0 0f 84 4e 01 00 00 8b 53 04 <8b> 32 85 f6 74 3c 64 8b 15 40 0a 84 c0 83 3e 02 0f 84 80 01 00 
[    9.136016] EIP: [<f81794b7>] agp_add_bridge+0x37/0x200 [agpgart] SS:ESP 0068:f5dc1de8
[    9.136016] CR2: 0000000000000000
[    9.140811] ---[ end trace 4eb2c505cdd7ba83 ]---
[    9.240207] irda_init()
[    9.240277] NET: Registered protocol family 23
[    9.273213] type=1505 audit(1273311460.162:2):  operation="profile_load" pid=555 name="/sbin/dhclient3"
[    9.274028] type=1505 audit(1273311460.162:3):  operation="profile_load" pid=555 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.274494] type=1505 audit(1273311460.162:4):  operation="profile_load" pid=555 name="/usr/lib/connman/scripts/dhclient-script"
[    9.304345] [drm] Initialized drm 1.1.0 20060810
[    9.312078] sdhci: Secure Digital Host Controller Interface driver
[    9.312132] sdhci: Copyright(c) Pierre Ossman
[    9.330295] tifm_7xx1 0000:06:06.3: PCI INT D -> Link[LNKE] -> GSI 5 (level, low) -> IRQ 5
[    9.331135] ieee80211: 802.11 data/management/control stack, git-1.1.13
[    9.331188] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[    9.346273] lp: driver loaded but no devices found
[    9.372115] yenta_cardbus 0000:06:06.0: CardBus bridge found [1179:ff10]
[    9.372194] yenta_cardbus 0000:06:06.0: Enabling burst memory read transactions
[    9.372257] yenta_cardbus 0000:06:06.0: Using CSCINT to route CSC interrupts to PCI
[    9.372316] yenta_cardbus 0000:06:06.0: Routing CardBus interrupts to PCI
[    9.372372] yenta_cardbus 0000:06:06.0: TI: mfunc 0x01aa1b22, devctl 0x66
[    9.388101] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[    9.388166] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    9.604485] yenta_cardbus 0000:06:06.0: ISA IRQ mask 0x00d8, PCI irq 11
[    9.604546] yenta_cardbus 0000:06:06.0: Socket status: 30000006
[    9.604599] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[    9.604669] yenta_cardbus 0000:06:06.0: pcmcia: parent PCI bridge I/O window: 0x6000 - 0x7fff
[    9.604730] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x6000-0x7fff: clean.
[    9.605300] yenta_cardbus 0000:06:06.0: pcmcia: parent PCI bridge Memory window: 0xb0000000 - 0xb7ffffff
[    9.605361] yenta_cardbus 0000:06:06.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x87ffffff
[    9.605837] sdhci-pci 0000:06:06.4: SDHCI controller found [104c:8034] (rev 0)
[    9.605920] sdhci-pci 0000:06:06.4: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    9.606061] Registered led device: mmc0::
[    9.606151] mmc0: SDHCI controller on PCI [0000:06:06.4] using PIO
[    9.606241] Registered led device: mmc1::
[    9.606314] mmc1: SDHCI controller on PCI [0000:06:06.4] using PIO
[    9.606400] Registered led device: mmc2::
[    9.606477] mmc2: SDHCI controller on PCI [0000:06:06.4] using PIO
[    9.606612] ipw2200 0000:06:04.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    9.608381] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[    9.608487] ipw2200 0000:06:04.0: firmware: requesting ipw2200-bss.fw
[    9.779894] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
[    9.780367] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input6
[    9.780868] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    9.781916] [drm] VGACON disable radeon kernel modesetting.
[    9.782112] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    9.782174] pci 0000:01:00.0: setting latency timer to 64
[    9.782454] [drm] Initialized radeon 1.32.0 20080528 for 0000:01:00.0 on minor 0
[    9.968511] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[   10.031545] ipw2200: Radio Frequency Kill Switch is On:
[   10.031547] Kill switch must be turned off for wireless networking to work.
[   10.041690] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   10.055508] vga16fb: initializing
[   10.055564] vga16fb: mapped to 0xc00a0000
[   10.055769] fb0: VGA16 VGA frame buffer device
[   10.092306] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   10.330365] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x118-0x11f
[   10.331966] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   10.332946] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   10.333644] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   10.334535] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   10.514842] Console: switching to colour frame buffer device 80x30
[   14.986473] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   16.077064] type=1505 audit(1273311466.966:5):  operation="profile_load" pid=731 name="/usr/share/gdm/guest-session/Xsession"
[   16.085459] type=1505 audit(1273311466.974:6):  operation="profile_replace" pid=732 name="/sbin/dhclient3"
[   16.086216] type=1505 audit(1273311466.974:7):  operation="profile_replace" pid=732 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.086625] type=1505 audit(1273311466.974:8):  operation="profile_replace" pid=732 name="/usr/lib/connman/scripts/dhclient-script"
[   16.156740] type=1505 audit(1273311467.046:9):  operation="profile_load" pid=733 name="/usr/bin/evince"
[   16.178464] type=1505 audit(1273311467.066:10):  operation="profile_load" pid=733 name="/usr/bin/evince-previewer"
[   16.192345] type=1505 audit(1273311467.082:11):  operation="profile_load" pid=733 name="/usr/bin/evince-thumbnailer"
[   16.238916] type=1505 audit(1273311467.126:12):  operation="profile_load" pid=736 name="/usr/bin/freshclam"
[   16.263919] type=1505 audit(1273311467.150:13):  operation="profile_load" pid=737 name="/usr/lib/cups/backend/cups-pdf"
[   16.265008] type=1505 audit(1273311467.154:14):  operation="profile_load" pid=737 name="/usr/sbin/cupsd"
[   17.395094] apm: BIOS not found.
[   19.573680] sky2 eth0: enabling interface
[   19.574681] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.263088] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   21.263326] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.593460] [drm] Setting GART location based on new memory map
[   23.596358] [drm] Loading R300 Microcode
[   23.596982] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   23.655445] [drm] Num pipes: 1
[   23.655457] [drm] writeback test succeeded in 1 usecs

I can boot into the last grub instance and sound works, here is the working dmesg output. I can't see anything obvious - no alsa and no audio entries that appear relevant but here it is for comparision (the differences start at around 9 seconds)

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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffdfffc (usable)
[    0.000000]  BIOS-e820: 000000007ffdfffc - 000000007fffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fffffc0 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x7ffdf max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
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
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffdfffc (usable)
[    0.000000]  modified: 000000007ffdfffc - 000000007fffffc0 (ACPI data)
[    0.000000]  modified: 000000007fffffc0 - 0000000080000000 (ACPI NVS)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37857000 - 37fef24f
[    0.000000] Allocated new RAMDISK: 008de000 - 0107624f
[    0.000000] Move RAMDISK from 0000000037857000 - 0000000037fef24e to 008de000 - 0107624e
[    0.000000] ACPI: RSDP 000e5010 00014 (v00 TOSINV)
[    0.000000] ACPI: RSDT 7fff89f7 00034 (v01 INSYDE RSDT_000 00000100 ABCD 00010200)
[    0.000000] ACPI: FACP 7ffffb30 00074 (v01 TOSINV FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: DSDT 7fff9040 06AE5 (v01 TOSINV SONOMA   00001004 INTL 02002036)
[    0.000000] ACPI: FACS 7fffffc0 00040
[    0.000000] ACPI: MCFG 7ffffbc0 0003C (v01 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 7fff8be5 00237 (v01  PmRef  Cpu0Ist 00003000 INTL 20030522)
[    0.000000] ACPI: SSDT 7fff8a2b 001BA (v01  PmRef  Cpu0Cst 00003001 INTL 20030522)
[    0.000000] 1159MB HIGHMEM available.
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
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008da000 - 00008dd160]              BRK ==> [00008da000 - 00008dd160]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008de000 - 000107624f]      NEW RAMDISK ==> [00008de000 - 000107624f]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffdf
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffdf
[    0.000000] On node 0 totalpages: 524154
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1078000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294609 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ff00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520058
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=4f71a023-6a74-4ce8-ae71-b71154fd39af ro nomodeset splash quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10485100 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffdf)
[    0.000000] Memory: 2052280k/2097020k available (4673k kernel code, 43384k reserved, 2122k data, 656k init, 1187716k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1595.996 MHz processor.
[    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.99 BogoMIPS (lpj=6383984)
[    0.008033] Security Framework initialized
[    0.008070] AppArmor: AppArmor initialized
[    0.008081] Mount-cache hash table entries: 512
[    0.008260] Initializing cgroup subsys ns
[    0.008267] Initializing cgroup subsys cpuacct
[    0.008273] Initializing cgroup subsys memory
[    0.008285] Initializing cgroup subsys devices
[    0.008288] Initializing cgroup subsys freezer
[    0.008291] Initializing cgroup subsys net_cls
[    0.008322] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008326] CPU: L2 cache: 2048K
[    0.008332] mce: CPU supports 5 MCE banks
[    0.008353] Performance Events: 
[    0.008357] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.008360] no hardware sampling interrupt available.
[    0.008363] p6 PMU driver.
[    0.008370] ... version:                0
[    0.008372] ... bit width:              32
[    0.008375] ... generic registers:      2
[    0.008377] ... value mask:             00000000ffffffff
[    0.008380] ... max period:             000000007fffffff
[    0.008382] ... fixed-purpose events:   0
[    0.008385] ... event mask:             0000000000000003
[    0.008391] Checking 'hlt' instruction... OK.
[    0.024998] SMP alternatives: switching to UP code
[    0.033597] Freeing SMP alternatives: 19k freed
[    0.033608] ACPI: Core revision 20090903
[    0.045213] ACPI: setting ELCR to 0200 (from 0c20)
[    0.048030] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.048041] ftrace: allocating 21771 entries in 43 pages
[    0.056075] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.056080] weird, boot CPU (#0) not listed by the BIOS.
[    0.056083] SMP motherboard not detected.
[    0.056086] Local APIC not detected. Using dummy APIC emulation.
[    0.056089] SMP disabled
[    0.056216] Brought up 1 CPUs
[    0.056219] Total of 1 processors activated (3191.99 BogoMIPS).
[    0.060053] CPU0 attaching NULL sched-domain.
[    0.060204] devtmpfs: initialized
[    0.060628] regulator: core version 0.5
[    0.060661] Time: 10:23:01  Date: 05/08/10
[    0.060713] NET: Registered protocol family 16
[    0.060851] EISA bus registered
[    0.060861] ACPI: bus type pci registered
[    0.060944] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.060948] PCI: Not using MMCONFIG.
[    0.060996] PCI: PCI BIOS revision 2.10 entry at 0xea8f4, last bus=6
[    0.060998] PCI: Using configuration type 1 for base access
[    0.062128] bio: create slab <bio-0> at 0
[    0.063051] ACPI: EC: Look up EC in DSDT
[    0.072169] ACPI: Interpreter enabled
[    0.072177] ACPI: (supports S0 S3 S4 S5)
[    0.072205] ACPI: Using PIC for interrupt routing
[    0.072252] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.084171] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.084174] PCI: Using MMCONFIG for extended config space
[    0.103683] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.103746] ACPI: Power Resource [PUT2] (on)
[    0.103794] ACPI: Power Resource [PFA1] (off)
[    0.112197] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.112793] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.112908] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.112912] pci 0000:00:01.0: PME# disabled
[    0.113033] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.113039] pci 0000:00:1c.0: PME# disabled
[    0.113132] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.113137] pci 0000:00:1c.1: PME# disabled
[    0.113205] pci 0000:00:1d.0: reg 20 io port: [0x1200-0x121f]
[    0.113268] pci 0000:00:1d.1: reg 20 io port: [0x1220-0x123f]
[    0.113333] pci 0000:00:1d.2: reg 20 io port: [0x1240-0x125f]
[    0.113395] pci 0000:00:1d.3: reg 20 io port: [0x1260-0x127f]
[    0.113462] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4000000-0xf40003ff]
[    0.113523] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.113530] pci 0000:00:1d.7: PME# disabled
[    0.113640] pci 0000:00:1e.2: reg 10 io port: [0xe000-0xe0ff]
[    0.113649] pci 0000:00:1e.2: reg 14 io port: [0xe100-0xe13f]
[    0.113658] pci 0000:00:1e.2: reg 18 32bit mmio: [0xd0000000-0xd00001ff]
[    0.113667] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xd0000200-0xd00002ff]
[    0.113706] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.113712] pci 0000:00:1e.2: PME# disabled
[    0.113751] pci 0000:00:1e.3: reg 10 io port: [0xe200-0xe2ff]
[    0.113759] pci 0000:00:1e.3: reg 14 io port: [0xe300-0xe37f]
[    0.113808] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.113814] pci 0000:00:1e.3: PME# disabled
[    0.113904] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.113912] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.113918] pci 0000:00:1f.0: quirk: region 1300-133f claimed by ICH6 GPIO
[    0.113923] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0300-037f
[    0.113928] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 0110-011f
[    0.113971] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.113979] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.113988] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.113997] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.114005] pci 0000:00:1f.2: reg 20 io port: [0x1100-0x110f]
[    0.114040] pci 0000:00:1f.2: PME# supported from D3hot
[    0.114046] pci 0000:00:1f.2: PME# disabled
[    0.114087] pci 0000:01:00.0: reg 10 32bit mmio pref: [0x90000000-0x97ffffff]
[    0.114094] pci 0000:01:00.0: reg 14 io port: [0xc000-0xc0ff]
[    0.114101] pci 0000:01:00.0: reg 18 32bit mmio: [0xc0000000-0xc000ffff]
[    0.114118] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.114137] pci 0000:01:00.0: supports D1 D2
[    0.114192] pci 0000:00:01.0: bridge io port: [0xc000-0xdfff]
[    0.114196] pci 0000:00:01.0: bridge 32bit mmio: [0xc0000000-0xcfffffff]
[    0.114201] pci 0000:00:01.0: bridge 32bit mmio pref: [0x90000000-0x9fffffff]
[    0.114279] pci 0000:02:00.0: reg 10 64bit mmio: [0xbc000000-0xbc003fff]
[    0.114291] pci 0000:02:00.0: reg 18 io port: [0xa000-0xa0ff]
[    0.114375] pci 0000:02:00.0: supports D1 D2
[    0.114378] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.114385] pci 0000:02:00.0: PME# disabled
[    0.114448] pci 0000:00:1c.0: bridge io port: [0xa000-0xbfff]
[    0.114453] pci 0000:00:1c.0: bridge 32bit mmio: [0xbc000000-0xbfffffff]
[    0.114462] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x8c000000-0x8fffffff]
[    0.114520] pci 0000:00:1c.1: bridge io port: [0x8000-0x9fff]
[    0.114526] pci 0000:00:1c.1: bridge 32bit mmio: [0xb8000000-0xbbffffff]
[    0.114535] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x88000000-0x8bffffff]
[    0.114592] pci 0000:06:04.0: reg 10 32bit mmio: [0xb000b000-0xb000bfff]
[    0.114662] pci 0000:06:04.0: PME# supported from D0 D3hot D3cold
[    0.114668] pci 0000:06:04.0: PME# disabled
[    0.114719] pci 0000:06:06.0: reg 10 32bit mmio: [0x13000000-0x13000fff]
[    0.114747] pci 0000:06:06.0: supports D1 D2
[    0.114750] pci 0000:06:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.114756] pci 0000:06:06.0: PME# disabled
[    0.114807] pci 0000:06:06.2: reg 10 32bit mmio: [0xb0000000-0xb00007ff]
[    0.114818] pci 0000:06:06.2: reg 14 32bit mmio: [0xb0004000-0xb0007fff]
[    0.114883] pci 0000:06:06.2: supports D1 D2
[    0.114886] pci 0000:06:06.2: PME# supported from D0 D1 D2 D3hot
[    0.114892] pci 0000:06:06.2: PME# disabled
[    0.114940] pci 0000:06:06.3: reg 10 32bit mmio: [0xb0008000-0xb0009fff]
[    0.115008] pci 0000:06:06.3: supports D1 D2
[    0.115011] pci 0000:06:06.3: PME# supported from D0 D1 D2 D3hot
[    0.115017] pci 0000:06:06.3: PME# disabled
[    0.115065] pci 0000:06:06.4: reg 10 32bit mmio: [0xb000a000-0xb000a0ff]
[    0.115076] pci 0000:06:06.4: reg 14 32bit mmio: [0xb000a100-0xb000a1ff]
[    0.115087] pci 0000:06:06.4: reg 18 32bit mmio: [0xb000a200-0xb000a2ff]
[    0.115141] pci 0000:06:06.4: supports D1 D2
[    0.115144] pci 0000:06:06.4: PME# supported from D0 D1 D2 D3hot
[    0.115150] pci 0000:06:06.4: PME# disabled
[    0.115209] pci 0000:00:1e.0: transparent bridge
[    0.115215] pci 0000:00:1e.0: bridge io port: [0x6000-0x7fff]
[    0.115221] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0000000-0xb7ffffff]
[    0.115230] pci 0000:00:1e.0: bridge 64bit mmio pref: [0x80000000-0x87ffffff]
[    0.115277] pci_bus 0000:00: on NUMA node 0
[    0.115284] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.115588] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.115720] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.115848] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.116021] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.144323] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *11)
[    0.144446] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[    0.144566] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *11)
[    0.144685] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[    0.144805] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 11)
[    0.144924] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 10) *0, disabled.
[    0.145083] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *11
[    0.145202] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[    0.145330] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.145336] vgaarb: loaded
[    0.145476] SCSI subsystem initialized
[    0.145521] libata version 3.00 loaded.
[    0.145600] usbcore: registered new interface driver usbfs
[    0.145615] usbcore: registered new interface driver hub
[    0.145643] usbcore: registered new device driver usb
[    0.145788] ACPI: WMI: Mapper loaded
[    0.145790] PCI: Using ACPI for IRQ routing
[    0.145913] pci 0000:06:06.0: BAR 0: address space collision on of device [0x13000000-0x13000fff]
[    0.145916] pci 0000:06:06.0: BAR 0: can't allocate resource
[    0.146062] NetLabel: Initializing
[    0.146064] NetLabel:  domain hash size = 128
[    0.146066] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.146082] NetLabel:  unlabeled traffic allowed by default
[    0.146267] hpet clockevent registered
[    0.146272] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.146279] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.146286] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.148012] Switching to clocksource tsc
[    0.150354] AppArmor: AppArmor Filesystem Enabled
[    0.150365] pnp: PnP ACPI init
[    0.150377] ACPI: bus type pnp registered
[    0.157982] pnp: PnP ACPI: found 10 devices
[    0.157985] ACPI: ACPI bus type pnp unregistered
[    0.157988] PnPBIOS: Disabled by ACPI PNP
[    0.158001] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.158005] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.158009] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.158013] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.158017] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.158021] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.158025] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.158029] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.158037] system 00:05: ioport range 0x300-0x36f has been reserved
[    0.158041] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.158045] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.158049] system 00:05: ioport range 0x1300-0x133f has been reserved
[    0.158053] system 00:05: iomem range 0xe0000000-0xefffffff has been reserved
[    0.158057] system 00:05: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.158061] system 00:05: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.158065] system 00:05: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.158069] system 00:05: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.192817] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.192821] pci 0000:00:01.0:   IO window: 0xc000-0xdfff
[    0.192826] pci 0000:00:01.0:   MEM window: 0xc0000000-0xcfffffff
[    0.192831] pci 0000:00:01.0:   PREFETCH window: 0x90000000-0x9fffffff
[    0.192837] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.192841] pci 0000:00:1c.0:   IO window: 0xa000-0xbfff
[    0.192848] pci 0000:00:1c.0:   MEM window: 0xbc000000-0xbfffffff
[    0.192854] pci 0000:00:1c.0:   PREFETCH window: 0x0000008c000000-0x0000008fffffff
[    0.192863] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.192867] pci 0000:00:1c.1:   IO window: 0x8000-0x9fff
[    0.192874] pci 0000:00:1c.1:   MEM window: 0xb8000000-0xbbffffff
[    0.192880] pci 0000:00:1c.1:   PREFETCH window: 0x00000088000000-0x0000008bffffff
[    0.192900] pci 0000:06:06.0: CardBus bridge, secondary bus 0000:07
[    0.192903] pci 0000:06:06.0:   IO window: 0x006000-0x0060ff
[    0.192909] pci 0000:06:06.0:   IO window: 0x006400-0x0064ff
[    0.192916] pci 0000:06:06.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.192922] pci 0000:06:06.0:   MEM window: 0xb4000000-0xb7ffffff
[    0.192929] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.192933] pci 0000:00:1e.0:   IO window: 0x6000-0x7fff
[    0.192940] pci 0000:00:1e.0:   MEM window: 0xb0000000-0xb7ffffff
[    0.192946] pci 0000:00:1e.0:   PREFETCH window: 0x00000080000000-0x00000087ffffff
[    0.193142] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.193146] PCI: setting IRQ 11 as level-triggered
[    0.193153] pci 0000:00:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.193159] pci 0000:00:01.0: setting latency timer to 64
[    0.193340] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    0.193343] PCI: setting IRQ 10 as level-triggered
[    0.193349] pci 0000:00:1c.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    0.193355] pci 0000:00:1c.0: setting latency timer to 64
[    0.193367] pci 0000:00:1c.1: PCI INT B -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.193373] pci 0000:00:1c.1: setting latency timer to 64
[    0.193381] pci 0000:00:1e.0: setting latency timer to 64
[    0.193563] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.193567] pci 0000:06:06.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.193576] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.193580] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.193583] pci_bus 0000:01: resource 0 io:  [0xc000-0xdfff]
[    0.193587] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xcfffffff]
[    0.193590] pci_bus 0000:01: resource 2 pref mem [0x90000000-0x9fffffff]
[    0.193594] pci_bus 0000:02: resource 0 io:  [0xa000-0xbfff]
[    0.193597] pci_bus 0000:02: resource 1 mem: [0xbc000000-0xbfffffff]
[    0.193601] pci_bus 0000:02: resource 2 pref mem [0x8c000000-0x8fffffff]
[    0.193604] pci_bus 0000:03: resource 0 io:  [0x8000-0x9fff]
[    0.193608] pci_bus 0000:03: resource 1 mem: [0xb8000000-0xbbffffff]
[    0.193611] pci_bus 0000:03: resource 2 pref mem [0x88000000-0x8bffffff]
[    0.193615] pci_bus 0000:06: resource 0 io:  [0x6000-0x7fff]
[    0.193618] pci_bus 0000:06: resource 1 mem: [0xb0000000-0xb7ffffff]
[    0.193622] pci_bus 0000:06: resource 2 pref mem [0x80000000-0x87ffffff]
[    0.193625] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.193629] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.193632] pci_bus 0000:07: resource 0 io:  [0x6000-0x60ff]
[    0.193635] pci_bus 0000:07: resource 1 io:  [0x6400-0x64ff]
[    0.193639] pci_bus 0000:07: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.193642] pci_bus 0000:07: resource 3 mem: [0xb4000000-0xb7ffffff]
[    0.193676] NET: Registered protocol family 2
[    0.193775] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.194131] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.194991] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.195540] TCP: Hash tables configured (established 131072 bind 65536)
[    0.195544] TCP reno registered
[    0.195668] NET: Registered protocol family 1
[    0.195775] pci 0000:01:00.0: Boot video device
[    0.196062] cpufreq-nforce2: No nForce2 chipset.
[    0.196092] Scanning for low memory corruption every 60 seconds
[    0.196253] audit: initializing netlink socket (disabled)
[    0.196274] type=2000 audit(1273314181.195:1): initialized
[    0.209300] Trying to unpack rootfs image as initramfs...
[    0.224346] highmem bounce pool size: 64 pages
[    0.224354] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.232321] VFS: Disk quotas dquot_6.5.2
[    0.232407] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.233172] fuse init (API version 7.13)
[    0.233280] msgmni has been set to 1690
[    0.233522] alg: No test for stdrng (krng)
[    0.233590] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.233595] io scheduler noop registered
[    0.233597] io scheduler anticipatory registered
[    0.233599] io scheduler deadline registered
[    0.233657] io scheduler cfq registered (default)
[    0.233824]   alloc irq_desc for 16 on node -1
[    0.233827]   alloc kstat_irqs on node -1
[    0.233838] pcieport 0000:00:01.0: irq 16 for MSI/MSI-X
[    0.233846] pcieport 0000:00:01.0: setting latency timer to 64
[    0.233965]   alloc irq_desc for 17 on node -1
[    0.233968]   alloc kstat_irqs on node -1
[    0.233977] pcieport 0000:00:1c.0: irq 17 for MSI/MSI-X
[    0.233988] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.234140]   alloc irq_desc for 18 on node -1
[    0.234142]   alloc kstat_irqs on node -1
[    0.234151] pcieport 0000:00:1c.1: irq 18 for MSI/MSI-X
[    0.234162] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.234278] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.234389] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.236207] ACPI: AC Adapter [AC] (on-line)
[    0.236299] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.240496] ACPI: Lid Switch [LID0]
[    0.240561] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.240565] ACPI: Power Button [PWRB]
[    0.240637] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.240640] ACPI: Power Button [PWRF]
[    0.240775] fan PNP0C0B:00: registered as cooling_device0
[    0.240782] ACPI: Fan [FAN1] (off)
[    0.241257] Marking TSC unstable due to TSC halts in idle
[    0.241303] processor LNXCPU:00: registered as cooling_device1
[    0.246712] Switching to clocksource hpet
[    0.312344] thermal LNXTHERM:01: registered as thermal_zone0
[    0.312361] ACPI: Thermal Zone [TZCR] (72 C)
[    0.320371] thermal LNXTHERM:02: registered as thermal_zone1
[    0.320385] ACPI: Thermal Zone [TZVR] (55 C)
[    0.328540] thermal LNXTHERM:03: registered as thermal_zone2
[    0.328553] ACPI: Thermal Zone [TZVL] (53 C)
[    0.336521] thermal LNXTHERM:04: registered as thermal_zone3
[    0.336534] ACPI: Thermal Zone [TZCL] (53 C)
[    0.338381] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.338545] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.339117] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[    0.339121] PCI: setting IRQ 5 as level-triggered
[    0.339128] serial 0000:00:1e.3: PCI INT B -> Link[LNKE] -> GSI 5 (level, low) -> IRQ 5
[    0.339138] serial 0000:00:1e.3: PCI INT B disabled
[    0.344685] brd: module loaded
[    0.345259] loop: module loaded
[    0.345376] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.345521] ata_piix 0000:00:1f.2: version 2.13
[    0.345740] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.345745] ata_piix 0000:00:1f.2: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.345753] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.345819] isapnp: Scanning for PnP cards...
[    0.440413] ACPI: Battery Slot [BAT1] (battery present)
[    0.500180] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.504071] scsi0 : ata_piix
[    0.504228] scsi1 : ata_piix
[    0.505482] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    0.505486] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    0.505965] Fixed MDIO Bus: probed
[    0.506012] PPP generic driver version 2.4.2
[    0.506096] tun: Universal TUN/TAP device driver, 1.6
[    0.506099] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.506214] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.506240] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
[    0.506443] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    0.506449] ehci_hcd 0000:00:1d.7: PCI INT A -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    0.506474] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.506478] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.506518] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.506556] ehci_hcd 0000:00:1d.7: debug port 1
[    0.510441] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.516237] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[    0.536208] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.536404] usb usb1: configuration #1 chosen from 1 choice
[    0.536443] hub 1-0:1.0: USB hub found
[    0.536456] hub 1-0:1.0: 8 ports detected
[    0.536561] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.536583] uhci_hcd: USB Universal Host Controller Interface driver
[    0.536649] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    0.536660] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.536665] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.536721] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.536753] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[    0.536858] usb usb2: configuration #1 chosen from 1 choice
[    0.536889] hub 2-0:1.0: USB hub found
[    0.536897] hub 2-0:1.0: 2 ports detected
[    0.536953] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.536961] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.536965] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.537006] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.537036] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001220
[    0.537137] usb usb3: configuration #1 chosen from 1 choice
[    0.537168] hub 3-0:1.0: USB hub found
[    0.537176] hub 3-0:1.0: 2 ports detected
[    0.537230] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.537238] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.537242] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.537277] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.537303] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001240
[    0.537412] usb usb4: configuration #1 chosen from 1 choice
[    0.537443] hub 4-0:1.0: USB hub found
[    0.537451] hub 4-0:1.0: 2 ports detected
[    0.537505] uhci_hcd 0000:00:1d.3: PCI INT D -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.537513] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.537517] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.537553] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.537580] uhci_hcd 0000:00:1d.3: irq 11, io base 0x00001260
[    0.537680] usb usb5: configuration #1 chosen from 1 choice
[    0.537716] hub 5-0:1.0: USB hub found
[    0.537724] hub 5-0:1.0: 2 ports detected
[    0.537843] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.541965] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.550867] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.550882] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.550933] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.550964] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.550991] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.551148] mice: PS/2 mouse device common for all mice
[    0.551328] rtc_cmos 00:06: RTC can wake from S4
[    0.551379] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.551407] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.551563] device-mapper: uevent: version 1.0.3
[    0.554067] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.598598] device-mapper: multipath: version 1.1.0 loaded
[    0.598602] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.600359] EISA: Probing bus 0 at eisa.0
[    0.600367] Cannot allocate resource for EISA slot 1
[    0.600386] Cannot allocate resource for EISA slot 6
[    0.600389] Cannot allocate resource for EISA slot 7
[    0.600391] Cannot allocate resource for EISA slot 8
[    0.600394] EISA: Detected 0 cards.
[    0.600983] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.604138] cpuidle: using governor ladder
[    0.604215] cpuidle: using governor menu
[    0.604747] TCP cubic registered
[    0.604949] NET: Registered protocol family 10
[    0.605503] lo: Disabled Privacy Extensions
[    0.605872] NET: Registered protocol family 17
[    0.606347] Using IPI No-Shortcut mode
[    0.606454] PM: Resume from disk failed.
[    0.606470] registered taskstats version 1
[    0.606900]   Magic number: 10:475:375
[    0.607020] rtc_cmos 00:06: setting system clock to 2010-05-08 10:23:02 UTC (1273314182)
[    0.607024] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.607027] EDD information not available.
[    0.700199] ata2.01: NODEV after polling detection
[    0.708574] ata2.00: ATAPI: UJDA750 DVD/CDRW, 1.60, max UDMA/33
[    0.712392] Freeing initrd memory: 7776k freed
[    0.763379] ata1.00: ATA-6: FUJITSU MHT2060AT, 0022, max UDMA/100
[    0.763386] ata1.00: 117210240 sectors, multi 16: LBA 
[    0.763403] ata1.00: applying bridge limits
[    0.763950] ata2.00: configured for UDMA/33
[    0.895102] isapnp: No Plug & Play device found
[    0.895143] ata1.00: configured for UDMA/100
[    0.895343] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    0.895583] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.895812] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    0.895871] sd 0:0:0:0: [sda] Write Protect is off
[    0.895874] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.895904] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.896217]  sda:
[    0.897131] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA750 DVD/CDRW 1.60 PQ: 0 ANSI: 5
[    0.900293] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.900297] Uniform CD-ROM driver Revision: 3.20
[    0.900412] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.900474] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.926822]  sda1 sda2 < sda5 sda6 >
[    0.965706] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.965725] Freeing unused kernel memory: 656k freed
[    0.966215] Write protecting the kernel text: 4676k
[    0.966259] Write protecting the kernel read-only data: 1840k
[    1.000504] udev: starting version 151
[    1.136081] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.245590] sky2 driver version 1.25
[    1.245643] sky2 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.245661] sky2 0000:02:00.0: setting latency timer to 64
[    1.245693] sky2 0000:02:00.0: Yukon-2 EC chip revision 1
[    1.245802]   alloc irq_desc for 19 on node -1
[    1.245804]   alloc kstat_irqs on node -1
[    1.245822] sky2 0000:02:00.0: irq 19 for MSI/MSI-X
[    1.312956] usb 2-1: configuration #1 chosen from 1 choice
[    1.334116] usbcore: registered new interface driver hiddev
[    1.344032] sky2 0000:02:00.0: No interrupt generated using MSI, switching to INTx mode.
[    1.344762] sky2 eth0: addr 00:a0:d1:bc:49:3f
[    1.347320] input: Genius NetScroll + Mini Traveler as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input5
[    1.347570] generic-usb 0003:0458:0036.0001: input,hidraw0: USB HID v1.10 Mouse [Genius NetScroll + Mini Traveler] on usb-0000:00:1d.0-1/input0
[    1.347602] usbcore: registered new interface driver usbhid
[    1.347702] usbhid: v2.6:USB HID core driver
[    1.625113] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    8.537151] udev: starting version 151
[    8.580777] Adding 1084348k swap on /dev/sda6.  Priority:-1 extents:1 across:1084348k 
[    8.928427] type=1505 audit(1273314190.821:2):  operation="profile_load" pid=455 name="/sbin/dhclient3"
[    8.929176] type=1505 audit(1273314190.821:3):  operation="profile_load" pid=455 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    8.929579] type=1505 audit(1273314190.821:4):  operation="profile_load" pid=455 name="/usr/lib/connman/scripts/dhclient-script"
[   10.121151] lp: driver loaded but no devices found
[   10.235944] lib80211: common routines for IEEE802.11 drivers
[   10.235949] lib80211_crypt: registered algorithm 'NULL'
[   10.669513] irda_init()
[   10.669528] NET: Registered protocol family 23
[   10.681180] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   10.681184] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   10.710565] sdhci: Secure Digital Host Controller Interface driver
[   10.710570] sdhci: Copyright(c) Pierre Ossman
[   10.712474] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
[   10.712850] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input6
[   10.713016] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   10.714533] intel_rng: FWH not detected
[   10.721113] Linux agpgart interface v0.103
[   10.817574] sdhci-pci 0000:06:06.4: SDHCI controller found [104c:8034] (rev 0)
[   10.817602] sdhci-pci 0000:06:06.4: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.817747] Registered led device: mmc0::
[   10.817853] mmc0: SDHCI controller on PCI [0000:06:06.4] using PIO
[   10.817966] Registered led device: mmc1::
[   10.818056] mmc1: SDHCI controller on PCI [0000:06:06.4] using PIO
[   10.818159] Registered led device: mmc2::
[   10.818257] mmc2: SDHCI controller on PCI [0000:06:06.4] using PIO
[   10.824218] tifm_7xx1 0000:06:06.3: PCI INT D -> Link[LNKE] -> GSI 5 (level, low) -> IRQ 5
[   10.847587] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   10.847591] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   10.847672] ipw2200 0000:06:04.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   10.847980] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   10.848103] ipw2200 0000:06:04.0: firmware: requesting ipw2200-bss.fw
[   11.193580] ipw2200: Radio Frequency Kill Switch is On:
[   11.193582] Kill switch must be turned off for wireless networking to work.
[   11.206070] [drm] Initialized drm 1.1.0 20060810
[   11.228812] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   11.228867] yenta_cardbus 0000:06:06.0: CardBus bridge found [1179:ff10]
[   11.228892] yenta_cardbus 0000:06:06.0: Enabling burst memory read transactions
[   11.228898] yenta_cardbus 0000:06:06.0: Using CSCINT to route CSC interrupts to PCI
[   11.228902] yenta_cardbus 0000:06:06.0: Routing CardBus interrupts to PCI
[   11.228909] yenta_cardbus 0000:06:06.0: TI: mfunc 0x01aa1b22, devctl 0x66
[   11.460481] yenta_cardbus 0000:06:06.0: ISA IRQ mask 0x00d8, PCI irq 11
[   11.460487] yenta_cardbus 0000:06:06.0: Socket status: 30000006
[   11.460493] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[   11.460504] yenta_cardbus 0000:06:06.0: pcmcia: parent PCI bridge I/O window: 0x6000 - 0x7fff
[   11.460509] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x6000-0x7fff: clean.
[   11.460987] yenta_cardbus 0000:06:06.0: pcmcia: parent PCI bridge Memory window: 0xb0000000 - 0xb7ffffff
[   11.460991] yenta_cardbus 0000:06:06.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x87ffffff
[   11.507671] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[   11.566991] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   11.736615] [drm] VGACON disable radeon kernel modesetting.
[   11.736771] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.736778] pci 0000:01:00.0: setting latency timer to 64
[   11.737065] [drm] Initialized radeon 1.32.0 20080528 for 0000:01:00.0 on minor 0
[   11.826256] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   11.950048] vga16fb: initializing
[   11.950054] vga16fb: mapped to 0xc00a0000
[   11.950213] fb0: VGA16 VGA frame buffer device
[   12.253900] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x118-0x11f
[   12.255346] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   12.256230] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.256839] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.257626] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.433190] Console: switching to colour frame buffer device 80x30
[   13.328030] Intel ICH 0000:00:1e.2: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   13.328065] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   14.264026] type=1505 audit(1273314196.152:5):  operation="profile_load" pid=719 name="/usr/share/gdm/guest-session/Xsession"
[   14.266092] type=1505 audit(1273314196.156:6):  operation="profile_replace" pid=721 name="/sbin/dhclient3"
[   14.266855] type=1505 audit(1273314196.156:7):  operation="profile_replace" pid=721 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.267265] type=1505 audit(1273314196.156:8):  operation="profile_replace" pid=721 name="/usr/lib/connman/scripts/dhclient-script"
[   14.429320] type=1505 audit(1273314196.320:9):  operation="profile_load" pid=722 name="/usr/bin/evince"
[   14.439717] type=1505 audit(1273314196.328:10):  operation="profile_load" pid=722 name="/usr/bin/evince-previewer"
[   14.445805] type=1505 audit(1273314196.336:11):  operation="profile_load" pid=722 name="/usr/bin/evince-thumbnailer"
[   14.514288] type=1505 audit(1273314196.404:12):  operation="profile_load" pid=727 name="/usr/bin/freshclam"
[   14.750457] type=1505 audit(1273314196.641:13):  operation="profile_load" pid=733 name="/usr/lib/cups/backend/cups-pdf"
[   14.751372] type=1505 audit(1273314196.641:14):  operation="profile_load" pid=733 name="/usr/sbin/cupsd"
[   17.260893] apm: BIOS not found.
[   21.177183] sky2 eth0: enabling interface
[   21.177724] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.861044] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   22.861287] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   26.407343] [drm] Setting GART location based on new memory map
[   26.409360] [drm] Loading R300 Microcode
[   26.410016] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   26.489712] [drm] Num pipes: 1
[   26.489723] [drm] writeback test succeeded in 1 usecs
[   40.369344] spurious 8259A interrupt: IRQ7.

Sorry about the long post, if someone can advise on how to insert the text into scroll boxes I will correct.
 
So basically the card is not being recognised at aplay -l, nothings muted, I'm on the latest alsa version and I can't see what has changed to break this!

I suspect I need to blacklist something which is interfering with the onboard sound card, maybe the onboard modem but this is more a jedi like feeling than cold hard logic! 

Suggestions please guys?

---

### Post by lidex on 2010-05-08
First - discover code tags!
Second - your alsa install is borked. Follow the directions in the thread you'll find in the alsa-upgrade-script link in my sig.

---

### Post by debaser4 on 2010-05-09
Ran the upgrade instructions. No dice. Any other ideas?

```
debaser@debaser-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on May  9 2010 for kernel 2.6.32-22-generic (SMP).
debaser@debaser-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
```

ps Code Tags...ahhhh...advanced responses not quick replies!

---

### Post by lidex on 2010-05-10
Yeah, not cool. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by ram130 on 2010-05-13
Having the same problem since I upgraded to this new kernel. I did as you requested here is my info [http://www.alsa-project.org/db/?f=4328c50b6af2bdcbb1f759d64507483a1bf31166](http://www.alsa-project.org/db/?f=4328c50b6af2bdcbb1f759d64507483a1bf31166)

---

### Post by debaser4 on 2010-05-13
Lidex, here is my info: [http://www.alsa-project.org/db/?f=aa1e995ebf9185a5119574403bd84d0fed1c261]("http://www.alsa-project.org/db/?f=aa1e995ebf9185a5119574403bd84d0fed1c2615")5

Just wondering if there is anything I could check when booting into a earlier grub version that works on same laptop? I guess the only difference will be the kernel as per ram130's comment but could run the script in that session if would help anyone?

Otherwise I'm wondering if this is a 9.10 to 10.04 path problem and if a clean 10.04 install would clean up. I mean, that should be unnecessary right? As this is a family machine, I want to keep it familiar and don't really want to put Arch on it like my other laptop.

Thank you for looking at this.:)

---

### Post by lidex on 2010-05-13
Upgrade, eh? Go here and do 'Part A':
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Then try the upgrade script again - it's up to 1.0.23

---

### Post by ram130 on 2010-05-14
Yea I did so because I was having flash player problems(high cpu usage)...either I switch back to the default kernel so Im ok again.:guitar:

---

### Post by debaser4 on 2010-05-14
After running all section A in the other post and upgrading to 1.0.23 still no luck

```
debaser@debaser-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 14 2010 for kernel 2.6.32-22-generic (SMP).
debaser@debaser-laptop:~$ aplay -l
aplay: device_list:235: no soundcards found...
```

This is not good :(

Any more ideas please anyone? Please not I am on a course for a week soon; so if I don't post don't think I'm leaving this, I will read answers and respond when I can!

---

### Post by ram130 on 2010-05-14
> **debaser4 said:**
> After running all section A in the other post and upgrading to 1.0.23 still no luck

```
debaser@debaser-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 14 2010 for kernel 2.6.32-22-generic (SMP).
debaser@debaser-laptop:~$ aplay -l
aplay: device_list:235: no soundcards found...
```

This is not good :(

Any more ideas please anyone? Please not I am on a course for a week soon; so if I don't post don't think I'm leaving this, I will read answers and respond when I can!

Yea switch back to the default kernel or reinstall. You can boot the live cd too and see if that picks any thing up.

---

### Post by lidex on 2010-05-14
What's the deal with this modprobe option:
```
snd-intel8x0: ac97_clock=48000

```
Perhaps you should disable/remove that. What happens with this command:
```
sudo modprobe snd_intel8x0
```

---

### Post by debaser4 on 2010-05-24
> **lidex said:**
> What's the deal with this modprobe option:
```
snd-intel8x0: ac97_clock=48000

```
Perhaps you should disable/remove that. What happens with this command:
```
sudo modprobe snd_intel8x0
```

I get:
```
debaser@debaser-laptop:~$ sudo modprobe snd_intel8x0
[sudo] password for debaser: 
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.

```

The terminal hangs.

Contents of /etc/modprobe.d/sound (just rem'd clock line):

no 2.2.2               File: sound                                      

alias snd-card-0 snd-intel8x0
alias sound-slot-0 snd-intel8x0
# options snd-intel8x0 ac97_clock=48000
options snd slots=snd-intel8x0
# CvwD.FAMlirE10w6:82801AA AC'97 Audio Controller
alias snd-card-0 snd-intel8x0

---

### Post by lidex on 2010-05-25
Try removing that sound file (/etc/modprobe.d/sound) and reboot.

---

### Post by debaser4 on 2010-06-03
Tried that Lidex, no difference.
 
I find it totally worrying an everyday update can do this. I guess you just have to accept that once in a while linux can bork like any other OS.
 
I am now using the latest Lubuntu and everything is fine on the same kernel version. The laptop is 5 years old now but flies now compared to Gnome.
 
I think more people will be attracted to LXDE now XFCE has got as memory heavy as Gnome (and KDE). Lubuntu is not quite as rapid as Arch but worth it for the ease of .deb.
 
Thanks to those who tried to help. Travel well. 
 
:)

---

### Post by 0olong on 2010-06-08
Very similar problem, and I seem to have the same (disappearing) sound card. However, with me it seems to have followed on from removing PulseAudio altogether and then reinstalling, in the vain hopes of getting sound input (which had inexplicably stopped working several months before) to work again. Of course, it might have vanished anyway for all I know.

My output from your script looks like this:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Tue Jun  8 14:33:28 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      MICRO-STAR INC.
Product Name:      MS-6728


!!Kernel Information
!!------------------

Kernel release:    2.6.32-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.23
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:24d5 (rev 02)
	Subsystem: 1462:7585


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 3 Jun  8 14:01 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Jun  8 14:01 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
radeon
ttm
drm_kms_helper
ppdev
ftdi_sio
snd
drm
usbserial
soundcore
i2c_algo_bit
parport_pc
intel_agp
snd_page_alloc
psmouse
serio_raw
shpchp
agpgart
lp
parport
usb_storage
usbhid
hid
r8169
mii
floppy


!!ALSA/HDA dmesg
!!------------------


```

...but for me sudo modprobe snd_intel8x0 gives:
```
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.32-22-generic/kernel/sound/modules/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Any ideas?

---

