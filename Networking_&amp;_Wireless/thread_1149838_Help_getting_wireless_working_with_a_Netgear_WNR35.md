---
title: "Help getting wireless working with a Netgear WNR3500"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by BastardNamban on 2009-05-05
Ubuntu 8.04HH, stable install for 6 months.

Dell Inspiron 9300 laptop with an Intel Pro Wireless 2915 a/b/g card that according to the card list, should work fine in Linux. 

I have a brand new Netgear WNR3500 N band wireless gigabit router, leading a slaved Westell 6100 DSL modem/router set to bridge mode, and the Netgear is working fine for wired internet, hooked up to the family XP box. I named a unique SSID, and set it for WGA2-AES option. I know my card can't pick up N band, but the router should also work with a G signal too, so that shouldn't be an issue. This should have great range, and I'm only using it in my small home.

I should have excellent reception, but I can't get anything! My SSID showed up once in the next room, with a loading bar at 75% or so, but dissapeared, and nothing happened. I have the laptop 6 feet from the router now, and can't get a signal! I find the linux wireless network manager a little confusing.

Can anyone help?:confused:

---

### Post by BastardNamban on 2009-05-05
Update-

Called Netgear for support help that comes with the router for 90 days. Surprise! They offer no support for anything Linux, not even commerical distributions like RedHat! I asked them to get at least 1 person that can help in the future.

I'm up sh*t creek, without a paddle, as it were. I need wireless on my laptop, since it's the only thing in the house that can do Japanese input- I need that to contact my previous employer in Japan for some urgent employment info- I can't apply for a job in the US till I get that info!

Can someone help? I have a feeling it's something simple I don't get. I have a feeling the so-called "Geek Squad" in my area (or any) knows jack about linux, my impression of them so far is they're mostly Windows power-users.

---

### Post by BastardNamban on 2009-05-05
anyone?

I've tried all 3 modes (54 Mbps legacy mode, 145Mbps mode, and full 300Mbps mode full N. That one time recognition was under 300Mbps option, which my card shouldn't even be able to detect.)

Still, nothing. Can someone please help? I've read all the documentation I can find, I cannot figure out why this isn't working- I think I've tried everything. I've never connected wirelessly before in my linux build- would upgrading to Jaunty make any difference? I could download a live CD with the XP box and try it..

---

### Post by BastardNamban on 2009-05-06
UPDATE: Some more detailed info. Perhaps something here will help? Cut & pasted over USB drive.
Found this at [HTML]http://www.linuxforums.org/forum/wireless-internet/137532-wireless-setup-start-here.html[/HTML].

```
shogun@Valhalla:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV41.8 [GeForce Go 6800] [10de:00c8] (rev a2)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b3)
03:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 08)
03:01.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 17)
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG Network Connection [8086:4223] (rev 05)
shogun@Valhalla:~$ 

```

and this:
```
shogun@Valhalla:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:13:11 UTC 2009 (Ubuntu 2.6.24-23.48-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffda000 (usable)
[    0.000000]  BIOS-e820: 000000003ffda000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262106) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262106
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262106
[    0.000000] On node 0 totalpages: 262106
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32475 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FC9B0 checksum 0
[    0.000000] ACPI: RSDP 000FC9B0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 3FFDA7D3, 0040 (r1 DELL    CPi R   27D50615 ASL        61)
[    0.000000] ACPI: FACP 3FFDB400, 0074 (r1 DELL    CPi R   27D50615 ASL        61)
[    0.000000] ACPI: DSDT 3FFDC000, 2A1A (r1 INT430 SYSFexxx     1001 MSFT  100000E)
[    0.000000] ACPI: FACS 3FFEA800, 0040
[    0.000000] ACPI: APIC 3FFDBC00, 0068 (r1 DELL    CPi R   27D50615 ASL        47)
[    0.000000] ACPI: MCFG 3FFDBBC0, 003E (r16 DELL    CPi R   27D50615 ASL        61)
[    0.000000] ACPI: BOOT 3FFDB7C0, 0028 (r1 DELL    CPi R   27D50615 ASL        61)
[    0.000000] ACPI: SSDT 3FFDABE6, 0280 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
[    0.000000] ACPI: SSDT 3FFDAA0E, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] ACPI: SSDT 3FFDA813, 01FB (r1  PmRef    CpuPm     3000 INTL 20030522)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
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
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260059
[    0.000000] Kernel command line: root=UUID=e4ab4aee-f8d0-4324-95ee-b149bbf30924 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.004 MHz processor.
[    3.900951] Console: colour VGA+ 80x25
[    3.900955] console [tty0] enabled
[    3.901268] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    3.901645] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    3.927896] Memory: 1027268k/1048424k available (2179k kernel code, 20448k reserved, 1008k data, 368k init, 130920k highmem)
[    3.927903] virtual kernel memory layout:
[    3.927904]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    3.927905]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    3.927906]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    3.927907]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    3.927909]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[    3.927910]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[    3.927911]       .text : 0xc0100000 - 0xc0320c08   (2179 kB)
[    3.927914] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    3.927946] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    4.007927] Calibrating delay using timer specific routine.. 3994.17 BogoMIPS (lpj=7988356)
[    4.007949] Security Framework initialized
[    4.007955] SELinux:  Disabled at boot.
[    4.007968] AppArmor: AppArmor initialized
[    4.007972] Failure registering capabilities with primary security module.
[    4.007979] Mount-cache hash table entries: 512
[    4.008084] Initializing cgroup subsys ns
[    4.008088] Initializing cgroup subsys cpuacct
[    4.008098] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000 00000000
[    4.008107] CPU: L1 I cache: 32K, L1 D cache: 32K
[    4.008109] CPU: L2 cache: 2048K
[    4.008112] CPU: After all inits, caps: afe9fbff 00100000 00000000 00042040 00000180 00000000 00000000 00000000
[    4.008119] Compat vDSO mapped to ffffe000.
[    4.008129] Checking 'hlt' instruction... OK.
[    4.024255] SMP alternatives: switching to UP code
[    4.025868] Freeing SMP alternatives: 11k freed
[    4.025962] Early unpacking initramfs... done
[    4.331798] ACPI: Core revision 20070126
[    4.331843] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    4.335207] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
[    4.335223] Total of 1 processors activated (3994.17 BogoMIPS).
[    4.335381] ENABLING IO-APIC IRQs
[    4.335565] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    4.479732] Brought up 1 CPUs
[    4.479757] CPU0 attaching sched-domain:
[    4.479759]  domain 0: span 01
[    4.479761]   groups: 01
[    4.479897] net_namespace: 64 bytes
[    4.479907] Booting paravirtualized kernel on bare hardware
[    4.480307] Time:  3:59:19  Date: 05/06/09
[    4.480327] NET: Registered protocol family 16
[    4.480489] EISA bus registered
[    4.480513] ACPI: bus type pci registered
[    4.518112] PCI: PCI BIOS revision 2.10 entry at 0xfbaae, last bus=10
[    4.518114] PCI: Using configuration type 1
[    4.518126] Setting up standard PCI resources
[    4.522150] ACPI: EC: Look up EC in DSDT
[    4.525607] ACPI: Interpreter enabled
[    4.525610] ACPI: (supports S0 S3 S4 S5)
[    4.525620] ACPI: Using IOAPIC for interrupt routing
[    4.535641] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    4.536257] Force enabled HPET at base address 0xfed00000
[    4.536264] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    4.536268] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    4.536910] PCI: Transparent bridge - 0000:00:1e.0
[    4.536973] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    4.537340] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    4.537412] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    4.542264] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    4.542350] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    4.542434] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    4.542517] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[    4.542590] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    4.542665] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    4.542741] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    4.542841] Linux Plug and Play Support v0.97 (c) Adam Belay
[    4.542867] pnp: PnP ACPI init
[    4.542872] ACPI: bus type pnp registered
[    4.554052] pnpacpi: exceeded the max number of mem resources: 12
[    4.563802] pnp: PnP ACPI: found 11 devices
[    4.563804] ACPI: ACPI bus type pnp unregistered
[    4.563807] PnPBIOS: Disabled by ACPI PNP
[    4.563981] PCI: Using ACPI for IRQ routing
[    4.563984] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    4.603638] NET: Registered protocol family 8
[    4.603640] NET: Registered protocol family 20
[    4.603776] hpet clockevent registered
[    4.603782] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    4.603786] hpet0: 3 64-bit timers, 14318180 Hz
[    4.604819] AppArmor: AppArmor Filesystem Enabled
[    4.607631] Time: tsc clocksource has been installed.
[    4.615655] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    4.615658] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    4.615661] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    4.615663] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    4.615666] system 00:00: iomem range 0x100000-0x3ffd9fff could not be reserved
[    4.615668] system 00:00: iomem range 0x3ffda000-0x3fffffff could not be reserved
[    4.615671] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
[    4.615674] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
[    4.615677] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    4.615679] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    4.615682] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
[    4.615685] system 00:00: iomem range 0xf0000000-0xf0003fff could not be reserved
[    4.615690] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    4.615693] system 00:02: ioport range 0x1000-0x1005 has been reserved
[    4.615695] system 00:02: ioport range 0x1008-0x100f has been reserved
[    4.615700] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    4.615702] system 00:03: ioport range 0x1006-0x1007 has been reserved
[    4.615705] system 00:03: ioport range 0x100a-0x1059 could not be reserved
[    4.615708] system 00:03: ioport range 0x1060-0x107f has been reserved
[    4.615710] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    4.615712] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    4.615715] system 00:03: ioport range 0x10e0-0x10ff has been reserved
[    4.615721] system 00:08: ioport range 0x900-0x90f has been reserved
[    4.615723] system 00:08: ioport range 0x910-0x91f has been reserved
[    4.615726] system 00:08: ioport range 0x920-0x92f has been reserved
[    4.615728] system 00:08: ioport range 0x930-0x93f has been reserved
[    4.615730] system 00:08: ioport range 0x940-0x97f has been reserved
[    4.646054] PCI: Bridge: 0000:00:01.0
[    4.646055]   IO window: disabled.
[    4.646058]   MEM window: dd000000-dfefffff
[    4.646061]   PREFETCH window: c0000000-cfffffff
[    4.646071] PCI: Bus 4, cardbus bridge: 0000:03:01.0
[    4.646073]   IO window: 00001400-000014ff
[    4.646077]   IO window: 00001800-000018ff
[    4.646082]   PREFETCH window: 50000000-53ffffff
[    4.646086]   MEM window: 54000000-57ffffff
[    4.646090] PCI: Bridge: 0000:00:1e.0
[    4.646091]   IO window: disabled.
[    4.646096]   MEM window: dcf00000-dcffffff
[    4.646100]   PREFETCH window: disabled.
[    4.646115] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    4.646119] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    4.646131] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    4.646145] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
[    4.646149] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
[    4.646162] NET: Registered protocol family 2
[    4.683642] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    4.683830] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    4.684503] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    4.684899] TCP: Hash tables configured (established 131072 bind 65536)
[    4.684902] TCP reno registered
[    4.695728] checking if image is initramfs... it is
[    5.107382] Switched to high resolution mode on CPU 0
[    5.294871] Freeing initrd memory: 7306k freed
[    5.295069] Simple Boot Flag at 0x79 set to 0x1
[    5.295446] audit: initializing netlink socket (disabled)
[    5.295460] audit(1241582359.264:1): initialized
[    5.295614] highmem bounce pool size: 64 pages
[    5.297245] VFS: Disk quotas dquot_6.5.1
[    5.297309] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.297434] io scheduler noop registered
[    5.297436] io scheduler anticipatory registered
[    5.297438] io scheduler deadline registered
[    5.297447] io scheduler cfq registered (default)
[    5.297551] Boot video device is 0000:01:00.0
[    5.297644] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    5.297670] assign_interrupt_mode Found MSI capability
[    5.297695] Allocate Port Service[0000:00:01.0:pcie00]
[    5.297901] isapnp: Scanning for PnP cards...
[    5.651741] isapnp: No Plug & Play device found
[    5.674560] Real Time Clock Driver v1.12ac
[    5.674658] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    5.675155] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 18
[    5.675163] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[    5.675700] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    5.675761] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    5.675842] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    5.680736] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.680740] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.683101] mice: PS/2 mouse device common for all mice
[    5.683195] EISA: Probing bus 0 at eisa.0
[    5.683202] Cannot allocate resource for EISA slot 1
[    5.683228] EISA: Detected 0 cards.
[    5.683231] cpuidle: using governor ladder
[    5.683233] cpuidle: using governor menu
[    5.683315] NET: Registered protocol family 1
[    5.683339] Using IPI No-Shortcut mode
[    5.683367] registered taskstats version 1
[    5.683464]   Magic number: 9:201:967
[    5.683470]   hash matches device ttyb8
[    5.683548] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.683550] EDD information not available.
[    5.683735] Freeing unused kernel memory: 368k freed
[    5.683758] Write protecting the kernel read-only data: 806k
[    5.687641] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    6.856631] fuse init (API version 7.9)
[    6.872486] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    6.872492] ACPI: Processor [CPU0] (supports 8 throttling states)
[    6.872503] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[    6.875813] ACPI: Thermal Zone [THM] (35 C)
[    7.311586] usbcore: registered new interface driver usbfs
[    7.311609] usbcore: registered new interface driver hub
[    7.319525] usbcore: registered new device driver usb
[    7.327443] USB Universal Host Controller Interface driver v3.0
[    7.327500] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    7.327512] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    7.327516] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    7.327842] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    7.327876] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    7.327994] usb usb1: configuration #1 chosen from 1 choice
[    7.328015] hub 1-0:1.0: USB hub found
[    7.328019] hub 1-0:1.0: 2 ports detected
[    7.430028] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
[    7.430042] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    7.430046] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    7.430066] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    7.430098] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000bf60
[    7.430197] usb usb2: configuration #1 chosen from 1 choice
[    7.430219] hub 2-0:1.0: USB hub found
[    7.430224] hub 2-0:1.0: 2 ports detected
[    7.449292] SCSI subsystem initialized
[    7.481780] libata version 3.00 loaded.
[    7.533948] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[    7.533961] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    7.533966] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    7.533987] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    7.534018] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000bf40
[    7.534112] usb usb3: configuration #1 chosen from 1 choice
[    7.534131] hub 3-0:1.0: USB hub found
[    7.534136] hub 3-0:1.0: 2 ports detected
[    7.637884] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
[    7.637897] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    7.637901] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    7.637921] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    7.637953] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000bf20
[    7.638047] usb usb4: configuration #1 chosen from 1 choice
[    7.638067] hub 4-0:1.0: USB hub found
[    7.638071] hub 4-0:1.0: 2 ports detected
[    7.669790] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    7.741977] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
[    7.741991] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    7.741995] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    7.742015] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    7.745930] ehci_hcd 0000:00:1d.7: debug port 1
[    7.745936] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    7.745941] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    7.797710] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.797812] usb usb5: configuration #1 chosen from 1 choice
[    7.797834] hub 5-0:1.0: USB hub found
[    7.797839] hub 5-0:1.0: 8 ports detected
[    7.903174] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 19
[    7.955891] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dcffc800-dcffcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    7.974837] ata_piix 0000:00:1f.2: version 2.12
[    7.974844] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    8.101512] Clocksource tsc unstable (delta = -13787245029 ns)
[    8.105592] Time: hpet clocksource has been installed.
[    8.105820] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
[    8.105852] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    8.105991] scsi0 : ata_piix
[    8.106132] scsi1 : ata_piix
[    8.106737] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    8.106740] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    8.109212] usb 1-2: device not accepting address 2, error -71
[    8.112511] ata1.00: ATA-6: HTS726060M9AT00, MH4OA6EA, max UDMA/100
[    8.112514] ata1.00: 117210240 sectors, multi 8: LBA48 
[    8.112517] ata1.00: applying bridge limits
[    8.114195] ata1.00: configured for UDMA/100
[    8.122951] ata2.00: ATAPI: SONY DVD+/-RW DW-D56A, PDS7, max UDMA/33
[    8.124020] usb 1-2: new low speed USB device using uhci_hcd and address 4
[    8.128013] ata2.00: configured for UDMA/33
[    8.128112] scsi 0:0:0:0: Direct-Access     ATA      HTS726060M9AT00  MH4O PQ: 0 ANSI: 5
[    8.128640] scsi 1:0:0:0: CD-ROM            SONY     DVD+-RW DW-D56A  PDS7 PQ: 0 ANSI: 5
[    8.130490] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[    8.132240] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    8.132247] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    8.132253] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    8.136278] usb 1-2: configuration #1 chosen from 1 choice
[    8.144035] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    8.144055] b44.c:v2.0
[    8.150011] usbcore: registered new interface driver hiddev
[    8.151904] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:dd:68:16
[    8.154123] input: Kensington Kensington PocketMouse Pro as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
[    8.167508] input,hidraw0: USB HID v1.10 Mouse [Kensington Kensington PocketMouse Pro] on usb-0000:00:1d.0-2
[    8.167526] usbcore: registered new interface driver usbhid
[    8.167529] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    8.180350] Driver 'sd' needs updating - please use bus_type methods
[    8.180417] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    8.180428] sd 0:0:0:0: [sda] Write Protect is off
[    8.180430] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.180443] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.180483] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    8.180491] sd 0:0:0:0: [sda] Write Protect is off
[    8.180493] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.180506] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.180509]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    8.207235] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[424fc00029b80101]
[    8.209782]  sda1 sda2 < sda5 >
[    8.210076] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.215803] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.215818] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    8.219204] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    8.219207] Uniform CD-ROM driver Revision: 3.20
[    8.219245] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    8.295015] Attempting manual resume
[    8.295019] swsusp: Resume From Partition 8:5
[    8.295020] PM: Checking swsusp image.
[    8.295139] PM: Resume from disk failed.
[    8.307950] kjournald starting.  Commit interval 5 seconds
[    8.307958] EXT3-fs: mounted filesystem with ordered data mode.
[   10.101156] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.155227] Linux agpgart interface v0.102
[   10.241106] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.365519] ACPI: AC Adapter [AC] (off-line)
[   10.497676] input: Lid Switch as /devices/virtual/input/input3
[   10.498355] ACPI: Lid Switch [LID]
[   10.499072] input: Power Button (CM) as /devices/virtual/input/input4
[   10.508851] ACPI: Power Button (CM) [PBTN]
[   10.508908] input: Sleep Button (CM) as /devices/virtual/input/input5
[   10.524845] ACPI: Sleep Button (CM) [SBTN]
[   10.860047] ACPI: Battery Slot [BAT0] (battery present)
[   11.392359] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input6
[   11.404297] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   11.789506] nvidia: module license 'NVIDIA' taints kernel.
[   12.536160] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0189]
[   12.664280] Yenta: ISA IRQ mask 0x0cb8, PCI irq 17
[   12.664284] Socket status: 30000006
[   12.664287] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   12.664291] pcmcia: parent PCI bridge Memory window: 0xdcf00000 - 0xdcffffff
[   12.751507] iTCO_vendor_support: vendor-support=0
[   12.831167] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   12.831241] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   12.831280] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.852226] ieee80211_crypt: registered algorithm 'NULL'
[   12.895363] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   12.895366] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   13.011335] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   13.110537] intel_rng: FWH not detected
[   13.176819] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.176829] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   13.176946] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   13.236316] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   13.236320] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.236395] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 18
[   13.247534] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   13.264506] sdhci: Secure Digital Host Controller Interface driver
[   13.264509] sdhci: Copyright(c) Pierre Ossman
[   13.409339] input: PS/2 Mouse as /devices/virtual/input/input8
[   13.459835] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   13.485571] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.456118] ipw2200: Radio Frequency Kill Switch is On:
[   14.456120] Kill switch must be turned off for wireless networking to work.
[   14.502420] cs: IO port probe 0x100-0x3af: clean.
[   14.504092] cs: IO port probe 0x3e0-0x4ff: clean.
[   14.504794] cs: IO port probe 0x820-0x8ff: clean.
[   14.505376] cs: IO port probe 0xc00-0xcf7: clean.
[   14.506098] cs: IO port probe 0xa00-0xaff: clean.
[   14.552011] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   14.552037] sdhci: SDHCI controller found at 0000:03:01.2 [1180:0822] (rev 17)
[   14.552058] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 18
[   14.552109] mmc0: SDHCI at 0xdcffc700 irq 18 DMA
[   14.552150] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
[   14.552162] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   14.626446] intel8x0_measure_ac97_clock: measured 55465 usecs
[   14.626450] intel8x0: clocking to 48000
[   14.727188] lp: driver loaded but no devices found
[   14.877534] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k
[   14.895294] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   14.895496] EXT3 FS on sda1, internal journal
[   15.194474] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.368861] No dock devices found.
[   15.973173] apm: BIOS not found.
[   16.028117] ppdev: user-space parallel port driver
[   16.042255] audit(1241582395.936:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4919 profile="/usr/sbin/cupsd" namespace="default"
[   20.095082] Marking TSC unstable due to: cpufreq changes.
[   20.917364] Bluetooth: Core ver 2.11
[   20.917885] NET: Registered protocol family 31
[   20.917888] Bluetooth: HCI device and connection manager initialized
[   20.917892] Bluetooth: HCI socket layer initialized
[   16.807800] Bluetooth: L2CAP ver 2.9
[   16.807804] Bluetooth: L2CAP socket layer initialized
[   25.219186] Bluetooth: RFCOMM socket layer initialized
[   25.219406] Bluetooth: RFCOMM TTY layer initialized
[   25.219410] Bluetooth: RFCOMM ver 1.8
[   57.426790] NET: Registered protocol family 10
[   57.427538] lo: Disabled Privacy Extensions
[   57.429440] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.430077] ADDRCONF(NETDEV_UP): eth1: link is not ready
shogun@Valhalla:~$ 
```

Finally, found this: [HTML]http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1847&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go![/HTML], after understanding that the wireless cards themselves need drivers that work in Linux (gee, don't know HOW I missed that one... too much stuff to learn just to setup wireless! forgive me!)

Could that intel sponsored driver for linux be what I need to install?

---

### Post by chili555 on 2009-05-06
> ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)You already have the driver you need, *ipw2200*. Here is the whole problem:> [   14.456118] ipw2200: Radio Frequency Kill Switch is On:
[   14.456120] Kill switch must be turned off for wireless networking to work.The switch or key combination that turns the wireless radio on and off has become nudged to 'off.' Please find it and nudge it to 'on.'

---

### Post by BastardNamban on 2009-05-07
Yeah, I noticed that too. Which is why I checked the network manager. It says that wireless is on, which is why I posted this still confused!

Back when I had XP on this, before Ubuntu, I hit a key combo that worked in the Inspiron 9300 wireless settings to turn on/off the wireless card. I have tried that, but nothing noticeably changes like it did with XP, when the wireless light when on or off on the icon panel above my keyboard.

So linux is telling me 2 different things, as far as I can tell. the network manager icon both in the panel bar and under system settings says wireless is on, but that bit from terminal above says it's off. Thing is, even hitting the old key combo doesn't get me any signal.

I'm thinking of simplifying things by ordering a new N band card and router combo from Newegg anyway, hopefully simplifying things.

Looking at this: [HTML]http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.191919[/HTML]

From what I understand, that router uses a Ralink Driver thats available in linux, 2800 series of some kind in my searches, but I haven't been able to confirm if it is indeed available yet. Anyone know?

---

### Post by chili555 on 2009-05-08
The Ralink drivers, downloadable from their website are troublesome. I'd hate to trade one issue for another, perhaps worse. Please do:```
sudo ifconfig eth1 down
sudo rmmod -f ipw2200
sudo modprobe ipw2200 led=1 bt_coexist=1
sudo ifconfig eth1 up
```Is there any improvement?

---

