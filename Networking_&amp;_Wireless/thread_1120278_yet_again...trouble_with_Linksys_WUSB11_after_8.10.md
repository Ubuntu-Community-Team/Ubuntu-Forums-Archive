---
title: "yet again...trouble with Linksys WUSB11 after 8.10 upgrade"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by havensrobert on 2009-04-08
howdy,

First a disclaimer: I am a linux/Ubuntu noob.  I've been learning by doing and am doing ok but can't seem to resolve this.  Please know that i have little idea what i am doing....

I am running Xubuntu (8.10 now) on a crappy old Compaq with a celeron.

My Linksys usb adapter works in 2.6.24-19 generic (which i still have installed on the same crappy machine) but not in  2.6.27-11-generic after my upgrade to 8.10.  Apparently it is not unusal to have SOME kind of wireless problem after the upgrade.  I've tried various things (some of which in hindsight had little support for trying):  the most significant failures are trying a windows driver with the ndiswrapper (it was a pain in the *** to figure out....downloading stuff to a flash drive)...and more recently the How To Set up WUSB11 here
[]("https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11").  I believe the adapter is working in 2.6.24-19 because it is using the 76_usb driver and the setup instruction above were meant to install that driver but I've done something wrong apparently.  Help!  I'm pasting various outputs below.  I hope i m doing something fairly obvious to the experienced eye.  I should say one of my wrongheaded ideas was to blacklist ipv6...which i didn't succed in doing but I do occasionally get errors about that....could that be the problem?  I'll post those errors (which usually say WARNING rather than FATAL) if anyone thinks they are germane. Thanks!

-bob

(is this not the proper way to post the outputs?  sorry)

the final section of outputs is from the How To Set up WUSB11 instruction from step 22.

robertrjh@ubunturjh:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000bed0000 (usable)
[    0.000000]  BIOS-e820: 000000000bed0000 - 000000000bef0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000bef0000 - 000000000bf00000 (usable)
[    0.000000]  BIOS-e820: 00000000feea0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0xbf00 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to bf00000 @ 7000-d000
[    0.000000] RAMDISK: 0b6fb000 - 0bebfa38
[    0.000000] ACPI: RSDP 000E0010, 0014 (r0 COMPAQ)
[    0.000000] ACPI: RSDT 000E0080, 0050 (r1 COMPAQ CPQ001>  20010418             0)
[    0.000000] ACPI: FACP 000E0130, 0084 (r2 COMPAQ SOLANO          1             0)
[    0.000000] ACPI: DSDT 000E0248, 0F55 (r1 COMPAQ     DSDT        1 MSFT  100000D)
[    0.000000] ACPI: FACS 000E0040, 0040
[    0.000000] ACPI: SSDT 000E119D, 0174 (r1 COMPAQ CORE_UTL        1 MSFT  100000D)
[    0.000000] ACPI: SSDT 000E1311, 05DC (r1 COMPAQ VILLTBL1        1 MSFT  100000D)
[    0.000000] ACPI: APIC 000E01E8, 0060 (r1 COMPAQ SOLANO          1             0)
[    0.000000] ACPI: SSDT 000E2656, 0076 (r1 COMPAQ     APIC        1 MSFT  100000D)
[    0.000000] ACPI: SSDT 000E27B4, 065F (r1 COMPAQ LGCYLITE        1 MSFT  100000D)
[    0.000000] ACPI: SSDT 000E18ED, 046F (r1 COMPAQ PNP_PRSS        1 MSFT  100000D)
[    0.000000] ACPI: SSDT 000E1DBA, 0197 (r1 COMPAQ       S3        1 MSFT  100000D)
[    0.000000] ACPI: SSDT 000E1F51, 0158 (r1 COMPAQ   PIDETM        1 MSFT  100000D)
[    0.000000] ACPI: SSDT 000E2206, 010B (r1 COMPAQ     GTF0        1 MSFT  100000D)
[    0.000000] ACPI: SSDT 000E2EA1, 0064 (r1 COMPAQ    FINIS        1 MSFT  100000D)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 191MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0bf00000
[    0.000000]   low ram: 00000000 - 0bf00000
[    0.000000]   bootmap 00002000 - 000037e0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000bf00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [000b6fb000 - 000bebfa38]          RAMDISK ==> [000b6fb000 - 000bebfa38]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
[    0.000000] found SMP MP-table at [c00f9bf0] 000f9bf0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000bf00
[    0.000000]   HighMem  0x0000bf00 -> 0x0000bf00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000bed0
[    0.000000]     0: 0x0000bef0 -> 0x0000bf00
[    0.000000] On node 0 totalpages: 48767
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 44374 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0xf808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000000bed0000 - 000000000bef0000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: bf00000:f2fa0000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 48337
[    0.000000] Kernel command line: root=UUID=17052be5-050a-43b4-b364-329d91775c0a ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 698.984 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 180040k/195584k available (2576k kernel code, 14860k reserved, 1165k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xcc800000 - 0xff3fe000   ( 811 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcbf00000   ( 191 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004034] Calibrating delay loop (skipped), value calculated using timer frequency.. 1397.96 BogoMIPS (lpj=2795936)
[    0.004114] Security Framework initialized
[    0.004151] SELinux:  Disabled at boot.
[    0.004240] AppArmor: AppArmor initialized
[    0.004283] Mount-cache hash table entries: 512
[    0.004960] Initializing cgroup subsys ns
[    0.004985] Initializing cgroup subsys cpuacct
[    0.004996] Initializing cgroup subsys memory
[    0.005058] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.005068] CPU: L2 cache: 128K
[    0.005131] Checking 'hlt' instruction... OK.
[    0.021107] SMP alternatives: switching to UP code
[    0.032124] Freeing SMP alternatives: 11k freed
[    0.032145] ACPI: Core revision 20080609
[    0.032373] ACPI: Checking initramfs for custom DSDT
[    1.049604] ENABLING IO-APIC IRQs
[    1.049870] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    1.089579] CPU0: Intel Celeron (Coppermine) stepping 06
[    1.092031] Brought up 1 CPUs
[    1.092031] Total of 1 processors activated (1397.96 BogoMIPS).
[    1.092031] CPU0 attaching NULL sched-domain.
[    1.092031] net_namespace: 840 bytes
[    1.092031] Booting paravirtualized kernel on bare hardware
[    1.092031] Time: 22:49:05  Date: 04/08/09
[    1.092031] NET: Registered protocol family 16
[    1.092890] EISA bus registered
[    1.092979] ACPI: bus type pci registered
[    1.096071] PCI: PCI BIOS revision 2.10 entry at 0xe830e, last bus=2
[    1.096085] PCI: Using configuration type 1 for base access
[    1.104559] ACPI: EC: Look up EC in DSDT
[    1.114350] ACPI: Interpreter enabled
[    1.114374] ACPI: (supports S0 S1 S3 S4 S5)
[    1.114434] ACPI: Using IOAPIC for interrupt routing
[    1.135255] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.135773] PCI: 0000:00:02.0 reg 10 32bit mmio: [44000000, 47ffffff]
[    1.135793] PCI: 0000:00:02.0 reg 14 32bit mmio: [40300000, 4037ffff]
[    1.136191] pci 0000:00:1f.0: quirk: region f800-f87f claimed by ICH4 ACPI/GPIO/TCO
[    1.136204] pci 0000:00:1f.0: quirk: region fa00-fa3f claimed by ICH4 GPIO
[    1.136275] PCI: 0000:00:1f.1 reg 20 io port: [2480, 248f]
[    1.136370] PCI: 0000:00:1f.2 reg 20 io port: [2440, 245f]
[    1.136464] PCI: 0000:00:1f.4 reg 20 io port: [2460, 247f]
[    1.136526] PCI: 0000:00:1f.5 reg 10 io port: [2000, 20ff]
[    1.136542] PCI: 0000:00:1f.5 reg 14 io port: [2400, 243f]
[    1.136683] PCI: 0000:02:08.0 reg 10 32bit mmio: [40000000, 40000fff]
[    1.136700] PCI: 0000:02:08.0 reg 14 io port: [1000, 103f]
[    1.136763] pci 0000:02:08.0: supports D1
[    1.136770] pci 0000:02:08.0: supports D2
[    1.136779] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.136791] pci 0000:02:08.0: PME# disabled
[    1.136842] pci 0000:00:1e.0: transparent bridge
[    1.136856] PCI: bridge 0000:00:1e.0 io port: [1000, 1fff]
[    1.136869] PCI: bridge 0000:00:1e.0 32bit mmio: [40000000, 402fffff]
[    1.136893] bus 00 -> node 0
[    1.136949] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.137669] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    1.149511] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 14 15)
[    1.149839] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 14 15)
[    1.150149] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    1.150462] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 14 15)
[    1.150771] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)
[    1.151081] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    1.151398] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    1.151715] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 14 15)
[    1.152792] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.153068] pnp: PnP ACPI init
[    1.153116] ACPI: bus type pnp registered
[    1.163021] pnp 00:0b: io resource (0xf800-0xf81f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    1.163039] pnp 00:0b: io resource (0xf820-0xf83f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    1.163052] pnp 00:0b: io resource (0xf840-0xf85f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    1.163065] pnp 00:0b: io resource (0xf860-0xf87f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    1.165699] pnp: PnP ACPI: found 13 devices
[    1.165715] ACPI: ACPI bus type pnp unregistered
[    1.165730] PnPBIOS: Disabled by ACPI PNP
[    1.168622] PCI: Using ACPI for IRQ routing
[    1.169129] NET: Registered protocol family 8
[    1.169129] NET: Registered protocol family 20
[    1.169129] NetLabel: Initializing
[    1.169129] NetLabel:  domain hash size = 128
[    1.169129] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.169129] NetLabel:  unlabeled traffic allowed by default
[    1.169547] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.169556]    actual entries 65620
[    1.170476] AppArmor: AppArmor Filesystem Enabled
[    1.170551] ACPI: RTC can wake from S4
[    1.172236] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    1.172272] system 00:0b: ioport range 0x338-0x33f has been reserved
[    1.172283] system 00:0b: ioport range 0x400-0x41f has been reserved
[    1.172293] system 00:0b: ioport range 0x420-0x43f has been reserved
[    1.172303] system 00:0b: ioport range 0x440-0x45f has been reserved
[    1.172314] system 00:0b: ioport range 0x460-0x47f has been reserved
[    1.172327] system 00:0b: ioport range 0xfa00-0xfa3f has been reserved
[    1.172338] system 00:0b: ioport range 0xfc00-0xfc7f has been reserved
[    1.172349] system 00:0b: ioport range 0xfc80-0xfcff has been reserved
[    1.172359] system 00:0b: ioport range 0xfe00-0xfe7f has been reserved
[    1.172370] system 00:0b: ioport range 0xfe80-0xfeff has been reserved
[    1.172399] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    1.172411] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    1.172422] system 00:0c: iomem range 0x100000-0xbefffff could not be reserved
[    1.172434] system 00:0c: iomem range 0xfff80000-0xffffffff could not be reserved
[    1.172445] system 00:0c: iomem range 0xfeea0000-0xfeebffff could not be reserved
[    1.172456] system 00:0c: iomem range 0xd7800-0xd7fff has been reserved
[    1.172505] system 00:0c: iomem range 0xffb80000-0xffbfffff could not be reserved
[    1.211188] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    1.211206] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    1.211224] pci 0000:00:1e.0:   MEM window: 0x40000000-0x402fffff
[    1.211236] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.211277] pci 0000:00:1e.0: setting latency timer to 64
[    1.211290] bus: 00 index 0 io port: [0, ffff]
[    1.211297] bus: 00 index 1 mmio: [0, ffffffff]
[    1.211305] bus: 02 index 0 io port: [1000, 1fff]
[    1.211313] bus: 02 index 1 mmio: [40000000, 402fffff]
[    1.211321] bus: 02 index 2 mmio: [0, 0]
[    1.211328] bus: 02 index 3 io port: [0, ffff]
[    1.211336] bus: 02 index 4 mmio: [0, ffffffff]
[    1.211383] NET: Registered protocol family 2
[    1.211916] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    1.212937] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    1.213220] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    1.213510] TCP: Hash tables configured (established 8192 bind 8192)
[    1.213524] TCP reno registered
[    1.214111] NET: Registered protocol family 1
[    1.214646] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    2.216300]  it is
[    3.583778] Freeing initrd memory: 7954k freed
[    3.587898] audit: initializing netlink socket (disabled)
[    3.587965] type=2000 audit(1239230946.584:1): initialized
[    3.607344] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.623682] VFS: Disk quotas dquot_6.5.1
[    3.624389] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.625094] msgmni has been set to 367
[    3.625978] io scheduler noop registered
[    3.625994] io scheduler anticipatory registered
[    3.626003] io scheduler deadline registered
[    3.626115] io scheduler cfq registered (default)
[    3.626165] pci 0000:00:02.0: Boot video device
[    3.626258] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    3.628643] isapnp: Scanning for PnP cards...
[    3.982798] isapnp: No Plug & Play device found
[    4.431099] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    4.431570] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.438094] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.451472] brd: module loaded
[    4.451918] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    4.452963] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[    4.456077] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.456105] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.459043] mice: PS/2 mouse device common for all mice
[    4.460295] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.460362] rtc0: alarms up to one month, y3k
[    4.461269] EISA: Probing bus 0 at eisa.0
[    4.461304] Cannot allocate resource for EISA slot 1
[    4.461312] Cannot allocate resource for EISA slot 2
[    4.461356] EISA: Detected 0 cards.
[    4.461368] cpuidle: using governor ladder
[    4.461376] cpuidle: using governor menu
[    4.463803] TCP cubic registered
[    4.463967] Using IPI No-Shortcut mode
[    4.466373] registered taskstats version 1
[    4.466740]   Magic number: 5:709:855
[    4.467030] tty ptyv7: hash matches
[    4.467064] tty ptysa: hash matches
[    4.467238] rtc_cmos 00:03: setting system clock to 2009-04-08 22:49:08 UTC (1239230948)
[    4.467252] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.467259] EDD information not available.
[    4.469709] Freeing unused kernel memory: 424k freed
[    4.469921] Write protecting the kernel text: 2580k
[    4.470050] Write protecting the kernel read-only data: 940k
[    4.487816] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    5.284181] fuse init (API version 7.9)
[    5.720113] processor ACPI0007:00: registered as cooling_device0
[    5.720141] ACPI: Processor [CPU0] (supports 8 throttling states)
[    8.136464] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    8.136478] e100: Copyright(c) 1999-2006 Intel Corporation
[    8.146169] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    8.237829] e100 0000:02:08.0: PME# disabled
[    8.241562] No dock devices found.
[    8.601537] SCSI subsystem initialized
[    8.606269] e100: eth0: e100_probe: addr 0x40000000, irq 20, MAC addr 00:02:a5:7b:3b:7b
[    8.631901] usbcore: registered new interface driver usbfs
[    8.631993] usbcore: registered new interface driver hub
[    8.635430] usbcore: registered new device driver usb
[    8.741384] USB Universal Host Controller Interface driver v3.0
[    8.741619] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    8.741652] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    8.741664] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    8.741869] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    8.741972] uhci_hcd 0000:00:1f.2: irq 19, io base 0x00002440
[    8.742757] usb usb1: configuration #1 chosen from 1 choice
[    8.742916] hub 1-0:1.0: USB hub found
[    8.742962] hub 1-0:1.0: 2 ports detected
[    8.746766] libata version 3.00 loaded.
[    8.950267] uhci_hcd 0000:00:1f.4: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    8.950306] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    8.950318] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    8.950464] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    8.950551] uhci_hcd 0000:00:1f.4: irq 23, io base 0x00002460
[    8.951338] usb usb2: configuration #1 chosen from 1 choice
[    8.951474] hub 2-0:1.0: USB hub found
[    8.951519] hub 2-0:1.0: 2 ports detected
[    9.066643] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    9.075416] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    9.100363] ata_piix 0000:00:1f.1: version 2.12
[    9.100604] ata_piix 0000:00:1f.1: setting latency timer to 64
[    9.104816] scsi0 : ata_piix
[    9.105613] scsi1 : ata_piix
[    9.106273] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2480 irq 14
[    9.106286] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2488 irq 15
[    9.218780] usb 1-2: configuration #1 chosen from 1 choice
[    9.220449] hub 1-2:1.0: USB hub found
[    9.222131] hub 1-2:1.0: 4 ports detected
[    9.270699] ata1.00: ATA-6: SAMSUNG SV0602H, RH100-11, max UDMA/100
[    9.270716] ata1.00: 117304992 sectors, multi 16: LBA 
[    9.284732] ata1.00: configured for UDMA/100
[    9.448548] ata2.00: ATAPI: CD-224E, 9.8C, max MWDMA2
[    9.464683] ata2.00: configured for MWDMA2
[    9.465214] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SV0602H  RH10 PQ: 0 ANSI: 5
[    9.467240] scsi 1:0:0:0: CD-ROM            COMPAQ   CD-224E          9.8C PQ: 0 ANSI: 5
[    9.518160] usb 1-2.2: new full speed USB device using uhci_hcd and address 3
[    9.642745] usb 1-2.2: configuration #1 chosen from 1 choice
[    9.722080] usb 1-2.3: new full speed USB device using uhci_hcd and address 4
[    9.834651] usb 1-2.3: configuration #1 chosen from 1 choice
[   11.817779] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[   11.818066] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   12.062910] Driver 'sd' needs updating - please use bus_type methods
[   12.063406] sd 0:0:0:0: [sda] 117304992 512-byte hardware sectors (60060 MB)
[   12.063501] sd 0:0:0:0: [sda] Write Protect is off
[   12.063516] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.063660] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.064090] sd 0:0:0:0: [sda] 117304992 512-byte hardware sectors (60060 MB)
[   12.064195] sd 0:0:0:0: [sda] Write Protect is off
[   12.064209] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.064350] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.064372]  sda: sda1 sda2 <<6>usbcore: registered new interface driver libusual
[   12.115459]  sda5 sda6 sda7 >
[   12.134438] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.159580] Driver 'sr' needs updating - please use bus_type methods
[   12.170884] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   12.170905] Uniform CD-ROM driver Revision: 3.20
[   12.171325] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   12.172790] Initializing USB Mass Storage driver...
[   12.220392] scsi2 : SCSI emulation for USB Mass Storage devices
[   12.236347] usbcore: registered new interface driver usb-storage
[   12.236367] USB Mass Storage support registered.
[   12.236945] usb-storage: device found at 3
[   12.236956] usb-storage: waiting for device to settle before scanning
[   13.082162] PM: Starting manual resume from disk
[   13.082183] PM: Resume from partition 8:7
[   13.082190] PM: Checking hibernation image.
[   13.082728] PM: Resume from disk failed.
[   13.238192] kjournald starting.  Commit interval 5 seconds
[   13.238258] EXT3-fs: mounted filesystem with ordered data mode.
[   17.238076] usb-storage: device scan complete
[   17.241042] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[   17.243974] scsi 2:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[   17.251917] sd 2:0:0:0: [sdb] 4001422 512-byte hardware sectors (2049 MB)
[   17.254899] sd 2:0:0:0: [sdb] Write Protect is off
[   17.254918] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   17.254928] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   17.265910] sd 2:0:0:0: [sdb] 4001422 512-byte hardware sectors (2049 MB)
[   17.268945] sd 2:0:0:0: [sdb] Write Protect is off
[   17.268967] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   17.268977] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   17.269012]  sdb: sdb1
[   17.275524] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   17.276285] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   17.280905] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[   17.281327] sr 2:0:0:1: Attached scsi CD-ROM sr1
[   17.282058] sr 2:0:0:1: Attached scsi generic sg3 type 5
[   23.175622] udevd version 124 started
[   26.114260] Linux agpgart interface v0.103
[   26.208159] intel_rng: FWH not detected
[   26.312590] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.438504] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.531047] agpgart-intel 0000:00:00.0: Intel i815 Chipset
[   26.776126] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0x44000000
[   26.900575] iTCO_vendor_support: vendor-support=0
[   27.084608] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   27.085057] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0xf860)
[   27.085724] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   27.177076] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   28.121918] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   28.136118] ACPI: Power Button (FF) [PWRF]
[   28.136706] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   28.152102] ACPI: Power Button (CM) [PBTN]
[   30.464619] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   32.212429] parport_pc 00:08: reported by Plug and Play ACPI
[   32.212522] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   36.263308] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   36.263377] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   36.884280] intel8x0_measure_ac97_clock: measured 55528 usecs
[   36.884296] intel8x0: clocking to 41137
[   43.036486] loop: module loaded
[   43.105479] lp0: using parport0 (interrupt-driven).
[   43.739318] Adding 554200k swap on /dev/sda7.  Priority:-1 extents:1 across:554200k
[   44.611952] EXT3 FS on sda6, internal journal
[   47.372550] type=1505 audit(1239230991.691:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3815
[   47.374251] type=1505 audit(1239230991.691:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3815
[   47.827897] ip_tables: (C) 2000-2006 Netfilter Core Team
[   50.770522] NET: Registered protocol family 17
[   52.623545] ACPI: WMI: Mapper loaded
[   56.168283] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   56.368574] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   56.368597] apm: overridden by ACPI.
[   56.749082] ppdev: user-space parallel port driver
[   61.126666] Bluetooth: Core ver 2.13
[   61.133681] NET: Registered protocol family 31
[   61.133704] Bluetooth: HCI device and connection manager initialized
[   61.133719] Bluetooth: HCI socket layer initialized
[   61.278202] Bluetooth: L2CAP ver 2.11
[   61.278222] Bluetooth: L2CAP socket layer initialized
[   61.380126] Bluetooth: RFCOMM socket layer initialized
[   61.381126] Bluetooth: RFCOMM TTY layer initialized
[   61.381160] Bluetooth: RFCOMM ver 1.10
[   61.440526] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   61.440549] Bluetooth: BNEP filters: protocol multicast
[   61.639981] Bridge firewalling registered
[   61.788921] Bluetooth: SCO (Voice Link) ver 0.6
[   61.788944] Bluetooth: SCO socket layer initialized
[   67.985933] [drm] Initialized drm 1.1.0 20060810
[   68.036634] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   68.036664] pci 0000:00:02.0: setting latency timer to 64
[   68.039282] [drm] Initialized i810 1.4.0 20030605 on minor 0
[   68.042118] mtrr: base(0x44000000) is not aligned on a size(0x180000) boundary
[   68.498299] [drm] Using v1.4 init.
[   68.503536] mtrr: base(0x44000000) is not aligned on a size(0x3000000) boundary
[   71.792024] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[   71.792037] 	driver to use reclaim_buffers_idlelocked() instead.
[   71.792042] 	I will go on reclaiming the buffers anyway.
[  116.231316] NET: Registered protocol family 10
[  116.239599] lo: Disabled Privacy Extensions
[  116.246952] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  145.237816] usb 1-2.3: USB disconnect, address 4
[  147.485468] usb 1-2.3: new full speed USB device using uhci_hcd and address 5
[  147.598169] usb 1-2.3: configuration #1 chosen from 1 choice
[  195.812337] ppdev0: registered pardevice
[  195.860134] ppdev0: unregistered pardevice
[  200.069706] ppdev0: registered pardevice
[  200.121152] ppdev0: unregistered pardevice
[  200.326098] ppdev0: registered pardevice
[  200.377236] ppdev0: unregistered pardevice
[  259.090878] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  310.776027] pan0: no IPv6 routers present
[  734.974025] usb 1-2.3: USB disconnect, address 5
[  737.349669] usb 1-2.3: new full speed USB device using uhci_hcd and address 6
[  737.463374] usb 1-2.3: configuration #1 chosen from 1 choice
robertrjh@ubunturjh:~$ 


robertrjh@ubunturjh:~$ lsusb -v

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 006: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          254 Application Specific Interface
  bDeviceSubClass         1 Device Firmware Update
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x077b Linksys
  idProduct          0x2219 WUSB11 V2.6 802.11b Adapter
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      0 
      iInterface              0 
      ** UNRECOGNIZED:  07 21 01 13 05 00 04
cannot read device status, Operation not permitted (1)

Bus 001 Device 003: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0781 SanDisk Corp.
  idProduct          0x5406 Cruzer Micro 1/4GB Flash Drive
  bcdDevice            0.10
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0         8
  idVendor           0x0451 Texas Instruments, Inc.
  idProduct          0x2046 TUSB2046 Hub
  bcdDevice            1.25
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


robertrjh@ubunturjh:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:a5:7b:3b:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 00:02:a5:7b:3b:7b  
          inet addr:169.254.6.17  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 B)  TX bytes:600 (600.0 B)

robertrjh@ubunturjh:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
robertrjh@ubunturjh:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device


robertrjh@ubunturjh:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:02:a5:7b:3b:7b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d6:80:ad:61:15:d3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
	

robertrjh@ubunturjh:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
ipv6                  263972  8 
i810                   25984  2 
drm                    86056  3 i810
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ppdev                  15620  0 
cpufreq_ondemand       14988  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
sbs                    19464  0 
video                  25232  0 
output                 11008  1 video
pci_slot               12680  0 
wmi                    14504  0 
sbshc                  13440  1 sbs
container              11520  0 
battery                18436  0 
af_packet              25728  2 
p80211                 38536  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
loop                   23180  0 
snd_intel8x0           37532  2 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
evdev                  17696  6 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
parport_pc             39204  1 
snd_rawmidi            29824  1 snd_seq_midi
parport                42604  3 ppdev,lp,parport_pc
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                45200  0 
serio_raw              13444  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 14224  0 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
pcspkr                 10624  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
intel_agp              33724  1 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
agpgart                42184  3 drm,intel_agp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
usb_storage            82752  1 
sr_mod                 22212  0 
libusual               30356  1 usb_storage
cdrom                  43168  1 sr_mod
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
pata_acpi              12160  0 
ata_generic            12932  0 
uhci_hcd               30736  0 
libata                178208  3 ata_piix,pata_acpi,ata_generic
usbcore               149360  4 usb_storage,libusual,uhci_hcd
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
e100                   41356  0 
mii                    13440  1 e100
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1 


robertrjh@ubunturjh:~$ uname -r
2.6.27-11-generic


How To Set up WUSB11 (step 22 errors)

robertrjh@ubunturjh:~/Desktop$ cd at76c503a
robertrjh@ubunturjh:~/Desktop/at76c503a$ make
make -C /usr/src/linux-headers-2.6.27-11-generic M=/home/robertrjh/Desktop/at76c503a KERNELRELEASE=2.6.27-11-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/robertrjh/Desktop/at76c503a/at76_usb.o
/home/robertrjh/Desktop/at76c503a/at76_usb.c: In function ‘at76_iw_handler_get_scan’:
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2332: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2332: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2332: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2332: error: too few arguments to function ‘iwe_stream_add_event’
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2340: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2340: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2340: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2340: error: too few arguments to function ‘iwe_stream_add_point’
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2351: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2351: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2351: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2351: error: too few arguments to function ‘iwe_stream_add_event’
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2358: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2358: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2358: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2358: error: too few arguments to function ‘iwe_stream_add_event’
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2369: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2369: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2369: error: too few arguments to function ‘iwe_stream_add_point’
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2388: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2388: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2388: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2388: error: too few arguments to function ‘iwe_stream_add_event’
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2407: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2407: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2407: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/robertrjh/Desktop/at76c503a/at76_usb.c:2407: error: too few arguments to function ‘iwe_stream_add_value’
make[2]: *** [/home/robertrjh/Desktop/at76c503a/at76_usb.o] Error 1
make[1]: *** [_module_/home/robertrjh/Desktop/at76c503a] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2

---

### Post by BkkBonanza on 2009-04-08
Holy cow you dumped a lot of info. I see form your module list that no wifi driver is loaded. So the first thing to try is loading a suitable module. For your WUSB11 dongle there are several versions. So first determine what type it is. It sounds like you may have a rt73 based one given what you said above. I'm not familiar with that device personally but you could try **modprobe rt73** to see if that loads up the driver. If the correct driver is loaded then your interface should show up in **ifconfig -a**.

---

### Post by havensrobert on 2009-04-09
thanks for your reply.  Apparently this version of the Linksys wusb adapter is an amtel chipset ans uses the at_76 driver which i haven't been able to get to work yet.  But your reply made me investigate so it was helpful thanks.

-b

---

### Post by havensrobert on 2009-04-09
anyone?  I know I posted a lot of info....sorry.

-b

---

### Post by chowyunpat on 2009-04-19
Good luck with this, in Intrepid 8.10, I tried several times with the live cd and it never would detect my Linksys WUSB v 2.6, which is supposed to work out of box and did for previous versions of Ubuntu starting with 5.04, but   I'm afraid there is another issue with this device in Jaunty 9.04 in that it will detect my modem see my network, but will keep prompting me for my WEP code, which is also what happens in Mint Linux 6, which is based on Ubuntu 8.10.  I hope this issue is solved in the final release of 9.10, because if I have a piece of hardware that works in Ubuntu I like to stick with, I'm not going to switch hardware with every new release.

---

### Post by billyboy1995 on 2009-09-26
> **chowyunpat said:**
> Good luck with this, in Intrepid 8.10, I tried several times with the live cd and it never would detect my Linksys WUSB v 2.6, which is supposed to work out of box and did for previous versions of Ubuntu starting with 5.04, but   I'm afraid there is another issue with this device in Jaunty 9.04 in that it will detect my modem see my network, but will keep prompting me for my WEP code, which is also what happens in Mint Linux 6, which is based on Ubuntu 8.10.  I hope this issue is solved in the final release of 9.10, because if I have a piece of hardware that works in Ubuntu I like to stick with, I'm not going to switch hardware with every new release.
i agree... i had installed the alpha 5 or 6 of 9.10 and it could find my network but when it tryed to join it it failed evey time. i restarted my wierless to factory defaults but didnn't work. so i went back to 9.04 and is a little scared to upgrade to 9.10 when it comes out because i dont want to lose all my data again because of downgradeing.

---

