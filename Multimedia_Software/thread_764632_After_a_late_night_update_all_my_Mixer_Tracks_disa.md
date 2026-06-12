---
title: "After a late night update all my Mixer Tracks disappeared."
date: 2008-04-24
forum: Multimedia Software
---

### Post by airjer on 2008-04-24
Early in the AM on the 23rd Ubuntu stated that some updates were available so I went ahead and upgraded. After the download and update it stated it needed a reboot to complete the update process. Upon booting up I get horrible screeching static where the log on sound would be that faintly continues on. When I went to my sound settings all of my Default Mixer Tracks were gone!

[IMG]http://img155.imageshack.us/img155/8377/screenshotsoundpreferenyv4.png[/IMG]

I've tried everything in the Comprehensive Sound Problem Solutions Guide and nothing successfully brings my sound devices back. Whenever I get to the final step I receive:

```
dam4nn@dam4nn-desktop:~$ sudo modprobe snd-hda-intel
[sudo] password for dam4nn: 
FATAL: Error inserting snd (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-16-generic/updates/alsa/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg is:
```
dam4nn@dam4nn-desktop:~$ dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=420C547C0C546CC3 loop=/ubuntu/disks/root.disk ro quiet splash irqpoll
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1245184
[    0.000000] DMI 2.5 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7860 checksum 0
[    0.000000] ACPI: RSDP 000F7860, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT CFEE3000, 0034 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP CFEE3080, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT CFEE3100, 4D0B (r1 INTELR AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS CFEE0000, 0040
[    0.000000] ACPI: MCFG CFEE7F00, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC CFEE7E40, 0084 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT CFEE8860, 0380 (r1  PmRef    CpuPm     3000 INTL 20041203)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1245184
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   851680
[    0.000000]     0:  1048576 ->  1245184
[    0.000000] On node 0 totalpages: 1048191
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1225 pages reserved
[    0.000000]   DMA zone: 2718 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833304 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfee0000 - 00000000cfee3000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfee3000 - 00000000cfef0000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfef0000 - 00000000cff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000cff00000 - 00000000e0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029942
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=420C547C0C546CC3 loop=/ubuntu/disks/root.disk ro quiet splash irqpoll
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   22.869608] time.c: Detected 3239.999 MHz processor.
[   22.870380] Console: colour VGA+ 80x25
[   22.870382] console [tty0] enabled
[   22.870394] Checking aperture...
[   22.870400] Calgary: detecting Calgary via BIOS EBDA area
[   22.870401] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   22.870402] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   22.897886] Placing software IO TLB between 0x104d000 - 0x504d000
[   22.925350] Memory: 4046024k/4980736k available (2466k kernel code, 146740k reserved, 1309k data, 316k init)
[   22.925374] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   23.003607] Calibrating delay using timer specific routine.. 6500.75 BogoMIPS (lpj=13001512)
[   23.003630] Security Framework initialized
[   23.003635] SELinux:  Disabled at boot.
[   23.003644] AppArmor: AppArmor initialized
[   23.003646] Failure registering capabilities with primary security module.
[   23.003906] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   23.005585] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   23.006389] Mount-cache hash table entries: 256
[   23.006493] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.006495] CPU: L2 cache: 4096K
[   23.006496] CPU 0/0 -> Node 0
[   23.006497] using mwait in idle threads.
[   23.006498] CPU: Physical Processor ID: 0
[   23.006499] CPU: Processor Core ID: 0
[   23.006503] CPU0: Thermal monitoring enabled (TM2)
[   23.006512] SMP alternatives: switching to UP code
[   23.007021] Early unpacking initramfs... done
[   23.218576] ACPI: Core revision 20070126
[   23.218602] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.264298] Using local APIC timer interrupts.
[   23.425971] APIC timer calibration result 22499992
[   23.425972] Detected 22.499 MHz APIC timer.
[   23.426036] SMP alternatives: switching to SMP code
[   23.426467] Booting processor 1/4 APIC 0x1
[   23.436787] Initializing CPU#1
[   23.513975] Calibrating delay using timer specific routine.. 6480.05 BogoMIPS (lpj=12960112)
[   23.513980] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.513981] CPU: L2 cache: 4096K
[   23.513982] CPU 1/1 -> Node 0
[   23.513983] CPU: Physical Processor ID: 0
[   23.513983] CPU: Processor Core ID: 1
[   23.513987] CPU1: Thermal monitoring enabled (TM2)
[   23.514315] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   23.514382] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   23.534442] SMP alternatives: switching to SMP code
[   23.534893] Booting processor 2/4 APIC 0x3
[   23.545184] Initializing CPU#2
[   23.621957] Calibrating delay using timer specific routine.. 6480.00 BogoMIPS (lpj=12960012)
[   23.621962] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.621962] CPU: L2 cache: 4096K
[   23.621964] CPU 2/3 -> Node 0
[   23.621965] CPU: Physical Processor ID: 0
[   23.621965] CPU: Processor Core ID: 3
[   23.621969] CPU2: Thermal monitoring enabled (TM2)
[   23.622297] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   23.622393] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   23.642429] SMP alternatives: switching to SMP code
[   23.642707] Booting processor 3/4 APIC 0x2
[   23.652997] Initializing CPU#3
[   23.729939] Calibrating delay using timer specific routine.. 6479.99 BogoMIPS (lpj=12959996)
[   23.729944] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.729944] CPU: L2 cache: 4096K
[   23.729946] CPU 3/2 -> Node 0
[   23.729947] CPU: Physical Processor ID: 0
[   23.729947] CPU: Processor Core ID: 2
[   23.729951] CPU3: Thermal monitoring enabled (TM2)
[   23.730278] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   23.730306] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   23.750315] Brought up 4 CPUs
[   23.750390] CPU0 attaching sched-domain:
[   23.750399]  domain 0: span 03
[   23.750400]   groups: 01 02
[   23.750402]   domain 1: span 0f
[   23.750402]    groups: 03 0c
[   23.750404]    domain 2: span 0f
[   23.750405]     groups: 0f
[   23.750406] CPU1 attaching sched-domain:
[   23.750407]  domain 0: span 03
[   23.750407]   groups: 02 01
[   23.750409]   domain 1: span 0f
[   23.750409]    groups: 03 0c
[   23.750411]    domain 2: span 0f
[   23.750414]     groups: 0f
[   23.750415] CPU2 attaching sched-domain:
[   23.750416]  domain 0: span 0c
[   23.750417]   groups: 04 08
[   23.750418]   domain 1: span 0f
[   23.750419]    groups: 0c 03
[   23.750420]    domain 2: span 0f
[   23.750421]     groups: 0f
[   23.750422] CPU3 attaching sched-domain:
[   23.750422]  domain 0: span 0c
[   23.750423]   groups: 08 04
[   23.750424]   domain 1: span 0f
[   23.750425]    groups: 0c 03
[   23.750426]    domain 2: span 0f
[   23.750427]     groups: 0f
[   23.750622] net_namespace: 120 bytes
[   23.750862] Time:  3:06:31  Date: 04/24/08
[   23.750878] NET: Registered protocol family 16
[   23.750995] ACPI: bus type pci registered
[   23.751038] PCI: Using configuration type 1
[   23.751922] ACPI: EC: Look up EC in DSDT
[   23.754850] ACPI: Interpreter enabled
[   23.754852] ACPI: (supports S0 S3 S4 S5)
[   23.754867] ACPI: Using IOAPIC for interrupt routing
[   23.757876] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.758401] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   23.758403] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   23.759096] PCI: Transparent bridge - 0000:00:1e.0
[   23.759116] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.759205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   23.759257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   23.759307] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   23.768996] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 7 9 *10 11 12)
[   23.769061] ACPI: PCI Interrupt Link [LNKB] (IRQs *4 5 7 9 10 11 12)
[   23.769125] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 7 9 *10 11 12)
[   23.769188] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 5 7 9 10 *11 12)
[   23.769252] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 7 9 10 11 12) *0, disabled.
[   23.769315] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 7 9 10 *11 12)
[   23.769379] ACPI: PCI Interrupt Link [LNK0] (IRQs 4 5 *7 9 10 11 12)
[   23.769442] ACPI: PCI Interrupt Link [LNK1] (IRQs 4 *5 7 9 10 11 12)
[   23.769513] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.769529] pnp: PnP ACPI init
[   23.769533] ACPI: bus type pnp registered
[   23.771002] pnp: PnP ACPI: found 12 devices
[   23.771004] ACPI: ACPI bus type pnp unregistered
[   23.771134] PCI: Using ACPI for IRQ routing
[   23.771135] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.786050] NET: Registered protocol family 8
[   23.786052] NET: Registered protocol family 20
[   23.786079] PCI-GART: No AMD northbridge found.
[   23.786105] AppArmor: AppArmor Filesystem Enabled
[   23.790058] Time: tsc clocksource has been installed.
[   23.798147] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   23.798149] system 00:01: ioport range 0x880-0x88f has been reserved
[   23.798155] system 00:07: ioport range 0x400-0x4bf could not be reserved
[   23.798160] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[   23.798165] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[   23.798167] system 00:0b: iomem range 0xcff00000-0xcfffffff has been reserved
[   23.798169] system 00:0b: iomem range 0xcfee0000-0xcfefffff could not be reserved
[   23.798171] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   23.798173] system 00:0b: iomem range 0x100000-0xcfedffff could not be reserved
[   23.798176] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   23.798178] system 00:0b: iomem range 0xfed14000-0xfed1dfff has been reserved
[   23.798180] system 00:0b: iomem range 0xfed20000-0xfed9ffff has been reserved
[   23.798182] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   23.798184] system 00:0b: iomem range 0xffb00000-0xffb7ffff has been reserved
[   23.798186] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[   23.798188] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
[   23.798443] PCI: Bridge: 0000:00:01.0
[   23.798444]   IO window: a000-afff
[   23.798446]   MEM window: fdc00000-fdcfffff
[   23.798448]   PREFETCH window: d0000000-dfffffff
[   23.798449] PCI: Bridge: 0000:00:1c.0
[   23.798451]   IO window: d000-dfff
[   23.798453]   MEM window: fda00000-fdafffff
[   23.798456]   PREFETCH window: fd900000-fd9fffff
[   23.798459] PCI: Bridge: 0000:00:1c.4
[   23.798460]   IO window: c000-cfff
[   23.798463]   MEM window: fde00000-fdefffff
[   23.798465]   PREFETCH window: fdd00000-fddfffff
[   23.798468] PCI: Bridge: 0000:00:1e.0
[   23.798469]   IO window: b000-bfff
[   23.798472]   MEM window: f4000000-fbffffff
[   23.798474]   PREFETCH window: fdb00000-fdbfffff
[   23.798482] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.798485] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.798496] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.798499] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.798510] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   23.798512] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   23.798519] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   23.798524] NET: Registered protocol family 2
[   23.834494] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.835233] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   23.837879] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   23.838305] TCP: Hash tables configured (established 524288 bind 65536)
[   23.838307] TCP reno registered
[   23.846581] checking if image is initramfs... it is
[   24.262958] Freeing initrd memory: 7505k freed
[   24.265896] audit: initializing netlink socket (disabled)
[   24.265916] audit(1209006391.192:1): initialized
[   24.268146] VFS: Disk quotas dquot_6.5.1
[   24.268202] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   24.268300] io scheduler noop registered
[   24.268302] io scheduler anticipatory registered
[   24.268303] io scheduler deadline registered
[   24.268391] io scheduler cfq registered (default)
[   24.271085] Boot video device is 0000:01:00.0
[   24.271267] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.271306] assign_interrupt_mode Found MSI capability
[   24.271322] Allocate Port Service[0000:00:01.0:pcie00]
[   24.271400] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.271431] assign_interrupt_mode Found MSI capability
[   24.271456] Allocate Port Service[0000:00:1c.0:pcie00]
[   24.271489] Allocate Port Service[0000:00:1c.0:pcie02]
[   24.271554] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   24.271585] assign_interrupt_mode Found MSI capability
[   24.271610] Allocate Port Service[0000:00:1c.4:pcie00]
[   24.271639] Allocate Port Service[0000:00:1c.4:pcie02]
[   24.295790] Real Time Clock Driver v1.12ac
[   24.295884] Linux agpgart interface v0.102
[   24.295886] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.297079] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.297133] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   24.297265] PNP: No PS/2 controller found. Probing ports directly.
[   24.299960] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.299963] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.300978] Switched to high resolution mode on CPU 2
[   24.301349] Switched to high resolution mode on CPU 1
[   24.304935] Switched to high resolution mode on CPU 3
[   24.304959] Switched to high resolution mode on CPU 0
[   24.315022] mice: PS/2 mouse device common for all mice
[   24.315056] cpuidle: using governor ladder
[   24.315057] cpuidle: using governor menu
[   24.315152] NET: Registered protocol family 1
[   24.315187] registered taskstats version 1
[   24.315264]   Magic number: 4:171:109
[   24.315303] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   24.315305] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   24.315306] EDD information not available.
[   24.315310] Freeing unused kernel memory: 316k freed
[   25.429072] fuse init (API version 7.9)
[   25.438747] ACPI: SSDT CFEE7F80, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
[   25.438955] ACPI: SSDT CFEE8440, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[   25.439112] ACPI: SSDT CFEE85A0, 0152 (r1  PmRef  Cpu2Ist     3000 INTL 20041203)
[   25.439274] ACPI: SSDT CFEE8700, 0152 (r1  PmRef  Cpu3Ist     3000 INTL 20041203)
[   25.439887] ACPI Error (dswstate-0226): No result objects! State=ffff810128bd8800 [20070126]
[   25.439892] ACPI Exception (dsutils-0642): AE_AML_NO_RETURN_VALUE, Missing or null operand [20070126]
[   25.439895] ACPI Exception (dsutils-0735): AE_AML_NO_RETURN_VALUE, While creating Arg 1 [20070126]
[   25.439899] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.THRM._TMP] (Node ffff810129a3e8a0), AE_AML_NO_RETURN_VALUE
[   25.499378] usbcore: registered new interface driver usbfs
[   25.499392] usbcore: registered new interface driver hub
[   25.499414] usbcore: registered new device driver usb
[   25.499858] USB Universal Host Controller Interface driver v3.0
[   25.499893] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.499901] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   25.499903] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   25.500046] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   25.500069] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[   25.500140] usb usb1: configuration #1 chosen from 1 choice
[   25.500152] hub 1-0:1.0: USB hub found
[   25.500155] hub 1-0:1.0: 2 ports detected
[   25.546410] SCSI subsystem initialized
[   25.559773] libata version 3.00 loaded.
[   25.598987] FDC 0 is a post-1991 82077
[   25.602761] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   25.602771] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   25.602773] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   25.602793] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   25.602814] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[   25.602874] usb usb2: configuration #1 chosen from 1 choice
[   25.602885] hub 2-0:1.0: USB hub found
[   25.602888] hub 2-0:1.0: 2 ports detected
[   25.706733] ACPI: PCI Interrupt 0000:00:1a.2[D] -> GSI 19 (level, low) -> IRQ 19
[   25.706741] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   25.706744] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   25.706757] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   25.706777] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fd00
[   25.706847] usb usb3: configuration #1 chosen from 1 choice
[   25.706859] hub 3-0:1.0: USB hub found
[   25.706862] hub 3-0:1.0: 2 ports detected
[   25.810930] ahci 0000:03:00.0: version 3.0
[   25.810964] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.841766] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   26.005210] usb 1-2: configuration #1 chosen from 1 choice
[   26.245550] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   26.418773] usb 2-1: configuration #1 chosen from 1 choice
[   26.661445] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   26.817429] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   26.817432] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   26.817438] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   26.817603] scsi0 : ahci
[   26.817644] scsi1 : ahci
[   26.817678] ata1: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
[   26.817681] ata2: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
[   26.938717] usb 2-2: configuration #1 chosen from 1 choice
[   27.137363] ata1: SATA link down (SStatus 0 SControl 300)
[   27.457383] ata2: SATA link down (SStatus 0 SControl 300)
[   27.457585] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 21 (level, low) -> IRQ 21
[   27.458313] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   27.458369] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   27.458372] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   27.458390] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   27.458416] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[   27.458483] usb usb4: configuration #1 chosen from 1 choice
[   27.458496] hub 4-0:1.0: USB hub found
[   27.458499] hub 4-0:1.0: 2 ports detected
[   27.512510] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fbffd000-fbffd7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   27.561331] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   27.561339] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   27.561341] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   27.561360] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   27.561381] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[   27.561529] usb usb5: configuration #1 chosen from 1 choice
[   27.561541] hub 5-0:1.0: USB hub found
[   27.561545] hub 5-0:1.0: 2 ports detected
[   27.665303] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   27.665310] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   27.665312] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   27.665337] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   27.665361] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[   27.665497] usb usb6: configuration #1 chosen from 1 choice
[   27.665509] hub 6-0:1.0: USB hub found
[   27.665513] hub 6-0:1.0: 2 ports detected
[   27.769316] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   27.770378] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   27.770383] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   27.770415] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   27.774367] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   27.774373] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
[   27.793289] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.793364] usb usb7: configuration #1 chosen from 1 choice
[   27.793378] hub 7-0:1.0: USB hub found
[   27.793384] hub 7-0:1.0: 6 ports detected
[   27.795815] usbcore: registered new interface driver hiddev
[   27.846513] usbcore: registered new interface driver usbhid
[   27.846517] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   27.893293] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   27.894051] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   27.894056] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   27.894095] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   27.898009] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   27.898013] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
[   27.913193] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.913261] usb usb8: configuration #1 chosen from 1 choice
[   27.913405] hub 8-0:1.0: USB hub found
[   27.913409] hub 8-0:1.0: 6 ports detected
[   28.017280] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[   28.017290] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 17 (level, low) -> IRQ 17
[   28.017321] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   28.017372] scsi2 : pata_jmicron
[   28.017758] scsi3 : pata_jmicron
[   28.017774] ata3: PATA max UDMA/100 cmd 0xcf00 ctl 0xce00 bmdma 0xcb00 irq 17
[   28.017775] ata4: PATA max UDMA/100 cmd 0xcd00 ctl 0xcc00 bmdma 0xcb08 irq 17
[   28.133498] usb 7-2: new high speed USB device using ehci_hcd and address 2
[   28.269378] usb 7-2: configuration #1 chosen from 1 choice
[   28.338191] ata3.00: ATAPI: ASUS    DRW-2014L1, 1.01, max UDMA/66
[   28.509755] ata3.00: configured for UDMA/66
[   28.677222] scsi 2:0:0:0: CD-ROM            ASUS     DRW-2014L1       1.01 PQ: 0 ANSI: 5
[   28.677316] r8169 Gigabit Ethernet driver 2.2LK loaded
[   28.677334] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 23 (level, low) -> IRQ 23
[   28.677543] eth0: RTL8169sc/8110sc at 0xffffc20001040000, 00:50:8d:b5:5b:7b, XID 18000000 IRQ 23
[   28.678280] r8169 Gigabit Ethernet driver 2.2LK loaded
[   28.678301] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 22 (level, low) -> IRQ 22
[   28.678477] eth1: RTL8169sc/8110sc at 0xffffc20001048000, 00:50:8d:b5:5b:7c, XID 18000000 IRQ 22
[   28.679289] ata_piix 0000:00:1f.2: version 2.12
[   28.679297] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   28.679317] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 19
[   28.679343] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.679638] scsi4 : ata_piix
[   28.679672] scsi5 : ata_piix
[   28.680051] ata5: SATA max UDMA/133 cmd 0xf900 ctl 0xf800 bmdma 0xf500 irq 19
[   28.680053] ata6: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf508 irq 19
[   28.693556] usb 1-2: USB disconnect, address 2
[   28.781059] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00508d0000b1203c]
[   28.821032] usb 2-1: USB disconnect, address 2
[   28.849838] ata5.00: ATA-7: WDC WD1500ADFD-00NLR1, 20.07P20, max UDMA/133
[   28.849840] ata5.00: 293046768 sectors, multi 16: LBA48 NCQ (not used)
[   28.849972] ata5.01: ATA-7: SAMSUNG HD103UJ, 1AA01104, max UDMA7
[   28.849974] ata5.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   28.866826] ata5.00: configured for UDMA/133
[   28.876326] ata5.01: configured for UDMA/133
[   29.061437] usb 2-1: new full speed USB device using uhci_hcd and address 4
[   29.201084] ata6.00: ATAPI: ASUS    DRW-2014L1T, 1.02, max UDMA/66
[   29.201787] ata6.01: ATA-7: WDC WD1500ADFD-00NLR5, 21.07QR5, max UDMA/133
[   29.201789] ata6.01: 293046768 sectors, multi 16: LBA48 NCQ (not used)
[   29.243331] usb 2-1: configuration #1 chosen from 1 choice
[   29.251416] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-1/2-1:1.0/input/input1
[   29.270442] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-1
[   29.276350] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-1/2-1:1.1/input/input2
[   29.302450] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.1-1
[   29.302498] usb 2-2: USB disconnect, address 3
[   29.373069] ata6.00: configured for UDMA/66
[   29.389712] ata6.01: configured for UDMA/133
[   29.389795] scsi 4:0:0:0: Direct-Access     ATA      WDC WD1500ADFD-0 20.0 PQ: 0 ANSI: 5
[   29.389879] scsi 4:0:1:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[   29.390410] scsi 5:0:0:0: CD-ROM            ASUS     DRW-2014L1T      1.02 PQ: 0 ANSI: 5
[   29.390461] scsi 5:0:1:0: Direct-Access     ATA      WDC WD1500ADFD-0 21.0 PQ: 0 ANSI: 5
[   29.390502] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[   29.390521] ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 19 (level, low) -> IRQ 19
[   29.390546] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   29.390583] scsi6 : ata_piix
[   29.390610] scsi7 : ata_piix
[   29.390774] ata7: SATA max UDMA/133 cmd 0xf200 ctl 0xf100 bmdma 0xee00 irq 19
[   29.390776] ata8: SATA max UDMA/133 cmd 0xf000 ctl 0xef00 bmdma 0xee08 irq 19
[   29.540837] usb 2-2: new low speed USB device using uhci_hcd and address 5
[   29.726933] Driver 'sr' needs updating - please use bus_type methods
[   29.728701] Driver 'sd' needs updating - please use bus_type methods
[   29.731436] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   29.731439] Uniform CD-ROM driver Revision: 3.20
[   29.731479] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   29.731589] sd 4:0:0:0: [sda] 293046768 512-byte hardware sectors (150040 MB)
[   29.731604] sd 4:0:0:0: [sda] Write Protect is off
[   29.731605] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.731614] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.731646] sd 4:0:0:0: [sda] 293046768 512-byte hardware sectors (150040 MB)
[   29.731651] sd 4:0:0:0: [sda] Write Protect is off
[   29.731652] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.731660] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.731662]  sda:sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   29.735641] sr 5:0:0:0: Attached scsi CD-ROM sr1
[   29.738158] sr 2:0:0:0: Attached scsi generic sg0 type 5
[   29.738170] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   29.738180] scsi 4:0:1:0: Attached scsi generic sg2 type 0
[   29.738191] sr 5:0:0:0: Attached scsi generic sg3 type 5
[   29.738201] scsi 5:0:1:0: Attached scsi generic sg4 type 0
[   29.743532]  sda1
[   29.743574] sd 4:0:0:0: [sda] Attached SCSI disk
[   29.743611] sd 4:0:1:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   29.743618] sd 4:0:1:0: [sdb] Write Protect is off
[   29.743620] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.743629] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.743662] sd 4:0:1:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   29.743667] sd 4:0:1:0: [sdb] Write Protect is off
[   29.743668] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.743677] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.743679]  sdb: sdb1
[   29.747727] sd 4:0:1:0: [sdb] Attached SCSI disk
[   29.748299] sd 5:0:1:0: [sdc] 293046768 512-byte hardware sectors (150040 MB)
[   29.748532] sd 5:0:1:0: [sdc] Write Protect is off
[   29.748534] sd 5:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   29.748545] sd 5:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.748566] sd 5:0:1:0: [sdc] 293046768 512-byte hardware sectors (150040 MB)
[   29.748571] sd 5:0:1:0: [sdc] Write Protect is off
[   29.748572] sd 5:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   29.748581] sd 5:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.748583]  sdc: sdc1
[   29.758536] sd 5:0:1:0: [sdc] Attached SCSI disk
[   29.822269] usb 2-2: configuration #1 chosen from 1 choice
[   29.876391] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.0/input/input3
[   29.906313] input,hidraw2: USB HID v1.11 Keyboard [Chicony Saitek Eclipse Keyboard] on usb-0000:00:1a.1-2
[   30.011204] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.1/input/input4
[   30.029766] input,hiddev97,hidraw3: USB HID v1.11 Device [Chicony Saitek Eclipse Keyboard] on usb-0000:00:1a.1-2
[   30.297714] loop: module loaded
[   30.313392] kjournald starting.  Commit interval 5 seconds
[   30.313399] EXT3-fs: mounted filesystem with ordered data mode.
[   34.913281] input: Power Button (FF) as /devices/virtual/input/input5
[   34.945173] ACPI: Power Button (FF) [PWRF]
[   34.945233] input: Power Button (CM) as /devices/virtual/input/input6
[   34.981164] ACPI: Power Button (CM) [PWRB]
[   35.001211] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.029289] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.047950] snd: Unknown symbol unregister_sound_special
[   35.048007] snd: Unknown symbol register_sound_special_device
[   35.048161] snd: Unknown symbol sound_class
[   35.065419] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   35.079661] iTCO_vendor_support: vendor-support=0
[   35.080038] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   35.080996] snd_hwdep: Unknown symbol snd_info_register
[   35.081012] snd_hwdep: Unknown symbol snd_info_create_module_entry
[   35.081026] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[   35.081041] snd_hwdep: Unknown symbol snd_info_free_entry
[   35.081059] snd_hwdep: Unknown symbol snd_unregister_oss_device
[   35.081076] snd_hwdep: Unknown symbol snd_verbose_printk
[   35.081091] snd_hwdep: Unknown symbol snd_register_oss_device
[   35.081107] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[   35.081121] snd_hwdep: Unknown symbol snd_card_file_add
[   35.081140] snd_hwdep: Unknown symbol snd_iprintf
[   35.081155] snd_hwdep: Unknown symbol snd_major
[   35.081176] snd_hwdep: Unknown symbol snd_unregister_device
[   35.081192] snd_hwdep: Unknown symbol snd_device_new
[   35.081212] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[   35.081231] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[   35.081247] snd_hwdep: Unknown symbol snd_lookup_minor_data
[   35.081262] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[   35.081278] snd_hwdep: Unknown symbol snd_card_file_remove
[   35.081293] snd_hwdep: Unknown symbol snd_register_device_for_dev
[   35.084190] iTCO_wdt: Found a ICH9R TCO device (Version=2, TCOBASE=0x0460)
[   35.084216] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   35.096164] snd_timer: Unknown symbol snd_info_register
[   35.096181] snd_timer: Unknown symbol snd_info_create_module_entry
[   35.096198] snd_timer: Unknown symbol snd_info_free_entry
[   35.096229] snd_timer: Unknown symbol snd_verbose_printk
[   35.096248] snd_timer: Unknown symbol snd_iprintf
[   35.096271] snd_timer: Unknown symbol snd_ecards_limit
[   35.096289] snd_timer: Unknown symbol snd_oss_info_register
[   35.096303] snd_timer: Unknown symbol snd_unregister_device
[   35.096322] snd_timer: Unknown symbol snd_device_new
[   35.096359] snd_timer: Unknown symbol snd_register_device_for_dev
[   35.100747] snd: Unknown symbol unregister_sound_special
[   35.100803] snd: Unknown symbol register_sound_special_device
[   35.100954] snd: Unknown symbol sound_class
[   35.113384] snd_timer: Unknown symbol snd_info_register
[   35.113400] snd_timer: Unknown symbol snd_info_create_module_entry
[   35.113418] snd_timer: Unknown symbol snd_info_free_entry
[   35.113448] snd_timer: Unknown symbol snd_verbose_printk
[   35.113468] snd_timer: Unknown symbol snd_iprintf
[   35.113491] snd_timer: Unknown symbol snd_ecards_limit
[   35.113508] snd_timer: Unknown symbol snd_oss_info_register
[   35.113523] snd_timer: Unknown symbol snd_unregister_device
[   35.113541] snd_timer: Unknown symbol snd_device_new
[   35.113578] snd_timer: Unknown symbol snd_register_device_for_dev
[   35.113868] snd_pcm: Unknown symbol snd_info_register
[   35.113885] snd_pcm: Unknown symbol snd_info_create_module_entry
[   35.113900] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[   35.113929] snd_pcm: Unknown symbol snd_timer_notify
[   35.113949] snd_pcm: Unknown symbol snd_timer_interrupt
[   35.113964] snd_pcm: Unknown symbol snd_info_free_entry
[   35.113978] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[   35.113998] snd_pcm: Unknown symbol snd_info_get_str
[   35.114038] snd_pcm: Unknown symbol snd_verbose_printk
[   35.114073] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[   35.114088] snd_pcm: Unknown symbol snd_card_file_add
[   35.114107] snd_pcm: Unknown symbol snd_iprintf
[   35.114132] snd_pcm: Unknown symbol snd_major
[   35.114167] snd_pcm: Unknown symbol snd_unregister_device
[   35.114185] snd_pcm: Unknown symbol snd_timer_new
[   35.114200] snd_pcm: Unknown symbol snd_device_new
[   35.114229] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[   35.114255] snd_pcm: Unknown symbol snd_lookup_minor_data
[   35.114270] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[   35.114292] snd_pcm: Unknown symbol snd_info_create_card_entry
[   35.114307] snd_pcm: Unknown symbol snd_power_wait
[   35.114324] snd_pcm: Unknown symbol snd_device_free
[   35.114350] snd_pcm: Unknown symbol snd_card_file_remove
[   35.114366] snd_pcm: Unknown symbol snd_register_device_for_dev
[   35.114403] snd_pcm: Unknown symbol snd_device_register
[   35.114419] snd_pcm: Unknown symbol snd_info_get_line
[   35.135564] snd: Unknown symbol unregister_sound_special
[   35.135624] snd: Unknown symbol register_sound_special_device
[   35.135775] snd: Unknown symbol sound_class
[   35.136023] snd_hwdep: Unknown symbol snd_info_register
[   35.136039] snd_hwdep: Unknown symbol snd_info_create_module_entry
[   35.136054] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[   35.136069] snd_hwdep: Unknown symbol snd_info_free_entry
[   35.136086] snd_hwdep: Unknown symbol snd_unregister_oss_device
[   35.136104] snd_hwdep: Unknown symbol snd_verbose_printk
[   35.136119] snd_hwdep: Unknown symbol snd_register_oss_device
[   35.136134] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[   35.136149] snd_hwdep: Unknown symbol snd_card_file_add
[   35.136168] snd_hwdep: Unknown symbol snd_iprintf
[   35.136182] snd_hwdep: Unknown symbol snd_major
[   35.136203] snd_hwdep: Unknown symbol snd_unregister_device
[   35.136219] snd_hwdep: Unknown symbol snd_device_new
[   35.136239] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[   35.136259] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[   35.136275] snd_hwdep: Unknown symbol snd_lookup_minor_data
[   35.136290] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[   35.136306] snd_hwdep: Unknown symbol snd_card_file_remove
[   35.136321] snd_hwdep: Unknown symbol snd_register_device_for_dev
[   35.136498] snd_timer: Unknown symbol snd_info_register
[   35.136514] snd_timer: Unknown symbol snd_info_create_module_entry
[   35.136531] snd_timer: Unknown symbol snd_info_free_entry
[   35.136561] snd_timer: Unknown symbol snd_verbose_printk
[   35.136580] snd_timer: Unknown symbol snd_iprintf
[   35.136603] snd_timer: Unknown symbol snd_ecards_limit
[   35.136621] snd_timer: Unknown symbol snd_oss_info_register
[   35.136635] snd_timer: Unknown symbol snd_unregister_device
[   35.136654] snd_timer: Unknown symbol snd_device_new
[   35.136691] snd_timer: Unknown symbol snd_register_device_for_dev
[   35.140237] snd: Unknown symbol unregister_sound_special
[   35.140292] snd: Unknown symbol register_sound_special_device
[   35.140442] snd: Unknown symbol sound_class
[   35.141527] snd_timer: Unknown symbol snd_info_register
[   35.141543] snd_timer: Unknown symbol snd_info_create_module_entry
[   35.141561] snd_timer: Unknown symbol snd_info_free_entry
[   35.141591] snd_timer: Unknown symbol snd_verbose_printk
[   35.141611] snd_timer: Unknown symbol snd_iprintf
[   35.141634] snd_timer: Unknown symbol snd_ecards_limit
[   35.141652] snd_timer: Unknown symbol snd_oss_info_register
[   35.141666] snd_timer: Unknown symbol snd_unregister_device
[   35.141685] snd_timer: Unknown symbol snd_device_new
[   35.141721] snd_timer: Unknown symbol snd_register_device_for_dev
[   35.142069] snd_pcm: Unknown symbol snd_info_register
[   35.142085] snd_pcm: Unknown symbol snd_info_create_module_entry
[   35.142100] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[   35.142129] snd_pcm: Unknown symbol snd_timer_notify
[   35.142149] snd_pcm: Unknown symbol snd_timer_interrupt
[   35.142164] snd_pcm: Unknown symbol snd_info_free_entry
[   35.142178] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[   35.142198] snd_pcm: Unknown symbol snd_info_get_str
[   35.142238] snd_pcm: Unknown symbol snd_verbose_printk
[   35.142272] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[   35.142287] snd_pcm: Unknown symbol snd_card_file_add
[   35.142306] snd_pcm: Unknown symbol snd_iprintf
[   35.142331] snd_pcm: Unknown symbol snd_major
[   35.142365] snd_pcm: Unknown symbol snd_unregister_device
[   35.142383] snd_pcm: Unknown symbol snd_timer_new
[   35.142398] snd_pcm: Unknown symbol snd_device_new
[   35.142427] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[   35.142452] snd_pcm: Unknown symbol snd_lookup_minor_data
[   35.142467] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[   35.142488] snd_pcm: Unknown symbol snd_info_create_card_entry
[   35.142503] snd_pcm: Unknown symbol snd_power_wait
[   35.142520] snd_pcm: Unknown symbol snd_device_free
[   35.142546] snd_pcm: Unknown symbol snd_card_file_remove
[   35.142561] snd_pcm: Unknown symbol snd_register_device_for_dev
[   35.142597] snd_pcm: Unknown symbol snd_device_register
[   35.142613] snd_pcm: Unknown symbol snd_info_get_line
[   35.155465] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   35.167686] [fglrx] Maximum main memory to use for locked dma buffers: 3796 MBytes.
[   35.167707] [fglrx] ASYNCIO init succeed!
[   35.168959] [fglrx] PAT is enabled successfully!
[   35.168977] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   35.308518] snd_hda_intel: Unknown symbol snd_ctl_add
[   35.308541] snd_hda_intel: Unknown symbol snd_pcm_new
[   35.308561] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   35.308579] snd_hda_intel: Unknown symbol snd_card_register
[   35.308593] snd_hda_intel: Unknown symbol snd_card_free
[   35.308608] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   35.308623] snd_hda_intel: Unknown symbol snd_card_proc_new
[   35.308677] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   35.308697] snd_hda_intel: Unknown symbol snd_verbose_printk
[   35.308725] snd_hda_intel: Unknown symbol snd_ctl_new1
[   35.308760] snd_hda_intel: Unknown symbol snd_component_add
[   35.308779] snd_hda_intel: Unknown symbol snd_card_new
[   35.308794] snd_hda_intel: Unknown symbol snd_iprintf
[   35.308812] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   35.308827] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[   35.308847] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   35.308864] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   35.308879] snd_hda_intel: Unknown symbol snd_hwdep_new
[   35.308897] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   35.308917] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   35.308937] snd_hda_intel: Unknown symbol snd_device_new
[   35.308961] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   35.308984] snd_hda_intel: Unknown symbol snd_card_disconnect
[   35.308999] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   35.309040] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[   35.309075] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   35.309090] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   35.309116] snd_hda_intel: Unknown symbol snd_pcm_format_width
[   35.336388] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0007
[   35.336399] usbcore: registered new interface driver usblp
[   35.337309] snd_hda_intel: Unknown symbol snd_ctl_add
[   35.337331] snd_hda_intel: Unknown symbol snd_pcm_new
[   35.337351] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   35.337368] snd_hda_intel: Unknown symbol snd_card_register
[   35.337383] snd_hda_intel: Unknown symbol snd_card_free
[   35.337398] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   35.337413] snd_hda_intel: Unknown symbol snd_card_proc_new
[   35.337466] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   35.337486] snd_hda_intel: Unknown symbol snd_verbose_printk
[   35.337513] snd_hda_intel: Unknown symbol snd_ctl_new1
[   35.337548] snd_hda_intel: Unknown symbol snd_component_add
[   35.337568] snd_hda_intel: Unknown symbol snd_card_new
[   35.337582] snd_hda_intel: Unknown symbol snd_iprintf
[   35.337599] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   35.337614] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[   35.337635] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   35.337651] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   35.337666] snd_hda_intel: Unknown symbol snd_hwdep_new
[   35.337684] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   35.337704] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   35.337724] snd_hda_intel: Unknown symbol snd_device_new
[   35.337748] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   35.337770] snd_hda_intel: Unknown symbol snd_card_disconnect
[   35.337785] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   35.337826] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[   35.337861] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   35.337876] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   35.337903] snd_hda_intel: Unknown symbol snd_pcm_format_width
[   36.184120] input: btnx keyboard as /devices/virtual/input/input8
[   36.231973] input: btnx mouse as /devices/virtual/input/input9
[   36.331568] input: btnx keyboard as /devices/virtual/input/input10
[   36.383422] input: btnx mouse as /devices/virtual/input/input11
[   36.673387] lp: driver loaded but no devices found
[   37.276176] EXT3 FS on loop0, internal journal
[   45.912422] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:2 across:15459124k
[   46.181633] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.418330] No dock devices found.
[   46.424708] ACPI: \_SB_.PCI0.PEX4.JMB0.IDE0.PRI0: found ejectable bay
[   46.424711] ACPI: \_SB_.PCI0.PEX4.JMB0.IDE0.PRI0: Adding notify handler
[   46.424733] ACPI: Bay [\_SB_.PCI0.PEX4.JMB0.IDE0.PRI0] Added
[   47.255970] ppdev: user-space parallel port driver
[   47.366041] NET: Registered protocol family 10
[   47.366177] lo: Disabled Privacy Extensions
[   47.409154] audit(1209020814.790:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5652 profile="/usr/sbin/cupsd" namespace="default"
[   48.975839] hdaudio: no version for "oss_register_device" found: kernel tainted.
[   48.976906] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   49.025362] ACPI: PCI Interrupt 0000:04:03.0[A] -> GSI 22 (level, low) -> IRQ 22
[   49.135330] usbcore: registered new interface driver ossusb
[   50.120773] r8169: eth1: link down
[   50.125453] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   50.158523] r8169: eth0: link up
[   50.255835] Bluetooth: Core ver 2.11
[   50.256185] NET: Registered protocol family 31
[   50.256188] Bluetooth: HCI device and connection manager initialized
[   50.256192] Bluetooth: HCI socket layer initialized
[   50.277084] Bluetooth: L2CAP ver 2.9
[   50.277089] Bluetooth: L2CAP socket layer initialized
[   50.372750] Bluetooth: RFCOMM socket layer initialized
[   50.372766] Bluetooth: RFCOMM TTY layer initialized
[   50.372767] Bluetooth: RFCOMM ver 1.8
[   52.093635] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   52.781738] input: btnx keyboard as /devices/virtual/input/input12
[   52.808900] input: btnx mouse as /devices/virtual/input/input13
[   53.296990] [fglrx] Reserve Block - 0 offset =  0X1fffc000 length = 0X4000
[   53.296995] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   53.296997] [fglrx] Reserve Block - 2 offset =  0Xff7f000 length = 0X80000
[   53.636930] [fglrx] interrupt source 20008000 successfully enabled
[   53.636935] [fglrx] enable ID = 0x00000006
[   53.636942] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   53.636986] [fglrx] interrupt source 10000000 successfully enabled
[   53.636989] [fglrx] enable ID = 0x00000008
[   53.636992] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   53.638681] [fglrx] interrupt source 60000001 successfully enabled
[   53.638685] [fglrx] enable ID = 0x00000009
[   53.638689] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
[   53.638723] [fglrx] interrupt source 00000040 successfully enabled
[   53.638725] [fglrx] enable ID = 0x0000000A
[   53.638728] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
[   53.649480] [fglrx] interrupt source ff00002c successfully enabled
[   53.649483] [fglrx] enable ID = 0x0000000B
[   53.649486] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
[   53.649516] [fglrx] interrupt source ff00002d successfully enabled
[   53.649518] [fglrx] enable ID = 0x0000000C
[   53.649521] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
[   53.649549] [fglrx] interrupt source 20000400 successfully enabled
[   53.649551] [fglrx] enable ID = 0x0000000D
[   53.649554] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
[   54.510198] NET: Registered protocol family 17
[   69.497775] eth0: no IPv6 routers present
[  358.421431] snd: Unknown symbol unregister_sound_special
[  358.421518] snd: Unknown symbol register_sound_special_device
[  358.421747] snd: Unknown symbol sound_class
[  358.424462] snd_hwdep: Unknown symbol snd_info_register
[  358.424492] snd_hwdep: Unknown symbol snd_info_create_module_entry
[  358.424518] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[  358.424544] snd_hwdep: Unknown symbol snd_info_free_entry
[  358.424575] snd_hwdep: Unknown symbol snd_unregister_oss_device
[  358.424604] snd_hwdep: Unknown symbol snd_verbose_printk
[  358.424630] snd_hwdep: Unknown symbol snd_register_oss_device
[  358.424658] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[  358.424684] snd_hwdep: Unknown symbol snd_card_file_add
[  358.424716] snd_hwdep: Unknown symbol snd_iprintf
[  358.424741] snd_hwdep: Unknown symbol snd_major
[  358.424776] snd_hwdep: Unknown symbol snd_unregister_device
[  358.424805] snd_hwdep: Unknown symbol snd_device_new
[  358.424840] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[  358.424873] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[  358.424901] snd_hwdep: Unknown symbol snd_lookup_minor_data
[  358.424927] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[  358.424955] snd_hwdep: Unknown symbol snd_card_file_remove
[  358.424981] snd_hwdep: Unknown symbol snd_register_device_for_dev
[  358.427869] snd_timer: Unknown symbol snd_info_register
[  358.427897] snd_timer: Unknown symbol snd_info_create_module_entry
[  358.427926] snd_timer: Unknown symbol snd_info_free_entry
[  358.427975] snd_timer: Unknown symbol snd_verbose_printk
[  358.428008] snd_timer: Unknown symbol snd_iprintf
[  358.428046] snd_timer: Unknown symbol snd_ecards_limit
[  358.428076] snd_timer: Unknown symbol snd_oss_info_register
[  358.428102] snd_timer: Unknown symbol snd_unregister_device
[  358.428135] snd_timer: Unknown symbol snd_device_new
[  358.428195] snd_timer: Unknown symbol snd_register_device_for_dev
[  358.434395] snd: Unknown symbol unregister_sound_special
[  358.434483] snd: Unknown symbol register_sound_special_device
[  358.434714] snd: Unknown symbol sound_class
[  358.435238] snd_timer: Unknown symbol snd_info_register
[  358.435267] snd_timer: Unknown symbol snd_info_create_module_entry
[  358.435297] snd_timer: Unknown symbol snd_info_free_entry
[  358.435347] snd_timer: Unknown symbol snd_verbose_printk
[  358.435381] snd_timer: Unknown symbol snd_iprintf
[  358.435420] snd_timer: Unknown symbol snd_ecards_limit
[  358.435450] snd_timer: Unknown symbol snd_oss_info_register
[  358.435477] snd_timer: Unknown symbol snd_unregister_device
[  358.435510] snd_timer: Unknown symbol snd_device_new
[  358.435569] snd_timer: Unknown symbol snd_register_device_for_dev
[  358.436007] snd_pcm: Unknown symbol snd_info_register
[  358.436035] snd_pcm: Unknown symbol snd_info_create_module_entry
[  358.436062] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[  358.436110] snd_pcm: Unknown symbol snd_timer_notify
[  358.436144] snd_pcm: Unknown symbol snd_timer_interrupt
[  358.436171] snd_pcm: Unknown symbol snd_info_free_entry
[  358.436197] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[  358.436231] snd_pcm: Unknown symbol snd_info_get_str
[  358.436295] snd_pcm: Unknown symbol snd_verbose_printk
[  358.436351] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[  358.436377] snd_pcm: Unknown symbol snd_card_file_add
[  358.436411] snd_pcm: Unknown symbol snd_iprintf
[  358.436452] snd_pcm: Unknown symbol snd_major
[  358.436508] snd_pcm: Unknown symbol snd_unregister_device
[  358.436539] snd_pcm: Unknown symbol snd_timer_new
[  358.436565] snd_pcm: Unknown symbol snd_device_new
[  358.436614] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[  358.436657] snd_pcm: Unknown symbol snd_lookup_minor_data
[  358.436683] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[  358.436719] snd_pcm: Unknown symbol snd_info_create_card_entry
[  358.436746] snd_pcm: Unknown symbol snd_power_wait
[  358.436776] snd_pcm: Unknown symbol snd_device_free
[  358.436820] snd_pcm: Unknown symbol snd_card_file_remove
[  358.436846] snd_pcm: Unknown symbol snd_register_device_for_dev
[  358.436906] snd_pcm: Unknown symbol snd_device_register
[  358.436934] snd_pcm: Unknown symbol snd_info_get_line
[  358.438452] snd_hda_intel: Unknown symbol snd_ctl_add
[  358.438491] snd_hda_intel: Unknown symbol snd_pcm_new
[  358.438525] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  358.438553] snd_hda_intel: Unknown symbol snd_card_register
[  358.438579] snd_hda_intel: Unknown symbol snd_card_free
[  358.438604] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  358.438630] snd_hda_intel: Unknown symbol snd_card_proc_new
[  358.438712] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  358.438746] snd_hda_intel: Unknown symbol snd_verbose_printk
[  358.438789] snd_hda_intel: Unknown symbol snd_ctl_new1
[  358.438844] snd_hda_intel: Unknown symbol snd_component_add
[  358.438876] snd_hda_intel: Unknown symbol snd_card_new
[  358.438901] snd_hda_intel: Unknown symbol snd_iprintf
[  358.438930] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  358.438955] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[  358.438989] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  358.439018] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  358.439043] snd_hda_intel: Unknown symbol snd_hwdep_new
[  358.439073] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  358.439105] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  358.439138] snd_hda_intel: Unknown symbol snd_device_new
[  358.439178] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  358.439213] snd_hda_intel: Unknown symbol snd_card_disconnect
[  358.439238] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  358.439303] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[  358.439358] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  358.439383] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[  358.439426] snd_hda_intel: Unknown symbol snd_pcm_format_width
[  587.101161] snd: Unknown symbol unregister_sound_special
[  587.101250] snd: Unknown symbol register_sound_special_device
[  587.101478] snd: Unknown symbol sound_class
[  587.102303] snd_hwdep: Unknown symbol snd_hidden_kzalloc
[  587.102330] snd_hwdep: Unknown symbol snd_info_register
[  587.102356] snd_hwdep: Unknown symbol snd_info_create_module_entry
[  587.102382] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[  587.102407] snd_hwdep: Unknown symbol snd_info_free_entry
[  587.102435] snd_hwdep: Unknown symbol snd_hidden_kfree
[  587.102460] snd_hwdep: Unknown symbol snd_unregister_oss_device
[  587.102489] snd_hwdep: Unknown symbol snd_verbose_printk
[  587.102514] snd_hwdep: Unknown symbol snd_register_oss_device
[  587.102541] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[  587.102567] snd_hwdep: Unknown symbol snd_card_file_add
[  587.102595] snd_hwdep: Unknown symbol snd_iprintf
[  587.102620] snd_hwdep: Unknown symbol snd_major
[  587.102654] snd_hwdep: Unknown symbol snd_unregister_device
[  587.102682] snd_hwdep: Unknown symbol snd_device_new
[  587.102715] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[  587.102747] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[  587.102775] snd_hwdep: Unknown symbol snd_lookup_minor_data
[  587.102800] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[  587.102828] snd_hwdep: Unknown symbol snd_card_file_remove
[  587.102853] snd_hwdep: Unknown symbol snd_register_device_for_dev
[  587.105061] snd_timer: Unknown symbol snd_verbose_printd
[  587.105089] snd_timer: Unknown symbol snd_hidden_kzalloc
[  587.105114] snd_timer: Unknown symbol snd_info_register
[  587.105141] snd_timer: Unknown symbol snd_info_create_module_entry
[  587.105170] snd_timer: Unknown symbol snd_info_free_entry
[  587.105199] snd_timer: Unknown symbol snd_hidden_kfree
[  587.105240] snd_timer: Unknown symbol snd_verbose_printk
[  587.105270] snd_timer: Unknown symbol snd_iprintf
[  587.105308] snd_timer: Unknown symbol snd_ecards_limit
[  587.105337] snd_timer: Unknown symbol snd_oss_info_register
[  587.105362] snd_timer: Unknown symbol snd_unregister_device
[  587.105393] snd_timer: Unknown symbol snd_hidden_kstrdup
[  587.105418] snd_timer: Unknown symbol snd_device_new
[  587.105474] snd_timer: Unknown symbol snd_hidden_kmalloc
[  587.105500] snd_timer: Unknown symbol snd_register_device_for_dev
[  587.116572] snd: Unknown symbol unregister_sound_special
[  587.116659] snd: Unknown symbol register_sound_special_device
[  587.116882] snd: Unknown symbol sound_class
[  587.118062] snd_timer: Unknown symbol snd_verbose_printd
[  587.118089] snd_timer: Unknown symbol snd_hidden_kzalloc
[  587.118115] snd_timer: Unknown symbol snd_info_register
[  587.118141] snd_timer: Unknown symbol snd_info_create_module_entry
[  587.118170] snd_timer: Unknown symbol snd_info_free_entry
[  587.118200] snd_timer: Unknown symbol snd_hidden_kfree
[  587.118241] snd_timer: Unknown symbol snd_verbose_printk
[  587.118271] snd_timer: Unknown symbol snd_iprintf
[  587.118309] snd_timer: Unknown symbol snd_ecards_limit
[  587.118338] snd_timer: Unknown symbol snd_oss_info_register
[  587.118363] snd_timer: Unknown symbol snd_unregister_device
[  587.118394] snd_timer: Unknown symbol snd_hidden_kstrdup
[  587.118419] snd_timer: Unknown symbol snd_device_new
[  587.118475] snd_timer: Unknown symbol snd_hidden_kmalloc
[  587.118501] snd_timer: Unknown symbol snd_register_device_for_dev
[  587.120910] snd_pcm: Unknown symbol snd_verbose_printd
[  587.120940] snd_pcm: Unknown symbol snd_hidden_kzalloc
[  587.120965] snd_pcm: Unknown symbol snd_info_register
[  587.120991] snd_pcm: Unknown symbol snd_info_create_module_entry
[  587.121017] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[  587.121063] snd_pcm: Unknown symbol snd_timer_notify
[  587.121096] snd_pcm: Unknown symbol snd_timer_interrupt
[  587.121121] snd_pcm: Unknown symbol snd_info_free_entry
[  587.121147] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[  587.121176] snd_pcm: Unknown symbol snd_info_get_str
[  587.121202] snd_pcm: Unknown symbol snd_hidden_kcalloc
[  587.121229] snd_pcm: Unknown symbol snd_hidden_kfree
[  587.121291] snd_pcm: Unknown symbol snd_verbose_printk
[  587.121346] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[  587.121372] snd_pcm: Unknown symbol snd_card_file_add
[  587.121401] snd_pcm: Unknown symbol snd_iprintf
[  587.121441] snd_pcm: Unknown symbol snd_major
[  587.121496] snd_pcm: Unknown symbol snd_unregister_device
[  587.121526] snd_pcm: Unknown symbol snd_timer_new
[  587.121551] snd_pcm: Unknown symbol snd_device_new
[  587.121622] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[  587.121664] snd_pcm: Unknown symbol snd_lookup_minor_data
[  587.121690] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[  587.121724] snd_pcm: Unknown symbol snd_info_create_card_entry
[  587.121750] snd_pcm: Unknown symbol snd_power_wait
[  587.121779] snd_pcm: Unknown symbol snd_hidden_kmalloc
[  587.121805] snd_pcm: Unknown symbol snd_device_free
[  587.121847] snd_pcm: Unknown symbol snd_card_file_remove
[  587.121873] snd_pcm: Unknown symbol snd_register_device_for_dev
[  587.121931] snd_pcm: Unknown symbol snd_device_register
[  587.121958] snd_pcm: Unknown symbol snd_info_get_line
[  587.128452] snd_hda_intel: Unknown symbol snd_verbose_printd
[  587.128483] snd_hda_intel: Unknown symbol snd_hidden_kzalloc
[  587.128526] snd_hda_intel: Unknown symbol snd_ctl_add
[  587.128568] snd_hda_intel: Unknown symbol snd_pcm_new
[  587.128601] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  587.128629] snd_hda_intel: Unknown symbol snd_card_register
[  587.128655] snd_hda_intel: Unknown symbol snd_card_free
[  587.128681] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  587.128707] snd_hda_intel: Unknown symbol snd_card_proc_new
[  587.128764] snd_hda_intel: Unknown symbol snd_hidden_kcalloc
[  587.128797] snd_hda_intel: Unknown symbol snd_hidden_kfree
[  587.128837] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  587.128871] snd_hda_intel: Unknown symbol snd_verbose_printk
[  587.128916] snd_hda_intel: Unknown symbol snd_ctl_new1
[  587.128971] snd_hda_intel: Unknown symbol snd_component_add
[  587.128999] snd_hda_intel: Unknown symbol snd_card_new
[  587.129024] snd_hda_intel: Unknown symbol snd_iprintf
[  587.129053] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  587.129078] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[  587.129113] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  587.129141] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  587.129166] snd_hda_intel: Unknown symbol snd_hwdep_new
[  587.129196] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  587.129229] snd_hda_intel: Unknown symbol snd_hidden_kstrdup
[  587.129254] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  587.129295] snd_hda_intel: Unknown symbol snd_device_new
[  587.129321] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[  587.129360] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  587.129393] snd_hda_intel: Unknown symbol snd_card_disconnect
[  587.129419] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  587.129483] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[  587.129522] snd_hda_intel: Unknown symbol snd_hidden_kmalloc
[  587.129565] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  587.129621] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[  587.129657] snd_hda_intel: Unknown symbol snd_pcm_format_width
[  675.055149] snd: Unknown symbol unregister_sound_special
[  675.055238] snd: Unknown symbol register_sound_special_device
[  675.055463] snd: Unknown symbol sound_class
[  675.056286] snd_hwdep: Unknown symbol snd_hidden_kzalloc
[  675.056315] snd_hwdep: Unknown symbol snd_info_register
[  675.056342] snd_hwdep: Unknown symbol snd_info_create_module_entry
[  675.056369] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.056396] snd_hwdep: Unknown symbol snd_info_free_entry
[  675.056425] snd_hwdep: Unknown symbol snd_hidden_kfree
[  675.056451] snd_hwdep: Unknown symbol snd_unregister_oss_device
[  675.056482] snd_hwdep: Unknown symbol snd_verbose_printk
[  675.056509] snd_hwdep: Unknown symbol snd_register_oss_device
[  675.056537] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[  675.056563] snd_hwdep: Unknown symbol snd_card_file_add
[  675.056593] snd_hwdep: Unknown symbol snd_iprintf
[  675.056620] snd_hwdep: Unknown symbol snd_major
[  675.056655] snd_hwdep: Unknown symbol snd_unregister_device
[  675.056685] snd_hwdep: Unknown symbol snd_device_new
[  675.056719] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[  675.056752] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[  675.056781] snd_hwdep: Unknown symbol snd_lookup_minor_data
[  675.056808] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[  675.056837] snd_hwdep: Unknown symbol snd_card_file_remove
[  675.056863] snd_hwdep: Unknown symbol snd_register_device_for_dev
[  675.057413] snd_timer: Unknown symbol snd_verbose_printd
[  675.057442] snd_timer: Unknown symbol snd_hidden_kzalloc
[  675.057467] snd_timer: Unknown symbol snd_info_register
[  675.057493] snd_timer: Unknown symbol snd_info_create_module_entry
[  675.057522] snd_timer: Unknown symbol snd_info_free_entry
[  675.057553] snd_timer: Unknown symbol snd_hidden_kfree
[  675.057596] snd_timer: Unknown symbol snd_verbose_printk
[  675.057628] snd_timer: Unknown symbol snd_iprintf
[  675.057667] snd_timer: Unknown symbol snd_ecards_limit
[  675.057698] snd_timer: Unknown symbol snd_oss_info_register
[  675.057725] snd_timer: Unknown symbol snd_unregister_device
[  675.057757] snd_timer: Unknown symbol snd_hidden_kstrdup
[  675.057784] snd_timer: Unknown symbol snd_device_new
[  675.057841] snd_timer: Unknown symbol snd_hidden_kmalloc
[  675.057868] snd_timer: Unknown symbol snd_register_device_for_dev
[  675.067213] snd: Unknown symbol unregister_sound_special
[  675.067300] snd: Unknown symbol register_sound_special_device
[  675.067527] snd: Unknown symbol sound_class
[  675.068557] snd_timer: Unknown symbol snd_verbose_printd
[  675.068585] snd_timer: Unknown symbol snd_hidden_kzalloc
[  675.068611] snd_timer: Unknown symbol snd_info_register
[  675.068637] snd_timer: Unknown symbol snd_info_create_module_entry
[  675.068666] snd_timer: Unknown symbol snd_info_free_entry
[  675.068696] snd_timer: Unknown symbol snd_hidden_kfree
[  675.068737] snd_timer: Unknown symbol snd_verbose_printk
[  675.068767] snd_timer: Unknown symbol snd_iprintf
[  675.068805] snd_timer: Unknown symbol snd_ecards_limit
[  675.068834] snd_timer: Unknown symbol snd_oss_info_register
[  675.068860] snd_timer: Unknown symbol snd_unregister_device
[  675.068890] snd_timer: Unknown symbol snd_hidden_kstrdup
[  675.068915] snd_timer: Unknown symbol snd_device_new
[  675.068972] snd_timer: Unknown symbol snd_hidden_kmalloc
[  675.068997] snd_timer: Unknown symbol snd_register_device_for_dev
[  675.072053] snd_pcm: Unknown symbol snd_verbose_printd
[  675.072087] snd_pcm: Unknown symbol snd_hidden_kzalloc
[  675.072114] snd_pcm: Unknown symbol snd_info_register
[  675.072142] snd_pcm: Unknown symbol snd_info_create_module_entry
[  675.072169] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.072219] snd_pcm: Unknown symbol snd_timer_notify
[  675.072253] snd_pcm: Unknown symbol snd_timer_interrupt
[  675.072279] snd_pcm: Unknown symbol snd_info_free_entry
[  675.072305] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[  675.072335] snd_pcm: Unknown symbol snd_info_get_str
[  675.072360] snd_pcm: Unknown symbol snd_hidden_kcalloc
[  675.072388] snd_pcm: Unknown symbol snd_hidden_kfree
[  675.072449] snd_pcm: Unknown symbol snd_verbose_printk
[  675.072505] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[  675.072531] snd_pcm: Unknown symbol snd_card_file_add
[  675.072559] snd_pcm: Unknown symbol snd_iprintf
[  675.072600] snd_pcm: Unknown symbol snd_major
[  675.072656] snd_pcm: Unknown symbol snd_unregister_device
[  675.072686] snd_pcm: Unknown symbol snd_timer_new
[  675.072711] snd_pcm: Unknown symbol snd_device_new
[  675.072759] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[  675.072800] snd_pcm: Unknown symbol snd_lookup_minor_data
[  675.072826] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[  675.072861] snd_pcm: Unknown symbol snd_info_create_card_entry
[  675.072886] snd_pcm: Unknown symbol snd_power_wait
[  675.072916] snd_pcm: Unknown symbol snd_hidden_kmalloc
[  675.072941] snd_pcm: Unknown symbol snd_device_free
[  675.072983] snd_pcm: Unknown symbol snd_card_file_remove
[  675.073010] snd_pcm: Unknown symbol snd_register_device_for_dev
[  675.073068] snd_pcm: Unknown symbol snd_device_register
[  675.073095] snd_pcm: Unknown symbol snd_info_get_line
[  675.079606] snd_hda_intel: Unknown symbol snd_verbose_printd
[  675.079642] snd_hda_intel: Unknown symbol snd_hidden_kzalloc
[  675.079688] snd_hda_intel: Unknown symbol snd_ctl_add
[  675.079731] snd_hda_intel: Unknown symbol snd_pcm_new
[  675.079767] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  675.079796] snd_hda_intel: Unknown symbol snd_card_register
[  675.079821] snd_hda_intel: Unknown symbol snd_card_free
[  675.079847] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  675.079873] snd_hda_intel: Unknown symbol snd_card_proc_new
[  675.079931] snd_hda_intel: Unknown symbol snd_hidden_kcalloc
[  675.079965] snd_hda_intel: Unknown symbol snd_hidden_kfree
[  675.080006] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  675.080041] snd_hda_intel: Unknown symbol snd_verbose_printk
[  675.080088] snd_hda_intel: Unknown symbol snd_ctl_new1
[  675.080143] snd_hda_intel: Unknown symbol snd_component_add
[  675.080172] snd_hda_intel: Unknown symbol snd_card_new
[  675.080198] snd_hda_intel: Unknown symbol snd_iprintf
[  675.080226] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  675.080253] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[  675.080288] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  675.080316] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  675.080342] snd_hda_intel: Unknown symbol snd_hwdep_new
[  675.080372] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  675.080406] snd_hda_intel: Unknown symbol snd_hidden_kstrdup
[  675.080433] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  675.080475] snd_hda_intel: Unknown symbol snd_device_new
[  675.080501] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[  675.080541] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  675.080575] snd_hda_intel: Unknown symbol snd_card_disconnect
[  675.080601] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  675.080667] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[  675.080706] snd_hda_intel: Unknown symbol snd_hidden_kmalloc
[  675.080751] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  675.080798] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[  675.080839] snd_hda_intel: Unknown symbol snd_pcm_format_width
dam4nn@dam4nn-desktop:~$ 

```

Any ideas?

---

