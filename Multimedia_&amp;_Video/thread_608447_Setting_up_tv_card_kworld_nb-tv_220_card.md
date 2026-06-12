---
title: "Setting up tv card kworld nb-tv 220 card"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by yinglcs2 on 2007-11-10
Hi,

I am trying to setup my kworld nb-tv 220 card on ubuntu 7.10.

Here is my output of my 'dmesg' command. Can you please tell me how to get my card to work?

# dmesg
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfed0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfed0000 - 00000000bfedf000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfedf000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] 2174MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6820
[    0.000000] Entering add_active_range(0, 0, 786128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   786128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   786128
[    0.000000] On node 0 totalpages: 786128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4349 pages used for memmap
[    0.000000]   HighMem zone: 552403 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F67E0 checksum 0
[    0.000000] ACPI: RSDP 000F67E0, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT BFED1599, 0084 (r1 LENOVO TP-79        2060  LTP        0)
[    0.000000] ACPI: FACP BFED1700, 00F4 (r3 LENOVO TP-79        2060 LNVO        1)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20070126]
[    0.000000] ACPI: DSDT BFED1B32, D29A (r1 LENOVO TP-79        2060 MSFT  100000E)
[    0.000000] ACPI: FACS BFEF4000, 0040
[    0.000000] ACPI: SSDT BFED18B4, 027E (r1 LENOVO TP-79        2060 MSFT  100000E)
[    0.000000] ACPI: ECDT BFEDEDCC, 0052 (r1 LENOVO TP-79        2060 LNVO        1)
[    0.000000] ACPI: TCPA BFEDEE1E, 0032 (r2 LENOVO TP-79        2060 LNVO        1)
[    0.000000] ACPI: APIC BFEDEE50, 0068 (r1 LENOVO TP-79        2060 LNVO        1)
[    0.000000] ACPI: MCFG BFEDEEB8, 003C (r1 LENOVO TP-79        2060 LNVO        1)
[    0.000000] ACPI: HPET BFEDEEF4, 0038 (r1 LENOVO TP-79        2060 LNVO        1)
[    0.000000] ACPI: BOOT BFEDEFD8, 0028 (r1 LENOVO TP-79        2060  LTP        1)
[    0.000000] ACPI: SSDT BFEF2697, 025F (r1 LENOVO TP-79        2060 INTL 20050513)
[    0.000000] ACPI: SSDT BFEF28F6, 00A6 (r1 LENOVO TP-79        2060 INTL 20050513)
[    0.000000] ACPI: SSDT BFEF299C, 04F7 (r1 LENOVO TP-79        2060 INTL 20050513)
[    0.000000] ACPI: SSDT BFEF2E93, 01D8 (r1 LENOVO TP-79        2060 INTL 20050513)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
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
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:30000000)
[    0.000000] Built 1 zonelists.  Total pages: 779987
[    0.000000] Kernel command line: root=UUID=ee7b84cb-dbae-469a-a616-22e965ed56cc ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.080 MHz processor.
[   14.069591] Console: colour VGA+ 80x25
[   14.069834] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.070152] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.250797] Memory: 3106692k/3144512k available (2015k kernel code, 36452k reserved, 916k data, 364k init, 2227008k highmem)
[   14.250806] virtual kernel memory layout:
[   14.250807]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   14.250808]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.250809]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.250811]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.250812]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   14.250813]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   14.250814]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   14.250817] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.250852] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.250981] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.250986] hpet0: 3 64-bit timers, 14318180 Hz
[   14.331961] Calibrating delay using timer specific routine.. 3994.27 BogoMIPS (lpj=7988540)
[   14.331983] Security Framework v1.0.0 initialized
[   14.331991] SELinux:  Disabled at boot.
[   14.332003] Mount-cache hash table entries: 512
[   14.332121] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   14.332128] monitor/mwait feature present.
[   14.332130] using mwait in idle threads.
[   14.332134] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.332136] CPU: L2 cache: 2048K
[   14.332139] CPU: Physical Processor ID: 0
[   14.332140] CPU: Processor Core ID: 0
[   14.332142] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[   14.332150] Compat vDSO mapped to ffffe000.
[   14.332162] Checking 'hlt' instruction... OK.
[   14.348065] SMP alternatives: switching to UP code
[   14.348490] Early unpacking initramfs... done
[   14.641547] ACPI: Core revision 20070126
[   14.641637] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.669103] CPU0: Intel(R) Core(TM) Duo CPU      T2500  @ 2.00GHz stepping 0c
[   14.669118] SMP alternatives: switching to SMP code
[   14.669222] Booting processor 1/1 eip 3000
[   14.679700] Initializing CPU#1
[   14.760003] Calibrating delay using timer specific routine.. 3990.04 BogoMIPS (lpj=7980092)
[   14.760009] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   14.760013] monitor/mwait feature present.
[   14.760016] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.760018] CPU: L2 cache: 2048K
[   14.760020] CPU: Physical Processor ID: 0
[   14.760021] CPU: Processor Core ID: 1
[   14.760023] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[   14.760279] CPU1: Intel(R) Core(TM) Duo CPU      T2500  @ 2.00GHz stepping 0c
[   14.760302] Total of 2 processors activated (7984.31 BogoMIPS).
[   14.760497] ENABLING IO-APIC IRQs
[   14.760700] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.907720] checking TSC synchronization [CPU#0 -> CPU#1]:
[   14.927715] Measured 568344 cycles TSC warp between CPUs, turning off TSC clock.
[    0.528000] Marking TSC unstable due to: check_tsc_sync_source failed.
[    0.532000] Brought up 2 CPUs
[    0.616000] migration_cost=4000
[    0.616000] Booting paravirtualized kernel on bare hardware
[    0.616000] Time: 22:27:10  Date: 10/09/107
[    0.616000] NET: Registered protocol family 16
[    0.616000] EISA bus registered
[    0.616000] ACPI: bus type pci registered
[    0.616000] PCI: PCI BIOS revision 2.10 entry at 0xfd84b, last bus=24
[    0.616000] PCI: Using configuration type 1
[    0.616000] Setting up standard PCI resources
[    0.620000] ACPI: EC: Found ECDT
[    0.628000] ACPI: Interpreter enabled
[    0.628000] ACPI: (supports S0 S3 S4 S5)
[    0.628000] ACPI: Using IOAPIC for interrupt routing
[    0.636000] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[    0.636000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.636000] PCI: Probing PCI hardware (bus 00)
[    0.636000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.636000] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.636000] PCI: Transparent bridge - 0000:00:1e.0
[    0.636000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.636000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.636000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.640000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.640000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.640000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.640000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.640000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.640000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.640000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.640000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.640000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.640000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.644000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.644000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.644000] ACPI: Power Resource [PUBS] (on)
[    0.644000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.644000] pnp: PnP ACPI init
[    0.644000] ACPI: bus type pnp registered
[    0.648000] pnp: PnP ACPI: found 12 devices
[    0.648000] ACPI: ACPI bus type pnp unregistered
[    0.648000] PnPBIOS: Disabled by ACPI PNP
[    0.648000] PCI: Using ACPI for IRQ routing
[    0.648000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.700000] NET: Registered protocol family 8
[    0.700000] NET: Registered protocol family 20
[    0.700000] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.700000] pnp: 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.700000] pnp: 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.700000] pnp: 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.700000] pnp: 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.700000] pnp: 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.700000] pnp: 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[    0.700000] pnp: 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.704000] Time: hpet clocksource has been installed.
[    0.704000] Switched to high resolution mode on CPU 0
[    0.704000] Switched to high resolution mode on CPU 1
[    0.728000] PCI: Bridge: 0000:00:01.0
[    0.728000]   IO window: 2000-2fff
[    0.728000]   MEM window: ee100000-ee1fffff
[    0.728000]   PREFETCH window: d8000000-dfffffff
[    0.728000] PCI: Bridge: 0000:00:1c.0
[    0.728000]   IO window: 3000-3fff
[    0.728000]   MEM window: ee000000-ee0fffff
[    0.728000]   PREFETCH window: disabled.
[    0.728000] PCI: Bridge: 0000:00:1c.1
[    0.728000]   IO window: 4000-5fff
[    0.728000]   MEM window: ec000000-edffffff
[    0.728000]   PREFETCH window: e4000000-e40fffff
[    0.728000] PCI: Bridge: 0000:00:1c.2
[    0.728000]   IO window: 6000-7fff
[    0.728000]   MEM window: e8000000-e9ffffff
[    0.728000]   PREFETCH window: e4100000-e41fffff
[    0.728000] PCI: Bridge: 0000:00:1c.3
[    0.728000]   IO window: 8000-9fff
[    0.728000]   MEM window: ea000000-ebffffff
[    0.728000]   PREFETCH window: e4200000-e42fffff
[    0.728000] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[    0.728000]   IO window: 0000a000-0000a0ff
[    0.728000]   IO window: 0000a400-0000a4ff
[    0.728000]   PREFETCH window: e0000000-e3ffffff
[    0.728000]   MEM window: c4000000-c7ffffff
[    0.728000] PCI: Bridge: 0000:00:1e.0
[    0.728000]   IO window: a000-dfff
[    0.728000]   MEM window: e4300000-e7ffffff
[    0.728000]   PREFETCH window: e0000000-e3ffffff
[    0.728000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.728000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.728000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 17
[    0.728000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.728000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 18
[    0.728000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.728000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 19
[    0.728000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.728000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 20
[    0.728000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.728000] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[    0.728000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.728000] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.728000] NET: Registered protocol family 2
[    0.772000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.772000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.772000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.772000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.772000] TCP reno registered
[    0.788000] checking if image is initramfs... it is
[    1.368000] Freeing initrd memory: 7113k freed
[    1.368000] Simple Boot Flag at 0x35 set to 0x1
[    1.368000] audit: initializing netlink socket (disabled)
[    1.368000] audit(1194647229.204:1): initialized
[    1.368000] highmem bounce pool size: 64 pages
[    1.372000] VFS: Disk quotas dquot_6.5.1
[    1.372000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.372000] io scheduler noop registered
[    1.372000] io scheduler anticipatory registered
[    1.372000] io scheduler deadline registered
[    1.372000] io scheduler cfq registered (default)
[    1.372000] Boot video device is 0000:01:00.0
[    1.372000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    1.372000] assign_interrupt_mode Found MSI capability
[    1.372000] Allocate Port Service[0000:00:01.0:pcie00]
[    1.372000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.372000] assign_interrupt_mode Found MSI capability
[    1.372000] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.372000] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.372000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.372000] assign_interrupt_mode Found MSI capability
[    1.372000] Allocate Port Service[0000:00:1c.1:pcie00]
[    1.372000] Allocate Port Service[0000:00:1c.1:pcie02]
[    1.372000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    1.372000] assign_interrupt_mode Found MSI capability
[    1.372000] Allocate Port Service[0000:00:1c.2:pcie00]
[    1.372000] Allocate Port Service[0000:00:1c.2:pcie02]
[    1.372000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    1.372000] assign_interrupt_mode Found MSI capability
[    1.372000] Allocate Port Service[0000:00:1c.3:pcie00]
[    1.372000] Allocate Port Service[0000:00:1c.3:pcie02]
[    1.372000] isapnp: Scanning for PnP cards...
[    1.728000] isapnp: No Plug & Play device found
[    1.748000] Real Time Clock Driver v1.12ac
[    1.748000] hpet_resources: 0xfed00000 is busy
[    1.748000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.748000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.748000] input: Macintosh mouse button emulation as /class/input/input0
[    1.748000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.756000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.756000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.756000] mice: PS/2 mouse device common for all mice
[    1.756000] EISA: Probing bus 0 at eisa.0
[    1.756000] Cannot allocate resource for EISA slot 1
[    1.756000] Cannot allocate resource for EISA slot 2
[    1.756000] Cannot allocate resource for EISA slot 3
[    1.756000] Cannot allocate resource for EISA slot 4
[    1.756000] Cannot allocate resource for EISA slot 5
[    1.756000] Cannot allocate resource for EISA slot 6
[    1.756000] Cannot allocate resource for EISA slot 7
[    1.756000] Cannot allocate resource for EISA slot 8
[    1.756000] EISA: Detected 0 cards.
[    1.756000] TCP cubic registered
[    1.756000] NET: Registered protocol family 1
[    1.756000] Using IPI No-Shortcut mode
[    1.756000]   Magic number: 15:965:501
[    1.756000] Freeing unused kernel memory: 364k freed
[    1.764000] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.932000] AppArmor: AppArmor initialized<5>audit(1194647230.704:2):  type=1505 info="AppArmor initialized" pid=1239
[    2.936000] fuse init (API version 7.8)
[    2.940000] Failure registering capabilities with primary security module.
[    2.972000] ACPI: SSDT BFEF1D36, 0282 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[    2.972000] ACPI: SSDT BFEF203D, 065A (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[    2.972000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.972000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.972000] ACPI: SSDT BFEF1C6E, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[    2.976000] ACPI: SSDT BFEF1FB8, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[    2.976000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.976000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.976000] ACPI: Thermal Zone [THM0] (79 C)
[    2.976000] ACPI: Thermal Zone [THM1] (76 C)
[    3.332000] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[    3.332000] Copyright (c) 1999-2006 Intel Corporation.
[    3.332000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.332000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    3.364000] usbcore: registered new interface driver usbfs
[    3.364000] usbcore: registered new interface driver hub
[    3.364000] usbcore: registered new device driver usb
[    3.364000] USB Universal Host Controller Interface driver v3.0
[    3.396000] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:15:58:7d:61:d4
[    3.444000] SCSI subsystem initialized
[    3.448000] libata version 2.21 loaded.
[    3.464000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.464000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.464000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.464000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.464000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.464000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[    3.464000] usb usb1: configuration #1 chosen from 1 choice
[    3.464000] hub 1-0:1.0: USB hub found
[    3.464000] hub 1-0:1.0: 2 ports detected
[    3.592000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
[    3.592000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.592000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.592000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.592000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001820
[    3.592000] usb usb2: configuration #1 chosen from 1 choice
[    3.592000] hub 2-0:1.0: USB hub found
[    3.592000] hub 2-0:1.0: 2 ports detected
[    3.696000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
[    3.696000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.696000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.696000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.696000] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001840
[    3.696000] usb usb3: configuration #1 chosen from 1 choice
[    3.696000] hub 3-0:1.0: USB hub found
[    3.696000] hub 3-0:1.0: 2 ports detected
[    4.000000] Clocksource tsc unstable (delta = -338502766 ns)
[    4.000000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 23
[    4.000000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.000000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.000000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.000000] uhci_hcd 0000:00:1d.3: irq 23, io base 0x00001860
[    4.000000] usb usb4: configuration #1 chosen from 1 choice
[    4.000000] hub 4-0:1.0: USB hub found
[    4.000000] hub 4-0:1.0: 2 ports detected
[    4.104000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
[    4.104000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.104000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.104000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.104000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.104000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.104000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xee404000
[    4.144000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    4.144000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.144000] usb usb5: configuration #1 chosen from 1 choice
[    4.144000] hub 5-0:1.0: USB hub found
[    4.144000] hub 5-0:1.0: 8 ports detected
[    4.272000] ahci 0000:00:1f.2: version 2.2
[    4.272000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
[    5.276000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[    5.276000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    5.276000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.276000] scsi0 : ahci
[    5.276000] scsi1 : ahci
[    5.276000] scsi2 : ahci
[    5.276000] scsi3 : ahci
[    5.276000] ata1: SATA max UDMA/133 cmd 0xf886e500 ctl 0x00000000 bmdma 0x00000000 irq 16
[    5.276000] ata2: SATA max UDMA/133 cmd 0xf886e580 ctl 0x00000000 bmdma 0x00000000 irq 16
[    5.276000] ata3: SATA max UDMA/133 cmd 0xf886e600 ctl 0x00000000 bmdma 0x00000000 irq 16
[    5.276000] ata4: SATA max UDMA/133 cmd 0xf886e680 ctl 0x00000000 bmdma 0x00000000 irq 16
[    5.368000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    5.552000] usb 1-2: configuration #1 chosen from 1 choice
[    5.796000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    5.796000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.796000] ata1.00: ATA-7: HTS721010G9SA00, MCZIC10V, max UDMA/100
[    5.796000] ata1.00: 195371568 sectors, multi 16: LBA48 
[    5.796000] ata1.00: configured for UDMA/100
[    5.964000] usb 4-1: configuration #1 chosen from 1 choice
[    6.108000] ata2: SATA link down (SStatus 0 SControl 0)
[    6.208000] usb 4-2: new full speed USB device using uhci_hcd and address 3
[    6.384000] usb 4-2: configuration #1 chosen from 1 choice
[    6.384000] usbcore: registered new interface driver hiddev
[    6.400000] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /class/input/input2
[    6.400000] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.0-2
[    6.420000] ata3: SATA link down (SStatus 0 SControl 0)
[    6.548000] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /class/input/input3
[    6.548000] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.0-2
[    6.548000] usbcore: registered new interface driver usbhid
[    6.548000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    6.736000] ata4: SATA link down (SStatus 0 SControl 0)
[    6.736000] scsi 0:0:0:0: Direct-Access     ATA      HTS721010G9SA00  MCZI PQ: 0 ANSI: 5
[    6.736000] ata_piix 0000:00:1f.1: version 2.11
[    6.736000] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 16
[    6.736000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    6.736000] scsi4 : ata_piix
[    6.736000] scsi5 : ata_piix
[    6.736000] ata5: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011880 irq 14
[    6.736000] ata6: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011888 irq 15
[    6.740000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    6.740000] sd 0:0:0:0: [sda] Write Protect is off
[    6.740000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.740000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.740000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    6.740000] sd 0:0:0:0: [sda] Write Protect is off
[    6.740000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.740000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.740000]  sda:<6>ata5.00: ATA-6: HTS541060G9AT00, MB3IA60A, max UDMA/100
[    6.900000] ata5.00: 117210240 sectors, multi 16: LBA 
[    6.916000] ata5.00: configured for UDMA/100
[    6.916000] ata6: port disabled. ignoring.
[    6.916000] scsi 4:0:0:0: Direct-Access     ATA      HTS541060G9AT00  MB3I PQ: 0 ANSI: 5
[    7.080000]  sda1 sda2 < sda5 sda6 sda7 sda8 > sda3
[    7.148000] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.148000] sd 4:0:0:0: [sdb] 117210240 512-byte hardware sectors (60012 MB)
[    7.148000] sd 4:0:0:0: [sdb] Write Protect is off
[    7.148000] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    7.148000] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.148000] sd 4:0:0:0: [sdb] 117210240 512-byte hardware sectors (60012 MB)
[    7.148000] sd 4:0:0:0: [sdb] Write Protect is off
[    7.148000] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    7.148000] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.148000]  sdb: sdb1 sdb2
[    7.172000] sd 4:0:0:0: [sdb] Attached SCSI disk
[    7.172000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.172000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    7.380000] Attempting manual resume
[    7.380000] swsusp: Resume From Partition 8:17
[    7.380000] PM: Checking swsusp image.
[    7.380000] PM: Resume from disk failed.
[    7.408000] kjournald starting.  Commit interval 5 seconds
[    7.408000] EXT3-fs: mounted filesystem with ordered data mode.
[   17.424000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   17.424000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   18.328000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.376000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.380000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.484000] iTCO_vendor_support: vendor-support=0
[   18.528000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   18.528000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   18.528000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.664000] intel_rng: FWH not detected
[   18.680000] input: PC Speaker as /class/input/input4
[   18.852000] Bluetooth: Core ver 2.11
[   18.852000] NET: Registered protocol family 31
[   18.852000] Bluetooth: HCI device and connection manager initialized
[   18.852000] Bluetooth: HCI socket layer initialized
[   19.092000] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:2012]
[   19.092000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   19.092000] Yenta: Routing CardBus interrupts to PCI
[   19.092000] Yenta TI: socket 0000:15:00.0, mfunc 0x01d01002, devctl 0x64
[   19.116000] ieee80211_crypt: registered algorithm 'NULL'
[   19.164000] Bluetooth: HCI USB driver ver 2.9
[   19.164000] usbcore: registered new interface driver hci_usb
[   19.180000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.180000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.208000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   19.208000] serio: Synaptics pass-through port at isa0060/serio1/input0
[   19.248000] input: SynPS/2 Synaptics TouchPad as /class/input/input5
[   19.308000] irda_init()
[   19.308000] NET: Registered protocol family 23
[   19.328000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   19.328000] Socket status: 30000020
[   19.328000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xdfff
[   19.328000] cs: IO port probe 0xa000-0xdfff: clean.
[   19.328000] pcmcia: parent PCI bridge Memory window: 0xe4300000 - 0xe7ffffff
[   19.328000] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe3ffffff
[   19.336000] NET: Registered protocol family 17
[   19.340000] pnp: Device 00:0a activated.
[   19.340000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   19.340000] nsc-ircc, chip->init
[   19.340000] nsc-ircc, Found chip at base=0x164e
[   19.340000] nsc-ircc, driver loaded (Dag Brattli)
[   19.340000] IrDA: Registered device irda0
[   19.340000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   19.456000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   19.456000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.456000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   19.456000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   19.456000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.596000] usbcore: registered new interface driver xpad
[   19.596000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   19.904000] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[   19.904000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.964000] pccard: CardBus card inserted into slot 0
[   20.084000] cs: IO port probe 0x100-0x3af: clean.
[   20.088000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.088000] cs: IO port probe 0x820-0x8ff: clean.
[   20.088000] cs: IO port probe 0xc00-0xcf7: clean.
[   20.088000] cs: IO port probe 0xa00-0xaff: clean.
[   20.112000] Linux video capture interface: v2.00
[   20.284000] saa7130/34: v4l2 driver version 0.2.14 loaded
[   20.284000] PCI: Enabling device 0000:16:00.0 (0000 -> 0002)
[   20.284000] ACPI: PCI Interrupt 0000:16:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.284000] saa7133[0]: found at 0000:16:00.0, rev: 240, irq: 16, latency: 0, mmio: 0xc4000000
[   20.284000] PCI: Setting latency timer of device 0000:16:00.0 to 64
[   20.284000] saa7133[0]: subsystem: 17de:7203, board: UNKNOWN/GENERIC [card=0,autodetected]
[   20.284000] saa7133[0]: board init: gpio is 0
[   20.420000] saa7133[0]: i2c eeprom 00: de 17 03 72 ff ff ff ff ff ff ff ff ff ff ff ff
[   20.420000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.420000] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.420000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.420000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.420000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.420000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.420000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.420000] saa7133[0]: registered device video0 [v4l2]
[   20.420000] saa7133[0]: registered device vbi0
[   20.432000] saa7134 ALSA driver for DMA sound loaded
[   20.432000] saa7133[0]/alsa: saa7133[0] at 0xc4000000 irq 16 registered as card -2
[   20.608000] lp: driver loaded but no devices found
[   20.652000] Adding 2441840k swap on /dev/sdb1.  Priority:-1 extents:1 across:2441840k
[   20.656000] Adding 2441840k swap on /dev/sda8.  Priority:-2 extents:1 across:2441840k
[   21.088000] EXT3 FS on sdb2, internal journal
[   21.480000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   21.976000] NET: Registered protocol family 10
[   21.980000] lo: Disabled Privacy Extensions
[   24.780000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   25.012000] input: TPPS/2 IBM TrackPoint as /class/input/input6
[   25.460000] kjournald starting.  Commit interval 5 seconds
[   25.472000] EXT3 FS on sda5, internal journal
[   25.472000] EXT3-fs: mounted filesystem with ordered data mode.
[   25.496000] kjournald starting.  Commit interval 5 seconds
[   25.496000] EXT3 FS on sda6, internal journal
[   25.496000] EXT3-fs: mounted filesystem with ordered data mode.
[   25.528000] kjournald starting.  Commit interval 5 seconds
[   25.528000] EXT3 FS on sda7, internal journal
[   25.528000] EXT3-fs: mounted filesystem with ordered data mode.
[   26.832000] ACPI: ACPI Dock Station Driver 
[   26.836000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   26.836000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   26.836000] ACPI: Error installing bay notify handler
[   26.836000] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
[   26.864000] ACPI: Battery Slot [BAT0] (battery present)
[   26.992000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   26.996000] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   27.016000] ACPI: AC Adapter [AC] (on-line)
[   27.036000] input: Power Button (FF) as /class/input/input7
[   27.036000] ACPI: Power Button (FF) [PWRF]
[   27.036000] input: Lid Switch as /class/input/input8
[   27.036000] ACPI: Lid Switch [LID]
[   27.036000] input: Sleep Button (CM) as /class/input/input9
[   27.036000] ACPI: Sleep Button (CM) [SLPB]
[   28.836000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   30.856000] ppdev: user-space parallel port driver
[   31.584000] audit(1194668860.949:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5429 profile="/usr/sbin/cupsd"
[   31.732000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   31.736000] [fglrx] Maximum main memory to use for locked dma buffers: 2896 MBytes.
[   31.736000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   31.744000] apm: BIOS not found.
[   31.780000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.068000] Failure registering capabilities with primary security module.
[   32.404000] eth0: no IPv6 routers present
[   33.640000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   33.640000] thinkpad_acpi: http://ibm-acpi.sf.net/
[   33.640000] thinkpad_acpi: ThinkPad EC firmware 79HT50WW-1.07
[   33.848000] [fglrx] total      GART = 130023424
[   33.848000] [fglrx] free       GART = 114032640
[   33.848000] [fglrx] max single GART = 114032640
[   33.848000] [fglrx] total      LFB  = 134086656
[   33.848000] [fglrx] free       LFB  = 114143232
[   33.848000] [fglrx] max single LFB  = 114143232
[   33.848000] [fglrx] total      Inv  = 0
[   33.848000] [fglrx] free       Inv  = 0
[   33.848000] [fglrx] max single Inv  = 0
[   33.848000] [fglrx] total      TIM  = 0
[ 3035.732000] pccard: card ejected from slot 0
[ 3161.624000] ------------[ cut here ]------------
[ 3161.624000] kernel BUG at /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/saa7134/saa7134-core.c:306!
[ 3161.624000] invalid opcode: 0000 [#1]
[ 3161.624000] SMP 
[ 3161.624000] Modules linked in: binfmt_misc thinkpad_acpi fglrx(P) ppdev acpi_cpufreq cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table cpufreq_conservative cpufreq_powersave sbs button ac video container battery bay dock nls_iso8859_1 nls_cp437 vfat fat ipv6 parport_pc lp parport saa7134_alsa saa7134 video_buf compat_ioctl32 ir_kbd_i2c i2c_core ir_common videodev v4l2_common v4l1_compat snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event pcmcia xpad snd_seq joydev ipw3945 snd_timer snd_seq_device irtty_sir sir_dev nsc_ircc af_packet irda ieee80211 hci_usb ieee80211_crypt yenta_socket rsrc_nonstatic pcmcia_core crc_ccitt bluetooth snd soundcore intel_agp psmouse iTCO_wdt serio_raw iTCO_vendor_support snd_page_alloc shpchp pci_hotplug agpgart evdev ext3 jbd mbcache sg sd_mod ata_piix usbhid hid ahci ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore e1000 thermal processor fan fuse apparmor commoncap
[ 3161.624000] CPU:    0
[ 3161.624000] EIP:    0060:[<f8bfb55c>]    Tainted: P       VLI
[ 3161.624000] EFLAGS: 00010002   (2.6.22-14-generic #1)
[ 3161.624000] EIP is at saa7134_buffer_queue+0xbc/0xc0 [saa7134]
[ 3161.624000] eax: 0000007f   ebx: f7fb95c4   ecx: f45d23c0   edx: f7fb95c4
[ 3161.624000] esi: f45d23c0   edi: f7fb9000   ebp: b7543008   esp: f45cbf1c
[ 3161.624000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
[ 3161.624000] Process xawtv.bin (pid: 6639, ti=f45ca000 task=f5a56a60 task.ti=f45ca000)
[ 3161.624000] Stack: 00000120 0006c000 f8c190e8 00000286 f45900ec 0006c000 f8b88366 0000006d 
[ 3161.624000]        00100073 00000001 0006c000 00000000 f4590000 b7543008 0006c000 f8c01332 
[ 3161.624000]        f45cbfa0 00000000 00000000 f45d9480 b7543008 f45cbfa0 0006c000 c0180dbc 
[ 3161.624000] Call Trace:
[ 3161.624000]  [<f8b88366>] videobuf_read_one+0x286/0x300 [video_buf]
[ 3161.624000]  [<f8c01332>] video_read+0xa2/0xb0 [saa7134]
[ 3161.624000]  [<c0180dbc>] vfs_read+0xbc/0x160
[ 3161.624000]  [<f8c01290>] video_read+0x0/0xb0 [saa7134]
[ 3161.624000]  [<c01812f1>] sys_read+0x41/0x70
[ 3161.624000]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[ 3161.624000]  =======================
[ 3161.624000] Code: 46 20 02 00 00 00 eb ab 89 73 04 31 c9 89 f2 89 f8 ff 96 90 00 00 00 eb 9a 89 73 04 83 e9 68 89 f2 89 f8 ff 96 90 00 00 00 eb 88 <0f> 0b eb fe 83 ec 14 89 5c 24 0c 89 c3 b8 ed ff ff ff 89 74 24 
[ 3161.624000] EIP: [<f8bfb55c>] saa7134_buffer_queue+0xbc/0xc0 [saa7134] SS:ESP 0068:f45cbf1c
[ 3161.628000] BUG: unable to handle kernel NULL pointer dereference at virtual address 000002ff
[ 3161.628000]  printing eip:
[ 3161.628000] f8c03061
[ 3161.628000] *pde = 00000000
[ 3161.628000] Oops: 0000 [#2]
[ 3161.628000] SMP 
[ 3161.628000] Modules linked in: binfmt_misc thinkpad_acpi fglrx(P) ppdev acpi_cpufreq cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table cpufreq_conservative cpufreq_powersave sbs button ac video container battery bay dock nls_iso8859_1 nls_cp437 vfat fat ipv6 parport_pc lp parport saa7134_alsa saa7134 video_buf compat_ioctl32 ir_kbd_i2c i2c_core ir_common videodev v4l2_common v4l1_compat snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event pcmcia xpad snd_seq joydev ipw3945 snd_timer snd_seq_device irtty_sir sir_dev nsc_ircc af_packet irda ieee80211 hci_usb ieee80211_crypt yenta_socket rsrc_nonstatic pcmcia_core crc_ccitt bluetooth snd soundcore intel_agp psmouse iTCO_wdt serio_raw iTCO_vendor_support snd_page_alloc shpchp pci_hotplug agpgart evdev ext3 jbd mbcache sg sd_mod ata_piix usbhid hid ahci ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore e1000 thermal processor fan fuse apparmor commoncap
[ 3161.628000] CPU:    0
[ 3161.628000] EIP:    0060:[<f8c03061>]    Tainted: P       VLI
[ 3161.628000] EFLAGS: 00010246   (2.6.22-14-generic #1)
[ 3161.628000] EIP is at video_release+0xa1/0x1e0 [saa7134]
[ 3161.628000] eax: 00000000   ebx: f45901c4   ecx: 00000000   edx: ffffffff
[ 3161.628000] esi: f45900ec   edi: f4590000   ebp: f7fb9000   esp: f45cbd74
[ 3161.628000] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
[ 3161.628000] Process xawtv.bin (pid: 6639, ti=f45ca000 task=f5a56a60 task.ti=f45ca000)
[ 3161.628000] Stack: f45d9480 00000008 f45d9480 f7f85770 f78cd8d0 c018166d 00000000 00000000 
[ 3161.628000]        f7f85770 dfe3f380 f78cd8d0 f45d9480 f52b7900 00000000 f52b7900 c017ea47 
[ 3161.628000]        f45cbdbc 00000001 f52c8540 00000000 c012a3df 00000010 f52b7900 f5a56a60 
[ 3161.628000] Call Trace:
[ 3161.628000]  [<c018166d>] __fput+0xad/0x1a0
[ 3161.628000]  [<c017ea47>] filp_close+0x47/0x80
[ 3161.628000]  [<c012a3df>] put_files_struct+0x8f/0xb0
[ 3161.628000]  [<c012b641>] do_exit+0x151/0x810
[ 3161.628000]  [<c0120688>] __wake_up+0x38/0x50
[ 3161.628000]  [<c0105edf>] die+0x25f/0x260
[ 3161.628000]  [<c0106200>] do_invalid_op+0x0/0x90
[ 3161.628000]  [<c0106281>] do_invalid_op+0x81/0x90
[ 3161.628000]  [<f8bfb55c>] saa7134_buffer_queue+0xbc/0xc0 [saa7134]
[ 3161.628000]  [<f8b88870>] videobuf_vmalloc_to_sg+0x30/0xc0 [video_buf]
[ 3161.628000]  [<c016a97b>] vmalloc_to_page+0x6b/0xa0
[ 3161.628000]  [<f8b888c9>] videobuf_vmalloc_to_sg+0x89/0xc0 [video_buf]
[ 3161.628000]  [<f8b87be0>] pci_map_sg+0x0/0x90 [video_buf]
[ 3161.628000]  [<c02f4292>] error_code+0x72/0x80
[ 3161.628000]  [<f8bfb55c>] saa7134_buffer_queue+0xbc/0xc0 [saa7134]
[ 3161.628000]  [<f8b88366>] videobuf_read_one+0x286/0x300 [video_buf]
[ 3161.628000]  [<f8c01332>] video_read+0xa2/0xb0 [saa7134]
[ 3161.628000]  [<c0180dbc>] vfs_read+0xbc/0x160
[ 3161.628000]  [<f8c01290>] video_read+0x0/0xb0 [saa7134]
[ 3161.628000]  [<c01812f1>] sys_read+0x41/0x70
[ 3161.628000]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[ 3161.628000]  =======================
[ 3161.628000] Code: c0 0f 85 f3 00 00 00 8b 87 80 02 00 00 85 c0 0f 85 d5 00 00 00 b9 04 00 00 00 89 fa 89 e8 e8 57 db ff ff 8b 95 28 01 00 00 31 c9 <0f> b6 82 00 03 00 00 25 e0 00 00 00 88 82 00 03 00 00 8b 95 28 
[ 3161.628000] EIP: [<f8c03061>] video_release+0xa1/0x1e0 [saa7134] SS:ESP 0068:f45cbd74
[ 3161.628000] Fixing recursive fault but reboot is needed!
[ 3529.628000] pccard: CardBus card inserted into slot 0
[ 3529.628000] PCI: Enabling device 0000:16:00.0 (0000 -> 0002)
[ 3529.628000] ACPI: PCI Interrupt 0000:16:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 3529.628000] saa7133[0]: found at 0000:16:00.0, rev: 240, irq: 16, latency: 0, mmio: 0xc4000000
[ 3529.628000] PCI: Setting latency timer of device 0000:16:00.0 to 64
[ 3529.628000] saa7133[0]: subsystem: 17de:7203, board: UNKNOWN/GENERIC [card=0,autodetected]
[ 3529.628000] saa7133[0]: board init: gpio is 0
[ 3529.764000] saa7133[0]: i2c eeprom 00: de 17 03 72 ff ff ff ff ff ff ff ff ff ff ff ff
[ 3529.764000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 3529.764000] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 3529.764000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 3529.764000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 3529.764000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 3529.764000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 3529.764000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 3529.764000] saa7133[0]: registered device video0 [v4l2]
[ 3529.764000] saa7133[0]: registered device vbi0
[ 3529.764000] saa7133[0]/alsa: saa7133[0] at 0xc4000000 irq 16 registered as card -2
[ 3978.936000] pccard: card ejected from slot 0
[ 4156.964000] pccard: CardBus card inserted into slot 0
[ 4156.964000] PCI: Enabling device 0000:16:00.0 (0000 -> 0002)
[ 4156.964000] ACPI: PCI Interrupt 0000:16:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 4156.964000] saa7133[0]: found at 0000:16:00.0, rev: 240, irq: 16, latency: 0, mmio: 0xc4000000
[ 4156.964000] PCI: Setting latency timer of device 0000:16:00.0 to 64
[ 4156.964000] saa7133[0]: subsystem: 17de:7203, board: UNKNOWN/GENERIC [card=0,autodetected]
[ 4156.964000] saa7133[0]: board init: gpio is 0
[ 4157.100000] saa7133[0]: i2c eeprom 00: de 17 03 72 ff ff ff ff ff ff ff ff ff ff ff ff
[ 4157.100000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4157.100000] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4157.100000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4157.100000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4157.100000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4157.100000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4157.100000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4157.100000] saa7133[0]: registered device video0 [v4l2]
[ 4157.100000] saa7133[0]: registered device vbi0
[ 4157.100000] saa7133[0]/alsa: saa7133[0] at 0xc4000000 irq 16 registered as card -2
root@scheung-laptop:/home/scheung# 

```

---

