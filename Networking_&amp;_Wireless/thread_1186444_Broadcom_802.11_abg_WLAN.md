---
title: "Broadcom 802.11 a/b/g WLAN"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by freak937 on 2009-06-13
Hi, i am very new to ubuntu and linux in general.

I bought a new notebook recently (hp pavillion tx2650eg) and couldn't manage to get the WLAN working. Could you give me some advice please? I just did a Forum search but couldn't fint anything working for me. If you need some additional infos feel free to ask, but please add the shell commands or where i can find the information you request.

thank you

just read the sticky

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:23:8b:1d:8c:df  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe1d:8cdf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16927778 (16.1 MB)  TX bytes:2043928 (1.9 MB)
          Interrupt:220 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:6b:9e:21  
          inet6 addr: fe80::221:ff:fe6b:9e21/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:12643
          TX packets:0 errors:371 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1:avahi Link encap:Ethernet  HWaddr 00:21:00:6b:9e:21  
          inet addr:169.254.4.128  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98885 (96.5 KB)  TX bytes:98885 (96.5 KB)


**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:163
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


**lsb_release -d**
Description:    Ubuntu 8.04.2

**dmesg**
[   20.665942] EISA bus registered
[   20.665948] ACPI: bus type pci registered
[   20.667298] PCI: Using configuration type 1
[   20.667312] Setting up standard PCI resources
[   20.674286] ACPI: EC: Look up EC in DSDT
[   20.679299] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   20.679767] ACPI: Interpreter enabled
[   20.679772] ACPI: (supports S0 S3 S4 S5)
[   20.679801] ACPI: Using IOAPIC for interrupt routing
[   20.582432] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   20.595612] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[   20.595614] ACPI: EC: driver started in interrupt mode
[   20.595678] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.597716] PCI: Transparent bridge - 0000:00:14.4
[   20.597750] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.597985] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   20.598086] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   20.598203] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   20.598317] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   20.598450] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   20.609176] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   20.609369] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   20.609562] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   20.609713] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   20.609864] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   20.609992] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   20.610178] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   20.610373] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   20.610562] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.610606] pnp: PnP ACPI init
[   20.610611] ACPI: bus type pnp registered
[   20.615086] pnp: PnP ACPI: found 12 devices
[   20.615088] ACPI: ACPI bus type pnp unregistered
[   20.615091] PnPBIOS: Disabled by ACPI PNP
[   20.615559] PCI: Using ACPI for IRQ routing
[   20.615562] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.630146] NET: Registered protocol family 8
[   20.630148] NET: Registered protocol family 20
[   20.630286] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   20.630290] hpet0: 4 32-bit timers, 14318180 Hz
[   20.631331] AppArmor: AppArmor Filesystem Enabled
[   20.732053] Time: hpet clocksource has been installed.
[   20.732071] Switched to high resolution mode on CPU 0
[   20.634159] Switched to high resolution mode on CPU 1
[   20.643001] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   20.643004] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   20.643011] system 00:09: ioport range 0x400-0x4cf has been reserved
[   20.643013] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   20.643015] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
[   20.643018] system 00:09: ioport range 0x680-0x6ff has been reserved
[   20.643020] system 00:09: ioport range 0x77a-0x77a has been reserved
[   20.643022] system 00:09: ioport range 0xc00-0xc01 has been reserved
[   20.643024] system 00:09: ioport range 0xc14-0xc14 has been reserved
[   20.643027] system 00:09: ioport range 0xc50-0xc52 has been reserved
[   20.643029] system 00:09: ioport range 0xc6c-0xc6c has been reserved
[   20.643031] system 00:09: ioport range 0xc6f-0xc6f has been reserved
[   20.643033] system 00:09: ioport range 0xcd0-0xcdb has been reserved
[   20.643038] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[   20.643041] system 00:0a: iomem range 0xfff00000-0xffffffff could not be reserved
[   20.673909] PCI: Bridge: 0000:00:01.0
[   20.673911]   IO window: 5000-5fff
[   20.673915]   MEM window: d2200000-d23fffff
[   20.673917]   PREFETCH window: c0000000-cfffffff
[   20.673921] PCI: Bridge: 0000:00:04.0
[   20.673923]   IO window: 3000-4fff
[   20.673926]   MEM window: d1200000-d21fffff
[   20.673929]   PREFETCH window: d0000000-d0ffffff
[   20.673932] PCI: Bridge: 0000:00:05.0
[   20.673933]   IO window: disabled.
[   20.673936]   MEM window: d1100000-d11fffff
[   20.673939]   PREFETCH window: disabled.
[   20.673943] PCI: Bridge: 0000:00:06.0
[   20.673945]   IO window: 2000-2fff
[   20.673948]   MEM window: b0000000-b00fffff
[   20.673951]   PREFETCH window: d1000000-d10fffff
[   20.673954] PCI: Bridge: 0000:00:14.4
[   20.673990]   IO window: 1000-1fff
[   20.673995]   MEM window: disabled.
[   20.673999]   PREFETCH window: disabled.
[   20.674013] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.674024] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.674028] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   20.674037] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   20.674040] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   20.674049] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   20.674052] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   20.674069] NET: Registered protocol family 2
[   20.710753] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.710980] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.711548] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   20.711840] TCP: Hash tables configured (established 131072 bind 65536)
[   20.711843] TCP reno registered
[   20.722776] checking if image is initramfs... it is
[   21.266513] Freeing initrd memory: 7319k freed
[   21.266632] Simple Boot Flag at 0x44 set to 0x1
[   21.267942] audit: initializing netlink socket (disabled)
[   21.267953] audit(1244909925.504:1): initialized
[   21.268211] highmem bounce pool size: 64 pages
[   21.271397] VFS: Disk quotas dquot_6.5.1
[   21.271472] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.271595] io scheduler noop registered
[   21.271597] io scheduler anticipatory registered
[   21.271598] io scheduler deadline registered
[   21.271607] io scheduler cfq registered (default)
[   21.718191] Boot video device is 0000:01:05.0
[   21.718536] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   21.718566] assign_interrupt_mode Found MSI capability
[   21.718596] Allocate Port Service[0000:00:04.0:pcie00]
[   21.718729] Allocate Port Service[0000:00:04.0:pcie02]
[   21.718824] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   21.718852] assign_interrupt_mode Found MSI capability
[   21.718878] Allocate Port Service[0000:00:05.0:pcie00]
[   21.718988] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   21.719016] assign_interrupt_mode Found MSI capability
[   21.719041] Allocate Port Service[0000:00:06.0:pcie00]
[   21.719598] isapnp: Scanning for PnP cards...
[   22.102224] isapnp: No Plug & Play device found
[   22.150456] Real Time Clock Driver v1.12ac
[   22.150685] hpet_resources: 0xfed00000 is busy
[   22.150752] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.152758] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.152828] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.153000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.174350] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.174355] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.193595] mice: PS/2 mouse device common for all mice
[   22.193857] EISA: Probing bus 0 at eisa.0
[   22.193864] Cannot allocate resource for EISA slot 1
[   22.193866] Cannot allocate resource for EISA slot 2
[   22.193868] Cannot allocate resource for EISA slot 3
[   22.193870] Cannot allocate resource for EISA slot 4
[   22.193871] Cannot allocate resource for EISA slot 5
[   22.193873] Cannot allocate resource for EISA slot 6
[   22.193883] EISA: Detected 0 cards.
[   22.193885] cpuidle: using governor ladder
[   22.193887] cpuidle: using governor menu
[   22.193958] NET: Registered protocol family 1
[   22.193979] Using IPI No-Shortcut mode
[   22.194010] registered taskstats version 1
[   22.194139]   Magic number: 13:942:337
[   22.194147]   hash matches device ttyzc
[   22.194190]   hash matches device tty58
[   22.194215] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.194217] EDD information not available.
[   22.194427] Freeing unused kernel memory: 368k freed
[   22.194449] Write protecting the kernel read-only data: 806k
[   22.232357] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   23.469050] fuse init (API version 7.9)
[   23.592721] ACPI: Processor [CPU0] (supports 8 throttling states)
[   23.499179] ACPI: Thermal Zone [THRM] (46 C)
[   23.987243] SCSI subsystem initialized
[   24.077545] r8169 Gigabit Ethernet driver 2.2LK loaded
[   24.077581] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   24.077607] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   24.078031] eth0: RTL8168c/8111c at 0xf8852000, 00:23:8b:1d:8c:df, XID 3c2000c0 IRQ 220
[   24.099885] usbcore: registered new interface driver usbfs
[   24.099918] usbcore: registered new interface driver hub
[   24.099998] libata version 3.00 loaded.
[   24.100282] usbcore: registered new device driver usb
[   24.104209] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   24.104309] PCI: Setting latency timer of device 0000:00:14.1 to 64
[   24.121528] scsi0 : pata_atiixp
[   24.123437] scsi1 : pata_atiixp
[   24.124257] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6000 irq 14
[   24.124262] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6008 irq 15
[   24.124351] ata1: port disabled. ignoring.
[   24.124568] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.282448] ahci 0000:00:11.0: version 3.0
[   24.282535] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 19
[   24.282566] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
[   25.280072] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   25.280080] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pio 
[   25.281026] scsi2 : ahci
[   25.281141] scsi3 : ahci
[   25.281229] scsi4 : ahci
[   25.281319] scsi5 : ahci
[   25.281415] scsi6 : ahci
[   25.281503] scsi7 : ahci
[   25.281586] ata3: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409100 irq 19
[   25.281592] ata4: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409180 irq 19
[   25.281598] ata5: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409200 irq 19
[   25.281603] ata6: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409280 irq 19
[   25.281609] ata7: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409300 irq 19
[   25.281615] ata8: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409380 irq 19
[   25.754348] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   25.657180] ata3.00: ATA-8: Hitachi HTS543232L9A300, FB4OC40C, max UDMA/133
[   25.657185] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   25.658279] ata3.00: configured for UDMA/133
[   26.232650] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   26.290111] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T50L, SC04, max UDMA/100
[   26.450535] ata4.00: configured for UDMA/100
[   26.858445] ata5: SATA link down (SStatus 0 SControl 300)
[   27.169344] ata6: SATA link down (SStatus 0 SControl 300)
[   27.480248] ata7: SATA link down (SStatus 0 SControl 300)
[   27.791148] ata8: SATA link down (SStatus 0 SControl 300)
[   27.791300] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54323 FB4O PQ: 0 ANSI: 5
[   27.696802] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50L  SC04 PQ: 0 ANSI: 5
[   27.795058] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.795092] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   27.795099] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   27.795495] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   27.795557] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2408000
[   27.704522] Driver 'sd' needs updating - please use bus_type methods
[   27.704602] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   27.704613] sd 2:0:0:0: [sda] Write Protect is off
[   27.704615] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.704629] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.704673] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   27.704681] sd 2:0:0:0: [sda] Write Protect is off
[   27.704683] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.704695] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.704698]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   27.730086]  sda1 sda2 sda3 sda4 < sda5<6>usb usb1: configuration #1 chosen from 1 choice
[   27.855123] hub 1-0:1.0: USB hub found
[   27.855171] hub 1-0:1.0: 3 ports detected
[   27.769700]  sda6 >
[   27.769818] sd 2:0:0:0: [sda] Attached SCSI disk
[   27.874989] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   27.875021] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   27.790913] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   27.790918] Uniform CD-ROM driver Revision: 3.20
[   27.790957] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   27.962668] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 16
[   27.962694] PCI: Setting latency timer of device 0000:00:12.1 to 64
[   27.962701] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   27.962741] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[   27.962765] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2407000
[   28.018504] usb usb2: configuration #1 chosen from 1 choice
[   28.018546] hub 2-0:1.0: USB hub found
[   28.018592] hub 2-0:1.0: 3 ports detected
[   28.122080] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
[   28.122103] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   28.122109] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   28.122148] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[   28.122174] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd2406000
[   28.181893] usb usb3: configuration #1 chosen from 1 choice
[   28.181925] hub 3-0:1.0: USB hub found
[   28.181968] hub 3-0:1.0: 3 ports detected
[   28.273438] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   28.281508] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 18
[   28.281523] PCI: Setting latency timer of device 0000:00:13.1 to 64
[   28.281528] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   28.281562] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[   28.281623] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd2405000
[   28.341314] usb usb4: configuration #1 chosen from 1 choice
[   28.341345] hub 4-0:1.0: USB hub found
[   28.341355] hub 4-0:1.0: 3 ports detected
[   28.444932] ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 18
[   28.444944] PCI: Setting latency timer of device 0000:00:14.5 to 64
[   28.444950] ohci_hcd 0000:00:14.5: OHCI Host Controller
[   28.444979] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
[   28.445001] ohci_hcd 0000:00:14.5: irq 18, io mem 0xd2404000
[   28.395936] usb 1-1: configuration #1 chosen from 1 choice
[   28.508724] usb usb5: configuration #1 chosen from 1 choice
[   28.508755] hub 5-0:1.0: USB hub found
[   28.508797] hub 5-0:1.0: 2 ports detected
[   28.610168] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 17
[   28.610182] PCI: Setting latency timer of device 0000:00:12.2 to 64
[   28.610188] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   28.610225] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 6
[   28.610313] ehci_hcd 0000:00:12.2: debug port 1
[   28.610333] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2409500
[   28.620216] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.620363] usb usb6: configuration #1 chosen from 1 choice
[   28.620402] hub 6-0:1.0: USB hub found
[   28.620410] hub 6-0:1.0: 6 ports detected
[   28.724000] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 20
[   28.724025] PCI: Setting latency timer of device 0000:00:13.2 to 64
[   28.724031] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   28.724079] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 7
[   28.724132] ehci_hcd 0000:00:13.2: debug port 1
[   28.724153] ehci_hcd 0000:00:13.2: irq 20, io mem 0xd2409400
[   28.735800] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.735938] usb usb7: configuration #1 chosen from 1 choice
[   28.735974] hub 7-0:1.0: USB hub found
[   28.735982] hub 7-0:1.0: 6 ports detected
[   28.849112] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   28.849120] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.778260] usb 1-1: USB disconnect, address 2
[   28.778443] usbcore: registered new interface driver hiddev
[   29.215676] usb 5-1: new full speed USB device using ohci_hcd and address 2
[   29.428075] usb 5-1: configuration #1 chosen from 1 choice
[   29.737832] usb 5-2: new full speed USB device using ohci_hcd and address 3
[   29.952219] usb 5-2: configuration #1 chosen from 1 choice
[   29.954267] usbcore: registered new interface driver usbhid
[   29.954271] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.131294] Attempting manual resume
[   30.131300] swsusp: Resume From Partition 8:6
[   30.131303] PM: Checking swsusp image.
[   30.131512] PM: Resume from disk failed.
[   30.069827] kjournald starting.  Commit interval 5 seconds
[   30.069843] EXT3-fs: mounted filesystem with ordered data mode.
[   30.376577] usb 6-4: new high speed USB device using ehci_hcd and address 3
[   30.752186] usb 6-4: configuration #1 chosen from 1 choice
[   30.994399] usb 7-2: new high speed USB device using ehci_hcd and address 2
[   31.160805] usb 7-2: configuration #1 chosen from 1 choice
[   31.471708] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   31.689134] usb 1-1: configuration #1 chosen from 1 choice
[   31.699173] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1:1.0/input/input2
[   31.711884] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:12.0-1
[   39.291782] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.294538] shpchp: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   39.294543] shpchp: shpc_init: cannot reserve MMIO region
[   39.294569] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.339819] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   39.607624] ACPI: Battery Slot [BAT0] (battery absent)
[   39.636210] input: Power Button (FF) as /devices/virtual/input/input3
[   39.647994] ACPI: Power Button (FF) [PWRF]
[   39.648087] input: Power Button (CM) as /devices/virtual/input/input4
[   39.663780] ACPI: Power Button (CM) [PWRB]
[   39.663925] input: Sleep Button (CM) as /devices/virtual/input/input5
[   39.679733] ACPI: Sleep Button (CM) [SLPB]
[   39.679868] input: Lid Switch as /devices/virtual/input/input6
[   39.681271] ACPI: Lid Switch [LID]
[   39.863323] ACPI: WMI-Acer: Mapper loaded
[   39.982814] ACPI: AC Adapter [ACAD] (on-line)
[   40.082395] ieee80211_crypt: registered algorithm 'NULL'
[   40.086967] wl: module license '' taints kernel.
[   40.089511] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   40.089522] PCI: Setting latency timer of device 0000:08:00.0 to 64
[   40.130431] ieee80211_crypt: registered algorithm 'TKIP'
[   40.130868] eth1: Broadcom BCM432b 802.11 Wireless Controller 5.10.79.10
[   40.638421] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   40.664235] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   40.669829] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/LNXVIDEO:01/input/input8
[   40.696137] ACPI: Video Device [DVGA] (multi-head: yes  rom: no  post: no)
[   40.920946] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   40.920977] PCI: Setting latency timer of device 0000:00:14.2 to 64
[   40.956538] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   40.976615] Linux agpgart interface v0.102
[   41.137868] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04711/0xa00000
[   41.206391] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   41.327420] [fglrx] Maximum main memory to use for locked dma buffers: 2635 MBytes.
[   41.327476] [fglrx] ASYNCIO init succeed!
[   41.328192] [fglrx] PAT is enabled successfully!
[   41.328664] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   41.404710] Linux video capture interface: v2.00
[   41.584144] usbcore: registered new interface driver libusual
[   41.498668] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a104)
[   41.515194] usbcore: registered new interface driver uvcvideo
[   41.515199] USB Video Class driver (v0.1.0)
[   41.517116] Initializing USB Mass Storage driver...
[   41.520777] scsi8 : SCSI emulation for USB Mass Storage devices
[   41.523130] usbcore: registered new interface driver usb-storage
[   41.523133] USB Mass Storage support registered.
[   41.621333] usb-storage: device found at 3
[   41.621339] usb-storage: waiting for device to settle before scanning
[   42.922548] lp: driver loaded but no devices found
[   43.229827] Adding 3526228k swap on /dev/sda6.  Priority:-1 extents:1 across:3526228k
[   43.677118] EXT3 FS on sda5, internal journal
[   44.918465] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.347404] No dock devices found.
[   46.507016] usb-storage: device scan complete
[   46.607027] scsi 8:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   46.519297] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[   46.519337] sd 8:0:0:0: Attached scsi generic sg2 type 0
[   46.578394] apm: BIOS not found.
[   46.980558] ppdev: user-space parallel port driver
[   47.083526] audit(1244902751.354:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5331 profile="/usr/sbin/cupsd" namespace="default"
[   48.511308] r8169: eth0: link down
[   48.590660] Bluetooth: Core ver 2.11
[   48.590961] NET: Registered protocol family 31
[   48.590964] Bluetooth: HCI device and connection manager initialized
[   48.590969] Bluetooth: HCI socket layer initialized
[   48.610373] Bluetooth: L2CAP ver 2.9
[   48.610378] Bluetooth: L2CAP socket layer initialized
[   48.770970] Bluetooth: RFCOMM socket layer initialized
[   48.770997] Bluetooth: RFCOMM TTY layer initialized
[   48.771001] Bluetooth: RFCOMM ver 1.8
[   50.575951] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[   53.051186] [fglrx] GART Table is not in FRAME_BUFFER range 
[   53.051197] [fglrx] Reserve Block - 0 offset =  0X13ffb000 length = 0X5000
[   53.051201] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   53.290085] [fglrx] interrupt source ff000034 successfully enabled
[   53.290092] [fglrx] enable ID = 0x00000006
[   53.290101] [fglrx] Receive enable interrupt message with irqEnableMask: ff000034
[   59.829263] hda-intel: Invalid position buffer, using LPIB read method instead.
[   66.422999] NET: Registered protocol family 10
[   66.423238] lo: Disabled Privacy Extensions
[   66.423566] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.992159] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x10a90000
[   69.992588] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:600: hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x10a90000
[   74.564332] CPU0 attaching NULL sched-domain.
[   74.564339] CPU1 attaching NULL sched-domain.
[   74.580423] CPU0 attaching sched-domain:
[   74.580429]  domain 0: span 03
[   74.580431]   groups: 01 02
[   74.580434] CPU1 attaching sched-domain:
[   74.580435]  domain 0: span 03
[   74.580439]   groups: 02 01
[   77.014784] eth1: no IPv6 routers present
[  196.019755] r8169: eth0: link up
[  196.021076] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  198.124344] NET: Registered protocol family 17
[  203.428282] r8169: eth0: link down
[  205.256632] r8169: eth0: link up
[  205.257617] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  216.211090] eth0: no IPv6 routers present
[  229.886784] eth0: no IPv6 routers present
[  752.401380] r8169: eth0: link up
[  757.294972] r8169: eth0: link down
[  893.064250] r8169: eth0: link down
[  893.065295] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  893.145929] r8169: eth0: link down
[  893.146931] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  903.955949] eth1: no IPv6 routers present
[  919.673107] r8169: eth0: link down
[  919.675051] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  978.304245] r8169: eth0: link down
[  978.305217] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  978.438917] r8169: eth0: link down
[  978.439977] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  989.194880] eth1: no IPv6 routers present
[ 1004.948381] r8169: eth0: link down
[ 1004.950278] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1029.893259] r8169: eth0: link up
[ 1029.894706] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1046.950210] eth0: no IPv6 routers present

---

### Post by billyfd on 2009-06-13
well there's a few things you can try:


[LIST=1]
[*]Go to System>Administration>Hardware Drivers, then if a driver shows in the box,  click the activate button
[*]Use ndiswrapper there is a forum on how to use that
[*]Upgrade to 9.04 and use step one
[/LIST]
There are some sites out there where they may have the linux driver for your card, but you must find out what type of card it is and the device ID and Chipset ID

---

### Post by freak937 on 2009-06-13
I just did this [http://ubuntuforums.org/showthread.php?p=4443721#post4443721](http://ubuntuforums.org/showthread.php?p=4443721#post4443721) but didn't work.

---

### Post by freak937 on 2009-06-13
> **billyfd said:**
> well there's a few things you can try:


[LIST=1]
[*]Go to System>Administration>Hardware Drivers, then if a driver shows in the box,  click the activate button
[*]Use ndiswrapper there is a forum on how to use that
[*]Upgrade to 9.04 and use step one
[/LIST]
There are some sites out there where they may have the linux driver for your card, but you must find out what type of card it is and the device ID and Chipset ID

At System>Administration there shows up a Broadcom STA wireless driver which i have activated already.

I will try to Upgrade to 9.04 now. Thank you for your answer.

---

### Post by jtayl22 on 2009-11-18
I had miserable wireless performance on my Mac Book Pro with Broadcom BCM432b 802.11 Wireless Controller, Broadcom STA proprietary driver and Ubuntu 9.10 until I disabled TKIP on my wireless router. Everything is fine now that the only option on the router is AES. The change didn't disrupt any of the other 10 or so wireless devices around the house. HTH.

---

