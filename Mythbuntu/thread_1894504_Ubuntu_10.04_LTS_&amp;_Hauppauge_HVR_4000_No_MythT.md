---
title: "Ubuntu 10.04 LTS &amp; Hauppauge HVR 4000 No MythTV"
date: 2011-12-12
forum: Mythbuntu
---

### Post by petatkinson on 2011-12-12
Been away from MythTV for a while and accidently upgraded to 10.10.MythTV broke so I did a fresh install back to 10.04 LTS updated the packages, downloaded MythTV from the MythBuntu site using the option "Install on top of current Ubuntu desktop".Well I'm not having any luck scanning for channels.Went through all the usual routes with no luck.

Setting up the card the Hauppauge HVR4000 is recognised both as DVB-S frontend 0 and DVB-T frontend 1 when probed.

With all the recent changes in versions can I still use 10.04.I downloaded Kaffeine to test the card with no luck but I hear that Kaffeine is posing a few problems too.Just to confirm that MythTV was working under 10.04 before the accidental update.

---

### Post by nickrout on 2011-12-12
if the proper firmware files are not present the card is sometimes seen as "present", but does not work. dmesg should tell you if the firmware is or is not getting loaded. ```
dmesg|grep firmware
```

Try ```
sudo apt-get install linux-firmware-nonfree
```

---

### Post by petatkinson on 2011-12-13
Will do and will report back.

---

### Post by petatkinson on 2011-12-13
Ok.Nothing showing up after dmesg|grep firmware but here is the output of dmesg

[    0.289142] pci 0000:00:0b.0:   MEM window: 0xe0000000-0xe3ffffff
[    0.289145] pci 0000:00:0b.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.289150] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.289153] pci 0000:00:0c.0:   IO window: 0xa000-0xafff
[    0.289156] pci 0000:00:0c.0:   MEM window: disabled
[    0.289159] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.289164] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    0.289166] pci 0000:00:0d.0:   IO window: 0x9000-0x9fff
[    0.289170] pci 0000:00:0d.0:   MEM window: disabled
[    0.289173] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.289185] pci 0000:00:0a.0: setting latency timer to 64
[    0.289192] pci 0000:00:0b.0: setting latency timer to 64
[    0.289199] pci 0000:00:0c.0: setting latency timer to 64
[    0.289206] pci 0000:00:0d.0: setting latency timer to 64
[    0.289210] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.289213] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.289216] pci_bus 0000:01: resource 1 mem: [0xe6000000-0xeaffffff]
[    0.289218] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.289221] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.289223] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.289226] pci_bus 0000:02: resource 1 mem: [0xe0000000-0xe3ffffff]
[    0.289229] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.289231] pci_bus 0000:03: resource 0 io:  [0xa000-0xafff]
[    0.289234] pci_bus 0000:04: resource 0 io:  [0x9000-0x9fff]
[    0.289275] NET: Registered protocol family 2
[    0.289383] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.289767] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.290423] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.290758] TCP: Hash tables configured (established 131072 bind 65536)
[    0.290760] TCP reno registered
[    0.290840] NET: Registered protocol family 1
[    0.371378] pci 0000:02:00.0: Boot video device
[    0.371575] cpufreq-nforce2: No nForce2 chipset.
[    0.371601] Scanning for low memory corruption every 60 seconds
[    0.371724] audit: initializing netlink socket (disabled)
[    0.371736] type=2000 audit(1323777311.371:1): initialized
[    0.374107] Freeing initrd memory: 7765k freed
[    0.382313] highmem bounce pool size: 64 pages
[    0.382319] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.383780] VFS: Disk quotas dquot_6.5.2
[    0.383838] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.384421] fuse init (API version 7.13)
[    0.384507] msgmni has been set to 1636
[    0.384732] alg: No test for stdrng (krng)
[    0.384783] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.384787] io scheduler noop registered
[    0.384788] io scheduler anticipatory registered
[    0.384790] io scheduler deadline registered
[    0.384831] io scheduler cfq registered (default)
[    0.384994]   alloc irq_desc for 24 on node -1
[    0.384996]   alloc kstat_irqs on node -1
[    0.385005] pcieport 0000:00:0b.0: irq 24 for MSI/MSI-X
[    0.385012] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.385102]   alloc irq_desc for 25 on node -1
[    0.385104]   alloc kstat_irqs on node -1
[    0.385109] pcieport 0000:00:0c.0: irq 25 for MSI/MSI-X
[    0.385115] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.385202]   alloc irq_desc for 26 on node -1
[    0.385204]   alloc kstat_irqs on node -1
[    0.385210] pcieport 0000:00:0d.0: irq 26 for MSI/MSI-X
[    0.385215] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.385277] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.385301] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.385404] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.385408] ACPI: Power Button [PWRB]
[    0.385474] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.385476] ACPI: Power Button [PWRF]
[    0.385864] processor LNXCPU:00: registered as cooling_device0
[    0.385903] processor LNXCPU:01: registered as cooling_device1
[    0.389373] isapnp: Scanning for PnP cards...
[    0.390744] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.390842] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.391236] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.392333] brd: module loaded
[    0.392794] loop: module loaded
[    0.392874] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.393067] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.393370] Fixed MDIO Bus: probed
[    0.393404] PPP generic driver version 2.4.2
[    0.393436] tun: Universal TUN/TAP device driver, 1.6
[    0.393438] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.393526] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.393799] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 23
[    0.393804]   alloc irq_desc for 23 on node -1
[    0.393806]   alloc kstat_irqs on node -1
[    0.393811] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AUB2] -> GSI 23 (level, low) -> IRQ 23
[    0.393820] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.393823] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.393854] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.393881] ehci_hcd 0000:00:04.1: debug port 1
[    0.393889] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    0.393903] ehci_hcd 0000:00:04.1: irq 23, io mem 0xeb006000
[    0.403342] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.403422] usb usb1: configuration #1 chosen from 1 choice
[    0.403450] hub 1-0:1.0: USB hub found
[    0.403457] hub 1-0:1.0: 10 ports detected
[    0.403515] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.403776] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 22
[    0.403779]   alloc irq_desc for 22 on node -1
[    0.403781]   alloc kstat_irqs on node -1
[    0.403786] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AUBA] -> GSI 22 (level, low) -> IRQ 22
[    0.403794] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.403797] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.403827] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    0.403847] ohci_hcd 0000:00:04.0: irq 22, io mem 0xeb007000
[    0.461389] usb usb2: configuration #1 chosen from 1 choice
[    0.461414] hub 2-0:1.0: USB hub found
[    0.461422] hub 2-0:1.0: 10 ports detected
[    0.461475] uhci_hcd: USB Universal Host Controller Interface driver
[    0.461550] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.462018] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.462025] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.462089] mice: PS/2 mouse device common for all mice
[    0.462200] rtc_cmos 00:05: RTC can wake from S4
[    0.462234] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.462267] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.462358] device-mapper: uevent: version 1.0.3
[    0.462446] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.462505] device-mapper: multipath: version 1.1.0 loaded
[    0.462508] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.462608] EISA: Probing bus 0 at eisa.0
[    0.462613] Cannot allocate resource for EISA slot 1
[    0.462635] EISA: Detected 0 cards.
[    0.462699] cpuidle: using governor ladder
[    0.462701] cpuidle: using governor menu
[    0.463112] TCP cubic registered
[    0.463264] NET: Registered protocol family 10
[    0.464068] NET: Registered protocol family 17
[    0.464107] Using IPI No-Shortcut mode
[    0.464168] PM: Resume from disk failed.
[    0.464179] registered taskstats version 1
[    0.464559]   Magic number: 7:71:934
[    0.464620] rtc_cmos 00:05: setting system clock to 2011-12-13 11:55:11 UTC (1323777311)
[    0.464623] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.464625] EDD information not available.
[    0.485090] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.742216] isapnp: No Plug & Play device found
[    0.742235] Freeing unused kernel memory: 684k freed
[    0.742739] Write protecting the kernel text: 4836k
[    0.742817] Write protecting the kernel read-only data: 1884k
[    0.758640] udev: starting version 151
[    0.767367] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.842508] pata_amd 0000:00:08.0: version 0.4.1
[    0.842559] pata_amd 0000:00:08.0: setting latency timer to 64
[    0.863250] scsi0 : pata_amd
[    0.865159] Floppy drive(s): fd0 is 1.44M
[    0.867087] scsi1 : pata_amd
[    0.867805] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.867808] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.867972] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.868240] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[    0.868244]   alloc irq_desc for 21 on node -1
[    0.868247]   alloc kstat_irqs on node -1
[    0.868254] forcedeth 0000:00:0f.0: PCI INT A -> Link[APCH] -> GSI 21 (level, low) -> IRQ 21
[    0.868259] forcedeth 0000:00:0f.0: setting latency timer to 64
[    0.883222] FDC 0 is a post-1991 82077
[    1.012314] usb 1-1: configuration #1 chosen from 1 choice
[    1.019366] Initializing USB Mass Storage driver...
[    1.019439] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.019518] usbcore: registered new interface driver usb-storage
[    1.019521] USB Mass Storage support registered.
[    1.019526] usb-storage: device found at 2
[    1.019527] usb-storage: waiting for device to settle before scanning
[    1.148277] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[    1.148282] ata1.00: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/133
[    1.148285] ata1.00: 976773168 sectors, multi 16: LBA48 
[    1.148321] ata1.01: ATAPI: JLMS XJ-HD166S, DS18, max UDMA/33
[    1.148347] ata1: nv_mode_filter: 0x7f39f&0x7f39f->0x7f39f, BIOS=0x7f000 (0xc7c00000) ACPI=0x7f01f (15:60:0x1f)
[    1.148351] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc7c00000) ACPI=0x701f (15:60:0x1f)
[    1.164927] ata1.00: configured for UDMA/133
[    1.165367] ata1.01: configured for UDMA/33
[    1.165659] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKB-0 05.0 PQ: 0 ANSI: 5
[    1.165789] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.166089] scsi 0:0:1:0: CD-ROM            JLMS     XJ-HD166S        DS18 PQ: 0 ANSI: 5
[    1.166271] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.167614] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.167618] Uniform CD-ROM driver Revision: 3.20
[    1.167629] sd 0:0:0:0: [sda] Write Protect is off
[    1.167633] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.167666] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.167726] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.167770] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.167796]  sda:
[    1.167879] ata2: port disabled. ignoring.
[    1.177551]  sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    1.245837] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.248965] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    1.248970]   alloc irq_desc for 18 on node -1
[    1.248972]   alloc kstat_irqs on node -1
[    1.248977] ohci1394 0000:01:07.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    1.304546] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[ea004000-ea0047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.377224] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:d0:91:2a:00
[    1.377228] forcedeth 0000:00:0f.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.377248] ahci 0000:00:0e.0: version 3.0
[    1.377562] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    1.377567]   alloc irq_desc for 20 on node -1
[    1.377569]   alloc kstat_irqs on node -1
[    1.377576] ahci 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    1.377620]   alloc irq_desc for 27 on node -1
[    1.377622]   alloc kstat_irqs on node -1
[    1.377629] ahci 0000:00:0e.0: irq 27 for MSI/MSI-X
[    1.377635] ahci 0000:00:0e.0: controller can do NCQ, turning on CAP_NCQ
[    1.377697] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.377700] ahci 0000:00:0e.0: flags: 64bit ncq sntf led clo pmp pio 
[    1.377704] ahci 0000:00:0e.0: setting latency timer to 64
[    1.378149] scsi3 : ahci
[    1.378226] scsi4 : ahci
[    1.378287] scsi5 : ahci
[    1.378344] scsi6 : ahci
[    1.378474] ata3: SATA max UDMA/133 abar m8192@0xeb004000 port 0xeb004100 irq 27
[    1.378478] ata4: SATA max UDMA/133 abar m8192@0xeb004000 port 0xeb004180 irq 27
[    1.378480] ata5: SATA max UDMA/133 abar m8192@0xeb004000 port 0xeb004200 irq 27
[    1.378483] ata6: SATA max UDMA/133 abar m8192@0xeb004000 port 0xeb004280 irq 27
[    1.584014] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    1.696023] ata4: SATA link down (SStatus 0 SControl 300)
[    1.696513] ata5: SATA link down (SStatus 0 SControl 300)
[    1.696528] ata6: SATA link down (SStatus 0 SControl 300)
[    1.719321] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    1.719326] EXT4-fs (sda6): write access will be enabled during recovery
[    1.797296] usb 2-2: configuration #1 chosen from 1 choice
[    1.810531] usbcore: registered new interface driver hiddev
[    1.816426] input: iPazzPort iPazzPort as /devices/pci0000:00/0000:00:04.0/usb2/2-2/2-2:1.0/input/input4
[    1.816492] generic-usb 0003:0168:1998.0001: input,hidraw0: USB HID v1.11 Keyboard [iPazzPort iPazzPort] on usb-0000:00:04.0-2/input0
[    1.824519] input: iPazzPort iPazzPort as /devices/pci0000:00/0000:00:04.0/usb2/2-2/2-2:1.1/input/input5
[    1.824595] generic-usb 0003:0168:1998.0002: input,hidraw1: USB HID v1.11 Mouse [iPazzPort iPazzPort] on usb-0000:00:04.0-2/input1
[    1.824615] usbcore: registered new interface driver usbhid
[    1.824617] usbhid: v2.6:USB HID core driver
[    1.832216] EXT4-fs (sda6): orphan cleanup on readonly fs
[    1.832224] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 655370
[    1.832251] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 655369
[    1.832261] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 655368
[    1.832269] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 655367
[    1.832278] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 655366
[    1.832285] EXT4-fs (sda6): 5 orphan inodes deleted
[    1.832288] EXT4-fs (sda6): recovery complete
[    1.860013] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.861026] ata3.00: ATA-8: ST3500418AS, CC37, max UDMA/133
[    1.861030] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.862254] ata3.00: configured for UDMA/133
[    1.862358] scsi 3:0:0:0: Direct-Access     ATA      ST3500418AS      CC37 PQ: 0 ANSI: 5
[    1.862488] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.862571] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.862627] sd 3:0:0:0: [sdb] Write Protect is off
[    1.862630] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.862658] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.862804]  sdb: sdb1 sdb2
[    1.878626] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.965350] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    2.092529] usb 2-7: new full speed USB device using ohci_hcd and address 3
[    2.305237] usb 2-7: configuration #1 chosen from 1 choice
[    2.314438] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-7/2-7:1.0/input/input6
[    2.314497] generic-usb 0003:046E:5577.0003: input,hidraw2: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:04.0-7/input0
[    2.321603] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-7/2-7:1.1/input/input7
[    2.321719] generic-usb 0003:046E:5577.0004: input,hiddev96,hidraw3: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:04.0-7/input1
[    2.576123] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[007795a100001fd0]
[    2.624520] usb 2-8: new full speed USB device using ohci_hcd and address 4
[    2.846177] usb 2-8: configuration #1 chosen from 1 choice
[    2.849114] hub 2-8:1.0: USB hub found
[    2.852089] hub 2-8:1.0: 3 ports detected
[    2.878113] udev: starting version 151
[    2.902991] Adding 10740728k swap on /dev/sda7.  Priority:-1 extents:1 across:10740728k 
[    3.153054] usb 2-8.2: new full speed USB device using ohci_hcd and address 5
[    3.277149] usb 2-8.2: configuration #1 chosen from 1 choice
[    3.293310] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:04.0/usb2/2-8/2-8.2/2-8.2:1.0/input/input8
[    3.293384] generic-usb 0003:046D:C71E.0005: input,hidraw4: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:04.0-8.2/input0
[    3.374032] usb 2-8.3: new full speed USB device using ohci_hcd and address 6
[    3.498247] usb 2-8.3: configuration #1 chosen from 1 choice
[    3.692767] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    3.692789] i2c i2c-1: nForce2 SMBus adapter at 0x1c80
[    3.708076] vga16fb: initializing
[    3.708080] vga16fb: mapped to 0xc00a0000
[    3.708237] fb0: VGA16 VGA frame buffer device
[    3.778181] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:04.0/usb2/2-8/2-8.3/2-8.3:1.0/input/input9
[    3.779342] logitech 0003:046D:C71F.0006: input,hiddev97,hidraw5: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:04.0-8.3/input0
[    3.950748] psmouse serio1: ID: 10 00 64
[    3.955944] Console: switching to colour frame buffer device 80x30
[    4.010131] parport_pc 00:0a: reported by Plug and Play ACPI
[    4.010178] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    4.046813] ppdev: user-space parallel port driver
[    4.053299] Linux agpgart interface v0.103
[    4.065135] Linux video capture interface: v2.00
[    4.126061] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input10
[    4.286490] nvidia: module license 'NVIDIA' taints kernel.
[    4.286494] Disabling lock debugging due to kernel taint
[    4.449075] type=1505 audit(1323777315.483:2):  operation="profile_load" pid=537 name="/sbin/dhclient3"
[    4.449786] type=1505 audit(1323777315.483:3):  operation="profile_load" pid=537 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    4.450180] type=1505 audit(1323777315.483:4):  operation="profile_load" pid=537 name="/usr/lib/connman/scripts/dhclient-script"
[    4.450710] type=1505 audit(1323777315.483:5):  operation="profile_replace" pid=532 name="/sbin/dhclient3"
[    4.451428] type=1505 audit(1323777315.483:6):  operation="profile_replace" pid=532 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    4.451821] type=1505 audit(1323777315.483:7):  operation="profile_replace" pid=532 name="/usr/lib/connman/scripts/dhclient-script"
[    5.122426] lp0: using parport0 (interrupt-driven).
[    5.355325] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[    5.355330]   alloc irq_desc for 16 on node -1
[    5.355332]   alloc kstat_irqs on node -1
[    5.355339] nvidia 0000:02:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[    5.355347] nvidia 0000:02:00.0: setting latency timer to 64
[    5.355351] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    5.355558] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[    5.485855] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[    5.486225] cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68,autodetected], frontend(s): 2
[    5.486228] cx88[0]: TV tuner type 63, Radio tuner type -1
[    5.489057] cx2388x alsa driver version 0.0.7 loaded
[    5.489815] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[    5.606585] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
[    5.618478] type=1505 audit(1323777316.651:8):  operation="profile_load" pid=763 name="/usr/sbin/ntpd"
[    5.618487] type=1505 audit(1323777316.651:9):  operation="profile_replace" pid=762 name="/usr/sbin/ntpd"
[    5.684571] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[    5.684605] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[    5.684870] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[    5.684875] HDA Intel 0000:00:09.0: PCI INT A -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[    5.684878] hda_intel: Disable MSI for Nvidia chipset
[    5.684901] HDA Intel 0000:00:09.0: setting latency timer to 64
[    5.743170] tuner 2-0043: chip found @ 0x86 (cx88[0])
[    5.755051] tda9887 2-0043: creating new instance
[    5.755054] tda9887 2-0043: tda988[5/6/7] found
[    5.758048] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[    5.796118] tveeprom 2-0050: Hauppauge model 69009, rev B2D3, serial# 5375849
[    5.796122] tveeprom 2-0050: MAC address is 00-0D-FE-52-07-69
[    5.796125] tveeprom 2-0050: tuner model is Philips FMD1216MEX (idx 133, type 78)
[    5.796128] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[    5.796131] tveeprom 2-0050: audio processor is CX882 (idx 33)
[    5.796133] tveeprom 2-0050: decoder processor is CX882 (idx 25)
[    5.796136] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[    5.796138] cx88[0]: hauppauge eeprom: model=69009
[    5.821354] tuner-simple 2-0061: creating new instance
[    5.821357] tuner-simple 2-0061: type set to 78 (Philips FMD1216MEX MK3 Hybrid Tuner)
[    5.825395] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:0a.0/0000:01:06.2/input/input11
[    5.825451] cx88[0]/2: cx2388x 8802 Driver Manager
[    5.825745] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[    5.825749]   alloc irq_desc for 17 on node -1
[    5.825752]   alloc kstat_irqs on node -1
[    5.825758] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[    5.825766] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 17, latency: 32, mmio: 0xe8000000
[    5.825771] IRQ 17/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.825832] cx88_audio 0000:01:06.1: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[    5.825842] IRQ 17/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.825861] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[    5.826254] cx8800 0000:01:06.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[    5.826261] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 17, latency: 32, mmio: 0xe6000000
[    5.826269] IRQ 17/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.849750] wm8775 2-001b: chip found @ 0x36 (cx88[0])
[    5.856308] cx88[0]/0: registered device video0 [v4l2]
[    5.856398] cx88[0]/0: registered device vbi0
[    5.856485] cx88[0]/0: registered device radio0
[    5.915271] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[    5.915274] cx88/2: registering cx8802 driver, type: dvb access: shared
[    5.915277] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68]
[    5.915280] cx88[0]/2: cx2388x based DVB/ATSC card
[    5.915282] cx8802_alloc_frontends() allocating 2 frontend(s)
[    5.983792] tuner-simple 2-0061: attaching existing instance
[    5.983796] tuner-simple 2-0061: couldn't set type to 63. Using 78 (Philips FMD1216MEX MK3 Hybrid Tuner) instead
[    5.986433] DVB: registering new adapter (cx88[0])
[    5.986437] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
[    5.989414] DVB: registering adapter 0 frontend 1 (Conexant CX22702 DVB-T)...
[    6.008204] usb-storage: device scan complete
[    6.043580] scsi 2:0:0:0: Direct-Access     ST310005 28AS             CC44 PQ: 0 ANSI: 0
[    6.044208] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    6.046560] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    6.048430] sd 2:0:0:0: [sdc] Write Protect is off
[    6.048433] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[    6.048436] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    6.051431] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    6.051435]  sdc: sdc1 sdc2 sdc3 sdc4
[    6.098428] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    6.098433] sd 2:0:0:0: [sdc] Attached SCSI disk
[    6.404933] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:09.0/input/input12
[    6.511378] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    7.552843] EXT4-fs (sda8): mounted filesystem with ordered data mode
[    7.582150] EXT4-fs (sda9): mounted filesystem with ordered data mode
[    8.199718] EXT4-fs (sda10): mounted filesystem with ordered data mode
[   11.269404] type=1505 audit(1323777322.303:10):  operation="profile_replace" pid=1076 name="/sbin/dhclient3"
[   11.270129] type=1505 audit(1323777322.303:11):  operation="profile_replace" pid=1076 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.270527] type=1505 audit(1323777322.303:12):  operation="profile_replace" pid=1076 name="/usr/lib/connman/scripts/dhclient-script"
[   11.299178] type=1505 audit(1323777322.331:13):  operation="profile_load" pid=1075 name="/usr/share/gdm/guest-session/Xsession"
[   11.505271] type=1505 audit(1323777322.539:14):  operation="profile_load" pid=1079 name="/usr/lib/cups/backend/cups-pdf"
[   11.506124] type=1505 audit(1323777322.539:15):  operation="profile_load" pid=1079 name="/usr/sbin/cupsd"
[   11.562022]   alloc irq_desc for 28 on node -1
[   11.562025]   alloc kstat_irqs on node -1
[   11.562034] forcedeth 0000:00:0f.0: irq 28 for MSI/MSI-X
[   11.712851] type=1505 audit(1323777322.747:16):  operation="profile_load" pid=1077 name="/usr/bin/evince"
[   11.722074] type=1505 audit(1323777322.755:17):  operation="profile_load" pid=1077 name="/usr/bin/evince-previewer"
[   11.727648] type=1505 audit(1323777322.759:18):  operation="profile_load" pid=1077 name="/usr/bin/evince-thumbnailer"
[   11.735117] type=1505 audit(1323777322.767:19):  operation="profile_replace" pid=1149 name="/usr/sbin/ntpd"
[   17.849243] __ratelimit: 6 callbacks suppressed
[   17.849246] type=1505 audit(1323777328.883:22):  operation="profile_replace" pid=1289 name="/usr/sbin/mysqld"
[   18.341850] type=1503 audit(1323777329.375:23):  operation="capable" pid=1284 parent=1 profile="/usr/sbin/ntpd" name="dac_override"
[   22.448006] eth0: no IPv6 routers present
[   23.284884] CPU0 attaching NULL sched-domain.
[   23.284890] CPU1 attaching NULL sched-domain.
[   23.308080] CPU0 attaching sched-domain:
[   23.308084]  domain 0: span 0-1 level MC
[   23.308087]   groups: 0 1
[   23.308092] CPU1 attaching sched-domain:
[   23.308094]  domain 0: span 0-1 level MC
[   23.308097]   groups: 1 0
[   27.104108] CPU0 attaching NULL sched-domain.
[   27.104113] CPU1 attaching NULL sched-domain.
[   27.136072] CPU0 attaching sched-domain:
[   27.136076]  domain 0: span 0-1 level MC
[   27.136078]   groups: 0 1
[   27.136083] CPU1 attaching sched-domain:
[   27.136085]  domain 0: span 0-1 level MC
[   27.136088]   groups: 1 0
[   32.731351] kjournald starting.  Commit interval 5 seconds
[   32.731361] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   32.732187] EXT3 FS on sdc2, internal journal
[   32.732190] EXT3-fs: recovery complete.
[   32.732193] EXT3-fs: mounted filesystem with ordered data mode.
[   33.239526] kjournald starting.  Commit interval 5 seconds
[   33.239529] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   33.239918] EXT3 FS on sdc1, internal journal
[   33.239921] EXT3-fs: recovery complete.
[   33.239924] EXT3-fs: mounted filesystem with ordered data mode.
peter@DownStairs:~$

---

### Post by petatkinson on 2011-12-13
I've run Kaffeine and managed to get a scan of Astra 28. When trying to play a Chanel I get the following error message 

"Cannot find demux plugin for MRL "fifo:/home/peter/.kde/share/apps/kaffeine/dvbpipe.m2t".

Any ideas on this one

---

### Post by nickrout on 2011-12-13
So it's working. Why do you need to scan? What happened to all the tuning data in your old database?

---

### Post by petatkinson on 2011-12-13
As I said got Kaffeine to scan and solved the Mux issue.Followed your advice on the drivers so MythTV is working up to the point of scanning for channels.Signal is showing 86% but timeout and no channels found.Diseqc set for LNB Universal so that is not an issue.Tried various options under the "Scan for Channels" and adjusted up the Timeout wait but no joy.

As I said I downloaded the firmware as you suggested and the card is properly recognised as a combo DVB S/DVB T.

Anything else to try at this stage.I repartioned and formatted the drive during installation so no old channel database available.How could I scan and and import a channel.cfg file

---

### Post by nickrout on 2011-12-13
> **petatkinson said:**
> As I said got Kaffeine to scan and solved the Mux issue.Followed your advice on the drivers so MythTV is working up to the point of scanning for channels.Signal is showing 86% but timeout and no channels found.Diseqc set for LNB Universal so that is not an issue.Tried various options under the "Scan for Channels" and adjusted up the Timeout wait but no joy.

As I said I downloaded the firmware as you suggested and the card is properly recognised as a combo DVB S/DVB T.

Anything else to try at this stage.I repartioned and formatted the drive during installation so no old channel database available.How could I scan and and import a channel.cfg file

[LIST=1]
[*]are you sure that is the right lnb type? I know nothing about what is common in your marketplace
[*]are you sure the lnb setting has "stuck", i find the mythtv-setup a bit flaky in this regard
[*]scan each mux rather than a blind scan through every frequency., look at a website like lyngsat.com for details of each mux on your local satellite. There is a howto here for NZ, but the principles are the same. [http://support.openmedia.co.nz/mypvr/support/how-to-set-up-freeview-dth-channels/](http://support.openmedia.co.nz/mypvr/support/how-to-set-up-freeview-dth-channels/)
[/LIST]

---

### Post by petatkinson on 2011-12-13
I'm not sure but I think you are refering to DVB-T and not to DVB-S with your reference to NZ tuning guide.Yes the LNB setting under Diseqc is holding firm and I used the "Scan Channels" option before and got the channels to scan and store.I still think its something simple that is not being set correctly in the setup stage.I'm convinced its down to a conflict between DVB-S and DVB-T with the hybrid card.I really need input from someone scanning under DVB-S but thanks for your input to date.

---

### Post by nickrout on 2011-12-13
> **petatkinson said:**
> I'm not sure but I think you are refering to DVB-T and not to DVB-S with your reference to NZ tuning guide.No I am not. Read the page I referred you to.> Yes the LNB setting under Diseqc is holding firm and I used the "Scan Channels" option before and got the channels to scan and store.I still think its something simple that is not being set correctly in the setup stage.I'm convinced its down to a conflict between DVB-S and DVB-T with the hybrid card.I really need input from someone scanning under DVB-S but thanks for your input to date.Try the indivdual muxes, how can it hurt?

---

### Post by petatkinson on 2011-12-14
Ok.I've tried the individual transponders and have also tried changing from DVB-S and DVB-S2 under the Channel Scan options and the various other settings.At least I know its working under Kaffeine.The device is recognised correctly under the card configuration in MythTV so I assume after installing the NON FREE FIRMWARE at least I have the right drivers installed.I will keep experimenting as one does with MythTV ans see what happens.Thanks for all your input.

Can anyone with a Hauppauge HVR4000 card running under 10.04 LTS and running MythTV give me an idea how they got it working.

---

### Post by bance on 2011-12-14
OK, I have this card,

It works but only the s2 portion, I haven't been able to get DVB-T working. I haven't tried radio or analogue, but they're a bit superflous, really.

I used this[ _guide_]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000") to set it up. I have problems sometimes, but I think it might be because the hvr 4000 doesn't play nicely with other cards. I have two other cards.... a K-world dual DVB-T and a Compro sat card.

I get great quality recordings from the hvr 4000. Things go astray occasionally something or other out of range but I've never figured out what goes wrong, or even what card, a cold reboot usually sorts it.

 I suppose I'm a lazy git!

HTH Steve.

I can have a look at my settings and let you know, what's where, tomorrow. if you like.

---

### Post by petatkinson on 2011-12-17
Yes I'd love to know your settings.It would help a great deal.Also if you could tell me what version of the Linux firmware/drivers you have installed.The annoying thing is I had it all working under 10.04 LTS before the accidental upgrade and I know the card or the hardware is not the problem.

---

### Post by petatkinson on 2011-12-19
Ok.I did the following

1) Fresh install of 10.04 LTS from ISO download.
2) Updates then installed.
3) Linux firmware non-free installed
4) Kaffeine installed to check card working.
5) MythTV 0.23 and MythTV Control Centre installed from Synaptic.
6) Ran MCC followed by MythTV Backend and configured the card from there and now haved just completed a successful scan of Asrtra 28.2.

The only difference to my previous installs was the following

1) I didn't install MythTV from the Mythbuntu site.
2) No install of Medibuntu this time
3) Instead of starting the scan at 10714 H which failed I scanned a higher transponder 12022 V which worked and scanned all available transponders.

The LNB setting under Diseqc option held firm and that basically what I did

As I can't use the DVB-S and the DVB-T simultaneously I will just stick with DVB-S for the moment.

---

