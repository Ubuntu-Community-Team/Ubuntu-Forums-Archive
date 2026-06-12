---
title: "Asus usb-n13 in ubuntu 10.10"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by xnols on 2010-11-13
I have been trying to install the Asus usb-n113 wireless card for a day now. I went through all the steps in in this thread [http://ubuntuforums.org/showthread.php?t=1444746&page=1](http://ubuntuforums.org/showthread.php?t=1444746&page=1) . None of it worked.

when i do a iwconfig i get 
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

Im new to ubuntu so i dont know to much.

Thanks for the help

---

### Post by uncaspi on 2010-11-13
Will you please post the output of dmesq and lsusb

---

### Post by xnols on 2010-11-13
lsusb :
```
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 002 Device 003: ID 0bc2:3001 Seagate RSS LLC 
Bus 002 Device 002: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

it said dmesq was not found, this is for dmesg
```
[    1.042732] pci 0000:00:1c.1: setting latency timer to 64
[    1.042738] pci 0000:00:1c.2: enabling device (0006 -> 0007)
[    1.042740]   alloc irq_desc for 18 on node -1
[    1.042741]   alloc kstat_irqs on node -1
[    1.042743] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.042746] pci 0000:00:1c.2: setting latency timer to 64
[    1.042751] pci 0000:00:1e.0: setting latency timer to 64
[    1.042754] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.042755] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.042757] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.042758] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    1.042760] pci_bus 0000:00: resource 8 [mem 0xdfc00000-0xfebfffff]
[    1.042761] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    1.042763] pci_bus 0000:01: resource 1 [mem 0xfbb00000-0xfbbfffff]
[    1.042764] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    1.042766] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    1.042767] pci_bus 0000:02: resource 1 [mem 0xfba00000-0xfbafffff]
[    1.042769] pci_bus 0000:02: resource 2 [mem 0xdfc00000-0xdfcfffff pref]
[    1.042771] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    1.042772] pci_bus 0000:03: resource 1 [mem 0xdfd00000-0xdfefffff]
[    1.042773] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf01fffff 64bit pref]
[    1.042775] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    1.042776] pci_bus 0000:04: resource 1 [mem 0xfbe00000-0xfbefffff]
[    1.042778] pci_bus 0000:04: resource 2 [mem 0xfbd00000-0xfbdfffff 64bit pref]
[    1.042779] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    1.042781] pci_bus 0000:05: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    1.042782] pci_bus 0000:05: resource 2 [mem 0xf0200000-0xf03fffff 64bit pref]
[    1.042784] pci_bus 0000:06: resource 0 [io  0xb000-0xbfff]
[    1.042785] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    1.042787] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    1.042788] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    1.042790] pci_bus 0000:06: resource 7 [mem 0x000c0000-0x000dffff]
[    1.042791] pci_bus 0000:06: resource 8 [mem 0xdfc00000-0xfebfffff]
[    1.042814] NET: Registered protocol family 2
[    1.042850] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.042966] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.043426] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.043656] TCP: Hash tables configured (established 131072 bind 65536)
[    1.043657] TCP reno registered
[    1.043659] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    1.043666] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    1.043720] NET: Registered protocol family 1
[    1.075792] pci 0000:01:00.0: Boot video device
[    1.075820] PCI: CLS 64 bytes, default 64
[    1.076124] cpufreq-nforce2: No nForce2 chipset.
[    1.076139] Scanning for low memory corruption every 60 seconds
[    1.076219] audit: initializing netlink socket (disabled)
[    1.076226] type=2000 audit(1289641193.864:1): initialized
[    1.084071] highmem bounce pool size: 64 pages
[    1.084074] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.084931] VFS: Disk quotas dquot_6.5.2
[    1.084967] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.085298] fuse init (API version 7.14)
[    1.085348] msgmni has been set to 1624
[    1.085610] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.085612] io scheduler noop registered
[    1.085613] io scheduler deadline registered
[    1.085621] io scheduler cfq registered (default)
[    1.085693] pcieport 0000:00:03.0: setting latency timer to 64
[    1.085714]   alloc irq_desc for 45 on node -1
[    1.085715]   alloc kstat_irqs on node -1
[    1.085721] pcieport 0000:00:03.0: irq 45 for MSI/MSI-X
[    1.085763] pcieport 0000:00:05.0: setting latency timer to 64
[    1.085782]   alloc irq_desc for 46 on node -1
[    1.085783]   alloc kstat_irqs on node -1
[    1.085787] pcieport 0000:00:05.0: irq 46 for MSI/MSI-X
[    1.085830] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.085855]   alloc irq_desc for 47 on node -1
[    1.085856]   alloc kstat_irqs on node -1
[    1.085861] pcieport 0000:00:1c.0: irq 47 for MSI/MSI-X
[    1.085911] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.085936]   alloc irq_desc for 48 on node -1
[    1.085937]   alloc kstat_irqs on node -1
[    1.085942] pcieport 0000:00:1c.1: irq 48 for MSI/MSI-X
[    1.085992] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.086017]   alloc irq_desc for 49 on node -1
[    1.086018]   alloc kstat_irqs on node -1
[    1.086023] pcieport 0000:00:1c.2: irq 49 for MSI/MSI-X
[    1.086079] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    1.086083] aer 0000:00:05.0:pcie02: AER service couldn't init device: no _OSC support
[    1.086095] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.086144] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.086197] intel_idle: MWAIT substates: 0x1120
[    1.086198] intel_idle: v0.4 model 0x1E
[    1.086199] intel_idle: lapic_timer_reliable_states 0x2
[    1.086270] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.086274] ACPI: Power Button [PWRB]
[    1.086303] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.086305] ACPI: Power Button [PWRF]
[    1.086474] ACPI: acpi_idle yielding to intel_idle
[    1.093572] ERST: Table is not found!
[    1.093600] isapnp: Scanning for PnP cards...
[    1.093698] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.093787] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.094022] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.094692] brd: module loaded
[    1.094990] loop: module loaded
[    1.095100] ata_piix 0000:00:1f.2: version 2.13
[    1.095111]   alloc irq_desc for 19 on node -1
[    1.095112]   alloc kstat_irqs on node -1
[    1.095116] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.095119] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.095144] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.095183] scsi0 : ata_piix
[    1.095226] scsi1 : ata_piix
[    1.095624] ata1: SATA max UDMA/133 cmd 0xf800 ctl 0xf700 bmdma 0xf400 irq 19
[    1.095628] ata2: SATA max UDMA/133 cmd 0xf600 ctl 0xf500 bmdma 0xf408 irq 19
[    1.095641] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.095645] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.095668] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.095693] scsi2 : ata_piix
[    1.095727] scsi3 : ata_piix
[    1.096068] ata3: SATA max UDMA/133 cmd 0xf100 ctl 0xf000 bmdma 0xed00 irq 19
[    1.096071] ata4: SATA max UDMA/133 cmd 0xef00 ctl 0xee00 bmdma 0xed08 irq 19
[    1.096102] pata_acpi 0000:06:05.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.096116] pata_acpi 0000:06:05.0: setting latency timer to 64
[    1.096124] pata_acpi 0000:06:05.0: PCI INT A disabled
[    1.096280] Fixed MDIO Bus: probed
[    1.096298] PPP generic driver version 2.4.2
[    1.096319] tun: Universal TUN/TAP device driver, 1.6
[    1.096320] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.096363] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.096375] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.096383] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.096386] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.096403] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.096422] ehci_hcd 0000:00:1a.7: debug port 2
[    1.100310] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.100320] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbfff000
[    1.109257] Freeing initrd memory: 10480k freed
[    1.115609] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.115707] hub 1-0:1.0: USB hub found
[    1.115710] hub 1-0:1.0: 6 ports detected
[    1.115772]   alloc irq_desc for 23 on node -1
[    1.115773]   alloc kstat_irqs on node -1
[    1.115778] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.115792] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.115794] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.115818] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.115837] ehci_hcd 0000:00:1d.7: debug port 2
[    1.119731] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.119744] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbffe000
[    1.135583] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.135637] hub 2-0:1.0: USB hub found
[    1.135640] hub 2-0:1.0: 8 ports detected
[    1.135691] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.135701] uhci_hcd: USB Universal Host Controller Interface driver
[    1.135725] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.135730] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.135732] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.135751] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.135778] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[    1.135842] hub 3-0:1.0: USB hub found
[    1.135845] hub 3-0:1.0: 2 ports detected
[    1.135881]   alloc irq_desc for 21 on node -1
[    1.135882]   alloc kstat_irqs on node -1
[    1.135885] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.135890] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.135892] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.135912] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.135938] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[    1.136000] hub 4-0:1.0: USB hub found
[    1.136003] hub 4-0:1.0: 2 ports detected
[    1.136041] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.136045] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.136048] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.136069] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.136089] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fd00
[    1.136152] hub 5-0:1.0: USB hub found
[    1.136154] hub 5-0:1.0: 2 ports detected
[    1.136190] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.136194] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.136196] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.136215] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.136234] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[    1.136298] hub 6-0:1.0: USB hub found
[    1.136300] hub 6-0:1.0: 2 ports detected
[    1.136336] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.136340] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.136343] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.136365] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.136384] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[    1.136446] hub 7-0:1.0: USB hub found
[    1.136448] hub 7-0:1.0: 2 ports detected
[    1.136485] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.136489] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.136491] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.136508] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.136527] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[    1.136590] hub 8-0:1.0: USB hub found
[    1.136592] hub 8-0:1.0: 2 ports detected
[    1.136628] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.136632] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.136634] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.136651] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 9
[    1.136670] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000f900
[    1.136733] hub 9-0:1.0: USB hub found
[    1.136735] hub 9-0:1.0: 2 ports detected
[    1.136808] PNP: No PS/2 controller found. Probing ports directly.
[    1.170980] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.170981] If AUX port is really absent please use the 'i8042.noaux' option.
[    1.419486] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.419527] mice: PS/2 mouse device common for all mice
[    1.419594] rtc_cmos 00:04: RTC can wake from S4
[    1.419616] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.419639] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.419701] device-mapper: uevent: version 1.0.3
[    1.419781] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.419911] device-mapper: multipath: version 1.1.1 loaded
[    1.419914] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.419981] EISA: Probing bus 0 at eisa.0
[    1.419983] EISA: Cannot allocate resource for mainboard
[    1.419984] Cannot allocate resource for EISA slot 1
[    1.419986] Cannot allocate resource for EISA slot 2
[    1.419987] Cannot allocate resource for EISA slot 3
[    1.419988] Cannot allocate resource for EISA slot 4
[    1.419989] Cannot allocate resource for EISA slot 5
[    1.419990] Cannot allocate resource for EISA slot 6
[    1.419991] Cannot allocate resource for EISA slot 7
[    1.419992] Cannot allocate resource for EISA slot 8
[    1.419993] EISA: Detected 0 cards.
[    1.420297] cpuidle: using governor ladder
[    1.427541] ata3: SATA link down (SStatus 0 SControl 300)
[    1.438155] ata4: SATA link down (SStatus 0 SControl 300)
[    1.438347] cpuidle: using governor menu
[    1.438514] TCP cubic registered
[    1.438589] NET: Registered protocol family 10
[    1.438796] lo: Disabled Privacy Extensions
[    1.438916] NET: Registered protocol family 17
[    1.440825] Using IPI No-Shortcut mode
[    1.440862] PM: Resume from disk failed.
[    1.440868] registered taskstats version 1
[    1.441152]   Magic number: 2:94:677
[    1.441285] rtc_cmos 00:04: setting system clock to 2010-11-13 09:39:54 UTC (1289641194)
[    1.441290] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.441296] EDD information not available.
[    1.459450] isapnp: No Plug & Play device found
[    1.491388] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    1.741837] ata1.00: SATA link down (SStatus 0 SControl 300)
[    1.741851] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.895111] ata2.00: SATA link down (SStatus 0 SControl 300)
[    1.895127] ata2.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.911175] ata2.01: ATAPI: ATAPI   iHAS124   B, AL02, max UDMA/100
[    1.927183] ata2.01: configured for UDMA/100
[    1.929281] scsi 1:0:1:0: CD-ROM            ATAPI    iHAS124   B      AL02 PQ: 0 ANSI: 5
[    1.935970] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.935975] Uniform CD-ROM driver Revision: 3.20
[    1.936111] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    1.936139] sr 1:0:1:0: Attached scsi generic sg0 type 5
[    1.936270] Freeing unused kernel memory: 704k freed
[    1.936716] Write protecting the kernel text: 5088k
[    1.937045] Write protecting the kernel read-only data: 2012k
[    1.951906] udev[155]: starting version 163
[    1.974030] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.974049] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.974083] r8169 0000:04:00.0: setting latency timer to 64
[    1.974088] r8169 0000:04:00.0: (unregistered net_device): unknown MAC, using family default
[    1.974126]   alloc irq_desc for 50 on node -1
[    1.974128]   alloc kstat_irqs on node -1
[    1.974129] ahci 0000:02:00.0: version 3.0
[    1.974143] ahci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.974145] r8169 0000:04:00.0: irq 50 for MSI/MSI-X
[    1.974171]   alloc irq_desc for 51 on node -1
[    1.974173]   alloc kstat_irqs on node -1
[    1.974179] ahci 0000:02:00.0: irq 51 for MSI/MSI-X
[    1.974553] r8169 0000:04:00.0: eth0: RTL8168b/8111b at 0xf8496000, 6c:f0:49:ee:b2:89, XID 0c100000 IRQ 50
[    1.978909] pata_it8213 0000:06:05.0: version 0.0.3
[    1.978916] pata_it8213 0000:06:05.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.978960] scsi4 : pata_it8213
[    1.979006] scsi5 : pata_it8213
[    1.979030] ata5: PATA max UDMA/66 cmd 0xbf00 ctl 0xbe00 bmdma 0xbb00 irq 19
[    1.979031] ata6: DUMMY
[    1.987673] ahci 0000:02:00.0: AHCI 0001.0200 32 slots 8 ports 6 Gbps 0xff impl SATA mode
[    1.987680] ahci 0000:02:00.0: flags: 64bit ncq pio 
[    1.987686] ahci 0000:02:00.0: setting latency timer to 64
[    1.988093] scsi6 : ahci
[    1.988335] scsi7 : ahci
[    1.988516] scsi8 : ahci
[    1.988712] scsi9 : ahci
[    1.988898] scsi10 : ahci
[    1.989113] scsi11 : ahci
[    1.989279] scsi12 : ahci
[    1.989448] scsi13 : ahci
[    1.989526] ata7: SATA max UDMA/133 abar m2048@0xfbaff000 port 0xfbaff100 irq 51
[    1.989531] ata8: SATA max UDMA/133 abar m2048@0xfbaff000 port 0xfbaff180 irq 51
[    1.989535] ata9: SATA max UDMA/133 abar m2048@0xfbaff000 port 0xfbaff200 irq 51
[    1.989540] ata10: SATA max UDMA/133 abar m2048@0xfbaff000 port 0xfbaff280 irq 51
[    1.989545] ata11: SATA max UDMA/133 abar m2048@0xfbaff000 port 0xfbaff300 irq 51
[    1.989551] ata12: SATA max UDMA/133 abar m2048@0xfbaff000 port 0xfbaff380 irq 51
[    1.989553] ata13: SATA max UDMA/133 abar m2048@0xfbaff000 port 0xfbaff400 irq 51
[    1.989555] ata14: SATA max UDMA/133 abar m2048@0xfbaff000 port 0xfbaff480 irq 51
[    2.012593] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    2.151607] Initializing USB Mass Storage driver...
[    2.151887] scsi14 : usb-storage 2-4:1.0
[    2.151998] usbcore: registered new interface driver usb-storage
[    2.151999] USB Mass Storage support registered.
[    2.263101] usb 2-7: new high speed USB device using ehci_hcd and address 3
[    2.302587] ata9: SATA link down (SStatus 0 SControl 300)
[    2.302612] ata12: SATA link down (SStatus 0 SControl 300)
[    2.306603] ata11: SATA link down (SStatus 0 SControl 300)
[    2.306626] ata10: SATA link down (SStatus 0 SControl 300)
[    2.306645] ata13: SATA link down (SStatus 0 SControl 300)
[    2.306665] ata14: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.306838] ata14.00: ATAPI: MARVELL VIRTUALL, 1.09, max UDMA/66
[    2.307187] ata14.00: configured for UDMA/66
[    2.315059] ata8: SATA link down (SStatus 0 SControl 300)
[    2.315886] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.318245] ata7.00: ATA-8: WDC WD1002FAEX-00Z3A0, 05.01D05, max UDMA/133
[    2.318251] ata7.00: 1953525168 sectors, multi 8: LBA48 NCQ (depth 31/32), AA
[    2.320814] ata7.00: configured for UDMA/133
[    2.320974] scsi 6:0:0:0: Direct-Access     ATA      WDC WD1002FAEX-0 05.0 PQ: 0 ANSI: 5
[    2.321150] sd 6:0:0:0: Attached scsi generic sg1 type 0
[    2.321219] sd 6:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.321379] sd 6:0:0:0: [sda] Write Protect is off
[    2.321384] sd 6:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.321445] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.321728]  sda:
[    2.323298] scsi 13:0:0:0: Processor         Marvell  91xx Config      1.01 PQ: 0 ANSI: 5
[    2.323429] scsi 13:0:0:0: Attached scsi generic sg2 type 3
[    2.326352]  sda1 sda2 sda3 < sda5 sda6 >
[    2.335063] sd 6:0:0:0: [sda] Attached SCSI disk
[    2.398005] scsi15 : usb-storage 2-7:1.0
[    2.506384] usb 2-8: new high speed USB device using ehci_hcd and address 4
[    2.602101] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.897977] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    3.151371] scsi 14:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9744 PQ: 0 ANSI: 0
[    3.152199] scsi 14:0:0:1: Direct-Access     Generic  STORAGE DEVICE   9744 PQ: 0 ANSI: 0
[    3.153073] scsi 14:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9744 PQ: 0 ANSI: 0
[    3.153958] scsi 14:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9744 PQ: 0 ANSI: 0
[    3.154826] scsi 14:0:0:4: Direct-Access     Generic  STORAGE DEVICE   9744 PQ: 0 ANSI: 0
[    3.155299] sd 14:0:0:0: Attached scsi generic sg3 type 0
[    3.155385] sd 14:0:0:1: Attached scsi generic sg4 type 0
[    3.155463] sd 14:0:0:2: Attached scsi generic sg5 type 0
[    3.155545] sd 14:0:0:3: Attached scsi generic sg6 type 0
[    3.155627] sd 14:0:0:4: Attached scsi generic sg7 type 0
[    3.159512] sd 14:0:0:0: [sdb] Attached SCSI removable disk
[    3.160176] sd 14:0:0:4: [sdf] Attached SCSI removable disk
[    3.160749] sd 14:0:0:1: [sdc] Attached SCSI removable disk
[    3.161418] sd 14:0:0:2: [sdd] Attached SCSI removable disk
[    3.162143] sd 14:0:0:3: [sde] Attached SCSI removable disk
[    3.313595] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    3.394638] scsi 15:0:0:0: Direct-Access     Seagate  FreeAgent        102F PQ: 0 ANSI: 4
[    3.395032] sd 15:0:0:0: Attached scsi generic sg8 type 0
[    3.395574] sd 15:0:0:0: [sdg] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.396083] sd 15:0:0:0: [sdg] Write Protect is off
[    3.396088] sd 15:0:0:0: [sdg] Mode Sense: 1c 00 00 00
[    3.396091] sd 15:0:0:0: [sdg] Assuming drive cache: write through
[    3.397178] sd 15:0:0:0: [sdg] Assuming drive cache: write through
[    3.397186]  sdg: sdg1
[    3.398892] sd 15:0:0:0: [sdg] Assuming drive cache: write through
[    3.398894] sd 15:0:0:0: [sdg] Attached SCSI disk
[    8.662303] Adding 3086332k swap on /dev/sda6.  Priority:-1 extents:1 across:3086332k 
[    8.663361] udev[453]: starting version 163
[    8.696824] lp: driver loaded but no devices found
[    8.700921] Linux agpgart interface v0.103
[    8.705887] xhci_hcd 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.705907] xhci_hcd 0000:05:00.0: setting latency timer to 64
[    8.705911] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    8.705979] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 10
[    8.706125] xhci_hcd 0000:05:00.0: irq 18, io mem 0xfbcfe000
[    8.709054] Linux video capture interface: v2.00
[    8.709762] usb usb10: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    8.709881] xHCI xhci_add_endpoint called for root hub
[    8.709883] xHCI xhci_check_bandwidth called for root hub
[    8.709953] hub 10-0:1.0: USB hub found
[    8.709959] hub 10-0:1.0: 4 ports detected
[    8.713257] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0809)
[    8.721099] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    8.721102] Disabling lock debugging due to kernel taint
[    8.728925] input: UVC Camera (046d:0809) as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0/input/input2
[    8.728976] usbcore: registered new interface driver uvcvideo
[    8.728978] USB Video Class driver (v0.1.0)
[    8.730177] parport_pc 00:08: reported by Plug and Play ACPI
[    8.730227] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.744712] type=1400 audit(1289662801.807:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=531 comm="apparmor_parser"
[    8.745163] type=1400 audit(1289662801.807:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=531 comm="apparmor_parser"
[    8.745417] type=1400 audit(1289662801.807:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=531 comm="apparmor_parser"
[    8.748785] ppdev: user-space parallel port driver
[    8.773766] [fglrx] Maximum main memory to use for locked dma buffers: 3860 MBytes.
[    8.773812] [fglrx]   vendor: 1002 device: 689e count: 1
[    8.774161] [fglrx] ioport: bar 4, base 0xae00, size: 0x100
[    8.774171] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.774175] pci 0000:01:00.0: setting latency timer to 64
[    8.774498] [fglrx] Kernel PAT support is enabled
[    8.774508] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[    8.815111]   alloc irq_desc for 22 on node -1
[    8.815112]   alloc kstat_irqs on node -1
[    8.815116] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.815146]   alloc irq_desc for 52 on node -1
[    8.815147]   alloc kstat_irqs on node -1
[    8.815154] HDA Intel 0000:00:1b.0: irq 52 for MSI/MSI-X
[    8.815173] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.825110] lp0: using parport0 (interrupt-driven).
[    8.865376] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    8.865414]   alloc irq_desc for 53 on node -1
[    8.865416]   alloc kstat_irqs on node -1
[    8.865423] HDA Intel 0000:01:00.1: irq 53 for MSI/MSI-X
[    8.865442] HDA Intel 0000:01:00.1: setting latency timer to 64
[    8.876199] usbcore: registered new interface driver hiddev
[    8.891407] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input3
[    8.891466] generic-usb 0003:413C:2005.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1a.0-2/input0
[    8.904775] input: HID 04b4:0033 as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input4
[    8.904921] generic-usb 0003:04B4:0033.0002: input,hidraw1: USB HID v1.00 Mouse [HID 04b4:0033] on usb-0000:00:1a.2-2/input0
[    8.904932] usbcore: registered new interface driver usbhid
[    8.904933] usbhid: USB HID core driver
[    9.141589] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    9.305733] set resolution quirk: cval->res = 384
[    9.305917] usbcore: registered new interface driver snd-usb-audio
[    9.387647] r8169 0000:04:00.0: eth0: link up
[    9.387651] r8169 0000:04:00.0: eth0: link up
[    9.390823] type=1400 audit(1289662802.451:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1084 comm="apparmor_parser"
[    9.390872] type=1400 audit(1289662802.451:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1085 comm="apparmor_parser"
[    9.390992] type=1400 audit(1289662802.451:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1089 comm="apparmor_parser"
[    9.391297] type=1400 audit(1289662802.451:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1085 comm="apparmor_parser"
[    9.391541] type=1400 audit(1289662802.451:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1085 comm="apparmor_parser"
[    9.391851] type=1400 audit(1289662802.451:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1088 comm="apparmor_parser"
[    9.392394] type=1400 audit(1289662802.455:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1088 comm="apparmor_parser"
[   10.336589] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   10.336751]   alloc irq_desc for 54 on node -1
[   10.336753]   alloc kstat_irqs on node -1
[   10.336760] fglrx_pci 0000:01:00.0: irq 54 for MSI/MSI-X
[   10.337269] [fglrx] Firegl kernel thread PID: 1332
[   10.337495] [fglrx] IRQ 54 Enabled
[   10.560923] [fglrx] Gart USWC size:1260 M.
[   10.560925] [fglrx] Gart cacheable size:498 M.
[   10.560928] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   10.560930] [fglrx] Reserved FB block: Unshared offset:f90f000, size:3f1000 
[   10.560931] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   12.279248] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   12.789963] hda-intel: IRQ timing workaround is activated for card #2. Suggest a bigger bdl_pos_adj.
[   20.391669] eth0: no IPv6 routers present
[  118.422356] lo: Disabled Privacy Extensions

```

---

### Post by uncaspi on 2010-11-13
Can't see any driver loaded in dmesg. Perhaps you could post the contest of these commands.

sudo /sbin/lshw -C network

sudo /sbin/ifconfig

---

### Post by xnols on 2010-11-13
sudo /sbin/lshw -C network said command not found


sudo /sbin/ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:ee:b2:89  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:feee:b289/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:471703 errors:0 dropped:0 overruns:0 frame:0
          TX packets:321328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:670762664 (670.7 MB)  TX bytes:28572422 (28.5 MB)
          Interrupt:50 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

---

### Post by uncaspi on 2010-11-13
Try sudo lshw -C network

---

### Post by xnols on 2010-11-13
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: 6c:f0:49:ee:b2:89
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:50 ioport:de00(size=256) memory:fbdff000-fbdfffff memory:fbdf8000-fbdfbfff memory:fbd00000-fbd1ffff

```

---

### Post by uncaspi on 2010-11-13
And post sudo iwconfig

sudo iwlist scan

---

### Post by uncaspi on 2010-11-13
No driver for the device is loaded. I googled for it but couldent find any.
Perhaps you should by a stick compatible with ubuntu. I don't know.

---

### Post by uncaspi on 2010-11-14
Hi. I found this thread.
[http://ubuntuforums.org/showthread.php?t=1563281&highlight=asus+usb+n13](http://ubuntuforums.org/showthread.php?t=1563281&highlight=asus+usb+n13)

---

### Post by xnols on 2010-11-14
> **uncaspi said:**
> Hi. I found this thread.
[http://ubuntuforums.org/showthread.php?t=1563281&highlight=asus+usb+n13](http://ubuntuforums.org/showthread.php?t=1563281&highlight=asus+usb+n13)
I did what it said, it didnt work. When i do the make command i get this:
```
make -C tools
make[1]: Entering directory `/home/nols/Desktop/RT3070/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/nols/Desktop/RT3070/tools'
/home/nols/Desktop/RT3070/tools/bin2h
cp -f os/linux/Makefile.6 /home/nols/Desktop/RT3070/os/linux/Makefile
make  -C  /lib/modules/2.6.35-22-generic-pae/build SUBDIRS=/home/nols/Desktop/RT3070/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
  CC [M]  /home/nols/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.o
/home/nols/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/nols/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/nols/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/nols/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/nols/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/nols/Desktop/RT3070/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
make: *** [LINUX] Error 2

```

---

### Post by chili555 on 2010-11-14
Please try the approach on the first post here. As you can see, it is the same device. Yours is:> [COLOR="Red"]0b05:1784[/COLOR] ASUSTek Computer, Inc. 802.11n Network Adapter
He references:> ATTR{idVendor}=="[COLOR="Red"]0b05[/COLOR]", ATTR{idProduct}=="[COLOR="Red"]1784[/COLOR]",[http://www.pclinuxos.com/forum/index.php?action=printpage;topic=76312.0](http://www.pclinuxos.com/forum/index.php?action=printpage;topic=76312.0)

Post back if you get stuck.

---

### Post by xnols on 2010-11-15
It worked. Thanks for the help :)

---

### Post by uncaspi on 2010-11-15
Remember to put solved on the thread:):):)

---

### Post by roxxar on 2011-02-03
What did he do to fix it? I get the same installation error... I don't have an account to that forum.

---

### Post by chili555 on 2011-02-04
> **roxxar said:**
> What did he do to fix it? I get the same installation error... I don't have an account to that forum.It depends on your kernel version. Please post:```
uname -r
modinfo rt2870sta | grep 1784
modinfo rt2800usb | grep 1784
```This assumes you have the same usb.id:> 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter Thanks.

---

### Post by roxxar on 2011-02-04
tyler@pc:/tyler$ uname -r 2.6.35-25-generic tyler@pc:/tyler$ modinfo rt2870sta | grep 1784 alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip* tyler@pc:/tyler$ modinfo rt2800usb | grep 1784 tyler@pc:/tyler$

---

### Post by chili555 on 2011-02-04
If you have the same device as mentioned above:> 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter Then the fix is easy. Find out with:```
lsusb
```If so, both rt2870sta and rt2800usb drive your device. Let's blacklist rt2800usb:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread, save and close gedit. Reboot and let us have your report.

---

### Post by roxxar on 2011-02-04
It works. I am able to see it in the network manager. Is there a way to check which wireless driver I am using for the asus usb-n13? I used the command airmon-ng and this is what it shows: 

Interface    Chipset        Driver

wlan0        Unknown         usb

wlan1-wlan0        Atheros     ath9k - [phy0]

IEEE        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)
802.11bgn        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)
ESSID:"NV"        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)

the first one wlan0 is the asus usb-n13. It doesn't detect the chipset and driver is usb. The signal strength is very weak compared to my integrated wireless chip. Is it because I don't have the correct driver? 

appreciate your help ty.

---

### Post by chili555 on 2011-02-04
> Is there a way to check which wireless driver I am using for the asus usb-n13?Well, I sure hope it's rt2870sta! Please check with:```
lsmod | grep rt2
```

---

### Post by roxxar on 2011-02-04
Usage: lsmod
tyler@pc:~$ lsmod | grep rt2
rt2870sta             446110  0 
crc_ccitt               1699  1 rt2870sta

it is :) ... How come it airmon-ng detect it as USB? Airmon-ng doesn't work with it as well. Guess I got to do more research... thanks for the help. cheers.

---

### Post by chili555 on 2011-02-04
> How come it airmon-ng detect it as USB?Do you mean instead of detecting it more specifically as rt2870sta? I don't know; I suggest you contact the developers of airmon-ng. It's not an Ubuntu creation.

---

