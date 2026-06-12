---
title: "No wifi"
date: 2013-08-21
forum: Networking &amp; Wireless
---

### Post by david61 on 2013-08-21
I have just installed ubuntu and wifi not working please help please give step by stem instruction dell 5720

---

### Post by slw210 on 2013-08-21
[**[COLOR="#000000"]HOWTO post a Wireless issue (ticket)[/COLOR]**]("http://ubuntuforums.org/showthread.php?p=6183681")

---

### Post by david61 on 2013-08-21
```
[    0.412499] system 00:04: [io  0x1000-0x1003] has been reserved
[    0.412500] system 00:04: [io  0x1004-0x1013] has been reserved
[    0.412502] system 00:04: [io  0xffff] has been reserved
[    0.412504] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.412505] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.412507] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.412508] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.412510] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.412516] pnp 00:05: [io  0x0070-0x0077]
[    0.412521] pnp 00:05: [irq 8]
[    0.412535] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.412555] pnp 00:06: [io  0x0454-0x0457]
[    0.412582] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.412585] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.412600] pnp 00:07: [io  0x0060]
[    0.412601] pnp 00:07: [io  0x0064]
[    0.412606] pnp 00:07: [irq 1]
[    0.412640] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.412653] pnp 00:08: [irq 12]
[    0.412672] pnp 00:08: Plug and Play ACPI device, IDs DLL0565 PNP0f13 (active)
[    0.412753] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.412754] pnp 00:09: [mem 0xfed10000-0xfed17fff]
[    0.412756] pnp 00:09: [mem 0xfed18000-0xfed18fff]
[    0.412757] pnp 00:09: [mem 0xfed19000-0xfed19fff]
[    0.412758] pnp 00:09: [mem 0xf8000000-0xfbffffff]
[    0.412759] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.412762] pnp 00:09: [mem 0xfed90000-0xfed93fff]
[    0.412763] pnp 00:09: [mem 0xfed45000-0xfed8ffff]
[    0.412765] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.412766] pnp 00:09: [mem 0xfee00000-0xfeefffff]
[    0.412767] pnp 00:09: [mem 0xfffff000-0xffffffff]
[    0.412778] pnp 00:09: disabling [mem 0xfffff000-0xffffffff] because it overlaps 0000:01:00.0 BAR 6 [mem 0xfff80000-0xffffffff pref]
[    0.412798] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.412800] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.412801] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.412803] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.412805] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.412806] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.412808] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.412809] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.412811] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.412813] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.412815] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.413033] pnp: PnP ACPI: found 10 devices
[    0.413034] ACPI: ACPI bus type pnp unregistered
[    0.419168] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.419203] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x80000)
[    0.419206] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.419208] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.419210] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf0ffffff]
[    0.419213] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.419216] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.419223] pci 0000:00:1c.0:   bridge window [mem 0xf1500000-0xf15fffff]
[    0.419235] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.419238] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.419245] pci 0000:00:1c.4:   bridge window [mem 0xf1400000-0xf14fffff 64bit pref]
[    0.419283] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.419284] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.419286] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.419287] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xfeafffff]
[    0.419289] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.419290] pci_bus 0000:01: resource 1 [mem 0xf0000000-0xf0ffffff]
[    0.419292] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.419294] pci_bus 0000:02: resource 1 [mem 0xf1500000-0xf15fffff]
[    0.419295] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.419297] pci_bus 0000:03: resource 2 [mem 0xf1400000-0xf14fffff 64bit pref]
[    0.419320] NET: Registered protocol family 2
[    0.419461] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.420032] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.421038] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.421153] TCP: Hash tables configured (established 524288 bind 65536)
[    0.421154] TCP: reno registered
[    0.421167] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.421196] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.421262] NET: Registered protocol family 1
[    0.421274] pci 0000:00:02.0: Boot video device
[    0.421458] PCI: CLS 64 bytes, default 64
[    0.421459] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.421461] software IO TLB [mem 0xb3f65000-0xb7f64fff] (64MB) mapped at [ffff8800b3f65000-ffff8800b7f64fff]
[    0.421859] audit: initializing netlink socket (disabled)
[    0.421866] type=2000 audit(1377108099.316:1): initialized
[    0.434701] Freeing initrd memory: 15184k freed
[    0.443758] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.445023] VFS: Disk quotas dquot_6.5.2
[    0.445052] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.445391] fuse init (API version 7.19)
[    0.445450] msgmni has been set to 11648
[    0.445751] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.445774] io scheduler noop registered
[    0.445776] io scheduler deadline registered (default)
[    0.445796] io scheduler cfq registered
[    0.445877] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.446027] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.446040] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.446073] intel_idle: MWAIT substates: 0x21120
[    0.446074] intel_idle: v0.4 model 0x3A
[    0.446075] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.643024] ACPI: AC Adapter [ADP0] (on-line)
[    0.643107] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.643111] ACPI: Power Button [PWRB]
[    0.643134] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.643137] ACPI: Sleep Button [SLPB]
[    0.643161] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.643612] ACPI: Lid Switch [LID0]
[    0.643643] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.643646] ACPI: Power Button [PWRF]
[    0.643709] ACPI: Requesting acpi_cpufreq
[    0.647023] thermal LNXTHERM:00: registered as thermal_zone0
[    0.647026] ACPI: Thermal Zone [TZ00] (54 C)
[    0.647168] thermal LNXTHERM:01: registered as thermal_zone1
[    0.647169] ACPI: Thermal Zone [TZ01] (54 C)
[    0.647189] ACPI: Battery Slot [BAT0] (battery present)
[    0.647205] GHES: HEST is not enabled!
[    0.647268] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.649908] Linux agpgart interface v0.103
[    0.650819] brd: module loaded
[    0.651323] loop: module loaded
[    0.651393] ahci 0000:00:1f.2: version 3.0
[    0.651449] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    0.654180] ACPI: Battery Slot [BAT0] (battery present)
[    0.666987] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x9 impl SATA mode
[    0.666993] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    0.667000] ahci 0000:00:1f.2: setting latency timer to 64
[    0.675283] scsi0 : ahci
[    0.675345] scsi1 : ahci
[    0.675391] scsi2 : ahci
[    0.675435] scsi3 : ahci
[    0.675479] scsi4 : ahci
[    0.675524] scsi5 : ahci
[    0.675637] ata1: SATA max UDMA/133 abar m2048@0xf1618000 port 0xf1618100 irq 41
[    0.675638] ata2: DUMMY
[    0.675639] ata3: DUMMY
[    0.675641] ata4: SATA max UDMA/133 abar m2048@0xf1618000 port 0xf1618280 irq 41
[    0.675642] ata5: DUMMY
[    0.675643] ata6: DUMMY
[    0.675868] Fixed MDIO Bus: probed
[    0.675895] tun: Universal TUN/TAP device driver, 1.6
[    0.675896] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.675938] PPP generic driver version 2.4.2
[    0.675976] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.676007] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.676011] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.676015] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.676039] ehci_hcd 0000:00:1a.0: debug port 2
[    0.679913] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.679928] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf161a000
[    0.690940] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.690968] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.690971] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.690974] usb usb1: Product: EHCI Host Controller
[    0.690977] usb usb1: Manufacturer: Linux 3.5.0-23-generic ehci_hcd
[    0.690979] usb usb1: SerialNumber: 0000:00:1a.0
[    0.691093] hub 1-0:1.0: USB hub found
[    0.691097] hub 1-0:1.0: 2 ports detected
[    0.691154] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.691158] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.691161] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.691180] ehci_hcd 0000:00:1d.0: debug port 2
[    0.695058] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.695070] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf1619000
[    0.706918] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.706938] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.706941] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.706944] usb usb2: Product: EHCI Host Controller
[    0.706947] usb usb2: Manufacturer: Linux 3.5.0-23-generic ehci_hcd
[    0.706949] usb usb2: SerialNumber: 0000:00:1d.0
[    0.707054] hub 2-0:1.0: USB hub found
[    0.707056] hub 2-0:1.0: 2 ports detected
[    0.707095] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.707105] uhci_hcd: USB Universal Host Controller Interface driver
[    0.707141] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    0.707144] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.707147] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.707231] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.707243] xhci_hcd 0000:00:14.0: irq 21, io mem 0xf1600000
[    0.707289] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X
[    0.707329] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.707330] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.707332] usb usb3: Product: xHCI Host Controller
[    0.707333] usb usb3: Manufacturer: Linux 3.5.0-23-generic xhci_hcd
[    0.707334] usb usb3: SerialNumber: 0000:00:14.0
[    0.707396] xHCI xhci_add_endpoint called for root hub
[    0.707397] xHCI xhci_check_bandwidth called for root hub
[    0.707413] hub 3-0:1.0: USB hub found
[    0.707419] hub 3-0:1.0: 4 ports detected
[    0.707459] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.707462] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.707479] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.707481] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.707482] usb usb4: Product: xHCI Host Controller
[    0.707483] usb usb4: Manufacturer: Linux 3.5.0-23-generic xhci_hcd
[    0.707484] usb usb4: SerialNumber: 0000:00:14.0
[    0.707540] xHCI xhci_add_endpoint called for root hub
[    0.707541] xHCI xhci_check_bandwidth called for root hub
[    0.707556] hub 4-0:1.0: USB hub found
[    0.707565] hub 4-0:1.0: 4 ports detected
[    0.707658] usbcore: registered new interface driver libusual
[    0.707682] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.710861] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.710865] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.710969] mousedev: PS/2 mouse device common for all mice
[    0.711106] rtc_cmos 00:05: RTC can wake from S4
[    0.711221] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.711248] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.711297] device-mapper: uevent: version 1.0.3
[    0.711346] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.711411] cpuidle: using governor ladder
[    0.711496] cpuidle: using governor menu
[    0.711497] EFI Variables Facility v0.08 2004-May-17
[    0.711675] ashmem: initialized
[    0.711766] TCP: cubic registered
[    0.711834] NET: Registered protocol family 10
[    0.711969] NET: Registered protocol family 17
[    0.711977] Key type dns_resolver registered
[    0.712107] PM: Hibernation image not present or could not be loaded.
[    0.712115] registered taskstats version 1
[    0.713874] Key type trusted registered
[    0.715409] Key type encrypted registered
[    0.717235]   Magic number: 9:461:39
[    0.717247] bdi 7:4: hash matches
[    0.717335] rtc_cmos 00:05: setting system clock to 2013-08-21 18:01:40 UTC (1377108100)
[    0.717910] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.717911] EDD information not available.
[    0.718491] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.994573] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.994603] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.000917] ata4.00: ATAPI: TSSTcorp DVD+/-RW SN-208BB, D300, max UDMA/100
[    1.001004] ata1.00: ATA-8: ST1000LM024 HN-M101MBB, 2AR20002, max UDMA/133
[    1.001009] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.002558] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.007427] ata1.00: configured for UDMA/133
[    1.007716] scsi 0:0:0:0: Direct-Access     ATA      ST1000LM024 HN-M 2AR2 PQ: 0 ANSI: 5
[    1.007827] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.007838] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.007910] sd 0:0:0:0: [sda] Write Protect is off
[    1.007912] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.007961] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.008651] ata4.00: configured for UDMA/100
[    1.036991]  sda: sda1 sda2 sda3
[    1.037846] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.044877] scsi 3:0:0:0: CD-ROM            TSSTcorp DVD+-RW SN-208BB D300 PQ: 0 ANSI: 5
[    1.059192] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.059197] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.059386] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.059500] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.060678] Freeing unused kernel memory: 948k freed
[    1.060761] Write protecting the kernel read-only data: 12288k
[    1.063537] Freeing unused kernel memory: 1352k freed
[    1.065644] Freeing unused kernel memory: 1048k freed
[    1.076876] udevd[113]: starting version 175
[    1.134799] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.134805] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.135194] hub 1-1:1.0: USB hub found
[    1.135271] hub 1-1:1.0: 6 ports detected
[    1.246227] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.300676] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.300790] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
[    1.300905] r8169 0000:03:00.0: eth0: RTL8105e at 0xffffc90000c6e000, 5c:f9:dd:49:fb:4c, XID 00c00000 IRQ 43
[    1.378448] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.378455] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.378717] hub 2-1:1.0: USB hub found
[    1.378825] hub 2-1:1.0: 8 ports detected
[    1.418017] Refined TSC clocksource calibration: 2494.333 MHz.
[    1.418024] Switching to clocksource tsc
[    1.450137] usb 1-1.3: new high-speed USB device number 3 using ehci_hcd
[    1.542740] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=0129
[    1.542745] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.542749] usb 1-1.3: Product: USB2.0-CRW
[    1.542751] usb 1-1.3: Manufacturer: Generic
[    1.542754] usb 1-1.3: SerialNumber: 20100201396000000
[    1.613928] usb 1-1.5: new high-speed USB device number 4 using ehci_hcd
[    1.769350] usb 1-1.5: New USB device found, idVendor=0c45, idProduct=648d
[    1.769355] usb 1-1.5: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    1.769358] usb 1-1.5: Product: Laptop_Integrated_Webcam_HD
[    1.769361] usb 1-1.5: Manufacturer: 1234567890-20A
[    1.845593] usb 2-1.5: new full-speed USB device number 3 using ehci_hcd
[    1.940355] usb 2-1.5: New USB device found, idVendor=0a5c, idProduct=21d7
[    1.940361] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.940364] usb 2-1.5: Product: BCM43142A0
[    1.940367] usb 2-1.5: Manufacturer: Broadcom Corp
[    1.940369] usb 2-1.5: SerialNumber: 9C2A70C9F42C
[    2.609510] EXT3-fs (loop0): recovery required on readonly filesystem
[    2.609513] EXT3-fs (loop0): write access will be enabled during recovery
[    4.533719] kjournald starting.  Commit interval 5 seconds
[    4.585387] EXT3-fs (loop0): recovery complete
[    4.585389] EXT3-fs (loop0): mounted filesystem with ordered data mode
[   24.819288] Adding 262140k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262140k 
[   24.824169] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.825161] EXT3-fs (loop0): using internal journal
[   24.827095] udevd[447]: starting version 175
[   24.945733] lp: driver loaded but no devices found
[   24.947543] Bluetooth: Core ver 2.16
[   24.947558] NET: Registered protocol family 31
[   24.947560] Bluetooth: HCI device and connection manager initialized
[   24.947562] Bluetooth: HCI socket layer initialized
[   24.947563] Bluetooth: L2CAP socket layer initialized
[   24.947566] Bluetooth: SCO socket layer initialized
[   24.950127] ppdev: user-space parallel port driver
[   24.950148] Bluetooth: RFCOMM TTY layer initialized
[   24.950151] Bluetooth: RFCOMM socket layer initialized
[   24.950153] Bluetooth: RFCOMM ver 1.11
[   24.956687] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.956691] Bluetooth: BNEP filters: protocol multicast
[   24.960021] type=1400 audit(1377104524.770:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=539 comm="apparmor_parser"
[   24.960370] type=1400 audit(1377104524.770:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=539 comm="apparmor_parser"
[   25.062754] mei 0000:00:16.0: setting latency timer to 64
[   25.064734] mei 0000:00:16.0: irq 44 for MSI/MSI-X
[   25.069270] wmi: Mapper loaded
[   25.071456] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   25.071464] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.071465] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   25.071469] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   25.071472] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.071476] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[   25.071480] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20120320/utaddress-251)
[   25.071483] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.071484] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   25.072197] mei 0000:00:16.0: wd: failed to find the client
[   25.081565] type=1400 audit(1377104524.890:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=650 comm="apparmor_parser"
[   25.082694] type=1400 audit(1377104524.890:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=650 comm="apparmor_parser"
[   25.082891] type=1400 audit(1377104524.890:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=650 comm="apparmor_parser"
[   25.086400] [drm] Initialized drm 1.1.0 20060810
[   25.094840] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.GFX0 handle
[   25.094864] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   25.094867] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   25.095210] [drm] nouveau 0000:01:00.0: Detected an NVd0 generation card (0x0d7000a2)
[   25.100187] [drm] nouveau 0000:01:00.0: Checking PRAMIN for VBIOS
[   25.148254] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   25.148257] [drm] nouveau 0000:01:00.0: Checking PROM for VBIOS
[   25.148322] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   25.148323] [drm] nouveau 0000:01:00.0: Checking ACPI for VBIOS
[   25.162284] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x12
[   25.168528] Linux video capture interface: v2.00
[   25.170660] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (0c45:648d)
[   25.181168] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   25.196533] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input5
[   25.196639] usbcore: registered new interface driver uvcvideo
[   25.196641] USB Video Class driver (1.1.1)
[   25.221974] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   25.228675] scsi6 : SCSI emulation for RTS5139 USB card reader
[   25.230337] usbcore: registered new interface driver btusb
[   25.231063] init: failsafe main process (768) killed by TERM signal
[   25.233199] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   25.235819] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   25.237853] usbcore: registered new interface driver rts5139
[   25.241855] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   25.276896] type=1400 audit(1377104525.086:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=930 comm="apparmor_parser"
[   25.277066] type=1400 audit(1377104525.086:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=929 comm="apparmor_parser"
[   25.278867] type=1400 audit(1377104525.086:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=933 comm="apparmor_parser"
[   25.279090] type=1400 audit(1377104525.086:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=930 comm="apparmor_parser"
[   25.279367] type=1400 audit(1377104525.090:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=930 comm="apparmor_parser"
[   25.357797] Bluetooth: can't load firmware, may not work correctly
[   25.357829] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x12
[   25.359516] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x12
[   25.362454] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x12
[   25.363701] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   25.367868] init: alsa-restore main process (988) terminated with status 19
[   25.396502] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   25.438120] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   25.438123] [drm] nouveau 0000:01:00.0: Using VBIOS from ACPI
[   25.438125] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   25.438127] [drm] nouveau 0000:01:00.0: Bios version 75.17.33.00
[   25.438129] [drm] nouveau 0000:01:00.0: Pointer to TMDS table invalid
[   25.438186] [drm] nouveau 0000:01:00.0: MXM: no VBIOS data, nothing to do
[   25.438187] [drm] nouveau 0000:01:00.0: DCB version 4.0
[   25.438585] i915 0000:00:02.0: setting latency timer to 64
[   25.439098] pci 0000:00:00.0: Intel Ivybridge Chipset
[   25.439177] pci 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[   25.439985] pci 0000:00:00.0: detected 65536K stolen memory
[   25.468202] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   25.468211] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   25.468211] [drm] Driver supports precise vblank timestamp query.
[   25.468829] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   25.549663] r8169 0000:03:00.0: eth0: link down
[   25.549676] r8169 0000:03:00.0: eth0: link down
[   25.550121] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.550347] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.698707] vboxdrv: Found 4 processor cores.
[   25.698840] vboxdrv: fAsync=0 offMin=0xdd offMax=0xfec
[   25.698905] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   25.698907] vboxdrv: Successfully loaded version 4.2.16 (interface 0x001a0005).
[   25.904416] vboxpci: IOMMU not found (not registered)
[   26.032496] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   26.110172] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input7
[   26.209618] fbcon: inteldrmfb (fb0) is primary device
[   26.209709] Console: switching to colour frame buffer device 200x56
[   26.209734] fb0: inteldrmfb frame buffer device
[   26.209735] drm: registered panic notifier
[   26.209978] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   26.449353] acpi device:33: registered as cooling_device4
[   26.449359] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   26.449397] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2f/LNXVIDEO:00/input/input8
[   26.454296] acpi device:36: registered as cooling_device5
[   26.454417] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   26.454464] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
[   26.454526] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   26.454622] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   27.010299] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   27.010470] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   27.010585] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   27.177201] r8169 0000:03:00.0: eth0: link up
[   27.177639] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.774449] init: plymouth-stop pre-start process (1319) terminated with status 1
[   50.915482] audit_printk_skb: 36 callbacks suppressed
[   50.915485] type=1400 audit(1377104550.094:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2115 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
dovi@ubuntu:~$ sudo lshw -C network
[sudo] password for dovi: 
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f1500000-f1507fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 5c:f9:dd:49:fb:4c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.159 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f1404000-f1404fff memory:f1400000-f1403fff
dovi@ubuntu:~$ iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


dovi@ubuntu:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
dovi@ubuntu:~$ lsb_release -d
Description:	Ubuntu 12.04.2 LTS
dovi@ubuntu:~$ uname -mr
3.5.0-23-generic x86_64
dovi@ubuntu:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                        [ OK ] 
dovi@ubuntu:~$
```

---

### Post by slw210 on 2013-08-21
Try [THIS ARTICLE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers").

---

### Post by Bucky Ball on 2013-08-21
@slw210: I have edited your first post. Please note, from the forum guidelines:

> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. 

Cheers. BB

Incidentally, 

```
sudo lshw -C network
```

... is a good place to start, also. ;)

---

### Post by slw210 on 2013-08-21
Sorry about that, BUT, that is the color YOU have them in, I just copy and pasted the link.

I won't bother helping around here anymore.

PS.

He has already

```
dovi@ubuntu:~$ sudo lshw -C network
```

---

