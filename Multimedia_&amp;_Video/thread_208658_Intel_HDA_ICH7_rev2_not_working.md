---
title: "Intel HDA ICH7 rev2 not working"
date: 2006-07-03
forum: Multimedia &amp; Video
---

### Post by killerjay_47 on 2006-07-03
Hello all,

I've followed just about every piece of advice that I can find on the subject, to no avail. I've reinstalled the ALSA drivers, recompiled the source for version 1.0.10 using the guide in the sticky, and compiled the drivers, utils, and lib version 1.0.11 that I downloaded directly from ALSA.

The volume is turned up to 90 on every single channel in the ALSAMixer, and the module is being loaded (or at least, I'm loading it). I've run alsaconf a couple times, and I even reinstalled Dapper. I'm using kernel 2.6.15-25.

Everything that I know how to look at looks like it should work. Yet nothing comes out the speakers, or the headphone jack. I'm using an ASUS W3J laptop.

Thanks,
Jay

P.S. I had to cut down on the dmesg output because my post is too long. I got rid of some BIOS entries.

aplay -l results:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci | grep Audio results:
```
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

dmesg results:
```
[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
<edit here>
[17179572.616000] Security Framework v1.0.0 initialized
[17179572.616000] SELinux:  Disabled at boot.
[17179572.616000] Mount-cache hash table entries: 512
[17179572.616000] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[17179572.616000] CPU: After vendor identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[17179572.616000] monitor/mwait feature present.
[17179572.616000] using mwait in idle threads.
[17179572.616000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.616000] CPU: L2 cache: 2048K
[17179572.616000] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00000040 0000c1a9 00000000 00000000
[17179572.616000] mtrr: v2.0 (20020519)
[17179572.616000] CPU: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
[17179572.616000] Enabling fast FPU save and restore... done.
[17179572.616000] Enabling unmasked SIMD FPU exception support... done.
[17179572.616000] Checking 'hlt' instruction... OK.
[17179572.632000] checking if image is initramfs... it is
[17179573.204000] Freeing initrd memory: 6614k freed
[17179573.208000] ACPI: Looking for DSDT ... not found!
[17179573.224000] ENABLING IO-APIC IRQs
[17179573.224000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.368000] NET: Registered protocol family 16
[17179573.368000] EISA bus registered
[17179573.368000] ACPI: bus type pci registered
[17179573.368000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[17179573.368000] PCI: Using MMCONFIG
[17179573.368000] ACPI: Subsystem revision 20051216
[17179573.444000] ACPI: Interpreter enabled
[17179573.444000] ACPI: Using IOAPIC for interrupt routing
[17179573.444000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.444000] PCI: Probing PCI hardware (bus 00)
[17179573.448000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179573.448000] Boot video device is 0000:01:00.0
[17179573.448000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.448000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.468000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[17179573.468000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179573.472000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[17179573.476000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[17179573.476000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[17179573.476000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[17179573.480000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.480000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.480000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.480000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[17179573.480000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.480000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[17179573.480000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.480000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[17179573.480000] ACPI: Power Resource [GFAN] (off)
[17179573.480000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.480000] pnp: PnP ACPI init
[17179573.488000] pnp: PnP ACPI: found 16 devices
[17179573.488000] PnPBIOS: Disabled by ACPI PNP
[17179573.488000] PCI: Using ACPI for IRQ routing
[17179573.488000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.488000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179573.488000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179573.488000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[17179573.504000] pnp: 00:09: ioport range 0x680-0x69f has been reserved
[17179573.504000] pnp: 00:0d: ioport range 0x400-0x41f has been reserved
[17179573.504000] PCI: Bridge: 0000:00:01.0
[17179573.504000]   IO window: 9000-bfff
[17179573.504000]   MEM window: fdf00000-fdffffff
[17179573.504000]   PREFETCH window: bdf00000-ddefffff
[17179573.504000] PCI: Bridge: 0000:00:1c.0
[17179573.504000]   IO window: c000-cfff
[17179573.504000]   MEM window: fe000000-fe0fffff
[17179573.504000]   PREFETCH window: disabled.
[17179573.504000] PCI: Bridge: 0000:00:1c.1
[17179573.504000]   IO window: disabled.
[17179573.504000]   MEM window: fe100000-fe1fffff
[17179573.504000]   PREFETCH window: disabled.
[17179573.504000] PCI: Bridge: 0000:00:1c.2
[17179573.504000]   IO window: disabled.
[17179573.504000]   MEM window: disabled.
[17179573.504000]   PREFETCH window: disabled.
[17179573.504000] PCI: Bridge: 0000:00:1e.0
[17179573.504000]   IO window: disabled.
[17179573.504000]   MEM window: fea00000-feafffff
[17179573.504000]   PREFETCH window: disabled.
[17179573.504000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.504000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.504000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.504000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179573.504000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179573.504000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179573.504000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179573.504000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179573.504000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.504000] Simple Boot Flag at 0x52 set to 0x1
[17179573.504000] audit: initializing netlink socket (disabled)
[17179573.504000] audit(1151962084.504:1): initialized
[17179573.504000] highmem bounce pool size: 64 pages
[17179573.504000] VFS: Disk quotas dquot_6.5.1
[17179573.504000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.504000] Initializing Cryptographic API
[17179573.504000] io scheduler noop registered
[17179573.504000] io scheduler anticipatory registered
[17179573.504000] io scheduler deadline registered
[17179573.504000] io scheduler cfq registered
[17179573.504000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.504000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.504000] assign_interrupt_mode Found MSI capability
[17179573.504000] Allocate Port Service[pcie00]
[17179573.504000] Allocate Port Service[pcie03]
[17179573.504000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.504000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179573.504000] assign_interrupt_mode Found MSI capability
[17179573.504000] Allocate Port Service[pcie00]
[17179573.504000] Allocate Port Service[pcie02]
[17179573.504000] Allocate Port Service[pcie03]
[17179573.504000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179573.504000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179573.504000] assign_interrupt_mode Found MSI capability
[17179573.504000] Allocate Port Service[pcie00]
[17179573.504000] Allocate Port Service[pcie02]
[17179573.504000] Allocate Port Service[pcie03]
[17179573.504000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179573.504000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179573.504000] assign_interrupt_mode Found MSI capability
[17179573.504000] Allocate Port Service[pcie00]
[17179573.504000] Allocate Port Service[pcie02]
[17179573.504000] Allocate Port Service[pcie03]
[17179573.504000] isapnp: Scanning for PnP cards...
[17179573.860000] isapnp: No Plug & Play device found
[17179573.872000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179573.876000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179573.876000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179573.876000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179573.876000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179573.876000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179573.876000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.876000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.876000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.880000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.880000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.880000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.880000] mice: PS/2 mouse device common for all mice
[17179573.880000] EISA: Probing bus 0 at eisa.0
[17179573.880000] EISA: Detected 0 cards.
[17179573.880000] NET: Registered protocol family 2
[17179573.920000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.920000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179573.920000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.920000] TCP: Hash tables configured (established 262144 bind 65536)
[17179573.920000] TCP reno registered
[17179573.920000] TCP bic registered
[17179573.920000] NET: Registered protocol family 1
[17179573.920000] NET: Registered protocol family 8
[17179573.920000] NET: Registered protocol family 20
[17179573.920000] Using IPI Shortcut mode
[17179573.920000] ACPI wakeup devices: 
[17179573.920000] P0P2 P0P1 P394 USB0 USB2 USB3 EUSB MC97 HDAC P0P4 P0P5 P0P7 P0P8 P0P9 P0P6 SLPB 
[17179573.920000] ACPI: (supports S0 S1 S3 S4 S5)
[17179573.920000] Freeing unused kernel memory: 288k freed
[17179573.960000] vga16fb: initializing
[17179573.960000] vga16fb: mapped to 0xc00a0000
[17179574.040000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.160000] Console: switching to colour frame buffer device 80x25
[17179574.160000] fb0: VGA16 VGA frame buffer device
[17179575.180000] Capability LSM initialized
[17179575.204000] ACPI: Fan [FN00] (off)
[17179575.208000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.208000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179575.428000] ACPI: Thermal Zone [THRM] (67 C)
[17179575.904000] SCSI subsystem initialized
[17179575.904000] ACPI: bus type scsi registered
[17179575.904000] libata version 1.20 loaded.
[17179575.904000] ata_piix 0000:00:1f.2: version 1.05
[17179575.904000] ata_pci_init_one: pci_dev class+intf: 0x10180
[17179575.904000] ata_pci_init_one: NO_LEGACY == 0
[17179575.904000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 233
[17179575.904000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179575.904000] ata1: PATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xFFA0 irq 14
[17179576.068000] ata1: dev 0 cfg 00:045a 49:2b00 82:346b 83:5b29 84:6003 85:3469 86:9a09 87:6003 88:203f 93:600b
[17179576.068000] ata1: dev 0 ATA-6, max UDMA/100, 195371568 sectors: LBA
[17179576.068000] ata1(0): applying bridge limits
[17179576.068000] ata_acpi_push_id: skipping for PATA mode
[17179576.068000] ata1: dev 0 configured for UDMA/100
[17179576.068000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179576.072000] pata_get_dev_handle: dev_handle: 0xdffe76e0, parent_handle: 0xdf96fa60
[17179576.072000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff66a00, *handle=0xdffe76e0
[17179576.072000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdffe7280
[17179576.072000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node dffe7c80), AE_AML_OPERAND_VALUE
[17179576.072000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0.DRV0._GTF] (Node dffe7240), AE_AML_OPERAND_VALUE
[17179576.072000] scsi0 : ata_piix
[17179576.072000]   Vendor: ATA       Model: FUJITSU MHV2100A  Rev: 0000
[17179576.072000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179576.072000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179576.072000] pata_get_dev_handle: dev_handle: 0xdffe76e0, parent_handle: 0xdf96fa60
[17179576.072000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff66a00, *handle=0xdffe76e0
[17179576.072000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xFFA8 irq 15
[17179576.400000] ata2: dev 0 cfg 00:85c0 49:0f00 82:4218 83:5000 84:4000 85:4218 86:1000 87:4000 88:0407 93:604d
[17179576.400000] ata2: dev 0 ATAPI, max UDMA/33
[17179576.400000] ata2(0): applying bridge limits
[17179576.400000] ata_acpi_push_id: skipping for PATA mode
[17179576.400000] ata2: dev 0 configured for UDMA/33
[17179576.400000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179576.400000] pata_get_dev_handle: dev_handle: 0xdffe76e0, parent_handle: 0xdf96fa60
[17179576.400000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff66a00, *handle=0xdffe76e0
[17179576.400000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdffe7f60
[17179576.400000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node dffe7c80), AE_AML_OPERAND_VALUE
[17179576.400000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.IDE0.CHN1.DRV0._GTF] (Node dffe7ee0), AE_AML_OPERAND_VALUE
[17179576.400000] scsi1 : ata_piix
[17179576.412000]   Vendor: TSSTcorp  Model: CD/DVDW TS-L632C  Rev: AS07
[17179576.412000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179576.412000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179576.412000] pata_get_dev_handle: dev_handle: 0xdffe76e0, parent_handle: 0xdf96fa60
[17179576.412000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff66a00, *handle=0xdffe76e0
[17179576.420000] Driver 'sd' needs updating - please use bus_type methods
[17179576.428000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179576.432000] SCSI device sda: drive cache: write back
[17179576.436000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179576.436000] SCSI device sda: drive cache: write back
[17179576.436000]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[17179576.580000] sd 0:0:0:0: Attached scsi disk sda
[17179577.120000] usbcore: registered new driver usbfs
[17179577.120000] usbcore: registered new driver hub
[17179577.124000] USB Universal Host Controller Interface driver v2.3
[17179577.124000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 50
[17179577.124000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.124000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.124000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.124000] uhci_hcd 0000:00:1d.0: irq 50, io base 0x0000ec00
[17179577.124000] hub 1-0:1.0: USB hub found
[17179577.124000] hub 1-0:1.0: 2 ports detected
[17179577.176000] ieee1394: Initialized config rom entry `ip1394'
[17179577.228000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 233
[17179577.228000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.228000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.228000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.228000] uhci_hcd 0000:00:1d.1: irq 233, io base 0x0000e880
[17179577.228000] hub 2-0:1.0: USB hub found
[17179577.228000] hub 2-0:1.0: 2 ports detected
[17179577.332000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179577.332000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.332000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.332000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179577.332000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x0000e800
[17179577.332000] hub 3-0:1.0: USB hub found
[17179577.332000] hub 3-0:1.0: 2 ports detected
[17179577.436000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 22 (level, low) -> IRQ 58
[17179577.436000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179577.436000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179577.436000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179577.436000] uhci_hcd 0000:00:1d.3: irq 58, io base 0x0000e480
[17179577.436000] hub 4-0:1.0: USB hub found
[17179577.436000] hub 4-0:1.0: 2 ports detected
[17179577.540000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 50
[17179577.540000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.540000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.540000] ehci_hcd 0000:00:1d.7: debug port 1
[17179577.540000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179577.540000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179577.540000] ehci_hcd 0000:00:1d.7: irq 50, io mem 0xfebfbc00
[17179577.544000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.544000] hub 5-0:1.0: USB hub found
[17179577.544000] hub 5-0:1.0: 8 ports detected
[17179577.572000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[17179577.648000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179577.648000] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179577.700000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[169]  MMIO=[feaff800-feafffff]  Max Packet=[2048]
[17179577.732000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179577.732000] ide0: ports already in use, skipping probe
[17179577.732000] ide1: I/O resource 0x170-0x177 not free.
[17179577.732000] ide1: ports already in use, skipping probe
[17179577.752000] Attempting manual resume
[17179577.784000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.796000] kjournald starting.  Commit interval 5 seconds
[17179578.076000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[17179579.136000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000354a7ae]
[17179587.180000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179587.180000]  1:0:0:0: Attached scsi generic sg1 type 5
[17179587.304000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[17179587.304000] Uniform CD-ROM driver Revision: 3.20
[17179587.304000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179588.036000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.076000] agpgart: Detected an Intel 945GM Chipset.
[17179588.092000] agpgart: AGP aperture is 256M @ 0x0
[17179588.104000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.120000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.188000] hw_random: RNG not detected
[17179588.340000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179588.340000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179588.340000] eth0: Identified chip type is 'RTL8168B/8111B'.
[17179588.340000] eth0: r10001.02, the Linux device driver for Realtek Ethernet Controllers at 0xc800, 00:17:31:25:76:5e, IRQ 169
[17179588.340000] eth0: Auto-negotiation Enabled.
[17179588.392000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 66
[17179588.392000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179588.624000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[17179588.640000] Bluetooth: Core ver 2.8
[17179588.640000] NET: Registered protocol family 31
[17179588.640000] Bluetooth: HCI device and connection manager initialized
[17179588.640000] Bluetooth: HCI socket layer initialized
[17179588.656000] Bluetooth: HCI USB driver ver 2.9
[17179588.660000] usbcore: registered new driver hci_usb
[17179589.068000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[17179589.068000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179589.092000] ieee80211_crypt: registered algorithm 'NULL'
[17179589.116000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179589.116000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179589.200000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.3m
[17179589.200000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179590.352000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[17179590.352000] sdhci: Copyright(c) Pierre Ossman
[17179590.440000] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[17179590.480000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179590.592000] Real Time Clock Driver v1.12
[17179590.592000] input: PC Speaker as /class/input/input2
[17179591.692000] ts: Compaq touchscreen protocol output
[17179597.428000] Realtek RTL8168/8111 Family PCI-E Gigabit Ethernet Network Adapter
[17179597.428000] Driver version:1.02
[17179597.428000] Released date:2006/02/23
[17179597.428000] Link Status:Not Linked
[17179597.428000] I/O Base:0xC800(I/O port)
[17179597.428000] IRQ:169
[17179597.432000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179597.432000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179597.432000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179597.648000] ACPI: PCI Interrupt 0000:06:01.1[A] -> GSI 16 (level, low) -> IRQ 169
[17179597.696000] sdhci: ============== REGISTER DUMP ==============
[17179597.696000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
[17179597.696000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179597.696000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179597.696000] sdhci: Present:  0x01f20000 | Host ctl: 0x00000000
[17179597.696000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179597.696000] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[17179597.696000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179597.696000] sdhci: Int enab: 0xe1ff00cf | Sig enab: 0xe1ff00cf
[17179597.696000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179597.696000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[17179597.696000] sdhci: ===========================================
[17179597.748000] mmc0: SDHCI at 0xfeaff400 irq 169 DMA
[17179598.452000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[17179598.976000] lp: driver loaded but no devices found
[17179598.996000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179598.996000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179598.996000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179599.028000] Adding 2096440k swap on /dev/sda7.  Priority:-1 extents:1 across:2096440k
[17179599.228000] EXT3 FS on sda6, internal journal
[17179599.372000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179599.372000] md: bitmap version 4.39
[17179599.920000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179600.756000] cdrom: open failed.
[17179603.020000] kjournald starting.  Commit interval 5 seconds
[17179603.020000] EXT3 FS on sda8, internal journal
[17179603.020000] EXT3-fs: mounted filesystem with ordered data mode.
[17179604.020000] ACPI: AC Adapter [AC0] (on-line)
[17179604.048000] ACPI: Battery Slot [BAT0] (battery present)
[17179604.048000] ACPI: Battery Slot [BAT1] (battery absent)
[17179604.072000] Asus Laptop ACPI Extras version 0.29
[17179604.072000]   no string returned by INIT
[17179604.072000]   trying default values, supply the developers with your DSDT
[17179604.096000] ACPI: Power Button (FF) [PWRF]
[17179604.096000] ACPI: Sleep Button (CM) [SLPB]
[17179604.096000] ACPI: Lid Switch [LID]
[17179604.096000] ACPI: Power Button (CM) [PWRB]
[17179604.168000] ibm_acpi: ec object not found
[17179604.196000] pcc_acpi: loading...
[17179604.276000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179608.696000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179608.696000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179608.696000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179608.708000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179610.516000] [fglrx] total      GART = 67108864
[17179610.516000] [fglrx] free       GART = 51118080
[17179610.516000] [fglrx] max single GART = 51118080
[17179610.516000] [fglrx] total      LFB  = 262336512
[17179610.516000] [fglrx] free       LFB  = 254472192
[17179610.516000] [fglrx] max single LFB  = 254472192
[17179610.516000] [fglrx] total      Inv  = 0
[17179610.516000] [fglrx] free       Inv  = 0
[17179610.516000] [fglrx] max single Inv  = 0
[17179610.516000] [fglrx] total      TIM  = 0
[17179610.680000] ppdev: user-space parallel port driver
[17179611.252000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179611.252000] apm: overridden by ACPI.
[17179616.452000] hci_cmd_task: hci0 command tx timeout
[17179616.484000] Bluetooth: L2CAP ver 2.8
[17179616.484000] Bluetooth: L2CAP socket layer initialized
[17179616.488000] Bluetooth: RFCOMM socket layer initialized
[17179616.488000] Bluetooth: RFCOMM TTY layer initialized
[17179616.488000] Bluetooth: RFCOMM ver 1.7
[17179627.308000] usb 5-2: new high speed USB device using ehci_hcd and address 3
[17179627.440000] hub 5-2:1.0: USB hub found
[17179627.440000] hub 5-2:1.0: 4 ports detected
[17179627.744000] usb 5-2.1: new full speed USB device using ehci_hcd and address 4
[17179628.036000] usb 5-2.4: new full speed USB device using ehci_hcd and address 5
[17179628.128000] hub 5-2.4:1.0: USB hub found
[17179628.128000] hub 5-2.4:1.0: 4 ports detected
[17179628.232000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x043D pid 0x0057
[17179628.232000] usbcore: registered new driver usblp
[17179628.232000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179628.432000] usb 5-2.4.1: new low speed USB device using ehci_hcd and address 6
[17179628.744000] usb 5-2.4.2: new low speed USB device using ehci_hcd and address 7
[17179628.840000] usbcore: registered new driver hiddev
[17179628.864000] input: ATEN ATEN-COMPOSITE as /class/input/input3
[17179628.864000] input: USB HID v1.10 Keyboard [ATEN ATEN-COMPOSITE] on usb-0000:00:1d.7-2.4.1
[17179628.888000] input: ATEN ATEN-COMPOSITE as /class/input/input4
[17179628.888000] input: USB HID v1.10 Mouse [ATEN ATEN-COMPOSITE] on usb-0000:00:1d.7-2.4.1
[17179628.892000] input: Logitech USB Receiver as /class/input/input5
[17179628.892000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.7-2.4.2
[17179628.900000] input: Logitech USB Receiver as /class/input/input6
[17179628.900000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-2.4.2
[17179628.900000] usbcore: registered new driver usbhid
[17179628.900000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179639.104000] NET: Registered protocol family 10
[17179639.104000] lo: Disabled Privacy Extensions
[17179639.104000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179639.104000] IPv6 over IPv4 tunneling driver
[17179651.580000] NET: Registered protocol family 17
[17179654.608000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179656.608000] ieee80211_crypt: registered algorithm 'TKIP'
[17179665.516000] eth1: no IPv6 routers present
[17179666.564000] ipw3945: Error sending ADD_STA: Already sending a host command
[17179685.404000] eth1: no IPv6 routers present

```

---

### Post by killerjay_47 on 2006-07-04
I should add that at the moment, at login when there's supposed to be the login sound, I am getting a very low static, some buzzing and stuff, but I know that it isn't the sounds that I'm supposed to hear. I also know the card works, because I get sound no problem in Windows.
At my wit's end here, and normally I can bludgeon my way through these things. Any ideas whatsoever?

Thanks again,
Jay

---

### Post by LordRaiden on 2006-07-04
I see a few things in your dmesg that is common with with another hda-intel user. 

[17179573.488000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179573.488000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179573.488000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2

Try muting (with M key) everything in alsamixer except for Master volume and PCM.


By the way, what version of alsa and which module are you using?  I took a quick-look at this post [http://www.linux-on-laptops.com/forum/showthread.php?p=963#post963]("http://www.linux-on-laptops.com/forum/showthread.php?p=963#post963") and the poster managed to get it work (same card as well). You could even try the alsa 1.0.12rc1 version as well.

---

### Post by killerjay_47 on 2006-07-04
I can try the 1.0.12rc drivers. I have tried the default alsa package, the alsa source for 1.0.10, and I tried a compile of the 1.0.11 packages. One thing I'm not sure about is removing and replacing the drivers when I want to use a different version.
I don't have a Master volume in alsamixer. I have headphones and various side and front channels and stuff. I can try muting everything except headphone and PCM and I will have a look at that posting. Thanks.

Jay

---

### Post by LordRaiden on 2006-07-04
I don't know if it is a problem if you don't have a master volume, because then either something is wrong or your front panel is master. Your headphone slider would probably only control the very front.

---

### Post by killerjay_47 on 2006-07-04
Channels available to me:
Headphones
PCM
Front
Surround
Center
LFE
Line
CD
Mic
PC Speaker
Aux
Mono

All are muted at the moment except PCM, Headphones, and Front. No sound comes out. (Although I don't have anything plugged into the headphone jack, so there might be something there that I don't know about.)

The guy in the linux-on-laptops post you showed me is using a different kernel than the one I'm using... will that make any difference? I'll try the module-assistant, but apt is grabbing an older version of the ALSA drivers than the current release.

Thanks,
Jay

---

### Post by LordRaiden on 2006-07-04
Using module-assistant is fine with alsa-source, the Ubuntu version is patched anyway.

However, I suggest tinkering with alsamixer as much as you can, especially if you cannot find any errors in your sound card install using dmesg, besides the cannot allocate errors.

Try plugging in a headphone to see if it works. Also, unmute the center slider.

---

### Post by killerjay_47 on 2006-07-05
Ok, well, I get a bunch of garbled noise through the headphone that sounds like what I'm expecting to hear when I first log in. When I start playing an mp3 file in VLC, I can hear it, but it's extremely distorted. Then it gradually fades away, so when I max out my stereo (connected through the headphone jack), I get the same garbled, fuzzy sounding audio that is what I'm playing with a bunch of distortion. Eventually, after about 10 minutes or so, it fades away to nothing. I'm using VLC as my player because none of the others that are installed recognize my mp3s as music files.
I'm wondering if maybe I'm supposed to have a master volume but it isn't showing up in ALSA? That doesn't explain the fading, though.
I've tried everything in every forum I can find, and every suggestion in every posting that I've stumbled across. I'm not sure where to go next.

Thanks for your attention and help.

Jay

---

### Post by LordRaiden on 2006-07-05
Reading the alsa bug-tracking forums. Intel drivers ==> plague. 

Try this ```
sudo nano /etc/modprobe.d/alsa-base

``` 
Add this line to the very end ```
options snd-hda-intel model=3stack
``` Do a reboot (or sudo modprobe snd-hda-intel - it might work and you won't have to reboot) afterwards.

---

### Post by killerjay_47 on 2006-07-05
Well, I thought maybe it would work this time, because the login drum sounded fine. But when I got in and started playing a file, same deal, it was distorted, and faded away really quick, to the point where when I cranked my stereo, I could hear it, and it was still distorted. I tried playing with my volumes while the file was still playing and immediately after I touched one of the sliders, the sound died completely and hasn't come back.
I will reiterate that the hardware can't be at fault, because it works fine in Windows, although this does sound somewhat like a hardware problem.
Any more ideas?

Jay

P.S. Something else I can add: When I first start VLC, for some reason it defaults to muted, even though I've set the default volume to 50%. I don't know if this has anything to do with the problem. Either way, I don't hear anything until I crank the VLC volume up.

---

### Post by LordRaiden on 2006-07-05
Wait. I thought you had a desktop. Go back to /etc/modprobe.d/alsa-base change

```

options snd-hda-intel model=3stack

```

to 


```

options snd-hda-intel model=laptop

```

or 


 ```

 options snd-hda-intel model=laptop-eapd
 
```

depending on whichever is better if any.

---

### Post by tuanway on 2006-07-05
hey killerjay, i have the same laptop
just wondering what your alsamixer sliders are at.
because i can't hear anything, except for fuzzy static sounds.
i want to be able to at least hear that same drumroll u got.

thanks

---

### Post by killerjay_47 on 2006-07-05
Ok, tried both the options you gave me, and neither work. the -laptop gives me nothing, and the -laptop-eapd gives me the exact same as before, with the distortion and it fades right away to super quiet.

tuanway, my alsamixer sliders are set to 100% on everything, and the channels I have unmuted are headphones, PCM, front, and center. To hear anything, I have my stereo plugged into the headphone jack. Like I've said before, it starts loud enough to hear, and then quickly fades.

Thanks for your help so far, LordRaiden. Hopefully we can get this working, but I'm right out of ideas.

Jay

---

### Post by LordRaiden on 2006-07-06
Yeah I am also bit on the blank side. A lot of these problems that I am seeing recently are similar. Sound 'plays' but nothing is actually heard. I suggest you sign up with [https://bugtrack.alsa-project.org]("https://bugtrack.alsa-project.org") and file a bug report. You'll a bit more concrete help and verification if your problem has something to do with settings or is an actual bug. In any case, post the result back (whether it was a setting; if so what setting - or if it was a bug).

---

### Post by Liquid2006 on 2006-09-29
Are you using an Acer per chance? There is a specific Acer patch for Alsa that I had to use to get sound running on my system with the same chip set. Sorry, I cant find the link right now for you.

---

### Post by ReaderRat on 2006-10-26
> **LordRaiden said:**
> Yeah I am also bit on the blank side. A lot of these problems that I am seeing recently are similar. Sound 'plays' but nothing is actually heard. I suggest you sign up with [https://bugtrack.alsa-project.org]("https://bugtrack.alsa-project.org") and file a bug report. You'll a bit more concrete help and verification if your problem has something to do with settings or is an actual bug. In any case, post the result back (whether it was a setting; if so what setting - or if it was a bug).
Has there been any resolution to this problem?
I am dual-booting Whinedows/Dapper and the sound is great in Win, but nothing in Dapper. I just bought a toshiba Satellite laptop, and it disappoints me not to have sound (so I can hear the drumbeat).It is an Intel mobo with 82801G ICH7 chipset.
Over 1000 people have viewed these posts - are there no answers?

---

### Post by Ugeek on 2006-11-01
Dear all, I have a workaround which works for me on my compaq laptop (v3018) with same chipset. I have found it out of some other post here but cant locate now.

     You have to have windows dual boot and the latest alsa installed (for me its 1.0.13 rc2). the hibernate linux and got to windows (for me XP), raise all the volume to maximum. reboot to linux.
  It does not work on subsequent reboot. better you hibernate. Let me know if it works for you too....

---

### Post by LarsBjerregaard on 2006-11-10
Posting this in case it helps anybody.

Sound worked for me in Ubuntu Breezy, but in a completely new install of Dapper - no sound at all.
I see many people all over the place struggling with this. After many hours of googling, I found a simple workaround which works for me. It was described on: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2038](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2038)

So basically what I did (as root or using sudo):
1) Add to the bottom of /etc/modprobe.d/alsa-base: options snd-hda-intel model=ref
2) Reboot

Voila! Sound works.

My system:

Dell Dimension 9150

OS: Ubuntu Dapper (6.06 LTS)

cat /proc/asound/version:
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).

lspci -vv | fgrep Audio:
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

cat /proc/asound/card0/codec#0:
Codec: SigmaTel STAC9221 A1

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The problem seems to be Alsa headaches with STAC9221, and also seems to be fixed upstream now.

---

### Post by rax_m on 2006-11-20
Hi, 

I've also had sound issues ever since I installed Edgy on my Toshiba P100-429. 
I've tried a lot of the suggestions in the sticky (Comprehensive Sound Problems guide) and this post, however no luck yet. Did manage to break various X windows components in the process. 

Has anyone managed to get sound working on their Toshiba laptop as yet?
What did you do?

Thanks 
Rax

---

### Post by ivago on 2006-11-20
same problem with my new toshiba SA120, I have a Fedora 6 DVD lay!n' round wich I'll probably install tonite... it's been since FC3 I used that distro cause I really like ubuntu.... anyway keep you guys posted if it works or not.

---

### Post by ivago on 2006-11-20
same problem on FC6 :confused: hardware support was even worse and even had to install rpm's from atrpms to get my intel 3945 wifi up and runnin'.

Anyway without music I'm gonna stick to windows when working on my laptop. Lucky for me I'm  90% of the time a desktop user 

still a pitty tho and hopefully this intel stuff gets better support in upcoming kernel or alsa builds.

---

### Post by wylie348 on 2006-11-20
This did not work for me.  Still only sound from headphone jack and not from internal speakers on ICH7.
:(

---

### Post by wylie348 on 2006-11-21
Still no solution to this problem after lots of time searching the net - but it is definitely a problem that is common to most ICH7 users!

<BUMP>

---

### Post by wylie348 on 2006-11-23
Bump...

---

### Post by bombadier337 on 2006-11-23
I don't know if this will help everyone, but no guide on the internet got my sound to work.  After days of work I got it, but I made it a new thread so it wouldn't be in the middle of a very large thread.  Hope this helps, it finally gave me audio on my ICH7 rev.2

[http://ubuntuforums.org/showthread.php?t=305712](http://ubuntuforums.org/showthread.php?t=305712)

---

### Post by Hubi17 on 2006-11-30
i had the same problem as killerjay_47, sound would work distorted and after a while fade/stop working. I also noticed that if I changed the volume while playing any sound it went completely off.

Though LordRaiden's solution worked for me:
adding "options snd-hda-intel model=3stack" to the /etc/modprobe.d/alsa-base

I also used apt-get to get the latest ALSA, but that was already available after Ubuntu updates.

Thanks for all the help - i got it working. Good luck to the rest, hope you get it working too!!

---

### Post by Pcghost on 2006-12-08
Has anyone found a model=X that works for the Toshiba Satellite P100?  I have installed the latest stable ALSA (driver,lib,oss,utils) drivers, and have tried the various model=ref, model=etc.... and I still have no sound.  ](*,)

---

### Post by dactry on 2006-12-11
a small fix to get sound is to try booting without acpi 
can't remember how to do it right now but the answer was in some other posts. it worked for me but without acpi some laptop functions probably will not work like hibernation and stuff like that. one side affect for me was my nvidia driver will not work without acpi for some reason. :( I'm still trying to find a fix for that

---

### Post by Avian00 on 2006-12-14
I've got the same problem.  By passing the "acpi=off" argument to my kernel at boot time, I magically get sound!  Now my question becomes, if disabling ACPI fixes my found, is the problem really with my sound card driver?  My working theory is that ACPI turns my speakers amplifiers off.  In that case, it's really an ACPI problem and not an ALSA problem (as many other forums have suggested).  What do others think of this theory?

---

### Post by Pcghost on 2006-12-20
Great news for Toshiba Satellite owners who still have to choose between sound and acpi.  I just recieved this from the toshiba-linux mailing list.:KS 

<message start>
For those who have had no luck in getting the audio working on the
P100 line of notebooks, it appears that the necessary components are
finally coming together. The two problems in getting the audio up and
running are support for the Conexant codec used to implement the Intel
HDA functionality and ACPI conflicts created by what is likely a
bugged DSDT (resulting in the inability to use other parts of ACPI for
monitoring battery levels/temps/hardware events/etc if one wishes to
use the sound).

The snd-hda-intel driver included in the alsa-driver 1.0.14-rc1 and
above now supports the Conexant codec. I would estimate that in-kernel
support will appear in the vanilla kernel with the 2.6.20 release
(2.6.19 and below do not include support).

A Gentoo user has sussed out the required DSDT modifications and
posted them on the Gentoo forums at
[http://forums.gentoo.org/viewtopic-p-3774561.html#3774561](http://forums.gentoo.org/viewtopic-p-3774561.html#3774561). If you
don't know how to modify the DSDT there is a reasonable guide located
at [http://www.gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://www.gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)

I have tested the DSDT modifications described with a PSPA6A-01J017
running the v2.40 BIOS, a 2.6.19 kernel and alsa-driver 1.0.14-rc1 and
they appear to work with no ill side effects, will see how it holds up
over the Christmas period. Toshiba might like to take note of these
modifications and provide an official fix for this issue in a future
BIOS update.
<end>

---

