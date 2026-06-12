---
title: "Tv card not working"
date: 2010-10-16
forum: Multimedia Software
---

### Post by Camuflage on 2010-10-16
I own a Pixelview Play Pro Ultra tv card and here are the specs

lspci

```
navyseal@navyseal:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
```


dmesg

```
[    0.273594] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.273599] pci 0000:00:14.4:   bridge window [mem 0xfd000000-0xfdffffff]
[    0.273602] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.273612]   alloc irq_desc for 18 on node -1
[    0.273614]   alloc kstat_irqs on node -1
[    0.273618] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.273621] pci 0000:00:02.0: setting latency timer to 64
[    0.273626] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.273628] pci 0000:00:06.0: setting latency timer to 64
[    0.273635] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.273636] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.273638] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.273640] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.273642] pci_bus 0000:00: resource 8 [mem 0x80000000-0xdfffffff]
[    0.273643] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.273645] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.273647] pci_bus 0000:01: resource 1 [mem 0xfce00000-0xfcefffff]
[    0.273649] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.273651] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.273653] pci_bus 0000:02: resource 1 [mem 0xfcf00000-0xfcffffff]
[    0.273655] pci_bus 0000:03: resource 1 [mem 0xfd000000-0xfdffffff]
[    0.273656] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.273658] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.273660] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.273661] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.273663] pci_bus 0000:03: resource 8 [mem 0x80000000-0xdfffffff]
[    0.273665] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.273694] NET: Registered protocol family 2
[    0.273748] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.273923] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.274374] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.274614] TCP: Hash tables configured (established 131072 bind 65536)
[    0.274616] TCP reno registered
[    0.274618] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.274627] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.274705] NET: Registered protocol family 1
[    0.395140] pci 0000:01:00.0: Boot video device
[    0.395150] PCI: CLS 64 bytes, default 64
[    0.395300] cpufreq-nforce2: No nForce2 chipset.
[    0.395318] Scanning for low memory corruption every 60 seconds
[    0.395391] audit: initializing netlink socket (disabled)
[    0.395400] type=2000 audit(1287227036.392:1): initialized
[    0.402188] highmem bounce pool size: 64 pages
[    0.402191] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.403062] VFS: Disk quotas dquot_6.5.2
[    0.403108] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.403480] fuse init (API version 7.14)
[    0.403535] msgmni has been set to 1682
[    0.405132] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.405134] io scheduler noop registered
[    0.405136] io scheduler deadline registered
[    0.405145] io scheduler cfq registered (default)
[    0.405225] pcieport 0000:00:02.0: setting latency timer to 64
[    0.405244]   alloc irq_desc for 40 on node -1
[    0.405245]   alloc kstat_irqs on node -1
[    0.405252] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.405290] pcieport 0000:00:06.0: setting latency timer to 64
[    0.405306]   alloc irq_desc for 41 on node -1
[    0.405307]   alloc kstat_irqs on node -1
[    0.405310] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    0.405355] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.405369] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.405489] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.405493] ACPI: Power Button [PWRB]
[    0.405521] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.405523] ACPI: Power Button [PWRF]
[    0.405772] ACPI: acpi_idle registered with cpuidle
[    0.408502] ERST: Table is not found!
[    0.408666] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.408769] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.409039] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.409739] brd: module loaded
[    0.410064] loop: module loaded
[    0.410196]   alloc irq_desc for 16 on node -1
[    0.410198]   alloc kstat_irqs on node -1
[    0.410204] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.410230] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.410408] Fixed MDIO Bus: probed
[    0.410427] PPP generic driver version 2.4.2
[    0.410447] tun: Universal TUN/TAP device driver, 1.6
[    0.410449] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.410496] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.410509]   alloc irq_desc for 17 on node -1
[    0.410510]   alloc kstat_irqs on node -1
[    0.410513] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.410523] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.410541] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.410565] ehci_hcd 0000:00:12.2: debug port 1
[    0.410584] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfcdff800
[    0.410614] isapnp: Scanning for PnP cards...
[    0.413899] Freeing initrd memory: 10512k freed
[    0.419020] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.419153] hub 1-0:1.0: USB hub found
[    0.419157] hub 1-0:1.0: 6 ports detected
[    0.419221]   alloc irq_desc for 19 on node -1
[    0.419222]   alloc kstat_irqs on node -1
[    0.419227] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.419242] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.419265] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.419288] ehci_hcd 0000:00:13.2: debug port 1
[    0.419308] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfcdff400
[    0.431125] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.431231] hub 2-0:1.0: USB hub found
[    0.431234] hub 2-0:1.0: 6 ports detected
[    0.431295] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.431309] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.431325] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.431347] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.431371] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfcdfe000
[    0.491229] hub 3-0:1.0: USB hub found
[    0.491236] hub 3-0:1.0: 3 ports detected
[    0.491289] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.491303] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.491328] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.491344] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfcdfd000
[    0.551242] hub 4-0:1.0: USB hub found
[    0.551251] hub 4-0:1.0: 3 ports detected
[    0.551310] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.551325] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.551351] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.551375] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfcdfc000
[    0.611244] hub 5-0:1.0: USB hub found
[    0.611252] hub 5-0:1.0: 3 ports detected
[    0.611305] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.611320] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.611343] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    0.611359] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfcdfb000
[    0.671264] hub 6-0:1.0: USB hub found
[    0.671270] hub 6-0:1.0: 3 ports detected
[    0.671323] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.671339] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    0.671364] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    0.671379] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfcdfa000
[    0.731163] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    0.731279] hub 7-0:1.0: USB hub found
[    0.731285] hub 7-0:1.0: 2 ports detected
[    0.731336] uhci_hcd: USB Universal Host Controller Interface driver
[    0.731401] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.731743] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.731747] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.731811] mice: PS/2 mouse device common for all mice
[    0.731886] rtc_cmos 00:03: RTC can wake from S4
[    0.731911] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.731933] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.731999] device-mapper: uevent: version 1.0.3
[    0.732072] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.732114] device-mapper: multipath: version 1.1.1 loaded
[    0.732116] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.732183] EISA: Probing bus 0 at eisa.0
[    0.732185] EISA: Cannot allocate resource for mainboard
[    0.732187] Cannot allocate resource for EISA slot 1
[    0.732188] Cannot allocate resource for EISA slot 2
[    0.732190] Cannot allocate resource for EISA slot 3
[    0.732191] Cannot allocate resource for EISA slot 4
[    0.732192] Cannot allocate resource for EISA slot 5
[    0.732194] Cannot allocate resource for EISA slot 6
[    0.732195] Cannot allocate resource for EISA slot 7
[    0.732196] Cannot allocate resource for EISA slot 8
[    0.732198] EISA: Detected 0 cards.
[    0.732238] cpuidle: using governor ladder
[    0.732239] cpuidle: using governor menu
[    0.732436] TCP cubic registered
[    0.732517] NET: Registered protocol family 10
[    0.732766] lo: Disabled Privacy Extensions
[    0.732914] NET: Registered protocol family 17
[    0.732932] powernow-k8: Found 1 AMD Athlon(tm) II X2 245 Processor (2 cpu cores) (version 2.20.00)
[    0.732968] powernow-k8:    0 : pstate 0 (2900 MHz)
[    0.732969] powernow-k8:    1 : pstate 1 (2200 MHz)
[    0.732970] powernow-k8:    2 : pstate 2 (1700 MHz)
[    0.732972] powernow-k8:    3 : pstate 3 (800 MHz)
[    0.747129] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.764470] isapnp: No Plug & Play device found
[    0.764573] Using IPI No-Shortcut mode
[    0.764730] PM: Resume from disk failed.
[    0.764738] registered taskstats version 1
[    0.764941]   Magic number: 14:903:74
[    0.765020] rtc_cmos 00:03: setting system clock to 2010-10-16 11:03:57 UTC (1287227037)
[    0.765022] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.765023] EDD information not available.
[    0.765069] Freeing unused kernel memory: 684k freed
[    0.765306] Write protecting the kernel text: 4932k
[    0.765333] Write protecting the kernel read-only data: 1976k
[    0.781753] udev[75]: starting version 163
[    0.847346] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.847365] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.847398] r8169 0000:02:00.0: setting latency timer to 64
[    0.847441]   alloc irq_desc for 42 on node -1
[    0.847442]   alloc kstat_irqs on node -1
[    0.847453] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    0.847806] r8169 0000:02:00.0: eth0: RTL8168b/8111b at 0xf8096000, 00:26:18:6e:fc:da, XID 18000000 IRQ 42
[    0.860815] scsi0 : pata_atiixp
[    0.871175] scsi1 : pata_atiixp
[    0.872282] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    0.872285] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    0.872547] ahci 0000:00:11.0: version 3.0
[    0.872567]   alloc irq_desc for 22 on node -1
[    0.872569]   alloc kstat_irqs on node -1
[    0.872575] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.872622]   alloc irq_desc for 43 on node -1
[    0.872623]   alloc kstat_irqs on node -1
[    0.872632] ahci 0000:00:11.0: irq 43 for MSI/MSI-X
[    0.872720] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.872723] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    0.874958] scsi2 : ahci
[    0.875031] scsi3 : ahci
[    0.875145] scsi4 : ahci
[    0.875184] scsi5 : ahci
[    0.875285] ata3: SATA max UDMA/133 abar m1024@0xfcdffc00 port 0xfcdffd00 irq 43
[    0.875289] ata4: SATA max UDMA/133 abar m1024@0xfcdffc00 port 0xfcdffd80 irq 43
[    0.875291] ata5: SATA max UDMA/133 abar m1024@0xfcdffc00 port 0xfcdffe00 irq 43
[    0.875294] ata6: SATA max UDMA/133 abar m1024@0xfcdffc00 port 0xfcdffe80 irq 43
[    1.056050] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.056522] ata1.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB02, max UDMA/33
[    1.056870] ata1.01: ATA-5: ST340016A, 3.75, max UDMA/100
[    1.056873] ata1.01: 78165360 sectors, multi 16: LBA 
[    1.072438] ata1.00: configured for UDMA/33
[    1.088624] ata1.01: configured for UDMA/100
[    1.090051] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB02 PQ: 0 ANSI: 5
[    1.097032] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.097036] Uniform CD-ROM driver Revision: 3.20
[    1.097141] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.097191] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.097281] scsi 0:0:1:0: Direct-Access     ATA      ST340016A        3.75 PQ: 0 ANSI: 5
[    1.097368] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.097547] sd 0:0:1:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.097653] sd 0:0:1:0: [sda] Write Protect is off
[    1.097656] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.097679] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.097829]  sda: sda1 sda2
[    1.116503] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.172051] ata5: SATA link down (SStatus 0 SControl 300)
[    1.172080] ata4: SATA link down (SStatus 0 SControl 300)
[    1.172380] ata6: SATA link down (SStatus 0 SControl 300)
[    1.195425] Initializing USB Mass Storage driver...
[    1.195528] scsi6 : usb-storage 1-4:1.0
[    1.195589] usbcore: registered new interface driver usb-storage
[    1.195590] USB Mass Storage support registered.
[    1.336050] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.336989] ata3.00: ATA-8: ST3250318AS, CC35, max UDMA/133
[    1.336992] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.338122] ata3.00: configured for UDMA/133
[    1.352181] scsi 2:0:0:0: Direct-Access     ATA      ST3250318AS      CC35 PQ: 0 ANSI: 5
[    1.352321] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.352383] sd 2:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.352445] sd 2:0:0:0: [sdb] Write Protect is off
[    1.352448] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.352472] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.352632]  sdb: sdb1 sdb2
[    1.380932] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.720687] EXT3-fs: barriers not enabled
[    1.737296] kjournald starting.  Commit interval 5 seconds
[    1.737313] EXT3-fs (sda2): mounted filesystem with ordered data mode
[    2.192744] scsi 6:0:0:0: Direct-Access              USB 2.0          5.00 PQ: 0 ANSI: 2
[    2.193109] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    2.194476] sd 6:0:0:0: [sdc] 4136960 512-byte logical blocks: (2.11 GB/1.97 GiB)
[    2.194977] sd 6:0:0:0: [sdc] Write Protect is off
[    2.194981] sd 6:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[    2.194983] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.196728] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.196735]  sdc: sdc4
[    2.198979] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.198983] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   20.342193] udev[433]: starting version 163
[   20.347344] Adding 1028156k swap on /dev/sdb2.  Priority:-1 extents:1 across:1028156k 
[   20.438693] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [??? 0x00000b00-0x00000b0f flags 0x31]
[   20.438696] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.518601] Linux agpgart interface v0.103
[   20.541338] parport_pc 00:06: reported by Plug and Play ACPI
[   20.541411] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   20.544222] lp: driver loaded but no devices found
[   20.550367] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   20.550370] Disabling lock debugging due to kernel taint
[   20.552051] Linux video capture interface: v2.00
[   20.554987] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a4)
[   20.586872] ppdev: user-space parallel port driver
[   20.611234] input: UVC Camera (046d:09a4) as /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/input/input3
[   20.611283] usbcore: registered new interface driver uvcvideo
[   20.611285] USB Video Class driver (v0.1.0)
[   20.619507] [fglrx] Maximum main memory to use for locked dma buffers: 1884 MBytes.
[   20.619730] [fglrx]   vendor: 1002 device: 9490 count: 1
[   20.620216] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
[   20.620230] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.620235] pci 0000:01:00.0: setting latency timer to 64
[   20.620488] [fglrx] Kernel PAT support is enabled
[   20.620506] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   20.632515] lp0: using parport0 (interrupt-driven).
[   20.669503] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.669624] IR NEC protocol handler initialized
[   20.671941] IR RC5(x) protocol handler initialized
[   20.673221] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[   20.673255]   alloc irq_desc for 21 on node -1
[   20.673257]   alloc kstat_irqs on node -1
[   20.673262] cx8800 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.673628] IR RC6 protocol handler initialized
[   20.674940] cx88[0]: Your board has no valid PCI Subsystem ID and thus can't
[   20.674941] cx88[0]: be autodetected.  Please pass card=<n> insmod option to
[   20.674942] cx88[0]: workaround that.  Redirect complaints to the vendor of
[   20.674943] cx88[0]: the TV card.  Best regards,
[   20.674944] cx88[0]:         -- tux
[   20.675123] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   20.675161] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   20.675198] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   20.675234] cx88[0]:    card=2 -> GDI Black Gold
[   20.675277] cx88[0]:    card=3 -> PixelView
[   20.675312] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   20.675351] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   20.675388] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   20.675425] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   20.675469] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   20.675505] cx88[0]:    card=9 -> Leadtek PVR 2000
[   20.675552] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   20.675597] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   20.675633] cx88[0]:    card=12 -> ASUS PVR-416
[   20.675668] cx88[0]:    card=13 -> MSI TV-@nywhere
[   20.675704] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   20.675740] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   20.675776] cx88[0]:    card=16 -> KWorld LTV883RF
[   20.675811] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   20.675850] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   20.675887] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   20.675941] cx88[0]:    card=20 -> Provideo PV259
[   20.675999] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   20.676064] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   20.676102] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   20.676140] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   20.676178] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   20.676224] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   20.676289] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   20.676346] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   20.676384] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   20.676423] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   20.676461] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   20.676499] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   20.676537] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   20.676575] cx88[0]:    card=34 -> ATI HDTV Wonder
[   20.676612] cx88[0]:    card=35 -> WinFast DTV1000-T
[   20.676649] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   20.676687] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   20.676725] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   20.676762] cx88[0]:    card=39 -> KWorld DVB-S 100
[   20.676800] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   20.676838] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   20.676879] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   20.676917] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   20.676955] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   20.676993] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   20.677031] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   20.677069] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   20.677106] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   20.677144] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   20.677182] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   20.677206] IR JVC protocol handler initialized
[   20.677220] cx88[0]:    card=51 -> WinFast DTV2000 H
[   20.677258] cx88[0]:    card=52 -> Geniatech DVB-S
[   20.677296] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   20.677336] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   20.677374] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   20.677415] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   20.677456] cx88[0]:    card=57 -> ADS Tech Instant Video PCI
[   20.677493] cx88[0]:    card=58 -> Pinnacle PCTV HD 800i
[   20.677531] cx88[0]:    card=59 -> DViCO FusionHDTV 5 PCI nano
[   20.677569] cx88[0]:    card=60 -> Pinnacle Hybrid PCTV
[   20.677607] cx88[0]:    card=61 -> Leadtek TV2000 XP Global
[   20.677645] cx88[0]:    card=62 -> PowerColor RA330
[   20.677682] cx88[0]:    card=63 -> Geniatech X8000-MT DVBT
[   20.677719] cx88[0]:    card=64 -> DViCO FusionHDTV DVB-T PRO
[   20.677758] cx88[0]:    card=65 -> DViCO FusionHDTV 7 Gold
[   20.677796] cx88[0]:    card=66 -> Prolink Pixelview MPEG 8000GT
[   20.677834] cx88[0]:    card=67 -> Kworld PlusTV HD PCI 120 (ATSC 120)
[   20.677872] cx88[0]:    card=68 -> Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid
[   20.677911] cx88[0]:    card=69 -> Hauppauge WinTV-HVR4000(Lite) DVB-S/S2
[   20.677954] cx88[0]:    card=70 -> TeVii S460 DVB-S/S2
[   20.677991] cx88[0]:    card=71 -> Omicom SS4 DVB-S/S2 PCI
[   20.678032] cx88[0]:    card=72 -> TBS 8920 DVB-S/S2
[   20.678070] cx88[0]:    card=73 -> TeVii S420 DVB-S
[   20.678107] cx88[0]:    card=74 -> Prolink Pixelview Global Extreme
[   20.678145] cx88[0]:    card=75 -> PROF 7300 DVB-S/S2
[   20.678183] cx88[0]:    card=76 -> SATTRADE ST4200 DVB-S/S2
[   20.678220] cx88[0]:    card=77 -> TBS 8910 DVB-S
[   20.678257] cx88[0]:    card=78 -> Prof 6200 DVB-S
[   20.678294] cx88[0]:    card=79 -> Terratec Cinergy HT PCI MKII
[   20.678332] cx88[0]:    card=80 -> Hauppauge WinTV-IR Only
[   20.678370] cx88[0]:    card=81 -> Leadtek WinFast DTV1800 Hybrid
[   20.678408] cx88[0]:    card=82 -> WinFast DTV2000 H rev. J
[   20.678446] cx88[0]:    card=83 -> Prof 7301 DVB-S/S2
[   20.678483] cx88[0]:    card=84 -> Samsung SMT 7020 DVB-S
[   20.678522] cx88[0]: subsystem: 0000:0000, board: UNKNOWN/GENERIC [card=0,autodetected], frontend(s): 0
[   20.678523] cx88[0]: TV tuner type -1, Radio tuner type -1
[   20.679773] IR Sony protocol handler initialized
[   20.681696] lirc_dev: IR Remote Control driver registered, major 250 
[   20.682524] IR LIRC bridge handler initialized
[   20.697301] type=1400 audit(1287223457.429:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=749 comm="apparmor_parser"
[   20.697556] type=1400 audit(1287223457.429:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=749 comm="apparmor_parser"
[   20.697672] type=1400 audit(1287223457.429:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=749 comm="apparmor_parser"
[   20.713031] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   20.713070]   alloc irq_desc for 44 on node -1
[   20.713072]   alloc kstat_irqs on node -1
[   20.713081] HDA Intel 0000:01:00.1: irq 44 for MSI/MSI-X
[   20.713102] HDA Intel 0000:01:00.1: setting latency timer to 64
[   20.728240] psmouse serio1: ID: 10 00 64
[   20.738749] set volume quirk for QuickCam E3500
[   20.738878] usbcore: registered new interface driver snd-usb-audio
[   20.806908] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   20.807772] tveeprom 0-0050: Huh, no eeprom present (err=-6)?
[   20.810347] cx88[0]/0: found at 0000:03:07.0, rev: 5, irq: 21, latency: 64, mmio: 0xfd000000
[   20.810461] cx88[0]/0: registered device video1 [v4l2]
[   20.810519] cx88[0]/0: registered device vbi0
[   20.810527] tuner 0-0061: tuner type not set
[   20.823171] EXT3-fs (sda2): using internal journal
[   21.303195] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   21.412522] type=1400 audit(1287223458.145:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1144 comm="apparmor_parser"
[   21.413353] type=1400 audit(1287223458.145:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1151 comm="apparmor_parser"
[   21.413557] type=1400 audit(1287223458.145:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1151 comm="apparmor_parser"
[   21.413673] type=1400 audit(1287223458.145:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1151 comm="apparmor_parser"
[   21.415170] type=1400 audit(1287223458.145:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1162 comm="apparmor_parser"
[   21.415460] type=1400 audit(1287223458.145:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1164 comm="apparmor_parser"
[   21.416309] type=1400 audit(1287223458.145:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1164 comm="apparmor_parser"
[   21.418520] r8169 0000:02:00.0: eth0: link up
[   21.418528] r8169 0000:02:00.0: eth0: link up
[   21.955900]   alloc irq_desc for 45 on node -1
[   21.955903]   alloc kstat_irqs on node -1
[   21.955912] fglrx_pci 0000:01:00.0: irq 45 for MSI/MSI-X
[   21.956406] [fglrx] Firegl kernel thread PID: 1356
[   21.956592] [fglrx] IRQ 45 Enabled
[   22.772828] [fglrx] Gart USWC size:628 M.
[   22.772831] [fglrx] Gart cacheable size:247 M.
[   22.772835] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   22.772837] [fglrx] Reserved FB block: Unshared offset:fe07000, size:1f9000 
[   22.772839] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
[   26.754175] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   31.856027] eth0: no IPv6 routers present
[ 1435.592482] show_signal_msg: 9 callbacks suppressed
[ 1435.592494] tvtime[11178]: segfault at 6b0 ip 0804cf64 sp bfc792cc error 4 in tvtime[8048000+76000]
[ 1448.944987] tvtime[11181]: segfault at 6b0 ip 0804cf64 sp bfc6f39c error 4 in tvtime[8048000+76000]
[ 1544.276115] tvtime[11310]: segfault at 6b0 ip 0804cf64 sp bfc46d6c error 4 in tvtime[8048000+76000]
[ 1989.593378] tvtime[12667]: segfault at 6b0 ip 0804cf64 sp bfd679cc error 4 in tvtime[8048000+76000]
[ 3039.510510] tvtime[13005]: segfault at 6b0 ip 0804cf64 sp bfccad7c error 4 in tvtime[8048000+76000]
```

when i run the command tvtime:

```
navyseal@navyseal:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/navyseal/.tvtime/tvtime.xml
videoinput: Driver won't tell us its norm: Argumento inválido
videoinput: Can't get tuner info: Argumento inválido

    Your capture card driver: uvcvideo [UVC Camera (046d:09a4)/usb-0000:00:12.2-2/256]
    does not support full size studio-quality images required by tvtime.
    This is true for many low-quality webcams.  Please select a
    different video device for tvtime to use with the command line
    option --device.

mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
Found "USB Device 0x46d:0x9a4 : USB Audio (hw:2,0)"
Segmentation fail
```

From what i see it starts to read USB (my webcam) instead of reading from the PCI (the tv card).

Any help?

---

### Post by Camuflage on 2010-10-16
bump

---

### Post by TChiOBi on 2010-10-17
try editing /etc/tvtime/tvtime.xml

in terminal with:
sudo gedit /etc/tvtime/tvtime.xml

find the folowing text:

 <!-- This sets the default capture device to use. -->
  <option name="V4LDevice" value="/dev/video0"/>

or it should be like this
where /dev/video0 is the video source, play around with it until it works for you, video0, video1.. depends wich /dev/video is your tv card

hope this helps

---

### Post by Banglaboy on 2010-10-17
Friends,
I am using HP 6730s laptop and Ubuntu 10.10 .. I have a Transcend TVCapture Box 3Q which is working fine in Windows 7. Now, I want to use it in Ubuntu .... How to install it please let me know .....

Thanks ...

---

### Post by Camuflage on 2010-10-17
> **TChiOBi said:**
> try editing /etc/tvtime/tvtime.xml

in terminal with:
sudo gedit /etc/tvtime/tvtime.xml

find the folowing text:

 <!-- This sets the default capture device to use. -->
  <option name="V4LDevice" value="/dev/video0"/>

or it should be like this
where /dev/video0 is the video source, play around with it until it works for you, video0, video1.. depends wich /dev/video is your tv card

hope this helps

I've done that, and keeps always reading the video0 instead the video1.
So i've unplugged my webcam from the USB and now i get this:

```
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/navyseal/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: Ficheiro ou directoria inexistente
mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
Segmentation fail
```

---

### Post by Camuflage on 2010-10-17
Well now it's working, i altered the configuration in the /home/navyseal/.tvtime/tvtime.xml like i did for the /etc/tvtime/tvtime.xml changing video0 to video1

Now i just have to put the sound working.

---

### Post by Meneer Jansen on 2010-10-17
It is beyond me why you have a picture at all in TVTime because from your dmesg uotput I read that Linux can not load the driver for your TV card:
```

Your board has no valid PCI Subsystem ID and thus can't be 
autodetected.  Please pass card=<n> insmod option to 
workaround that.  Redirect complaints to the vendor of the 
TV card.  Best regards,
         -- tux
Here is a list of valid choices for the card=<n> insmod option:
card=0 -> UNKNOWN/GENERIC
card=1 -> Hauppauge WinTV 34xxx models
card=2 -> GDI Black Gold
...
...
**card=27 -> PixelView PlayTV Ultra Pro (Stereo)**
...
...

```
Anyway sound may be redirected via the PCI bus to ALSA (=sounddrivers). Start Gnome-alsamixer to see if your TV card is recognised as an alsa device. If not, connect your TV card directly to your sound card w/ a cable.

Good luck :)

---

### Post by Camuflage on 2010-10-18
I'll try it later and post a new dmesg output.

---

### Post by Camuflage on 2010-10-24
My actual dmesg:

```
[    0.771737] Write protecting the kernel text: 4932k
[    0.771764] Write protecting the kernel read-only data: 1976k
[    0.787161] udev[74]: starting version 163
[    0.799220] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    0.846140] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.846159] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.846191] r8169 0000:02:00.0: setting latency timer to 64
[    0.846233]   alloc irq_desc for 42 on node -1
[    0.846234]   alloc kstat_irqs on node -1
[    0.846245] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    0.846586] r8169 0000:02:00.0: eth0: RTL8168b/8111b at 0xf80be000, 00:26:18:6e:fc:da, XID 18000000 IRQ 42
[    0.850527] scsi0 : pata_atiixp
[    0.862983] scsi1 : pata_atiixp
[    0.864049] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    0.864051] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    0.864078] ahci 0000:00:11.0: version 3.0
[    0.864095]   alloc irq_desc for 22 on node -1
[    0.864097]   alloc kstat_irqs on node -1
[    0.864103] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.864149]   alloc irq_desc for 43 on node -1
[    0.864150]   alloc kstat_irqs on node -1
[    0.864159] ahci 0000:00:11.0: irq 43 for MSI/MSI-X
[    0.864239] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.864242] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    0.874862] scsi2 : ahci
[    0.875643] scsi3 : ahci
[    0.875701] scsi4 : ahci
[    0.875745] scsi5 : ahci
[    0.875850] ata3: SATA max UDMA/133 abar m1024@0xfcdffc00 port 0xfcdffd00 irq 43
[    0.875853] ata4: SATA max UDMA/133 abar m1024@0xfcdffc00 port 0xfcdffd80 irq 43
[    0.875856] ata5: SATA max UDMA/133 abar m1024@0xfcdffc00 port 0xfcdffe00 irq 43
[    0.875859] ata6: SATA max UDMA/133 abar m1024@0xfcdffc00 port 0xfcdffe80 irq 43
[    1.048498] ata1.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB02, max UDMA/33
[    1.048864] ata1.01: ATA-5: ST340016A, 3.75, max UDMA/100
[    1.048867] ata1.01: 78165360 sectors, multi 16: LBA 
[    1.064446] ata1.00: configured for UDMA/33
[    1.080586] ata1.01: configured for UDMA/100
[    1.082031] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB02 PQ: 0 ANSI: 5
[    1.089009] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.089013] Uniform CD-ROM driver Revision: 3.20
[    1.089113] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.089161] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.089252] scsi 0:0:1:0: Direct-Access     ATA      ST340016A        3.75 PQ: 0 ANSI: 5
[    1.089345] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.089521] sd 0:0:1:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.089628] sd 0:0:1:0: [sda] Write Protect is off
[    1.089631] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.089653] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.089841]  sda: sda1 sda2
[    1.102941] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.172049] ata5: SATA link down (SStatus 0 SControl 300)
[    1.172079] ata6: SATA link down (SStatus 0 SControl 300)
[    1.172103] ata4: SATA link down (SStatus 0 SControl 300)
[    1.336033] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.336971] ata3.00: ATA-8: ST3250318AS, CC35, max UDMA/133
[    1.336974] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.338103] ata3.00: configured for UDMA/133
[    1.352163] scsi 2:0:0:0: Direct-Access     ATA      ST3250318AS      CC35 PQ: 0 ANSI: 5
[    1.352297] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.352369] sd 2:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.352429] sd 2:0:0:0: [sdb] Write Protect is off
[    1.352432] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.352455] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.352612]  sdb: sdb1 sdb2
[    1.392303] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.748666] EXT3-fs: barriers not enabled
[    1.765264] kjournald starting.  Commit interval 5 seconds
[    1.765280] EXT3-fs (sda2): mounted filesystem with ordered data mode
[   20.581671] Adding 1028156k swap on /dev/sdb2.  Priority:-1 extents:1 across:1028156k 
[   20.593348] udev[422]: starting version 163
[   20.687259] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [??? 0x00000b00-0x00000b0f flags 0x31]
[   20.687262] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.712129] Linux agpgart interface v0.103
[   20.756138] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   20.756141] Disabling lock debugging due to kernel taint
[   20.772451] Linux video capture interface: v2.00
[   20.783595] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a4)
[   20.812287] input: UVC Camera (046d:09a4) as /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/input/input3
[   20.812449] usbcore: registered new interface driver uvcvideo
[   20.812451] USB Video Class driver (v0.1.0)
[   20.814915] parport_pc 00:06: reported by Plug and Play ACPI
[   20.814966] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   20.851677] ppdev: user-space parallel port driver
[   20.854994] type=1400 audit(1287922048.577:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=706 comm="apparmor_parser"
[   20.855198] type=1400 audit(1287922048.577:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=706 comm="apparmor_parser"
[   20.855314] type=1400 audit(1287922048.577:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=706 comm="apparmor_parser"
[   20.856058] IR NEC protocol handler initialized
[   20.856392] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[   20.856424]   alloc irq_desc for 21 on node -1
[   20.856426]   alloc kstat_irqs on node -1
[   20.856432] cx8800 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.857698] cx88[0]: subsystem: 0000:0000, board: Prolink Pixelview MPEG 8000GT [card=66,insmod option], frontend(s): 0
[   20.857701] cx88[0]: TV tuner type 71, Radio tuner type 0
[   20.868033] IR RC5(x) protocol handler initialized
[   20.872565] [fglrx] Maximum main memory to use for locked dma buffers: 3125 MBytes.
[   20.872707] [fglrx]   vendor: 1002 device: 9490 count: 1
[   20.872909] IR RC6 protocol handler initialized
[   20.873354] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
[   20.873368] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.873372] pci 0000:01:00.0: setting latency timer to 64
[   20.873583] [fglrx] Kernel PAT support is enabled
[   20.873599] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   20.883084] psmouse serio1: ID: 10 00 64
[   20.884368] IR JVC protocol handler initialized
[   20.891812] IR Sony protocol handler initialized
[   20.894748] lirc_dev: IR Remote Control driver registered, major 250 
[   20.897255] IR LIRC bridge handler initialized
[   20.947775] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.985122] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   20.985162]   alloc irq_desc for 44 on node -1
[   20.985164]   alloc kstat_irqs on node -1
[   20.985172] HDA Intel 0000:01:00.1: irq 44 for MSI/MSI-X
[   20.985193] HDA Intel 0000:01:00.1: setting latency timer to 64
[   21.088416] cx88[0]: Test OK
[   21.092695] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   21.093556] tveeprom 0-0050: Huh, no eeprom present (err=-6)?
[   21.189550] EXT3-fs (sda2): using internal journal
[   21.472804] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   21.496823] xc2028 0-0061: creating new instance
[   21.496826] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   21.496829] cx88[0]: Asking xc2028/3028 to load firmware xc3028-v27.fw
[   21.632361] Registered IR keymap rc-pixelview-new
[   21.632436] input: cx88 IR (Prolink Pixelview MPEG as /devices/pci0000:00/0000:00:14.4/0000:03:07.0/rc/rc0/input5
[   21.632490] rc0: cx88 IR (Prolink Pixelview MPEG as /devices/pci0000:00/0000:00:14.4/0000:03:07.0/rc/rc0
[   21.632498] cx88[0]/0: found at 0000:03:07.0, rev: 5, irq: 21, latency: 64, mmio: 0xfd000000
[   21.632545] cx88[0]/0: registered device video1 [v4l2]
[   21.632564] cx88[0]/0: registered device vbi0
[   21.632582] cx88[0]/0: registered device radio0
[   21.840643] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   21.840712] cx88[0]: Calling XC2028/3028 callback
[   21.908511] 2:3:1: cannot set freq 16000 to ep 0x86
[   21.939922] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   21.939926] cx88[0]: Calling XC2028/3028 callback
[   21.958787] type=1400 audit(1287922049.681:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1000 comm="apparmor_parser"
[   21.960888] type=1400 audit(1287922049.685:6): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1002 comm="apparmor_parser"
[   21.965224] type=1400 audit(1287922049.689:7): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1002 comm="apparmor_parser"
[   21.966845] type=1400 audit(1287922049.689:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1002 comm="apparmor_parser"
[   21.970200] type=1400 audit(1287922049.693:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1005 comm="apparmor_parser"
[   21.970469] type=1400 audit(1287922049.693:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1005 comm="apparmor_parser"
[   21.971534] type=1400 audit(1287922049.693:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1006 comm="apparmor_parser"
[   22.010228] r8169 0000:02:00.0: eth0: link up
[   22.010234] r8169 0000:02:00.0: eth0: link up
[   22.585044] set volume quirk for QuickCam E3500
[   22.585174] usbcore: registered new interface driver snd-usb-audio
[   23.580806] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
[   23.606109] SCODE (20000000), id 000000000000b700:
[   23.606112] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   23.612117] xc2028 0-0061: Incorrect readback of firmware version.
[   23.664365] cx88[0]: Calling XC2028/3028 callback
[   23.763577] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   23.763580] cx88[0]: Calling XC2028/3028 callback
[   25.388775] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
[   25.414095] SCODE (20000000), id 000000000000b700:
[   25.414097] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   25.420107] xc2028 0-0061: Incorrect readback of firmware version.
[   25.421633] cx88[0]: Calling XC2028/3028 callback
[   25.542087] cx88[0]: Calling XC2028/3028 callback
[   25.641349] xc2028 0-0061: Loading firmware for type=BASE FM (401), id 0000000000000000.
[   25.641352] cx88[0]: Calling XC2028/3028 callback
[   27.244778] xc2028 0-0061: Loading firmware for type=FM (400), id 0000000000000000.
[   27.268009] xc2028 0-0061: Incorrect readback of firmware version.
[   27.320032] cx88[0]: Calling XC2028/3028 callback
[   27.419290] xc2028 0-0061: Loading firmware for type=BASE FM (401), id 0000000000000000.
[   27.419294] cx88[0]: Calling XC2028/3028 callback
[   29.024786] xc2028 0-0061: Loading firmware for type=FM (400), id 0000000000000000.
[   29.048059] xc2028 0-0061: Incorrect readback of firmware version.
[   29.049020] cx88[0]: Calling XC2028/3028 callback
[   29.231070] lp0: using parport0 (interrupt-driven).
[   29.633037]   alloc irq_desc for 45 on node -1
[   29.633040]   alloc kstat_irqs on node -1
[   29.633048] fglrx_pci 0000:01:00.0: irq 45 for MSI/MSI-X
[   29.633532] [fglrx] Firegl kernel thread PID: 1394
[   29.633717] [fglrx] IRQ 45 Enabled
[   30.252974] [fglrx] Gart USWC size:1024 M.
[   30.252977] [fglrx] Gart cacheable size:405 M.
[   30.252981] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   30.252984] [fglrx] Reserved FB block: Unshared offset:fccb000, size:335000 
[   30.252986] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
[   32.832337] eth0: no IPv6 routers present
[   34.397634] hda-intel: IRQ timing workaround is activated for card #2. Suggest a bigger bdl_pos_adj.
[  383.132477] cx88[0]: Calling XC2028/3028 callback
[  383.231758] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  383.231770] cx88[0]: Calling XC2028/3028 callback
[  384.864840] (0), id 00000000000000f7:
[  384.864843] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  384.890131] SCODE (20000000), id 0000000100000007:
[  384.890134] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  384.896140] xc2028 0-0061: Incorrect readback of firmware version.
[  384.952061] cx88[0]: Calling XC2028/3028 callback
[  385.051342] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  385.051353] cx88[0]: Calling XC2028/3028 callback
[  386.685092] (0), id 00000000000000f7:
[  386.685095] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  386.710379] SCODE (20000000), id 0000000100000007:
[  386.710382] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  386.716391] xc2028 0-0061: Incorrect readback of firmware version.
[  386.717864] cx88[0]: Calling XC2028/3028 callback
[  387.128488] cx88[0]: Calling XC2028/3028 callback
[  387.227770] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  387.227782] cx88[0]: Calling XC2028/3028 callback
[  388.861005] (0), id 00000000000000f7:
[  388.861008] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  388.886317] SCODE (20000000), id 0000000100000007:
[  388.886319] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  388.892328] xc2028 0-0061: Incorrect readback of firmware version.
[  388.944053] cx88[0]: Calling XC2028/3028 callback
[  389.043337] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  389.043348] cx88[0]: Calling XC2028/3028 callback
[  390.677092] (0), id 00000000000000f7:
[  390.677095] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  390.702392] SCODE (20000000), id 0000000100000007:
[  390.702394] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  390.708406] xc2028 0-0061: Incorrect readback of firmware version.
[  390.709881] cx88[0]: Calling XC2028/3028 callback
[  391.009778] cx88[0]: Calling XC2028/3028 callback
[  391.109178] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  391.109192] cx88[0]: Calling XC2028/3028 callback
[  392.745091] (0), id 00000000000000f7:
[  392.745094] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  392.770387] SCODE (20000000), id 0000000100000007:
[  392.770389] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  392.776395] xc2028 0-0061: Incorrect readback of firmware version.
[  392.832073] cx88[0]: Calling XC2028/3028 callback
[  392.931355] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  392.931366] cx88[0]: Calling XC2028/3028 callback
[  394.560856] (0), id 00000000000000f7:
[  394.560860] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  394.586331] SCODE (20000000), id 0000000100000007:
[  394.586334] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  394.592401] xc2028 0-0061: Incorrect readback of firmware version.
[  394.593880] cx88[0]: Calling XC2028/3028 callback
[  414.344483] cx88[0]: Calling XC2028/3028 callback
[  414.443837] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  414.443850] cx88[0]: Calling XC2028/3028 callback
[  416.092910] (0), id 00000000000000f7:
[  416.092913] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  416.118369] SCODE (20000000), id 0000000100000007:
[  416.118372] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  416.124389] xc2028 0-0061: Incorrect readback of firmware version.
[  416.180054] cx88[0]: Calling XC2028/3028 callback
[  416.279337] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  416.279348] cx88[0]: Calling XC2028/3028 callback
[  417.909152] (0), id 00000000000000f7:
[  417.909155] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  417.934469] SCODE (20000000), id 0000000100000007:
[  417.934472] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  417.940480] xc2028 0-0061: Incorrect readback of firmware version.
[  417.941952] cx88[0]: Calling XC2028/3028 callback
[  418.316475] cx88[0]: Calling XC2028/3028 callback
[  418.415759] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  418.415771] cx88[0]: Calling XC2028/3028 callback
[  420.049008] (0), id 00000000000000f7:
[  420.049012] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  420.074322] SCODE (20000000), id 0000000100000007:
[  420.074324] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  420.080337] xc2028 0-0061: Incorrect readback of firmware version.
[  420.136062] cx88[0]: Calling XC2028/3028 callback
[  420.235344] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  420.235356] cx88[0]: Calling XC2028/3028 callback
[  421.869114] (0), id 00000000000000f7:
[  421.869117] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  421.894440] SCODE (20000000), id 0000000100000007:
[  421.894444] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  421.900459] xc2028 0-0061: Incorrect readback of firmware version.
[  421.901933] cx88[0]: Calling XC2028/3028 callback
[  422.185277] cx88[0]: Calling XC2028/3028 callback
[  422.284563] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  422.284574] cx88[0]: Calling XC2028/3028 callback
[  423.916915] (0), id 00000000000000f7:
[  423.916918] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  423.942219] SCODE (20000000), id 0000000100000007:
[  423.942221] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  423.948230] xc2028 0-0061: Incorrect readback of firmware version.
[  424.004079] cx88[0]: Calling XC2028/3028 callback
[  424.103362] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  424.103373] cx88[0]: Calling XC2028/3028 callback
[  425.737018] (0), id 00000000000000f7:
[  425.737022] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  425.763068] SCODE (20000000), id 0000000100000007:
[  425.763071] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  425.769082] xc2028 0-0061: Incorrect readback of firmware version.
[  425.770557] cx88[0]: Calling XC2028/3028 callback
[  441.456458] cx88[0]: Calling XC2028/3028 callback
[  441.555746] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  441.555758] cx88[0]: Calling XC2028/3028 callback
[  443.184847] (0), id 00000000000000f7:
[  443.184850] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  443.210254] SCODE (20000000), id 0000000100000007:
[  443.210256] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  443.216263] xc2028 0-0061: Incorrect readback of firmware version.
[  443.272037] cx88[0]: Calling XC2028/3028 callback
[  443.371320] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  443.371332] cx88[0]: Calling XC2028/3028 callback
[  445.005112] (0), id 00000000000000f7:
[  445.005116] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  445.030435] SCODE (20000000), id 0000000100000007:
[  445.030437] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  445.036450] xc2028 0-0061: Incorrect readback of firmware version.
[  445.037927] cx88[0]: Calling XC2028/3028 callback
[  445.412486] cx88[0]: Calling XC2028/3028 callback
[  445.511770] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  445.511782] cx88[0]: Calling XC2028/3028 callback
[  447.144863] (0), id 00000000000000f7:
[  447.144867] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  447.170187] SCODE (20000000), id 0000000100000007:
[  447.170190] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  447.176198] xc2028 0-0061: Incorrect readback of firmware version.
[  447.228053] cx88[0]: Calling XC2028/3028 callback
[  447.327337] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  447.327347] cx88[0]: Calling XC2028/3028 callback
[  448.960917] (0), id 00000000000000f7:
[  448.960920] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  448.986241] SCODE (20000000), id 0000000100000007:
[  448.986243] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  448.992255] xc2028 0-0061: Incorrect readback of firmware version.
[  448.993742] cx88[0]: Calling XC2028/3028 callback
[  449.277702] cx88[0]: Calling XC2028/3028 callback
[  449.376963] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  449.376967] cx88[0]: Calling XC2028/3028 callback
[  451.008998] (0), id 00000000000000f7:
[  451.009002] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  451.034284] SCODE (20000000), id 0000000100000007:
[  451.034286] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  451.040292] xc2028 0-0061: Incorrect readback of firmware version.
[  451.096075] cx88[0]: Calling XC2028/3028 callback
[  451.195358] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  451.195369] cx88[0]: Calling XC2028/3028 callback
[  452.824936] (0), id 00000000000000f7:
[  452.824939] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  452.850251] SCODE (20000000), id 0000000100000007:
[  452.850254] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  452.856267] xc2028 0-0061: Incorrect readback of firmware version.
[  452.857753] cx88[0]: Calling XC2028/3028 callback
[  475.919941] usb 1-2: USB disconnect, address 2
[  485.756785] cx88[0]: Calling XC2028/3028 callback
[  485.856068] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  485.856081] cx88[0]: Calling XC2028/3028 callback
[  487.525548] (0), id 00000000000000f7:
[  487.525551] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  487.550976] SCODE (20000000), id 0000000100000007:
[  487.550978] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  487.556984] xc2028 0-0061: Incorrect readback of firmware version.
[  487.612380] cx88[0]: Calling XC2028/3028 callback
[  487.711661] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  487.711672] cx88[0]: Calling XC2028/3028 callback
[  489.361552] (0), id 00000000000000f7:
[  489.361556] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  489.386992] SCODE (20000000), id 0000000100000007:
[  489.386995] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  489.393063] xc2028 0-0061: Incorrect readback of firmware version.
[  489.394538] cx88[0]: Calling XC2028/3028 callback
[  489.820786] cx88[0]: Calling XC2028/3028 callback
[  489.920069] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  489.920081] cx88[0]: Calling XC2028/3028 callback
[  491.585549] (0), id 00000000000000f7:
[  491.585552] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  491.611083] SCODE (20000000), id 0000000100000007:
[  491.611086] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  491.617160] xc2028 0-0061: Incorrect readback of firmware version.
[  491.672381] cx88[0]: Calling XC2028/3028 callback
[  491.771664] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  491.771674] cx88[0]: Calling XC2028/3028 callback
[  493.417736] (0), id 00000000000000f7:
[  493.417739] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  493.443173] SCODE (20000000), id 0000000100000007:
[  493.443176] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  493.449247] xc2028 0-0061: Incorrect readback of firmware version.
[  493.450723] cx88[0]: Calling XC2028/3028 callback
[  493.758259] cx88[0]: Calling XC2028/3028 callback
[  493.857544] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  493.857557] cx88[0]: Calling XC2028/3028 callback
[  495.505334] (0), id 00000000000000f7:
[  495.505343] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  495.530920] SCODE (20000000), id 0000000100000007:
[  495.530922] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  495.536928] xc2028 0-0061: Incorrect readback of firmware version.
[  495.596048] cx88[0]: Calling XC2028/3028 callback
[  495.695326] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  495.695337] cx88[0]: Calling XC2028/3028 callback
[  497.341084] (0), id 00000000000000f7:
[  497.341089] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[  497.366490] SCODE (20000000), id 0000000100000007:
[  497.366493] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[  497.372509] xc2028 0-0061: Incorrect readback of firmware version.
[  497.373983] cx88[0]: Calling XC2028/3028 callback
```

I have image but no sound. Interesting to know is that if i have the webcam plugged to the usb tvtimer tries to read it instead of reading the tvcard, but if i unplug the webcam it reads the tvcard...
Installed the gnome-alsamixer but no sound yet.

---

### Post by Meneer Jansen on 2010-10-24
How many devices does *gnome-alsamixer* show (screenshot)?

P.S. All video for Linux (v4l) devices get named */dev/videoX*. TVTime probably looks per default to */dev/video0*. When you plug in your webcam (= a v4l device!) it probably gets named */dev/video0*.

---

### Post by Camuflage on 2010-10-30
How do i change the webcam video from 0 to another number device?
See the attachment for screenshot of alsa.

---

### Post by Meneer Jansen on 2010-10-30
I don't think I see your TV card in gnome-alsamixer. I'd plug my PC speakers in the TV card directly If I were you.

---

### Post by ultimajji on 2010-11-01
Hi guys!

I need some help setting up WinFast DTV2000 H rev. J tv tuner (card = 82) according to dmesg.
I have Ubuntu 10.10 32 bit installed, Nvidia VGA card (i'm using the default nouveau driver) and Creative SB-XFI soundcard.
When i first installed tvtime, the channel scan was successful, and i managed to get sound too by using sox.
However, my problem is when I reboot, then start up tvtime, I just get a blue screen with no signal, I tried to rescan the channels but tvtime can't seem to find any channels. But if I reboot again, then everything goes back to normal, tvtime suddenly finds all the channels again, but if I reboot again, I still get the blue screen no signal, so basically it means i can use tvtime in every second system boot, it's weird isn't it?
I also checked the tuner in windows xp, and it's fine, so I don't think it's hardware related problem.
Any thoughts what could be the problem? Thanks in advance.

---

