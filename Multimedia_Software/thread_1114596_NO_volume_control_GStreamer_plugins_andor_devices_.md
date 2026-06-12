---
title: "NO volume control GStreamer plugins and/or devices found."
date: 2009-04-02
forum: Multimedia Software
---

### Post by purinsy on 2009-04-02
Click volume control.
the above message poped up.
I install virtualbox in the host o/s windows xp service pack 3
and for the guest o/s i installed ubuntu intrepid.

I tried to find some solutions and have done something like this.

cat /proc/asound/modules
cat: /proc/asound/modules: no such file or directory

Here is my result of both lspci and dmesg

 lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)

dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000007ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000007ff0000 - 0000000008000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] last_pfn = 0x7ff0 max_arch_pfn = 0x100000
[    0.000000] ------------[ cut here ]------------
[    0.000000] WARNING: at /build/buildd/linux-2.6.27/arch/x86/kernel/cpu/mtrr/main.c:1500 mtrr_trim_uncached_memory+0x153/0x386()
[    0.000000] WARNING: strange, CPU MTRRs all blank?
[    0.000000] Modules linked in:
[    0.000000] Pid: 0, comm: swapper Not tainted 2.6.27-11-generic #1
[    0.000000]  [<c0131e15>] warn_slowpath+0x65/0x90
[    0.000000]  [<c037f4e8>] ? _spin_unlock_irqrestore+0x28/0x40
[    0.000000]  [<c037f4e8>] ? _spin_unlock_irqrestore+0x28/0x40
[    0.000000]  [<c01325ab>] ? wake_up_klogd+0xb/0x40
[    0.000000]  [<c01327a1>] ? release_console_sem+0x1c1/0x1d0
[    0.000000]  [<c04b8766>] ? mtrr_cleanup+0x11/0x868
[    0.000000]  [<c0132b60>] ? vprintk+0x170/0x370
[    0.000000]  [<c0254972>] ? strcmp+0x12/0x40
[    0.000000]  [<c04b942e>] mtrr_trim_uncached_memory+0x153/0x386
[    0.000000]  [<c04b988a>] ? get_mtrr_state+0x120/0x307
[    0.000000]  [<c02de713>] ? dmi_table+0x93/0xa0
[    0.000000]  [<c04b4186>] setup_arch+0x530/0x83a
[    0.000000]  [<c0370020>] ? enable_nonboot_cpus+0x80/0xc0
[    0.000000]  [<c04c7101>] ? cgroup_init_subsys+0x31/0xce
[    0.000000]  [<c014c339>] ? raw_notifier_chain_register+0x9/0x50
[    0.000000]  [<c04ad6a7>] start_kernel+0x6d/0x37f
[    0.000000]  [<c04ad117>] ? reserve_ebda_region+0x6e/0x77
[    0.000000]  [<c04ad09e>] __init_begin+0x9e/0xa9
[    0.000000]  =======================
[    0.000000] ---[ end trace 4eaa2a86a8e2da22 ]---
[    0.000000] kernel direct mapping tables up to 7ff0000 @ 7000-d000
[    0.000000] RAMDISK: 07810000 - 07fdf423
[    0.000000] ACPI: RSDP 000E0000, 0024 (r2 VBOX  )
[    0.000000] ACPI: XSDT 07FF0030, 002C (r1 VBOX   VBOXXSDT        1 ASL        61)
[    0.000000] ACPI: FACP 07FF0060, 00F4 (r4 VBOX   VBOXFACP        1 ASL        61)
[    0.000000] ACPI: DSDT 07FF01A0, 1725 (r1 VBOX   VBOXBIOS        2 INTL 20050309)
[    0.000000] ACPI: FACS 07FF0160, 0040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 127MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 07ff0000
[    0.000000]   low ram: 00000000 - 07ff0000
[    0.000000]   bootmap 00002000 - 00003000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0007ff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [0007810000 - 0007fdf423]          RAMDISK ==> [0007810000 - 0007fdf423]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000003000]          BOOTMAP ==> [0000002000 - 0000003000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00007ff0
[    0.000000]   HighMem  0x00007ff0 -> 0x00007ff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00007ff0
[    0.000000] On node 0 totalpages: 32655
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 28404 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 8000000:f7fc0000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 32367
[    0.000000] Kernel command line: root=UUID=45b3a747-1d0f-4c60-81b4-09c95c11c53f ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 512 (order: 9, 2048 bytes)
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using PMTIMER reference calibration
[    0.000000] Detected 1655.830 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[    0.004000] Memory: 116240k/131008k available (2576k kernel code, 14224k reserved, 1165k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xc8800000 - 0xff3fe000   ( 875 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xc7ff0000   ( 127 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.012694] Calibrating delay loop (skipped), value calculated using timer frequency.. 3311.66 BogoMIPS (lpj=6623320)
[    0.013683] Security Framework initialized
[    0.013769] SELinux:  Disabled at boot.
[    0.016942] AppArmor: AppArmor initialized
[    0.017218] Mount-cache hash table entries: 512
[    0.032467] Initializing cgroup subsys ns
[    0.032598] Initializing cgroup subsys cpuacct
[    0.032719] Initializing cgroup subsys memory
[    0.033631] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.033745] CPU: L2 cache: 2048K
[    0.034786] Checking 'hlt' instruction... OK.
[    0.056243] SMP alternatives: switching to UP code
[    0.420026] Freeing SMP alternatives: 11k freed
[    0.425984] ACPI: Core revision 20080609
[    0.430246] ACPI: Checking initramfs for custom DSDT
[    0.789640] ACPI: setting ELCR to 0200 (from 0c00)
[    0.817261] weird, boot CPU (#0) not listedby the BIOS.
[    0.817321] SMP motherboard not detected.
[    0.820031] SMP disabled
[    0.844976] Brought up 1 CPUs
[    0.845033] Total of 1 processors activated (3311.66 BogoMIPS).
[    0.845121] CPU0 attaching NULL sched-domain.
[    0.871948] net_namespace: 840 bytes
[    0.872480] Booting paravirtualized kernel on bare hardware
[    0.876292] Time:  8:42:45  Date: 04/03/09
[    0.877208] NET: Registered protocol family 16
[    0.887383] EISA bus registered
[    0.888599] ACPI: bus type pci registered
[    0.895089] PCI: PCI BIOS revision 2.10 entry at 0xfbc20, last bus=0
[    0.895149] PCI: Using configuration type 1 for base access
[    0.922158] ACPI: EC: Look up EC in DSDT
[    0.932142] ACPI: Interpreter enabled
[    0.932201] ACPI: (supports S0 S5)
[    0.932295] ACPI: Using PIC for interrupt routing
[    0.947981] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.954620] PCI: 0000:00:01.1 reg 20 io port: [c000, c00f]
[    0.956744] PCI: 0000:00:02.0 reg 10 32bit mmio: [e0000000, e07fffff]
[    0.957845] PCI: 0000:00:03.0 reg 10 io port: [c020, c03f]
[    0.958038] PCI: 0000:00:03.0 reg 14 32bit mmio: [f0000000, f0000fff]
[    0.958234] PCI: 0000:00:03.0 reg 18 32bit mmio: [f0080000, f00fffff]
[    0.959070] PCI: 0000:00:04.0 reg 10 io port: [c040, c05f]
[    0.959372] PCI: 0000:00:04.0 reg 14 32bit mmio: [f0400000, f07fffff]
[    0.959553] PCI: 0000:00:04.0 reg 18 32bit mmio: [f0800000, f0803fff]
[    0.961594] bus 00 -> node 0
[    0.961695] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.974591] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 9 10 11) *0, disabled.
[    0.975643] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 9 10 11) *0, disabled.
[    0.976209] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 9 10 *11)
[    0.976648] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 9 *10 11)
[    0.977772] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.978170] pnp: PnP ACPI init
[    0.978247] ACPI: bus type pnp registered
[    0.983207] pnp: PnP ACPI: found 6 devices
[    0.983248] ACPI: ACPI bus type pnp unregistered
[    0.983978] PnPBIOS: Disabled by ACPI PNP
[    0.990418] PCI: Using ACPI for IRQ routing
[    0.996793] NET: Registered protocol family 8
[    0.996835] NET: Registered protocol family 20
[    0.997292] NetLabel: Initializing
[    0.997329] NetLabel:  domain hash size = 128
[    0.997364] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.997387] NetLabel:  unlabeled traffic allowed by default
[    1.005934] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.005990]    actual entries 65620
[    1.006557] AppArmor: AppArmor Filesystem Enabled
[    1.049034] bus: 00 index 0 io port: [0, ffff]
[    1.049078] bus: 00 index 1 mmio: [0, ffffffff]
[    1.049165] NET: Registered protocol family 2
[    1.054845] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[    1.058486] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[    1.058605] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[    1.058702] TCP: Hash tables configured (established 4096 bind 4096)
[    1.058748] TCP reno registered
[    1.059771] NET: Registered protocol family 1
[    1.064191] checking if image is initramfs... it is
[    1.557962] Switched to high resolution mode on CPU 0
[    2.145571] Freeing initrd memory: 7997k freed
[    2.147048] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    2.152367] audit: initializing netlink socket (disabled)
[    2.152801] type=2000 audit(1238748166.152:1): initialized
[    2.161916] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.173846] VFS: Disk quotas dquot_6.5.1
[    2.174315] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.174694] msgmni has been set to 242
[    2.175500] io scheduler noop registered
[    2.175521] io scheduler anticipatory registered
[    2.175542] io scheduler deadline registered
[    2.175577] io scheduler cfq registered (default)
[    2.175763] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    2.175833] pci 0000:00:01.0: Activating ISA DMA hang workarounds
[    2.175881] pci 0000:00:02.0: Boot video device
[    2.177617] isapnp: Scanning for PnP cards...
[    2.538815] isapnp: No Plug & Play device found
[    2.662645] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.676628] brd: module loaded
[    2.676940] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.677853] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.682359] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.682755] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.686169] mice: PS/2 mouse device common for all mice
[    2.693918] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.694086] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    2.695513] rtc0: alarms up to one day
[    2.699348] EISA: Probing bus 0 at eisa.0
[    2.699393] Cannot allocate resource for EISA slot 4
[    2.699426] EISA: Detected 0 cards.
[    2.699445] cpuidle: using governor ladder
[    2.699463] cpuidle: using governor menu
[    2.701075] TCP cubic registered
[    2.701740] Using IPI No-Shortcut mode
[    2.702534] registered taskstats version 1
[    2.702659]   Magic number: 5:741:724
[    2.704331] rtc_cmos rtc_cmos: setting system clock to 2009-04-03 08:42:47 UTC (1238748167)
[    2.704371] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.704393] EDD information not available.
[    2.707619] Freeing unused kernel memory: 424k freed
[    2.710263] Write protecting the kernel text: 2580k
[    2.711906] Write protecting the kernel read-only data: 940k
[    3.484493] fuse init (API version 7.9)
[    4.741235] No dock devices found.
[    4.845361] SCSI subsystem initialized
[    4.957484] libata version 3.00 loaded.
[    4.987310] pata_acpi 0000:00:01.1: setting latency timer to 64
[    5.015820] ata_piix 0000:00:01.1: version 2.12
[    5.023977] scsi0 : ata_piix
[    5.072564] scsi1 : ata_piix
[    5.073448] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xc000 irq 14
[    5.073482] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xc008 irq 15
[    5.120698] pcnet32.c:v1.35 21.Apr.2008 [email]tsbogend@alpha.franken.de[/email]
[    5.256244] ata1.00: ATA-6: VBOX HARDDISK, 1.0, max UDMA/133
[    5.256275] ata1.00: 16777216 sectors, multi 128: LBA 
[    5.257268] ata1.00: configured for UDMA/33
[    5.415244] ata2.00: ATAPI: VBOX CD-ROM, 1.0, max UDMA/133
[    5.415945] ata2.00: configured for UDMA/33
[    5.442602] scsi 0:0:0:0: Direct-Access     ATA      VBOX HARDDISK    1.0  PQ: 0 ANSI: 5
[    5.456831] scsi 1:0:0:0: CD-ROM            VBOX     CD-ROM           1.0  PQ: 0 ANSI: 5
[    5.460786] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    5.460815] PCI: setting IRQ 11 as level-triggered
[    5.460846] pcnet32 0000:00:03.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    5.460912] pcnet32 0000:00:03.0: setting latency timer to 64
[    5.461129] pcnet32: PCnet/FAST III 79C973 at 0xc020, 08:00:27:b0:85:69 assigned IRQ 11.
[    5.461495] pcnet32: Found PHY 0022:561b at address 0.
[    5.464411] eth0: registered as PCnet/FAST III 79C973
[    5.464575] pcnet32: 1 cards_found.
[    7.886800] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.886926] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    7.977631] Driver 'sd' needs updating - please use bus_type methods
[    7.983218] sd 0:0:0:0: [sda] 16777216 512-byte hardware sectors (8590 MB)
[    7.984278] sd 0:0:0:0: [sda] Write Protect is off
[    7.984304] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.984624] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.997192] sd 0:0:0:0: [sda] 16777216 512-byte hardware sectors (8590 MB)
[    7.997381] sd 0:0:0:0: [sda] Write Protect is off
[    7.997406] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.997725] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.997766]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    8.024199]  sda1 sda2 < sda5 >
[    8.060556] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.064159] sr0: scsi3-mmc drive: 32x/32x xa/form2 tray
[    8.064191] Uniform CD-ROM driver Revision: 3.20
[    8.064342] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    8.563637] PM: Starting manual resume from disk
[    8.563668] PM: Resume from partition 8:5
[    8.563685] PM: Checking hibernation image.
[    8.565368] PM: Resume from disk failed.
[    8.648470] kjournald starting.  Commit interval 5 seconds
[    8.648552] EXT3-fs: mounted filesystem with ordered data mode.
[   14.763720] udevd version 124 started
[   16.709069] usbcore: registered new interface driver usbfs
[   16.709392] usbcore: registered new interface driver hub
[   16.745269] usbcore: registered new device driver usb
[   16.773417] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   16.773454] PCI: setting IRQ 10 as level-triggered
[   16.773489] pci 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   16.782859] vboxadd: Successfully loaded version 2.1.4 (interface 0x00010004)
[   16.809494] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   16.853156] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   16.871223] ACPI: Power Button (FF) [PWRF]
[   16.872003] input: Sleep Button (FF) as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input4
[   16.880924] request region #1
[   16.883313] isp1760: probe of 0000:00:07.0 failed with error -16
[   16.888579] ACPI: Sleep Button (FF) [SLPF]
[   17.156945] piix4_smbus 0000:00:07.0: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr
[   17.263409] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   17.569535] ACPI: AC Adapter [AC] (on-line)
[   17.610999] ACPI: Battery Slot [BAT0] (battery present)
[   17.815055] parport_pc 00:05: reported by Plug and Play ACPI
[   23.657896] lp: driver loaded but no devices found
[   24.135370] Adding 409616k swap on /dev/sda5.  Priority:-1 extents:1 across:409616k
[   24.831858] EXT3 FS on sda1, internal journal
[   26.808496] type=1505 audit(1238748191.545:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3517
[   27.063291] type=1505 audit(1238748191.796:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3522
[   27.064003] type=1505 audit(1238748191.796:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3522
[   27.187382] type=1505 audit(1238748191.920:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=3526
[   27.545773] ip_tables: (C) 2000-2006 Netfilter Core Team
[   29.025498] vboxvfs: Successfully loaded version 2.1.4 (interface 0x00010004)
[   29.942631] ACPI: WMI: Mapper loaded
[   33.147404] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   33.720308] NET: Registered protocol family 10
[   33.727505] lo: Disabled Privacy Extensions
[   38.539139] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   38.539173] apm: overridden by ACPI.
[   39.591315] ppdev: user-space parallel port driver
[   45.096863] Bluetooth: Core ver 2.13
[   45.109740] NET: Registered protocol family 31
[   45.109770] Bluetooth: HCI device and connection manager initialized
[   45.109796] Bluetooth: HCI socket layer initialized
[   45.196452] Bluetooth: L2CAP ver 2.11
[   45.196484] Bluetooth: L2CAP socket layer initialized
[   45.294127] Bluetooth: RFCOMM socket layer initialized
[   45.294187] Bluetooth: RFCOMM TTY layer initialized
[   45.294210] Bluetooth: RFCOMM ver 1.10
[   45.299140] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   45.299173] Bluetooth: BNEP filters: protocol multicast
[   45.464861] Bridge firewalling registered
[   45.496942] Bluetooth: SCO (Voice Link) ver 0.6
[   45.496975] Bluetooth: SCO socket layer initialized
[   49.732100] eth0: link up, 100Mbps, full-duplex
[   50.456499] NET: Registered protocol family 17
[   60.236105] eth0: no IPv6 routers present
[  352.407201] UDF-fs: No VRS found
[  352.415491] ISO 9660 Extensions: Microsoft Joliet Level 3
[  352.434154] ISO 9660 Extensions: RRIP_1991A


thank you for your help in advance.:KS):P

---

