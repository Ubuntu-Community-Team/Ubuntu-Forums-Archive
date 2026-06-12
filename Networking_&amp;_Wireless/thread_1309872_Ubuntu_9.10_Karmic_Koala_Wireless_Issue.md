---
title: "Ubuntu 9.10 Karmic Koala Wireless Issue"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by Feareilo on 2009-11-01
I was running Jaunty Jackalope, connecting to the internet with the WICD client. I upgraded, *over the internet* to Ubuntu 9.10.
Now, I can't use wireless.

I need help please. Do you need me to post the results of some commands?

How do I completely remove anything wireless related?

I used to connect manually in Hardy Heron but since Jaunty Jackalope I couldn't. I started using WICD because whenever I tried to connect manually the way I always used to I'd get "No DHCPOffers received".

I'm getting the exact same thing now. I think it has to do with some Network Manager and WICD leftovers...

---

### Post by rastro123 on 2009-11-01
Have a look here: [http://ubuntuforums.org/showthread.php?t=1304978](http://ubuntuforums.org/showthread.php?t=1304978) 
maybe something will help. Me, Im gonna stay with 9.4 after trying to upgrade twice and being left with no connection with wireless. I'll wait till ubuntu get their act together - hopefully with with the next one after 9.10

---

### Post by Feareilo on 2009-11-02
That didn't help. Thank you anyway.
I'm posting the results of dmesg, ifconfig and iwconfig:

dmesg:
> ```
amosupremo@amosupremo:~$ dmesg

[    0.093441] pci 0000:02:09.0: PME# supported from D0 D2 D3hot D3cold
[    0.093449] pci 0000:02:09.0: PME# disabled
[    0.093492] pci 0000:00:1e.0: transparent bridge
[    0.093501] pci 0000:00:1e.0: bridge io port: [0x1000-0x1fff]
[    0.093510] pci 0000:00:1e.0: bridge 32bit mmio: [0xfd000000-0xfd2fffff]
[    0.093532] pci_bus 0000:00: on NUMA node 0
[    0.093542] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.093695] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    0.097596] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.097741] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.097876] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.098019] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.098154] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.098287] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.098423] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.098559] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.098993] SCSI subsystem initialized
[    0.099176] libata version 3.00 loaded.
[    0.099369] usbcore: registered new interface driver usbfs
[    0.099413] usbcore: registered new interface driver hub
[    0.099477] usbcore: registered new device driver usb
[    0.099825] ACPI: WMI: Mapper loaded
[    0.099832] PCI: Using ACPI for IRQ routing
[    0.100175] Bluetooth: Core ver 2.15
[    0.100299] NET: Registered protocol family 31
[    0.100303] Bluetooth: HCI device and connection manager initialized
[    0.100311] Bluetooth: HCI socket layer initialized
[    0.100316] NetLabel: Initializing
[    0.100321] NetLabel:  domain hash size = 128
[    0.100325] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.100357] NetLabel:  unlabeled traffic allowed by default
[    0.104430] pnp: PnP ACPI init
[    0.104490] ACPI: bus type pnp registered
[    0.108185] pnp 00:0d: io resource (0xf800-0xf81f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling
[    0.108195] pnp 00:0d: io resource (0xf820-0xf83f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling
[    0.108203] pnp 00:0d: io resource (0xf840-0xf85f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling
[    0.108211] pnp 00:0d: io resource (0xf860-0xf87f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling
[    0.108928] pnp: PnP ACPI: found 15 devices
[    0.108934] ACPI: ACPI bus type pnp unregistered
[    0.108942] PnPBIOS: Disabled by ACPI PNP
[    0.108978] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.108991] system 00:0d: ioport range 0x400-0x41f has been reserved
[    0.108998] system 00:0d: ioport range 0x420-0x43f has been reserved
[    0.109005] system 00:0d: ioport range 0x440-0x45f has been reserved
[    0.109012] system 00:0d: ioport range 0x460-0x47f has been reserved
[    0.109020] system 00:0d: ioport range 0xfa00-0xfa3f has been reserved
[    0.109028] system 00:0d: ioport range 0xfc00-0xfc7f has been reserved
[    0.109035] system 00:0d: ioport range 0xfc80-0xfcff has been reserved
[    0.109042] system 00:0d: ioport range 0xfe00-0xfe7f has been reserved
[    0.109049] system 00:0d: ioport range 0xfe80-0xfeff has been reserved
[    0.109063] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.109071] system 00:0e: iomem range 0xe8000-0xfffff could not be reserved
[    0.109078] system 00:0e: iomem range 0x100000-0x200fffff could not be reserved
[    0.109086] system 00:0e: iomem range 0xfff80000-0xffffffff has been reserved
[    0.109093] system 00:0e: iomem range 0xfeea0000-0xfeebffff has been reserved
[    0.109101] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.109108] system 00:0e: iomem range 0xcc800-0xcffff has been reserved
[    0.109115] system 00:0e: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.143985] AppArmor: AppArmor Filesystem Enabled
[    0.144038] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xf8000000-0xf7ffffff]
[    0.144046] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.144051] pci 0000:00:01.0:   IO window: disabled
[    0.144061] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfcffffff
[    0.144069] pci 0000:00:01.0:   PREFETCH window: 0xf0000000-0xf7ffffff
[    0.144078] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.144085] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.144095] pci 0000:00:1e.0:   MEM window: 0xfd000000-0xfd2fffff
[    0.144103] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.144132] pci 0000:00:1e.0: setting latency timer to 64
[    0.144141] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.144148] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.144155] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfcffffff]
[    0.144162] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]
[    0.144169] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.144175] pci_bus 0000:02: resource 1 mem: [0xfd000000-0xfd2fffff]
[    0.144182] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.144189] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.144276] NET: Registered protocol family 2
[    0.144467] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.144997] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.145189] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.145405] TCP: Hash tables configured (established 16384 bind 16384)
[    0.145413] TCP reno registered
[    0.145733] NET: Registered protocol family 1
[    0.145909] Trying to unpack rootfs image as initramfs...
[    0.537722] Freeing initrd memory: 7456k freed
[    0.558807] cpufreq-nforce2: No nForce2 chipset.
[    0.558874] Scanning for low memory corruption every 60 seconds
[    0.559130] audit: initializing netlink socket (disabled)
[    0.559185] type=2000 audit(1257171146.555:1): initialized
[    0.571868] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.574639] VFS: Disk quotas dquot_6.5.2
[    0.574784] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.576029] fuse init (API version 7.12)
[    0.576238] msgmni has been set to 993
[    0.576816] alg: No test for stdrng (krng)
[    0.576853] io scheduler noop registered
[    0.576859] io scheduler anticipatory registered
[    0.576865] io scheduler deadline registered
[    0.577005] io scheduler cfq registered (default)
[    0.577093] pci 0000:01:00.0: Boot video device
[    0.577136] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    0.577343] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.577397] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.577635] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.577645] ACPI: Power Button [PWRF]
[    0.577761] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.577772] ACPI: Power Button [PBTN]
[    0.578086] processor LNXCPU:00: registered as cooling_device0
[    0.578095] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.580410] isapnp: Scanning for PnP cards...
[    0.643951] Switched to high resolution mode on CPU 0
[    0.934902] isapnp: No Plug & Play device found
[    0.937411] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.937594] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.937733] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.938271] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.938458] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.938694]   alloc irq_desc for 18 on node -1
[    0.938700]   alloc kstat_irqs on node -1
[    0.938718] serial 0000:02:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.941354] brd: module loaded
[    0.942310] loop: module loaded
[    0.942533] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.942793] ata_piix 0000:00:1f.1: version 2.13
[    0.942935] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.943179] scsi0 : ata_piix
[    0.943430] scsi1 : ata_piix
[    0.943862] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2480 irq 14
[    0.943870] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2488 irq 15
[    0.945617] Fixed MDIO Bus: probed
[    0.945702] PPP generic driver version 2.4.2
[    0.945958] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.946015] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.946044] uhci_hcd: USB Universal Host Controller Interface driver
[    0.946160]   alloc irq_desc for 19 on node -1
[    0.946166]   alloc kstat_irqs on node -1
[    0.946183] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.946201] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    0.946210] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    0.946377] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    0.946440] uhci_hcd 0000:00:1f.2: irq 19, io base 0x00002440
[    0.946661] usb usb1: configuration #1 chosen from 1 choice
[    0.946727] hub 1-0:1.0: USB hub found
[    0.946751] hub 1-0:1.0: 2 ports detected
[    0.946872]   alloc irq_desc for 23 on node -1
[    0.946878]   alloc kstat_irqs on node -1
[    0.946894] uhci_hcd 0000:00:1f.4: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    0.946910] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    0.946918] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    0.947013] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    0.947065] uhci_hcd 0000:00:1f.4: irq 23, io base 0x00002460
[    0.947249] usb usb2: configuration #1 chosen from 1 choice
[    0.947310] hub 2-0:1.0: USB hub found
[    0.947335] hub 2-0:1.0: 2 ports detected
[    0.947571] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[    0.950591] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.950607] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.950823] mice: PS/2 mouse device common for all mice
[    0.951019] rtc_cmos 00:03: RTC can wake from S4
[    0.951112] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.951149] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.951396] device-mapper: uevent: version 1.0.3
[    0.951680] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.951910] device-mapper: multipath: version 1.1.0 loaded
[    0.951919] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.952315] EISA: Probing bus 0 at eisa.0
[    0.952332] Cannot allocate resource for EISA slot 1
[    0.952338] Cannot allocate resource for EISA slot 2
[    0.952368] EISA: Detected 0 cards.
[    0.952509] cpuidle: using governor ladder
[    0.952515] cpuidle: using governor menu
[    0.953563] TCP cubic registered
[    0.953826] NET: Registered protocol family 10
[    0.954638] lo: Disabled Privacy Extensions
[    0.955239] NET: Registered protocol family 17
[    0.955311] Bluetooth: L2CAP ver 2.13
[    0.955355] Bluetooth: L2CAP socket layer initialized
[    0.955391] Bluetooth: SCO (Voice Link) ver 0.6
[    0.955395] Bluetooth: SCO socket layer initialized
[    0.955509] Bluetooth: RFCOMM TTY layer initialized
[    0.955515] Bluetooth: RFCOMM socket layer initialized
[    0.955519] Bluetooth: RFCOMM ver 1.11
[    0.955609] Using IPI No-Shortcut mode
[    0.955819] PM: Resume from disk failed.
[    0.955850] registered taskstats version 1
[    0.956101]   Magic number: 1:831:231
[    0.956233] rtc_cmos 00:03: setting system clock to 2009-11-02 14:12:27 UTC (1257171147)
[    0.956241] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.956245] EDD information not available.
[    0.975146] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.113008] ata1.00: ATA-6: Maxtor 4D080H4, DAH017K0, max UDMA/100
[    1.113016] ata1.00: 156301488 sectors, multi 16: LBA 
[    1.120486] ata2.00: ATAPI: LTN486S, YQS8, max MWDMA2, CDB intr
[    1.120545] ata2.01: ATAPI: PIONEER DVD-RW  DVR-103, 1.55, max MWDMA2
[    1.128659] ata1.00: configured for UDMA/100
[    1.128941] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 4D080H4   DAH0 PQ: 0 ANSI: 5
[    1.129243] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.129372] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.129474] sd 0:0:0:0: [sda] Write Protect is off
[    1.129481] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.129532] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.129837]  sda:
[    1.136278] ata2.00: configured for MWDMA2
[    1.143348]  sda1 sda2 <
[    1.152265] ata2.01: configured for MWDMA2
[    1.159565] scsi 1:0:0:0: CD-ROM            COMPAQ   CD-ROM LTN486S   YQS8 PQ: 0 ANSI: 5
[    1.160705]  sda5sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.162285] Uniform CD-ROM driver Revision: 3.20
[    1.162518] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.162647] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.166084] scsi 1:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-103  1.55 PQ: 0 ANSI: 5
[    1.179763]  sda6 sda7sr1: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.189372] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.189504] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.193784]  sda8 >
[    1.194584] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.194624] Freeing unused kernel memory: 540k freed
[    1.196183] Write protecting the kernel text: 4568k
[    1.196241] Write protecting the kernel read-only data: 1836k
[    1.260096] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    1.454854] usb 1-1: configuration #1 chosen from 1 choice
[    1.596633] Floppy drive(s): fd0 is 1.44M
[    1.639087] FDC 0 is a post-1991 82077
[    1.641802] Linux agpgart interface v0.103
[    1.673183] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[    1.677268] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    1.940567]   alloc irq_desc for 16 on node -1
[    1.940575]   alloc kstat_irqs on node -1
[    1.940592] ohci1394 0000:02:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.950577] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.950585] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.960873] usbcore: registered new interface driver hiddev
[    1.981941] input: Compaq Compaq Internet Keyboard as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.0/input/input4
[    1.982146] generic-usb 0003:049F:000E.0001: input,hidraw0: USB HID v1.00 Keyboard [Compaq Compaq Internet Keyboard] on usb-0000:00:1f.2-1/input0
[    1.997129] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[fd205000-fd2057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.001808]   alloc irq_desc for 20 on node -1
[    2.001816]   alloc kstat_irqs on node -1
[    2.001834] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.092188] e100 0000:02:08.0: PME# disabled
[    2.126965] e100: eth0: e100_probe: addr 0xfd204000, irq 20, MAC addr 00:02:a5:f1:4a:3c
[    2.129415] input: Compaq Compaq Internet Keyboard as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.1/input/input5
[    2.129669] generic-usb 0003:049F:000E.0002: input,hiddev96,hidraw1: USB HID v1.00 Device [Compaq Compaq Internet Keyboard] on usb-0000:00:1f.2-1/input1
[    2.129713] usbcore: registered new interface driver usbhid
[    2.129721] usbhid: v2.6:USB HID core driver
[    3.276369] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010b50000037341]
[    3.644346] PM: Starting manual resume from disk
[    3.644358] PM: Resume from partition 8:8
[    3.644362] PM: Checking hibernation image.
[    3.644743] PM: Resume from disk failed.
[    3.664156] EXT4-fs (sda7): barriers enabled
[    3.677537] kjournald2 starting: pid 321, dev sda7:8, commit interval 5 seconds
[    3.677587] EXT4-fs (sda7): delayed allocation enabled
[    3.677595] EXT4-fs: file extents enabled
[    3.682118] EXT4-fs: mballoc enabled
[    3.682150] EXT4-fs (sda7): mounted filesystem with ordered data mode
[    4.684756] type=1505 audit(1257171151.227:2): operation="profile_load" pid=344 name=/usr/share/gdm/guest-session/Xsession
[    4.983918] type=1505 audit(1257171151.523:3): operation="profile_load" pid=345 name=/sbin/dhclient3
[    4.984394] type=1505 audit(1257171151.527:4): operation="profile_load" pid=345 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.984516] type=1505 audit(1257171151.527:5): operation="profile_load" pid=345 name=/usr/lib/connman/scripts/dhclient-script
[   20.919351] type=1505 audit(1257171167.459:6): operation="profile_load" pid=346 name=/usr/bin/evince
[   20.922036] type=1505 audit(1257171167.463:7): operation="profile_load" pid=346 name=/usr/bin/evince-previewer
[   20.924832] type=1505 audit(1257171167.467:8): operation="profile_load" pid=346 name=/usr/bin/evince-thumbnailer
[   21.498569] type=1505 audit(1257171168.039:9): operation="profile_load" pid=348 name=/usr/lib/cups/backend/cups-pdf
[   21.499041] type=1505 audit(1257171168.039:10): operation="profile_load" pid=348 name=/usr/sbin/cupsd
[   21.661623] type=1505 audit(1257171168.203:11): operation="profile_load" pid=349 name=/usr/sbin/tcpdump
[   22.672657] Adding 1028120k swap on /dev/sda8.  Priority:-1 extents:1 across:1028120k 
[   22.987771] EXT4-fs (sda7): internal journal on sda7:8
[   23.110540] udev: starting version 147
[   25.351446] lp: driver loaded but no devices found
[   25.560900] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.164267] psmouse serio1: ID: 00 00 3c
[   26.637732] parport_pc 00:07: reported by Plug and Play ACPI
[   26.637796] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   26.645285] intel_rng: Firmware space is locked read-only. If you can't or
[   26.645289] intel_rng: don't want to disable this in firmware setup, and if
[   26.645291] intel_rng: you are certain that your system has a functional
[   26.645294] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   26.724401] lp0: using parport0 (interrupt-driven).
[   26.761784] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.794991] ppdev: user-space parallel port driver
[   26.862721] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   28.728417]   alloc irq_desc for 17 on node -1
[   28.728427]   alloc kstat_irqs on node -1
[   28.728444] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   28.728483] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   29.292997] intel8x0: white list rate for 0e11:008a is 41000
[   30.091482] type=1505 audit(1257192776.631:12): operation="profile_replace" pid=723 name=/usr/share/gdm/guest-session/Xsession
[   30.401005] type=1505 audit(1257192776.943:13): operation="profile_replace" pid=798 name=/sbin/dhclient3
[   30.401504] type=1505 audit(1257192776.943:14): operation="profile_replace" pid=798 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   30.401777] type=1505 audit(1257192776.943:15): operation="profile_replace" pid=798 name=/usr/lib/connman/scripts/dhclient-script
[   34.353890] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.276328] type=1505 audit(1257192798.819:16): operation="profile_replace" pid=799 name=/usr/bin/evince
[   52.287170] type=1505 audit(1257192798.827:17): operation="profile_replace" pid=799 name=/usr/bin/evince-previewer
[   52.291175] type=1505 audit(1257192798.831:18): operation="profile_replace" pid=799 name=/usr/bin/evince-thumbnailer
[   53.175266] type=1505 audit(1257192799.715:19): operation="profile_replace" pid=1120 name=/usr/lib/cups/backend/cups-pdf
[   53.176170] type=1505 audit(1257192799.719:20): operation="profile_replace" pid=1120 name=/usr/sbin/cupsd
[   53.526640] type=1505 audit(1257192800.067:21): operation="profile_replace" pid=1124 name=/usr/sbin/tcpdump
[  510.504038] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  510.654179] usb 2-1: configuration #1 chosen from 1 choice
[  510.733483] cfg80211: Calling CRDA to update world regulatory domain
[  510.789331] cfg80211: World regulatory domain updated:
[  510.789342] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  510.789350] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  510.789356] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  510.789363] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  510.789369] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  510.789376] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  510.901309] Atmel at76x USB Wireless LAN Driver 0.17 loading
[  510.901368] usb 2-1: firmware: requesting atmel_at76c505a-rfmd2958.bin
[  510.980840] usb 2-1: using firmware atmel_at76c505a-rfmd2958.bin (version 1.102.0-113)
[  510.983410] at76c50x-usb 2-1:1.0: downloading internal firmware
[  515.240028] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[  515.384581] usb 2-1: device firmware changed
[  515.384695] usbcore: registered new interface driver at76c50x-usb
[  515.386008] usb 2-1: USB disconnect, address 2
[  515.409591] at76_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  515.419137] Atmel at76x USB Wireless LAN Driver 0.17 loading
[  515.419236] usbcore: registered new interface driver at76_usb
[  515.419249] LED trigger at76_usb-tx failed to register (-17)
[  515.496053] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  515.645735] usb 2-1: configuration #1 chosen from 1 choice
[  515.661146] at76c50x-usb 2-1:1.0: downloading external firmware
[  516.065520] phy0: Selected rate control algorithm 'minstrel'
[  516.066879] phy0: USB 2-1:1.0, MAC 00:04:e2:b0:a6:ba, firmware 1.102.0-113
[  516.066887] phy0: regulatory domain 0x10: FCC (USA)
[  516.896234] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  541.641088] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  541.840056] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  542.040058] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  542.240617] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  543.214638] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  543.412097] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  543.612060] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  543.812062] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  554.636587] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  554.840147] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  555.044116] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  555.244041] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  566.310775] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  566.508041] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  566.708041] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  566.908039] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  577.815621] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  578.012404] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  578.212282] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  578.412106] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  583.430624] wlan0: direct probe to AP 00:0f:66:30:6b:7d try 1
[  583.628061] wlan0: direct probe to AP 00:0f:66:30:6b:7d try 2
[  583.828105] wlan0: direct probe to AP 00:0f:66:30:6b:7d try 3
[  584.028058] wlan0: direct probe to AP 00:0f:66:30:6b:7d timed out
[  589.062755] wlan0: direct probe to AP 00:0f:66:30:6b:7d try 1
[  589.260059] wlan0: direct probe to AP 00:0f:66:30:6b:7d try 2
[  589.460054] wlan0: direct probe to AP 00:0f:66:30:6b:7d try 3
[  589.660037] wlan0: direct probe to AP 00:0f:66:30:6b:7d timed out
[  600.451734] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  600.652112] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  600.854983] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  601.052107] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  611.650112] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  611.848052] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  612.048052] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  612.248045] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  623.021308] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  623.220049] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  623.420046] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  623.620047] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  634.406668] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  634.612131] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  634.812030] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  635.012038] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  645.798368] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  645.996034] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  646.196032] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  646.396032] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  657.186133] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  657.384058] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  657.584055] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  657.784051] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  668.575027] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  668.772801] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  668.972049] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  669.172049] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  679.982606] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  680.180032] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  680.380031] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  680.580030] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  691.370355] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  691.568033] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  691.768029] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  691.968029] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  693.214809] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  693.412043] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  693.612032] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  693.812030] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  704.626572] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  704.824106] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  705.024037] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  705.224033] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  716.018319] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  716.216035] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  716.416219] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  716.616044] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  721.661713] wlan0: direct probe to AP 00:0f:66:30:6b:7d try 1
[  721.860041] wlan0: direct probe to AP 00:0f:66:30:6b:7d try 2
[  722.060035] wlan0: direct probe to AP 00:0f:66:30:6b:7d try 3
[  722.260055] wlan0: direct probe to AP 00:0f:66:30:6b:7d timed out
[  733.070447] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  733.268036] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  733.468034] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  733.668028] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  744.478981] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  744.676057] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  744.876050] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  745.076037] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  753.299757] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  756.110930] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  756.308928] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  756.508030] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  756.708029] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  767.523113] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  767.720056] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  767.920053] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  768.120042] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  778.890369] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  779.088032] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  779.288031] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  779.488031] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  790.283320] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  790.480097] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  790.680057] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  790.880058] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  801.674878] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  801.872049] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  802.072044] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  802.272056] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  813.058635] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  813.256037] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  813.456033] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  813.656032] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  824.447703] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  824.644029] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  824.844030] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  825.044048] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  835.835153] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  836.032062] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  836.232058] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  836.433027] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
[  847.262893] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  847.460050] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  847.660037] wlan0: authenticate with AP 00:0f:66:30:6b:7d
[  847.860035] wlan0: authentication with AP 00:0f:66:30:6b:7d timed out
```

> ```
amosupremo@amosupremo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

> ```
amosupremo@amosupremo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:a5:f1:4a:3c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:04:e2:b0:a6:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-04-E2-B0-A6-BA-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Feareilo on 2009-11-03
C'mon guys... I'm having a major headache over this problem. I've always had a lot of trouble over wireless connections whenever I upgrade Ubuntu. I normally solve it but this time I'm nowhere near solving it. I'm in desperate need of help. Please help me!

---

### Post by Feareilo on 2009-11-03
Ok, I guess I'm gonna give up.

---

### Post by iliketv01 on 2009-11-03
I feel your pain man, I'm new to linux and I'm trying to give it a shot but this wireless thing has left me jaded. The thing is my only access to the internet is through a wireless connection, without it I can't really do much. I think I'm just going to install the 9.04 version until someone comes up with a good fix for this wireless problem.

---

### Post by Feareilo on 2009-11-03
> **iliketv01 said:**
> I feel your pain man, I'm new to linux and I'm trying to give it a shot but this wireless thing has left me jaded. The thing is my only access to the internet is through a wireless connection, without it I can't really do much. I think I'm just going to install the 9.04 version until someone comes up with a good fix for this wireless problem.

Yeah, wireless-only for me too.

By the way, be careful with 9.04. I had trouble with it too. I had to get WICD instead of Network Manager.

---

### Post by Feareilo on 2009-11-03
Read last post. I was a dumbass.

---

### Post by Feareilo on 2009-11-04
Issue solved in this thread:

[http://ubuntuforums.org/showthread.php?t=1280956](http://ubuntuforums.org/showthread.php?t=1280956)

> **claudio70b said:**
> Ah, still both included. Yep, now you use the "more or less old" driver again. ;-)

So one can run **gksudo gedit /etc/modprobe.d/blacklist.conf** and add the line **blacklist at76c50x_usb** to the file, run **sudo depmod -aeq** to get it working again.

So I wonder why the new driver (at76c50x_usb) doesn't work (yet; for you?) and what they will change in the next releases.

---

