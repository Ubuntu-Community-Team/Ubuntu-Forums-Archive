---
title: "Sound is dead"
date: 2012-10-03
forum: Multimedia Software
---

### Post by Farinet on 2012-10-03
Since a couple of days sound is completely dead on my Samsung NP150 running lubuntu 12.04. I purged either oss or alsa or pulseaudio completely and reinstalled then first alsa. And since that did not have any effect i reinstalled pulseaudio too. No effect either.

At this point, i'm clueless. I followed a bit several discussions but i did not find something that seems to match my case. Anyway on the german ubuntu wiki i found an instruction what informations are needed to do an effective diagnosis and so i did. The results are here:


```
meinname@Samsung-N150P:~$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS
meinname@Samsung-N150P:~$ uname -r
3.2.0-32-generic
meinname@Samsung-N150P:~$ grep "^audio" /etc/group | grep "$USER" | wc -l 
1
meinname@Samsung-N150P:~$ lspci -nnk | grep -iA2 audio 
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c072]
    Kernel driver in use: oss_hdaudio
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
meinname@Samsung-N150P:~$ lsmod | grep "snd" 
snd                    62064  0 
soundcore              14635  1 snd
meinname@Samsung-N150P:~$ cat /proc/asound/cards
--- no soundcards ---
meinname@Samsung-N150P:~$ head -n 3 /proc/asound/card0/codec#0 
head: »/proc/asound/card0/codec#0“ kann nicht zum Lesen geöffnet werden: Datei oder Verzeichnis nicht gefunden
meinname@Samsung-N150P:~$ head -n 3 /proc/asound/card0/codec97#0/ac97#0-0
head: »/proc/asound/card0/codec97#0/ac97#0-0“ kann nicht zum Lesen geöffnet werden: Datei oder Verzeichnis nicht gefunden
meinname@Samsung-N150P:~$ head -n 3 /proc/asound/card0/codec97#0/ac97#0-0+regs head: »/proc/asound/card0/codec97#0/ac97#0-0+regs“ kann nicht zum Lesen geöffnet werden: Datei oder Verzeichnis nicht gefunden
meinname@Samsung-N150P:~$ aplay -l
aplay: device_list:252: keine Soundkarten gefunden ...
meinname@Samsung-N150P:~$ aplay /usr/share/sounds/startup.wav 
/usr/share/sounds/startup.wav: Datei oder Verzeichnis nicht gefunden
meinname@Samsung-N150P:~$ asoundconf list 
asoundconf: Befehl nicht gefunden.
meinname@Samsung-N150P:~$ cat ~/.asoundrc 
cat: /home/meinname/.asoundrc: Datei oder Verzeichnis nicht gefunden
meinname@Samsung-N150P:~$ cat ~/.asoundrc.asoundconf 
cat: /home/meinname/.asoundrc.asoundconf: Datei oder Verzeichnis nicht gefunden
meinname@Samsung-N150P:~$ ps -C esd 
  PID TTY          TIME CMD
meinname@Samsung-N150P:~$ ps -C arts 
  PID TTY          TIME CMD
meinname@Samsung-N150P:~$ ps -C pulseaudio 
  PID TTY          TIME CMD
 1553 ?        00:00:00 pulseaudio
meinname@Samsung-N150P:~$ dmesg 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-32-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #51-Ubuntu SMP Wed Sep 26 21:32:50 UTC 2012 (Ubuntu 3.2.0-32.51-generic 3.2.30)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5b0000 (usable)
[    0.000000]  BIOS-e820: 000000007f5b0000 - 000000007f5c0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f5c0000 - 000000007f5c3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f5c3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: SAMSUNG ELECTRONICS CO., LTD. N150P/N210P/N220P          /N150P/N210P/N220P          , BIOS 01KY.M008.20100430.RHU 04/30/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f5b0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F600000 mask 0FFE00000 uncachable
[    0.000000]   2 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2038MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] total RAM covered: 2038M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2038MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [c00f7dd0] f7dd0
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35a1a000 - 36d05000
[    0.000000] ACPI: RSDP 000f7da0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7f5b8d8d 0006C (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7f5bfc92 000F4 (v03 INTEL           06040000 PTL  00000002)
[    0.000000] ACPI: DSDT 7f5b9ff5 05BA9 (v01  INTEL BEARG31A 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS 7f5c2fc0 00040
[    0.000000] ACPI: MCFG 7f5bfd86 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 7f5bfdc2 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC 7f5bfdfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7f5bfe62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7f5bfe8a 00176 (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 7f5b9395 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b92ef 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b8df9 004F6 (v02  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1149MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f5b0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007f5b0
[    0.000000] On node 0 totalpages: 521533
[    0.000000] free_area_init_node: node 0, pgdat c1824ec0, node_mem_map f4a2a200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2300 pages used for memmap
[    0.000000]   HighMem zone: 292022 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
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
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77d7000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517457
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic root=UUID=377fef90-2aa9-4dc0-be0e-462f3c3db05a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8346112 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f5b0)
[    0.000000] Memory: 2031308k/2086592k available (5620k kernel code, 54824k reserved, 2768k data, 712k init, 1177288k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1832000 - 0xc18e4000   ( 712 kB)
[    0.000000]       .data : 0xc157d344 - 0xc18315c0   (2768 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157d344   (5620 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.410 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.82 BogoMIPS (lpj=6649640)
[    0.004016] pid_max: default: 32768 minimum: 301
[    0.004066] Security Framework initialized
[    0.004104] AppArmor: AppArmor initialized
[    0.004109] Yama: becoming mindful.
[    0.004230] Mount-cache hash table entries: 512
[    0.004496] Initializing cgroup subsys cpuacct
[    0.004511] Initializing cgroup subsys memory
[    0.004529] Initializing cgroup subsys devices
[    0.004535] Initializing cgroup subsys freezer
[    0.004540] Initializing cgroup subsys blkio
[    0.004556] Initializing cgroup subsys perf_event
[    0.004605] CPU: Physical Processor ID: 0
[    0.004610] CPU: Processor Core ID: 0
[    0.004617] mce: CPU supports 5 MCE banks
[    0.004629] CPU0: Thermal monitoring handled by SMI
[    0.004637] using mwait in idle threads.
[    0.010852] ACPI: Core revision 20110623
[    0.020029] ftrace: allocating 25910 entries in 51 pages
[    0.028096] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028604] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070327] CPU0: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.072003] APIC calibration not consistent with PM-Timer: 291ms instead of 100ms
[    0.072003] APIC delta adjusted to PM-Timer: 1039062 (3034019)
[    0.072003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.072003] ... version:                3
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] CPU 1 irqstacks, hard=f44ea000 soft=f44ec000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.072003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.008000] CPU0: Thermal monitoring enabled (TM1)
[    0.160063] NMI watchdog enabled, takes one hw-pmu counter.
[    0.160150] Brought up 2 CPUs
[    0.160158] Total of 2 processors activated (6649.82 BogoMIPS).
[    0.160719] devtmpfs: initialized
[    0.160719] EVM: security.selinux
[    0.160719] EVM: security.SMACK64
[    0.160719] EVM: security.capability
[    0.160719] PM: Registering ACPI NVS region at 7f5c0000 (12288 bytes)
[    0.164427] print_constraints: dummy: 
[    0.164480] RTC time: 16:06:51, date: 10/02/12
[    0.164567] NET: Registered protocol family 16
[    0.164698] Trying to unpack rootfs image as initramfs...
[    0.164992] EISA bus registered
[    0.165087] ACPI: bus type pci registered
[    0.165278] PCI: MMCONFIG for domain 0000 [bus 00-10] at [mem 0xe0000000-0xe10fffff] (base 0xe0000000)
[    0.165290] PCI: MMCONFIG at [mem 0xe0000000-0xe10fffff] reserved in E820
[    0.165297] PCI: Using MMCONFIG for extended config space
[    0.165304] PCI: Using configuration type 1 for base access
[    0.180230] bio: create slab <bio-0> at 0
[    0.180566] ACPI: Added _OSI(Module Device)
[    0.180576] ACPI: Added _OSI(Processor Device)
[    0.180583] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.180591] ACPI: Added _OSI(Processor Aggregator Device)
[    0.183916] ACPI: EC: Look up EC in DSDT
[    0.197513] ACPI: SSDT 7f5b9d1e 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.198374] ACPI: Dynamic OEM Table Load:
[    0.198387] ACPI: SSDT   (null) 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.198907] ACPI: SSDT 7f5b95f4 006A5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.199723] ACPI: Dynamic OEM Table Load:
[    0.199735] ACPI: SSDT   (null) 006A5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.200719] ACPI: SSDT 7f5b9f21 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.201557] ACPI: Dynamic OEM Table Load:
[    0.201569] ACPI: SSDT   (null) 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.201911] ACPI: SSDT 7f5b9c99 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.202714] ACPI: Dynamic OEM Table Load:
[    0.202725] ACPI: SSDT   (null) 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.204587] ACPI: Interpreter enabled
[    0.204621] ACPI: (supports S0 S3 S4 S5)
[    0.204677] ACPI: Using IOAPIC for interrupt routing
[    0.217744] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.220111] ACPI: No dock devices found.
[    0.220120] HEST: Table not found.
[    0.220136] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.222557] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.222583] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4420e88), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.222611] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.222634] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.227035] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.227049] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.227061] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.227070] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.227081] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.227091] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.227102] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xf7ffffff]
[    0.227112] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xfdff]
[    0.227152] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.227240] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.227264] pci 0000:00:02.0: reg 10: [mem 0xf0300000-0xf037ffff]
[    0.227279] pci 0000:00:02.0: reg 14: [io  0x18d0-0x18d7]
[    0.227294] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.227309] pci 0000:00:02.0: reg 1c: [mem 0xf0000000-0xf00fffff]
[    0.227378] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.227398] pci 0000:00:02.1: reg 10: [mem 0xf0380000-0xf03fffff]
[    0.227552] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.227590] pci 0000:00:1b.0: reg 10: [mem 0xf0400000-0xf0403fff 64bit]
[    0.227734] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.227747] pci 0000:00:1b.0: PME# disabled
[    0.227795] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.227956] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.227968] pci 0000:00:1c.0: PME# disabled
[    0.228044] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.228200] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.228212] pci 0000:00:1c.1: PME# disabled
[    0.228264] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.228416] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.228427] pci 0000:00:1c.2: PME# disabled
[    0.228479] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.228630] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.228642] pci 0000:00:1c.3: PME# disabled
[    0.228699] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.228782] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.228852] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.228932] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.228998] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.229077] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.229144] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.229223] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.229305] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.229344] pci 0000:00:1d.7: reg 10: [mem 0xf0604000-0xf06043ff]
[    0.229493] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.229507] pci 0000:00:1d.7: PME# disabled
[    0.229559] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.229698] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.229821] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    0.229907] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.229946] pci 0000:00:1f.2: reg 10: [io  0x18e8-0x18ef]
[    0.229967] pci 0000:00:1f.2: reg 14: [io  0x18dc-0x18df]
[    0.229989] pci 0000:00:1f.2: reg 18: [io  0x18e0-0x18e7]
[    0.230010] pci 0000:00:1f.2: reg 1c: [io  0x18d8-0x18db]
[    0.230031] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18cf]
[    0.230052] pci 0000:00:1f.2: reg 24: [mem 0xf0604400-0xf06047ff]
[    0.230136] pci 0000:00:1f.2: PME# supported from D3hot
[    0.230148] pci 0000:00:1f.2: PME# disabled
[    0.230183] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.230266] pci 0000:00:1f.3: reg 20: [io  0x18a0-0x18bf]
[    0.230486] pci 0000:05:00.0: [14e4:4727] type 0 class 0x000280
[    0.230538] pci 0000:05:00.0: reg 10: [mem 0xf0100000-0xf0103fff 64bit]
[    0.230741] pci 0000:05:00.0: supports D1 D2
[    0.230749] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.230762] pci 0000:05:00.0: PME# disabled
[    0.236107] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.236127] pci 0000:00:1c.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.236232] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.236522] pci 0000:09:00.0: [11ab:4354] type 0 class 0x000200
[    0.236737] pci 0000:09:00.0: reg 10: [mem 0xf0200000-0xf0203fff 64bit]
[    0.236843] pci 0000:09:00.0: reg 18: [io  0x2000-0x20ff]
[    0.237676] pci 0000:09:00.0: supports D1 D2
[    0.237685] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.237721] pci 0000:09:00.0: PME# disabled
[    0.238040] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.238054] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.238067] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.238166] pci 0000:00:1c.3: PCI bridge to [bus 0b-0b]
[    0.238300] pci 0000:00:1e.0: PCI bridge to [bus 11-11] (subtractive decode)
[    0.238325] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.238336] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.238346] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.238356] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.238366] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.238376] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.238386] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xf7ffffff] (subtractive decode)
[    0.238396] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xfdff] (subtractive decode)
[    0.238447] pci_bus 0000:00: on NUMA node 0
[    0.238463] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.238746] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.238896] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.239032] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.239174] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.239311] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.239758] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.239781] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4420e88), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.239820]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.240039] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.240060] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4420e88), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.240096]  pci0000:00: ACPI _OSC request failed (AE_ALREADY_EXISTS), returned control mask: 0x1d
[    0.240104] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.253563] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.253754] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.253926] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.254097] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.254293] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.254490] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.254675] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.254867] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.255247] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.255279] vgaarb: loaded
[    0.255284] vgaarb: bridge control possible 0000:00:02.0
[    0.255716] i2c-core: driver [aat2870] using legacy suspend method
[    0.255724] i2c-core: driver [aat2870] using legacy resume method
[    0.255977] SCSI subsystem initialized
[    0.256157] libata version 3.00 loaded.
[    0.256312] usbcore: registered new interface driver usbfs
[    0.256358] usbcore: registered new interface driver hub
[    0.256460] usbcore: registered new device driver usb
[    0.256791] PCI: Using ACPI for IRQ routing
[    0.257322] PCI: pci_cache_line_size set to 64 bytes
[    0.257542] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.257552] reserve RAM buffer: 000000007f5b0000 - 000000007fffffff 
[    0.257871] NetLabel: Initializing
[    0.257879] NetLabel:  domain hash size = 128
[    0.257884] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.257914] NetLabel:  unlabeled traffic allowed by default
[    0.258104] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.258118] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.258134] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.268184] Switching to clocksource hpet
[    0.291910] AppArmor: AppArmor Filesystem Enabled
[    0.291991] pnp: PnP ACPI init
[    0.292096] ACPI: bus type pnp registered
[    0.294248] pnp 00:00: [bus 00-3f]
[    0.294258] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.294267] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.294276] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.294285] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.294294] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.294303] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.294311] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.294320] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.294329] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.294338] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.294346] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.294355] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.294364] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.294372] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.294381] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.294390] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.294405] pnp 00:00: [mem 0x80000000-0xf7ffffff window]
[    0.294414] pnp 00:00: [io  0x0d00-0xfdff window]
[    0.294422] pnp 00:00: [mem 0x00000000 window]
[    0.294431] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.294627] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.295694] pnp 00:01: [io  0x0010-0x001f]
[    0.295705] pnp 00:01: [io  0x0024-0x0025]
[    0.295713] pnp 00:01: [io  0x0028-0x0029]
[    0.295721] pnp 00:01: [io  0x002c-0x002d]
[    0.295728] pnp 00:01: [io  0x0030-0x0031]
[    0.295736] pnp 00:01: [io  0x0034-0x0035]
[    0.295743] pnp 00:01: [io  0x0038-0x0039]
[    0.295751] pnp 00:01: [io  0x003c-0x003d]
[    0.295758] pnp 00:01: [io  0x0072-0x0077]
[    0.295765] pnp 00:01: [io  0x0080]
[    0.295772] pnp 00:01: [io  0x0090-0x009f]
[    0.295779] pnp 00:01: [io  0x00a4-0x00a5]
[    0.295787] pnp 00:01: [io  0x00a8-0x00a9]
[    0.295794] pnp 00:01: [io  0x00ac-0x00ad]
[    0.295801] pnp 00:01: [io  0x00b0-0x00b5]
[    0.295809] pnp 00:01: [io  0x00b8-0x00b9]
[    0.295816] pnp 00:01: [io  0x00bc-0x00bd]
[    0.295824] pnp 00:01: [io  0x0800-0x080f]
[    0.295832] pnp 00:01: [io  0x1000-0x107f]
[    0.295839] pnp 00:01: [io  0x1180-0x11bf]
[    0.295847] pnp 00:01: [io  0x002e-0x002f]
[    0.295855] pnp 00:01: [io  0x04d0-0x04d1]
[    0.295862] pnp 00:01: [io  0xfe00]
[    0.295869] pnp 00:01: [io  0x164e-0x174c]
[    0.295877] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.295886] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.295894] pnp 00:01: [mem 0xf8000000-0xfbffffff]
[    0.295902] pnp 00:01: [mem 0xfef00000-0xfeffffff]
[    0.296179] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.296191] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.296202] system 00:01: [io  0x1180-0x11bf] has been reserved
[    0.296212] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.296222] system 00:01: [io  0xfe00] has been reserved
[    0.296231] system 00:01: [io  0x164e-0x174c] has been reserved
[    0.296243] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.296253] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.296264] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.296274] system 00:01: [mem 0xfef00000-0xfeffffff] has been reserved
[    0.296287] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.296328] pnp 00:02: [io  0x0000-0x000f]
[    0.296337] pnp 00:02: [io  0x0081-0x008f]
[    0.296345] pnp 00:02: [io  0x00c0-0x00df]
[    0.296354] pnp 00:02: [dma 4]
[    0.296467] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.296507] pnp 00:03: [io  0x00f0-0x00fe]
[    0.296533] pnp 00:03: [irq 13]
[    0.296646] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.296768] pnp 00:04: [io  0x0070-0x0071]
[    0.296786] pnp 00:04: [irq 8]
[    0.296890] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.296925] pnp 00:05: [io  0x0061]
[    0.297027] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.297110] pnp 00:06: [io  0x0060]
[    0.297118] pnp 00:06: [io  0x0064]
[    0.297135] pnp 00:06: [irq 1]
[    0.297247] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.297295] pnp 00:07: [irq 12]
[    0.297411] pnp 00:07: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.297833] pnp 00:08: [mem 0xff800000-0xffffffff]
[    0.297957] pnp 00:08: Plug and Play ACPI device, IDs INT0800 (active)
[    0.298478] pnp: PnP ACPI: found 9 devices
[    0.298487] ACPI: ACPI bus type pnp unregistered
[    0.298497] PnPBIOS: Disabled by ACPI PNP
[    0.340129] PCI: max bus depth: 1 pci_try_num: 2
[    0.340241] pci 0000:00:1c.3: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.340257] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.340273] pci 0000:00:1c.3: BAR 13: assigned [io  0x3000-0x3fff]
[    0.340288] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.340303] pci 0000:00:1c.1: BAR 14: assigned [mem 0x80600000-0x807fffff]
[    0.340318] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80800000-0x809fffff 64bit pref]
[    0.340332] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.340345] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.340358] pci 0000:00:1c.0: BAR 13: assigned [io  0x5000-0x5fff]
[    0.340369] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.340379] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.340394] pci 0000:00:1c.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.340406] pci 0000:00:1c.0:   bridge window [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.340423] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.340433] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.340447] pci 0000:00:1c.1:   bridge window [mem 0x80600000-0x807fffff]
[    0.340459] pci 0000:00:1c.1:   bridge window [mem 0x80800000-0x809fffff 64bit pref]
[    0.340477] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.340487] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.340501] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.340513] pci 0000:00:1c.2:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.340530] pci 0000:00:1c.3: PCI bridge to [bus 0b-0b]
[    0.340540] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.340554] pci 0000:00:1c.3:   bridge window [mem 0x80000000-0x801fffff]
[    0.340566] pci 0000:00:1c.3:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.340583] pci 0000:00:1e.0: PCI bridge to [bus 11-11]
[    0.340648] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.340662] pci 0000:00:1c.0: setting latency timer to 64
[    0.340680] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.340703] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.340717] pci 0000:00:1c.1: setting latency timer to 64
[    0.340746] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.340758] pci 0000:00:1c.2: setting latency timer to 64
[    0.340775] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.340797] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.340811] pci 0000:00:1c.3: setting latency timer to 64
[    0.340829] pci 0000:00:1e.0: setting latency timer to 64
[    0.340840] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.340849] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.340858] pci_bus 0000:00: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.340868] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.340877] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.340886] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.340895] pci_bus 0000:00: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.340904] pci_bus 0000:00: resource 11 [io  0x0d00-0xfdff]
[    0.340913] pci_bus 0000:05: resource 0 [io  0x5000-0x5fff]
[    0.340922] pci_bus 0000:05: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.340931] pci_bus 0000:05: resource 2 [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.340941] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    0.340950] pci_bus 0000:07: resource 1 [mem 0x80600000-0x807fffff]
[    0.340959] pci_bus 0000:07: resource 2 [mem 0x80800000-0x809fffff 64bit pref]
[    0.340969] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    0.340978] pci_bus 0000:09: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.340987] pci_bus 0000:09: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.340996] pci_bus 0000:0b: resource 0 [io  0x3000-0x3fff]
[    0.341005] pci_bus 0000:0b: resource 1 [mem 0x80000000-0x801fffff]
[    0.341015] pci_bus 0000:0b: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.341025] pci_bus 0000:11: resource 4 [io  0x0000-0x0cf7]
[    0.341033] pci_bus 0000:11: resource 5 [mem 0x000a0000-0x000bffff]
[    0.341042] pci_bus 0000:11: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.341051] pci_bus 0000:11: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.341060] pci_bus 0000:11: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.341069] pci_bus 0000:11: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.341079] pci_bus 0000:11: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.341088] pci_bus 0000:11: resource 11 [io  0x0d00-0xfdff]
[    0.341200] NET: Registered protocol family 2
[    0.341381] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.342020] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.343117] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.343657] TCP: Hash tables configured (established 131072 bind 65536)
[    0.343665] TCP reno registered
[    0.343677] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.343701] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.343978] NET: Registered protocol family 1
[    0.344077] pci 0000:00:02.0: Boot video device
[    0.344158] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.344188] pci 0000:00:1d.0: PCI INT A disabled
[    0.344210] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.344237] pci 0000:00:1d.1: PCI INT B disabled
[    0.344258] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.344285] pci 0000:00:1d.2: PCI INT C disabled
[    0.344305] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.344332] pci 0000:00:1d.3: PCI INT D disabled
[    0.344355] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.344403] pci 0000:00:1d.7: PCI INT A disabled
[    0.344494] PCI: CLS 32 bytes, default 64
[    0.344507] Simple Boot Flag at 0x36 set to 0x1
[    0.345585] audit: initializing netlink socket (disabled)
[    0.345612] type=2000 audit(1349194010.340:1): initialized
[    0.403566] highmem bounce pool size: 64 pages
[    0.403586] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.410456] VFS: Disk quotas dquot_6.5.2
[    0.410660] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.412645] fuse init (API version 7.17)
[    0.412986] msgmni has been set to 1668
[    0.414136] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.414235] io scheduler noop registered
[    0.414243] io scheduler deadline registered
[    0.414270] io scheduler cfq registered (default)
[    0.414632] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.414728] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.414884] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.414967] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.415123] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.415208] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.415373] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.415456] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.415692] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.415775] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.416046] intel_idle: MWAIT substates: 0x20220
[    0.416063] intel_idle: v0.4 model 0x1C
[    0.416069] intel_idle: lapic_timer_reliable_states 0x2
[    0.416077] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.416499] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.416874] ACPI: AC Adapter [ADP1] (off-line)
[    0.417409] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.417578] ACPI: Lid Switch [LID0]
[    0.417731] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.417747] ACPI: Power Button [PWRB]
[    0.417902] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.417916] ACPI: Sleep Button [SLPB]
[    0.418068] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.418081] ACPI: Power Button [PWRF]
[    0.430380] thermal LNXTHERM:00: registered as thermal_zone0
[    0.430390] ACPI: Thermal Zone [TZ00] (45 C)
[    0.430466] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.430503] ACPI: Battery Slot [BAT1] (battery present)
[    0.430666] ERST: Table is not found!
[    0.430673] GHES: HEST is not enabled!
[    0.430906] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.441168] isapnp: Scanning for PnP cards...
[    0.447388] ACPI: Battery Slot [BAT1] (battery present)
[    0.796190] isapnp: No Plug & Play device found
[    1.182673] Freeing initrd memory: 19372k freed
[    1.233045] Linux agpgart interface v0.103
[    1.233218] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.233420] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.233686] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.233936] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.238018] brd: module loaded
[    1.240226] loop: module loaded
[    1.240504] ahci 0000:00:1f.2: version 3.0
[    1.240532] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.240625] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.240747] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.240756] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.240766] ahci 0000:00:1f.2: setting latency timer to 64
[    1.242114] scsi0 : ahci
[    1.242372] scsi1 : ahci
[    1.242573] scsi2 : ahci
[    1.242775] scsi3 : ahci
[    1.243099] ata1: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604500 irq 44
[    1.243108] ata2: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604580 irq 44
[    1.243116] ata3: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604600 irq 44
[    1.243123] ata4: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604680 irq 44
[    1.244316] Fixed MDIO Bus: probed
[    1.244369] tun: Universal TUN/TAP device driver, 1.6
[    1.244374] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.244528] PPP generic driver version 2.4.2
[    1.244791] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.244839] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.244875] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.244883] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.245006] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.245045] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.245064] ehci_hcd 0000:00:1d.7: debug port 1
[    1.248969] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.249011] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0604000
[    1.264070] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.264428] hub 1-0:1.0: USB hub found
[    1.264441] hub 1-0:1.0: 8 ports detected
[    1.264616] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.264650] uhci_hcd: USB Universal Host Controller Interface driver
[    1.264699] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.264716] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.264724] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.264860] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.264900] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.265234] hub 2-0:1.0: USB hub found
[    1.265245] hub 2-0:1.0: 2 ports detected
[    1.265392] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.265408] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.265415] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.265533] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.265592] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.265925] hub 3-0:1.0: USB hub found
[    1.265937] hub 3-0:1.0: 2 ports detected
[    1.266077] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.266092] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.266100] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.266223] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.266279] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.266613] hub 4-0:1.0: USB hub found
[    1.266625] hub 4-0:1.0: 2 ports detected
[    1.266773] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.266789] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.266796] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.266928] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.266987] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.267336] hub 5-0:1.0: USB hub found
[    1.267348] hub 5-0:1.0: 2 ports detected
[    1.267627] usbcore: registered new interface driver libusual
[    1.267724] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.271417] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.271436] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.271819] mousedev: PS/2 mouse device common for all mice
[    1.272632] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.272679] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.272850] device-mapper: uevent: version 1.0.3
[    1.273049] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.273138] EISA: Probing bus 0 at eisa.0
[    1.273144] EISA: Cannot allocate resource for mainboard
[    1.273150] Cannot allocate resource for EISA slot 1
[    1.273155] Cannot allocate resource for EISA slot 2
[    1.273159] Cannot allocate resource for EISA slot 3
[    1.273164] Cannot allocate resource for EISA slot 4
[    1.273168] Cannot allocate resource for EISA slot 5
[    1.273173] Cannot allocate resource for EISA slot 6
[    1.273177] Cannot allocate resource for EISA slot 7
[    1.273182] Cannot allocate resource for EISA slot 8
[    1.273187] EISA: Detected 0 cards.
[    1.273205] cpufreq-nforce2: No nForce2 chipset.
[    1.273351] cpuidle: using governor ladder
[    1.273582] cpuidle: using governor menu
[    1.273588] EFI Variables Facility v0.08 2004-May-17
[    1.274129] TCP cubic registered
[    1.274416] NET: Registered protocol family 10
[    1.275724] NET: Registered protocol family 17
[    1.275736] Registering the dns_resolver key type
[    1.275779] Using IPI No-Shortcut mode
[    1.276169] PM: Hibernation image not present or could not be loaded.
[    1.276194] registered taskstats version 1
[    1.294196]   Magic number: 0:934:134
[    1.294290] acpi device:09: hash matches
[    1.294361] rtc_cmos 00:04: setting system clock to 2012-10-02 16:06:52 UTC (1349194012)
[    1.295152] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.295158] EDD information not available.
[    1.305390] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.560167] ata2: SATA link down (SStatus 0 SControl 300)
[    1.560220] ata4: SATA link down (SStatus 0 SControl 300)
[    1.560285] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.560322] ata3: SATA link down (SStatus 0 SControl 300)
[    1.570080] ata1.00: ATA-8: SAMSUNG HM250HI, 2AC101C4, max UDMA/133
[    1.570094] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.579936] ata1.00: configured for UDMA/133
[    1.580362] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM250HI  2AC1 PQ: 0 ANSI: 5
[    1.580731] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.580810] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.580953] sd 0:0:0:0: [sda] Write Protect is off
[    1.580963] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.581111] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.641213]  sda: sda1 sda2 < sda5 >
[    1.642492] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.642576] Freeing unused kernel memory: 712k freed
[    1.643102] Write protecting the kernel text: 5624k
[    1.643199] Write protecting the kernel read-only data: 2324k
[    1.689438] udevd[94]: starting version 175
[    1.744167] usb 1-8: new high-speed USB device number 4 using ehci_hcd
[    1.932629] sky2: driver version 1.30
[    1.932750] sky2 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.932821] sky2 0000:09:00.0: setting latency timer to 64
[    1.932959] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    1.933677] sky2 0000:09:00.0: irq 45 for MSI/MSI-X
[    1.935965] sky2 0000:09:00.0: eth0: addr 00:24:54:c2:85:c5
[    1.947200] [drm] Initialized drm 1.1.0 20060810
[    1.998382] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.998398] i915 0000:00:02.0: setting latency timer to 64
[    2.059196] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    2.059212] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.059218] [drm] Driver supports precise vblank timestamp query.
[    2.089795] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.132091] usb 2-1: new low-speed USB device number 2 using uhci_hcd
[    2.342040] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input5
[    2.342456] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.0-1/input0
[    2.342515] usbcore: registered new interface driver usbhid
[    2.342522] usbhid: USB HID core driver
[    2.412451] [drm] initialized overlay support
[    2.433386] fbcon: inteldrmfb (fb0) is primary device
[    2.433528] Console: switching to colour frame buffer device 128x37
[    2.433603] fb0: inteldrmfb frame buffer device
[    2.433609] drm: registered panic notifier
[    2.435299] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[    2.436076] acpi device:04: registered as cooling_device2
[    2.436393] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    2.436956] ACPI: Video Device [IGD0] (multi-head: yes  rom: no  post: no)
[    2.437054] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.560106] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[    3.108529] PM: Marking nosave pages: 000000000009d000 - 0000000000100000
[    3.108541] PM: Basic memory bitmaps created
[    3.134222] PM: Basic memory bitmaps freed
[    3.134276] video LNXVIDEO:00: Restoring backlight state
[    3.257953] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   28.506221] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.556286] udevd[396]: starting version 175
[   28.600901] Adding 6142972k swap on /dev/sda5.  Priority:-1 extents:1 across:6142972k 
[   28.716930] lp: driver loaded but no devices found
[   28.779977] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
[   29.536729] ppdev: user-space parallel port driver
[   29.569071] Bluetooth: Core ver 2.16
[   29.569151] NET: Registered protocol family 31
[   29.569160] Bluetooth: HCI device and connection manager initialized
[   29.569169] Bluetooth: HCI socket layer initialized
[   29.569175] Bluetooth: L2CAP socket layer initialized
[   29.569194] Bluetooth: SCO socket layer initialized
[   29.574412] lib80211: common routines for IEEE802.11 drivers
[   29.574425] lib80211_crypt: registered algorithm 'NULL'
[   29.583913] wl: module license 'MIXED/Proprietary' taints kernel.
[   29.583924] Disabling lock debugging due to kernel taint
[   29.607291] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.607302] Bluetooth: BNEP filters: protocol multicast
[   29.640688] Bluetooth: RFCOMM TTY layer initialized
[   29.640705] Bluetooth: RFCOMM socket layer initialized
[   29.640712] Bluetooth: RFCOMM ver 1.11
[   29.701269] type=1400 audit(1349194040.901:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=686 comm="apparmor_parser"
[   29.717358] type=1400 audit(1349194040.917:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=686 comm="apparmor_parser"
[   29.912761] wl 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.912786] wl 0000:05:00.0: setting latency timer to 64
[   29.924998] type=1400 audit(1349194041.125:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=724 comm="apparmor_parser"
[   29.928086] type=1400 audit(1349194041.129:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=724 comm="apparmor_parser"
[   29.929360] type=1400 audit(1349194041.129:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=724 comm="apparmor_parser"
[   29.943189] type=1400 audit(1349194041.141:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=725 comm="apparmor_parser"
[   30.025389] lib80211_crypt: registered algorithm 'TKIP'
[   30.108279] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[   30.284751] psmouse serio1: hgpk: ID: 10 00 64
[   30.382614] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x040216)
[   30.419451] psmouse serio1: elantech: Synaptics capabilities query result 0x09, 0x14, 0x0b.
[   30.495569] samsung_laptop: found laptop model 'N150P'
[   36.269961] atkbd serio0: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[   36.271797] ACPI: Failed to switch the brightness
[   36.495682] samsung_laptop: enabled workaround for brightness stepping quirk
[   37.104128] psmouse serio1: elantech: retrying ps2 command 0x3e9 (2).
[   37.169562] init: portmap main process (856) terminated with status 127
[   37.169672] init: portmap main process ended, respawning
[   37.295088] init: failsafe main process (823) killed by TERM signal
[   37.598434] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   37.606605] usbcore: registered new interface driver btusb
[   37.627607] type=1400 audit(1349194048.825:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=977 comm="apparmor_parser"
[   37.630020] Linux video capture interface: v2.00
[   37.647722] uvcvideo: Found UVC 1.00 device WebCam SCB-0340N (0ac8:c33f)
[   37.657809] input: WebCam SCB-0340N as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input7
[   37.661355] usbcore: registered new interface driver uvcvideo
[   37.661365] USB Video Class driver (1.1.1)
[   37.665986] type=1400 audit(1349194048.865:9): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=976 comm="apparmor_parser"
[   37.668660] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8
[   37.674604] type=1400 audit(1349194048.873:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=980 comm="apparmor_parser"
[   37.680455] type=1400 audit(1349194048.881:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=980 comm="apparmor_parser"
[   37.681454] type=1400 audit(1349194048.881:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=980 comm="apparmor_parser"
[   37.787078] type=1400 audit(1349194048.985:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=992 comm="apparmor_parser"
[   37.794808] type=1400 audit(1349194048.993:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=992 comm="apparmor_parser"
[   37.838734] type=1400 audit(1349194049.037:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1001 comm="apparmor_parser"
[   37.840377] type=1400 audit(1349194049.041:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=987 comm="apparmor_parser"
[   37.991611] sky2 0000:09:00.0: eth0: enabling interface
[   37.993527] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.002008] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.634156] init: alsa-restore main process (1087) terminated with status 19
[   38.829693] init: gdm main process (1145) killed by TERM signal
[   38.842767] init: lightdm main process (1150) killed by TERM signal
[   46.183390] oss_hdaudio 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   46.188510] oss_hdaudio: HDA codec 0x10ec0269 not known yet
[   46.194954] oss_hdaudio: Balanced I/O not supported
[   46.200658] oss_hdaudio: HDA codec 0x10ec0269 not known yet
[   46.221262] usbcore: registered new interface driver oss_usb
[   53.312190] Non-volatile memory driver v1.3
[   53.504160] thinkpad_ec: no ThinkPad embedded controller!
[   53.544564] coretemp coretemp.0: Using relative temperature scale!
[   54.290149] init: plymouth-stop pre-start process (1764) terminated with status 1
[   55.822457] thinkpad_ec: no ThinkPad embedded controller!
[   71.296065] eth1: no IPv6 routers present
meinname@Samsung-N150P:~$
```

---

