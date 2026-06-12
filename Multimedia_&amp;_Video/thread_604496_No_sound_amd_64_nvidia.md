---
title: "No sound amd 64 nvidia"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by d00by on 2007-11-06
I had reinstalled ubuntu gutsy in the hope that my sound issue would be fixed.

It did not work! :(

What is causing the problem.

I have installed the packages for multimedia mentioned at the ubuntu documentation website. [https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796]("https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796")

It did not help. I cannot hear any sound!

Here is the output of lspci, dmesg, lsmod

```


00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=d49b59dd-0a2e-4b7e-955d-7a2e8fb043cf ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bf10000 (usable)
[    0.000000]  BIOS-e820: 000000003bf10000 - 000000003bf17000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bf17000 - 000000003bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 245520) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F87A0 checksum 0
[    0.000000] ACPI: RSDP 000F87A0, 0024 (r3 HPQOEM)
[    0.000000] ACPI: XSDT 3BF100AC, 005C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 3BF16B21, 00F4 (r3 HPQOEM SLIC-MPC  6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 3BF10108, 6A19 (r1 HPQOEM SLIC-MPC  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BF17FC0, 0040
[    0.000000] ACPI: SLIC 3BF16C89, 0176 (r1 HPQOEM SLIC-MPC  6040000 HPQ         1)
[    0.000000] ACPI: MCFG 3BF16DFF, 003C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: HPET 3BF16E3B, 0038 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: APIC 3BF16E73, 0050 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: BOOT 3BF16EC3, 0028 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3BF16EEB, 0115 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003bf10000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 245520) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003bf10000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   245520
[    0.000000] On node 0 totalpages: 245421
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2816 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3300 pages used for memmap
[    0.000000]   DMA32 zone: 238124 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 240940
[    0.000000] Kernel command line: root=UUID=d49b59dd-0a2e-4b7e-955d-7a2e8fb043cf ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[   19.152645] time.c: Detected 2009.144 MHz processor.
[   19.155703] Console: colour VGA+ 80x25
[   19.155718] Checking aperture...
[   19.155722] CPU 0: aperture @ 3600000000 size 32 MB
[   19.155723] Aperture too small (32 MB)
[   19.162489] No AGP bridge found
[   19.173556] Memory: 956424k/982080k available (2274k kernel code, 25260k reserved, 1181k data, 296k init)
[   19.173599] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   19.250739] Calibrating delay using timer specific routine.. 4021.63 BogoMIPS (lpj=8043263)
[   19.250772] Security Framework v1.0.0 initialized
[   19.250777] SELinux:  Disabled at boot.
[   19.250868] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.251650] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   19.251993] Mount-cache hash table entries: 256
[   19.252123] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   19.252126] CPU: L2 Cache: 512K (64 bytes/line)
[   19.252128] CPU 0/0 -> Node 0
[   19.252149] SMP alternatives: switching to UP code
[   19.252309] Freeing SMP alternatives: 24k freed
[   19.252697] Early unpacking initramfs... done
[   19.541399] ACPI: Core revision 20070126
[   19.541460] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.592829] Using local APIC timer interrupts.
[   19.642539] result 12557145
[   19.642541] Detected 12.557 MHz APIC timer.
[   19.646247] Brought up 1 CPUs
[   19.646480] NET: Registered protocol family 16
[   19.646551] ACPI: bus type pci registered
[   19.646557] PCI: Using configuration type 1
[   19.647342] ACPI: EC: Look up EC in DSDT
[   19.649372] ACPI: EC: GPE=0x01, ports=0x66, 0x62
[   19.660205] ACPI: System BIOS is requesting _OSI(Linux)
[   19.660207] ACPI: Please test with "acpi_osi=!Linux"
[   19.660209] Please send dmidecode to linux-acpi@vger.kernel.org
[   19.660468] ACPI: Interpreter enabled
[   19.660471] ACPI: (supports S0 S3 S4 S5)
[   19.660484] ACPI: Using IOAPIC for interrupt routing
[   19.671416] ACPI: EC: GPE=0x01, ports=0x66, 0x62
[   19.671468] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.671476] PCI: Probing PCI hardware (bus 00)
[   19.672562] PCI: Transparent bridge - 0000:00:10.0
[   19.672589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.672681] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   19.672718] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   19.672744] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   19.764350] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 22 23) *0, disabled.
[   19.764525] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 22 23) *10
[   19.764697] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 *10 11 14 15)
[   19.764867] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[   19.765039] ACPI: PCI Interrupt Link [LK1E] (IRQs 20) *0, disabled.
[   19.765209] ACPI: PCI Interrupt Link [LK2E] (IRQs 19) *11
[   19.765379] ACPI: PCI Interrupt Link [LK3E] (IRQs 21) *10
[   19.765549] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 22 23) *0, disabled.
[   19.765721] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 22 23) *10
[   19.765897] ACPI: PCI Interrupt Link [LSMU] (IRQs 16 17 18 22 23) *11
[   19.766079] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 22 23) *11
[   19.766252] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 22 23) *7
[   19.766423] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 22 23) *11
[   19.766600] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 22 23) *0, disabled.
[   19.766772] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 22 23) *0, disabled.
[   19.766944] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 22 23) *0, disabled.
[   19.767116] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 22 23) *0, disabled.
[   19.767294] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 22 23) *5
[   19.767471] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 22 23) *0
[   19.767550] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.767559] pnp: PnP ACPI init
[   19.767567] ACPI: bus type pnp registered
[   19.771426] pnp: PnP ACPI: found 11 devices
[   19.771429] ACPI: ACPI bus type pnp unregistered
[   19.771476] PCI: Using ACPI for IRQ routing
[   19.771479] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.771568] NET: Registered protocol family 8
[   19.771570] NET: Registered protocol family 20
[   19.771650] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   19.771654] hpet0: 3 32-bit timers, 25000000 Hz
[   19.772704] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   19.772709] pnp: 00:02: ioport range 0x1000-0x107f has been reserved
[   19.772712] pnp: 00:02: ioport range 0x1080-0x10ff has been reserved
[   19.772714] pnp: 00:02: ioport range 0x1400-0x147f has been reserved
[   19.772717] pnp: 00:02: ioport range 0x1480-0x14ff has been reserved
[   19.772720] pnp: 00:02: ioport range 0x1800-0x187f has been reserved
[   19.772723] pnp: 00:02: ioport range 0x1880-0x18ff has been reserved
[   19.772726] pnp: 00:02: ioport range 0x2000-0x203f has been reserved
[   19.772979] PCI: Bridge: 0000:00:02.0
[   19.772980]   IO window: disabled.
[   19.772984]   MEM window: b3000000-b30fffff
[   19.772986]   PREFETCH window: disabled.
[   19.772988] PCI: Bridge: 0000:00:03.0
[   19.772990]   IO window: 4000-4fff
[   19.772993]   MEM window: b4000000-b7ffffff
[   19.772996]   PREFETCH window: d0000000-d01fffff
[   19.772998] PCI: Bridge: 0000:00:10.0
[   19.773000]   IO window: disabled.
[   19.773003]   MEM window: b8000000-b80fffff
[   19.773006]   PREFETCH window: disabled.
[   19.773017] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   19.773023] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   19.773030] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   19.773073] NET: Registered protocol family 2
[   19.774047] Time: tsc clocksource has been installed.
[   19.806057] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   19.806404] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   19.808822] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   19.809593] TCP: Hash tables configured (established 131072 bind 65536)
[   19.809596] TCP reno registered
[   19.818099] checking if image is initramfs... it is
[   20.379274] Freeing initrd memory: 7202k freed
[   20.384682] Simple Boot Flag at 0x36 set to 0x1
[   20.385036] audit: initializing netlink socket (disabled)
[   20.385046] audit(1194368062.180:1): initialized
[   20.386729] VFS: Disk quotas dquot_6.5.1
[   20.386781] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   20.386865] io scheduler noop registered
[   20.386867] io scheduler anticipatory registered
[   20.386869] io scheduler deadline registered
[   20.386948] io scheduler cfq registered (default)
[   20.386963] Boot video device is 0000:00:05.0
[   20.609283] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   20.609304] assign_interrupt_mode Found MSI capability
[   20.609307] Allocate Port Service[0000:00:02.0:pcie00]
[   20.609360] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   20.609378] assign_interrupt_mode Found MSI capability
[   20.609380] Allocate Port Service[0000:00:03.0:pcie00]
[   20.630214] Real Time Clock Driver v1.12ac
[   20.630386] hpet_resources: 0xfed00000 is busy
[   20.630426] Linux agpgart interface v0.102 (c) Dave Jones
[   20.630429] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.631350] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.631536] input: Macintosh mouse button emulation as /class/input/input0
[   20.631592] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.631938] i8042.c: Detected active multiplexing controller, rev 1.1.
[   20.632009] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.632013] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   20.632016] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   20.632018] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   20.632021] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   20.632225] mice: PS/2 mouse device common for all mice
[   20.632402] TCP cubic registered
[   20.632457] NET: Registered protocol family 1
[   20.632683] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   20.632691] Freeing unused kernel memory: 296k freed
[   20.700878] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.797092] AppArmor: AppArmor initialized<5>audit(1194368063.596:2):  type=1505 info="AppArmor initialized" pid=1249
[   21.861365] fuse init (API version 7.8)
[   21.865217] Failure registering capabilities with primary security module.
[   21.882389] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   21.882395] ACPI: Processor [CPU0] (supports 8 throttling states)
[   21.882405] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.888479] Marking TSC unstable due to possible TSC halt in C2
[   21.891260] Time: hpet clocksource has been installed.
[   21.895642] ACPI: Thermal Zone [TZS0] (72 C)
[   21.900298] ACPI: Thermal Zone [TZS1] (75 C)
[   22.511107] usbcore: registered new interface driver usbfs
[   22.511131] usbcore: registered new interface driver hub
[   22.511152] usbcore: registered new device driver usb
[   22.511791] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   22.512128] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[   22.512138] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 23
[   22.512249] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   22.512256] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   22.512388] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   22.512411] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xb0004000
[   22.523128] SCSI subsystem initialized
[   22.527888] libata version 2.21 loaded.
[   22.554249] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   22.604672] usb usb1: configuration #1 chosen from 1 choice
[   22.604697] hub 1-0:1.0: USB hub found
[   22.604709] hub 1-0:1.0: 8 ports detected
[   22.710895] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   22.710901] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.711542] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   22.711560] NFORCE-MCP51: chipset revision 241
[   22.711563] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   22.711569] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[   22.711577]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:pio, hdb:pio
[   22.711586]     ide1: BM-DMA at 0x3088-0x308f, BIOS settings: hdc:pio, hdd:pio
[   22.711592] Probing IDE interface ide0...
[   23.277438] Probing IDE interface ide1...
[   24.012627] hdc: MATSHITADVD-RAM UJ-850S, ATAPI CD/DVD-ROM drive
[   24.348665] ide1 at 0x170-0x177,0x376 on irq 15
[   24.351153] sata_nv 0000:00:0e.0: version 3.4
[   24.351165] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   24.351464] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 22
[   24.351474] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 22 (level, high) -> IRQ 22
[   24.351649] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   24.352159] scsi0 : sata_nv
[   24.352378] scsi1 : sata_nv
[   24.352548] ata1: SATA max UDMA/133 cmd 0x00000000000130b0 ctl 0x00000000000130a6 bmdma 0x0000000000013090 irq 22
[   24.352553] ata2: SATA max UDMA/133 cmd 0x00000000000130a8 ctl 0x00000000000130a2 bmdma 0x0000000000013098 irq 22
[   24.360995] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, (U)DMA
[   24.361003] Uniform CD-ROM driver Revision: 3.20
[   24.819329] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.827476] ata1.00: ATA-7: ST980811AS, 3.BHD, max UDMA/100
[   24.827479] ata1.00: 156301488 sectors, multi 16: LBA48 
[   24.843461] ata1.00: configured for UDMA/100
[   25.154859] ata2: SATA link down (SStatus 0 SControl 300)
[   25.165549] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.BH PQ: 0 ANSI: 5
[   25.166774] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 18
[   25.166785] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 18 (level, high) -> IRQ 18
[   25.166791] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   25.166799] forcedeth: using HIGHDMA
[   25.174797] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   25.174825] sd 0:0:0:0: [sda] Write Protect is off
[   25.174828] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.174840] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.174889] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   25.174896] sd 0:0:0:0: [sda] Write Protect is off
[   25.174899] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.174909] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.174914]  sda: sda1 sda2 < sda5 sda6 > sda3
[   25.254325] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.257947] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.556564] Attempting manual resume
[   25.556567] swsusp: Resume From Partition 8:6
[   25.556569] PM: Checking swsusp image.
[   25.556774] PM: Resume from disk failed.
[   25.587382] kjournald starting.  Commit interval 5 seconds
[   25.587392] EXT3-fs: mounted filesystem with ordered data mode.
[   25.686446] eth0: forcedeth.c: subsystem: 0103c:30b5 bound to 0000:00:14.0
[   25.686893] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 17
[   25.686903] ACPI: PCI Interrupt 0000:05:09.0[A] -> Link [LNK1] -> GSI 17 (level, high) -> IRQ 17
[   25.739065] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   25.743514] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 16
[   25.743523] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 16 (level, high) -> IRQ 16
[   25.743710] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   25.743716] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   25.743766] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   25.743795] ehci_hcd 0000:00:0b.1: debug port 1
[   25.743799] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   25.743811] ehci_hcd 0000:00:0b.1: irq 16, io mem 0xb0005000
[   25.743820] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.743892] usb usb2: configuration #1 chosen from 1 choice
[   25.743914] hub 2-0:1.0: USB hub found
[   25.743920] hub 2-0:1.0: 8 ports detected
[   27.012401] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[07e40a00a8d45010]
[   35.251772] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.264541] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.601325] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   35.601354] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   36.251166] sdhci: Secure Digital Host Controller Interface driver
[   36.251170] sdhci: Copyright(c) Pierre Ossman
[   36.251215] sdhci: SDHCI controller found at 0000:05:09.1 [1180:0822] (rev 19)
[   36.251538] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 23
[   36.251542] ACPI: PCI Interrupt 0000:05:09.1[B] -> Link [LNK2] -> GSI 23 (level, high) -> IRQ 23
[   36.251740] mmc0: SDHCI at 0xb8000800 irq 23 DMA
[   36.333061] nvidia: module license 'NVIDIA' taints kernel.
[   36.709293] input: PC Speaker as /class/input/input2
[   36.820520] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 21
[   36.820532] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 21 (level, high) -> IRQ 21
[   36.820540] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   36.820757] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   37.096344] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   37.126358] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   37.154465] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   37.154470] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 22 (level, high) -> IRQ 22
[   37.154621] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   38.154618] loop: module loaded
[   38.245738] lp: driver loaded but no devices found
[   38.376760] ndiswrapper version 1.45 loaded (smp=yes)
[   38.497404] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   38.498664] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   38.499153] ACPI: PCI Interrupt Link [LK2E] enabled at IRQ 19
[   38.499164] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 19
[   38.499192] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   38.505585] ndiswrapper: using IRQ 19
[   38.868414] wlan0: ethernet device 00:1a:73:34:82:eb using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
[   38.868453] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   38.873067] usbcore: registered new interface driver ndiswrapper
[   38.882405] ndiswrapper: changing interface name from 'wlan0' to 'eth0'
[   38.962121] Adding 377488k swap on /dev/sda6.  Priority:-1 extents:1 across:377488k
[   39.370850] EXT3 FS on sda3, internal journal
[   40.491958] ACPI: Battery Slot [BAT0] (battery present)
[   40.538355] No dock devices found.
[   40.550539] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   40.578943] ACPI: AC Adapter [ADP1] (on-line)
[   40.619589] input: Power Button (FF) as /class/input/input4
[   40.623527] ACPI: Power Button (FF) [PWRF]
[   40.649211] input: Lid Switch as /class/input/input5
[   40.653115] ACPI: Lid Switch [LID0]
[   40.678897] input: Sleep Button (CM) as /class/input/input6
[   40.682826] ACPI: Sleep Button (CM) [SLPB]
[   40.708435] input: Power Button (CM) as /class/input/input7
[   40.712323] ACPI: Power Button (CM) [PWRB]
[   40.932616] powernow-k8: Found 1 AMD Turion(tm) 64  processors (version 2.00.00)
[   40.932653] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
[   40.932656] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   40.932658] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   40.932660] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[   42.403941] ppdev: user-space parallel port driver
[   42.699094] audit(1194348284.689:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4907 profile="/usr/sbin/cupsd"
[   43.172203] Failure registering capabilities with primary security module.
[   43.333944] Bluetooth: Core ver 2.11
[   43.334035] NET: Registered protocol family 31
[   43.334038] Bluetooth: HCI device and connection manager initialized
[   43.334041] Bluetooth: HCI socket layer initialized
[   43.341961] Bluetooth: L2CAP ver 2.8
[   43.341965] Bluetooth: L2CAP socket layer initialized
[   43.372261] Bluetooth: RFCOMM socket layer initialized
[   43.372332] Bluetooth: RFCOMM TTY layer initialized
[   43.372335] Bluetooth: RFCOMM ver 1.8
[   46.019740] NET: Registered protocol family 17
[   48.849961] NET: Registered protocol family 10
[   48.850102] lo: Disabled Privacy Extensions
[   48.850438] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   53.050885] eth1: no IPv6 routers present
[   81.793397] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   89.509077] eth0: no IPv6 routers present
[  407.867611] eth1: link down.
Module                  Size  Used by
ipv6                  317192  8 
af_packet              28172  4 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16608  0 
cpufreq_ondemand       10896  1 
cpufreq_userspace       6048  0 
cpufreq_conservative     9608  0 
cpufreq_powersave       3072  0 
cpufreq_stats           8160  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    21520  0 
container               6400  0 
button                 10400  0 
ac                      7304  0 
video                  21140  8 
dock                   12264  0 
battery                12424  0 
ndiswrapper           233632  0 
sbp2                   27144  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
loop                   21764  0 
joydev                 13440  0 
snd_hda_intel         337192  1 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4608  0 
nvidia               7013492  36 
serio_raw               9092  0 
psmouse                45596  0 
sdhci                  21004  0 
mmc_core               33416  1 sdhci
snd                    69288  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
k8temp                  7680  0 
i2c_nforce2             7808  0 
i2c_core               30208  2 nvidia,i2c_nforce2
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
evdev                  13056  6 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
sd_mod                 32512  3 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
amd74xx                17328  0 [permanent]
ide_core              141200  2 ide_cd,amd74xx
ehci_hcd               40076  0 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
forcedeth              55048  0 
sata_nv                24068  2 
ata_generic             9988  0 
libata                138928  2 sata_nv,ata_generic
scsi_mod              172856  4 sbp2,sg,sd_mod,libata
ohci_hcd               25092  0 
usbcore               161584  4 ndiswrapper,ehci_hcd,ohci_hcd
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor

```

---

### Post by rajeev1204 on 2007-11-06
have you tried alsamixer in terminal and check if everything is not muted ?

Or you can try the latest alsa drivers .I recently compiled new drivers for my acer laptop .

Its very easy , ill guide you .


But first try double check if all channels are un muted in alsamixer.

Also have you tried fiddling with menu/system/preferences/sound ?


regards

rajeev

---

### Post by d00by on 2007-11-06
> **rajeev1204 said:**
> have you tried alsamixer in terminal and check if everything is not muted ?

Or you can try the latest alsa drivers .I recently compiled new drivers for my acer laptop .

Its very easy , ill guide you .


rajeev

 bhai rajeev,

I have checked for mute. Checkout the attached screenshot. A picture says a thousand words.

I have not tried the driver thing as I do not know how to. I just resinstalled gutsy with latest updates.

Any help will be **most welcome** as running a computer without sound is AWFUL! :(

'dukhi' d00by

---

### Post by rajeev1204 on 2007-11-06
Download latest alsa driver from [www.alsa-project.org](www.alsa-project.org) 

From synaptic , install the package build-essential.

Now change into the directory where u downloaded alsa driver.

type ./configure then wait for it to finish,.

then type make.

then type sudo make install.

do these steps and let me know.There are a few more steps.(later :)


regards

rajeev

---

### Post by rmtatum on 2007-11-06
Is the Nviidia card set as the default? 

Post the results of 
```
asoundconf list
```

---

### Post by d00by on 2007-11-06
> **rmtatum said:**
> Is the Nviidia card set as the default? 

Post the results of 
```
asoundconf list
```
The results are this.

> Names of available sound cards:
NVidia


---

### Post by d00by on 2007-11-06
> **rajeev1204 said:**
> Download latest alsa driver from [www.alsa-project.org](www.alsa-project.org) 

From synaptic , install the package build-essential.

Now change into the directory where u downloaded alsa driver.

type ./configure then wait for it to finish,.

then type make.

then type sudo make install.

do these steps and let me know.There are a few more steps.(later :)


regards

rajeev
err, I downloaded the alsa driver 1.0.15 to Documents directoy.

do I have to extract it first and then run configure command?

EDIT : **[COLOR="DarkRed"]Ok. i figured it out. running the configure thing now. :)[/COLOR]**

---

### Post by d00by on 2007-11-06
Ok. I did it. After the sudo command ended, it gave this last 'warning' message/output/whatever


> 
[COLOR="Red"]WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.
[/COLOR]

Ok. Now, what do I do next?? :|

---

### Post by xgene on 2007-11-06
I have the same problem and I'm getting crazy heir...some smart ideas would be more then welcome...I browsed all possible forums and tried everything...somehow it just won't start...

I have the same card Nvidia everything is unmuted, compiled ...etc..    

Help is more then wanted :-)



And some Ideas on why my Laptop won't restart ...or ideas why it get stuck while doing restart... it writes Mashine is restarting and nothing hapens...

---

### Post by rajeev1204 on 2007-11-07
> **d00by said:**
> Ok. I did it. After the sudo command ended, it gave this last 'warning' message/output/whatever




Ok. Now, what do I do next?? :|

This message is normal. Go to terminal and type alsamixer .

Unmute all sliders  . Try muting / unmuting the IEC 958 option by pressing M.

---

### Post by d00by on 2007-11-07
> **rajeev1204 said:**
> This message is normal. Go to terminal and type alsamixer .

Unmute all sliders  . Try muting / unmuting the IEC 958 option by pressing M.

I am getting this message when I type alsamixer

>  alsamixer

alsamixer: function snd_ctl_open failed for default: No such device


View the screenshot. I am not able to [COLOR="Red"]open[/COLOR] the volume control any more. :(

---

### Post by d00by on 2007-11-07
were there supposed to be more commands after _sudo make install_??

---

### Post by rajeev1204 on 2007-11-07
ok

change into that alsa directory again and type ./snddevices. 

also can you post the contents of cat /etc/modprobe.d/alsa-base?





thanks

rajeev

---

### Post by d00by on 2007-11-07
> **rajeev1204 said:**
> ok

change into that alsa directory again and type ./snddevices. 

also can you post the contents of cat /etc/modprobe.d/alsa-base?




when I type the first command in the alsa directory I get a lot of *chown cannot access no such directory , mknode permission denied* outputs.

I am giving the results of the second command

```

 cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


```

Also, FWIW this is the output of the first command that  could capture in a file using >> operator. It was not able to capture the error commands. I think there is a specific operator for that I can not remember right now. My UNIX is a little rusty. I had done a unix course 7-8 years back.... :mad:

Anyway, here is some of the output from the first snddevices command.

```

Creating mixer?...done.
Creating sequencer...done.
Creating midi0?...done.
Creating dsp?...done.
Creating audio?...done.
Creating sndstat...done.
Creating music...done.
Creating dmmidi?...done.
Creating dmfm?...done.
Creating amixer?...done.
Creating adsp?...done.
Creating amidi?...done.
Creating admmidi?...done.
Creating snd/control?...done.
Creating snd/seq...done.
Creating snd/timer...done.
Creating snd/hw??...done.
Creating snd/midi??...done.
Creating snd/pcm??p...done.
Creating snd/pcm??c...done.
Creating aload?...done.
Creating aloadSEQ...done.
```

Any idea what is happening?? :confused:

---

### Post by rajeev1204 on 2007-11-07
> **d00by said:**
> when I type the first command in the alsa directory I get a lot of *chown cannot access no such directory , mknode permission denied* outputs.

I am giving the results of the second command

```

 cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


```

Also, FWIW this is the output of the first command that  could capture in a file using >> operator. It was not able to capture the error commands. I think there is a specific operator for that I can not remember right now. My UNIX is a little rusty. I had done a unix course 7-8 years back.... :mad:

Anyway, here is some of the output from the first snddevices command.

```

Creating mixer?...done.
Creating sequencer...done.
Creating midi0?...done.
Creating dsp?...done.
Creating audio?...done.
Creating sndstat...done.
Creating music...done.
Creating dmmidi?...done.
Creating dmfm?...done.
Creating amixer?...done.
Creating adsp?...done.
Creating amidi?...done.
Creating admmidi?...done.
Creating snd/control?...done.
Creating snd/seq...done.
Creating snd/timer...done.
Creating snd/hw??...done.
Creating snd/midi??...done.
Creating snd/pcm??p...done.
Creating snd/pcm??c...done.
Creating aload?...done.
Creating aloadSEQ...done.
```

Any idea what is happening?? :confused:


type sudo ./snddevices.

---

### Post by d00by on 2007-11-07
i am having problems with 2nd command modprobe. neither intel nor nvidia option work. i have stopped at that step

> $ sudo ./snddevices
[sudo] password for user:
Creating mixer?...done.
Creating sequencer...done.
Creating midi0?...done.
Creating dsp?...done.
Creating audio?...done.
Creating sndstat...done.
Creating music...done.
Creating dmmidi?...done.
Creating dmfm?...done.
Creating amixer?...done.
Creating adsp?...done.
Creating amidi?...done.
Creating admmidi?...done.
rm: cannot remove `/dev/snd': Is a directory
Creating snd/control?...done.
Creating snd/seq...done.
Creating snd/timer...done.
Creating snd/hw??...done.
Creating snd/midi??...done.
Creating snd/pcm??p...done.
Creating snd/pcm??c...done.
Creating aload?...done.
Creating aloadSEQ...done.

modprobe snd-intel
FATAL: Module snd_intel not found.

user:~/Documents/alsa-driver-1.0.15$ modprobe snd-nvidia
FATAL: Module snd_nvidia not found.


---

### Post by rajeev1204 on 2007-11-07
> **d00by said:**
> i am having problems with 2nd command modprobe. neither intel nor nvidia option work. i have stopped at that step


What happens when you right click on the volume tab?

what devices does it list ?

---

### Post by d00by on 2007-11-07
I get gstreamer plugin error dialog when I try to open volume control.

I am posting screenshoots of sound preferences.

I tried to reinstall alsa-base using synaptics. 

It did not help. :(

---

### Post by rajeev1204 on 2007-11-07
> **d00by said:**
> I get gstreamer plugin error dialog when I try to open volume control.

I am posting screenshoots of sound preferences.

I tried to reinstall alsa-base using synaptics. 

It did not help. :(


Iam sorry about that man . I guess reinstalling alsa-base may solve .Restart machine .

Or try a clean install by first removing alsa-base with all configuration files option .
Then reinstall .

Also maybe its something to do with gstreamer so try fresh install for those too ?

Do let me know how it goes . 

regards

rajeev

---

### Post by d00by on 2007-11-07
did not help.

Any idea how to reconfigure the sound card?

---

### Post by rajeev1204 on 2007-11-07
Hmm 

Thats all for now . 

Ill find out more about this .






regards

rajeev

Happy diwali

---

### Post by d00by on 2007-11-07
any suggestions on what to do next??

Can you tell me what you think may be wrong with my system so that I can atleast understand what the problem is??

Was/is my sound card being detected before? Is it a driver thingy??

I am so frustrated by this. This would suck if I can not play sound! :(

having said that, thank you for your time, patience and help. :)

I just wsh I would atleast understand what my problem really is!

Right now, I even don't know for sure what kind of sound card config I have!!

This is soooooooo frustrating... Is it because of 64 bit thing??

---

### Post by jaybombalous on 2007-11-07
excuse me for asking a really dumb question here, but what kind of sounds are u trying to hear? I ask this because when I installed another linux I had the right drivers installed for the sound card and nothing would play. After days of messing around I finally d/l'd a simple *.wav file and tried it, to my amazement it played. Then I started sorting out the real problem, the codecs and applications used to play my media. :)

Just a thought

---

### Post by d00by on 2007-11-07
I am not able to play any sound.

All I can hear is when I ry to take my cursor to the very end in cursor window, I can hear the system beep and my screen flashes.

That's it.

Apart from that NOTHING.

Here is the status. Life SUCKS right now. I think I have messed it up even more. ear;lier the aplay -l used to display nvidia something. Now even that is gone. 

I think I have completely removed my sound card driver. In plain english, I haev made matters worse.. :(

> 
aplay -l
aplay: device_list:204: no soundcards found...


modinfo soundcore
filename:       /lib/modules/2.6.22-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.22-14-generic SMP mod_unload 

sudo lshw -class sound
  *-multimedia UNCLAIMED  
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2


---

### Post by d00by on 2007-11-07
> **rajeev1204 said:**
> Hmm 

Thats all for now . 

Ill find out more about this .




 i was able 

Using this set of commands i was atleast able to restore to version 1.0.14.

I got from this site [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

```
Method C

Confirmed with kernel 2.6.22-13:

    *

      does work: Lenovo T61p
    *

      does not work: Aluminium iMac

Confirmed with kernel 2.6.22-14:

    *

      does work: Dell D830
    *

      causes gnome-settings-manager to crash on Dell Latitude D630

sudo apt-get install alsa-source
cd && mkdir alsa-patched && cd alsa-patched
tar -jxvf /usr/src/alsa-driver.tar.bz2
cd modules/alsa-driver/
wget -O alsa-kernel/pci/hda/patch_analog.c http://launchpadlibrarian.net/9021234/patch_analog.c
./configure --with-cards=hda-intel && make
sudo make install
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo depmod -a


```

But, sound has not come back.

aplay -l gives this

```


 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

---

### Post by d00by on 2007-11-07
> **rajeev1204 said:**
> What happens when you right click on the volume tab?

what devices does it list ?

see the attached screen shot.

---

### Post by teqagogo on 2007-11-07
Hi,

I got the same problem with both 7.04 and 7.10. Toshiba psp3ae

Here is how i fixed the sound pb:

1/ Kernel startup option
sudo cp -p /boot/grub/menu.lst /boot/grub/menu.lst.bck
vi /boot/grub/menu.lst
and add the option acpi=off to the kernel
you should have something like:
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=xxxxxxxxxxxxxx ro quiet splash acpi=off


2/ Re-configure the alsa driver

there are several ways to so that, i found an easy one on a forum and it worked fine for me, if you prefer starting from the source go to alsa it's very well documented:

first get this tool:
sudo apt-get install module-assistant

Then :
cd /usr/src
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa
sudo shutdown -r now

Hope you hear the tam tam

---

### Post by d00by on 2007-11-07
vi is too complicated. can I use another editor?? I am on ubuntu. Do I need special permission to edit the file??

---

### Post by teqagogo on 2007-11-07
hi

try this:

 sudo gedit /boot/grub/menu.lst

---

### Post by d00by on 2007-11-07
doing it. report in a couple of minutes as to how it went after reboot.... 

keepig fingers and toes crossed. :D

edit : this is slow. wen i do it using configure make, it is much faster.

out of curiosity, will it install v14 or v15 of alsa driver?

---

### Post by teqagogo on 2007-11-07
there is more than one way to do it, it's up to you.

I did not say i got the true but just it worked for me :lolflag:

i also did the manual install from source on 7.04 but in this case you'll get the lastest provided by ubuntu and was successfully tested on 7.04 and 7.10....v14

v15 is also working fine

---

### Post by d00by on 2007-11-07
did not work.

no sound.

plus, my screen went out of whack because of acpi=off thingy... :|

what does acpi do??

How do I get my original screen resolution and stuff back??

---

### Post by macpeteo on 2007-11-07
Well, I to don't have sound:

Running Ubuntu 7.10 on a HP Media Center PVCm1160n

Using Alsa 1.0.14 (as loaded by Ubuntu.

Thanks for any help you can provide,
Macpeteo

---

### Post by jaybombalous on 2007-11-07
> **d00by said:**
> did not work.

no sound.

plus, my screen went out of whack because of acpi=off thingy... :|

what does acpi do??

How do I get my original screen resolution and stuff back??

you need to restore the file u made with the sudo cp command. What the command did was copy the menu.lst to menu.lst.back.

In reguards to changing it back, u need to restore that file. Delete the menu.lst and rename the menu.lst.back file to menu.lst.

U do this in the same directory that u did the copy command in to begin with.

---

### Post by d00by on 2007-11-08
I don't know what happened. The sound is working now.

I logged in to windows today and after listening to some music on iTunes for an hour or two, I shut my sytem down,

Then after a hour I booted up and logged in to Ubuntu.

What is the first thing that happen?? The sweet ubuntu login sound.

I can not believ my ears! Is ths sound I am hearing, I ask myself? Am I in a dream? Am I hallucinating!

I open a .wav file to make sure. It works????

Now, I am petrified of logging out or playing soud formats like mp3/mp4.

I am afraid that this miracle will not last!! :guitar:

All I can do is hope for the best....

Pray for me folks..... :confused:

---

### Post by mempman on 2008-01-08
> **d00by said:**
> I don't know what happened. The sound is working now.

I logged in to windows today and after listening to some music on iTunes for an hour or two, I shut my sytem down,

Then after a hour I booted up and logged in to Ubuntu.

What is the first thing that happen?? The sweet ubuntu login sound.

I can not believ my ears! Is ths sound I am hearing, I ask myself? Am I in a dream? Am I hallucinating!

I open a .wav file to make sure. It works????

Now, I am petrified of logging out or playing soud formats like mp3/mp4.

I am afraid that this miracle will not last!! :guitar:

All I can do is hope for the best....

Pray for me folks..... :confused:



Dooby,
Read my other post: [http://www.backports.ubuntuforums.org/showthread.php?t=661433](http://www.backports.ubuntuforums.org/showthread.php?t=661433)
I think this is what you problem might be, as you mentioned that you logged into windows xp.  Try it.

---

