---
title: "Ubuntu will not connect to ethernet"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by AADude on 2010-05-25
Recently I have installed Windows XP and Ubuntu 10.04 on my other computer. Although Ubuntu detects eth0, the connection always fails (eth0 is enabled but a resolv.conf is not found). When I plugged the ethernet cable into my laptop, it connected immediately (using Xubuntu 10.04). Not sure how to go about resolving this issue, as nothing seems to be wrong (other than the obvious fact that I cannot connect).

---

### Post by SlidingHorn on 2010-05-25
Need more info to help: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by AADude on 2010-05-25
Not a wireless issue, but I did most of what the post asked for:

lspci:
```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

lsusb:
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:0024 Microsoft Corp. Trackball Explorer
Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 001 Device 006: ID 10df:0500 In-Win Development, Inc. iAPP CR-e500 Card reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:50:8d:53:3b:70  
          inet6 addr: fe80::250:8dff:fe53:3b70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14888 (14.8 KB)  TX bytes:14888 (14.8 KB)

```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

dmesg:
```

[    0.388227] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.388232] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.388237] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xf9ffffff]
[    0.388243] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xefffffff]
[    0.388249] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.388255] pci_bus 0000:02: resource 1 mem: [0xfa000000-0xfbffffff]
[    0.388260] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x200fffff]
[    0.388265] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.388270] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.388340] NET: Registered protocol family 2
[    0.388536] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.389108] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.389188] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.389264] TCP: Hash tables configured (established 16384 bind 16384)
[    0.389269] TCP reno registered
[    0.389424] NET: Registered protocol family 1
[    0.389568] pci 0000:01:00.0: Boot video device
[    0.389784] cpufreq-nforce2: No nForce2 chipset.
[    0.389842] Scanning for low memory corruption every 60 seconds
[    0.390067] audit: initializing netlink socket (disabled)
[    0.390084] type=2000 audit(1274789162.387:1): initialized
[    0.401164] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.404461] VFS: Disk quotas dquot_6.5.2
[    0.404594] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.405865] fuse init (API version 7.13)
[    0.406063] msgmni has been set to 977
[    0.406519] alg: No test for stdrng (krng)
[    0.406643] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.406649] io scheduler noop registered
[    0.406653] io scheduler anticipatory registered
[    0.406657] io scheduler deadline registered
[    0.406743] io scheduler cfq registered (default)
[    0.406975] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.407026] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.407209] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.407217] ACPI: Power Button [PWRB]
[    0.407334] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.407341] ACPI: Power Button [PWRF]
[    0.463078] Freeing initrd memory: 7776k freed
[    0.607717] fan PNP0C0B:00: registered as cooling_device0
[    0.607730] ACPI: Fan [FAN] (off)
[    0.608017] processor LNXCPU:00: registered as cooling_device1
[    0.608074] processor LNXCPU:01: registered as cooling_device2
[    0.907728] thermal LNXTHERM:01: registered as thermal_zone0
[    0.907741] ACPI: Thermal Zone [THRM] (52 C)
[    0.907870] isapnp: Scanning for PnP cards...
[    0.910438] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.910544] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.911036] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.913090] brd: module loaded
[    0.914013] loop: module loaded
[    0.914176] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.914341] ata_piix 0000:00:1f.1: version 2.13
[    0.914361]   alloc irq_desc for 18 on node -1
[    0.914365]   alloc kstat_irqs on node -1
[    0.914374] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.914432] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.914569] scsi0 : ata_piix
[    0.914704] scsi1 : ata_piix
[    0.916001] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.916006] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.916042] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.916049] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.916103] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.916185] scsi2 : ata_piix
[    0.916287] scsi3 : ata_piix
[    0.917176] ata3: SATA max UDMA/133 cmd 0xc000 ctl 0xc400 bmdma 0xd000 irq 18
[    0.917181] ata4: SATA max UDMA/133 cmd 0xc800 ctl 0xcc00 bmdma 0xd008 irq 18
[    0.917855] Fixed MDIO Bus: probed
[    0.917923] PPP generic driver version 2.4.2
[    0.918014] tun: Universal TUN/TAP device driver, 1.6
[    0.918018] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.918176] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.918208]   alloc irq_desc for 23 on node -1
[    0.918212]   alloc kstat_irqs on node -1
[    0.918221] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.918240] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.918246] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.918315] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.918352] ehci_hcd 0000:00:1d.7: debug port 1
[    0.922245] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.922267] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc000000
[    0.935655] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.935840] usb usb1: configuration #1 chosen from 1 choice
[    0.935891] hub 1-0:1.0: USB hub found
[    0.935905] hub 1-0:1.0: 8 ports detected
[    0.936020] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.936050] uhci_hcd: USB Universal Host Controller Interface driver
[    0.936105]   alloc irq_desc for 16 on node -1
[    0.936108]   alloc kstat_irqs on node -1
[    0.936117] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.936129] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.936135] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.936201] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.936240] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bc00
[    0.936391] usb usb2: configuration #1 chosen from 1 choice
[    0.936439] hub 2-0:1.0: USB hub found
[    0.936450] hub 2-0:1.0: 2 ports detected
[    0.936526]   alloc irq_desc for 19 on node -1
[    0.936530]   alloc kstat_irqs on node -1
[    0.936537] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.936546] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.936551] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.936612] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.936649] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b000
[    0.936799] usb usb3: configuration #1 chosen from 1 choice
[    0.936846] hub 3-0:1.0: USB hub found
[    0.936858] hub 3-0:1.0: 2 ports detected
[    0.936937] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.936947] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.936951] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.937010] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.937035] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[    0.937197] usb usb4: configuration #1 chosen from 1 choice
[    0.937245] hub 4-0:1.0: USB hub found
[    0.937256] hub 4-0:1.0: 2 ports detected
[    0.937334] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.937343] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.937348] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.937407] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.937432] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b800
[    0.937585] usb usb5: configuration #1 chosen from 1 choice
[    0.937633] hub 5-0:1.0: USB hub found
[    0.937644] hub 5-0:1.0: 2 ports detected
[    0.937805] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.937809] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.938535] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.938737] mice: PS/2 mouse device common for all mice
[    0.938923] rtc_cmos 00:03: RTC can wake from S4
[    0.938989] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.939016] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.939205] device-mapper: uevent: version 1.0.3
[    0.939385] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.939495] device-mapper: multipath: version 1.1.0 loaded
[    0.939500] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.939716] EISA: Probing bus 0 at eisa.0
[    0.939761] EISA: Detected 0 cards.
[    0.939892] cpuidle: using governor ladder
[    0.939896] cpuidle: using governor menu
[    0.940714] TCP cubic registered
[    0.940943] NET: Registered protocol family 10
[    0.941810] lo: Disabled Privacy Extensions
[    0.942504] NET: Registered protocol family 17
[    0.942582] Using IPI No-Shortcut mode
[    0.942722] PM: Resume from disk failed.
[    0.942749] registered taskstats version 1
[    0.943062]   Magic number: 10:209:128
[    0.943127] acpi device:03: hash matches
[    0.943135] acpi PNP0C02:00: hash matches
[    0.943167] rtc_cmos 00:03: setting system clock to 2010-05-25 12:06:03 UTC (1274789163)
[    0.943172] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.943175] EDD information not available.
[    0.959898] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.102416] ata2.00: ATAPI: IDE DVD-ROM 16X, VER 2.50, max UDMA/33
[    1.102466] ata2.01: ATAPI: _NEC DVD_RW ND-1300A, 1.07, max UDMA/33
[    1.102607] ata1.00: ATA-7: Maxtor 6Y120L0, YAR41BW0, max UDMA/133
[    1.102612] ata1.00: 240121728 sectors, multi 16: LBA 
[    1.107970] ata2.00: configured for UDMA/33
[    1.116097] ata1.00: configured for UDMA/100
[    1.123904] ata2.01: configured for UDMA/33
[    1.261624] isapnp: No Plug & Play device found
[    1.261781] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y120L0   YAR4 PQ: 0 ANSI: 5
[    1.261993] sd 0:0:0:0: [sda] 240121728 512-byte logical blocks: (122 GB/114 GiB)
[    1.262040] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.262098] sd 0:0:0:0: [sda] Write Protect is off
[    1.262105] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.262169] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.262451]  sda:
[    1.262459] scsi 1:0:0:0: CD-ROM            IDE      DVD-ROM 16X      2.50 PQ: 0 ANSI: 5
[    1.264163] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[    1.264169] Uniform CD-ROM driver Revision: 3.20
[    1.264302] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.264386] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.267530] scsi 1:0:1:0: CD-ROM            _NEC     DVD_RW ND-1300A  1.07 PQ: 0 ANSI: 5
[    1.271935] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.272078] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.272150] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.307112]  sda1 sda2 < sda5 sda6 >
[    1.363544] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.363571] Freeing unused kernel memory: 656k freed
[    1.364222] Write protecting the kernel text: 4676k
[    1.364290] Write protecting the kernel read-only data: 1840k
[    1.368043] usb 1-3: new high speed USB device using ehci_hcd and address 4
[    1.391843] udev: starting version 151
[    1.492080] usb 1-3: device descriptor read/64, error -71
[    1.561258] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.561304] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.601747] 8139too Fast Ethernet driver 0.9.28
[    1.601813] 8139too 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.603576] eth0: RealTek RTL8139 at 0xa000, 00:50:8d:53:3b:70, IRQ 18
[    1.621844] Floppy drive(s): fd0 is 1.44M
[    1.639783] FDC 0 is a post-1991 82077
[    1.772824] usb 1-3: configuration #1 chosen from 1 choice
[    1.783285] Initializing USB Mass Storage driver...
[    1.783455] scsi4 : SCSI emulation for USB Mass Storage devices
[    1.783681] usb-storage: device found at 4
[    1.783686] usb-storage: waiting for device to settle before scanning
[    1.783707] usbcore: registered new interface driver usb-storage
[    1.783840] USB Mass Storage support registered.
[    2.012023] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    2.208411] usb 2-1: configuration #1 chosen from 1 choice
[    2.226729] usbcore: registered new interface driver hiddev
[    2.303078] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    2.448048] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    2.623408] usb 2-2: configuration #1 chosen from 1 choice
[    2.627401] generic-usb 0003:051D:0002.0001: hiddev96,hidraw0: USB HID v1.10 Device [APC Back-UPS ES 650 FW:818.w1.D USB FW:w1] on usb-0000:00:1d.0-1/input0
[    2.642591] input: Microsoft Microsoft Trackball Explorer® as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
[    2.642729] generic-usb 0003:045E:0024.0002: input,hidraw1: USB HID v1.00 Mouse [Microsoft Microsoft Trackball Explorer®] on usb-0000:00:1d.0-2/input0
[    2.642765] usbcore: registered new interface driver usbhid
[    2.642769] usbhid: v2.6:USB HID core driver
[    6.785363] usb-storage: device scan complete
[    6.788328] scsi 4:0:0:0: Direct-Access     IN-WIN   iAPP  HS-CF      1.63 PQ: 0 ANSI: 0
[    6.790693] scsi 4:0:0:1: Direct-Access     IN-WIN   iAPP  HS-MS      1.63 PQ: 0 ANSI: 0
[    6.793316] scsi 4:0:0:2: Direct-Access     IN-WIN   iAPP  HS-SM      1.63 PQ: 0 ANSI: 0
[    6.795691] scsi 4:0:0:3: Direct-Access     IN-WIN   iAPP  HS-SD/MMC  1.63 PQ: 0 ANSI: 0
[    6.796369] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    6.796609] sd 4:0:0:1: Attached scsi generic sg4 type 0
[    6.796849] sd 4:0:0:2: Attached scsi generic sg5 type 0
[    6.797108] sd 4:0:0:3: Attached scsi generic sg6 type 0
[    6.854804] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    6.857801] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[    6.860801] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[    6.863549] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   10.213570] Adding 1489912k swap on /dev/sda6.  Priority:-1 extents:1 across:1489912k 
[   10.499508] udev: starting version 151
[   11.454916] type=1505 audit(1274803574.009:2):  operation="profile_load" pid=461 name="/sbin/dhclient3"
[   11.455649] type=1505 audit(1274803574.009:3):  operation="profile_load" pid=461 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.456133] type=1505 audit(1274803574.009:4):  operation="profile_load" pid=461 name="/usr/lib/connman/scripts/dhclient-script"
[   11.828040] lp: driver loaded but no devices found
[   12.089293] parport_pc 00:08: reported by Plug and Play ACPI
[   12.089352] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.176973] lp0: using parport0 (interrupt-driven).
[   12.229148] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.245168] ppdev: user-space parallel port driver
[   12.287639] intel_rng: FWH not detected
[   12.299623] Linux agpgart interface v0.103
[   12.454694] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   12.459284] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   12.571117] [drm] Initialized drm 1.1.0 20060810
[   13.450177] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   13.506288] [drm] radeon defaulting to kernel modesetting.
[   13.506294] [drm] radeon kernel modesetting enabled.
[   13.506367] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.509536] [drm] radeon: Initializing kernel modesetting.
[   13.509659] [drm] register mmio base: 0xF9000000
[   13.509663] [drm] register mmio size: 65536
[   13.509946] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   13.509973] [drm] Generation 2 PCI interface, using max accessible memory
[   13.509984] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   13.510010] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   13.510070] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[   13.510090] [drm] radeon: VRAM 256M
[   13.510095] [drm] radeon: VRAM from 0x00000000 to 0x0FFFFFFF
[   13.510099] [drm] radeon: GTT 128M
[   13.510102] [drm] radeon: GTT from 0xF0000000 to 0xF7FFFFFF
[   13.510138] [drm] radeon: irq initialized.
[   13.510301] [drm] Detected VRAM RAM=256M, BAR=256M
[   13.510307] [drm] RAM width 128bits DDR
[   13.510407] [TTM] Zone  kernel: Available graphics memory: 254584 kiB.
[   13.510431] [drm] radeon: 256M of VRAM memory ready
[   13.510436] [drm] radeon: 128M of GTT memory ready.
[   13.510682] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   13.510710] [drm] radeon: cp idle (0x10000C03)
[   13.510773] [drm] Loading R300 Microcode
[   13.510779] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   13.659473] [drm] radeon: ring at 0x00000000F0000000
[   13.659497] [drm] ring test succeeded in 1 usecs
[   13.665600] [drm] radeon: ib pool ready.
[   13.665746] [drm] ib test succeeded in 0 usecs
[   13.666398] [drm] Default TV standard: NTSC
[   13.666405] [drm] 27.000000000 MHz TV ref clk
[   13.666412] [drm] DFP table revision: 4
[   13.667246] [drm] Default TV standard: NTSC
[   13.667252] [drm] 27.000000000 MHz TV ref clk
[   13.667531] [drm] Radeon Display Connectors
[   13.667536] [drm] Connector 0:
[   13.667540] [drm]   VGA
[   13.667546] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   13.667550] [drm]   Encoders:
[   13.667554] [drm]     CRT1: INTERNAL_DAC1
[   13.667557] [drm] Connector 1:
[   13.667561] [drm]   DVI-I
[   13.667564] [drm]   HPD1
[   13.667569] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   13.667573] [drm]   Encoders:
[   13.667576] [drm]     CRT2: INTERNAL_DAC2
[   13.667579] [drm]     DFP1: INTERNAL_TMDS1
[   13.667583] [drm] Connector 2:
[   13.667586] [drm]   S-video
[   13.667589] [drm]   Encoders:
[   13.667592] [drm]     TV1: INTERNAL_DAC2
[   13.824946] [drm] fb mappable at 0xD0040000
[   13.824954] [drm] vram apper at 0xD0000000
[   13.824958] [drm] size 5242880
[   13.824962] [drm] fb depth is 24
[   13.824966] [drm]    pitch is 5120
[   13.826161] fb0: radeondrmfb frame buffer device
[   13.826167] registered panic notifier
[   13.826180] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   13.877149] vga16fb: initializing
[   13.877157] vga16fb: mapped to 0xc00a0000
[   13.877165] vga16fb: not registering due to another framebuffer present
[   14.127213]   alloc irq_desc for 17 on node -1
[   14.127218]   alloc kstat_irqs on node -1
[   14.127232] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.127345] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.247887] Console: switching to colour frame buffer device 160x64
[   14.449026] intel8x0_measure_ac97_clock: measured 52633 usecs (2536 samples)
[   14.449031] intel8x0: clocking to 48000
[   14.614859] type=1505 audit(1274803577.169:5):  operation="profile_load" pid=807 name="/usr/share/gdm/guest-session/Xsession"
[   14.617501] type=1505 audit(1274803577.173:6):  operation="profile_replace" pid=813 name="/sbin/dhclient3"
[   14.618052] type=1505 audit(1274803577.173:7):  operation="profile_replace" pid=813 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.618362] type=1505 audit(1274803577.173:8):  operation="profile_replace" pid=813 name="/usr/lib/connman/scripts/dhclient-script"
[   14.706392] type=1505 audit(1274803577.261:9):  operation="profile_load" pid=814 name="/usr/bin/evince"
[   14.713783] type=1505 audit(1274803577.268:10):  operation="profile_load" pid=814 name="/usr/bin/evince-previewer"
[   14.718344] type=1505 audit(1274803577.272:11):  operation="profile_load" pid=814 name="/usr/bin/evince-thumbnailer"
[   18.001870] CPU0 attaching NULL sched-domain.
[   18.001879] CPU1 attaching NULL sched-domain.
[   18.021132] CPU0 attaching sched-domain:
[   18.021139]  domain 0: span 0-1 level SIBLING
[   18.021145]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   18.021158]   domain 1: span 0-1 level MC
[   18.021164]    groups: 0-1 (cpu_power = 1178)
[   18.021176] CPU1 attaching sched-domain:
[   18.021180]  domain 0: span 0-1 level SIBLING
[   18.021186]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   18.021199]   domain 1: span 0-1 level MC
[   18.021205]    groups: 0-1 (cpu_power = 1178)
[   20.623059] CPU0 attaching NULL sched-domain.
[   20.623070] CPU1 attaching NULL sched-domain.
[   20.649094] CPU0 attaching sched-domain:
[   20.649100]  domain 0: span 0-1 level SIBLING
[   20.649104]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   20.649114]   domain 1: span 0-1 level MC
[   20.649118]    groups: 0-1 (cpu_power = 1178)
[   20.649127] CPU1 attaching sched-domain:
[   20.649130]  domain 0: span 0-1 level SIBLING
[   20.649134]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   20.649143]   domain 1: span 0-1 level MC
[   20.649147]    groups: 0-1 (cpu_power = 1178)
[   21.948063] end_request: I/O error, dev fd0, sector 0
[   22.012055] end_request: I/O error, dev fd0, sector 0
[   23.624024] eth0: no IPv6 routers present
[   25.816012] ------------[ cut here ]------------
[   25.816024] WARNING: at /build/buildd/linux-2.6.32/net/sched/sch_generic.c:261 dev_watchdog+0x1fe/0x210()
[   25.816028] Hardware name:  
[   25.816031] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out
[   25.816034] Modules linked in: binfmt_misc snd_intel8x0 fbcon tileblit snd_ac97_codec font ac97_bus snd_pcm_oss bitblit softcursor snd_mixer_oss vga16fb vgastate snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi radeon snd_seq_midi_event ttm snd_seq drm_kms_helper snd_timer drm i2c_algo_bit intel_agp snd_seq_device agpgart snd soundcore snd_page_alloc ppdev shpchp parport_pc lp parport usbhid hid usb_storage floppy 8139too 8139cp mii
[   25.816099] Pid: 0, comm: swapper Not tainted 2.6.32-21-generic #32-Ubuntu
[   25.816102] Call Trace:
[   25.816111]  [<c014c3d2>] warn_slowpath_common+0x72/0xa0
[   25.816117]  [<c04d824e>] ? dev_watchdog+0x1fe/0x210
[   25.816123]  [<c04d824e>] ? dev_watchdog+0x1fe/0x210
[   25.816128]  [<c014c44b>] warn_slowpath_fmt+0x2b/0x30
[   25.816132]  [<c04d824e>] dev_watchdog+0x1fe/0x210
[   25.816139]  [<c0163980>] ? insert_work+0x60/0xb0
[   25.816145]  [<c012a438>] ? default_spin_lock_flags+0x8/0x10
[   25.816151]  [<c058b5af>] ? _spin_lock_irqsave+0x2f/0x50
[   25.816157]  [<c0163c46>] ? __queue_work+0x36/0x50
[   25.816161]  [<c015b63e>] run_timer_softirq+0x13e/0x2c0
[   25.816168]  [<c0176814>] ? tick_dev_program_event+0x74/0xd0
[   25.816173]  [<c04d8050>] ? dev_watchdog+0x0/0x210
[   25.816178]  [<c0153068>] __do_softirq+0x98/0x1b0
[   25.816182]  [<c01531c5>] do_softirq+0x45/0x50
[   25.816186]  [<c0153315>] irq_exit+0x65/0x70
[   25.816192]  [<c058faec>] smp_apic_timer_interrupt+0x5c/0x8b
[   25.816198]  [<c0103df1>] apic_timer_interrupt+0x31/0x40
[   25.816202]  [<c012982a>] ? native_safe_halt+0xa/0x10
[   25.816207]  [<c010a750>] default_idle+0x40/0x90
[   25.816211]  [<c01021d4>] cpu_idle+0x94/0xd0
[   25.816218]  [<c0579168>] rest_init+0x58/0x60
[   25.816224]  [<c07a38ec>] start_kernel+0x351/0x357
[   25.816228]  [<c07a33c7>] ? unknown_bootoption+0x0/0x19e
[   25.816233]  [<c07a30aa>] i386_start_kernel+0xaa/0xb1
[   25.816236] ---[ end trace 031d46e77e9aa069 ]---
[   28.816041] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   40.816065] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   70.816055] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  106.816043] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  154.816042] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  268.820037] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  311.000059] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  641.513918] usb 1-3: USB disconnect, address 4
[  641.800029] usb 1-3: new high speed USB device using ehci_hcd and address 5
[  641.924025] usb 1-3: device descriptor read/64, error -71
[  642.204898] usb 1-3: configuration #1 chosen from 1 choice
[  642.205346] scsi5 : SCSI emulation for USB Mass Storage devices
[  642.205847] usb-storage: device found at 5
[  642.205852] usb-storage: waiting for device to settle before scanning
[  647.209412] usb-storage: device scan complete
[  647.212288] scsi 5:0:0:0: Direct-Access     IN-WIN   iAPP  HS-CF      1.63 PQ: 0 ANSI: 0
[  647.214891] scsi 5:0:0:1: Direct-Access     IN-WIN   iAPP  HS-MS      1.63 PQ: 0 ANSI: 0
[  647.217519] scsi 5:0:0:2: Direct-Access     IN-WIN   iAPP  HS-SM      1.63 PQ: 0 ANSI: 0
[  647.219878] scsi 5:0:0:3: Direct-Access     IN-WIN   iAPP  HS-SD/MMC  1.63 PQ: 0 ANSI: 0
[  647.224202] sd 5:0:0:0: Attached scsi generic sg3 type 0
[  647.225197] sd 5:0:0:1: Attached scsi generic sg4 type 0
[  647.236265] sd 5:0:0:2: Attached scsi generic sg5 type 0
[  647.237615] sd 5:0:0:3: Attached scsi generic sg6 type 0
[  647.238894] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  647.247376] sd 5:0:0:2: [sdd] Attached SCSI removable disk
[  647.330816] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[  647.333668] sd 5:0:0:3: [sde] Attached SCSI removable disk
[  671.000042] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  692.937288] usb 1-3: USB disconnect, address 5
[  693.220036] usb 1-3: new high speed USB device using ehci_hcd and address 6
[  693.344024] usb 1-3: device descriptor read/64, error -71
[  693.624888] usb 1-3: configuration #1 chosen from 1 choice
[  693.625862] scsi6 : SCSI emulation for USB Mass Storage devices
[  693.626128] usb-storage: device found at 6
[  693.626133] usb-storage: waiting for device to settle before scanning
[  698.629405] usb-storage: device scan complete
[  698.632432] scsi 6:0:0:0: Direct-Access     IN-WIN   iAPP  HS-CF      1.63 PQ: 0 ANSI: 0
[  698.635001] scsi 6:0:0:1: Direct-Access     IN-WIN   iAPP  HS-MS      1.63 PQ: 0 ANSI: 0
[  698.637628] scsi 6:0:0:2: Direct-Access     IN-WIN   iAPP  HS-SM      1.63 PQ: 0 ANSI: 0
[  698.639987] scsi 6:0:0:3: Direct-Access     IN-WIN   iAPP  HS-SD/MMC  1.63 PQ: 0 ANSI: 0
[  698.648614] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  698.652482] sd 6:0:0:1: Attached scsi generic sg4 type 0
[  698.662911] sd 6:0:0:2: Attached scsi generic sg5 type 0
[  698.664763] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  698.665165] sd 6:0:0:3: Attached scsi generic sg6 type 0
[  698.672919] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[  698.727389] sd 6:0:0:3: [sde] Attached SCSI removable disk
[  698.748520] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[  713.000057] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  809.000048] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  917.000040] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  965.000079] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1097.000044] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1247.000036] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1301.000052] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1511.000182] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1691.000186] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1715.000050] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1829.000048] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1946.828028] end_request: I/O error, dev fd0, sector 0
[ 1946.852035] end_request: I/O error, dev fd0, sector 0
[ 2195.000040] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2225.004034] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2633.000066] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2661.468026] usb 1-4: new high speed USB device using ehci_hcd and address 7
[ 2661.601724] usb 1-4: configuration #1 chosen from 1 choice
[ 2661.602201] scsi7 : SCSI emulation for USB Mass Storage devices
[ 2661.602697] usb-storage: device found at 7
[ 2661.602703] usb-storage: waiting for device to settle before scanning
[ 2666.600226] usb-storage: device scan complete
[ 2666.600825] scsi 7:0:0:0: Direct-Access     Ut165    USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[ 2666.603062] sd 7:0:0:0: Attached scsi generic sg7 type 0
[ 2666.605086] sd 7:0:0:0: [sdf] 7892040 512-byte logical blocks: (4.04 GB/3.76 GiB)
[ 2666.608933] sd 7:0:0:0: [sdf] Write Protect is off
[ 2666.608942] sd 7:0:0:0: [sdf] Mode Sense: 00 00 00 00
[ 2666.608948] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 2666.613831] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 2666.613843]  sdf:
[ 2667.119555] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 2667.119563] sd 7:0:0:0: [sdf] Attached SCSI removable disk

```

lshw -C network:
```

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:50:8d:53:3b:70
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:a000(size=256) memory:fb000000-fb0000ff memory:20000000-2000ffff(prefetchable)

```

/etc/init.d/networking restart:
```

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

```

Kernel: 2.6.32-21-generic i686

---

