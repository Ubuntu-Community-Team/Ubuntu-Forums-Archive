---
title: "Screetch noises"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by peponline on 2006-06-15
Hello there!

Whenever I play a sound in ubuntu dapper or the system plays a sound I hear a terrible beep (screetch) noise through the speakers (Not the internal speaker)

I tried unmuting some channels in alsamixer, but no luck. I also tried changing  asound.conf, but that didn't work either.

In System > Preferences > Sound I can choose from HDA Intel and MPU-401 UART. Both gives the same problem.

When I doubleclick on the volume settings, I can choose from HDA Intel (Alsa Mixer) and Analog Devices (AD1986A) OSS mixer.
Both have the same problem, but when OSS is selected, the beep seems to sound lower.

I already tried so many things that alsamixer says " no mixer elems found"

My LSCPI output:

```
0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub (rev 81)
0000:00:01.0 PCI bridge: Intel Corporation 945G/P PCI Express Graphics Port (rev 81)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8168 (rev 01)
0000:04:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
```

My DMESG output:
```

[17179569.184000] Linux version 2.6.15-25-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffa0000 (usable)
[17179569.184000]  BIOS-e820: 000000003ffa0000 - 000000003ffae000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ffae000 - 000000003ffe0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003ffe0000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 262048
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32672 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fad60
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x09000516 MSFT 0x00000097) @ 0x3ffa0000
[17179569.184000] ACPI: FADT (v001 A M I  OEMFACP  0x09000516 MSFT 0x00000097) @ 0x3ffa0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x09000516 MSFT 0x00000097) @ 0x3ffa0390
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x09000516 MSFT 0x00000097) @ 0x3ffae040
[17179569.184000]   >>> ERROR: Invalid checksum
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x09000516 MSFT 0x00000097) @ 0x3ffa8490
[17179569.184000] ACPI: DSDT (v001  A0355 A0355000 0x00000000 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:4 APIC version 20
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 3011.195 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.616000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.616000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179571.644000] Memory: 1026912k/1048192k available (2101k kernel code, 20592k reserved, 592k data, 332k init, 130688k highmem)
[17179571.644000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.724000] Calibrating delay using timer specific routine.. 6029.34 BogoMIPS (lpj=12058687)
[17179571.724000] Security Framework v1.0.0 initialized
[17179571.724000] SELinux:  Disabled at boot.
[17179571.724000] Mount-cache hash table entries: 512
[17179571.724000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000649d 00000000 00000000
[17179571.724000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000649d 00000000 00000000
[17179571.724000] monitor/mwait feature present.
[17179571.724000] using mwait in idle threads.
[17179571.724000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179571.724000] CPU: L2 cache: 2048K
[17179571.724000] CPU: Hyper-Threading is disabled
[17179571.724000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000080 0000649d 00000000 00000000
[17179571.724000] mtrr: v2.0 (20020519)
[17179571.724000] Enabling fast FPU save and restore... done.
[17179571.724000] Enabling unmasked SIMD FPU exception support... done.
[17179571.724000] Checking 'hlt' instruction... OK.
[17179571.740000] SMP alternatives: switching to UP code
[17179571.740000] checking if image is initramfs... it is
[17179572.224000] Freeing initrd memory: 6803k freed
[17179572.224000] ACPI: Looking for DSDT ... not found!
[17179572.240000] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[17179572.240000] SMP alternatives: switching to SMP code
[17179572.240000] Booting processor 1/1 eip 3000
[17179572.252000] Initializing CPU#1
[17179572.332000] Calibrating delay using timer specific routine.. 6021.71 BogoMIPS (lpj=12043431)
[17179572.332000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000649d 00000000 00000000
[17179572.332000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000649d 00000000 00000000
[17179572.332000] monitor/mwait feature present.
[17179572.332000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179572.332000] CPU: L2 cache: 2048K
[17179572.332000] CPU: Hyper-Threading is disabled
[17179572.332000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000080 0000649d 00000000 00000000
[17179572.332000] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[17179572.332000] Total of 2 processors activated (12051.05 BogoMIPS).
[17179572.332000] ENABLING IO-APIC IRQs
[17179572.332000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.496000] checking TSC synchronization across 2 CPUs: passed.
[17179572.500000] Brought up 2 CPUs
[17179572.500000] NET: Registered protocol family 16
[17179572.500000] EISA bus registered
[17179572.500000] ACPI: bus type pci registered
[17179572.500000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=4
[17179572.500000] PCI: Using MMCONFIG
[17179572.500000] ACPI: Subsystem revision 20051216
[17179572.512000] ACPI: Interpreter enabled
[17179572.512000] ACPI: Using IOAPIC for interrupt routing
[17179572.512000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.512000] PCI: Probing PCI hardware (bus 00)
[17179572.516000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179572.516000] Boot video device is 0000:04:00.0
[17179572.516000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.516000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.516000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179572.520000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[17179572.520000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[17179572.520000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[17179572.528000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.528000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.528000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.528000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.528000] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[17179572.528000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.528000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.528000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.528000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.528000] pnp: PnP ACPI init
[17179572.536000] pnp: PnP ACPI: found 17 devices
[17179572.536000] PnPBIOS: Disabled by ACPI PNP
[17179572.536000] PCI: Using ACPI for IRQ routing
[17179572.536000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.548000] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[17179572.548000] PCI: Bridge: 0000:00:01.0
[17179572.548000]   IO window: e000-efff
[17179572.552000]   MEM window: e2f00000-e7ffffff
[17179572.552000]   PREFETCH window: e8000000-efffffff
[17179572.552000] PCI: Bridge: 0000:00:1c.0
[17179572.552000]   IO window: d000-dfff
[17179572.552000]   MEM window: disabled.
[17179572.552000]   PREFETCH window: disabled.
[17179572.552000] PCI: Bridge: 0000:00:1c.3
[17179572.552000]   IO window: c000-cfff
[17179572.552000]   MEM window: e2e00000-e2efffff
[17179572.552000]   PREFETCH window: disabled.
[17179572.552000] PCI: Bridge: 0000:00:1e.0
[17179572.552000]   IO window: b000-bfff
[17179572.552000]   MEM window: disabled.
[17179572.552000]   PREFETCH window: disabled.
[17179572.552000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.552000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179572.552000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.552000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179572.552000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179572.552000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179572.552000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.552000] audit: initializing netlink socket (disabled)
[17179572.552000] audit(1150393861.548:1): initialized
[17179572.552000] highmem bounce pool size: 64 pages
[17179572.552000] VFS: Disk quotas dquot_6.5.1
[17179572.552000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.552000] Initializing Cryptographic API
[17179572.552000] io scheduler noop registered
[17179572.552000] io scheduler anticipatory registered
[17179572.552000] io scheduler deadline registered
[17179572.552000] io scheduler cfq registered
[17179572.552000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.552000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179572.552000] assign_interrupt_mode Found MSI capability
[17179572.552000] Allocate Port Service[pcie00]
[17179572.552000] Allocate Port Service[pcie03]
[17179572.552000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.552000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179572.552000] assign_interrupt_mode Found MSI capability
[17179572.552000] Allocate Port Service[pcie00]
[17179572.552000] Allocate Port Service[pcie02]
[17179572.552000] Allocate Port Service[pcie03]
[17179572.552000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179572.552000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179572.552000] assign_interrupt_mode Found MSI capability
[17179572.552000] Allocate Port Service[pcie00]
[17179572.552000] Allocate Port Service[pcie03]
[17179572.552000] isapnp: Scanning for PnP cards...
[17179572.904000] isapnp: No Plug & Play device found
[17179572.924000] Real Time Clock Driver v1.12
[17179572.924000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179572.924000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179572.928000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.928000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.928000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.928000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.928000] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.932000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.932000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.932000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.932000] mice: PS/2 mouse device common for all mice
[17179572.932000] EISA: Probing bus 0 at eisa.0
[17179572.932000] Cannot allocate resource for EISA slot 8
[17179572.932000] EISA: Detected 0 cards.
[17179572.932000] NET: Registered protocol family 2
[17179572.972000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.984000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.984000] TCP established hash table entries: 262144 (order: 9, 3145728 bytes)
[17179572.984000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[17179572.988000] TCP: Hash tables configured (established 262144 bind 65536)
[17179572.988000] TCP reno registered
[17179572.988000] TCP bic registered
[17179572.988000] NET: Registered protocol family 1
[17179572.988000] NET: Registered protocol family 8
[17179572.988000] NET: Registered protocol family 20
[17179572.988000] Starting balanced_irq
[17179572.988000] Using IPI No-Shortcut mode
[17179572.988000] ACPI wakeup devices:
[17179572.988000] P0P1 P0P3 P0P4 P0P5 P0P6 P0P7 P0P8 P0P9 PS2K UAR1 USB2 USB3 USB4 MC97 USB1 EUSB
[17179572.988000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.988000] Freeing unused kernel memory: 332k freed
[17179573.032000] vga16fb: initializing
[17179573.032000] vga16fb: mapped to 0xc00a0000
[17179573.240000] Console: switching to colour frame buffer device 80x25
[17179573.240000] fb0: VGA16 VGA frame buffer device
[17179574.264000] Capability LSM initialized
[17179574.348000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179574.900000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179574.900000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 217
[17179574.900000] ICH7: chipset revision 1
[17179574.900000] ICH7: not 100% native mode: will probe irqs later
[17179574.900000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179574.900000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[17179574.900000] Probing IDE interface ide0...
[17179575.316000] hda: TSSTcorpCD/DVDW TS-H552B, ATAPI CD/DVD-ROM drive
[17179575.600000] hdb: Maxtor 6B200P0, ATA DISK drive
[17179575.660000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.680000] Probing IDE interface ide1...
[17179576.264000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.264000] Uniform CD-ROM driver Revision: 3.20
[17179576.268000] hdb: max request size: 1024KiB
[17179576.268000] hdb: 398297088 sectors (203928 MB) w/8192KiB Cache, CHS=24792/255/63, UDMA(100)
[17179576.272000] hdb: cache flushes supported
[17179576.272000]  hdb: hdb1 hdb2 hdb4 < hdb5 >
[17179576.448000] SCSI subsystem initialized
[17179576.448000] ACPI: bus type scsi registered
[17179576.448000] libata version 1.20 loaded.
[17179576.452000] ata_piix 0000:00:1f.2: version 1.05
[17179576.452000] ata_pci_init_one: pci_dev class+intf: 0x1018f
[17179576.452000] ata_pci_init_one: NO_LEGACY == 0
[17179576.452000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 225
[17179576.452000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179576.452000] ata1: PATA max UDMA/133 cmd 0xA800 ctl 0xA402 bmdma 0x9400 irq 225
[17179576.452000] ata2: PATA max UDMA/133 cmd 0xA000 ctl 0x9802 bmdma 0x9408 irq 225
[17179577.624000] ata1: disabling port
[17179577.624000] scsi0 : ata_piix
[17179578.796000] ata2: disabling port
[17179578.796000] scsi1 : ata_piix
[17179578.876000] usbcore: registered new driver usbfs
[17179578.876000] usbcore: registered new driver hub
[17179578.876000] USB Universal Host Controller Interface driver v2.3
[17179578.876000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 233
[17179578.876000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179578.876000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179578.876000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179578.876000] uhci_hcd 0000:00:1d.0: irq 233, io base 0x00008000
[17179578.876000] hub 1-0:1.0: USB hub found
[17179578.876000] hub 1-0:1.0: 2 ports detected
[17179578.980000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 50
[17179578.980000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179578.980000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179578.980000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179578.980000] uhci_hcd 0000:00:1d.1: irq 50, io base 0x00008400
[17179578.980000] hub 2-0:1.0: USB hub found
[17179578.980000] hub 2-0:1.0: 2 ports detected
[17179579.084000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 58
[17179579.084000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179579.084000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179579.084000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179579.084000] uhci_hcd 0000:00:1d.2: irq 58, io base 0x00008800
[17179579.084000] hub 3-0:1.0: USB hub found
[17179579.084000] hub 3-0:1.0: 2 ports detected
[17179579.188000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179579.188000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179579.188000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179579.188000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179579.188000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x00009000
[17179579.188000] hub 4-0:1.0: USB hub found
[17179579.188000] hub 4-0:1.0: 2 ports detected
[17179579.228000] usb 1-1: new low speed USB device using uhci_hcd and address 2[17179579.292000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 233
[17179579.292000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179579.292000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179579.296000] ehci_hcd 0000:00:1d.7: debug port 1
[17179579.296000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179579.296000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179579.296000] ehci_hcd 0000:00:1d.7: irq 233, io mem 0xe2dffc00
[17179579.300000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.300000] hub 5-0:1.0: USB hub found
[17179579.300000] hub 5-0:1.0: 8 ports detected
[17179579.420000] Probing IDE interface ide1...
[17179579.760000] usb 1-1: device not accepting address 2, error -71
[17179580.052000] Attempting manual resume
[17179580.068000] kjournald starting.  Commit interval 5 seconds
[17179580.068000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.384000] usb 5-8: new high speed USB device using ehci_hcd and address 3
[17179580.772000] usb 1-1: new low speed USB device using uhci_hcd and address 4[17179587.516000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.516000] agpgart: Detected an Intel 945G Chipset.
[17179587.844000] hw_random hardware driver 1.0.0 loaded
[17179587.876000] agpgart: AGP aperture is 256M @ 0x0
[17179587.876000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179587.876000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179587.928000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.196000] Initializing USB Mass Storage driver...
[17179588.196000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179588.196000] usb-storage: device found at 3
[17179588.196000] usb-storage: waiting for device to settle before scanning
[17179588.196000] usbcore: registered new driver usb-storage
[17179588.196000] USB Mass Storage support registered.
[17179588.196000] input: PC Speaker as /class/input/input1
[17179588.248000] Floppy drive(s): fd0 is 1.44M
[17179588.268000] FDC 0 is a post-1991 82077
[17179588.300000] parport: PnPBIOS parport detected.
[17179588.300000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179588.528000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.584000] usbcore: registered new driver hiddev
[17179588.620000] input: B16_b_02 USB-PS/2 Optical Mouse as /class/input/input2
[17179588.620000] input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
[17179588.620000] usbcore: registered new driver usbhid
[17179588.620000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179588.772000] nvidia: module license 'NVIDIA' taints kernel.
[17179588.776000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179588.776000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[17179588.776000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179588.816000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179588.816000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179588.820000] eth0: Identified chip type is 'RTL8168B/8111B'.
[17179588.820000] eth0: r10001.02, the Linux device driver for Realtek Ethernet Controllers at 0xc800, 00:15:f2:08:10:73, IRQ 177
[17179588.820000] eth0: Auto-negotiation Enabled.
[17179589.076000] ts: Compaq touchscreen protocol output
[17179590.388000] eth0: 100Mbps Full-duplex operation.
[17179590.388000] Realtek RTL8168/8111 Family PCI-E Gigabit Ethernet Network Adapter
[17179590.388000] Driver version:1.02
[17179590.388000] Released date:2006/02/23
[17179590.388000] Link Status:Linked
[17179590.388000] Link Speed:100Mbps
[17179590.388000] Duplex mode:Full-Duplex
[17179590.388000] I/O Base:0xC800(I/O port)
[17179590.388000] IRQ:177
[17179590.580000] lp0: using parport0 (interrupt-driven).
[17179590.676000] Adding 1518100k swap on /dev/hdb5.  Priority:-1 extents:1 across:1518100k
[17179590.736000] EXT3 FS on hdb1, internal journal
[17179590.944000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179590.944000] md: bitmap version 4.39
[17179591.640000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179591.684000] NET: Registered protocol family 17
[17179592.104000] cdrom: open failed.
[17179592.412000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179592.460000] NTFS volume version 3.1.
[17179593.200000]   Vendor: Generic   Model: IC1210        CF  Rev: 1.9C
[17179593.200000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179593.204000]   Vendor: Generic   Model: IC1210        MS  Rev: 1.9C
[17179593.204000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179593.204000]   Vendor: Generic   Model: IC1210    MMC/SD  Rev: 1.9C
[17179593.204000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179593.208000]   Vendor: Generic   Model: IC1210        SM  Rev: 1.9C
[17179593.208000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179593.216000] usb-storage: device scan complete
[17179593.244000] Driver 'sd' needs updating - please use bus_type methods
[17179593.248000] sd 2:0:0:0: Attached scsi removable disk sda
[17179593.256000] sd 2:0:0:1: Attached scsi removable disk sdb
[17179593.264000] sd 2:0:0:2: Attached scsi removable disk sdc
[17179593.276000] sd 2:0:0:3: Attached scsi removable disk sdd
[17179593.288000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17179593.288000] sd 2:0:0:1: Attached scsi generic sg1 type 0
[17179593.288000] sd 2:0:0:2: Attached scsi generic sg2 type 0
[17179593.288000] sd 2:0:0:3: Attached scsi generic sg3 type 0
[17179594.028000] NET: Registered protocol family 10
[17179594.028000] lo: Disabled Privacy Extensions
[17179594.028000] IPv6 over IPv4 tunneling driver
[17179598.068000] ACPI: Power Button (FF) [PWRF]
[17179598.068000] ACPI: Power Button (CM) [PWRB]
[17179598.156000] ibm_acpi: ec object not found
[17179598.196000] pcc_acpi: loading...
[17179598.664000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179598.664000] acpi-cpufreq: CPU1 - ACPI performance management activated.
[17179602.308000] ppdev: user-space parallel port driver
[17179602.688000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179602.688000] apm: disabled - APM is not SMP safe.
[17179604.264000] eth0: no IPv6 routers present
[17179606.200000] Bluetooth: Core ver 2.8
[17179606.200000] NET: Registered protocol family 31
[17179606.200000] Bluetooth: HCI device and connection manager initialized
[17179606.200000] Bluetooth: HCI socket layer initialized
[17179606.220000] Bluetooth: L2CAP ver 2.8
[17179606.220000] Bluetooth: L2CAP socket layer initialized
[17179606.228000] Bluetooth: RFCOMM socket layer initialized
[17179606.228000] Bluetooth: RFCOMM TTY layer initialized
[17179606.228000] Bluetooth: RFCOMM ver 1.7
[17179948.944000] opl3: Unknown parameter `port'
```

```
daniel@daniel-linux:~$ lsmod | grep snd
snd_intel8x0           35708  0
snd_ac97_codec         99808  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_mpu401              6792  0
snd_mpu401_uart         8640  1 snd_mpu401
snd_rawmidi            26848  1 snd_mpu401_uart
snd_seq_device          9228  1 snd_rawmidi
snd_hda_intel          20468  1
snd_hda_codec         151056  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  5 snd_intel8x0,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  14 snd_intel8x0,snd_ac97_codec,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  2 sound,snd
snd_page_alloc         11304  3 snd_intel8x0,snd_hda_intel,snd_pcm
```

I am using kernel 2.6.15-25-686.


Hope that anybody can help! Thanx in Advance ;)

---

### Post by peponline on 2006-06-15
Just a quick update: 

Tried to install alsa 0.1.11 rc5, but I can't seem to compile it (gcc cannot create executables :-( )

Also something very strange: Alsa is saying a headphone is connected, but I haven't. Changing the volume of the headphone slider will indeed make the sound softer or louder, but the beep goes with it. Changing the speaker slider does nothing. Also PCM and PCM2 sliders make the sound louder, but also the beep noise. IEC and stereo downmix switches make the sound even more terrible.

Anyone who knows something more about this? :confused:

---

### Post by gr4ssi on 2006-08-10
Same issue on a Samsung X11 with similar chipset and same soundchip.
I got rid of that noise by deactivating the kde-sound-system in kde controll-center. Who needs sound anyway? ;-)

Greetz, 
grassi

---

### Post by Robertjm on 2006-08-14
Is it a VERY loud screetching noise?? If so, I had a similar problem. One of the CAPTURE devices is turned on that should be turned off. 

In the Mixer (not Alsa, but the other one installed with Dapper-Gnome), and go to the Capture tab. At the very bottom are two icons below each slider section, one for Mute/Unmute and one for Toggle Audio Capture from (device name). Start by clicking on ALL the Toggle icons so that there are red X's on them all. Hopefully, that kills the screetch. You can then turn each on back on, one at a time, and see which one is the culprit. I honestly don't remember which one I turned off to get rid of that nasty sound.

Hope that helps!!

Robert

---

### Post by dholm on 2006-09-04
I had the same problem with my Packard Bell MX65-008. The following patch solved the problem for me: [http://www.nabble.com/Intel-HDA-AD1986A-without-surround-t595968.html]("http://www.nabble.com/Intel-HDA-AD1986A-without-surround-t595968.html")
It's only a temporary workaround so don't expect it to end up in an official kernel tree any time soon.
Note: The patch doesn't apply cleanly to ubuntu's kernel sources. Apply it manualy, you'll find the section at around line 1900.
Use *sudo make modules SUBDIRS=sound/pci/hda* to build only the Intel HD audio modules.

---

