---
title: "DVB-C video corrupted after ATI binary driver install"
date: 2008-09-17
forum: Multimedia Software
---

### Post by midas80 on 2008-09-17
Hi all,
I was previously running gxine successfully on my Hardy installation using my Terratec Cinergy PCI DVB-C card. (after installing mantis drivers...) I was then using the onboard nvidia 7100 graphics card with proprietary drivers.

So today I got my new Saphire Radeon HD 4850 graphics card and installed it. After some fiddling about and with the help of 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
I got the card recognized and working.

However when I start up gxine to watch tv the video is corrupted, greenish and half of the image messed up. If I use the mesa drives then the image is fine. The audio is constantly ok.

Does anyone have a clue how to approach the problem?

ps. my first post here on ubuntuforums.org

---

### Post by midas80 on 2008-09-17
Some more information about my system:

$ lspci 
01:07.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)
02:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.7873 Release

$ glxgears 
36853 frames in 5.0 seconds = 7370.409 FPS
36834 frames in 5.0 seconds = 7366.781 FPS
36607 frames in 5.0 seconds = 7321.346 FPS

and complete dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 17:53:40 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] Command line: root=UUID=4bd07d8b-63b7-4c76-ac39-29578201cdf2 ro quiet splash vga=0x0318
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524016) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.5 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7D10 checksum 0
[    0.000000] ACPI: RSDP 000F7D10, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FEF3000, 0038 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEF3080, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20070126]
[    0.000000] ACPI: DSDT 7FEF3100, 5793 (r1 NVIDIA AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FEF1800, 0040
[    0.000000] ACPI: HPET 7FEF8980, 0038 (r1 Nvidia AWRDACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 7FEF89C0, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEF88C0, 0098 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 7FEF9320, 0380 (r1  PmRef    CpuPm     3000 INTL 20041203)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fef0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524016) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fef0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524016
[    0.000000] On node 0 totalpages: 523919
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1235 pages reserved
[    0.000000]   DMA zone: 2708 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7108 pages used for memmap
[    0.000000]   DMA32 zone: 512812 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
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
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515520
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=4bd07d8b-63b7-4c76-ac39-29578201cdf2 ro quiet splash vga=0x0318
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   21.723408] time.c: Detected 2399.999 MHz processor.
[   21.724416] Console: colour VGA+ 80x25
[   21.724419] console [tty0] enabled
[   21.724434] Checking aperture...
[   21.724443] Calgary: detecting Calgary via BIOS EBDA area
[   21.724444] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   21.740806] Memory: 2052632k/2096064k available (2489k kernel code, 43044k reserved, 1318k data, 320k init)
[   21.740840] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   21.817248] Calibrating delay using timer specific routine.. 4804.82 BogoMIPS (lpj=9609641)
[   21.817277] Security Framework initialized
[   21.817283] SELinux:  Disabled at boot.
[   21.817293] AppArmor: AppArmor initialized
[   21.817296] Failure registering capabilities with primary security module.
[   21.817451] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   21.818746] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.819304] Mount-cache hash table entries: 256
[   21.819417] Initializing cgroup subsys ns
[   21.819422] Initializing cgroup subsys cpuacct
[   21.819434] CPU: L1 I cache: 32K, L1 D cache: 32K
[   21.819435] CPU: L2 cache: 4096K
[   21.819437] CPU 0/0 -> Node 0
[   21.819438] using mwait in idle threads.
[   21.819440] CPU: Physical Processor ID: 0
[   21.819441] CPU: Processor Core ID: 0
[   21.819446] CPU0: Thermal monitoring enabled (TM2)
[   21.819457] SMP alternatives: switching to UP code
[   21.820085] Early unpacking initramfs... done
[   22.129884] ACPI: Core revision 20070126
[   22.129917] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.175606] Using local APIC timer interrupts.
[   22.217211] APIC timer calibration result 16666668
[   22.217212] Detected 16.666 MHz APIC timer.
[   22.217276] SMP alternatives: switching to SMP code
[   22.217811] Booting processor 1/4 APIC 0x3
[   22.228156] Initializing CPU#1
[   22.305078] Calibrating delay using timer specific routine.. 4800.07 BogoMIPS (lpj=9600149)
[   22.305083] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.305084] CPU: L2 cache: 4096K
[   22.305086] CPU 1/3 -> Node 0
[   22.305087] CPU: Physical Processor ID: 0
[   22.305088] CPU: Processor Core ID: 3
[   22.305093] CPU1: Thermal monitoring enabled (TM2)
[   22.305488] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   22.305527] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   22.325558] SMP alternatives: switching to SMP code
[   22.325936] Booting processor 2/4 APIC 0x1
[   22.336353] Initializing CPU#2
[   22.412908] Calibrating delay using timer specific routine.. 4800.02 BogoMIPS (lpj=9600046)
[   22.412913] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.412914] CPU: L2 cache: 4096K
[   22.412916] CPU 2/1 -> Node 0
[   22.412917] CPU: Physical Processor ID: 0
[   22.412918] CPU: Processor Core ID: 1
[   22.412923] CPU2: Thermal monitoring enabled (TM2)
[   22.413314] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   22.413352] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   22.433393] SMP alternatives: switching to SMP code
[   22.433956] Booting processor 3/4 APIC 0x2
[   22.444301] Initializing CPU#3
[   22.524732] Calibrating delay using timer specific routine.. 4800.06 BogoMIPS (lpj=9600126)
[   22.524737] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.524738] CPU: L2 cache: 4096K
[   22.524740] CPU 3/2 -> Node 0
[   22.524741] CPU: Physical Processor ID: 0
[   22.524742] CPU: Processor Core ID: 2
[   22.524747] CPU3: Thermal monitoring enabled (TM2)
[   22.525141] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   22.525172] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   22.545158] Brought up 4 CPUs
[   22.545260] CPU0 attaching sched-domain:
[   22.545262]  domain 0: span 05
[   22.545263]   groups: 01 04
[   22.545265]   domain 1: span 0f
[   22.545266]    groups: 05 0a
[   22.545268]    domain 2: span 0f
[   22.545269]     groups: 0f
[   22.545270] CPU1 attaching sched-domain:
[   22.545271]  domain 0: span 0a
[   22.545272]   groups: 02 08
[   22.545274]   domain 1: span 0f
[   22.545275]    groups: 0a 05
[   22.545277]    domain 2: span 0f
[   22.545278]     groups: 0f
[   22.545279] CPU2 attaching sched-domain:
[   22.545280]  domain 0: span 05
[   22.545281]   groups: 04 01
[   22.545283]   domain 1: span 0f
[   22.545284]    groups: 05 0a
[   22.545285]    domain 2: span 0f
[   22.545287]     groups: 0f
[   22.545288] CPU3 attaching sched-domain:
[   22.545289]  domain 0: span 0a
[   22.545290]   groups: 08 02
[   22.545292]   domain 1: span 0f
[   22.545293]    groups: 0a 05
[   22.545294]    domain 2: span 0f
[   22.545295]     groups: 0f
[   22.545554] net_namespace: 120 bytes
[   22.545863] Time: 18:02:08  Date: 09/17/08
[   22.545881] NET: Registered protocol family 16
[   22.546021] ACPI: bus type pci registered
[   22.546075] PCI: Using configuration type 1
[   22.547202] ACPI: EC: Look up EC in DSDT
[   22.552355] ACPI: Interpreter enabled
[   22.552357] ACPI: (supports S0 S3 S4 S5)
[   22.552369] ACPI: Using IOAPIC for interrupt routing
[   22.559640] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.561000] PCI: Transparent bridge - 0000:00:0a.0
[   22.561148] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.561364] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   22.601163] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.601299] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.601433] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.601569] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
[   22.601702] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.601839] ACPI: PCI Interrupt Link [LNK6] (IRQs *5 7 9 10 11 14 15)
[   22.601973] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 *11 14 15)
[   22.602106] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.602240] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.602373] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.602508] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   22.602641] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   22.602774] ACPI: PCI Interrupt Link [LU1B] (IRQs 5 7 9 10 11 14 15) *0
[   22.602907] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 10 11 14 15) *0
[   22.603044] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[   22.603181] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[   22.603319] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.603454] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[   22.603590] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.603725] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   22.603889] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   22.604046] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   22.604202] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   22.604359] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   22.604514] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   22.604678] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
[   22.604835] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[   22.604991] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   22.605147] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
[   22.605304] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[   22.605460] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
[   22.605617] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
[   22.605773] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
[   22.605931] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   22.606089] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   22.606247] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   22.606404] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   22.606561] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   22.606719] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   22.606879] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   22.606979] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.607000] pnp: PnP ACPI init
[   22.607005] ACPI: bus type pnp registered
[   22.610426] pnp: PnP ACPI: found 12 devices
[   22.610428] ACPI: ACPI bus type pnp unregistered
[   22.610593] PCI: Using ACPI for IRQ routing
[   22.610596] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.620669] NET: Registered protocol family 8
[   22.620671] NET: Registered protocol family 20
[   22.620707] PCI-GART: No AMD northbridge found.
[   22.620713] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   22.620717] hpet0: 3 32-bit timers, 25000000 Hz
[   22.621745] AppArmor: AppArmor Filesystem Enabled
[   22.624633] Time: tsc clocksource has been installed.
[   22.624641] Switched to high resolution mode on CPU 0
[   22.625102] Switched to high resolution mode on CPU 2
[   22.625507] Switched to high resolution mode on CPU 3
[   22.625808] Switched to high resolution mode on CPU 1
[   22.632637] system 00:01: ioport range 0x1000-0x107f has been reserved
[   22.632641] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   22.632644] system 00:01: ioport range 0x1400-0x147f has been reserved
[   22.632648] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   22.632651] system 00:01: ioport range 0x1800-0x187f has been reserved
[   22.632654] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   22.632658] system 00:01: iomem range 0xfec80000-0xfecbffff has been reserved
[   22.632661] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   22.632665] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[   22.632668] system 00:01: iomem range 0x0-0x0 could not be reserved
[   22.632674] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   22.632677] system 00:02: ioport range 0x290-0x30f has been reserved
[   22.632681] system 00:02: ioport range 0x880-0x88f has been reserved
[   22.632690] system 00:0a: iomem range 0xf0000000-0xf1ffffff could not be reserved
[   22.632697] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[   22.632700] system 00:0b: iomem range 0xfeff0000-0xfeff00ff has been reserved
[   22.632704] system 00:0b: iomem range 0x7fef0000-0x7fefffff could not be reserved
[   22.632707] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[   22.632710] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   22.632713] system 00:0b: iomem range 0x100000-0x7feeffff could not be reserved
[   22.632717] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   22.632720] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   22.632724] system 00:0b: iomem range 0xfeff0000-0xfeff03ff could not be reserved
[   22.633028] PCI: Bridge: 0000:00:0a.0
[   22.633029]   IO window: e000-efff
[   22.633032]   MEM window: efc00000-efcfffff
[   22.633035]   PREFETCH window: efe00000-efefffff
[   22.633038] PCI: Bridge: 0000:00:0b.0
[   22.633040]   IO window: d000-dfff
[   22.633042]   MEM window: efd00000-efdfffff
[   22.633044]   PREFETCH window: d0000000-dfffffff
[   22.633052] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   22.633061] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   22.633067] NET: Registered protocol family 2
[   22.668642] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   22.669148] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   22.670546] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   22.670998] TCP: Hash tables configured (established 262144 bind 65536)
[   22.671000] TCP reno registered
[   22.680705] checking if image is initramfs... it is
[   23.289823] Freeing initrd memory: 9229k freed
[   23.296282] audit: initializing netlink socket (disabled)
[   23.296297] audit(1221674528.492:1): initialized
[   23.298785] VFS: Disk quotas dquot_6.5.1
[   23.298863] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   23.298982] io scheduler noop registered
[   23.298984] io scheduler anticipatory registered
[   23.298986] io scheduler deadline registered
[   23.299106] io scheduler cfq registered (default)
[   23.303169] Boot video device is 0000:02:00.0
[   23.303348] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.303382] assign_interrupt_mode Found MSI capability
[   23.303411] Allocate Port Service[0000:00:0b.0:pcie00]
[   23.332740] Real Time Clock Driver v1.12ac
[   23.332933] hpet_resources: 0xfeff0000 is busy
[   23.332967] Linux agpgart interface v0.102
[   23.332969] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.334253] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.334337] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.334437] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   23.334439] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   23.334883] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.353037] mice: PS/2 mouse device common for all mice
[   23.353082] cpuidle: using governor ladder
[   23.353084] cpuidle: using governor menu
[   23.353219] NET: Registered protocol family 1
[   23.353319] registered taskstats version 1
[   23.353425]   Magic number: 8:167:39
[   23.353458]   hash matches device 00:0b
[   23.353468] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   23.353471] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.353473] EDD information not available.
[   23.353483] Freeing unused kernel memory: 320k freed
[   23.388062] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   24.505214] fuse init (API version 7.9)
[   24.514544] ACPI: Fan [FAN] (on)
[   24.518374] ACPI: SSDT 7FEF8A40, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
[   24.518663] ACPI: SSDT 7FEF8F00, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[   24.518917] ACPI: SSDT 7FEF9060, 0152 (r1  PmRef  Cpu2Ist     3000 INTL 20041203)
[   24.519177] ACPI: SSDT 7FEF91C0, 0152 (r1  PmRef  Cpu3Ist     3000 INTL 20041203)
[   24.917078] ACPI: Thermal Zone [THRM] (43 C)
[   25.133620] usbcore: registered new interface driver usbfs
[   25.133640] usbcore: registered new interface driver hub
[   25.133813] SCSI subsystem initialized
[   25.147827] usbcore: registered new device driver usb
[   25.153138] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   25.153457] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   25.153464] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   25.153469] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   25.154364] Floppy drive(s): fd0 is 1.44M
[   25.155479] libata version 3.00 loaded.
[   25.156746] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.173954] FDC 0 is a post-1991 82077
[   25.672588] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:50:8d:b6:ba:0f
[   25.672591] forcedeth 0000:00:0f.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[   25.672969] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
[   25.672976] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [AUB2] -> GSI 22 (level, low) -> IRQ 22
[   25.674273] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   25.674278] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   25.674468] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[   25.674496] ehci_hcd 0000:00:04.1: debug port 1
[   25.674500] PCI: cache line size of 32 is not supported by device 0000:00:04.1
[   25.674508] ehci_hcd 0000:00:04.1: irq 22, io mem 0xefffe000
[   25.683680] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.683793] usb usb1: configuration #1 chosen from 1 choice
[   25.683815] hub 1-0:1.0: USB hub found
[   25.683821] hub 1-0:1.0: 10 ports detected
[   25.787920] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 21
[   25.787926] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [AUBA] -> GSI 21 (level, low) -> IRQ 21
[   25.788637] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   25.788641] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   25.788679] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[   25.788694] ohci_hcd 0000:00:04.0: irq 21, io mem 0xeffff000
[   25.845487] usb usb2: configuration #1 chosen from 1 choice
[   25.845505] hub 2-0:1.0: USB hub found
[   25.845511] hub 2-0:1.0: 10 ports detected
[   25.948891] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   25.949172] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   25.949178] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   25.949194] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   25.949200] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[   25.950556] ahci 0000:00:0e.0: version 3.0
[   25.950562] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   26.274795] usb 2-2: new low speed USB device using ohci_hcd and address 2
[   26.498490] usb 2-2: configuration #1 chosen from 1 choice
[   26.510207] usbcore: registered new interface driver hiddev
[   26.518618] input: Microsoft Microsoft Wheel Mouse Optical® as /devices/pci0000:00/0000:00:04.0/usb2/2-2/2-2:1.0/input/input2
[   26.534330] input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical®] on usb-0000:00:04.0-2
[   26.534345] usbcore: registered new interface driver usbhid
[   26.534349] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   26.949619] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   26.949623] ahci 0000:00:0e.0: flags: 64bit sntf led clo pmp pio 
[   26.949628] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   26.950223] scsi0 : ahci
[   26.950364] scsi1 : ahci
[   26.950508] scsi2 : ahci
[   26.950646] scsi3 : ahci
[   26.950709] ata1: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8100 irq 510
[   26.950711] ata2: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8180 irq 510
[   26.950713] ata3: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8200 irq 510
[   26.950715] ata4: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8280 irq 510
[   27.270101] ata1: SATA link down (SStatus 0 SControl 300)
[   27.592573] ata2: SATA link down (SStatus 0 SControl 300)
[   28.231540] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   28.272391] ata3.00: ATA-7: ST3250820SCE, 3.ACD, max UDMA/133
[   28.272394] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   28.330613] ata3.00: configured for UDMA/133
[   28.646863] ata4: SATA link down (SStatus 0 SControl 300)
[   28.646975] scsi 2:0:0:0: Direct-Access     ATA      ST3250820SCE     3.AC PQ: 0 ANSI: 5
[   28.647074] pata_amd 0000:00:08.0: version 0.3.10
[   28.647121] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   28.647278] scsi4 : pata_amd
[   28.647412] scsi5 : pata_amd
[   28.647865] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   28.647867] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   28.651888] Driver 'sd' needs updating - please use bus_type methods
[   28.651949] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   28.651957] sd 2:0:0:0: [sda] Write Protect is off
[   28.651958] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.651969] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.652008] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   28.652014] sd 2:0:0:0: [sda] Write Protect is off
[   28.652016] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.652026] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.652029]  sda: sda1 sda2 < sda5 sda6 >
[   28.732549] sd 2:0:0:0: [sda] Attached SCSI disk
[   28.735216] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   28.966618] ata5.00: ATAPI: TSSTcorp CDDVDW SH-S202J, SB01, max UDMA/66
[   29.138285] ata5.00: configured for UDMA/66
[   29.138340] ata6: port disabled. ignoring.
[   29.139028] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202J  SB01 PQ: 0 ANSI: 5
[   29.139113] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   29.143388] Driver 'sr' needs updating - please use bus_type methods
[   29.147705] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   29.147708] Uniform CD-ROM driver Revision: 3.20
[   29.147764] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   34.351759] kjournald starting.  Commit interval 5 seconds
[   34.351762] EXT3-fs: mounted filesystem with ordered data mode.
[   40.337378] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.371454] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.398659] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   40.452440] input: Power Button (FF) as /devices/virtual/input/input4
[   40.507649] ACPI: Power Button (FF) [PWRF]
[   40.507696] input: Power Button (CM) as /devices/virtual/input/input5
[   40.571543] ACPI: Power Button (CM) [PWRB]
[   41.200920] ACPI: WMI-Acer: Mapper loaded
[   41.379927] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   41.394646] [fglrx] Maximum main memory to use for locked dma buffers: 1886 MBytes.
[   41.394771] [fglrx]   vendor: 1002 device: 9442 count: 1
[   41.394875] [fglrx] ioport: bar 4, base 0xde00, size: 0x100
[   41.395185] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   41.395193] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 16
[   41.395198] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   41.400401] [fglrx] PAT is enabled successfully!
[   41.400421] [fglrx] module loaded - fglrx 8.52.3 [Aug  1 2008] with 1 minors
[   41.439648] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   41.439655] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   41.439669] PCI: Setting latency timer of device 0000:01:07.0 to 64
[   41.439674] irq: 19, latency: 64
[   41.439675]  memory: 0xefeff000, mmio: 0xffffc200008b4000
[   41.439677] found a VP-2040 PCI DVB-C device on (01:07.0),
[   41.439678]     Mantis Rev 1 [153b:1178], irq: 19, latency: 64
[   41.439679]     memory: 0xefeff000, mmio: 0xffffc200008b4000
[   41.442373]     MAC Address=[00:08:ca:1d:3c:17]
[   41.442388] mantis_alloc_buffers (0): DMA=0x7bb10000 cpu=0xffff81007bb10000 size=65536
[   41.442442] mantis_alloc_buffers (0): RISC=0x7cd98000 cpu=0xffff81007cd98000 size=1000
[   41.442494] DVB: registering new adapter (Mantis dvb adapter)
[   41.523668] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   41.523671] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 23
[   41.524757] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   41.560674] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   41.957370] mantis_frontend_init (0): Probing for CU1216 (DVB-C)
[   41.959528] mantis_frontend_init (0): found Philips CU1216 DVB-C frontend (TDA10023) @ 0x0c
[   41.959579] mantis_frontend_init (0): Mantis DVB-C Philips CU1216 frontend attach success
[   41.959631] DVB: registering frontend 0 (Philips TDA10023 DVB-C)...
[   41.959659] mantis_ca_init (0): Registering EN50221 device
[   41.959754] mantis_ca_init (0): Registered EN50221 device
[   41.959817] mantis_hif_init (0): Adapter(0) Initializing Mantis Host Interface
[   41.960517] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   41.960520] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 16
[   41.961244] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   42.467416] loop: module loaded
[   42.514393] lp: driver loaded but no devices found
[   42.714194] Adding 5269280k swap on /dev/sda6.  Priority:-1 extents:1 across:5269280k
[   43.020473] EXT3 FS on sda5, internal journal
[   43.198069] device-mapper: uevent: version 1.0.3
[   43.198095] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   44.027577] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.387432] No dock devices found.
[   46.010255] NET: Registered protocol family 10
[   46.010430] lo: Disabled Privacy Extensions
[   46.616595] ppdev: user-space parallel port driver
[   46.721527] audit(1221663752.321:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5690 profile="/usr/sbin/cupsd" namespace="default"
[   50.629928] Bluetooth: Core ver 2.11
[   50.630187] NET: Registered protocol family 31
[   50.630194] Bluetooth: HCI device and connection manager initialized
[   50.630197] Bluetooth: HCI socket layer initialized
[   50.647859] Bluetooth: L2CAP ver 2.9
[   50.647866] Bluetooth: L2CAP socket layer initialized
[   50.682877] Bluetooth: RFCOMM socket layer initialized
[   50.682896] Bluetooth: RFCOMM TTY layer initialized
[   50.682900] Bluetooth: RFCOMM ver 1.8
[   52.235562] /dev/vmmon[6319]: Module vmmon: registered with major=10 minor=165
[   52.235579] /dev/vmmon[6319]: Module vmmon: initialized
[   52.760117] /dev/vmnet: open called by PID 6351 (vmnet-bridge)
[   52.760127] /dev/vmnet: hub 0 does not exist, allocating memory.
[   52.760139] /dev/vmnet: port on hub 0 successfully opened
[   52.760154] bridge-eth0: enabling the bridge
[   52.760158] bridge-eth0: up
[   52.760161] bridge-eth0: already up
[   52.760165] bridge-eth0: attached
[   52.970595] /dev/vmnet: open called by PID 6370 (vmnet-natd)
[   52.970716] /dev/vmnet: hub 8 does not exist, allocating memory.
[   52.970822] /dev/vmnet: port on hub 8 successfully opened
[   52.971897] /dev/vmnet: open called by PID 6372 (vmnet-netifup)
[   52.971905] /dev/vmnet: port on hub 8 successfully opened
[   52.972534] /dev/vmnet: open called by PID 6371 (vmnet-netifup)
[   52.972541] /dev/vmnet: hub 1 does not exist, allocating memory.
[   52.972552] /dev/vmnet: port on hub 1 successfully opened
[   53.695279] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   53.695287] [fglrx] Reserved FB block: Unshared offset:ff7f000, size:80000 
[   53.762347] /dev/vmnet: open called by PID 6462 (vmnet-dhcpd)
[   53.762362] /dev/vmnet: port on hub 1 successfully opened
[   53.763434] /dev/vmnet: open called by PID 6461 (vmnet-dhcpd)
[   53.763444] /dev/vmnet: port on hub 8 successfully opened
[   54.132052] NET: Registered protocol family 17
[   63.534253] vmnet8: no IPv6 routers present
[   63.953577] vmnet1: no IPv6 routers present
[   65.786626] eth0: no IPv6 routers present
[  239.560705] usb 2-2: reset low speed USB device using ohci_hcd and address 2
[  239.888173] usb 2-2: device descriptor read/64, error -62
[  240.319472] usb 2-2: device descriptor read/64, error -62
[  240.746780] usb 2-2: reset low speed USB device using ohci_hcd and address 2
[  241.078241] usb 2-2: device descriptor read/64, error -62
[  241.505548] usb 2-2: device descriptor read/64, error -62
[  241.936848] usb 2-2: reset low speed USB device using ohci_hcd and address 2
[  242.344187] usb 2-2: device not accepting address 2, error -62
[  242.667664] usb 2-2: reset low speed USB device using ohci_hcd and address 2
[  243.074998] usb 2-2: device not accepting address 2, error -62
[  243.075015] usb 2-2: USB disconnect, address 2
[  243.286659] usb 2-2: new low speed USB device using ohci_hcd and address 3
[  243.466368] usb 2-2: device descriptor read/64, error -62
[  243.749906] usb 2-2: device descriptor read/64, error -62
[  244.029456] usb 2-2: new low speed USB device using ohci_hcd and address 4
[  244.209163] usb 2-2: device descriptor read/64, error -62
[  244.492701] usb 2-2: device descriptor read/64, error -62
[  244.772250] usb 2-2: new low speed USB device using ohci_hcd and address 5
[  245.179590] usb 2-2: device not accepting address 5, error -62
[  245.355302] usb 2-2: new low speed USB device using ohci_hcd and address 6
[  245.762640] usb 2-2: device not accepting address 6, error -62
[  310.965578] usb 2-5: new low speed USB device using ohci_hcd and address 7
[  311.187639] usb 2-5: configuration #1 chosen from 1 choice
[  311.200777] input: Microsoft Microsoft Wheel Mouse Optical® as /devices/pci0000:00/0000:00:04.0/usb2/2-5/2-5:1.0/input/input6
[  311.240445] input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical®] on usb-0000:00:04.0-5

```

---

### Post by midas80 on 2008-09-17
Now GDM crashed when I was changing channels in kaffeine.

Is there some way I can find logs of the crash, or record the text output from kaffeine to see what caused the crash?

---

### Post by midas80 on 2008-09-29
Still having the same problems. 

When the ati driver is not in use and using mesa drivers watching dvb-c works fine. Then if I start using the ati driver I run into problems. Sometimes gdm crashes when I start the tv-program or then the video is corrupted.
So to my understanding it is a problem with the ATI graphics driver? Can anyone suggest anything, I'm stuck.

I use the ubuntu as my main TV-set so I need the tv-card to work but I also want good graphics, with the mesa driver I dont get full resolution.

---

### Post by midas80 on 2008-09-29
One more thing I just realized. 

If I use kaffeine for broadcasting a channel the image is fine when viewing the broadcsted video on another machine.

Even opening the stream in vlc on the same computer shows good video???

I'm confused.

---

