---
title: "TV-card doesn't work"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by jeroen6bis on 2006-11-04
I'm trying to install MythTV with [this manual]("http://parker1.co.uk/mythtv_ubuntu.php"), but it seems like My Pinnacle PCTV 40i isn't recognized.

This is what I get when I type **lspci**:
```

00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01df (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
04:02.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
04:06.0 Mass storage controller: <pci_lookup_name: buffer too small> (rev 13)

```

And when I type **dmesg**, I get:
```

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5080
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f69f0
[17179569.184000] ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff3040
[17179569.184000] ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff30c0
[17179569.184000] ACPI: MCFG (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff6bc0
[17179569.184000] ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff6b00
[17179569.184000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:6 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:6 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 3015.154 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.580000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.580000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.600000] Memory: 1029508k/1048512k available (1910k kernel code, 18368k reserved, 1070k data, 308k init, 131008k highmem)
[17179569.600000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.680000] Calibrating delay using timer specific routine.. 6036.92 BogoMIPS (lpj=12073853)
[17179569.680000] Security Framework v1.0.0 initialized
[17179569.680000] SELinux:  Disabled at boot.
[17179569.680000] Mount-cache hash table entries: 512
[17179569.680000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e43d 00000000 00000001
[17179569.680000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e43d 00000000 00000001
[17179569.680000] monitor/mwait feature present.
[17179569.680000] using mwait in idle threads.
[17179569.680000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.680000] CPU: L2 cache: 2048K
[17179569.680000] CPU: Hyper-Threading is disabled
[17179569.680000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000e43d 00000000 00000001
[17179569.680000] Checking 'hlt' instruction... OK.
[17179569.696000] SMP alternatives: switching to UP code
[17179569.696000] checking if image is initramfs... it is
[17179570.136000] Freeing initrd memory: 5564k freed
[17179570.136000] ACPI: Core revision 20060707
[17179570.140000] ACPI: Looking for DSDT ... not found!
[17179570.144000] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 02
[17179570.144000] SMP alternatives: switching to SMP code
[17179570.144000] Booting processor 1/1 eip 3000
[17179570.152000] Initializing CPU#1
[17179570.236000] Calibrating delay using timer specific routine.. 6029.57 BogoMIPS (lpj=12059149)
[17179570.236000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e43d 00000000 00000001
[17179570.236000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e43d 00000000 00000001
[17179570.236000] monitor/mwait feature present.
[17179570.236000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179570.236000] CPU: L2 cache: 2048K
[17179570.236000] CPU: Hyper-Threading is disabled
[17179570.236000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000e43d 00000000 00000001
[17179570.236000] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 02
[17179570.236000] Total of 2 processors activated (12066.50 BogoMIPS).
[17179570.236000] ENABLING IO-APIC IRQs
[17179570.236000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.380000] checking TSC synchronization across 2 CPUs: passed.
[17179570.384000] Brought up 2 CPUs
[17179570.460000] migration_cost=4000
[17179570.460000] NET: Registered protocol family 16
[17179570.460000] EISA bus registered
[17179570.460000] ACPI: bus type pci registered
[17179570.460000] PCI: Using MMCONFIG
[17179570.460000] Setting up standard PCI resources
[17179570.472000] ACPI: Interpreter enabled
[17179570.472000] ACPI: Using IOAPIC for interrupt routing
[17179570.476000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.476000] PCI: Probing PCI hardware (bus 00)
[17179570.476000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.476000] Boot video device is 0000:01:00.0
[17179570.476000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.476000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.488000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[17179570.488000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[17179570.492000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.492000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179570.492000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179570.496000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179570.496000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.496000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.496000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179570.496000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[17179570.496000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.496000] pnp: PnP ACPI init
[17179570.500000] pnp: PnP ACPI: found 14 devices
[17179570.500000] PnPBIOS: Disabled by ACPI PNP
[17179570.500000] PCI: Using ACPI for IRQ routing
[17179570.500000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.500000] pnp: 00:0a: ioport range 0x400-0x4bf could not be reserved
[17179570.500000] PCI: Bridge: 0000:00:01.0
[17179570.500000]   IO window: disabled.
[17179570.500000]   MEM window: e0000000-e2ffffff
[17179570.500000]   PREFETCH window: d0000000-dfffffff
[17179570.500000] PCI: Bridge: 0000:00:1c.0
[17179570.500000]   IO window: 8000-8fff
[17179570.500000]   MEM window: disabled.
[17179570.500000]   PREFETCH window: disabled.
[17179570.500000] PCI: Bridge: 0000:00:1c.2
[17179570.500000]   IO window: disabled.
[17179570.500000]   MEM window: e5000000-e50fffff
[17179570.500000]   PREFETCH window: disabled.
[17179570.500000] PCI: Bridge: 0000:00:1e.0
[17179570.500000]   IO window: 9000-afff
[17179570.500000]   MEM window: e3000000-e4ffffff
[17179570.500000]   PREFETCH window: 50000000-500fffff
[17179570.500000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.500000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.500000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.500000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.500000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179570.500000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179570.500000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.500000] NET: Registered protocol family 2
[17179570.544000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.544000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179570.544000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.544000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.544000] TCP reno registered
[17179570.544000] audit: initializing netlink socket (disabled)
[17179570.544000] audit(1162651655.544:1): initialized
[17179570.544000] highmem bounce pool size: 64 pages
[17179570.544000] VFS: Disk quotas dquot_6.5.1
[17179570.544000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.544000] Initializing Cryptographic API
[17179570.544000] io scheduler noop registered
[17179570.544000] io scheduler anticipatory registered
[17179570.544000] io scheduler deadline registered
[17179570.544000] io scheduler cfq registered (default)
[17179570.544000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.544000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.544000] assign_interrupt_mode Found MSI capability
[17179570.544000] Allocate Port Service[0000:00:01.0:pcie00]
[17179570.544000] Allocate Port Service[0000:00:01.0:pcie03]
[17179570.544000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.544000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.544000] assign_interrupt_mode Found MSI capability
[17179570.544000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179570.544000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179570.544000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179570.544000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179570.544000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179570.544000] assign_interrupt_mode Found MSI capability
[17179570.544000] Allocate Port Service[0000:00:1c.2:pcie00]
[17179570.544000] Allocate Port Service[0000:00:1c.2:pcie02]
[17179570.544000] Allocate Port Service[0000:00:1c.2:pcie03]
[17179570.544000] isapnp: Scanning for PnP cards...
[17179570.896000] isapnp: No Plug & Play device found
[17179570.920000] Real Time Clock Driver v1.12ac
[17179570.920000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.920000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.920000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.924000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.924000] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.924000] mice: PS/2 mouse device common for all mice
[17179570.924000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.924000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.924000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.924000] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[17179570.924000] PNP: PS/2 controller doesn't have KBD irq; using default 1
[17179570.936000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.936000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.948000] EISA: Probing bus 0 at eisa.0
[17179570.948000] Cannot allocate resource for EISA slot 8
[17179570.948000] EISA: Detected 0 cards.
[17179570.948000] TCP bic registered
[17179570.948000] NET: Registered protocol family 1
[17179570.948000] NET: Registered protocol family 8
[17179570.948000] NET: Registered protocol family 20
[17179570.948000] Starting balanced_irq
[17179570.948000] Using IPI No-Shortcut mode
[17179570.948000] ACPI: (supports S0 S3 S4 S5)
[17179570.948000] Freeing unused kernel memory: 308k freed
[17179571.744000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.808000] Capability LSM initialized
[17179572.844000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179572.844000] ACPI: Processor [CPU1] (supports 2 throttling states)
[17179573.200000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179573.200000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
[17179573.200000] ICH7: chipset revision 1
[17179573.200000] ICH7: not 100% native mode: will probe irqs later
[17179573.200000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[17179573.200000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
[17179573.200000] Probing IDE interface ide0...
[17179573.492000] hda: WDC WD2500JB-00GVC0, ATA DISK drive
[17179573.776000] hdb: WDC WD2500JB-00GVC0, ATA DISK drive
[17179573.836000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.856000] Probing IDE interface ide1...
[17179574.432000] hda: max request size: 512KiB
[17179574.432000] hda: Host Protected Area detected.
[17179574.432000]       current capacity is 488395055 sectors (250058 MB)
[17179574.432000]       native  capacity is 488397168 sectors (250059 MB)
[17179574.436000] hda: Host Protected Area disabled.
[17179574.436000] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[17179574.436000] hda: cache flushes supported
[17179574.436000]  hda: hda1 hda2
[17179574.452000] hdb: max request size: 512KiB
[17179574.452000] hdb: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[17179574.456000] hdb: cache flushes supported
[17179574.456000]  hdb: hdb1 hdb2 < hdb5 >
[17179574.868000] SCSI subsystem initialized
[17179574.872000] libata version 1.20 loaded.
[17179574.872000] ata_piix 0000:00:1f.2: version 1.05
[17179574.872000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 217
[17179574.872000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179574.872000] ata1: SATA max UDMA/133 cmd 0xD000 ctl 0xD402 bmdma 0xE000 irq 217
[17179574.872000] ata2: SATA max UDMA/133 cmd 0xD800 ctl 0xDC02 bmdma 0xE008 irq 217
[17179575.040000] ata1: disabling port
[17179575.040000] scsi0 : ata_piix
[17179575.208000] ata2: disabling port
[17179575.208000] scsi1 : ata_piix
[17179575.256000] IT8212: IDE controller at PCI slot 0000:04:06.0
[17179575.256000] ACPI: PCI Interrupt 0000:04:06.0[A] -> GSI 22 (level, low) -> IRQ 225
[17179575.256000] IT8212: chipset revision 19
[17179575.256000] it821x: controller in pass through mode.
[17179575.256000] IT8212: 100% native mode on irq 225
[17179575.256000]     ide2: BM-DMA at 0xa000-0xa007, BIOS settings: hde:pio, hdf:pio
[17179575.256000]     ide3: BM-DMA at 0xa008-0xa00f, BIOS settings: hdg:pio, hdh:pio
[17179575.256000] Probing IDE interface ide2...
[17179576.000000] hde: HL-DT-ST DVDRAM GSA-4167B, ATAPI CD/DVD-ROM drive
[17179576.340000] ide2 at 0x9010-0x9017,0x9402 on irq 225
[17179576.340000] Probing IDE interface ide3...
[17179576.920000] hde: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[17179576.920000] Uniform CD-ROM driver Revision: 3.20
[17179576.992000] Probing IDE interface ide1...
[17179577.024000] usbcore: registered new driver usbfs
[17179577.024000] usbcore: registered new driver hub
[17179577.024000] USB Universal Host Controller Interface driver v3.0
[17179577.024000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 233
[17179577.024000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.024000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.024000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.024000] uhci_hcd 0000:00:1d.0: irq 233, io base 0x0000bc00
[17179577.024000] usb usb1: configuration #1 chosen from 1 choice
[17179577.024000] hub 1-0:1.0: USB hub found
[17179577.024000] hub 1-0:1.0: 2 ports detected
[17179577.132000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 217
[17179577.132000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.132000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.132000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.132000] uhci_hcd 0000:00:1d.1: irq 217, io base 0x0000b000
[17179577.132000] usb usb2: configuration #1 chosen from 1 choice
[17179577.132000] hub 2-0:1.0: USB hub found
[17179577.132000] hub 2-0:1.0: 2 ports detected
[17179577.240000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179577.240000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.240000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.240000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179577.240000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x0000b400
[17179577.240000] usb usb3: configuration #1 chosen from 1 choice
[17179577.240000] hub 3-0:1.0: USB hub found
[17179577.240000] hub 3-0:1.0: 2 ports detected
[17179577.348000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179577.348000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179577.348000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179577.348000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179577.348000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000b800
[17179577.348000] usb usb4: configuration #1 chosen from 1 choice
[17179577.348000] hub 4-0:1.0: USB hub found
[17179577.348000] hub 4-0:1.0: 2 ports detected
[17179577.456000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 233
[17179577.456000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.456000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.456000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179577.456000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179577.456000] ehci_hcd 0000:00:1d.7: irq 233, io mem 0xe5104000
[17179577.460000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.460000] usb usb5: configuration #1 chosen from 1 choice
[17179577.460000] hub 5-0:1.0: USB hub found
[17179577.460000] hub 5-0:1.0: 8 ports detected
[17179577.480000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179577.560000] Probing IDE interface ide3...
[17179578.160000] Attempting manual resume
[17179578.224000] kjournald starting.  Commit interval 5 seconds
[17179578.224000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.308000] usb 5-3: new high speed USB device using ehci_hcd and address 2
[17179578.464000] usb 5-3: configuration #1 chosen from 1 choice
[17179579.448000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[17179579.652000] usb 3-1: configuration #1 chosen from 1 choice
[17179579.896000] usb 3-2: new full speed USB device using uhci_hcd and address 3
[17179580.156000] usb 3-2: configuration #1 chosen from 1 choice
[17179580.400000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[17179580.592000] usb 4-1: configuration #1 chosen from 1 choice
[17179580.836000] usb 4-2: new low speed USB device using uhci_hcd and address 3
[17179581.020000] usb 4-2: configuration #1 chosen from 1 choice
[17179588.304000] Linux video capture interface: v1.00
[17179588.416000] input: PC Speaker as /class/input/input1
[17179588.492000] parport: PnPBIOS parport detected.
[17179588.492000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179588.568000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179588.644000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.660000] agpgart: Detected an Intel 945G Chipset.
[17179588.676000] agpgart: AGP aperture is 256M @ 0x0
[17179588.728000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.756000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.908000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179588.908000] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 18 (level, low) -> IRQ 177
[17179588.908000] saa7133[0]: found at 0000:04:02.0, rev: 208, irq: 177, latency: 32, mmio: 0xe4000000
[17179588.908000] saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV 40i/50i/110i (saa7133) [card=77,autodetected]
[17179588.908000] saa7133[0]: board init: gpio is 200c000
[17179589.036000] input: Pinnacle PCTV as /class/input/input3
[17179589.036000] ir-kbd-i2c: Pinnacle PCTV detected at i2c-0/0-0047/ir0 [saa7133[0]]
[17179589.088000] saa7133[0]: i2c eeprom 00: bd 11 2e 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179589.088000] saa7133[0]: i2c eeprom 10: ff e0 60 02 ff 20 ff ff ff ff ff ff ff ff ff ff
[17179589.088000] saa7133[0]: i2c eeprom 20: 01 2c 01 02 02 01 04 30 98 ff 00 a0 ff 22 00 c2
[17179589.088000] saa7133[0]: i2c eeprom 30: 96 ff 03 30 15 01 ff ff 0c 22 17 87 03 48 d8 65
[17179589.088000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179589.088000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179589.088000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179589.088000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179589.104000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.104000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179589.132000] usbcore: registered new driver hiddev
[17179589.148000] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input4
[17179589.148000] input: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.3-1
[17179589.168000] nvidia: module license 'NVIDIA' taints kernel.
[17179589.172000] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input5
[17179589.172000] input: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.3-1
[17179589.188000] ts: Compaq touchscreen protocol output
[17179589.192000] input: Logitech USB Trackball as /class/input/input6
[17179589.192000] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:1d.3-2
[17179589.192000] usbcore: registered new driver usbhid
[17179589.192000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.256000] drivers/media/video/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Type Vimicro Zc301P 0x301b
[17179589.352000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[17179589.416000] tuner 0-004b: setting tuner address to 61
[17179589.464000] tuner 0-004b: type set to tda8290+75a
[17179589.544000] usbcore: registered new driver spca5xx
[17179589.544000] drivers/media/video/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[17179589.548000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4911
[17179589.548000] usbcore: registered new driver usblp
[17179589.548000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179589.548000] usbcore: registered new driver libusual
[17179589.556000] saa7133[0]: registered device video1 [v4l2]
[17179589.556000] saa7133[0]: registered device vbi0
[17179589.556000] saa7133[0]: registered device radio0
[17179589.564000] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[17179589.568000] Initializing USB Mass Storage driver...
[17179589.568000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179589.572000] usb-storage: device found at 2
[17179589.572000] usb-storage: waiting for device to settle before scanning
[17179589.572000] scsi3 : SCSI emulation for USB Mass Storage devices
[17179589.572000] usb-storage: device found at 3
[17179589.572000] usb-storage: waiting for device to settle before scanning
[17179589.572000] usbcore: registered new driver usb-storage
[17179589.572000] USB Mass Storage support registered.
[17179589.580000] saa7134 ALSA driver for DMA sound loaded
[17179589.580000] saa7133[0]/alsa: saa7133[0] at 0xe4000000 irq 177 registered as card -1
[17179589.628000] hw_random hardware driver 1.0.0 loaded
[17179589.816000] tg3.c:v3.59.1 (August 25, 2006)
[17179589.816000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 177
[17179589.816000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179589.852000] eth0: Tigon3 [partno(BCM95789) rev 4101 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:14:85:c3:e4:e9
[17179589.852000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[17179589.852000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[17179589.852000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.852000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179589.852000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179590.196000] lp0: using parport0 (interrupt-driven).
[17179590.224000] Adding 3028212k swap on /dev/disk/by-uuid/1ee85bdb-a620-4af5-8c7a-2bf68c1f2693.  Priority:-1 extents:1 across:3028212k
[17179590.272000] EXT3 FS on hdb1, internal journal
[17179591.140000] NET: Registered protocol family 17
[17179591.736000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[17179591.736000] tg3: eth0: Flow control is on for TX and on for RX.
[17179594.576000] usb-storage: device scan complete
[17179594.576000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9317
[17179594.576000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179594.576000] usb-storage: device scan complete
[17179594.576000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9317
[17179594.576000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179594.576000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9317
[17179594.576000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179594.576000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9317
[17179594.576000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179594.580000]   Vendor: HP        Model: PSC 2355          Rev: 1.00
[17179594.580000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179594.608000] sd 2:0:0:0: Attached scsi removable disk sda
[17179594.616000] sd 2:0:0:1: Attached scsi removable disk sdb
[17179594.616000] sd 2:0:0:2: Attached scsi removable disk sdc
[17179594.624000] sd 2:0:0:3: Attached scsi removable disk sdd
[17179594.640000] sd 3:0:0:0: Attached scsi removable disk sde
[17179594.652000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17179594.652000] sd 2:0:0:1: Attached scsi generic sg1 type 0
[17179594.652000] sd 2:0:0:2: Attached scsi generic sg2 type 0
[17179594.652000] sd 2:0:0:3: Attached scsi generic sg3 type 0
[17179594.652000] sd 3:0:0:0: Attached scsi generic sg4 type 0
[17179595.012000] NET: Registered protocol family 10
[17179595.016000] lo: Disabled Privacy Extensions
[17179595.016000] IPv6 over IPv4 tunneling driver
[17179595.752000] ACPI: Power Button (FF) [PWRF]
[17179595.752000] ACPI: Power Button (CM) [PWRB]
[17179595.860000] ibm_acpi: ec object not found
[17179595.896000] pcc_acpi: loading...
[17179599.904000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179599.904000] apm: disabled - APM is not SMP safe.
[17179603.292000] Bluetooth: Core ver 2.8
[17179603.292000] NET: Registered protocol family 31
[17179603.292000] Bluetooth: HCI device and connection manager initialized
[17179603.292000] Bluetooth: HCI socket layer initialized
[17179603.308000] Bluetooth: L2CAP ver 2.8
[17179603.308000] Bluetooth: L2CAP socket layer initialized
[17179603.316000] Bluetooth: RFCOMM socket layer initialized
[17179603.316000] Bluetooth: RFCOMM TTY layer initialized
[17179603.316000] Bluetooth: RFCOMM ver 1.7
[17179605.324000] eth0: no IPv6 routers present

```

I'm running Edgy with the 2.6.17-10-generic kernel.

Somebody has an idea?

---

