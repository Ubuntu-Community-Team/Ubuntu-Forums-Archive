---
title: "xawtv + hauppage pvr 150 = not working for some reason"
date: 2008-09-01
forum: Multimedia Software
---

### Post by Randy_D28 on 2008-09-01
Hello, I am Randy a very new user and need a lot of help in regaurds to Linux and tvcard.

I find that most posts seem to ask for the info below but if you need more info just tell me how to get it and I will.

system : dual core (cheapie), 1GB Ram, 320GB sata HDD, Nvidia gforce 7300GS  (basicly bottom of the barrel cheap hardware about $220.00 tops)
 
I guess it is possible my system is to cheap to run Linux, it sure could not handle windows Vista Basic in classic mode.

lspci output :
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)

```

Dmesg output: 

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffa0000 - 000000003ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffae000 - 000000003ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ffe0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262048) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262048
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262048
[    0.000000] On node 0 totalpages: 262048
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32417 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB030 checksum 0
[    0.000000] ACPI: RSDP 000FB030, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 3FFA0100, 0054 (r1 &#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;  8000701 MSFT       97)
[    0.000000] ACPI: FACP 3FFA0290, 00F4 (r3 A_M_I_ OEMFACP   8000701 MSFT       97)
[    0.000000] ACPI: DSDT 3FFA05C0, 682B (r1  A0798 A0798000        0 INTL 20051117)
[    0.000000] ACPI: FACS 3FFAE000, 0040
[    0.000000] ACPI: APIC 3FFA0390, 006C (r1 A_M_I_ OEMAPIC   8000701 MSFT       97)
[    0.000000] ACPI: MCFG 3FFA0400, 003C (r1 A_M_I_ OEMMCFG   8000701 MSFT       97)
[    0.000000] ACPI: SLIC 3FFA0440, 0176 (r1 &#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;  8000701 MSFT       97)
[    0.000000] ACPI: OEMB 3FFAE040, 0080 (r1 A_M_I_ AMI_OEM   8000701 MSFT       97)
[    0.000000] ACPI: HPET 3FFA6DF0, 0038 (r1 A_M_I_ OEMHPET   8000701 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260001
[    0.000000] Kernel command line: root=UUID=68697cf8-8b9f-4d97-927b-14db681829fe ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2200.035 MHz processor.
[   22.082793] Console: colour VGA+ 80x25
[   22.082797] console [tty0] enabled
[   22.083007] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.083231] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.101541] Memory: 1027052k/1048192k available (2177k kernel code, 20456k reserved, 1006k data, 368k init, 130688k highmem)
[   22.101546] virtual kernel memory layout:
[   22.101547]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   22.101548]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.101548]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.101549]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.101550]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   22.101551]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   22.101551]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   22.101554] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.101579] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   22.101688] hpet clockevent registered
[   22.181613] Calibrating delay using timer specific routine.. 4403.28 BogoMIPS (lpj=8806569)
[   22.181628] Security Framework initialized
[   22.181632] SELinux:  Disabled at boot.
[   22.181641] AppArmor: AppArmor initialized
[   22.181644] Failure registering capabilities with primary security module.
[   22.181649] Mount-cache hash table entries: 512
[   22.181734] Initializing cgroup subsys ns
[   22.181738] Initializing cgroup subsys cpuacct
[   22.181745] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   22.181751] monitor/mwait feature present.
[   22.181752] using mwait in idle threads.
[   22.181755] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.181757] CPU: L2 cache: 2048K
[   22.181759] CPU: Physical Processor ID: 0
[   22.181760] CPU: Processor Core ID: 0
[   22.181761] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   22.181768] Compat vDSO mapped to ffffe000.
[   22.181777] Checking 'hlt' instruction... OK.
[   22.197973] SMP alternatives: switching to UP code
[   22.199260] Early unpacking initramfs... done
[   22.459535] ACPI: Core revision 20070126
[   22.459573] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.461625] CPU0: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   22.461640] SMP alternatives: switching to SMP code
[   22.462213] Booting processor 1/1 eip 3000
[   22.472393] Initializing CPU#1
[   22.549243] Calibrating delay using timer specific routine.. 4399.94 BogoMIPS (lpj=8799886)
[   22.549248] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   22.549253] monitor/mwait feature present.
[   22.549255] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.549257] CPU: L2 cache: 2048K
[   22.549258] CPU: Physical Processor ID: 0
[   22.549259] CPU: Processor Core ID: 1
[   22.549260] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   22.549749] CPU1: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   22.549765] Total of 2 processors activated (8803.22 BogoMIPS).
[   22.549911] ENABLING IO-APIC IRQs
[   22.550073] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.697192] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   22.717185] Brought up 2 CPUs
[   22.717206] CPU0 attaching sched-domain:
[   22.717208]  domain 0: span 03
[   22.717209]   groups: 01 02
[   22.717212] CPU1 attaching sched-domain:
[   22.717213]  domain 0: span 03
[   22.717214]   groups: 02 01
[   22.717388] net_namespace: 64 bytes
[   22.717397] Booting paravirtualized kernel on bare hardware
[   22.717744] Time:  8:48:04  Date: 09/01/08
[   22.717766] NET: Registered protocol family 16
[   22.717908] EISA bus registered
[   22.717912] ACPI: bus type pci registered
[   22.718219] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[   22.718221] PCI: Using configuration type 1
[   22.718235] Setting up standard PCI resources
[   22.727080] ACPI: EC: Look up EC in DSDT
[   22.730701] ACPI: Interpreter enabled
[   22.730703] ACPI: (supports S0 S1 S3 S4 S5)
[   22.730716] ACPI: Using IOAPIC for interrupt routing
[   22.735630] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.736116] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   22.736120] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   22.736527] PCI: Transparent bridge - 0000:00:1e.0
[   22.736551] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.736661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   22.736729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   22.736808] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   22.738498] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   22.738595] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   22.738689] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   22.738783] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   22.738877] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   22.738971] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   22.739065] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   22.739160] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[   22.739261] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.739285] pnp: PnP ACPI init
[   22.739291] ACPI: bus type pnp registered
[   22.741591] pnp: PnP ACPI: found 16 devices
[   22.741593] ACPI: ACPI bus type pnp unregistered
[   22.741596] PnPBIOS: Disabled by ACPI PNP
[   22.741763] PCI: Using ACPI for IRQ routing
[   22.741765] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.769086] NET: Registered protocol family 8
[   22.769089] NET: Registered protocol family 20
[   22.769130] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   22.769136] hpet0: 3 64-bit timers, 14318180 Hz
[   22.770165] AppArmor: AppArmor Filesystem Enabled
[   22.773083] Time: tsc clocksource has been installed.
[   22.773097] Switched to high resolution mode on CPU 0
[   22.773185] Switched to high resolution mode on CPU 1
[   22.789106] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   22.789117] system 00:06: ioport range 0x290-0x297 has been reserved
[   22.789125] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   22.789129] system 00:07: ioport range 0x800-0x87f has been reserved
[   22.789133] system 00:07: ioport range 0x480-0x4bf has been reserved
[   22.789136] system 00:07: ioport range 0x900-0x91f has been reserved
[   22.789140] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   22.789144] system 00:07: iomem range 0xfed20000-0xfed8ffff has been reserved
[   22.789148] system 00:07: iomem range 0xffb00000-0xffbfffff has been reserved
[   22.789152] system 00:07: iomem range 0xfff00000-0xffffffff could not be reserved
[   22.789162] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   22.789166] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   22.789174] system 00:0d: iomem range 0xffc00000-0xfff7ffff has been reserved
[   22.789182] system 00:0e: iomem range 0xf0000000-0xf3ffffff has been reserved
[   22.789191] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   22.789195] system 00:0f: iomem range 0xc0000-0xdffff could not be reserved
[   22.789198] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   22.789202] system 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
[   22.789206] system 00:0f: iomem range 0x0-0x0 could not be reserved
[   22.819494] PCI: Bridge: 0000:00:01.0
[   22.819496]   IO window: e000-efff
[   22.819499]   MEM window: d9f00000-dbffffff
[   22.819502]   PREFETCH window: e0000000-efffffff
[   22.819504] PCI: Bridge: 0000:00:1c.0
[   22.819507]   IO window: d000-dfff
[   22.819510]   MEM window: disabled.
[   22.819513]   PREFETCH window: disabled.
[   22.819517] PCI: Bridge: 0000:00:1e.0
[   22.819519]   IO window: c000-cfff
[   22.819523]   MEM window: disabled.
[   22.819526]   PREFETCH window: dc000000-dfffffff
[   22.819540] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.819544] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.819559] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.819563] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.819572] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   22.819580] NET: Registered protocol family 2
[   22.857064] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.857271] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.857672] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.857897] TCP: Hash tables configured (established 131072 bind 65536)
[   22.857899] TCP reno registered
[   22.869149] checking if image is initramfs... it is
[   23.381166] Freeing initrd memory: 7286k freed
[   23.381790] audit: initializing netlink socket (disabled)
[   23.381805] audit(1220258884.157:1): initialized
[   23.381953] highmem bounce pool size: 64 pages
[   23.383418] VFS: Disk quotas dquot_6.5.1
[   23.383474] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.383579] io scheduler noop registered
[   23.383580] io scheduler anticipatory registered
[   23.383582] io scheduler deadline registered
[   23.383590] io scheduler cfq registered (default)
[   23.383681] Boot video device is 0000:03:00.0
[   23.383757] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.383788] assign_interrupt_mode Found MSI capability
[   23.383814] Allocate Port Service[0000:00:01.0:pcie00]
[   23.383877] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.383913] assign_interrupt_mode Found MSI capability
[   23.383942] Allocate Port Service[0000:00:1c.0:pcie00]
[   23.383965] Allocate Port Service[0000:00:1c.0:pcie02]
[   23.384145] isapnp: Scanning for PnP cards...
[   23.736978] isapnp: No Plug & Play device found
[   23.755599] Real Time Clock Driver v1.12ac
[   23.755763] hpet_resources: 0xfed00000 is busy
[   23.755798] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.756719] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.756771] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.756846] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   23.759525] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.759529] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.776170] mice: PS/2 mouse device common for all mice
[   23.776285] EISA: Probing bus 0 at eisa.0
[   23.776310] EISA: Detected 0 cards.
[   23.776313] cpuidle: using governor ladder
[   23.776314] cpuidle: using governor menu
[   23.776388] NET: Registered protocol family 1
[   23.776412] Using IPI No-Shortcut mode
[   23.776438] registered taskstats version 1
[   23.776509]   Magic number: 8:725:825
[   23.776556]   hash matches device ptyt5
[   23.776585] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.776587] EDD information not available.
[   23.776744] Freeing unused kernel memory: 368k freed
[   24.945758] fuse init (API version 7.9)
[   24.964233] ACPI: SSDT 3FFAE0C0, 0214 (r1    AMI   CPU1PM        1 INTL 20051117)
[   24.964663] ACPI: Processor [CPU1] (supports 8 throttling states)
[   24.964787] ACPI: SSDT 3FFAE2E0, 0143 (r1    AMI   CPU2PM        1 INTL 20051117)
[   24.965213] ACPI: Processor [CPU2] (supports 8 throttling states)
[   24.965225] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.965234] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.258058] usbcore: registered new interface driver usbfs
[   25.258078] usbcore: registered new interface driver hub
[   25.258159] usbcore: registered new device driver usb
[   25.259371] SCSI subsystem initialized
[   25.259457] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 17
[   25.259466] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   25.259469] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   25.259695] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   25.263596] ehci_hcd 0000:00:1d.7: debug port 1
[   25.263601] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   25.263610] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xd9effc00
[   25.275538] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.275651] usb usb1: configuration #1 chosen from 1 choice
[   25.275670] hub 1-0:1.0: USB hub found
[   25.275675] hub 1-0:1.0: 8 ports detected
[   25.338677] USB Universal Host Controller Interface driver v3.0
[   25.338764] libata version 3.00 loaded.
[   25.379532] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 17
[   25.379544] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   25.379548] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   25.379571] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   25.379594] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00009000
[   25.379686] usb usb2: configuration #1 chosen from 1 choice
[   25.379705] hub 2-0:1.0: USB hub found
[   25.379710] hub 2-0:1.0: 2 ports detected
[   25.483412] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
[   25.483421] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   25.483425] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.483444] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   25.483468] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00009400
[   25.483561] usb usb3: configuration #1 chosen from 1 choice
[   25.483579] hub 3-0:1.0: USB hub found
[   25.483582] hub 3-0:1.0: 2 ports detected
[   25.587306] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   25.587316] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   25.587319] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   25.587341] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   25.587366] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00009800
[   25.587454] usb usb4: configuration #1 chosen from 1 choice
[   25.587472] hub 4-0:1.0: USB hub found
[   25.587476] hub 4-0:1.0: 2 ports detected
[   25.619193] usb 1-3: new high speed USB device using ehci_hcd and address 2
[   25.690251] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 20
[   25.690265] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   25.690270] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   25.690301] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   25.690325] uhci_hcd 0000:00:1d.3: irq 20, io base 0x0000a000
[   25.690409] usb usb5: configuration #1 chosen from 1 choice
[   25.690428] hub 5-0:1.0: USB hub found
[   25.690432] hub 5-0:1.0: 2 ports detected
[   25.770264] usb 1-3: configuration #1 chosen from 1 choice
[   25.797341] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 21
[   25.797374] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.797385] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   25.797408] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 22
[   25.797423] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   25.797431] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   25.799807] ata_piix 0000:00:1f.1: version 2.12
[   25.799818] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 21
[   25.799842] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.799896] scsi0 : ata_piix
[   25.799932] scsi1 : ata_piix
[   25.800800] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   25.800803] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   26.119020] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S202J, SB01, max UDMA/66
[   26.289778] ata1.00: configured for UDMA/66
[   26.321474] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   26.456689] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202J  SB01 PQ: 0 ANSI: 5
[   26.456747] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   26.456765] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 22
[   26.456796] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   26.456829] scsi2 : ata_piix
[   26.456863] scsi3 : ata_piix
[   26.457781] ata3: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xa400 irq 22
[   26.457783] ata4: SATA max UDMA/133 cmd 0xb000 ctl 0xa800 bmdma 0xa408 irq 22
[   26.500608] usb 3-2: configuration #1 chosen from 1 choice
[   26.514679] usbcore: registered new interface driver hiddev
[   26.529787] input: Generic USB+PS2 Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input1
[   26.561281] input,hidraw0: USB HID v1.10 Keyboard [Generic USB+PS2 Keyboard] on usb-0000:00:1d.1-2
[   26.588481] input: Generic USB+PS2 Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input2
[   26.597235] input,hidraw1: USB HID v1.10 Device [Generic USB+PS2 Keyboard] on usb-0000:00:1d.1-2
[   26.597253] usbcore: registered new interface driver usbhid
[   26.597257] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   26.639988] ata3.00: ATA-7: WDC WD1600AAJS-22PSA0, 05.06H05, max UDMA/133
[   26.639995] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   26.653562] ata3.00: configured for UDMA/133
[   26.817488] ata4.00: ATA-8: WDC WD3200AAKS-00B3A0, 01.03A01, max UDMA/133
[   26.817494] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   26.826468] ata4.00: configured for UDMA/133
[   26.826612] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-2 05.0 PQ: 0 ANSI: 5
[   26.826714] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[   26.836128] Driver 'sd' needs updating - please use bus_type methods
[   26.836211] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   26.836222] sd 2:0:0:0: [sda] Write Protect is off
[   26.836224] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.836236] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.836277] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   26.836285] sd 2:0:0:0: [sda] Write Protect is off
[   26.836287] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.836299] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.836302]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   26.839702]  sda1
[   26.839778] sd 2:0:0:0: [sda] Attached SCSI disk
[   26.839815] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   26.839823] sd 3:0:0:0: [sdb] Write Protect is off
[   26.839825] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   26.839838] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.839867] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   26.839875] sd 3:0:0:0: [sdb] Write Protect is off
[   26.839876] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   26.839888] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.839891]  sdb:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   26.841887] Uniform CD-ROM driver Revision: 3.20
[   26.841942] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   26.856606]  sdb1 sdb2
[   26.856940] sd 3:0:0:0: [sdb] Attached SCSI disk
[   26.860477] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   26.860493] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   26.860507] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   27.084760] Attempting manual resume
[   27.084763] swsusp: Resume From Partition 8:17
[   27.084765] PM: Checking swsusp image.
[   27.084922] PM: Resume from disk failed.
[   33.500112] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   33.571509] iTCO_vendor_support: vendor-support=0
[   33.595143] Linux agpgart interface v0.102
[   33.647169] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.722966] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   33.723049] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   33.723079] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.767009] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.853759] input: Power Button (FF) as /devices/virtual/input/input4
[   33.910776] ACPI: Power Button (FF) [PWRF]
[   33.910851] input: Power Button (CM) as /devices/virtual/input/input5
[   33.917645] intel_rng: FWH not detected
[   33.970715] ACPI: Power Button (CM) [PWRB]
[   34.157555] Linux video capture interface: v2.00
[   34.308318] ivtv:  Start initialization, version 1.1.0
[   34.308382] ivtv0: Initializing card #0
[   34.308384] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   34.356322] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 21 (level, low) -> IRQ 23
[   34.482354] tveeprom 0-0050: Hauppauge model 26582, rev F0B2, serial# 9717486
[   34.482357] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   34.482359] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   34.482361] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   34.482363] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   34.482365] tveeprom 0-0050: has no radio, has no IR receiver, has no IR transmitter
[   34.482367] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   34.637110] nvidia: module license 'NVIDIA' taints kernel.
[   34.925185] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   34.943442] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   34.976892] input: ImPS/2 Generic Wheel Mouse as /devices/platform[CENTER][LEFT][/LEFT][/CENTER]/i8042/serio1/input/input6
[   34.987117] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   35.061462] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   35.070155] tuner-simple 0-0061: type set to 50 (TCL 2002N)
[   35.070158] tuner 0-0061: type set to TCL 2002N
[   35.070385] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   35.070399] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   35.070414] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   35.070427] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   35.070430] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   35.070443] ivtv:  End initialization
[   35.070522] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.070529] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   35.070620] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   35.149346] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 20
[   35.149370] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.175324] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   35.240424] usb 1-3: reset high speed USB device using ehci_hcd and address 2
[   35.422575] ndiswrapper: driver rt2870 (Arcadyan Technology Corporation,08/24/2007, 1.00.04.0000) loaded
[   35.768195] wlan0: ethernet device 00:1c:df:30:bf:fb using NDIS driver: rt2870, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11n Wireless Card.', 050D:815C.F.conf
[   35.768898] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   35.768937] usbcore: registered new interface driver ndiswrapper
[   35.901811] lp: driver loaded but no devices found
[   35.968637] Adding 1558264k swap on /dev/sdb1.  Priority:-1 extents:1 across:1558264k
[   37.545214] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.879008] No dock devices found.
[   39.049054] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   39.049058] apm: disabled - APM is not SMP safe.
[   39.199867] ppdev: user-space parallel port driver
[   39.347700] audit(1220276900.543:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5072 profile="/usr/sbin/cupsd" namespace="default"
[   41.116522] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   41.314344] ivtv0: Encoder revision: 0x02060039
[   44.780783] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   45.203705] Bluetooth: Core ver 2.11
[   45.203812] NET: Registered protocol family 31
[   45.203815] Bluetooth: HCI device and connection manager initialized
[   45.203819] Bluetooth: HCI socket layer initialized
[   45.222444] Bluetooth: L2CAP ver 2.9
[   45.222451] Bluetooth: L2CAP socket layer initialized
[   45.278253] Bluetooth: RFCOMM socket layer initialized
[   45.278267] Bluetooth: RFCOMM TTY layer initialized
[   45.278269] Bluetooth: RFCOMM ver 1.8
[  100.463545] NET: Registered protocol family 10
[  100.463851] lo: Disabled Privacy Extensions
[  108.219239] NET: Registered protocol family 17
[  110.455799] wlan0: no IPv6 routers present
[  129.796092] wlan0: no IPv6 routers present

```

When install the Xawtv package, and try to configure it nothing happens just a black screen, also my card only has 1 s~video in and 1 composite video,audio left, audio right besides the standard 75 ohm cable input but according to xawtv app it sees 2 composite in sets and 2 s~video sets :(

Now I am a very new user but I can learn quickly, if I can find the right materials to read.

Places I have been before coming here are the following:

1. Linuxtv.org (assumes that I know alot about my card which I do not)
2. ivtv.org    (assumes that I know a lot about Linux which I do not)
3. LinuxQuestions.org  (got more questions than answers there :( )

I have searched the forums and found a lot of posts about this card but they are from people that have at least half of it working, I tried some of these first but to no avail cant seem to get anything to compile at all seem to be missing some stuff to do that but I am not sure anymore.

I think I may have to reinstall linux and try again :(

please if anyone knows the answer I will be greatful for the help

---

### Post by wolfen69 on 2008-09-01
I have a Hauppauge pvr card running on my hardy box, and I get  tv by: 

```
sudo apt-get install ivtv-utils 
```

open VLC player

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

```
ivtv-tune -c25
``` (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

```
cat /dev/video0 > /tmp/name_of_file.mpg
```

it will record whatever channel you are on. then ctrl-c to stop.

as far as i know, xawtv is v4l based and will not work with the pvr150. enjoy.

also, welcome to ubuntu!

---

### Post by Randy_D28 on 2008-09-01
Okay, I followed your instructions and installed java and CSMonkey remote control programs.

Now when I enter the "ivtv-tune -h" command in a terminal I get this:

```
Usage: ivtv-tune [OPTIONS]...

  -h, --help              Print help and exit
  -V, --version           Print version and exit
  -c, --channel=CHANNEL   set new channel
  -d, --device=DEVICE     set video device node
  -f, --frequency=FREQ    set new frequency (MHz)
  -l, --list-channels     list all channels and their frequencies  
                            (default=off)
  -L, --list-freqtable    list all available frequency mappings  (default=off)
  -t, --freqtable=STRING  set frequency map to use
  -x, --xawtv=CHANNEL     set new channel using custom map from ~/.xawtv
```

now for the questions.

1. what is a frequency map and how do I get/make it ?

2. how do I tell it to use NTSC ?

3. how can I tell the card when to use S-video,composite or tuner ?

thanks for the help so far, I think with just a little more I can get it.

Randy

EDIT: After a reboot, it started working woo hoo, but I am still stuck on what terminal command tells the card to use the composite mode.

---

### Post by wolfen69 on 2008-09-01
i found this [here]("http://ivtv.sourceforge.net/FAQ.html")

Set PAL video standard

[root@host]# ./test_ioctl -u 0xff

Set NTSC video standard

[root@host]# ./test_ioctl -u 0x3000

Select tuner input

[root@host]# ./test_ioctl -p 0

Select composite video input

[root@host]# ./test_ioctl -p 5

Set full PAL resolution

[root@host]# ./test_ioctl -f width=720,height=576

Set full NTSC resolution

[root@host]# ./test_ioctl -f width=720,height=480

Finally, try to capture some video:

[root@host]# cat /dev/video0 > first_capture.mpg

Press ctrl-c to stop the capture.

---

### Post by Randy_D28 on 2008-09-01
Thanks Wolfen69, you have made my day sir :), in the I have book marked all of the links and pages you and others have given me and when I have the time I will be reading and studying these very closely so I won't have to bug you guys so much. :)

Randy

---

### Post by saedelaere on 2008-09-10
> **Randy_D28 said:**
> Hello, I am Randy a very new user and need a lot of help in regaurds to Linux and tvcard.

I find that most posts seem to ask for the info below but if you need more info just tell me how to get it and I will.

system : dual core (cheapie), 1GB Ram, 320GB sata HDD, Nvidia gforce 7300GS  (basicly bottom of the barrel cheap hardware about $220.00 tops)
 
I guess it is possible my system is to cheap to run Linux, it sure could not handle windows Vista Basic in classic mode.

lspci output :
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)

```

Dmesg output: 

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffa0000 - 000000003ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffae000 - 000000003ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ffe0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262048) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262048
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262048
[    0.000000] On node 0 totalpages: 262048
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32417 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB030 checksum 0
[    0.000000] ACPI: RSDP 000FB030, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 3FFA0100, 0054 (r1 &#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;  8000701 MSFT       97)
[    0.000000] ACPI: FACP 3FFA0290, 00F4 (r3 A_M_I_ OEMFACP   8000701 MSFT       97)
[    0.000000] ACPI: DSDT 3FFA05C0, 682B (r1  A0798 A0798000        0 INTL 20051117)
[    0.000000] ACPI: FACS 3FFAE000, 0040
[    0.000000] ACPI: APIC 3FFA0390, 006C (r1 A_M_I_ OEMAPIC   8000701 MSFT       97)
[    0.000000] ACPI: MCFG 3FFA0400, 003C (r1 A_M_I_ OEMMCFG   8000701 MSFT       97)
[    0.000000] ACPI: SLIC 3FFA0440, 0176 (r1 &#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;  8000701 MSFT       97)
[    0.000000] ACPI: OEMB 3FFAE040, 0080 (r1 A_M_I_ AMI_OEM   8000701 MSFT       97)
[    0.000000] ACPI: HPET 3FFA6DF0, 0038 (r1 A_M_I_ OEMHPET   8000701 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260001
[    0.000000] Kernel command line: root=UUID=68697cf8-8b9f-4d97-927b-14db681829fe ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2200.035 MHz processor.
[   22.082793] Console: colour VGA+ 80x25
[   22.082797] console [tty0] enabled
[   22.083007] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.083231] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.101541] Memory: 1027052k/1048192k available (2177k kernel code, 20456k reserved, 1006k data, 368k init, 130688k highmem)
[   22.101546] virtual kernel memory layout:
[   22.101547]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   22.101548]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.101548]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.101549]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.101550]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   22.101551]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   22.101551]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   22.101554] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.101579] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   22.101688] hpet clockevent registered
[   22.181613] Calibrating delay using timer specific routine.. 4403.28 BogoMIPS (lpj=8806569)
[   22.181628] Security Framework initialized
[   22.181632] SELinux:  Disabled at boot.
[   22.181641] AppArmor: AppArmor initialized
[   22.181644] Failure registering capabilities with primary security module.
[   22.181649] Mount-cache hash table entries: 512
[   22.181734] Initializing cgroup subsys ns
[   22.181738] Initializing cgroup subsys cpuacct
[   22.181745] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   22.181751] monitor/mwait feature present.
[   22.181752] using mwait in idle threads.
[   22.181755] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.181757] CPU: L2 cache: 2048K
[   22.181759] CPU: Physical Processor ID: 0
[   22.181760] CPU: Processor Core ID: 0
[   22.181761] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   22.181768] Compat vDSO mapped to ffffe000.
[   22.181777] Checking 'hlt' instruction... OK.
[   22.197973] SMP alternatives: switching to UP code
[   22.199260] Early unpacking initramfs... done
[   22.459535] ACPI: Core revision 20070126
[   22.459573] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.461625] CPU0: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   22.461640] SMP alternatives: switching to SMP code
[   22.462213] Booting processor 1/1 eip 3000
[   22.472393] Initializing CPU#1
[   22.549243] Calibrating delay using timer specific routine.. 4399.94 BogoMIPS (lpj=8799886)
[   22.549248] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   22.549253] monitor/mwait feature present.
[   22.549255] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.549257] CPU: L2 cache: 2048K
[   22.549258] CPU: Physical Processor ID: 0
[   22.549259] CPU: Processor Core ID: 1
[   22.549260] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   22.549749] CPU1: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   22.549765] Total of 2 processors activated (8803.22 BogoMIPS).
[   22.549911] ENABLING IO-APIC IRQs
[   22.550073] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.697192] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   22.717185] Brought up 2 CPUs
[   22.717206] CPU0 attaching sched-domain:
[   22.717208]  domain 0: span 03
[   22.717209]   groups: 01 02
[   22.717212] CPU1 attaching sched-domain:
[   22.717213]  domain 0: span 03
[   22.717214]   groups: 02 01
[   22.717388] net_namespace: 64 bytes
[   22.717397] Booting paravirtualized kernel on bare hardware
[   22.717744] Time:  8:48:04  Date: 09/01/08
[   22.717766] NET: Registered protocol family 16
[   22.717908] EISA bus registered
[   22.717912] ACPI: bus type pci registered
[   22.718219] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[   22.718221] PCI: Using configuration type 1
[   22.718235] Setting up standard PCI resources
[   22.727080] ACPI: EC: Look up EC in DSDT
[   22.730701] ACPI: Interpreter enabled
[   22.730703] ACPI: (supports S0 S1 S3 S4 S5)
[   22.730716] ACPI: Using IOAPIC for interrupt routing
[   22.735630] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.736116] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   22.736120] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   22.736527] PCI: Transparent bridge - 0000:00:1e.0
[   22.736551] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.736661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   22.736729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   22.736808] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   22.738498] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   22.738595] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   22.738689] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   22.738783] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   22.738877] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   22.738971] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   22.739065] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   22.739160] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[   22.739261] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.739285] pnp: PnP ACPI init
[   22.739291] ACPI: bus type pnp registered
[   22.741591] pnp: PnP ACPI: found 16 devices
[   22.741593] ACPI: ACPI bus type pnp unregistered
[   22.741596] PnPBIOS: Disabled by ACPI PNP
[   22.741763] PCI: Using ACPI for IRQ routing
[   22.741765] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.769086] NET: Registered protocol family 8
[   22.769089] NET: Registered protocol family 20
[   22.769130] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   22.769136] hpet0: 3 64-bit timers, 14318180 Hz
[   22.770165] AppArmor: AppArmor Filesystem Enabled
[   22.773083] Time: tsc clocksource has been installed.
[   22.773097] Switched to high resolution mode on CPU 0
[   22.773185] Switched to high resolution mode on CPU 1
[   22.789106] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   22.789117] system 00:06: ioport range 0x290-0x297 has been reserved
[   22.789125] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   22.789129] system 00:07: ioport range 0x800-0x87f has been reserved
[   22.789133] system 00:07: ioport range 0x480-0x4bf has been reserved
[   22.789136] system 00:07: ioport range 0x900-0x91f has been reserved
[   22.789140] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   22.789144] system 00:07: iomem range 0xfed20000-0xfed8ffff has been reserved
[   22.789148] system 00:07: iomem range 0xffb00000-0xffbfffff has been reserved
[   22.789152] system 00:07: iomem range 0xfff00000-0xffffffff could not be reserved
[   22.789162] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   22.789166] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   22.789174] system 00:0d: iomem range 0xffc00000-0xfff7ffff has been reserved
[   22.789182] system 00:0e: iomem range 0xf0000000-0xf3ffffff has been reserved
[   22.789191] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   22.789195] system 00:0f: iomem range 0xc0000-0xdffff could not be reserved
[   22.789198] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   22.789202] system 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
[   22.789206] system 00:0f: iomem range 0x0-0x0 could not be reserved
[   22.819494] PCI: Bridge: 0000:00:01.0
[   22.819496]   IO window: e000-efff
[   22.819499]   MEM window: d9f00000-dbffffff
[   22.819502]   PREFETCH window: e0000000-efffffff
[   22.819504] PCI: Bridge: 0000:00:1c.0
[   22.819507]   IO window: d000-dfff
[   22.819510]   MEM window: disabled.
[   22.819513]   PREFETCH window: disabled.
[   22.819517] PCI: Bridge: 0000:00:1e.0
[   22.819519]   IO window: c000-cfff
[   22.819523]   MEM window: disabled.
[   22.819526]   PREFETCH window: dc000000-dfffffff
[   22.819540] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.819544] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.819559] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.819563] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.819572] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   22.819580] NET: Registered protocol family 2
[   22.857064] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.857271] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.857672] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.857897] TCP: Hash tables configured (established 131072 bind 65536)
[   22.857899] TCP reno registered
[   22.869149] checking if image is initramfs... it is
[   23.381166] Freeing initrd memory: 7286k freed
[   23.381790] audit: initializing netlink socket (disabled)
[   23.381805] audit(1220258884.157:1): initialized
[   23.381953] highmem bounce pool size: 64 pages
[   23.383418] VFS: Disk quotas dquot_6.5.1
[   23.383474] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.383579] io scheduler noop registered
[   23.383580] io scheduler anticipatory registered
[   23.383582] io scheduler deadline registered
[   23.383590] io scheduler cfq registered (default)
[   23.383681] Boot video device is 0000:03:00.0
[   23.383757] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.383788] assign_interrupt_mode Found MSI capability
[   23.383814] Allocate Port Service[0000:00:01.0:pcie00]
[   23.383877] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.383913] assign_interrupt_mode Found MSI capability
[   23.383942] Allocate Port Service[0000:00:1c.0:pcie00]
[   23.383965] Allocate Port Service[0000:00:1c.0:pcie02]
[   23.384145] isapnp: Scanning for PnP cards...
[   23.736978] isapnp: No Plug & Play device found
[   23.755599] Real Time Clock Driver v1.12ac
[   23.755763] hpet_resources: 0xfed00000 is busy
[   23.755798] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.756719] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.756771] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.756846] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   23.759525] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.759529] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.776170] mice: PS/2 mouse device common for all mice
[   23.776285] EISA: Probing bus 0 at eisa.0
[   23.776310] EISA: Detected 0 cards.
[   23.776313] cpuidle: using governor ladder
[   23.776314] cpuidle: using governor menu
[   23.776388] NET: Registered protocol family 1
[   23.776412] Using IPI No-Shortcut mode
[   23.776438] registered taskstats version 1
[   23.776509]   Magic number: 8:725:825
[   23.776556]   hash matches device ptyt5
[   23.776585] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.776587] EDD information not available.
[   23.776744] Freeing unused kernel memory: 368k freed
[   24.945758] fuse init (API version 7.9)
[   24.964233] ACPI: SSDT 3FFAE0C0, 0214 (r1    AMI   CPU1PM        1 INTL 20051117)
[   24.964663] ACPI: Processor [CPU1] (supports 8 throttling states)
[   24.964787] ACPI: SSDT 3FFAE2E0, 0143 (r1    AMI   CPU2PM        1 INTL 20051117)
[   24.965213] ACPI: Processor [CPU2] (supports 8 throttling states)
[   24.965225] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.965234] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.258058] usbcore: registered new interface driver usbfs
[   25.258078] usbcore: registered new interface driver hub
[   25.258159] usbcore: registered new device driver usb
[   25.259371] SCSI subsystem initialized
[   25.259457] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 17
[   25.259466] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   25.259469] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   25.259695] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   25.263596] ehci_hcd 0000:00:1d.7: debug port 1
[   25.263601] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   25.263610] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xd9effc00
[   25.275538] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.275651] usb usb1: configuration #1 chosen from 1 choice
[   25.275670] hub 1-0:1.0: USB hub found
[   25.275675] hub 1-0:1.0: 8 ports detected
[   25.338677] USB Universal Host Controller Interface driver v3.0
[   25.338764] libata version 3.00 loaded.
[   25.379532] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 17
[   25.379544] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   25.379548] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   25.379571] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   25.379594] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00009000
[   25.379686] usb usb2: configuration #1 chosen from 1 choice
[   25.379705] hub 2-0:1.0: USB hub found
[   25.379710] hub 2-0:1.0: 2 ports detected
[   25.483412] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
[   25.483421] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   25.483425] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.483444] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   25.483468] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00009400
[   25.483561] usb usb3: configuration #1 chosen from 1 choice
[   25.483579] hub 3-0:1.0: USB hub found
[   25.483582] hub 3-0:1.0: 2 ports detected
[   25.587306] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   25.587316] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   25.587319] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   25.587341] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   25.587366] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00009800
[   25.587454] usb usb4: configuration #1 chosen from 1 choice
[   25.587472] hub 4-0:1.0: USB hub found
[   25.587476] hub 4-0:1.0: 2 ports detected
[   25.619193] usb 1-3: new high speed USB device using ehci_hcd and address 2
[   25.690251] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 20
[   25.690265] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   25.690270] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   25.690301] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   25.690325] uhci_hcd 0000:00:1d.3: irq 20, io base 0x0000a000
[   25.690409] usb usb5: configuration #1 chosen from 1 choice
[   25.690428] hub 5-0:1.0: USB hub found
[   25.690432] hub 5-0:1.0: 2 ports detected
[   25.770264] usb 1-3: configuration #1 chosen from 1 choice
[   25.797341] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 21
[   25.797374] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.797385] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   25.797408] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 22
[   25.797423] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   25.797431] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   25.799807] ata_piix 0000:00:1f.1: version 2.12
[   25.799818] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 21
[   25.799842] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.799896] scsi0 : ata_piix
[   25.799932] scsi1 : ata_piix
[   25.800800] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   25.800803] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   26.119020] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S202J, SB01, max UDMA/66
[   26.289778] ata1.00: configured for UDMA/66
[   26.321474] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   26.456689] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202J  SB01 PQ: 0 ANSI: 5
[   26.456747] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   26.456765] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 22
[   26.456796] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   26.456829] scsi2 : ata_piix
[   26.456863] scsi3 : ata_piix
[   26.457781] ata3: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xa400 irq 22
[   26.457783] ata4: SATA max UDMA/133 cmd 0xb000 ctl 0xa800 bmdma 0xa408 irq 22
[   26.500608] usb 3-2: configuration #1 chosen from 1 choice
[   26.514679] usbcore: registered new interface driver hiddev
[   26.529787] input: Generic USB+PS2 Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input1
[   26.561281] input,hidraw0: USB HID v1.10 Keyboard [Generic USB+PS2 Keyboard] on usb-0000:00:1d.1-2
[   26.588481] input: Generic USB+PS2 Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input2
[   26.597235] input,hidraw1: USB HID v1.10 Device [Generic USB+PS2 Keyboard] on usb-0000:00:1d.1-2
[   26.597253] usbcore: registered new interface driver usbhid
[   26.597257] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   26.639988] ata3.00: ATA-7: WDC WD1600AAJS-22PSA0, 05.06H05, max UDMA/133
[   26.639995] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   26.653562] ata3.00: configured for UDMA/133
[   26.817488] ata4.00: ATA-8: WDC WD3200AAKS-00B3A0, 01.03A01, max UDMA/133
[   26.817494] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   26.826468] ata4.00: configured for UDMA/133
[   26.826612] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-2 05.0 PQ: 0 ANSI: 5
[   26.826714] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[   26.836128] Driver 'sd' needs updating - please use bus_type methods
[   26.836211] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   26.836222] sd 2:0:0:0: [sda] Write Protect is off
[   26.836224] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.836236] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.836277] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   26.836285] sd 2:0:0:0: [sda] Write Protect is off
[   26.836287] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.836299] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.836302]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   26.839702]  sda1
[   26.839778] sd 2:0:0:0: [sda] Attached SCSI disk
[   26.839815] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   26.839823] sd 3:0:0:0: [sdb] Write Protect is off
[   26.839825] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   26.839838] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.839867] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   26.839875] sd 3:0:0:0: [sdb] Write Protect is off
[   26.839876] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   26.839888] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.839891]  sdb:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   26.841887] Uniform CD-ROM driver Revision: 3.20
[   26.841942] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   26.856606]  sdb1 sdb2
[   26.856940] sd 3:0:0:0: [sdb] Attached SCSI disk
[   26.860477] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   26.860493] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   26.860507] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   27.084760] Attempting manual resume
[   27.084763] swsusp: Resume From Partition 8:17
[   27.084765] PM: Checking swsusp image.
[   27.084922] PM: Resume from disk failed.
[   33.500112] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   33.571509] iTCO_vendor_support: vendor-support=0
[   33.595143] Linux agpgart interface v0.102
[   33.647169] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.722966] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   33.723049] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   33.723079] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.767009] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.853759] input: Power Button (FF) as /devices/virtual/input/input4
[   33.910776] ACPI: Power Button (FF) [PWRF]
[   33.910851] input: Power Button (CM) as /devices/virtual/input/input5
[   33.917645] intel_rng: FWH not detected
[   33.970715] ACPI: Power Button (CM) [PWRB]
[   34.157555] Linux video capture interface: v2.00
[   34.308318] ivtv:  Start initialization, version 1.1.0
[   34.308382] ivtv0: Initializing card #0
[   34.308384] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   34.356322] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 21 (level, low) -> IRQ 23
[   34.482354] tveeprom 0-0050: Hauppauge model 26582, rev F0B2, serial# 9717486
[   34.482357] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   34.482359] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   34.482361] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   34.482363] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   34.482365] tveeprom 0-0050: has no radio, has no IR receiver, has no IR transmitter
[   34.482367] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   34.637110] nvidia: module license 'NVIDIA' taints kernel.
[   34.925185] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   34.943442] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   34.976892] input: ImPS/2 Generic Wheel Mouse as /devices/platform[CENTER][LEFT][/LEFT][/CENTER]/i8042/serio1/input/input6
[   34.987117] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   35.061462] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   35.070155] tuner-simple 0-0061: type set to 50 (TCL 2002N)
[   35.070158] tuner 0-0061: type set to TCL 2002N
[   35.070385] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   35.070399] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   35.070414] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   35.070427] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   35.070430] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   35.070443] ivtv:  End initialization
[   35.070522] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.070529] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   35.070620] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   35.149346] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 20
[   35.149370] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.175324] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   35.240424] usb 1-3: reset high speed USB device using ehci_hcd and address 2
[   35.422575] ndiswrapper: driver rt2870 (Arcadyan Technology Corporation,08/24/2007, 1.00.04.0000) loaded
[   35.768195] wlan0: ethernet device 00:1c:df:30:bf:fb using NDIS driver: rt2870, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11n Wireless Card.', 050D:815C.F.conf
[   35.768898] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   35.768937] usbcore: registered new interface driver ndiswrapper
[   35.901811] lp: driver loaded but no devices found
[   35.968637] Adding 1558264k swap on /dev/sdb1.  Priority:-1 extents:1 across:1558264k
[   37.545214] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.879008] No dock devices found.
[   39.049054] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   39.049058] apm: disabled - APM is not SMP safe.
[   39.199867] ppdev: user-space parallel port driver
[   39.347700] audit(1220276900.543:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5072 profile="/usr/sbin/cupsd" namespace="default"
[   41.116522] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   41.314344] ivtv0: Encoder revision: 0x02060039
[   44.780783] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   45.203705] Bluetooth: Core ver 2.11
[   45.203812] NET: Registered protocol family 31
[   45.203815] Bluetooth: HCI device and connection manager initialized
[   45.203819] Bluetooth: HCI socket layer initialized
[   45.222444] Bluetooth: L2CAP ver 2.9
[   45.222451] Bluetooth: L2CAP socket layer initialized
[   45.278253] Bluetooth: RFCOMM socket layer initialized
[   45.278267] Bluetooth: RFCOMM TTY layer initialized
[   45.278269] Bluetooth: RFCOMM ver 1.8
[  100.463545] NET: Registered protocol family 10
[  100.463851] lo: Disabled Privacy Extensions
[  108.219239] NET: Registered protocol family 17
[  110.455799] wlan0: no IPv6 routers present
[  129.796092] wlan0: no IPv6 routers present

```

When install the Xawtv package, and try to configure it nothing happens just a black screen, also my card only has 1 s~video in and 1 composite video,audio left, audio right besides the standard 75 ohm cable input but according to xawtv app it sees 2 composite in sets and 2 s~video sets :(

Now I am a very new user but I can learn quickly, if I can find the right materials to read.

Places I have been before coming here are the following:

1. Linuxtv.org (assumes that I know alot about my card which I do not)
2. ivtv.org    (assumes that I know a lot about Linux which I do not)
3. LinuxQuestions.org  (got more questions than answers there :( )

I have searched the forums and found a lot of posts about this card but they are from people that have at least half of it working, I tried some of these first but to no avail cant seem to get anything to compile at all seem to be missing some stuff to do that but I am not sure anymore.

I think I may have to reinstall linux and try again :(

please if anyone knows the answer I will be greatful for the help

Hi,

[this one]("http://home.arcor.de/info_eng.html") could also work for you.

Regards

---

### Post by pshown on 2008-10-04
OK, I have video and audio working just fine with a PVR-150. I have the list of PVR setting as shown by the terminal but I do not know where or how to open the card configuration console/ panel. I am a real newbe to Linux but the more I use it and get from help from you guys, I am sure I will be a total convert. As a quick side note I am able to change the color settings in VLC but I have to do it for each session when I open it.Is their any way to lock the color settings?

---

