---
title: "Can't get Creative Zen V plus to work"
date: 2009-03-31
forum: Multimedia Software
---

### Post by tegnoto89 on 2009-03-31
Okay, I've been doing a lot of searching on this, and I simply cannot get my Creative Zen V Plus to work.  I have tried Gnomad2 and KZenexplorer; both tell me they cannot find a jukebox from the USB.  When I plug it in, nothing happens, except that the light on the player turns on and (I believe) it charges.  No music players recognize it.  It does not show up in Nautilus, even after several refreshes.

It works perfectly in Windows both as a removable disk and as regular mp3 player.

Here's my output for sudo lsusb:

```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 004: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  

```

and sudo fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6951

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

```

I really want to get this working, so any help is SO well appreciated!  Thanks in advance!

---

### Post by tegnoto89 on 2009-04-04
Anyone at all?  :-\

---

### Post by vacadepollo on 2009-04-04
My Zen V plus 4gb works prefectly, and Rhythmbox/Gnomad2 detects ok :(

$lsusb
*Bus 004 Device 002: ID 041e:4152 Creative Technology, Ltd *


Check errors with dmesg and choose another usb port. 
Perhaps it's a Zen problem, try full format.

---

### Post by tegnoto89 on 2009-04-05
> Check errors with dmesg and choose another usb port.
Perhaps it's a Zen problem, try full format.

Here's what I'm getting for dmesg:

```
[   21.902950] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 17
[   21.902955] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.902991] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 18
[   21.902996] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.903030] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 19
[   21.903038] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   21.903079] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 20
[   21.903084] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   21.903116] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 20 (level, low) -> IRQ 17
[   21.903126] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   21.903143] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[   21.903149] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   21.903176] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.903182] PCI: Setting latency timer of device 0000:15:00.0 to 64
[   21.903193] NET: Registered protocol family 2
[   21.949192] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.949360] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.949685] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.949842] TCP: Hash tables configured (established 131072 bind 65536)
[   21.949844] TCP reno registered
[   21.961230] checking if image is initramfs... it is
[   22.475410] Freeing initrd memory: 7324k freed
[   22.475552] Simple Boot Flag at 0x35 set to 0x1
[   22.476093] audit: initializing netlink socket (disabled)
[   22.476105] audit(1238948515.341:1): initialized
[   22.475777] highmem bounce pool size: 64 pages
[   22.477369] VFS: Disk quotas dquot_6.5.1
[   22.477429] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.477533] io scheduler noop registered
[   22.477535] io scheduler anticipatory registered
[   22.477537] io scheduler deadline registered
[   22.477545] io scheduler cfq registered (default)
[   22.477732] Boot video device is 0000:01:00.0
[   22.477831] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.477864] assign_interrupt_mode Found MSI capability
[   22.477891] Allocate Port Service[0000:00:01.0:pcie00]
[   22.477920] Allocate Port Service[0000:00:01.0:pcie02]
[   22.477997] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.478089] assign_interrupt_mode Found MSI capability
[   22.478171] Allocate Port Service[0000:00:1c.0:pcie00]
[   22.478198] Allocate Port Service[0000:00:1c.0:pcie02]
[   22.478329] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   22.478429] assign_interrupt_mode Found MSI capability
[   22.478504] Allocate Port Service[0000:00:1c.1:pcie00]
[   22.478531] Allocate Port Service[0000:00:1c.1:pcie02]
[   22.478665] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   22.478755] assign_interrupt_mode Found MSI capability
[   22.478827] Allocate Port Service[0000:00:1c.2:pcie00]
[   22.478857] Allocate Port Service[0000:00:1c.2:pcie02]
[   22.479004] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   22.479089] assign_interrupt_mode Found MSI capability
[   22.479167] Allocate Port Service[0000:00:1c.3:pcie00]
[   22.479194] Allocate Port Service[0000:00:1c.3:pcie02]
[   22.479327] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   22.479419] assign_interrupt_mode Found MSI capability
[   22.479493] Allocate Port Service[0000:00:1c.4:pcie00]
[   22.479521] Allocate Port Service[0000:00:1c.4:pcie02]
[   22.479783] isapnp: Scanning for PnP cards...
[   22.837536] isapnp: No Plug & Play device found
[   22.857599] Real Time Clock Driver v1.12ac
[   22.857682] hpet_resources: 0xfed00000 is busy
[   22.857723] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.859285] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.859337] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.859415] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   22.868319] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.868323] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.891387] mice: PS/2 mouse device common for all mice
[   22.891479] EISA: Probing bus 0 at eisa.0
[   22.891487] Cannot allocate resource for EISA slot 1
[   22.891489] Cannot allocate resource for EISA slot 2
[   22.891491] Cannot allocate resource for EISA slot 3
[   22.891492] Cannot allocate resource for EISA slot 4
[   22.891494] Cannot allocate resource for EISA slot 5
[   22.891495] Cannot allocate resource for EISA slot 6
[   22.891497] Cannot allocate resource for EISA slot 7
[   22.891499] Cannot allocate resource for EISA slot 8
[   22.891500] EISA: Detected 0 cards.
[   22.891502] cpuidle: using governor ladder
[   22.891504] cpuidle: using governor menu
[   22.891567] NET: Registered protocol family 1
[   22.891590] Using IPI No-Shortcut mode
[   22.891612] registered taskstats version 1
[   22.891730]   Magic number: 5:880:387
[   22.891765]   hash matches device 0000:00:1c.4:pcie02
[   22.891775] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.891777] EDD information not available.
[   22.891965] Freeing unused kernel memory: 368k freed
[   22.891984] Write protecting the kernel read-only data: 806k
[   22.896312] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   24.055161] fuse init (API version 7.9)
[   24.068734] ACPI: SSDT BEEE1D72, 02C4 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[   24.068990] ACPI: SSDT BEEE20BB, 061E (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[   24.073046] Monitor-Mwait will be used to enter C-1 state
[   24.073048] Monitor-Mwait will be used to enter C-2 state
[   24.073050] Monitor-Mwait will be used to enter C-3 state
[   24.073156] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   24.073161] ACPI: Processor [CPU0] (supports 8 throttling states)
[   24.073342] ACPI: SSDT BEEE1CAA, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[   24.073579] ACPI: SSDT BEEE2036, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[   24.077611] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   24.077616] ACPI: Processor [CPU1] (supports 8 throttling states)
[   24.081049] ACPI: Thermal Zone [THM0] (38 C)
[   24.082470] ACPI: Thermal Zone [THM1] (32 C)
[   24.193429] usbcore: registered new interface driver usbfs
[   24.193448] usbcore: registered new interface driver hub
[   24.193888] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   24.193890] Copyright (c) 1999-2006 Intel Corporation.
[   24.193937] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 17
[   24.193953] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   24.195129] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1a:6b:38:aa:48
[   24.200916] usbcore: registered new device driver usb
[   24.201760] USB Universal Host Controller Interface driver v3.0
[   24.287108] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   24.287130] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 17
[   24.287143] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   24.287149] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   24.287332] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   24.287368] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001860
[   24.287472] usb usb1: configuration #1 chosen from 1 choice
[   24.287491] hub 1-0:1.0: USB hub found
[   24.287495] hub 1-0:1.0: 2 ports detected
[   24.354400] SCSI subsystem initialized
[   24.368025] libata version 3.00 loaded.
[   24.388252] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[   24.388263] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   24.388267] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   24.388285] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   24.388321] uhci_hcd 0000:00:1a.1: irq 18, io base 0x00001880
[   24.388413] usb usb2: configuration #1 chosen from 1 choice
[   24.388431] hub 2-0:1.0: USB hub found
[   24.388435] hub 2-0:1.0: 2 ports detected
[   24.492092] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.492107] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.492113] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.492130] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   24.492167] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[   24.492262] usb usb3: configuration #1 chosen from 1 choice
[   24.492280] hub 3-0:1.0: USB hub found
[   24.492284] hub 3-0:1.0: 2 ports detected
[   24.595926] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
[   24.595937] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   24.595943] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   24.595962] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   24.595997] uhci_hcd 0000:00:1d.1: irq 21, io base 0x000018c0
[   24.596083] usb usb4: configuration #1 chosen from 1 choice
[   24.596099] hub 4-0:1.0: USB hub found
[   24.596102] hub 4-0:1.0: 2 ports detected
[   24.629357] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   24.700338] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
[   24.700352] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   24.700358] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   24.700375] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   24.700415] uhci_hcd 0000:00:1d.2: irq 22, io base 0x000018e0
[   24.700511] usb usb5: configuration #1 chosen from 1 choice
[   24.700529] hub 5-0:1.0: USB hub found
[   24.700533] hub 5-0:1.0: 2 ports detected
[   24.718666] usb 1-1: configuration #1 chosen from 1 choice
[   24.724257] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 19
[   24.724272] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   24.724277] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   24.724296] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   24.728213] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   24.728223] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfe226c00
[   24.741818] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.741909] usb usb6: configuration #1 chosen from 1 choice
[   24.741928] hub 6-0:1.0: USB hub found
[   24.741932] hub 6-0:1.0: 4 ports detected
[   24.769742] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
[   24.769756] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   24.769761] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   24.769785] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   24.773716] ehci_hcd 0000:00:1d.7: debug port 1
[   24.773727] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   24.773736] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe227000
[   24.778909] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.778983] usb usb7: configuration #1 chosen from 1 choice
[   24.779001] hub 7-0:1.0: USB hub found
[   24.779004] hub 7-0:1.0: 6 ports detected
[   24.787433] ahci 0000:00:1f.2: version 3.0
[   24.787464] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
[   24.787525] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match, using nr_ports
[   24.787527] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   24.800275] Clocksource tsc unstable (delta = -331344570 ns)
[   24.815678] usb 1-1: USB disconnect, address 2
[   24.832718] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   24.840504] usb 1-1: configuration #1 chosen from 1 choice
[   24.867637] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x7 impl SATA mode
[   24.867640] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   24.867648] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.867898] scsi0 : ahci
[   24.868066] scsi1 : ahci
[   24.868202] scsi2 : ahci
[   24.868253] ata1: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 217
[   24.868258] ata2: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226180 irq 217
[   24.868263] ata3: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226200 irq 217
[   24.869176] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   24.876984] usb 1-2: configuration #1 chosen from 1 choice
[   24.933141] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.934104] ata1.00: ATA-8: Hitachi HTS543216L9A300, FB2OC40C, max UDMA/133
[   24.934106] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   24.934747] ata1.00: configured for UDMA/133
[   24.945939] ata2: SATA link down (SStatus 0 SControl 0)
[   24.957877] ata3: SATA link down (SStatus 0 SControl 0)
[   24.958613] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
[   24.958174] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 21
[   24.958186] PCI: Setting latency timer of device 0000:15:00.1 to 64
[   25.010896] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   25.015480] Driver 'sd' needs updating - please use bus_type methods
[   25.015528] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   25.015538] sd 0:0:0:0: [sda] Write Protect is off
[   25.015540] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.015552] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.015592] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   25.015600] sd 0:0:0:0: [sda] Write Protect is off
[   25.015602] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.015615] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.015617]  sda:<6>ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 16
[   25.016661] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.016678] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   25.018852] ata_piix 0000:00:1f.1: version 2.12
[   25.018864] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 16
[   25.018909] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.019244] scsi3 : ata_piix
[   25.019651] scsi4 : ata_piix
[   25.020268] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1830 irq 14
[   25.020270] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1838 irq 15
[   25.038158]  sda1 sda2 < sda5 >
[   25.063466] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.067143] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.227526] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-U10N, 1.05, max UDMA/33
[   25.232181] ata4.00: configured for UDMA/33
[   25.232302] ata5: port disabled. ignoring.
[   25.234612] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-U10N  1.05 PQ: 0 ANSI: 5
[   25.234679] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   25.241089] Driver 'sr' needs updating - please use bus_type methods
[   25.244025] sr0: scsi3-mmc drive: 47x/47x writer dvd-ram cd/rw xa/form2 cdda tray
[   25.244027] Uniform CD-ROM driver Revision: 3.20
[   25.244074] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   25.289452] Attempting manual resume
[   25.289454] swsusp: Resume From Partition 8:5
[   25.289455] PM: Checking swsusp image.
[   25.290150] PM: Resume from disk failed.
[   25.299960] EXT3-fs: INFO: recovery required on readonly filesystem.
[   25.299962] EXT3-fs: write access will be enabled during recovery.
[   25.972311] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00061b032a118cde]
[   26.043369] kjournald starting.  Commit interval 5 seconds
[   26.042864] EXT3-fs: sda1: orphan cleanup on readonly fs
[   26.042869] ext3_orphan_cleanup: deleting unreferenced inode 4833653
[   26.042902] ext3_orphan_cleanup: deleting unreferenced inode 6381589
[   26.042909] EXT3-fs: sda1: 2 orphan inodes deleted
[   26.042910] EXT3-fs: recovery complete.
[   26.046311] EXT3-fs: mounted filesystem with ordered data mode.
[   33.346261] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.382154] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.407044] Linux agpgart interface v0.102
[   33.417226] input: Power Button (FF) as /devices/virtual/input/input2
[   33.441009] ACPI: Power Button (FF) [PWRF]
[   33.441081] input: Lid Switch as /devices/virtual/input/input3
[   33.441875] ACPI: Lid Switch [LID]
[   33.441930] input: Sleep Button (CM) as /devices/virtual/input/input4
[   33.472963] ACPI: Sleep Button (CM) [SLPB]
[   33.649371] ACPI: WMI-Acer: Mapper loaded
[   33.701867] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   33.718157] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   33.719824] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input6
[   33.746112] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   34.017366] ACPI: AC Adapter [AC] (on-line)
[   34.052818] nvidia: module license 'NVIDIA' taints kernel.
[   34.305963] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.305973] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   34.306104] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   34.312491] ACPI: Battery Slot [BAT0] (battery present)
[   34.421209] ricoh-mmc: Ricoh MMC Controller disabling driver
[   34.421212] ricoh-mmc: Copyright(c) Philip Langdale
[   34.421252] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   34.421272] ricoh-mmc: Controller is now disabled.
[   34.517720] Bluetooth: Core ver 2.11
[   34.560646] iTCO_vendor_support: vendor-support=0
[   34.569557] NET: Registered protocol family 31
[   34.569559] Bluetooth: HCI device and connection manager initialized
[   34.569563] Bluetooth: HCI socket layer initialized
[   34.619084] sdhci: Secure Digital Host Controller Interface driver
[   34.619087] sdhci: Copyright(c) Pierre Ossman
[   34.619122] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 21)
[   34.619149] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 22
[   34.619166] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   34.619174] PCI: Setting latency timer of device 0000:15:00.2 to 64
[   34.619214] mmc0: SDHCI at 0xf8101800 irq 22 DMA
[   34.634025] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   34.661721] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   34.661724] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   34.661835] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   34.661860] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   34.661886] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   34.681893] Bluetooth: HCI USB driver ver 2.9
[   34.683378] usbcore: registered new interface driver hci_usb
[   34.705751] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   34.705827] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[   34.705865] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   34.742964] Non-volatile memory driver v1.2
[   34.805816] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   34.805819] thinkpad_acpi: http://ibm-acpi.sf.net/
[   34.805821] thinkpad_acpi: ThinkPad BIOS 7LET44WW (1.14 ), EC 7KHT22WW-1.06
[   34.805822] thinkpad_acpi: Lenovo ThinkPad T61
[   34.806449] thinkpad_acpi: radio switch found; radios are enabled
[   34.812553] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   34.812926] input: ThinkPad Extra Buttons as /devices/virtual/input/input8
[   35.230596] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   35.248076] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[   35.248081] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   35.248102] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.355643] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   35.355647] Socket status: 30000006
[   35.355649] pcmcia: parent PCI bridge I/O window: 0x8000 - 0xbfff
[   35.355651] cs: IO port probe 0x8000-0xbfff: clean.
[   35.356451] pcmcia: parent PCI bridge Memory window: 0xf8100000 - 0xfbffffff
[   35.356453] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   35.466874] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   35.467184] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   35.494708] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   35.494712] serio: Synaptics pass-through port at isa0060/serio1/input0
[   35.531074] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   35.696090] cs: IO port probe 0x100-0x3af: clean.
[   35.697851] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   35.698614] cs: IO port probe 0x820-0x8ff: clean.
[   35.699258] cs: IO port probe 0xc00-0xcf7: clean.
[   35.699985] cs: IO port probe 0xa00-0xaff: clean.
[   35.832329] lp: driver loaded but no devices found
[   35.914624] Adding 6385796k swap on /dev/sda5.  Priority:-1 extents:1 across:6385796k
[   36.339824] EXT3 FS on sda1, internal journal
[   36.826880] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.212136] ACPI: ACPI Dock Station Driver 
[   37.252485] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   37.252491] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   37.252515] ACPI: Error installing bay notify handler
[   37.252518] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
[   38.041026] apm: BIOS not found.
[   38.170183] ppdev: user-space parallel port driver
[   38.302735] audit(1238948535.201:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5365 profile="/usr/sbin/cupsd" namespace="default"
[   38.425858] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input10
[   40.120414] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   40.330976] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input11
[   40.529614] Bluetooth: L2CAP ver 2.9
[   40.529624] Bluetooth: L2CAP socket layer initialized
[   40.609705] Bluetooth: RFCOMM socket layer initialized
[   40.609722] Bluetooth: RFCOMM TTY layer initialized
[   40.609726] Bluetooth: RFCOMM ver 1.8
[   55.254180] NET: Registered protocol family 10
[   55.254679] lo: Disabled Privacy Extensions
[   55.255606] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.256614] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   64.337671] CPU0 attaching NULL sched-domain.
[   64.337678] CPU1 attaching NULL sched-domain.
[   64.364116] CPU0 attaching sched-domain:
[   64.364121]  domain 0: span 03
[   64.364122]   groups: 01 02
[   64.364125] CPU1 attaching sched-domain:
[   64.364126]  domain 0: span 03
[   64.364127]   groups: 02 01
[   64.888750] UDF-fs: Partition marked readonly; forcing readonly mount
[   64.949812] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'CREAM_FAREWELL_CONCERT', timestamp 2005/08/09 17:17 (1f10)
[   66.026798] NET: Registered protocol family 17
[   69.374802] wlan0: Initial auth_alg=0
[   69.374808] wlan0: authenticate with AP 00:17:df:2f:be:f0
[   69.379864] wlan0: Initial auth_alg=0
[   69.379869] wlan0: authenticate with AP 00:17:df:2f:63:51
[   69.383193] wlan0: Initial auth_alg=0
[   69.383197] wlan0: authenticate with AP 00:17:df:2f:63:51
[   69.383206] wlan0: RX authentication from 00:17:df:2f:63:51 (alg=0 transaction=2 status=0)
[   69.383209] wlan0: authenticated
[   69.383211] wlan0: associate with AP 00:17:df:2f:63:51
[   69.386774] wlan0: authentication frame received from 00:17:df:2f:63:51, but not in authenticate state - ignored
[   69.387477] wlan0: authentication frame received from 00:17:df:2f:63:51, but not in authenticate state - ignored
[   69.388618] wlan0: RX AssocResp from 00:17:df:2f:63:51 (capab=0x431 status=0 aid=28)
[   69.388622] wlan0: associated
[   69.390849] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   79.773147] wlan0: no IPv6 routers present
[  130.631004] wlan0: no IPv6 routers present
[  656.467566] irq 23: nobody cared (try booting with the "irqpoll" option)
[  656.467581] Pid: 0, comm: swapper Tainted: P        2.6.24-23-generic #1
[  656.467620]  [<c0169214>] __report_bad_irq+0x24/0x80
[  656.467649]  [<c01694eb>] note_interrupt+0x27b/0x2c0
[  656.467674]  [<f88bfccb>] usb_hcd_irq+0x2b/0x60 [usbcore]
[  656.467725]  [<c0168710>] handle_IRQ_event+0x30/0x60
[  656.467746]  [<c0169ea6>] handle_fasteoi_irq+0x86/0xe0
[  656.467766]  [<c0106f0b>] do_IRQ+0x3b/0x70
[  656.467791]  [<c0105403>] common_interrupt+0x23/0x30
[  656.467816]  [<c012007b>] __is_prefetch+0x3b/0x240
[  656.467833]  [<f8887440>] acpi_idle_enter_bm+0x25b/0x2ce [processor]
[  656.467875]  [<c02957ec>] cpuidle_idle_call+0x7c/0xb0
[  656.467890]  [<c0102695>] cpu_idle+0x45/0xd0
[  656.467942]  =======================
[  656.467945] handlers:
[  656.467948] [<f88bfca0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  656.467985] Disabling IRQ #23
[  751.966804] TCP: Treason uncloaked! Peer 85.225.142.84:63442/3155 shrinks window 281443515:281445827. Repaired.
[  756.400628] TCP: Treason uncloaked! Peer 85.225.142.84:63442/3155 shrinks window 281490619:281492163. Repaired.
[  757.460451] TCP: Treason uncloaked! Peer 85.225.142.84:63442/3155 shrinks window 281500859:281502299. Repaired.
[  760.351690] TCP: Treason uncloaked! Peer 85.225.142.84:63442/3155 shrinks window 281525435:281525467. Repaired.
[  788.984882] TCP: Treason uncloaked! Peer 85.225.142.84:63442/3155 shrinks window 281806500:281809275. Repaired.
[  793.542532] TCP: Treason uncloaked! Peer 85.225.142.84:63442/3155 shrinks window 281849508:281849819. Repaired.
[  798.645901] TCP: Treason uncloaked! Peer 85.225.142.84:63442/3155 shrinks window 281894564:281894707. Repaired.
[  803.221451] TCP: Treason uncloaked! Peer 85.225.142.84:63442/3155 shrinks window 281935524:281936699. Repaired.
[  803.987492] TCP: Treason uncloaked! Peer 85.225.142.84:63442/3155 shrinks window 281936548:281936699. Repaired.
[  959.342557] usb 7-2: new high speed USB device using ehci_hcd and address 2
[  964.335603] ehci_hcd 0000:00:1d.7: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[  974.878505] usb 7-2: device not accepting address 2, error -110
[  974.989337] usb 7-2: new high speed USB device using ehci_hcd and address 3
[  990.527182] usb 7-2: device not accepting address 3, error -110
[  990.640042] usb 7-2: new high speed USB device using ehci_hcd and address 4
[ 1001.066083] usb 7-2: device not accepting address 4, error -110
[ 1001.177371] usb 7-2: new high speed USB device using ehci_hcd and address 5
[ 1011.594443] usb 7-2: device not accepting address 5, error -110

```



I've tried both USB ports; what is full format?

---

### Post by tegnoto89 on 2009-04-05
Ugh!  I borrowed my brother's ipod shuffle to use until I got this figured out, and I'm having the same problem!  For the shuffle, this is what I'm getting for lsusb and sudo fdisk -l

lsusb:

```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 003: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  

```

sudo fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6951

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

```

Any other suggestions are more than welcome!  :-D

---

### Post by tegnoto89 on 2009-04-06
Grr.  Not even flash drives are showing up!  And I have DEFINITELY used flash drives in the past with this computer (not with Hardy though; I downgraded from Intrepid).

---

### Post by sombertattoo on 2009-06-16
My solution to this with a P5Q-E was in the bios under USB Setup, I disabled ehci hand off. Everything worked fine upon boot.

Good luck!

---

