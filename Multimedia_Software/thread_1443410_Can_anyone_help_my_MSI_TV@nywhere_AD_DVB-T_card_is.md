---
title: "Can anyone help my MSI TV@nywhere A/D DVB-T card is not recognized by ubuntu"
date: 2010-03-31
forum: Multimedia Software
---

### Post by thedruz on 2010-03-31
Can anyone help my MSI TV@nywhere A/D DVB-T card is not recognized by either ubuntu or   MYTHtv on ubuntu, the MYTHtv Wiki says it should be but It's not
the following is the wiki page for my card.

   * DVB-T and Analog 	

   * Philips SAA7133
   * Philips TDA10046H 

   * TV Antenna in
   * FM Antenna in
   * S-Video in
   * Composite video + stereo audio in
   * IR-Remote 

   * Hybrid analog/digital card
   * Supported by Linux kernel 2.6.15
   * clone of Lifeview FlyDVB-T Hybrid
   * requires "card=94"

I am a bit of a linux noob but can do a bit at the terminal window &  am not afraid of the command line.
I think it has something to do with card=94 but just what does that  mean?
Help someone please, I am sick of windows,which seems to bog right down  after a while.  						 						is not recognized by  MYTHtv, the MYTHtv Wiki says it should be but It's not
the following is the wiki page for my card.

   * DVB-T and Analog 	

   * Philips SAA7133
   * Philips TDA10046H 

   * TV Antenna in
   * FM Antenna in
   * S-Video in
   * Composite video + stereo audio in
   * IR-Remote 

   * Hybrid analog/digital card
   * Supported by Linux kernel 2.6.15
   * clone of Lifeview FlyDVB-T Hybrid
   * requires "card=94"

I am a bit of a linux noob but can do a bit at the terminal window &  am not afraid of the command line.
I think it has something to do with card=94 but just what does that  mean?
Help someone please, I am sick of windows,which seems to bog right down  after a while.

---

### Post by steefjeqv on 2010-03-31
Hi,

Try installing Kaffeine or Me-TV.
If everything is okay your card should be recognized be these programs.

Greetings,
Steven

---

### Post by thedruz on 2010-03-31
Thanks Steve, Already Tried that the card is recognized in me-tv but won't tune any stations Modified Modprobe.d/options with card=94 tuner=37 after a search but to no avail I live in Australia & am wondering if Tuner=37 is correct?.

---

### Post by thedruz on 2010-03-31
Thanks Steve, Already Tried that the card is recognized in me-tv but  won't tune any stations Modified Modprobe.d/options with card=94  tuner=37 after a search but to no avail I live in Australia & am  wondering if Tuner=37 is correct?.

---

### Post by steefjeqv on 2010-03-31
Hi,

Can you check/post your dmesg output ?
I'm off to work now, so I won't be able to reply within the first eight hours or so.

Greetings,
Steven

---

### Post by thedruz on 2010-03-31
Here's my dmesg output, as you can see I tried changing the Tuner= from 37 to 28 [didn't work]
  
  0.375378] io scheduler noop registered
[    0.375380] io scheduler anticipatory registered
[    0.375381] io scheduler deadline registered
[    0.375410] io scheduler cfq registered (default)
[    0.408079] pci 0000:02:00.0: Boot video device
[    0.408211]   alloc irq_desc for 24 on node -1
[    0.408213]   alloc kstat_irqs on node -1
[    0.408221] pcieport-driver 0000:00:0b.0: irq 24 for MSI/MSI-X
[    0.408226] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    0.408297]   alloc irq_desc for 25 on node -1
[    0.408298]   alloc kstat_irqs on node -1
[    0.408303] pcieport-driver 0000:00:0c.0: irq 25 for MSI/MSI-X
[    0.408307] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    0.408377]   alloc irq_desc for 26 on node -1
[    0.408378]   alloc kstat_irqs on node -1
[    0.408383] pcieport-driver 0000:00:0d.0: irq 26 for MSI/MSI-X
[    0.408387] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    0.408440] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.408458] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.408556] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.408560] ACPI: Power Button [PWRF]
[    0.408605] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.408611] ACPI: Power Button [PWRB]
[    0.409099] ACPI: SSDT bffae670 002B9 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.409328] processor LNXCPU:00: registered as cooling_device0
[    0.409331] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.409590] ACPI: SSDT bffae930 002B9 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.409804] processor LNXCPU:01: registered as cooling_device1
[    0.413698] ACPI Warning: \_TZ_.THRM._TZD: Return Package type mismatch at index 0 - found Processor, expected Reference 20090521 nspredef-946
[    0.413704] ACPI: Expecting a [Reference] package element, found type C
[    0.413809] thermal LNXTHERM:01: registered as thermal_zone0
[    0.413815] ACPI: Thermal Zone [THRM] (34 C)
[    0.413854] isapnp: Scanning for PnP cards...
[    0.521058] Switched to high resolution mode on CPU 1
[    0.523915] Switched to high resolution mode on CPU 0
[    0.766973] isapnp: No Plug & Play device found
[    0.767784] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.767884] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.767968] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.768187] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.768298] 00:05: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.769076] brd: module loaded
[    0.769390] loop: module loaded
[    0.769441] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.769496] ahci 0000:00:0e.0: version 3.0
[    0.769659] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 5
[    0.769660] PCI: setting IRQ 5 as level-triggered
[    0.769664] ahci 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 5 (level, low) -> IRQ 5
[    0.769685]   alloc irq_desc for 27 on node -1
[    0.769686]   alloc kstat_irqs on node -1
[    0.769692] ahci 0000:00:0e.0: irq 27 for MSI/MSI-X
[    0.769697] ahci 0000:00:0e.0: controller can do NCQ, turning on CAP_NCQ
[    0.769758] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
[    0.769760] ahci 0000:00:0e.0: flags: 64bit ncq sntf led clo pmp pio 
[    0.769763] ahci 0000:00:0e.0: setting latency timer to 64
[    0.770270] scsi0 : ahci
[    0.770327] scsi1 : ahci
[    0.770361] scsi2 : ahci
[    0.770394] scsi3 : ahci
[    0.770465] ata1: SATA max UDMA/133 abar m8192@0xfce7c000 port 0xfce7c100 irq 27
[    0.770467] ata2: SATA max UDMA/133 abar m8192@0xfce7c000 port 0xfce7c180 irq 27
[    0.770469] ata3: SATA max UDMA/133 abar m8192@0xfce7c000 port 0xfce7c200 irq 27
[    0.770471] ata4: SATA max UDMA/133 abar m8192@0xfce7c000 port 0xfce7c280 irq 27
[    0.770639] pata_amd 0000:00:08.0: version 0.4.1
[    0.770676] pata_amd 0000:00:08.0: setting latency timer to 64
[    0.770709] scsi4 : pata_amd
[    0.770745] scsi5 : pata_amd
[    0.771447] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.771449] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.771977] Fixed MDIO Bus: probed
[    0.772011] PPP generic driver version 2.4.2
[    0.772070] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.772234] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 11
[    0.772236] PCI: setting IRQ 11 as level-triggered
[    0.772240] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 11 (level, low) -> IRQ 11
[    0.772247] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.772249] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.772270] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.772290] ehci_hcd 0000:00:04.1: debug port 1
[    0.772293] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    0.772299] ehci_hcd 0000:00:04.1: irq 11, io mem 0xfce7ec00
[    0.784008] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.784101] usb usb1: configuration #1 chosen from 1 choice
[    0.784137] hub 1-0:1.0: USB hub found
[    0.784145] hub 1-0:1.0: 8 ports detected
[    0.784357] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 7
[    0.784358] PCI: setting IRQ 7 as level-triggered
[    0.784362] ehci_hcd 0000:01:05.2: PCI INT C -> Link[LNKD] -> GSI 7 (level, low) -> IRQ 7
[    0.784369] ehci_hcd 0000:01:05.2: EHCI Host Controller
[    0.784391] ehci_hcd 0000:01:05.2: new USB bus registered, assigned bus number 2
[    0.784418] ehci_hcd 0000:01:05.2: irq 7, io mem 0xfcfffc00
[    0.796010] ehci_hcd 0000:01:05.2: USB 2.0 started, EHCI 1.00
[    0.796083] usb usb2: configuration #1 chosen from 1 choice
[    0.796114] hub 2-0:1.0: USB hub found
[    0.796121] hub 2-0:1.0: 4 ports detected
[    0.796175] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.796348] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 10
[    0.796350] PCI: setting IRQ 10 as level-triggered
[    0.796353] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 10 (level, low) -> IRQ 10
[    0.796359] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.796362] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.796381] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.796392] ohci_hcd 0000:00:04.0: irq 10, io mem 0xfce7f000
[    0.854034] usb usb3: configuration #1 chosen from 1 choice
[    0.854052] hub 3-0:1.0: USB hub found
[    0.854058] hub 3-0:1.0: 8 ports detected
[    0.854095] uhci_hcd: USB Universal Host Controller Interface driver
[    0.854263] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    0.854266] uhci_hcd 0000:01:05.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    0.854270] uhci_hcd 0000:01:05.0: UHCI Host Controller
[    0.854291] uhci_hcd 0000:01:05.0: new USB bus registered, assigned bus number 4
[    0.854309] uhci_hcd 0000:01:05.0: irq 10, io base 0x0000dc00
[    0.854365] usb usb4: configuration #1 chosen from 1 choice
[    0.854383] hub 4-0:1.0: USB hub found
[    0.854387] hub 4-0:1.0: 2 ports detected
[    0.854570] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.854572] uhci_hcd 0000:01:05.1: PCI INT B -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.854577] uhci_hcd 0000:01:05.1: UHCI Host Controller
[    0.854603] uhci_hcd 0000:01:05.1: new USB bus registered, assigned bus number 5
[    0.854621] uhci_hcd 0000:01:05.1: irq 11, io base 0x0000d880
[    0.854676] usb usb5: configuration #1 chosen from 1 choice
[    0.854693] hub 5-0:1.0: USB hub found
[    0.854698] hub 5-0:1.0: 2 ports detected
[    0.854763] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[    0.854764] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.855065] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.855069] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.855107] mice: PS/2 mouse device common for all mice
[    0.855181] rtc_cmos 00:08: RTC can wake from S4
[    0.855201] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.855225] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.855291] device-mapper: uevent: version 1.0.3
[    0.855350] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.855393] device-mapper: multipath: version 1.1.0 loaded
[    0.855395] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.855472] EISA: Probing bus 0 at eisa.0
[    0.855482] Cannot allocate resource for EISA slot 4
[    0.855492] EISA: Detected 0 cards.
[    0.855541] cpuidle: using governor ladder
[    0.855542] cpuidle: using governor menu
[    0.855886] TCP cubic registered
[    0.855992] NET: Registered protocol family 10
[    0.856333] lo: Disabled Privacy Extensions
[    0.856564] NET: Registered protocol family 17
[    0.856578] Bluetooth: L2CAP ver 2.13
[    0.856579] Bluetooth: L2CAP socket layer initialized
[    0.856581] Bluetooth: SCO (Voice Link) ver 0.6
[    0.856582] Bluetooth: SCO socket layer initialized
[    0.856601] Bluetooth: RFCOMM TTY layer initialized
[    0.856603] Bluetooth: RFCOMM socket layer initialized
[    0.856604] Bluetooth: RFCOMM ver 1.11
[    0.857013] Using IPI No-Shortcut mode
[    0.857054] PM: Resume from disk failed.
[    0.857063] registered taskstats version 1
[    0.857166]   Magic number: 2:328:855
[    0.857231] rtc_cmos 00:08: setting system clock to 2010-03-31 21:49:26 UTC (1270072166)
[    0.857233] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.857234] EDD information not available.
[    1.088012] ata2: SATA link down (SStatus 0 SControl 300)
[    1.088027] ata4: SATA link down (SStatus 0 SControl 300)
[    1.096015] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.252010] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.252022] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.252470] ata3.00: ATAPI: ATAPI   DVD A  DH16A6S, YA17, max UDMA/100
[    1.252909] ata1.00: ATA-8: Hitachi HDT721064SLA360, STDOA31B, max UDMA/133
[    1.252913] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.253174] ata3.00: configured for UDMA/100
[    1.254086] ata1.00: configured for UDMA/133
[    1.254215] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72106 STDO PQ: 0 ANSI: 5
[    1.254346] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.254388] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.254446] sd 0:0:0:0: [sda] Write Protect is off
[    1.254448] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.254464] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.254552]  sda:
[    1.255568] scsi 2:0:0:0: CD-ROM            ATAPI    DVD A  DH16A6S   YA17 PQ: 0 ANSI: 5
[    1.260827] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.260830] Uniform CD-ROM driver Revision: 3.20
[    1.260913] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.260964] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.261006] ata6: port disabled. ignoring.
[    1.269124]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.288743] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.288757] Freeing unused kernel memory: 540k freed
[    1.289178] Write protecting the kernel text: 4580k
[    1.289208] Write protecting the kernel read-only data: 1840k
[    1.378851] usb 1-2: configuration #1 chosen from 1 choice
[    1.393941] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.394159] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 7
[    1.394162] forcedeth 0000:00:0f.0: PCI INT A -> Link[LMAC] -> GSI 7 (level, low) -> IRQ 7
[    1.394166] forcedeth 0000:00:0f.0: setting latency timer to 64
[    1.432994] ohci1394 0000:01:07.0: PCI INT A -> Link[LNKD] -> GSI 7 (level, low) -> IRQ 7
[    1.438866] Initializing USB Mass Storage driver...
[    1.439011] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.439095] usb-storage: device found at 2
[    1.439096] usb-storage: waiting for device to settle before scanning
[    1.439101] usbcore: registered new interface driver usb-storage
[    1.439103] USB Mass Storage support registered.
[    1.488017] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.490515] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[7]  MMIO=[fcffe800-fcffefff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.621585] usb 1-3: configuration #1 chosen from 1 choice
[    1.622589] scsi7 : SCSI emulation for USB Mass Storage devices
[    1.622738] usb-storage: device found at 3
[    1.622740] usb-storage: waiting for device to settle before scanning
[    1.788013] usb 1-5: new high speed USB device using ehci_hcd and address 5
[    1.913025] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:24:21:7d:f6:3c
[    1.913027] forcedeth 0000:00:0f.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.922286] usb 1-5: configuration #1 chosen from 1 choice
[    1.923874] scsi8 : SCSI emulation for USB Mass Storage devices
[    1.924844] usb-storage: device found at 5
[    1.924845] usb-storage: waiting for device to settle before scanning
[    2.036011] usb 1-6: new high speed USB device using ehci_hcd and address 6
[    2.172623] usb 1-6: configuration #1 chosen from 1 choice
[    2.173344] hub 1-6:1.0: USB hub found
[    2.173557] hub 1-6:1.0: 4 ports detected
[    2.652010] usb 3-4: new low speed USB device using ohci_hcd and address 2
[    2.820096] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00dc10008ce09501]
[    2.882604] PM: Starting manual resume from disk
[    2.882607] PM: Resume from partition 8:6
[    2.882608] PM: Checking hibernation image.
[    2.882714] PM: Resume from disk failed.
[    2.888345] usb 3-4: configuration #1 chosen from 1 choice
[    2.894477] usbcore: registered new interface driver hiddev
[    2.894531] usbcore: registered new interface driver usbhid
[    2.894532] usbhid: v2.6:USB HID core driver
[    2.898225] EXT4-fs (sda5): barriers enabled
[    2.902118] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:04.0/usb3/3-4/3-4:1.0/input/input3
[    2.902166] microsoft 0003:045E:009D.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:04.0-4/input0
[    2.909721] kjournald2 starting: pid 435, dev sda5:8, commit interval 5 seconds
[    2.909771] EXT4-fs (sda5): delayed allocation enabled
[    2.909775] EXT4-fs: file extents enabled
[    2.911377] EXT4-fs: mballoc enabled
[    2.911387] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    2.922982] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:04.0/usb3/3-4/3-4:1.1/input/input4
[    2.923049] microsoft 0003:045E:009D.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:04.0-4/input1
[    3.192012] usb 3-7: new full speed USB device using ohci_hcd and address 3
[    3.344152] type=1505 audit(1270072168.986:2): operation="profile_load" pid=461 name=/usr/share/gdm/guest-session/Xsession
[    3.345944] type=1505 audit(1270072168.986:3): operation="profile_load" pid=462 name=/sbin/dhclient3
[    3.346457] type=1505 audit(1270072168.986:4): operation="profile_load" pid=462 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.346755] type=1505 audit(1270072168.986:5): operation="profile_load" pid=462 name=/usr/lib/connman/scripts/dhclient-script
[    3.370710] type=1505 audit(1270072169.010:6): operation="profile_load" pid=463 name=/usr/bin/evince
[    3.378993] type=1505 audit(1270072169.018:7): operation="profile_load" pid=463 name=/usr/bin/evince-previewer
[    3.383881] type=1505 audit(1270072169.022:8): operation="profile_load" pid=463 name=/usr/bin/evince-thumbnailer
[    3.411409] type=1505 audit(1270072169.050:9): operation="profile_load" pid=465 name=/usr/lib/cups/backend/cups-pdf
[    3.412114] type=1505 audit(1270072169.054:10): operation="profile_load" pid=465 name=/usr/sbin/cupsd
[    3.413175] usb 3-7: configuration #1 chosen from 1 choice
[    3.500228] usb 1-6.3: new high speed USB device using ehci_hcd and address 8
[    3.610550] usb 1-6.3: configuration #1 chosen from 1 choice
[    3.610762] scsi9 : SCSI emulation for USB Mass Storage devices
[    3.610833] usb-storage: device found at 8
[    3.610834] usb-storage: waiting for device to settle before scanning
[    3.696203] usb 1-6.4: new full speed USB device using ehci_hcd and address 9
[    3.804997] usb 1-6.4: configuration #1 chosen from 1 choice
[    6.436143] usb-storage: device scan complete
[    6.438109] scsi 6:0:0:0: Direct-Access     Generic  Compact Flash    0.00 PQ: 0 ANSI: 2
[    6.438604] scsi 6:0:0:1: Direct-Access     Generic  SD/MMC           0.00 PQ: 0 ANSI: 2
[    6.439103] scsi 6:0:0:2: Direct-Access     Generic  microSD          0.00 PQ: 0 ANSI: 2
[    6.439603] scsi 6:0:0:3: Direct-Access     Generic  MS/MS-PRO        0.00 PQ: 0 ANSI: 2
[    6.440104] scsi 6:0:0:4: Direct-Access     Generic  SM/xD-Picture    0.00 PQ: 0 ANSI: 2
[    6.440414] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.440476] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    6.440543] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    6.440609] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    6.440674] sd 6:0:0:4: Attached scsi generic sg6 type 0
[    6.444458] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    6.445083] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    6.445707] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    6.446332] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    6.446958] sd 6:0:0:4: [sdf] Attached SCSI removable disk
[    6.620206] usb-storage: device scan complete
[    6.622089] scsi 7:0:0:0: Direct-Access     WDC WD32 00AAJB-00WGA0    0811 PQ: 0 ANSI: 0
[    6.622351] sd 7:0:0:0: Attached scsi generic sg7 type 0
[    6.623197] sd 7:0:0:0: [sdg] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    6.625445] sd 7:0:0:0: [sdg] Test WP failed, assume Write Enabled
[    6.625448] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[    6.628443] sd 7:0:0:0: [sdg] Test WP failed, assume Write Enabled
[    6.628446] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[    6.628451]  sdg: sdg1
[    6.631442] sd 7:0:0:0: [sdg] Test WP failed, assume Write Enabled
[    6.631446] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[    6.631448] sd 7:0:0:0: [sdg] Attached SCSI disk
[    6.924311] usb-storage: device scan complete
[    6.926062] scsi 8:0:0:0: Direct-Access     WDC WD32 00AAJB-00WGA0    0811 PQ: 0 ANSI: 0
[    6.926331] sd 8:0:0:0: Attached scsi generic sg8 type 0
[    6.927170] sd 8:0:0:0: [sdh] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    6.929417] sd 8:0:0:0: [sdh] Test WP failed, assume Write Enabled
[    6.929420] sd 8:0:0:0: [sdh] Assuming drive cache: write through
[    6.932416] sd 8:0:0:0: [sdh] Test WP failed, assume Write Enabled
[    6.932419] sd 8:0:0:0: [sdh] Assuming drive cache: write through
[    6.932422]  sdh: sdh1
[    6.935416] sd 8:0:0:0: [sdh] Test WP failed, assume Write Enabled
[    6.935419] sd 8:0:0:0: [sdh] Assuming drive cache: write through
[    6.935422] sd 8:0:0:0: [sdh] Attached SCSI disk
[    8.608185] usb-storage: device scan complete
[    8.609915] scsi 9:0:0:0: Direct-Access     SAMSUNG  SP2514N          VF10 PQ: 0 ANSI: 0
[    8.610194] sd 9:0:0:0: Attached scsi generic sg9 type 0
[    8.611021] sd 9:0:0:0: [sdi] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    8.612769] sd 9:0:0:0: [sdi] Write Protect is off
[    8.612773] sd 9:0:0:0: [sdi] Mode Sense: 03 00 00 00
[    8.612776] sd 9:0:0:0: [sdi] Assuming drive cache: write through
[    8.615766] sd 9:0:0:0: [sdi] Assuming drive cache: write through
[    8.615770]  sdi: sdi1
[    8.618770] sd 9:0:0:0: [sdi] Assuming drive cache: write through
[    8.618772] sd 9:0:0:0: [sdi] Attached SCSI disk
[   12.449242] udev: starting version 147
[   12.457161] Adding 1309256k swap on /dev/sda6.  Priority:-1 extents:1 across:1309256k 
[   12.478841] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4d00
[   12.478857] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4e00
[   12.546069] EXT4-fs (sda5): internal journal on sda5:8
[   12.586566] Linux video capture interface: v2.00
[   12.595061] gspca: main v2.6.0 registered
[   12.596079] gspca: probing 0c45:602c
[   12.604243] acer-wmi: Acer Laptop ACPI-WMI Extras
[   12.604256] acer-wmi: No or unsupported WMI interface, unable to load
[   12.617440] lp: driver loaded but no devices found
[   12.627356] saa7130/34: v4l2 driver version 0.2.15 loaded
[   12.627432] saa7134 0000:01:06.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   12.627440] saa7133[0]: found at 0000:01:06.0, rev: 209, irq: 11, latency: 64, mmio: 0xfcfff000
[   12.627445] saa7133[0]: subsystem: 1462:8625, board: LifeView FlyDVB-T Hybrid Cardbus/MSI TV @nywhere A/D NB [card=94,insmod option]
[   12.627461] saa7133[0]: board init: gpio is 100
[   12.627469] IRQ 11/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   12.631094] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.640441] gspca: probe ok
[   12.640462] usbcore: registered new interface driver sonixb
[   12.640465] sonixb: registered
[   12.675431] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[   12.675609] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 7
[   12.675612] HDA Intel 0000:00:09.0: PCI INT A -> Link[LAZA] -> GSI 7 (level, low) -> IRQ 7
[   12.675635] HDA Intel 0000:00:09.0: setting latency timer to 64
[   12.675731] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1098
[   12.675747] usbcore: registered new interface driver usblp
[   12.788021] RPC: Registered udp transport module.
[   12.788023] RPC: Registered tcp transport module.
[   12.799817] saa7133[0]: i2c eeprom 00: 62 14 25 86 ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799827] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799836] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799844] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799852] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799861] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799869] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799877] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799885] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799893] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799901] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799909] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799917] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799926] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799934] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799942] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.799952] i2c-adapter i2c-2: Invalid 7-bit address 0x7a
[   12.852128] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[   12.864032] tuner-simple 2-004b: creating new instance
[   12.864037] tuner-simple 2-004b: type set to 28 (LG PAL_BG+FM (TPI8PSB01D))
[   12.889150] saa7133[0]: registered device video1 [v4l2]
[   12.889168] saa7133[0]: registered device vbi0
[   12.889185] saa7133[0]: registered device radio0
[   12.892745] saa7134 ALSA driver for DMA sound loaded
[   12.892754] IRQ 11/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   12.892770] saa7133[0]/alsa: saa7133[0] at 0xfcfff000 irq 11 registered as card -2
[   12.905885] dvb_init() allocating 1 frontend
[   12.949717] DVB: registering new adapter (saa7133[0])
[   12.949721] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   12.953137]   alloc irq_desc for 28 on node -1
[   12.953140]   alloc kstat_irqs on node -1
[   12.953148] forcedeth 0000:00:0f.0: irq 28 for MSI/MSI-X
[   12.974201] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   13.009834] __ratelimit: 9 callbacks suppressed
[   13.009836] type=1505 audit(1270032578.650:14): operation="profile_replace" pid=1140 name=/usr/share/gdm/guest-session/Xsession
[   13.011007] type=1505 audit(1270032578.650:15): operation="profile_replace" pid=1141 name=/sbin/dhclient3
[   13.011523] type=1505 audit(1270032578.650:16): operation="profile_replace" pid=1141 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   13.011804] type=1505 audit(1270032578.650:17): operation="profile_replace" pid=1141 name=/usr/lib/connman/scripts/dhclient-script
[   13.014587] type=1505 audit(1270032578.654:18): operation="profile_replace" pid=1142 name=/usr/bin/evince
[   13.024456] type=1505 audit(1270032578.666:19): operation="profile_replace" pid=1142 name=/usr/bin/evince-previewer
[   13.029457] type=1505 audit(1270032578.670:20): operation="profile_replace" pid=1142 name=/usr/bin/evince-thumbnailer
[   13.036561] type=1505 audit(1270032578.678:21): operation="profile_replace" pid=1144 name=/usr/lib/cups/backend/cups-pdf
[   13.037170] type=1505 audit(1270032578.678:22): operation="profile_replace" pid=1144 name=/usr/sbin/cupsd
[   13.038868] type=1505 audit(1270032578.678:23): operation="profile_replace" pid=1145 name=/usr/sbin/mysqld
[   13.057052] tda1004x: setting up plls for 48MHz sampling clock
[   13.349023] hda_codec: Unknown model for ALC1200, trying auto-probe from BIOS...
[   13.365389] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:09.0/input/input5
[   13.372776] tda1004x: found firmware revision 29 -- ok
[   14.502382] svc: failed to register lockdv1 RPC service (errno 97).
[   14.502932] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   14.556454] NFSD: starting 90-second grace period
[   14.763447] ppdev: user-space parallel port driver
[   15.379327] CPU0 attaching NULL sched-domain.
[   15.379332] CPU1 attaching NULL sched-domain.
[   15.388571] CPU0 attaching sched-domain:
[   15.388574]  domain 0: span 0-1 level MC
[   15.388577]   groups: 0 1
[   15.388583]   domain 1: span 0-1 level CPU
[   15.388586]    groups: 0-1 (__cpu_power = 2048)
[   15.388592] CPU1 attaching sched-domain:
[   15.388594]  domain 0: span 0-1 level MC
[   15.388597]   groups: 1 0
[   15.388602]   domain 1: span 0-1 level CPU
[   15.388604]    groups: 0-1 (__cpu_power = 2048)
[   16.075400] usb 3-7: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   16.939547] CPU0 attaching NULL sched-domain.
[   16.939552] CPU1 attaching NULL sched-domain.
[   16.952096] CPU0 attaching sched-domain:
[   16.952101]  domain 0: span 0-1 level MC
[   16.952104]   groups: 0 1
[   16.952110] CPU1 attaching sched-domain:
[   16.952112]  domain 0: span 0-1 level MC
[   16.952115]   groups: 1 0
[   17.616439] tda1004x: setting up plls for 48MHz sampling clock
[   17.932007] tda1004x: found firmware revision 29 -- ok
[   23.500006] eth0: no IPv6 routers present
[   38.536007] tda1004x: setting up plls for 48MHz sampling clock
[   38.820007] tda1004x: found firmware revision 29 -- ok
thedruz@Drubuntu:~$ 

I really should be able to do this I started with CP/M over 20 years ago & most of the bash commands are similar to *nix but I am stumped [ in CP/M I'd use the pip command [peripheral interchange program] I wish linux had something like it]

---

### Post by thedruz on 2010-03-31
Here's the output of lshw Just in case it's of any help

 *-multimedia            
       description: Audio device
       product: MCP73 High Definition Audio
       vendor: nVidia Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:7 memory:fce78000-fce7bfff
  *-multimedia
       description: Multimedia controller
       product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 6
       bus info: pci@0000:01:06.0
       version: d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=255 mingnt=255
       resources: irq:11 memory:fcfff000-fcfff7ff
  *-multimedia UNCLAIMED
       description: Audio device
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:feb7c000-feb7ffff

As can be seen The card is there, but still can't seem to get it to tune anything in

---

### Post by wbee on 2010-03-31
Please see "Loving Linux's:" reply in this post:

[http://ubuntuforums.org/showthread.php?t=1091604](http://ubuntuforums.org/showthread.php?t=1091604)

Now,the bear will be to get your sound to work. If you want to physically connect a cable from the sound output of the card to the input of your sound card,that will work.

But let me tell you something it took me forever to figure out.

--Sound on most sound cards is 44.1. The sound from the MSI TV Anywhere card is less than that. I think it's 33.?

--Anyhow,if you want to try to get it to work without attaching a cable,Google>Pulse Audio>I Feel Lucky>(The Site)>FAQ.......there,you will find a shell command to have pulse do the conversion to 44.1.

Good luck to you;it is a frustrating card(for me) with Ubuntu------though it works better with KK than previous Ubuntu systems.

---

### Post by thedruz on 2010-03-31
Thanks for that I hope it will be useful Once I can get the stupid card to actually tune in anything, this is becoming a real pain 11 hours of trolling through search results trying to get this damn thing to tune in stations, I know it works because under Windows it works perfectly & picks up all local stations, I really want to make the switch over to Linux but if it is going to be this difficult....ARRGHHH!!!!!! [anguished cry of geek frustration]

---

