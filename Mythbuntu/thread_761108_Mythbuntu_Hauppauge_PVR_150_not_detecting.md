---
title: "Mythbuntu Hauppauge PVR 150 not detecting"
date: 2008-04-20
forum: Mythbuntu
---

### Post by SadaraX on 2008-04-20
I have a fresh install of Mythbuntu 7.10, fully upgraded, but my Hauppauge PVR 150 is not detecting.

I try to go through the MythTV setup and it does not detect my card at all. Also 'lspci' does not list my card in the system.

I have taken the additional step of install the various 'ivtv' packages, and rebooted but it does not help. The drivers do not appear to load automatically.

Running 'dmesg | grep -i ivtv' produces no output. When I try to run 'sudo modprobe ivtv-fb' it produces an error about not being able to find the kernel module (which is not correct, because the driver is in the correct place). I looked at the logs and the kernel tries to load the module but gives this error message:
> 
ivtv_fb_card_id parameter is out of range (valid range: 0--1)

I checked that the firmware is present in /lib/firmware and it is. I would like some help getting the card to work.

Because the command 'lspci' is not reporting anything that even looks like my card (or something unknown), I am afraid the card may be damaged.

---

### Post by tgm4883 on 2008-04-21
it does sound like the card is damaged.  Please post the output of lspci as well as the output of dmesg

---

### Post by agamotto on 2008-04-21
Before you send it in for repairs, try using nano to edit the following: 

/etc/mythtv/modules.conf 

add the line 'options tuner type=50

I had to add the above for my older pvr 150 card, and I haven't had trouble with it since.

---

### Post by SadaraX on 2008-04-27
Thanks for the replies.

EDIT: I also just did an upgrade to Mythbuntu 8.04 LTS through using the graphical program. My problem still persists, no card detected.

Here is my lspci output:
```

lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

```

My DMESG output:
```

 [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bee0000 (usable)
[    0.000000]  BIOS-e820: 000000003bee0000 - 000000003bee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bee3000 - 000000003bef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bf00000 (reserved)
[    0.000000]  BIOS-e820: 000000003c000000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 62MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3a00
[    0.000000] Entering add_active_range(0, 0, 245472) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245472
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245472
[    0.000000] On node 0 totalpages: 245472
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 125 pages used for memmap
[    0.000000]   HighMem zone: 15971 pages, LIFO batch:3
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7A10 checksum 0
[    0.000000] ACPI: RSDP 000F7A10, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3BEE3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP 3BEE30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20070126]
[    0.000000] ACPI: DSDT 3BEE3180, 6395 (r1 NVIDIA NVDAACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BEE0000, 0040
[    0.000000] ACPI: SSDT 3BEE9640, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: _HPT 3BEE98C0, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: MCFG 3BEE9940, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC 3BEE9580, 007C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] Built 1 zonelists.  Total pages: 243555
[    0.000000] Kernel command line: root=UUID=80d2d8a7-d7ea-47cb-a955-2567222021dd ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2210.267 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 961740k/981888k available (2015k kernel code, 19596k reserved, 915k data, 364k init, 64384k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.084000] Calibrating delay using timer specific routine.. 4424.95 BogoMIPS (lpj=8849901)
[    0.084000] Security Framework v1.0.0 initialized
[    0.084000] SELinux:  Disabled at boot.
[    0.084000] Mount-cache hash table entries: 512
[    0.084000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.084000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.084000] CPU 0(2) -> Core 0
[    0.084000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.084000] Compat vDSO mapped to ffffe000.
[    0.084000] Checking 'hlt' instruction... OK.
[    0.100000] SMP alternatives: switching to UP code
[    0.100000] Early unpacking initramfs... done
[    0.364000] ACPI: Core revision 20070126
[    0.364000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.368000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.368000] SMP alternatives: switching to SMP code
[    0.368000] Booting processor 1/1 eip 3000
[    0.376000] Initializing CPU#1
[    0.460000] Calibrating delay using timer specific routine.. 4420.67 BogoMIPS (lpj=8841352)
[    0.460000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.460000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.460000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.460000] CPU 1(2) -> Core 1
[    0.460000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.460000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.460000] Total of 2 processors activated (8845.62 BogoMIPS).
[    0.460000] ENABLING IO-APIC IRQs
[    0.460000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.500000] Brought up 2 CPUs
[    0.516000] migration_cost=4000
[    0.516000] Booting paravirtualized kernel on bare hardware
[    0.516000] Time:  8:12:37  Date: 03/27/108
[    0.516000] NET: Registered protocol family 16
[    0.516000] EISA bus registered
[    0.516000] ACPI: bus type pci registered
[    0.524000] PCI: PCI BIOS revision 3.00 entry at 0xfa7b0, last bus=4
[    0.524000] PCI: Using configuration type 1
[    0.524000] Setting up standard PCI resources
[    0.524000] ACPI: EC: Look up EC in DSDT
[    0.532000] ACPI: Interpreter enabled
[    0.532000] ACPI: (supports S0 S3 S4 S5)
[    0.532000] ACPI: Using IOAPIC for interrupt routing
[    0.540000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.540000] PCI: Probing PCI hardware (bus 00)
[    0.540000] PCI: Transparent bridge - 0000:00:04.0
[    0.540000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.540000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.576000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.576000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.576000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[    0.576000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.576000] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.576000] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.576000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.576000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.576000] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[    0.576000] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.576000] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.576000] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.576000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.576000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.576000] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[    0.576000] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.576000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.576000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.580000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[    0.580000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.580000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.580000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.580000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.580000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.580000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.580000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.580000] pnp: PnP ACPI init
[    0.580000] ACPI: bus type pnp registered
[    0.588000] pnp: PnP ACPI: found 12 devices
[    0.588000] ACPI: ACPI bus type pnp unregistered
[    0.588000] PnPBIOS: Disabled by ACPI PNP
[    0.588000] PCI: Using ACPI for IRQ routing
[    0.588000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.632000] NET: Registered protocol family 8
[    0.632000] NET: Registered protocol family 20
[    0.632000] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[    0.632000] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.632000] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    0.632000] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.632000] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    0.632000] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.632000] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
[    0.632000] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.632000] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[    0.632000] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[    0.632000] pnp: 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
[    0.632000] pnp: 00:01: iomem range 0x3c000000-0x3fffffff could not be reserved
[    0.632000] pnp: 00:0a: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.632000] pnp: 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[    0.632000] pnp: 00:0b: iomem range 0xfeff0000-0xfeff00ff could not be reserved
[    0.632000] pnp: 00:0b: iomem range 0x3bee0000-0x3befffff could not be reserved
[    0.632000] pnp: 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.664000] PCI: Bridge: 0000:00:04.0
[    0.664000]   IO window: c000-cfff
[    0.664000]   MEM window: fd800000-fd8fffff
[    0.664000]   PREFETCH window: fdf00000-fdffffff
[    0.664000] PCI: Bridge: 0000:00:09.0
[    0.664000]   IO window: b000-bfff
[    0.664000]   MEM window: fde00000-fdefffff
[    0.664000]   PREFETCH window: fdd00000-fddfffff
[    0.664000] PCI: Bridge: 0000:00:0b.0
[    0.664000]   IO window: a000-afff
[    0.664000]   MEM window: fdc00000-fdcfffff
[    0.664000]   PREFETCH window: fdb00000-fdbfffff
[    0.664000] PCI: Bridge: 0000:00:0c.0
[    0.664000]   IO window: 9000-9fff
[    0.664000]   MEM window: fda00000-fdafffff
[    0.664000]   PREFETCH window: fd900000-fd9fffff
[    0.664000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    0.664000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    0.664000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.664000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.664000] NET: Registered protocol family 2
[    0.668000] Time: acpi_pm clocksource has been installed.
[    0.668000] Switched to high resolution mode on CPU 0
[    0.668000] Switched to high resolution mode on CPU 1
[    0.708000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.708000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.708000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.708000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.708000] TCP reno registered
[    0.724000] checking if image is initramfs... it is
[    1.244000] Freeing initrd memory: 7201k freed
[    1.244000] audit: initializing netlink socket (disabled)
[    1.244000] audit(1209283957.168:1): initialized
[    1.248000] highmem bounce pool size: 64 pages
[    1.248000] VFS: Disk quotas dquot_6.5.1
[    1.248000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.248000] io scheduler noop registered
[    1.248000] io scheduler anticipatory registered
[    1.248000] io scheduler deadline registered
[    1.248000] io scheduler cfq registered (default)
[    1.264000] Boot video device is 0000:00:0d.0
[    1.264000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    1.264000] assign_interrupt_mode Found MSI capability
[    1.264000] Allocate Port Service[0000:00:09.0:pcie00]
[    1.264000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    1.264000] assign_interrupt_mode Found MSI capability
[    1.264000] Allocate Port Service[0000:00:0b.0:pcie00]
[    1.264000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    1.264000] assign_interrupt_mode Found MSI capability
[    1.264000] Allocate Port Service[0000:00:0c.0:pcie00]
[    1.264000] isapnp: Scanning for PnP cards...
[    1.616000] isapnp: No Plug & Play device found
[    1.632000] Real Time Clock Driver v1.12ac
[    1.632000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.632000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.632000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.636000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.636000] input: Macintosh mouse button emulation as /class/input/input0
[    1.636000] PNP: No PS/2 controller found. Probing ports directly.
[    1.636000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.636000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.636000] mice: PS/2 mouse device common for all mice
[    1.636000] EISA: Probing bus 0 at eisa.0
[    1.636000] Cannot allocate resource for EISA slot 1
[    1.636000] Cannot allocate resource for EISA slot 2
[    1.636000] EISA: Detected 0 cards.
[    1.636000] TCP cubic registered
[    1.636000] NET: Registered protocol family 1
[    1.636000] Using IPI No-Shortcut mode
[    1.636000]   Magic number: 4:32:221
[    1.636000]   hash matches device ttyu5
[    1.636000] Freeing unused kernel memory: 364k freed
[    2.812000] AppArmor: AppArmor initialized<5>audit(1209283958.668:2):  type=1505 info="AppArmor initialized" pid=1188
[    2.816000] fuse init (API version 7.8)
[    2.820000] Failure registering capabilities with primary security module.
[    2.848000] ACPI: Fan [FAN] (on)
[    2.856000] ACPI: Thermal Zone [THRM] (38 C)
[    3.316000] usbcore: registered new interface driver usbfs
[    3.316000] usbcore: registered new interface driver hub
[    3.316000] usbcore: registered new device driver usb
[    3.320000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[    3.320000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
[    3.320000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    3.320000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.320000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    3.320000] ehci_hcd 0000:00:02.1: debug port 1
[    3.320000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    3.320000] ehci_hcd 0000:00:02.1: irq 16, io mem 0xfe02e000
[    3.320000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.320000] usb usb1: configuration #1 chosen from 1 choice
[    3.320000] hub 1-0:1.0: USB hub found
[    3.320000] hub 1-0:1.0: 8 ports detected
[    3.332000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.344000] SCSI subsystem initialized
[    3.348000] libata version 2.21 loaded.
[    3.428000] sata_nv 0000:00:08.0: version 3.4
[    3.428000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[    3.428000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 17
[    3.428000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    3.428000] scsi0 : sata_nv
[    3.428000] scsi1 : sata_nv
[    3.428000] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001dc00 irq 17
[    3.428000] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001dc08 irq 17
[    3.432000] Floppy drive(s): fd0 is 1.44M
[    3.448000] FDC 0 is a post-1991 82077
[    3.896000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.904000] ata1.00: ATA-7: WDC WD4000YR-01PLB0, 01.06A01, max UDMA/133
[    3.904000] ata1.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.920000] ata1.00: configured for UDMA/133
[    4.388000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.396000] ata2.00: ATA-7: WDC WD4000YR-01PLB0, 01.06A01, max UDMA/133
[    4.396000] ata2.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.412000] ata2.00: configured for UDMA/133
[    4.412000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD4000YR-01P 01.0 PQ: 0 ANSI: 5
[    4.412000] scsi 1:0:0:0: Direct-Access     ATA      WDC WD4000YR-01P 01.0 PQ: 0 ANSI: 5
[    4.412000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    4.412000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 18
[    4.412000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    4.412000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.412000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    4.412000] ohci_hcd 0000:00:02.0: irq 18, io mem 0xfe02f000
[    4.468000] usb usb2: configuration #1 chosen from 1 choice
[    4.468000] hub 2-0:1.0: USB hub found
[    4.468000] hub 2-0:1.0: 8 ports detected
[    4.572000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    4.572000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.576000] NFORCE-MCP61: IDE controller at PCI slot 0000:00:06.0
[    4.576000] NFORCE-MCP61: chipset revision 162
[    4.576000] NFORCE-MCP61: not 100% native mode: will probe irqs later
[    4.576000] NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
[    4.576000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[    4.576000] Probing IDE interface ide0...
[    4.588000] sd 0:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
[    4.588000] sd 0:0:0:0: [sda] Write Protect is off
[    4.588000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.588000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.588000] sd 0:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
[    4.588000] sd 0:0:0:0: [sda] Write Protect is off
[    4.588000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.588000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.588000]  sda: sda1 sda2 sda3 sda4
[    4.628000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.628000] sd 1:0:0:0: [sdb] 781422768 512-byte hardware sectors (400088 MB)
[    4.628000] sd 1:0:0:0: [sdb] Write Protect is off
[    4.628000] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.628000] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.628000] sd 1:0:0:0: [sdb] 781422768 512-byte hardware sectors (400088 MB)
[    4.628000] sd 1:0:0:0: [sdb] Write Protect is off
[    4.628000] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.628000] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.628000]  sdb: sdb1
[    4.636000] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.640000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.640000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.892000] Attempting manual resume
[    4.892000] swsusp: Resume From Partition 8:4
[    4.892000] PM: Checking swsusp image.
[    4.892000] PM: Resume from disk failed.
[    4.940000] kjournald starting.  Commit interval 5 seconds
[    4.940000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.312000] hda: _NEC DV-5800A, ATAPI CD/DVD-ROM drive
[    5.652000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.656000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    5.656000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    5.656000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 19
[    5.656000] eth0: RTL8169sc/8110sc at 0xf8818000, 00:18:37:01:ee:49, XID 18000000 IRQ 19
[    9.656000] input: PC Speaker as /class/input/input1
[    9.676000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    9.680000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.700000] hda: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[    9.700000] Uniform CD-ROM driver Revision: 3.20
[    9.712000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[    9.712000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
[    9.720000] Linux agpgart interface v0.102 (c) Dave Jones
[    9.748000] parport_pc 00:09: reported by Plug and Play ACPI
[    9.748000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   10.024000] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   10.024000] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 20 (level, low) -> IRQ 20
[   10.024000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   10.232000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   11.460000] lp0: using parport0 (interrupt-driven).
[   11.564000] Adding 1959920k swap on /dev/sda4.  Priority:-1 extents:1 across:1959920k
[   11.896000] EXT3 FS on sda2, internal journal
[   12.744000] kjournald starting.  Commit interval 5 seconds
[   12.748000] EXT3 FS on sda1, internal journal
[   12.748000] EXT3-fs: mounted filesystem with ordered data mode.
[   12.792000] kjournald starting.  Commit interval 5 seconds
[   12.792000] EXT3 FS on sda3, internal journal
[   12.792000] EXT3-fs: mounted filesystem with ordered data mode.
[   12.796000] kjournald starting.  Commit interval 5 seconds
[   12.804000] EXT3 FS on sdb1, internal journal
[   12.804000] EXT3-fs: mounted filesystem with ordered data mode.
[   13.716000] input: Power Button (FF) as /class/input/input2
[   13.716000] ACPI: Power Button (FF) [PWRF]
[   13.720000] input: Power Button (CM) as /class/input/input3
[   13.720000] ACPI: Power Button (CM) [PWRB]
[   13.864000] No dock devices found.
[   15.872000] r8169: eth0: link up
[   16.148000] NET: Registered protocol family 10
[   16.148000] lo: Disabled Privacy Extensions
[   25.716000] NET: Registered protocol family 17
[   38.568000] eth0: no IPv6 routers present


```

**@agamotto:**
My /etc/modules.conf was blank, so I added it as you suggested. Nothing changed. The card is still not showing up, even after a few reboots.

As a last ditch effort I tried:
sudo modprobe ivtv. Running 'dmesg|grep ivtv' returns this:

```

dmesg|grep -i ivtv
[  148.582649] ivtv:  Start initialization, version 1.1.0
[  148.582686] ivtv:  End initialization

```

But nothing changed. My Hauppauge still does not detect when using 'sudo mythtv-setup.' I checked and my user is definitely in the 'mythtv' group.

---

### Post by Titus A Duxass on 2008-04-27
If you have one, try using another pci slot.
If you do not have another slot, remove the card boot the system and then shut it down. Boot the system once again and have a look at dmesg.

---

### Post by laga on 2008-04-27
Your card doesn't show up in lspci (unless I'm being blind), so make sure it's inserted properly or try a different PCI slots as suggested by Titus A Duxass.

---

### Post by 98springer on 2008-05-10
Did you buy this on eBay recently? I ask because I bought a "Hauppauge" card recently and the seller shipped the wrong card. Not even the right brand. I thought it looked strange but I installed it anyway. It gave alot of the symptoms you're having. I contacted customer service and they replaced the card with the right one.

---

