---
title: "pcHDTV 5500 disables PVR-150 in edgy"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by ralyon on 2006-11-07
Both cards were working fine in Dapper until I did an update and the PVR-150 started getting video glitches. Then I saw that Edgy was out and has Mythtv .20 in the repos I thought it would be a good time to upgrade. (Why is it I always forget that upgrades bring new problems?)

I have tried installing each card first and both times when the pcHDTV was installed the PVR-150 gets errors. The PVR did work on its own until I installed the other. My apoligies in advanced for anything I've left out.

```
 -------------dmesg--------------
[    0.000000] ACPI: RSDT (v001 K8T890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee3040
[    0.000000] ACPI: FADT (v001 K8T890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee30c0
[    0.000000] ACPI: MCFG (v001 K8T890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003feea840
[    0.000000] ACPI: MADT (v001 K8T890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003feea780
[    0.000000] ACPI: DSDT (v001 K8T890 AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003fee0000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fee0000
[    0.000000] On node 0 totalpages: 256826
[    0.000000]   DMA zone: 2590 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 254236 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ fe1a000000 size 128 MB
[    0.000000] Aperture from northbridge cpu 0 beyond 4GB. Ignoring.
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ b0000000 size 128 MB (APSIZE f20)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sda1 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 2200.130 MHz processor.
[   24.257292] Console: colour VGA+ 80x25
[   24.257791] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.258457] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   24.266572] Memory: 1019720k/1047424k available (2129k kernel code, 27312k reserved, 1424k data, 188k init)
[   24.344927] Calibrating delay using timer specific routine.. 4405.40 BogoMIPS (lpj=8810804)
[   24.344974] Security Framework v1.0.0 initialized
[   24.344979] SELinux:  Disabled at boot.
[   24.344997] Mount-cache hash table entries: 256
[   24.345113] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.345116] CPU: L2 Cache: 512K (64 bytes/line)
[   24.345119] CPU 0/0(1) -> Node 0 -> Core 0
[   24.345130] SMP alternatives: switching to UP code
[   24.345229] Freeing SMP alternatives: 20k freed
[   24.345339] checking if image is initramfs... it is
[   24.800838] Freeing initrd memory: 5927k freed
[   24.803660] ACPI: Core revision 20060707
[   24.807679] ACPI: Looking for DSDT ... not found!
[   25.097519] Using local APIC timer interrupts.
[   25.142934] result 12500741
[   25.142936] Detected 12.500 MHz APIC timer.
[   25.144269] Brought up 1 CPUs
[   25.144396] testing NMI watchdog ... OK.
[   25.184440] migration_cost=0
[   25.184638] NET: Registered protocol family 16
[   25.184659] ACPI: bus type pci registered
[   25.187608] PCI: Using MMCONFIG at e0000000
[   25.187643] PCI: No mmconfig possible on device 0:18
[   25.196989] ACPI: Interpreter enabled
[   25.196992] ACPI: Using IOAPIC for interrupt routing
[   25.197488] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.197490] PCI: Probing PCI hardware (bus 00)
[   25.201717] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.1
[   25.201958] PCI: Quirk-MSI-K8T Soundcard On
[   25.201961] PCI: Unexpected Value in PCI-Register: no Change!
[   25.201966] PCI: enabled onboard AC97/MC97 devices
[   25.202221] Boot video device is 0000:02:00.0
[   25.202706] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.321100] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
[   25.321467] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   25.321758] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[   25.322122] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[   25.322485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   25.322976] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   25.323302] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   25.323648] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[   25.323975] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   25.324299] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   25.324603] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   25.324906] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   25.325221] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *5
[   25.325721] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[   25.326211] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   25.326572] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[   25.327004] ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
[   25.330157] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.330169] pnp: PnP ACPI init
[   25.335744] pnp: PnP ACPI: found 16 devices
[   25.335781] PCI: Using ACPI for IRQ routing
[   25.335784] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.335791] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.0
[   25.335850] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.3
[   25.336082] agpgart: Detected AGP bridge 0
[   25.341054] agpgart: AGP aperture is 128M @ 0xb0000000
[   25.341073] PCI-DMA: Disabling IOMMU.
[   25.341489] pnp: 00:01: ioport range 0x4000-0x407f could not be reserved
[   25.341492] pnp: 00:01: ioport range 0x5000-0x500f has been reserved
[   25.341672] PCI: Bridge: 0000:00:01.0
[   25.341674]   IO window: disabled.
[   25.341676]   MEM window: disabled.
[   25.341677]   PREFETCH window: disabled.
[   25.341680] PCI: Bridge: 0000:00:02.0
[   25.341681]   IO window: disabled.
[   25.341684]   MEM window: c0000000-c7ffffff
[   25.341686]   PREFETCH window: b8000000-bfffffff
[   25.341688] PCI: Bridge: 0000:00:03.0
[   25.341689]   IO window: disabled.
[   25.341691]   MEM window: disabled.
[   25.341692]   PREFETCH window: disabled.
[   25.341694] PCI: Bridge: 0000:00:03.1
[   25.341697]   IO window: 9000-9fff
[   25.341699]   MEM window: ce000000-cfffffff
[   25.341702]   PREFETCH window: 40000000-400fffff
[   25.341704] PCI: Bridge: 0000:00:03.2
[   25.341707]   IO window: a000-afff
[   25.341709]   MEM window: cc000000-cdffffff
[   25.341711]   PREFETCH window: 40100000-401fffff
[   25.341713] PCI: Bridge: 0000:00:03.3
[   25.341715]   IO window: disabled.
[   25.341716]   MEM window: disabled.
[   25.341718]   PREFETCH window: disabled.
[   25.341730] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.341743] GSI 16 sharing vector 0xA9 and IRQ 16
[   25.341746] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 169
[   25.341750] PCI: Via IRQ fixup for 0000:00:02.0, from 5 to 9
[   25.341770] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.341781] GSI 17 sharing vector 0xB1 and IRQ 17
[   25.341783] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 177
[   25.341787] PCI: Via IRQ fixup for 0000:00:03.0, from 5 to 1
[   25.341807] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   25.341818] GSI 18 sharing vector 0xB9 and IRQ 18
[   25.341820] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 35 (level, low) -> IRQ 185
[   25.341824] PCI: Via IRQ fixup for 0000:00:03.1, from 0 to 9
[   25.341844] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   25.341854] GSI 19 sharing vector 0xC1 and IRQ 19
[   25.341856] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 39 (level, low) -> IRQ 193
[   25.341860] PCI: Via IRQ fixup for 0000:00:03.2, from 5 to 1
[   25.341880] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   25.341891] GSI 20 sharing vector 0xC9 and IRQ 20
[   25.341893] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 43 (level, low) -> IRQ 201
[   25.341897] PCI: Via IRQ fixup for 0000:00:03.3, from 5 to 9
[   25.341917] PCI: Setting latency timer of device 0000:00:03.3 to 64
[   25.341972] NET: Registered protocol family 2
[   25.376061] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   25.376236] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   25.377221] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   25.377694] TCP: Hash tables configured (established 131072 bind 65536)
[   25.377697] TCP reno registered
[   25.378002] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   25.378278] audit: initializing netlink socket (disabled)
[   25.378287] audit(1162869757.124:1): initialized
[   25.378405] VFS: Disk quotas dquot_6.5.1
[   25.378422] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   25.378463] Initializing Cryptographic API
[   25.378466] io scheduler noop registered
[   25.378472] io scheduler anticipatory registered
[   25.378478] io scheduler deadline registered
[   25.378492] io scheduler cfq registered (default)
[   25.378878] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 169
[   25.378886] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.378917] assign_interrupt_mode Found MSI capability
[   25.378969] Allocate Port Service[0000:00:02.0:pcie00]
[   25.378996] Allocate Port Service[0000:00:02.0:pcie01]
[   25.379018] Allocate Port Service[0000:00:02.0:pcie03]
[   25.379047] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 177
[   25.379053] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   25.379084] assign_interrupt_mode Found MSI capability
[   25.379123] Allocate Port Service[0000:00:03.0:pcie00]
[   25.379145] Allocate Port Service[0000:00:03.0:pcie01]
[   25.379165] Allocate Port Service[0000:00:03.0:pcie03]
[   25.379194] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 35 (level, low) -> IRQ 185
[   25.379200] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   25.379231] assign_interrupt_mode Found MSI capability
[   25.379270] Allocate Port Service[0000:00:03.1:pcie00]
[   25.379291] Allocate Port Service[0000:00:03.1:pcie01]
[   25.379311] Allocate Port Service[0000:00:03.1:pcie03]
[   25.379338] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 39 (level, low) -> IRQ 193
[   25.379344] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   25.379375] assign_interrupt_mode Found MSI capability
[   25.379414] Allocate Port Service[0000:00:03.2:pcie00]
[   25.379440] Allocate Port Service[0000:00:03.2:pcie01]
[   25.379460] Allocate Port Service[0000:00:03.2:pcie03]
[   25.379486] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 43 (level, low) -> IRQ 201
[   25.379492] PCI: Setting latency timer of device 0000:00:03.3 to 64
[   25.379523] assign_interrupt_mode Found MSI capability
[   25.379562] Allocate Port Service[0000:00:03.3:pcie00]
[   25.379586] Allocate Port Service[0000:00:03.3:pcie01]
[   25.379608] Allocate Port Service[0000:00:03.3:pcie03]
[   25.396664] Real Time Clock Driver v1.12ac
[   25.396695] Linux agpgart interface v0.101 (c) Dave Jones
[   25.396697] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.396798] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.397240] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.397415] mice: PS/2 mouse device common for all mice
[   25.397825] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.397979] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.397983] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.398234] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   25.398432] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.398445] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.398625] TCP bic registered
[   25.398631] NET: Registered protocol family 1
[   25.398636] NET: Registered protocol family 8
[   25.398637] NET: Registered protocol family 20
[   25.398769] ACPI: (supports S0 S1 S3 S4 S5)
[   25.398808] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   25.398824] Freeing unused kernel memory: 188k freed
[   25.421250] input: AT Translated Set 2 keyboard as /class/input/input0
[   25.442108] vga16fb: initializing
[   25.442113] vga16fb: mapped to 0xffff8100000a0000
[   25.662996] Console: switching to colour frame buffer device 80x25
[   25.663001] fb0: VGA16 VGA frame buffer device
[   26.700033] Capability LSM initialized
[   26.726294] ACPI: Fan [FAN] (on)
[   26.730301] ACPI: Thermal Zone [THRM] (41 C)
[   27.032278] SCSI subsystem initialized
[   27.035359] libata version 1.20 loaded.
[   27.036260] sata_via 0000:00:0f.0: version 1.1
[   27.036562] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   27.036566] GSI 21 sharing vector 0x42 and IRQ 21
[   27.036569] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 66
[   27.036578] PCI: Via IRQ fixup for 0000:00:0f.0, from 11 to 2
[   27.036604] sata_via 0000:00:0f.0: routed to hard irq line 2
[   27.036642] ata1: SATA max UDMA/133 cmd 0xB800 ctl 0xBC02 bmdma 0xC800 irq 66
[   27.036658] ata2: SATA max UDMA/133 cmd 0xC000 ctl 0xC402 bmdma 0xC808 irq 66
[   27.206498] ata1: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4063 85:7c69 86:3e01 87:4063 88:407f
[   27.206503] ata1: dev 0 ATA-7, max UDMA/133, 398297088 sectors: LBA48
[   27.218480] ata1: dev 0 configured for UDMA/133
[   27.218482] scsi0 : sata_via
[   27.390322] ata2: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4673 85:7c69 86:3e21 87:4663 88:047f
[   27.390325] ata2: dev 0 ATA-7, max UDMA/133, 490234752 sectors: LBA48
[   27.402307] ata2: dev 0 configured for UDMA/133
[   27.402309] scsi1 : sata_via
[   27.402451]   Vendor: ATA       Model: Maxtor 6L200M0    Rev: BANC
[   27.402457]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   27.402634]   Vendor: ATA       Model: Maxtor 6L250S0    Rev: BACE
[   27.402640]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   27.411501] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[   27.411511] sda: Write Protect is off
[   27.411513] sda: Mode Sense: 00 3a 00 00
[   27.411524] SCSI device sda: drive cache: write back
[   27.411565] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[   27.411572] sda: Write Protect is off
[   27.411573] sda: Mode Sense: 00 3a 00 00
[   27.411583] SCSI device sda: drive cache: write back
[   27.411587]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   27.454906] sd 0:0:0:0: Attached scsi disk sda
[   27.455540] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
[   27.458721] sdb: Write Protect is off
[   27.458724] sdb: Mode Sense: 00 3a 00 00
[   27.458756] SCSI device sdb: drive cache: write back
[   27.458797] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
[   27.458803] sdb: Write Protect is off
[   27.458805] sdb: Mode Sense: 00 3a 00 00
[   27.458815] SCSI device sdb: drive cache: write back
[   27.458817]  sdb: sdb1
[   27.479583] sd 1:0:0:0: Attached scsi disk sdb
[   27.660221] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   27.660238] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 66
[   27.660243] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 2
[   27.660266] VP_IDE: chipset revision 6
[   27.660268] VP_IDE: not 100% native mode: will probe irqs later
[   27.660278] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   27.660284]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:pio, hdb:pio
[   27.660296]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:pio, hdd:DMA
[   27.660305] Probing IDE interface ide0...
[   28.229348] Probing IDE interface ide1...
[   29.376368] hdd: _NEC DVD_RW ND-2500A, ATAPI CD/DVD-ROM drive
[   29.432439] ide1 at 0x170-0x177,0x376 on irq 15
[   29.440139] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   29.440146] Uniform CD-ROM driver Revision: 3.20
[   29.559910] Probing IDE interface ide0...
[   29.625175] ieee1394: Initialized config rom entry `ip1394'
[   29.626292] GSI 22 sharing vector 0x4A and IRQ 22
[   29.626296] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 74
[   29.676455] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[74]  MMIO=[d4004000-d40047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   29.690547] usbcore: registered new driver usbfs
[   29.690565] usbcore: registered new driver hub
[   29.691375] USB Universal Host Controller Interface driver v3.0
[   29.691753] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   29.691758] GSI 23 sharing vector 0x52 and IRQ 23
[   29.691761] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 82
[   29.691769] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 2
[   29.691792] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   29.691905] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   29.691932] uhci_hcd 0000:00:10.0: irq 82, io base 0x0000d400
[   29.692028] usb usb1: configuration #1 chosen from 1 choice
[   29.692044] hub 1-0:1.0: USB hub found
[   29.692050] hub 1-0:1.0: 2 ports detected
[   29.796053] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 82
[   29.796058] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 2
[   29.796081] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   29.796164] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   29.796184] uhci_hcd 0000:00:10.1: irq 82, io base 0x0000d800
[   29.796303] usb usb2: configuration #1 chosen from 1 choice
[   29.796378] hub 2-0:1.0: USB hub found
[   29.796384] hub 2-0:1.0: 2 ports detected
[   29.903878] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 82
[   29.903882] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 2
[   29.903902] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   29.903979] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   29.903996] uhci_hcd 0000:00:10.2: irq 82, io base 0x0000dc00
[   29.904114] usb usb3: configuration #1 chosen from 1 choice
[   29.904195] hub 3-0:1.0: USB hub found
[   29.904201] hub 3-0:1.0: 2 ports detected
[   30.011772] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 82
[   30.011777] PCI: Via IRQ fixup for 0000:00:10.3, from 255 to 2
[   30.011796] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   30.011874] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   30.011890] uhci_hcd 0000:00:10.3: irq 82, io base 0x0000e000
[   30.012006] usb usb4: configuration #1 chosen from 1 choice
[   30.012084] hub 4-0:1.0: USB hub found
[   30.012090] hub 4-0:1.0: 2 ports detected
[   30.035655] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   30.119769] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 82
[   30.119774] PCI: Via IRQ fixup for 0000:00:10.4, from 255 to 2
[   30.119877] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   30.120060] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   30.120096] ehci_hcd 0000:00:10.4: irq 82, io mem 0xd4005000
[   30.120102] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.120227] usb usb5: configuration #1 chosen from 1 choice
[   30.120315] hub 5-0:1.0: USB hub found
[   30.120321] hub 5-0:1.0: 8 ports detected
[   30.267939] Attempting manual resume
[   30.283094] kjournald starting.  Commit interval 5 seconds
[   30.283103] EXT3-fs: mounted filesystem with ordered data mode.
[   30.571160] usb 1-1: device not accepting address 2, error -71
[   30.950945] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000019c966]
[   32.313535] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   32.493385] usb 1-1: configuration #1 chosen from 1 choice
[   32.737133] usb 1-2: new low speed USB device using uhci_hcd and address 5
[   32.912989] usb 1-2: configuration #1 chosen from 1 choice
[   33.156740] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   33.332641] usb 2-1: configuration #1 chosen from 1 choice
[   37.701565] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.703664] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.240268] gameport: EMU10K1 is pci0000:00:0d.1/gameport0, io 0xb400, speed 1159kHz
[   38.579451] Linux video capture interface: v2.00
[   38.625342] GSI 24 sharing vector 0x5A and IRQ 24
[   38.625346] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 36 (level, low) -> IRQ 90
[   38.625356] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   38.625572] sky2 v1.6.1 addr 0xcd000000 irq 90 Yukon-EC (0xb6) rev 2
[   38.625705] sky2 eth0: addr 00:11:d8:a6:04:cd
[   38.681983] sata_sil24 0000:04:00.0: version 0.23
[   38.682004] GSI 25 sharing vector 0x6A and IRQ 25
[   38.682007] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 32 (level, low) -> IRQ 106
[   38.682350] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   38.682745] ata3: SATA max UDMA/100 cmd 0xFFFFC200100A8000 ctl 0x0 bmdma 0x0 irq 106
[   38.682763] ata4: SATA max UDMA/100 cmd 0xFFFFC200100AA000 ctl 0x0 bmdma 0x0 irq 106
[   38.739497] Floppy drive(s): fd0 is 1.44M
[   38.764006] FDC 0 is a post-1991 82077
[   38.887409] ata3: SATA link down (SStatus 0)
[   38.887414] scsi2 : sata_sil24
[   38.931689] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[   38.989803] parport: PnPBIOS parport detected.
[   38.989852] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   39.014185] input: PS2++ Logitech MX Mouse as /class/input/input1
[   39.101125] cx2388x v4l2 driver version 0.0.6 loaded
[   39.126708] input: PC Speaker as /class/input/input2
[   39.187778] cx2388x alsa driver version 0.0.6 loaded
[   39.211100] ata4: SATA link up 3.0 Gbps (SStatus 123)
[   39.213241] ata4: dev 0 cfg 49:2f00 82:746b 83:7f01 84:4163 85:7469 86:3c01 87:4163 88:407f
[   39.213246] ata4: dev 0 ATA-7, max UDMA/133, 781422768 sectors: LBA48
[   39.214703] ata4: dev 0 configured for UDMA/100
[   39.214706] scsi3 : sata_sil24
[   39.215810]   Vendor: ATA       Model: WDC WD4000KS-00M  Rev: 07.0
[   39.215817]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   39.219841] SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
[   39.224015] sdc: Write Protect is off
[   39.224017] sdc: Mode Sense: 00 3a 00 00
[   39.227797] SCSI device sdc: drive cache: write back
[   39.231796] SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
[   39.235127] sdc: Write Protect is off
[   39.235129] sdc: Mode Sense: 00 3a 00 00
[   39.239100] SCSI device sdc: drive cache: write back
[   39.239102]  sdc: sdc1
[   39.245110] sd 3:0:0:0: Attached scsi disk sdc
[   39.245193] CORE cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected]
[   39.245196] TV tuner 64 at 0x1fe, Radio tuner -1 at 0x1fe
[   39.257625] ivtv: disagrees about version of symbol video_unregister_device
[   39.257629] ivtv: Unknown symbol video_unregister_device
[   39.257666] ivtv: disagrees about version of symbol video_device_alloc
[   39.257668] ivtv: Unknown symbol video_device_alloc
[   39.257710] ivtv: disagrees about version of symbol video_register_device
[   39.257712] ivtv: Unknown symbol video_register_device
[   39.257893] ivtv: disagrees about version of symbol video_device_release
[   39.257895] ivtv: Unknown symbol video_device_release
[   39.318250] nvidia: module license 'NVIDIA' taints kernel.
[   39.396614] cx88[0]/2: cx2388x 8802 Driver Manager
[   39.396629] GSI 26 sharing vector 0x72 and IRQ 26
[   39.396632] ACPI: PCI Interrupt 0000:00:0c.2[A] -> GSI 17 (level, low) -> IRQ 114
[   39.396643] cx88[0]/2: found at 0000:00:0c.2, rev: 5, irq: 114, latency: 32, mmio: 0xd2000000
[   39.397640] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 17 (level, low) -> IRQ 114
[   39.397649] cx88[0]/0: found at 0000:00:0c.0, rev: 5, irq: 114, latency: 32, mmio: 0xd0000000
[   39.433354] tuner 0-0043: chip found @ 0x86 (cx88[0])
[   39.433376] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   39.435596] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   39.435610] tuner 0-0061: type set to 64 (LG TDVS-H06xF)
[   39.445427] cx88[0]/0: registered device video0 [v4l2]
[   39.445449] cx88[0]/0: registered device vbi0
[   39.447207] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   39.447490] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   39.447495] GSI 27 sharing vector 0x7A and IRQ 27
[   39.447498] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 122
[   39.447506] PCI: Via IRQ fixup for 0000:00:11.6, from 0 to 10
[   39.672568] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   39.672593] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   39.672619] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   39.842812] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0162
[   39.842825] usbcore: registered new driver usblp
[   39.842828] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   39.865647] ts: Compaq touchscreen protocol output
[   40.056058] sky2 eth0: enabling interface
[   40.083026] usbcore: registered new driver libusual
[   40.112010] usbcore: registered new driver hiddev
[   40.137843] Initializing USB Mass Storage driver...
[   40.139832] scsi4 : SCSI emulation for USB Mass Storage devices
[   40.139909] usb-storage: device found at 4
[   40.139911] usb-storage: waiting for device to settle before scanning
[   40.202153] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   40.259066] hiddev96: USB HID v1.10 Device [CPS UPS AE485] on usb-0000:00:10.0-2
[   40.259083] usbcore: registered new driver usb-storage
[   40.259086] USB Mass Storage support registered.
[   40.441944] hiddev97: USB HID v1.10 Device [CPS  BC 1000D] on usb-0000:00:10.1-1
[   40.441955] usbcore: registered new driver usbhid
[   40.441958] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   40.705887] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   40.705894] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   40.705997] ACPI: PCI Interrupt 0000:00:0c.1[A] -> GSI 17 (level, low) -> IRQ 114
[   40.706021] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   40.706634] GSI 28 sharing vector 0x82 and IRQ 28
[   40.706638] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 130
[   40.706644] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   40.706751] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-8776  Mon Oct 16 21:53:43 PDT 2006
[   40.957157] PCI: Enabling device 0000:00:11.5 (0000 -> 0001)
[   40.957162] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 122
[   40.957167] PCI: Via IRQ fixup for 0000:00:11.5, from 0 to 10
[   40.957314] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   41.086259] NET: Registered protocol family 17
[   41.477257] GSI 29 sharing vector 0x8A and IRQ 29
[   41.477261] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 18 (level, low) -> IRQ 138
[   41.730665] lp0: using parport0 (interrupt-driven).
[   41.773985] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   41.773989] ieee1394: sbp2: Try serialize_io=0 for better performance
[   41.809846] Adding 2224960k swap on /dev/disk/by-uuid/2209d488-0003-430a-9553-b192ebdbaf37.  Priority:-1 extents:1 across:2224960k
[   41.903314] EXT3 FS on sda1, internal journal
[   42.090647] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   42.090650] md: bitmap version 4.39
[   42.236743] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[   42.626458] sky2 eth0: Link is up at 1000 Mbps, full duplex, flow control both
[   42.705818] kjournald starting.  Commit interval 5 seconds
[   42.715899] EXT3 FS on sda3, internal journal
[   42.715903] EXT3-fs: mounted filesystem with ordered data mode.
[   42.717693] kjournald starting.  Commit interval 5 seconds
[   42.727890] EXT3 FS on sda2, internal journal
[   42.727894] EXT3-fs: mounted filesystem with ordered data mode.
[   45.140455] usb-storage: device scan complete
[   45.152435]   Vendor: Brother   Model: MFC-420CN         Rev: 1.00
[   45.152442]   Type:   Direct-Access                      ANSI SCSI revision: 02
[   45.221403] sd 4:0:0:0: Attached scsi removable disk sdd
[   45.221443] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   48.126784] NET: Registered protocol family 10
[   48.126865] lo: Disabled Privacy Extensions
[   48.126966] IPv6 over IPv4 tunneling driver
[   49.477798] ACPI: Power Button (FF) [PWRF]
[   49.477807] ACPI: Power Button (CM) [PWRB]
[   49.567343] ibm_acpi: ec object not found
[   49.593877] pcc_acpi: loading...
[   49.836953] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   49.836974] ACPI Exception (acpi_processor-0240): AE_NOT_FOUND, Evaluating _PSS [20060707]
[   49.844169] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   49.868025] ACPI Exception (acpi_processor-0240): AE_NOT_FOUND, Evaluating _PSS [20060707]
[   58.792768] eth0: no IPv6 routers present
[   59.712604] Bluetooth: Core ver 2.8
[   59.712608] NET: Registered protocol family 31
[   59.712610] Bluetooth: HCI device and connection manager initialized
[   59.712622] Bluetooth: HCI socket layer initialized
[   59.746318] Bluetooth: L2CAP ver 2.8
[   59.746322] Bluetooth: L2CAP socket layer initialized
[   59.760223] Bluetooth: RFCOMM socket layer initialized
[   59.760237] Bluetooth: RFCOMM TTY layer initialized
[   59.760239] Bluetooth: RFCOMM ver 1.7
[ 2667.218480] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 2667.218617] SGI XFS Quota Management subsystem
[ 2667.219359] Filesystem "dm-0": Disabling barriers, not supported by the underlying device
[ 2667.231657] XFS mounting filesystem dm-0
[ 2667.323841] Ending clean XFS mount for filesystem: dm-0
[ 2747.592137] ACPI: PCI interrupt for device 0000:00:0c.2 disabled
[ 2747.922158] ACPI: PCI interrupt for device 0000:00:0c.0 disabled
[ 2767.208935] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[ 2767.209495] cx88[0]/2: cx2388x 8802 Driver Manager
[ 2767.209550] ACPI: PCI Interrupt 0000:00:0c.2[A] -> GSI 17 (level, low) -> IRQ 114
[ 2767.209560] cx88[0]/2: found at 0000:00:0c.2, rev: 5, irq: 114, latency: 32, mmio: 0xd2000000
[ 2767.234630] cx2388x dvb driver version 0.0.6 loaded
[ 2767.234634] cx8802_register_driver() ->registering driver type=dvb access=shared
[ 2767.234638] CORE cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47]
[ 2767.234812] cx88[0]/2: cx2388x based dvb card
[ 2767.564389] DVB: registering new adapter (cx88[0]).
[ 2767.564443] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[ 3069.138908] NTFS driver 2.1.27 [Flags: R/O MODULE].
[ 3070.602439] JFS: nTxBlock = 8014, nTxLock = 64116
[ 3527.633626] lgdt330x: lgdt3303_read_snr: Modulation set to unsupported value
[ 3527.633750] lgdt330x: lgdt3303_read_snr: Modulation set to unsupported value
[ 3542.867905] cx88[0]: irq mpeg  [0x100000] ts_err?*
[ 3542.867911] cx88[0]/2-mpeg: general errors: 0x00100000
```

```
------------lsmod-------------
Module                  Size  Used by
jfs                   205392  0 
reiserfs              283648  0 
ext2                   83728  0 
hfs                    65288  0 
hfsplus                93832  0 
ntfs                  109128  0 
vfat                   17920  0 
fat                    65456  1 vfat
isofs                  43236  0 
udf                    97288  0 
lgdt330x               11908  1 
cx88_dvb               21252  48 
cx88_vp3054_i2c         7040  1 cx88_dvb
cx8802                 22916  1 cx88_dvb
dvb_pll                18308  1 cx88_dvb
video_buf_dvb           8708  1 cx88_dvb
dvb_core              102320  2 lgdt330x,video_buf_dvb
xfs                   648904  1 
binfmt_misc            16012  1 
rfcomm                 51360  0 
l2cap                  31744  5 rfcomm
bluetooth              64644  4 rfcomm,l2cap
cpufreq_userspace       6560  0 
cpufreq_stats           9312  0 
freq_table              7104  1 cpufreq_stats
cpufreq_powersave       3456  0 
cpufreq_ondemand       10928  0 
cpufreq_conservative    11272  0 
video                  22920  0 
tc1100_wmi             10632  0 
sony_acpi               7704  0 
sbs                    20928  0 
pcc_acpi               19968  0 
i2c_ec                  7808  1 sbs
hotkey                 14536  0 
dev_acpi               17540  0 
container               6656  0 
button                  9888  0 
battery                14088  0 
asus_acpi              21924  0 
ac                      8328  0 
ipv6                  334432  15 
dm_mod                 77776  3 
md_mod                 96156  0 
sbp2                   29448  0 
lp                     16584  0 
snd_emu10k1_synth      11008  0 
snd_emux_synth         50176  1 snd_emu10k1_synth
snd_seq_virmidi        10624  1 snd_emux_synth
snd_seq_midi_emul      10112  1 snd_emux_synth
snd_seq_dummy           6020  0 
snd_seq_oss            45824  0 
snd_seq_midi           12160  0 
snd_seq_midi_event     11520  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                77344  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
af_packet              29452  2 
usb_storage            89792  0 
usbhid                 51360  2 
libusual               21544  1 usb_storage
tsdev                  11136  0 
usblp                  18176  0 
sg                     44584  0 
snd_emu10k1           152480  1 snd_emu10k1_synth
tuner                  70184  0 
nvidia               5444468  12 
serio_raw              10244  0 
evdev                  14592  1 
i2c_viapro             11928  0 
snd_via82xx_modem      20364  0 
snd_pcm_oss            57344  0 
snd_mixer_oss          22784  1 snd_pcm_oss
cx88_alsa              17928  1 
snd_via82xx            36520  0 
snd_ac97_codec        127064  3 snd_emu10k1,snd_via82xx_modem,snd_via82xx
snd_ac97_bus            4352  1 snd_ac97_codec
snd_mpu401             12200  0 
snd_mpu401_uart        12928  2 snd_via82xx,snd_mpu401
pcspkr                  5248  0 
analog                 14048  0 
sk98lin               212572  0 
parport_pc             43560  1 
parport                49932  2 lp,parport_pc
cx88xx                 76964  3 cx88_dvb,cx8802,cx88_alsa
snd_util_mem            7552  2 snd_emux_synth,snd_emu10k1
ir_common              33924  1 cx88xx
snd_rawmidi            34432  4 snd_seq_virmidi,snd_seq_midi,snd_emu10k1,snd_mpu401_uart
snd_seq_device         12180  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
floppy                 76648  0 
psmouse                51088  0 
sata_sil24             16260  1 
i2c_algo_bit           11784  2 cx88_vp3054_i2c,cx88xx
sky2                   50436  0 
tveeprom               19600  1 cx88xx
videodev               29696  1 cx88xx
v4l1_compat            14852  1 videodev
i2c_core               29312  10 lgdt330x,cx88_dvb,dvb_pll,i2c_ec,tuner,nvidia,i2c_viapro,cx88xx,i2c_algo_bit,tveeprom
snd_pcm               108168  6 snd_emu10k1,snd_via82xx_modem,snd_pcm_oss,cx88_alsa,snd_via82xx,snd_ac97_codec
snd_timer              31112  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         13200  4 snd_emu10k1,snd_via82xx_modem,snd_via82xx,snd_pcm
snd_hwdep              14088  2 snd_emux_synth,snd_emu10k1
snd                    79016  20 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_via82xx_modem,snd_pcm_oss,snd_mixer_oss,cx88_alsa,snd_via82xx,snd_ac97_codec,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer,snd_hwdep
soundcore              14112  1 snd
emu10k1_gp              6016  0 
gameport               21008  4 snd_via82xx,analog,emu10k1_gp
btcx_risc               6920  3 cx8802,cx88_alsa,cx88xx
v4l2_common            28160  2 tuner,videodev
video_buf              32004  5 cx88_dvb,cx8802,video_buf_dvb,cx88_alsa,cx88xx
shpchp                 49068  0 
pci_hotplug            38912  1 shpchp
ext3                  164624  3 
jbd                    74024  1 ext3
ehci_hcd               40456  0 
uhci_hcd               30096  0 
usbcore               167840  9 usb_storage,usbhid,libusual,usblp,ehci_hcd,uhci_hcd
ohci1394               40776  0 
ieee1394              387704  2 sbp2,ohci1394
ide_generic             2944  0 
ide_cd                 39584  0 
cdrom                  43816  1 ide_cd
via82cxxx              11780  0 [permanent]
sd_mod                 25728  9 
generic                 7428  0 
sata_via               12548  5 
libata                 88984  2 sata_sil24,sata_via
scsi_mod              181424  5 sbp2,usb_storage,sg,sd_mod,libata
thermal                19472  0 
processor              38280  1 thermal
fan                     7432  0 
vesafb                 11048  0 
capability              7304  0 
commoncap              10752  1 capability
vga16fb                16656  1 
cfbcopyarea             5376  2 vesafb,vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4352  2 vesafb,vga16fb
cfbfillrect             6272  2 vesafb,vga16fb
fbcon                  45824  72 
tileblit                4736  1 fbcon
font                   10240  1 fbcon
bitblit                 8064  1 fbcon
softcursor              3968  1 bitblit
```

---

### Post by superm1 on 2006-11-07
Sounds to me like you need to rebuild the ivtv modules.  Remove anything from /lib/modules/2.6.17-* that was installed by a ivtv installer or such.

Follow these ivtv installation directions for edgy:
[https://wiki.ubuntu.com/Install_IVTV_Edgy](https://wiki.ubuntu.com/Install_IVTV_Edgy)

---

### Post by ralyon on 2006-11-15
Sorry, I haven't had a lot of time to work on it. The Edgy directions for ivtv worked fine on thier own. However, as soon as I installed the v4l-dvb drivers there was a conflict in the ivtv drivers. I got some help from mkrufky at the v4l irc channel. It seems to work, but I haven't had enough time to test it out completly. Here are the instruction if someone else wants to try them out.

**These instructions are for a v4l-dvb card with an ivtv* card.** (I have pcHDTV 5500 and Hauppauge PVR 150 MCE cards in my computer.)
* Note, This may not work with a Hauppauge 350.

Pre: Set up the build environment.

1. Install subversion
```
sudo apt-get install subversion
```

2. Go to [http://linuxtv.org/hg/v4l-dvb?cmd=tags;style=gitweb](http://linuxtv.org/hg/v4l-dvb?cmd=tags;style=gitweb) and click on "tree" to the right of "tip"

3. Click on "gz" or "bz2" near the top to download the drivers.

4. Extract the drivers then copy the folder to /usr/src. (Rename the folder if you like. I will use v4l-dvb in my code examples)

5. Open terminal, add the ivtv drivers, compile and install.
```
make ivtv-up
make
sudo make install
```

6. Install the firmware
```
cd /lib/firmware/
sudo wget http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz
sudo tar zxvf firmware.tar.gz
sudo rm firmware.tar.gz
```

7. Reboot

8. Load the drivers for the v4l-dvb card. (In my case it was cx88-dvb for the pcHDTV 5500)
```
sudo modprobe -v 'drivername'
```

The drivers do not autoload for the v4l-dvb card so you have to start it up every time you reboot. I put a script in my init.d folder and set it to run in run level 5. If someone could provide some better info on how to do this I would be very grateful.

Good Luck

---

### Post by superm1 on 2006-11-17
Well an easier way to autoload modules is to put them /etc/modules.

My question here is this v4l-dvb support for the pcHDTV 5500.  Was support added after 2.6.17?  Is it included in feisty (2.6.19)?

---

### Post by ralyon on 2006-11-19
I don't have an /etc/modules. Is this supposed to be in edgy? 

Support for the 5500 was added as of kernel 2.6.18 so it should be in feisty. I had tried compiling 2.6.18 and the 5500 worked fine, but I ran into other problems.

---

### Post by superm1 on 2006-11-19
If you don't have /etc/modules, you can create it.  It is just a file listing modules that need to loaded on bootup that aren't detected by hotplug.

---

### Post by ralyon on 2006-11-20
I'll give that a try, thanks.

I also did a reinstall from scratch and I got both cards working fine with the directions I wrote. Looks like the problems I was having were Mythtv specific. I keep my home dirs on a seperate partition so I renamed the mythtv home dir and the .mythtv under my profile and then installed mythtv and it worked fine. Then I imported the tables with my recordings and into the mythtv database and got back the important stuff.

One issue I still have is that I don't know how to specify which name a device gets after a reboot (as rare as they are). On one boot the PVR and analog part of the pcHDTV were video0 and video1 respectively and the next they were switched. Was it something I did or is there a way to lock a device to a name?

I look forward to not needing to compile mythtv anymore though.

[praise]Thanks to all the great people out there, including superm1, for getting ubuntu up to date on mythtv and for creating the great docs that helped me get everything running and mkrufky on the v4l-dvb forum for getting both cards working.[/praise]

Edit: Also forgot to mention that I found out what was causing the original problem with the video glitches on the PVR-150. It was the teletext being enabled and disabling it got it working fine in dapper again. #-o

---

### Post by superm1 on 2006-11-21
Well if you are using /etc/modules, then that is the order that the cards should get modprobed.  So say you have a module called cx2448 or something like that.

If you /etc/modules contains:
```

ivtv
cx2448
```

Then you will always have /dev/video0 be your hauppauge based card, and that  cx2448 will always get /dev/video1

---

### Post by ralyon on 2006-11-21
Ok, but the hauppauge (ivtv) is hotplug and the pchdtv (cx88-dvb) is not? I've put the cx88-dvb in the modules file so when I get a chance I'll see if that will set the order. If not, would there be a problem with ivtv being hotplug and having it in the modules file?

---

### Post by superm1 on 2006-11-21
Even if the ivtv driver is hotplug, my understanding was that if you put it in /etc/modules, this will override that behavior and force the loading of the module.

---

