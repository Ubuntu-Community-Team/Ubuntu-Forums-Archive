---
title: "mythtv-setup saa7146 ERROR_OPEN"
date: 2008-09-27
forum: Multimedia Software
---

### Post by thomi_ch on 2008-09-27
hi all

i have a problem with my dvb-c card:
sudo lspci -vvv
01:0a.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
        Subsystem: KNC One Unknown device 002c
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (3750ns min, 9500ns max)
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at cfeffc00 (32-bit, non-prefetchable) [size=512]


sometimes i get an error in mythtv-setup / tv-cards / [ DVB : 0]
- Frontend ID: ERROR_OPEN

so, i can't watch tv or record anything.

i have searched around the web, google, mythtv-user irc.. but no really good solution.

i reboot my system more then once.. an sometimes i get the dvb-c card to work.. until next time...

here some more information about my system:
uname -a
Linux xena 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

dmesg:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Aug 25 17:32:09 UTC 2008 (Ubuntu 2.6.24-21.42-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffce000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262080
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262080
[    0.000000] On node 0 totalpages: 262080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32449 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB2A0 checksum 0
[    0.000000] ACPI: RSDP 000FB2A0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFC0000, 0034 (r1 A M I  OEMRSDT   8000405 MSFT       97)
[    0.000000] ACPI: FACP 3FFC0200, 0081 (r1 A M I  OEMFACP   8000405 MSFT       97)
[    0.000000] ACPI: DSDT 3FFC0400, 3C29 (r1  A0092 A0092001        1 INTL  2002026)
[    0.000000] ACPI: FACS 3FFCE000, 0040
[    0.000000] ACPI: APIC 3FFC0390, 0070 (r1 A M I  OEMAPIC   8000405 MSFT       97)
[    0.000000] ACPI: OEMB 3FFCE040, 0046 (r1 A M I  AMI_OEM   8000405 MSFT       97)
[    0.000000] ACPI: MCFG 3FFC4030, 003C (r1 A M I  OEMMCFG   8000405 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260033
[    0.000000] Kernel command line: root=UUID=c0a49495-377e-426f-9a67-b80f9649aaf9 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3192.196 MHz processor.
[   26.473119] Console: colour VGA+ 80x25
[   26.473123] console [tty0] enabled
[   26.473404] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   26.473719] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.497057] Memory: 1026808k/1048320k available (2177k kernel code, 20884k reserved, 1006k data, 368k init, 130816k highmem)
[   26.497064] virtual kernel memory layout:
[   26.497065]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   26.497066]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.497067]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   26.497068]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   26.497069]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   26.497070]       .data : 0xc0320514 - 0xc041bdc4   (1006 kB)
[   26.497071]       .text : 0xc0100000 - 0xc0320514   (2177 kB)
[   26.497074] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.497103] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   26.576927] Calibrating delay using timer specific routine.. 6390.04 BogoMIPS (lpj=12780089)
[   26.576948] Security Framework initialized
[   26.576952] SELinux:  Disabled at boot.
[   26.576963] AppArmor: AppArmor initialized
[   26.576967] Failure registering capabilities with primary security module.
[   26.576975] Mount-cache hash table entries: 512
[   26.577078] Initializing cgroup subsys ns
[   26.577082] Initializing cgroup subsys cpuacct
[   26.577093] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000649d 00000000 00000000 00000000
[   26.577101] monitor/mwait feature present.
[   26.577103] using mwait in idle threads.
[   26.577108] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   26.577111] CPU: L2 cache: 2048K
[   26.577113] CPU: Physical Processor ID: 0
[   26.577115] CPU: After all inits, caps: bfebfbff 20000000 00000000 00043180 0000649d 00000000 00000000 00000000
[   26.577124] Compat vDSO mapped to ffffe000.
[   26.577137] Checking 'hlt' instruction... OK.
[   26.593279] SMP alternatives: switching to UP code
[   26.594946] Early unpacking initramfs... done
[   26.885646] ACPI: Core revision 20070126
[   26.885691] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.898687] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[   26.898705] SMP alternatives: switching to SMP code
[   26.899413] Booting processor 1/1 eip 3000
[   26.909744] Initializing CPU#1
[   26.987918] Calibrating delay using timer specific routine.. 6384.49 BogoMIPS (lpj=12768996)
[   26.987928] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000649d 00000000 00000000 00000000
[   26.987935] monitor/mwait feature present.
[   26.987941] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   26.987944] CPU: L2 cache: 2048K
[   26.987946] CPU: Physical Processor ID: 0
[   26.987948] CPU: After all inits, caps: bfebfbff 20000000 00000000 00043180 0000649d 00000000 00000000 00000000
[   26.988475] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[   26.988514] Total of 2 processors activated (12774.54 BogoMIPS).
[   26.988660] ENABLING IO-APIC IRQs
[   26.988832] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   27.135697] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   27.155663] Brought up 2 CPUs
[   27.155690] CPU0 attaching sched-domain:
[   27.155693]  domain 0: span 03
[   27.155695]   groups: 01 02
[   27.155699]   domain 1: span 03
[   27.155701]    groups: 03
[   27.155703] CPU1 attaching sched-domain:
[   27.155705]  domain 0: span 03
[   27.155707]   groups: 02 01
[   27.155710]   domain 1: span 03
[   27.155711]    groups: 03
[   27.155963] net_namespace: 64 bytes
[   27.155974] Booting paravirtualized kernel on bare hardware
[   27.156500] Time:  7:57:49  Date: 09/27/08
[   27.156523] NET: Registered protocol family 16
[   27.156770] EISA bus registered
[   27.156775] ACPI: bus type pci registered
[   27.157105] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=6
[   27.157107] PCI: Using configuration type 1
[   27.157125] Setting up standard PCI resources
[   27.168635] ACPI: EC: Look up EC in DSDT
[   27.173558] ACPI: Interpreter enabled
[   27.173561] ACPI: (supports S0 S1 S3 S4 S5)
[   27.173579] ACPI: Using IOAPIC for interrupt routing
[   27.180748] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.181385] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   27.181389] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   27.182286] PCI: Transparent bridge - 0000:00:1e.0
[   27.182327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.182481] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   27.182545] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   27.182662] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   27.185575] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   27.185686] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   27.185795] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   27.185903] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   27.186010] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   27.186118] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   27.186227] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   27.186334] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   27.186475] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  F4, should be EF [20070126]
[   27.186483] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.186522] pnp: PnP ACPI init
[   27.186530] ACPI: bus type pnp registered
[   27.190692] pnp: PnP ACPI: found 16 devices
[   27.190694] ACPI: ACPI bus type pnp unregistered
[   27.190699] PnPBIOS: Disabled by ACPI PNP
[   27.191012] PCI: Using ACPI for IRQ routing
[   27.191016] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.231488] NET: Registered protocol family 8
[   27.231491] NET: Registered protocol family 20
[   27.231573] AppArmor: AppArmor Filesystem Enabled
[   27.235339] Time: tsc clocksource has been installed.
[   27.251488] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   27.251500] system 00:07: ioport range 0x290-0x297 has been reserved
[   27.251507] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   27.251510] system 00:08: ioport range 0x800-0x87f has been reserved
[   27.251512] system 00:08: ioport range 0x480-0x4bf has been reserved
[   27.251520] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   27.251525] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   27.251527] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   27.251530] system 00:08: iomem range 0xfff80000-0xffffffff could not be reserved
[   27.251537] system 00:0a: iomem range 0xffc00000-0xfff7ffff could not be reserved
[   27.251544] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   27.251546] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[   27.251553] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[   27.251559] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[   27.251565] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   27.251567] system 00:0f: iomem range 0x0-0x0 could not be reserved
[   27.251570] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   27.251573] system 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
[   27.251575] system 00:0f: iomem range 0x0-0x0 could not be reserved
[   27.282019] PCI: Bridge: 0000:00:01.0
[   27.282022]   IO window: e000-efff
[   27.282026]   MEM window: cff00000-cfffffff
[   27.282029]   PREFETCH window: d0000000-dfffffff
[   27.282033] PCI: Bridge: 0000:00:1c.0
[   27.282036]   IO window: d000-dfff
[   27.282040]   MEM window: disabled.
[   27.282044]   PREFETCH window: disabled.
[   27.282049] PCI: Bridge: 0000:00:1c.1
[   27.282051]   IO window: c000-cfff
[   27.282056]   MEM window: disabled.
[   27.282059]   PREFETCH window: disabled.
[   27.282064] PCI: Bridge: 0000:00:1c.2
[   27.282066]   IO window: b000-bfff
[   27.282070]   MEM window: disabled.
[   27.282074]   PREFETCH window: disabled.
[   27.282078] PCI: Bridge: 0000:00:1c.3
[   27.282081]   IO window: a000-afff
[   27.282085]   MEM window: disabled.
[   27.282089]   PREFETCH window: disabled.
[   27.282096] PCI: Bridge: 0000:00:1e.0
[   27.282099]   IO window: 9000-9fff
[   27.282104]   MEM window: cfe00000-cfefffff
[   27.282108]   PREFETCH window: disabled.
[   27.282127] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.282132] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   27.282150] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.282155] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   27.282174] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   27.282179] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   27.282197] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   27.282202] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   27.282220] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   27.282225] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   27.282236] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   27.282246] NET: Registered protocol family 2
[   27.319350] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   27.319638] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   27.320176] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   27.320443] TCP: Hash tables configured (established 131072 bind 65536)
[   27.320446] TCP reno registered
[   27.331402] checking if image is initramfs... it is
[   27.782033] Switched to high resolution mode on CPU 0
[   27.782162] Switched to high resolution mode on CPU 1
[   27.902010] Freeing initrd memory: 7712k freed
[   27.902866] audit: initializing netlink socket (disabled)
[   27.902879] audit(1222502269.280:1): initialized
[   27.903070] highmem bounce pool size: 64 pages
[   27.905343] VFS: Disk quotas dquot_6.5.1
[   27.905437] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.905578] io scheduler noop registered
[   27.905581] io scheduler anticipatory registered
[   27.905583] io scheduler deadline registered
[   27.905594] io scheduler cfq registered (default)
[   27.905683] Boot video device is 0000:06:00.0
[   27.905689] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   27.905819] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   27.905858] assign_interrupt_mode Found MSI capability
[   27.905891] Allocate Port Service[0000:00:01.0:pcie00]
[   27.905981] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   27.906023] assign_interrupt_mode Found MSI capability
[   27.906057] Allocate Port Service[0000:00:1c.0:pcie00]
[   27.906098] Allocate Port Service[0000:00:1c.0:pcie02]
[   27.906190] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   27.906232] assign_interrupt_mode Found MSI capability
[   27.906266] Allocate Port Service[0000:00:1c.1:pcie00]
[   27.906310] Allocate Port Service[0000:00:1c.1:pcie02]
[   27.906402] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   27.906444] assign_interrupt_mode Found MSI capability
[   27.906478] Allocate Port Service[0000:00:1c.2:pcie00]
[   27.906520] Allocate Port Service[0000:00:1c.2:pcie02]
[   27.906612] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   27.906663] assign_interrupt_mode Found MSI capability
[   27.906697] Allocate Port Service[0000:00:1c.3:pcie00]
[   27.906740] Allocate Port Service[0000:00:1c.3:pcie02]
[   27.907041] isapnp: Scanning for PnP cards...
[   28.257818] isapnp: No Plug & Play device found
[   28.292456] Real Time Clock Driver v1.12ac
[   28.292569] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.292694] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.293418] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.294341] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.294414] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   28.294594] PNP: No PS/2 controller found. Probing ports directly.
[   28.297303] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.297310] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.316849] mice: PS/2 mouse device common for all mice
[   28.316993] EISA: Probing bus 0 at eisa.0
[   28.317017] Cannot allocate resource for EISA slot 7
[   28.317019] Cannot allocate resource for EISA slot 8
[   28.317021] EISA: Detected 0 cards.
[   28.317024] cpuidle: using governor ladder
[   28.317026] cpuidle: using governor menu
[   28.317101] NET: Registered protocol family 1
[   28.317129] Using IPI No-Shortcut mode
[   28.317157] registered taskstats version 1
[   28.317257]   Magic number: 8:231:977
[   28.317265]   hash matches device ttyc4
[   28.317318] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   28.317320] EDD information not available.
[   28.317502] Freeing unused kernel memory: 368k freed
[   29.533378] fuse init (API version 7.9)
[   29.553313] ACPI: Processor [CPU1] (supports 8 throttling states)
[   30.056372] usbcore: registered new interface driver usbfs
[   30.056404] usbcore: registered new interface driver hub
[   30.064294] usbcore: registered new device driver usb
[   30.084017] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   30.084034] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   30.084040] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   30.084323] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   30.088232] ehci_hcd 0000:00:1d.7: debug port 1
[   30.088240] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   30.088252] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xcfdffc00
[   30.104167] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.104345] usb usb1: configuration #1 chosen from 1 choice
[   30.104382] hub 1-0:1.0: USB hub found
[   30.104391] hub 1-0:1.0: 8 ports detected
[   30.117176] USB Universal Host Controller Interface driver v3.0
[   30.130534] SCSI subsystem initialized
[   30.160046] libata version 3.00 loaded.
[   30.208039] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   30.208055] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   30.208060] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   30.208101] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   30.208129] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00007880
[   30.208324] usb usb2: configuration #1 chosen from 1 choice
[   30.208365] hub 2-0:1.0: USB hub found
[   30.208375] hub 2-0:1.0: 2 ports detected
[   30.262011] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   30.262016] e100: Copyright(c) 1999-2006 Intel Corporation
[   30.312804] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   30.312822] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   30.312827] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   30.312862] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   30.312896] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00007c00
[   30.313053] usb usb3: configuration #1 chosen from 1 choice
[   30.313091] hub 3-0:1.0: USB hub found
[   30.313100] hub 3-0:1.0: 2 ports detected
[   30.416506] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   30.416521] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   30.416527] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   30.416561] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   30.416594] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008000
[   30.416766] usb usb4: configuration #1 chosen from 1 choice
[   30.416806] hub 4-0:1.0: USB hub found
[   30.416815] hub 4-0:1.0: 2 ports detected
[   30.519253] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   30.519268] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   30.519274] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   30.519308] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   30.519342] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00008080
[   30.519509] usb usb5: configuration #1 chosen from 1 choice
[   30.519550] hub 5-0:1.0: USB hub found
[   30.519560] hub 5-0:1.0: 2 ports detected
[   30.623026] pata_it821x: controller in pass through mode.
[   30.623057] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 20 (level, low) -> IRQ 21
[   30.623100] PCI: Setting latency timer of device 0000:01:03.0 to 64
[   30.623667] scsi0 : pata_it821x
[   30.623742] scsi1 : pata_it821x
[   30.623787] ata1: PATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9080 irq 21
[   30.623792] ata2: PATA max UDMA/133 cmd 0x9480 ctl 0x9400 bmdma 0x9088 irq 21
[   30.870260] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   30.957947] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   30.981944] e100: eth0: e100_probe: addr 0xcfefe000, irq 21, MAC addr 00:11:d8:13:30:2e
[   30.982430] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   30.982471] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   30.982486] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   30.982516] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   30.982546] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   30.982558] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   30.987945] ata_piix 0000:00:1f.1: version 2.12
[   30.987964] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   30.988004] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   30.988824] scsi2 : ata_piix
[   30.991134] scsi3 : ata_piix
[   30.992841] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   30.992846] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   31.047226] usb 2-1: configuration #1 chosen from 1 choice
[   31.289205] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   31.310583] ata3.00: ATAPI: _NEC DV-5700A, 1.91, max UDMA/33
[   31.459213] usb 2-2: configuration #1 chosen from 1 choice
[   31.462277] usbcore: registered new interface driver hiddev
[   31.476272] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input1
[   31.482090] ata3.00: configured for UDMA/33
[   31.482134] ata4: port disabled. ignoring.
[   31.484728] scsi 2:0:0:0: CD-ROM            _NEC     DV-5700A         1.91 PQ: 0 ANSI: 5
[   31.484820] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   31.484844] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   31.484888] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   31.484957] scsi4 : ata_piix
[   31.485031] scsi5 : ata_piix
[   31.485078] ata5: SATA max UDMA/133 cmd 0x8c00 ctl 0x8880 bmdma 0x8400 irq 19
[   31.485082] ata6: SATA max UDMA/133 cmd 0x8800 ctl 0x8480 bmdma 0x8408 irq 19
[   31.496723] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1
[   31.526323] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input2
[   31.560573] input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[   31.560598] usbcore: registered new interface driver usbhid
[   31.560609] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.664344] ata5.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[   31.664349] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   31.680819] ata5.00: configured for UDMA/133
[   31.846106] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[   31.857224] Driver 'sr' needs updating - please use bus_type methods
[   31.860975] Driver 'sd' needs updating - please use bus_type methods
[   31.861723] sr0: scsi3-mmc drive: 17x/40x cd/rw xa/form2 cdda tray
[   31.861728] Uniform CD-ROM driver Revision: 3.20
[   31.861796] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   31.862233] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   31.862253] sd 4:0:0:0: [sda] Write Protect is off
[   31.862258] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.862291] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.862359] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   31.862379] sd 4:0:0:0: [sda] Write Protect is off
[   31.862383] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.862414] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.862420]  sda:<5>sr 2:0:0:0: Attached scsi generic sg0 type 5
[   31.866820] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   31.868741]  sda1 sda2 < sda5 >
[   31.887957] sd 4:0:0:0: [sda] Attached SCSI disk
[   32.145206] Attempting manual resume
[   32.145210] swsusp: Resume From Partition 8:5
[   32.145212] PM: Checking swsusp image.
[   32.145390] PM: Resume from disk failed.
[   32.185013] kjournald starting.  Commit interval 5 seconds
[   32.185021] EXT3-fs: mounted filesystem with ordered data mode.
[   40.132374] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   40.386499] Linux agpgart interface v0.102
[   40.605371] parport_pc 00:06: reported by Plug and Play ACPI
[   40.605479] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   40.824595] intel_rng: FWH not detected
[   40.866833] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.994035] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.113689] iTCO_vendor_support: vendor-support=0
[   41.176087] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   41.176194] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
[   41.176235] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   41.480914] input: Power Button (FF) as /devices/virtual/input/input4
[   41.504651] ACPI: Power Button (FF) [PWRF]
[   41.504775] input: Power Button (CM) as /devices/virtual/input/input5
[   41.532594] ACPI: Power Button (CM) [PWRB]
[   42.642186] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   42.738246] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   42.738298] [fglrx] ASYNCIO init succeed!
[   42.739516] [fglrx] PAT is enabled successfully!
[   42.740460] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   43.008931] Linux video capture interface: v2.00
[   43.066460] saa7146: register extension 'budget_av'.
[   43.066519] ACPI: PCI Interrupt 0000:01:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
[   43.066548] saa7146: found saa7146 @ mem f8876c00 (revision 1, irq 22) (0x1894,0x002c).
[   43.066557] saa7146 (0): dma buffer size 192512
[   43.066561] DVB: registering new adapter (Satelco EasyWatch DVB-C MK3)
[   43.101570] adapter failed MAC signature check
[   43.101575] encoded MAC from EEPROM was ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff
[   43.250943] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.250974] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   43.274458] lirc_dev: IR Remote Control driver registered, at major 61 
[   43.289433] 
[   43.289435] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   43.289440] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   43.363404] KNC1-0: MAC addr = 00:09:d6:6d:61:2a
[   43.443844] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[   43.571350] DVB: registering frontend 0 (Philips TDA10023 DVB-C)...
[   43.571569] budget-av: ci interface initialised.
[   43.593077] lirc_dev: lirc_register_plugin: sample_rate: 0
[   43.597065] lirc_mceusb2[3]: Philips eHome Infrared Transceiver on usb2:3
[   43.597113] usbcore: registered new interface driver lirc_mceusb2
[   44.349837] usbcore: registered new interface driver lirc_mceusb
[   44.349846] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/lirc/lirc_mceusb/lirc_mceusb.c: USB Microsoft IR Transceiver Driver v0.2
[   44.904141] lp0: using parport0 (interrupt-driven).
[   44.941951] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   45.489359] EXT3 FS on sda1, internal journal
[   45.662864] device-mapper: uevent: version 1.0.3
[   45.662901] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   46.970899] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.639866] No dock devices found.
[   51.297286] NET: Registered protocol family 10
[   51.297631] lo: Disabled Privacy Extensions
[   51.804522] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   52.610942] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   52.610948] apm: disabled - APM is not SMP safe.
[   53.001268] ppdev: user-space parallel port driver
[   53.154195] audit(1222502295.365:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5405 profile="/usr/sbin/cupsd" namespace="default"
[   53.267454] [fglrx] Reserve Block - 0 offset =  0X7ffb400 length = 0X4c00
[   53.267461] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X40000
[   53.267467] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
[   53.267471] [fglrx] Reserve Block - 3 offset =  0X7fbb000 length = 0X40000
[   53.577308] [fglrx] interrupt source 20008000 successfully enabled
[   53.577314] [fglrx] enable ID = 0x00000004
[   53.577325] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   53.577410] [fglrx] interrupt source 10000000 successfully enabled
[   53.577415] [fglrx] enable ID = 0x00000005
[   53.577423] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   64.015602] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   64.015804] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   64.019204] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   64.258031] Bluetooth: Core ver 2.11
[   64.258681] NET: Registered protocol family 31
[   64.258687] Bluetooth: HCI device and connection manager initialized
[   64.258694] Bluetooth: HCI socket layer initialized
[   64.409352] Bluetooth: L2CAP ver 2.9
[   64.409358] Bluetooth: L2CAP socket layer initialized
[   64.599104] Bluetooth: RFCOMM socket layer initialized
[   64.599121] Bluetooth: RFCOMM TTY layer initialized
[   64.599124] Bluetooth: RFCOMM ver 1.8
[   66.742380] NET: Registered protocol family 17
[   79.227485] eth0: no IPv6 routers present

lsmod
Module                  Size  Used by
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
ipv6                  267780  25 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
ac                      6916  0 
lp                     12324  0 
lirc_mceusb            12128  0 
tda10023                7300  1 
lirc_mceusb2           14980  1 
lirc_dev               15732  2 lirc_mceusb,lirc_mceusb2
snd_hda_intel         344856  2 
snd_pcm_oss            42144  0 
serio_raw               7940  0 
snd_mixer_oss          17920  1 snd_pcm_oss
psmouse                40336  0 
budget_av              20864  4 
saa7146_vv             51072  1 budget_av
videobuf_dma_sg        14980  1 saa7146_vv
videobuf_core          18820  2 saa7146_vv,videobuf_dma_sg
videodev               29440  1 saa7146_vv
v4l2_common            18304  2 saa7146_vv,videodev
v4l1_compat            15492  2 saa7146_vv,videodev
budget_core            12420  1 budget_av
dvb_core               81404  2 budget_av,budget_core
saa7146                20488  3 budget_av,saa7146_vv,budget_core
ttpci_eeprom            3456  1 budget_core
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
i2c_core               24832  4 tda10023,budget_av,budget_core,ttpci_eeprom
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
fglrx                1555468  20 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
evdev                  13056  4 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
agpgart                34760  2 fglrx,intel_agp
pcspkr                  4224  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
usbhid                 32128  0 
hid                    38784  1 usbhid
ata_piix               19588  2 
pata_acpi               8320  0 
e100                   37388  0 
mii                     6400  1 e100
pata_it821x            12420  0 
ata_generic             8324  0 
libata                159344  4 ata_piix,pata_acpi,pata_it821x,ata_generic
scsi_mod              151436  4 sg,sd_mod,sr_mod,libata
uhci_hcd               27024  0 
ehci_hcd               37900  0 
usbcore               146412  6 lirc_mceusb,lirc_mceusb2,usbhid,uhci_hcd,ehci_hcd
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 

lspci -vvv
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
	Subsystem: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: cff00000-cfffffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at cfdf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 4: I/O ports at 7880 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at 7c00 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at 8000 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin D routed to IRQ 16
	Region 4: I/O ports at 8080 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at cfdffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: cfe00000-cfefffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-

	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at 8c00 [size=8]
	Region 1: I/O ports at 8880 [size=4]
	Region 2: I/O ports at 8800 [size=8]
	Region 3: I/O ports at 8480 [size=4]
	Region 4: I/O ports at 8400 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 10
	Region 4: I/O ports at 0400 [size=32]

01:03.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
	Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (2000ns min, 2000ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: I/O ports at 9880 [size=8]
	Region 1: I/O ports at 9800 [size=4]
	Region 2: I/O ports at 9480 [size=8]
	Region 3: I/O ports at 9400 [size=4]
	Region 4: I/O ports at 9080 [size=16]
	Expansion ROM at cfe00000 [disabled] [size=128K]
	Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (2000ns min, 14000ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at cfefe000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 9c00 [size=64]
	Capabilities: <access denied>

01:0a.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
	Subsystem: KNC One Unknown device 002c
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (3750ns min, 9500ns max)
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at cfeffc00 (32-bit, non-prefetchable) [size=512]

06:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 0058
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 2: Memory at cffe0000 (64-bit, non-prefetchable) [size=64K]
	Region 4: I/O ports at e000 [size=256]
	Expansion ROM at cffc0000 [disabled] [size=128K]
	Capabilities: <access denied>

06:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (Secondary)
	Subsystem: ASUSTeK Computer Inc. Unknown device 0059
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Region 0: Memory at cfff0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>


this log is from /var/log/mythtv/mythbackend.log when i exit mythtv-setup:
2008-09-27 10:43:03.464 Using runtime prefix = /usr
2008-09-27 10:43:03.472 Empty LocalHostName.
2008-09-27 10:43:03.488 Using localhost value of xena
2008-09-27 10:43:03.508 New DB connection, total: 1
2008-09-27 10:43:03.519 Connected to database 'mythconverg' at host: localhost
2008-09-27 10:43:03.524 Closing DB connection named 'DBManager0'
2008-09-27 10:43:03.526 Connected to database 'mythconverg' at host: localhost
2008-09-27 10:43:03.529 New DB connection, total: 2
2008-09-27 10:43:03.530 Connected to database 'mythconverg' at host: localhost
2008-09-27 10:43:03.534 Current Schema Version: 1214
Starting up as the master server.
2008-09-27 10:43:03.549 New DB connection, total: 3
2008-09-27 10:43:03.568 Connected to database 'mythconverg' at host: localhost
2008-09-27 10:43:03.586 DVBChan(1:0) Error: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-09-27 10:43:05.000 Main::Registering HttpStatus Extension
2008-09-27 10:43:05.003 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-09-27 10:43:05.003 Enabled verbose msgs:  important general
2008-09-27 10:43:05.006 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QSocketDevice::writeBlock: Invalid socket


if i can/should post more information please write that down.

thanks for help and greetings from switzerland
thomi

---

### Post by thomi_ch on 2008-09-29
more information:

i have found a workaround... rebooting with switching to an older kernel and then rebooting again with the original/actual kernel.

the older is 2.6.24-19
the actual is 2.6.24-21


greetings
thomi

---

