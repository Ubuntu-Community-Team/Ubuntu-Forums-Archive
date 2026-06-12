---
title: "Plantronics DSP-300 USB Headset on Kubuntu 6.10 not working ?!?!"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by mips on 2006-10-29
I cannot seem to get my Plantronics DSP-300 USB headset working in Kubuntu Edgy Eft 6.10. Please note that it worked in Dapper.

Has anyone got any advise for a fix ?

```
mips@obelix:~$ lsusb
Bus 001 Device 004: ID 047f:0ca1 Plantronics, Inc.
Bus 001 Device 003: ID 03f0:4b11 Hewlett-Packard
Bus 001 Device 006: ID 046d:c30e Logitech, Inc.
Bus 001 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 002: ID 046d:c510 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
```



```
mips@obelix:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000d0000000 - 00000000e0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5420
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f6fd0
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff3000
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff3040
[17179569.184000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff7bc0
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff7b40
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:15 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:90000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2010.511 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.412000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.412000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.432000] Memory: 1029764k/1048512k available (1910k kernel code, 17984k reserved, 1070k data, 308k init, 131008k highmem)
[17179572.432000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.512000] Calibrating delay using timer specific routine.. 4025.09 BogoMIPS (lpj=8050185)
[17179572.512000] Security Framework v1.0.0 initialized
[17179572.512000] SELinux:  Disabled at boot.
[17179572.512000] Mount-cache hash table entries: 512
[17179572.512000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000000 00000000 00000001
[17179572.512000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000000 00000000 00000001
[17179572.512000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.512000] CPU: L2 Cache: 512K (64 bytes/line)
[17179572.512000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000000 00000000 00000001
[17179572.512000] Checking 'hlt' instruction... OK.
[17179572.528000] SMP alternatives: switching to UP code
[17179572.528000] Freeing SMP alternatives: 16k freed
[17179572.528000] checking if image is initramfs... it is
[17179572.964000] Freeing initrd memory: 5215k freed
[17179572.964000] ACPI: Core revision 20060707
[17179572.964000] ACPI: Looking for DSDT ... not found!
[17179572.968000] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[17179572.968000] Total of 1 processors activated (4025.09 BogoMIPS).
[17179572.968000] ENABLING IO-APIC IRQs
[17179572.968000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179573.116000] Brought up 1 CPUs
[17179573.116000] migration_cost=0
[17179573.116000] NET: Registered protocol family 16
[17179573.116000] EISA bus registered
[17179573.116000] ACPI: bus type pci registered
[17179573.116000] PCI: Using MMCONFIG
[17179573.116000] PCI: No mmconfig possible on 0:18
[17179573.116000] Setting up standard PCI resources
[17179573.124000] ACPI: Interpreter enabled
[17179573.124000] ACPI: Using IOAPIC for interrupt routing
[17179573.124000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.124000] PCI: Probing PCI hardware (bus 00)
[17179573.128000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:06.0
[17179573.128000] PCI: Transparent bridge - 0000:00:09.0
[17179573.128000] Boot video device is 0000:05:00.0
[17179573.128000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.180000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179573.180000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179573.180000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179573.184000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179573.184000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179573.184000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179573.184000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179573.184000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179573.184000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179573.184000] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179573.184000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179573.184000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179573.184000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179573.184000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179573.184000] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179573.184000] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179573.184000] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179573.184000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[17179573.184000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[17179573.192000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.192000] pnp: PnP ACPI init
[17179573.196000] pnp: PnP ACPI: found 13 devices
[17179573.196000] PnPBIOS: Disabled by ACPI PNP
[17179573.196000] PCI: Using ACPI for IRQ routing
[17179573.196000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.196000] pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
[17179573.196000] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
[17179573.196000] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
[17179573.196000] pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
[17179573.196000] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
[17179573.196000] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
[17179573.196000] PCI: Bridge: 0000:00:09.0
[17179573.196000]   IO window: disabled.
[17179573.196000]   MEM window: f2000000-f20fffff
[17179573.196000]   PREFETCH window: disabled.
[17179573.196000] PCI: Bridge: 0000:00:0b.0
[17179573.196000]   IO window: 9000-9fff
[17179573.196000]   MEM window: f0000000-f1ffffff
[17179573.196000]   PREFETCH window: 50000000-500fffff
[17179573.196000] PCI: Bridge: 0000:00:0c.0
[17179573.196000]   IO window: 8000-8fff
[17179573.196000]   MEM window: disabled.
[17179573.196000]   PREFETCH window: disabled.
[17179573.196000] PCI: Bridge: 0000:00:0d.0
[17179573.196000]   IO window: 7000-7fff
[17179573.196000]   MEM window: disabled.
[17179573.196000]   PREFETCH window: disabled.
[17179573.196000] PCI: Bridge: 0000:00:0e.0
[17179573.196000]   IO window: disabled.
[17179573.196000]   MEM window: e0000000-efffffff
[17179573.196000]   PREFETCH window: 50100000-501fffff
[17179573.196000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[17179573.196000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179573.196000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179573.196000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179573.196000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179573.196000] NET: Registered protocol family 2
[17179573.236000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.236000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179573.236000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179573.236000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.236000] TCP reno registered
[17179573.236000] audit: initializing netlink socket (disabled)
[17179573.236000] audit(1162158183.236:1): initialized
[17179573.236000] highmem bounce pool size: 64 pages
[17179573.236000] VFS: Disk quotas dquot_6.5.1
[17179573.236000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.236000] Initializing Cryptographic API
[17179573.236000] io scheduler noop registered
[17179573.236000] io scheduler anticipatory registered
[17179573.236000] io scheduler deadline registered
[17179573.236000] io scheduler cfq registered (default)
[17179573.236000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179573.236000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179573.236000] assign_interrupt_mode Found MSI capability
[17179573.236000] Allocate Port Service[0000:00:0b.0:pcie00]
[17179573.236000] Allocate Port Service[0000:00:0b.0:pcie03]
[17179573.236000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179573.236000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179573.236000] assign_interrupt_mode Found MSI capability
[17179573.236000] Allocate Port Service[0000:00:0c.0:pcie00]
[17179573.236000] Allocate Port Service[0000:00:0c.0:pcie03]
[17179573.236000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179573.236000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179573.236000] assign_interrupt_mode Found MSI capability
[17179573.236000] Allocate Port Service[0000:00:0d.0:pcie00]
[17179573.236000] Allocate Port Service[0000:00:0d.0:pcie03]
[17179573.236000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179573.236000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179573.236000] assign_interrupt_mode Found MSI capability
[17179573.236000] Allocate Port Service[0000:00:0e.0:pcie00]
[17179573.236000] Allocate Port Service[0000:00:0e.0:pcie03]
[17179573.236000] isapnp: Scanning for PnP cards...
[17179573.592000] isapnp: No Plug & Play device found
[17179573.608000] Real Time Clock Driver v1.12ac
[17179573.608000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.608000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.608000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.608000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.608000] mice: PS/2 mouse device common for all mice
[17179573.608000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.608000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.608000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.608000] PNP: No PS/2 controller found. Probing ports directly.
[17179574.136000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.144000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.144000] EISA: Probing bus 0 at eisa.0
[17179574.144000] Cannot allocate resource for EISA slot 1
[17179574.144000] Cannot allocate resource for EISA slot 7
[17179574.144000] Cannot allocate resource for EISA slot 8
[17179574.144000] EISA: Detected 0 cards.
[17179574.144000] TCP bic registered
[17179574.144000] NET: Registered protocol family 1
[17179574.144000] NET: Registered protocol family 8
[17179574.144000] NET: Registered protocol family 20
[17179574.144000] Using IPI No-Shortcut mode
[17179574.144000] ACPI: (supports S0 S1 S4 S5)
[17179574.144000] Freeing unused kernel memory: 308k freed
[17179574.792000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.868000] Capability LSM initialized
[17179575.904000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179576.268000] SCSI subsystem initialized
[17179576.272000] libata version 1.20 loaded.
[17179576.276000] sata_nv 0000:00:07.0: version 0.8
[17179576.276000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[17179576.276000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 217
[17179576.276000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179576.276000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xC800 irq 217
[17179576.276000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xC808 irq 217
[17179576.480000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179576.656000] ata1: dev 0 cfg 49:2f00 82:346b 83:7f21 84:4003 85:3468 86:3c01 87:4003 88:203f
[17179576.656000] ata1: dev 0 ATA-6, max UDMA/100, 312581808 sectors: LBA48
[17179576.656000] nv_sata: Primary device added
[17179576.656000] nv_sata: Primary device removed
[17179576.656000] nv_sata: Secondary device added
[17179576.656000] nv_sata: Secondary device removed
[17179576.668000] ata1: dev 0 configured for UDMA/100
[17179576.668000] scsi0 : sata_nv
[17179576.876000] ata2: SATA link up 1.5 Gbps (SStatus 113)
[17179577.048000] ata2: dev 0 cfg 49:2f00 82:346b 83:7f21 84:4003 85:3468 86:3c01 87:4003 88:203f
[17179577.048000] ata2: dev 0 ATA-6, max UDMA/100, 312581808 sectors: LBA48
[17179577.048000] ata2(0): applying bridge limits
[17179577.048000] nv_sata: Primary device added
[17179577.048000] nv_sata: Primary device removed
[17179577.048000] nv_sata: Secondary device added
[17179577.048000] nv_sata: Secondary device removed
[17179577.060000] ata2: dev 0 configured for UDMA/100
[17179577.060000] scsi1 : sata_nv
[17179577.060000]   Vendor: ATA       Model: WDC WD1600JD-40G  Rev: 09.0
[17179577.060000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179577.064000]   Vendor: ATA       Model: WDC WD1600JD-00G  Rev: 02.0
[17179577.064000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179577.064000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[17179577.064000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 225
[17179577.064000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179577.064000] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xDC00 irq 225
[17179577.064000] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xDC08 irq 225
[17179577.068000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179577.068000] sda: Write Protect is off
[17179577.068000] sda: Mode Sense: 00 3a 00 00
[17179577.068000] SCSI device sda: drive cache: write back
[17179577.068000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179577.068000] sda: Write Protect is off
[17179577.068000] sda: Mode Sense: 00 3a 00 00
[17179577.068000] SCSI device sda: drive cache: write back
[17179577.068000]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[17179577.120000] sd 0:0:0:0: Attached scsi disk sda
[17179577.124000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[17179577.124000] sdb: Write Protect is off
[17179577.124000] sdb: Mode Sense: 00 3a 00 00
[17179577.124000] SCSI device sdb: drive cache: write back
[17179577.124000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[17179577.124000] sdb: Write Protect is off
[17179577.124000] sdb: Mode Sense: 00 3a 00 00
[17179577.124000] SCSI device sdb: drive cache: write back
[17179577.124000]  sdb: sdb1 sdb2 sdb3
[17179577.144000] sd 1:0:0:0: Attached scsi disk sdb
[17179577.268000] ata3: SATA link down (SStatus 0)
[17179577.268000] scsi2 : sata_nv
[17179577.476000] ata4: SATA link down (SStatus 0)
[17179577.476000] scsi3 : sata_nv
[17179577.480000] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[17179577.480000] NFORCE-CK804: chipset revision 162
[17179577.480000] NFORCE-CK804: not 100% native mode: will probe irqs later
[17179577.480000] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[17179577.480000] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[17179577.480000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[17179577.480000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[17179577.480000] Probing IDE interface ide0...
[17179578.224000] hda: SONY DVD RW DRU-720A, ATAPI CD/DVD-ROM drive
[17179578.900000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179578.900000] Probing IDE interface ide1...
[17179579.480000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[17179579.480000] Uniform CD-ROM driver Revision: 3.20
[17179579.652000] Probing IDE interface ide1...
[17179579.684000] usbcore: registered new driver usbfs
[17179579.684000] usbcore: registered new driver hub
[17179579.684000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179579.684000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[17179579.684000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 233
[17179579.684000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179579.684000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179579.684000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179579.732000] ohci_hcd 0000:00:02.0: irq 233, io mem 0xf2103000
[17179579.744000] ieee1394: Initialized config rom entry `ip1394'
[17179579.752000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179579.792000] usb usb1: configuration #1 chosen from 1 choice
[17179579.792000] hub 1-0:1.0: USB hub found
[17179579.792000] hub 1-0:1.0: 10 ports detected
[17179579.900000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179579.900000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 50
[17179579.900000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179579.900000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[17179579.900000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179579.900000] ehci_hcd 0000:00:02.1: debug port 1
[17179579.900000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[17179579.900000] ehci_hcd 0000:00:02.1: irq 50, io mem 0xf2105000
[17179579.900000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.900000] usb usb2: configuration #1 chosen from 1 choice
[17179579.900000] hub 2-0:1.0: USB hub found
[17179579.900000] hub 2-0:1.0: 10 ports detected
[17179580.008000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[17179580.008000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 217
[17179580.008000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[17179580.008000] forcedeth: using HIGHDMA
[17179580.532000] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:0a.0
[17179580.532000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179580.532000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 58
[17179580.580000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[58]  MMIO=[f2004000-f20047ff]  Max Packet=[4096]  IR/IT contexts=[4/8]
[17179580.648000] Attempting manual resume
[17179580.656000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179580.656000] SGI XFS Quota Management subsystem
[17179580.656000] XFS mounting filesystem sda2
[17179580.740000] Starting XFS recovery on filesystem: sda2 (logdev: internal)
[17179581.532000] ohci_hcd 0000:00:02.0: wakeup
[17179581.848000] Ending XFS recovery on filesystem: sda2 (logdev: internal)
[17179581.860000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea56007631c2]
[17179581.920000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[17179582.128000] usb 1-1: configuration #1 chosen from 1 choice
[17179582.436000] usb 1-4: new full speed USB device using ohci_hcd and address 3
[17179582.656000] usb 1-4: configuration #1 chosen from 1 choice
[17179582.960000] usb 1-7: new full speed USB device using ohci_hcd and address 4
[17179583.172000] usb 1-7: configuration #1 chosen from 1 choice
[17179583.480000] usb 1-9: new full speed USB device using ohci_hcd and address 5
[17179583.712000] usb 1-9: configuration #1 chosen from 1 choice
[17179584.020000] usb 1-10: new low speed USB device using ohci_hcd and address 6
[17179584.264000] usb 1-10: configuration #1 chosen from 1 choice
[17179596.524000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179596.528000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179596.528000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[17179596.528000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[17179596.616000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[17179596.616000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 66
[17179596.616000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179596.616000] sky2 v1.6.1 addr 0xf1000000 irq 66 Yukon-EC (0xb6) rev 1
[17179596.616000] sky2 eth1: addr 00:0f:ea:74:27:e7
[17179596.908000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[17179596.908000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 225
[17179596.908000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179597.220000] irda_init()
[17179597.220000] NET: Registered protocol family 23
[17179597.324000] intel8x0_measure_ac97_clock: measured 105522 usecs
[17179597.324000] intel8x0: clocking to 47411
[17179597.356000] parport: PnPBIOS parport detected.
[17179597.356000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179597.356000] input: PC Speaker as /class/input/input1
[17179597.364000] Floppy drive(s): fd0 is 1.44M
[17179597.588000] FDC 0 is a post-1991 82077
[17179597.716000] usbcore: registered new driver hiddev
[17179597.968000] input: Logitech USB Receiver as /class/input/input2
[17179597.968000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-1
[17179598.024000] Linux agpgart interface v0.101 (c) Dave Jones
[17179598.036000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179598.036000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[17179598.092000] Bluetooth: Core ver 2.8
[17179598.092000] NET: Registered protocol family 31
[17179598.092000] Bluetooth: HCI device and connection manager initialized
[17179598.092000] Bluetooth: HCI socket layer initialized
[17179598.092000] Bluetooth: HCI USB driver ver 2.9
[17179598.160000] nvidia: module license 'NVIDIA' taints kernel.
[17179598.168000] input: Plantronics Plantronics Headset as /class/input/input3
[17179598.168000] input: USB HID v1.00 Device [Plantronics Plantronics Headset] on usb-0000:00:02.0-7
[17179598.168000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 58
[17179598.168000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[17179598.168000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179598.788000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4B11
[17179598.804000] input: Logitech HID compliant keyboard as /class/input/input4
[17179598.804000] input: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:00:02.0-10
[17179598.832000] input: Logitech HID compliant keyboard as /class/input/input5
[17179598.832000] input: USB HID v1.10 Device [Logitech HID compliant keyboard] on usb-0000:00:02.0-10
[17179598.832000] usbcore: registered new driver usbhid
[17179598.832000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179598.832000] usbcore: registered new driver hci_usb
[17179598.916000] ts: Compaq touchscreen protocol output
[17179598.932000] usbcore: registered new driver usblp
[17179598.932000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179598.932000] usbcore: registered new driver snd-usb-audio
[17179599.356000] lp0: using parport0 (interrupt-driven).
[17179599.368000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179599.368000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179599.392000] Adding 1951856k swap on /dev/disk/by-uuid/72027f69-2830-4048-9082-4962bf56ffd8.  Priority:-1 extents:1 across:1951856k
[17179599.940000] kjournald starting.  Commit interval 5 seconds
[17179599.952000] EXT3 FS on sda4, internal journal
[17179599.952000] EXT3-fs: mounted filesystem with ordered data mode.
[17179600.052000] XFS mounting filesystem sda6
[17179600.196000] Ending clean XFS mount for filesystem: sda6
[17179600.260000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179600.320000] NTFS volume version 3.1.
[17179600.404000] XFS mounting filesystem sda5
[17179600.508000] Ending clean XFS mount for filesystem: sda5
[17179600.544000] XFS mounting filesystem sdb2
[17179600.676000] Ending clean XFS mount for filesystem: sdb2
[17179600.752000] XFS mounting filesystem sdb3
[17179600.884000] Ending clean XFS mount for filesystem: sdb3
[17179601.700000] ACPI: Power Button (FF) [PWRF]
[17179601.700000] ACPI: Power Button (CM) [PWRB]
[17179601.800000] ibm_acpi: ec object not found
[17179601.824000] pcc_acpi: loading...
[17179602.100000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179602.100000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6 (1400 mV)
[17179602.100000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x8 (1350 mV)
[17179602.100000] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[17179602.100000] cpu_init done, current fid 0xc, vid 0x6
[17179604.244000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179604.244000] apm: overridden by ACPI.
[17179609.912000] Bluetooth: L2CAP ver 2.8
[17179609.912000] Bluetooth: L2CAP socket layer initialized
[17179609.924000] Bluetooth: RFCOMM socket layer initialized
[17179609.924000] Bluetooth: RFCOMM TTY layer initialized
[17179609.924000] Bluetooth: RFCOMM ver 1.7
```

---

### Post by mips on 2006-10-29
Quick bump before I go to sleep.

---

### Post by mips on 2006-10-30
bump

---

### Post by alliera on 2006-11-03
this worked for me:

[http://techarena.co.uk/?q=node/18](http://techarena.co.uk/?q=node/18)

you'll probably have to restart kmix (or whatever you're using to control audio) to see the second interface or use alsamixer.

---

### Post by mips on 2006-11-07
Thanks but my snd_usb_audio device already =0

Any other ideas ?

```
mips@obelix:~$ more /proc/asound/cards
 0 [Headset        ]: USB-Audio - Plantronics Headset
                      Plantronics Plantronics Headset at usb-0000:00:02.0-7, full speed
 1 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at 0xf2106000, irq 225
mips@obelix:~$ cat /proc/asound/modules
 0 snd_usb_audio
 1 snd_intel8x0
```

---

### Post by hppyfngy on 2007-02-19
I set my headset to the default audio device by following these instructions:

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_change_default_soundcard](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_change_default_soundcard)

But I have to now use alsamixer to control volume...

---

