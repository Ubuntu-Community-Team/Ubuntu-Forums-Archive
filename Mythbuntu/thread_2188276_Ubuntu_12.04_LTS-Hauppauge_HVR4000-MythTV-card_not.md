---
title: "Ubuntu 12.04 LTS-Hauppauge HVR4000-MythTV-card not recognised"
date: 2013-11-16
forum: Mythbuntu
---

### Post by petatkinson on 2013-11-16
I've just completed a fresh install of Ubuntu 12.04 with the above.I was previously using 10.04LTS and MythTV was working fine.I installed MythTV and Linux-Firmware-Nonfree from the Software Centre.I ran mythtv-setup from the terminal.Everything worked fine until I came to configurig Capture Card.As the card is a hybrid it has a frontend0 for DVB S and frontend1 for DVB T.Myth reported not recognising the card for either so I didn't have the option to tune for DVB-S.I continued on and tried a scan for DVB T.I was surprised to see that it carried out a scan successfully and found 39 channels. 

I remember a problem a while back. There was a bug in the firmware  CX24116 when I was installing in 10.04 so is this firmware still a problem and is there an alternative source for downloading and installing it. If this is the case can I remove the version currently installed and install the alternative one.

---

### Post by petatkinson on 2013-11-17
Just including a copy of the dmesg grep cx* after starting and closing MythTV..............................

[    0.108136] pci_bus 0000:00: on NUMA node 0
[    0.108330]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.108333]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.113155] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.113155] vgaarb: bridge control possible 0000:02:00.0
[    0.113155] ACPI: bus type scsi registered
[    0.113155] usbcore: registered new interface driver usbfs
[    0.113155] usbcore: registered new interface driver hub
[    0.113155] usbcore: registered new device driver usb
[    0.113155] PCI: pci_cache_line_size set to 64 bytes
[    0.113155] e820: reserve RAM buffer [mem 0xcfef0000-0xcfffffff]
[    0.113155] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.113155] NetLabel:  unlabeled traffic allowed by default
[    0.113155] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.113155] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.116013] Switching to clocksource hpet
[    0.124793] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.124928] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.124974] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.125066] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.125121] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.125155] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.125201] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.125384] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.125643] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.125914] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.126057] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.126113] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.126817] system 00:0c: [mem 0xe4000000-0xe5ffffff] has been reserved
[    0.126822] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.127035] system 00:0d: [mem 0x000f0000-0x000fbfff] could not be reserved
[    0.127038] system 00:0d: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.127042] system 00:0d: [mem 0xcfef0000-0xcfefffff] could not be reserved
[    0.127048] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.127052] system 00:0d: [mem 0x00100000-0xcfeeffff] could not be reserved
[    0.127055] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.127062] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.127070] pnp: PnP ACPI: found 14 devices
[    0.164123] pci 0000:00:0a.0: PCI bridge to [bus 01]
[    0.164130] pci 0000:00:0a.0:   bridge window [mem 0xe6000000-0xeaffffff]
[    0.164141] pci 0000:02:00.0: BAR 6: assigned [mem 0xe3000000-0xe307ffff pref]
[    0.164144] pci 0000:00:0b.0: PCI bridge to [bus 02]
[    0.164148] pci 0000:00:0b.0:   bridge window [io  0xb000-0xbfff]
[    0.164152] pci 0000:00:0b.0:   bridge window [mem 0xe0000000-0xe3ffffff]
[    0.164156] pci 0000:00:0b.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.164161] pci 0000:00:0c.0: PCI bridge to [bus 03]
[    0.164164] pci 0000:00:0c.0:   bridge window [io  0xa000-0xafff]
[    0.164172] pci 0000:00:0d.0: PCI bridge to [bus 04]
[    0.164175] pci 0000:00:0d.0:   bridge window [io  0x9000-0x9fff]
[    0.164189] pci 0000:00:0a.0: setting latency timer to 64
[    0.164199] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.164202] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.164205] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.164207] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.164210] pci_bus 0000:00: resource 8 [mem 0xcff00000-0xfebfffff]
[    0.164213] pci_bus 0000:01: resource 1 [mem 0xe6000000-0xeaffffff]
[    0.164216] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.164218] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.164221] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.164224] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000dffff]
[    0.164227] pci_bus 0000:01: resource 8 [mem 0xcff00000-0xfebfffff]
[    0.164230] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.164232] pci_bus 0000:02: resource 1 [mem 0xe0000000-0xe3ffffff]
[    0.164235] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.164238] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
[    0.164241] pci_bus 0000:04: resource 0 [io  0x9000-0x9fff]
[    0.164284] NET: Registered protocol family 2
[    0.164540] TCP: Hash tables configured (established 8192 bind 8192)
[    0.164678] NET: Registered protocol family 1
[    0.236289] pci 0000:02:00.0: Boot video device
[    0.236345] Trying to unpack rootfs image as initramfs...
[    0.615464] Initialise module verification
[    0.615517] audit: initializing netlink socket (disabled)
[    0.642160] bounce pool size: 64 pages
[    0.642173] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.644281] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.645553] Key type asymmetric registered
[    0.645556] Asymmetric key parser 'x509' registered
[    0.645599] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.645631] io scheduler noop registered
[    0.645634] io scheduler deadline registered (default)
[    0.645641] io scheduler cfq registered
[    0.645820] pcieport 0000:00:0b.0: irq 40 for MSI/MSI-X
[    0.645896] pcieport 0000:00:0c.0: irq 41 for MSI/MSI-X
[    0.645967] pcieport 0000:00:0d.0: irq 42 for MSI/MSI-X
[    0.646039] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.646057] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.646238] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.646307] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.651124] isapnp: Scanning for PnP cards...
[    0.673126] Linux agpgart interface v0.103
[    0.676074] tun: Universal TUN/TAP device driver, 1.6
[    0.676076] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.676114] PPP generic driver version 2.4.2
[    0.676152] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.676155] ehci-pci: EHCI PCI platform driver
[    0.676183] ehci-pci 0000:00:04.1: setting latency timer to 64
[    0.676187] ehci-pci 0000:00:04.1: EHCI Host Controller
[    0.676194] ehci-pci 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.676204] ehci-pci 0000:00:04.1: debug port 1
[    0.676227] ehci-pci 0000:00:04.1: cache line size of 32 is not supported
[    0.676247] ehci-pci 0000:00:04.1: irq 22, io mem 0xeb006000
[    0.688019] ehci-pci 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.688045] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.688048] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.688051] usb usb1: Product: EHCI Host Controller
[    0.688053] usb usb1: Manufacturer: Linux 3.8.0-33-generic ehci_hcd
[    0.688163] hub 1-0:1.0: 10 ports detected
[    0.688341] ehci-platform: EHCI generic platform driver
[    0.688351] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.688378] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.688382] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.688387] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    0.688409] ohci_hcd 0000:00:04.0: irq 23, io mem 0xeb007000
[    0.746019] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.746022] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.746025] usb usb2: Product: OHCI Host Controller
[    0.746027] usb usb2: Manufacturer: Linux 3.8.0-33-generic ohci_hcd
[    0.746132] hub 2-0:1.0: 10 ports detected
[    0.746313] uhci_hcd: USB Universal Host Controller Interface driver
[    0.747024] mousedev: PS/2 mouse device common for all mice
[    0.747155] rtc_cmos 00:04: RTC can wake from S4
[    0.747307] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.747342] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.747452] device-mapper: uevent: version 1.0.3
[    0.747515] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [email]dm-devel@redhat.com[/email]
[    0.747537] EISA: Cannot allocate resource for mainboard
[    0.747539] Cannot allocate resource for EISA slot 1
[    0.747540] Cannot allocate resource for EISA slot 2
[    0.747542] Cannot allocate resource for EISA slot 3
[    0.747544] Cannot allocate resource for EISA slot 4
[    0.747546] Cannot allocate resource for EISA slot 5
[    0.747548] Cannot allocate resource for EISA slot 6
[    0.747550] Cannot allocate resource for EISA slot 7
[    0.747551] Cannot allocate resource for EISA slot 8
[    0.747553] EISA: Detected 0 cards.
[    0.747562] cpufreq-nforce2: No nForce2 chipset.
[    0.747565] cpuidle: using governor ladder
[    0.747566] cpuidle: using governor menu
[    0.747570] ledtrig-cpu: registered to indicate activity on CPUs
[    0.747572] EFI Variables Facility v0.08 2004-May-17
[    0.747882] TCP: cubic registered
[    0.748021] NET: Registered protocol family 10
[    0.748237] NET: Registered protocol family 17
[    0.748419] Using IPI No-Shortcut mode
[    0.748499] Loading module verification certificates
[    0.753040] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: cac17da54b6be5ca0ac92f3b2cb1130687394377'
[    0.757880] Key type encrypted registered
[    0.760437] rtc_cmos 00:04: setting system clock to 2013-11-17 19:19:13 UTC (1384715953)
[    0.760492] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.767489] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.000025] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.003957] isapnp: No Plug & Play device found
[    1.004444] Write protecting the kernel text: 6364k
[    1.004522] Write protecting the kernel read-only data: 2496k
[    1.004523] NX-protecting the kernel data: 3876k
[    1.075381] Disabling lock debugging due to kernel taint
[    1.076113] ahci 0000:00:0e.0: version 3.0
[    1.076362] ahci 0000:00:0e.0: controller can do NCQ, turning on CAP_NCQ
[    1.076365] ahci 0000:00:0e.0: controller can't do PMP, turning off CAP_PMP
[    1.076435] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.076438] ahci 0000:00:0e.0: flags: 64bit ncq sntf led clo pio 
[    1.076443] ahci 0000:00:0e.0: setting latency timer to 64
[    1.079421] scsi0 : ahci
[    1.083704] scsi1 : ahci
[    1.087674] scsi2 : ahci
[    1.091802] scsi3 : ahci
[    1.102285] pata_amd 0000:00:08.0: setting latency timer to 64
[    1.110371] scsi4 : pata_amd
[    1.112630] scsi5 : pata_amd
[    1.112898] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.112901] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.112958] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.113156] forcedeth 0000:00:0f.0: setting latency timer to 64
[    1.204087] firewire_ohci 0000:01:07.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    1.271400] usb 1-1: New USB device found, idVendor=148f, idProduct=2573
[    1.271405] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.271408] usb 1-1: Product: 802.11 bg WLAN
[    1.271412] usb 1-1: Manufacturer: Ralink
[    1.388774] ata5.00: HPA detected: current 976771055, native 976773168
[    1.388784] ata5.00: 976771055 sectors, multi 16: LBA48 
[    1.388812] ata5: nv_mode_filter: 0x7f39f&0x7f39f->0x7f39f, BIOS=0x7f000 (0xc7c00000) ACPI=0x7f01f (15:60:0x1f)
[    1.388817] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc7c00000) ACPI=0x701f (15:60:0x1f)
[    1.404768] ata5.00: configured for UDMA/133
[    1.405191] ata5.01: configured for UDMA/33
[    1.409062] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.410260] ata1.00: configured for UDMA/133
[    1.410405] scsi 0:0:0:0: Direct-Access     ATA      ST3500418AS      CC37 PQ: 0 ANSI: 5
[    1.410596] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.410598] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.410691] sd 0:0:0:0: [sda] Write Protect is off
[    1.410723] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.416150] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AAKB-0 05.0 PQ: 0 ANSI: 5
[    1.416324] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    1.416326] sd 4:0:0:0: [sdb] 976771055 512-byte logical blocks: (500 GB/465 GiB)
[    1.416383] sd 4:0:0:0: [sdb] Write Protect is off
[    1.416458] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.416704] scsi 4:0:1:0: CD-ROM            JLMS     XJ-HD166S        DS18 PQ: 0 ANSI: 5
[    1.417472] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.417476] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.417642] sr 4:0:1:0: Attached scsi CD-ROM sr0
[    1.417755] sr 4:0:1:0: Attached scsi generic sg2 type 5
[    1.420779] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.479417] sd 4:0:0:0: [sdb] Attached SCSI disk
[    1.612022] tsc: Refined TSC clocksource calibration: 2533.333 MHz
[    1.612029] Switching to clocksource tsc
[    1.636910] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:d0:91:2a:00
[    1.636914] forcedeth 0000:00:0f.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.704094] firewire_core 0000:01:07.0: created device fw0: GUID 007795a100001fd0, S400
[    2.792020] usb 2-2: new low-speed USB device number 2 using ohci_hcd
[    3.006047] usb 2-2: New USB device found, idVendor=0168, idProduct=1998
[    3.006052] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.006056] usb 2-2: Product: iPazzPort
[    3.006059] usb 2-2: Manufacturer: iPazzPort
[    3.312019] usb 2-4: new full-speed USB device number 3 using ohci_hcd
[    3.518737] init: ureadahead main process (329) terminated with status 5
[    3.532048] usb 2-4: New USB device found, idVendor=05a7, idProduct=1020
[    3.532053] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.532057] usb 2-4: Product: Bose USB Audio
[    3.532060] usb 2-4: Manufacturer: Bose Corporation
[    3.836021] usb 2-7: new full-speed USB device number 4 using ohci_hcd
[    4.048046] usb 2-7: New USB device found, idVendor=046e, idProduct=5577
[    4.048053] usb 2-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.048056] usb 2-7: Product: USB Multimedia Cordless Keyboard
[    4.048060] usb 2-7: Manufacturer: BTC
[    4.146344] Adding 9764860k swap on /dev/sdb6.  Priority:-1 extents:1 across:9764860k 
[    4.352025] usb 2-8: new full-speed USB device number 5 using ohci_hcd
[    4.573048] usb 2-8: New USB device found, idVendor=046d, idProduct=0b07
[    4.573055] usb 2-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.573058] usb 2-8: Product: Logitech BT Mini-Receiver
[    4.573062] usb 2-8: Manufacturer: Logitech
[    4.579040] hub 2-8:1.0: 3 ports detected
[    4.881050] usb 2-8.2: new full-speed USB device number 6 using ohci_hcd
[    5.005048] usb 2-8.2: New USB device found, idVendor=046d, idProduct=c71e
[    5.005054] usb 2-8.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.005058] usb 2-8.2: Product: Logitech BT Mini-Receiver
[    5.005061] usb 2-8.2: Manufacturer: Logitech
[    5.085045] usb 2-8.3: new full-speed USB device number 7 using ohci_hcd
[    5.213044] usb 2-8.3: New USB device found, idVendor=046d, idProduct=c71f
[    5.213049] usb 2-8.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.213052] usb 2-8.3: Product: Logitech BT Mini-Receiver
[    5.213055] usb 2-8.3: Manufacturer: Logitech
[    5.554201] lp: driver loaded but no devices found
[    5.956091] parport_pc 00:09: reported by Plug and Play ACPI
[    6.172379] microcode: CPU0 sig=0x10676, pf=0x1, revision=0x606
[    6.262046] ppdev: user-space parallel port driver
[    6.339809] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    6.339875] i2c i2c-1: nForce2 SMBus adapter at 0x1c80
[    6.604426] Linux video capture interface: v2.00
[    6.644593] microcode: CPU1 sig=0x10676, pf=0x1, revision=0x606
[    6.646575] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    6.721159] usbcore: registered new interface driver usbhid
[    6.721164] usbhid: USB HID core driver
[    6.855169] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-7/2-7:1.0/input/input3
[    6.856812] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-7/2-7:1.1/input/input4
[    6.905155] cfg80211: Calling CRDA to update world regulatory domain
[    6.972606] input: iPazzPort iPazzPort as /devices/pci0000:00/0000:00:04.0/usb2/2-2/2-2:1.0/input/input5
[    6.972872] hid-generic 0003:0168:1998.0001: input,hidraw2: USB HID v1.11 Keyboard [iPazzPort iPazzPort] on usb-0000:00:04.0-2/input0
[    6.973826] input: iPazzPort iPazzPort as /devices/pci0000:00/0000:00:04.0/usb2/2-2/2-2:1.1/input/input6
[    6.975175] hid-generic 0003:0168:1998.0002: input,hidraw3: USB HID v1.11 Mouse [iPazzPort iPazzPort] on usb-0000:00:04.0-2/input1
[    6.979193] hid-generic 0003:05A7:1020.0003: hiddev0,hidraw4: USB HID v1.10 Device [Bose Corporation Bose USB Audio] on usb-0000:00:04.0-4/input2
[    6.980366] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:04.0/usb2/2-8/2-8.2/2-8.2:1.0/input/input7
[    6.980627] hid-generic 0003:046D:C71E.0006: input,hidraw5: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:04.0-8.2/input0
[    6.998431] psmouse serio1: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[    7.068477] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:04.0/usb2/2-8/2-8.3/2-8.3:1.0/input/input8
[    7.069865] logitech 0003:046D:C71F.0007: input,hiddev0,hidraw6: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:04.0-8.3/input0
[    7.369573] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input9
[    7.441548] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.9 loaded
[    7.441964] cx88/0: cx2388x v4l2 driver version 0.0.9 loaded
[    7.442651] cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68,autodetected], frontend(s): 2
[    7.442654] cx88[0]: TV tuner type 63, Radio tuner type -1
[    7.449586] cx2388x alsa driver version 0.0.9 loaded
[    7.562224] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
[    7.582044] 3:1:1: cannot get freq at ep 0x1
[    7.624275] usbcore: registered new interface driver snd-usb-audio
[    7.734535] snd_hda_intel 0000:00:09.0: setting latency timer to 64
[    7.892023] usb 1-1: reset high-speed USB device number 2 using ehci-pci
[    8.221016] tda9887 2-0043: creating new instance
[    8.262407] tveeprom 2-0050: audio processor is CX882 (idx 33)
[    8.262409] tveeprom 2-0050: decoder processor is CX882 (idx 25)
[    8.262412] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[    8.262414] cx88[0]: hauppauge eeprom: model=69009
[    8.451313] tuner-simple 2-0061: creating new instance
[    8.600015] Registered IR keymap rc-hauppauge
[    8.600251] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:0a.0/0000:01:06.2/rc/rc0/input10
[    8.600345] rc0: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:0a.0/0000:01:06.2/rc/rc0
[    8.600393] cx88[0]/2: cx2388x 8802 Driver Manager
[    8.600625] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 17, latency: 32, mmio: 0xe8000000
[    8.600678] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 17, latency: 32, mmio: 0xe6000000
[    8.632614] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    8.633447] usbcore: registered new interface driver rt73usb
[    8.658997] IR NEC protocol handler initialized
[    8.743264] IR RC5(x) protocol handler initialized
[    8.789002] cfg80211: World regulatory domain updated:
[    8.789006] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.789009] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.789011] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.789014] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.789016] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.789018] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.825936] IR RC6 protocol handler initialized
[    8.900923] IR JVC protocol handler initialized
[    8.901398] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[    8.901401] cx88/2: registering cx8802 driver, type: dvb access: shared
[    8.901404] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68]
[    8.901407] cx88[0]/2: cx2388x based DVB/ATSC card
[    8.901409] cx8802_alloc_frontends() allocating 2 frontend(s)
[    8.999895] IR Sony protocol handler initialized
[    9.066475] wm8775 2-001b: chip found @ 0x36 (cx88[0])
[    9.087246] IR SANYO protocol handler initialized
[    9.175692] input: MCE IR Keyboard/Mouse (cx88xx) as /devices/virtual/input/input11
[    9.175780] IR MCE Keyboard/mouse protocol handler initialized
[    9.289503] lirc_dev: IR Remote Control driver registered, major 249 
[    9.332316] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
[    9.453483] type=1400 audit(1384715962.190:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=745 comm="apparmor_parser"
[    9.453494] type=1400 audit(1384715962.190:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=746 comm="apparmor_parser"
[    9.453991] type=1400 audit(1384715962.190:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=746 comm="apparmor_parser"
[    9.454056] type=1400 audit(1384715962.190:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=745 comm="apparmor_parser"
[    9.454268] type=1400 audit(1384715962.190:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=746 comm="apparmor_parser"
[    9.454335] type=1400 audit(1384715962.190:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=745 comm="apparmor_parser"
[    9.454802] type=1400 audit(1384715962.190:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=901 comm="apparmor_parser"
[    9.455304] type=1400 audit(1384715962.190:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=901 comm="apparmor_parser"
[    9.455589] type=1400 audit(1384715962.190:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=901 comm="apparmor_parser"
[    9.499703] tuner-simple 2-0061: attaching existing instance
[    9.499708] tuner-simple 2-0061: couldn't set type to 63. Using 78 (Philips FMD1216MEX MK3 Hybrid Tuner) instead
[    9.503537] DVB: registering new adapter (cx88[0])
[    9.503543] cx88-mpeg driver manager 0000:01:06.2: DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
[    9.504055] cx88-mpeg driver manager 0000:01:06.2: DVB: registering adapter 0 frontend 1 (Conexant CX22702 DVB-T)...
[    9.527190] cx88[0]/0: registered device video0 [v4l2]
[    9.527584] cx88[0]/0: registered device vbi0
[    9.527651] cx88[0]/0: registered device radio0
[    9.528055] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[    9.673050] type=1400 audit(1384715962.410:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=915 comm="apparmor_parser"
[    9.755962] nvidia: module license 'NVIDIA' taints kernel.
[    9.787196] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   10.060514] init: failsafe main process (934) killed by TERM signal
[   10.104120] input: HDA NVidia HDMI/DP,pcm=3 Phantom as /devices/pci0000:00/0000:00:09.0/sound/card0/input12
[   10.104283] input: HDA NVidia Line as /devices/pci0000:00/0000:00:09.0/sound/card0/input13
[   10.104415] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:09.0/sound/card0/input14
[   10.104542] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:09.0/sound/card0/input15
[   10.104670] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:09.0/sound/card0/input16
[   10.104804] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:09.0/sound/card0/input17
[   10.104931] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:09.0/sound/card0/input18
[   10.105058] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:09.0/sound/card0/input19
[   10.105186] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:09.0/sound/card0/input20
[   11.995285] NET: Registered protocol family 31
[   11.995287] Bluetooth: HCI device and connection manager initialized
[   11.995592] Bluetooth: HCI socket layer initialized
[   11.995596] Bluetooth: L2CAP socket layer initialized
[   11.995603] Bluetooth: SCO socket layer initialized
[   12.141717] Bluetooth: RFCOMM socket layer initialized
[   12.224535] Bluetooth: BNEP filters: protocol multicast
[   12.224546] Bluetooth: BNEP socket layer initialized
[   14.473516] init: udev-fallback-graphics main process (1240) terminated with status 1
[   15.436838] forcedeth 0000:00:0f.0: irq 43 for MSI/MSI-X
[   15.436873] forcedeth 0000:00:0f.0 eth0: MSI enabled
[   15.437106] forcedeth 0000:00:0f.0 eth0: no link during initialization
[   19.136434] wlan0: authenticate with cc:5d:4e:ae:c0:bc
[   19.175197] wlan0: send auth to cc:5d:4e:ae:c0:bc (try 1/3)
[   19.177034] wlan0: authenticated
[   19.180016] wlan0: associate with cc:5d:4e:ae:c0:bc (try 1/3)
[   19.182618] wlan0: RX AssocResp from cc:5d:4e:ae:c0:bc (capab=0x431 status=0 aid=4)
[   19.193148] wlan0: associated
[   19.193172] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   19.984367] init: plymouth-upstart-bridge main process (1058) killed by TERM signal
[   27.022704] i2c i2c-2: sendbytes: NAK bailout.
[   27.022730] cx22702_writereg: error (reg == 0x0d, val == 0x00, ret == -5)
[   27.059070] i2c i2c-2: sendbytes: NAK bailout.
[   27.059096] cx22702_writereg: error (reg == 0x0d, val == 0x00, ret == -5)
[   31.253047] 3:1:1: cannot get freq at ep 0x1
[   31.260047] 3:1:1: cannot get freq at ep 0x1
[   31.404050] 3:1:1: cannot get freq at ep 0x1
[   31.411046] 3:1:1: cannot get freq at ep 0x1
[   31.432048] 3:1:1: cannot get freq at ep 0x1
[   31.439047] 3:1:1: cannot get freq at ep 0x1
[   31.478049] 3:1:1: cannot get freq at ep 0x1
[   31.485049] 3:1:1: cannot get freq at ep 0x1
[   87.654734] cx88[0]: irq mpeg  [0x100000] ts_err?*
[   87.654741] cx88[0]/2-mpeg: general errors: 0x00100000
[ 1014.882127] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1016.358595] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1016.398858] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1016.558748] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1017.197398] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1017.277495] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1018.276714] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1021.069820] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1028.543864] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1029.190525] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1029.510002] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1032.590277] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1033.069352] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1033.548471] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1033.907847] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1034.466766] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1034.913968] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1035.025985] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1035.346718] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1037.118461] cx88[0]/2-mpeg: general errors: 0x00000100
[ 1076.545160] init: mythtv-backend main process (1671) killed by TERM signal
[ 1090.085063] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[ 1090.089582] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[ 1095.083348] cx24116_load_firmware: FW version 1.26.90.0
[ 1095.083361] cx24116_firmware_ondemand: Firmware upload complete
[ 1110.758637] i2c i2c-2: sendbytes: NAK bailout.
[ 1110.758662] cx22702_writereg: error (reg == 0x0d, val == 0x00, ret == -5)
[ 1117.752265] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[ 1117.752328] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[ 1122.747352] cx24116_load_firmware: FW version 1.26.90.0
[ 1122.747365] cx24116_firmware_ondemand: Firmware upload complete
[ 1143.622669] i2c i2c-2: sendbytes: NAK bailout.
[ 1143.622694] cx22702_writereg: error (reg == 0x0d, val == 0x00, ret == -5)
peter@peter-GA-73PVM-S2H:~$ 

I'm wondering if there is anything glaringly obvious to the experts out there

---

