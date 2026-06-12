---
title: "Toshiba cannot recognise ethernet or wireless network"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by messie on 2010-04-12
Greetings, I am a brand new user of linux with little experience. Recently, I tried ubuntu on my Desktop and found that they are so nice that decided to install them on my laptop which is a toshiba portege m800-10z. However, I find that ubuntu do not recognize neither my pci ethernet marvell card nor the intel 5100 wireless card. I have searched for a solution over the internet but none seems to work. I would appreciate if someone could point me to the right direction to solve this problem

Upon searching the net I found that the products of the commands lspci and lsmod as well as the dmesg command are helpful, so I post a file of the results in case they are helpful

```
[    2.894157] Marking TSC unstable due to TSC halts in idle
[    2.894175] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.894194] processor LNXCPU:00: registered as cooling_device0
[    2.894198] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.894624] ACPI: SSDT 00000000b5f19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20061109)
[    2.895004] ACPI: SSDT 00000000b5f19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20061109)
[    2.895978] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.895996] processor LNXCPU:01: registered as cooling_device1
[    2.895999] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.350061] thermal LNXTHERM:01: registered as thermal_zone0
[    3.350067] ACPI: Thermal Zone [THRM] (50 C)
[    3.351089] Linux agpgart interface v0.103
[    3.351097] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.352124] brd: module loaded
[    3.352513] loop: module loaded
[    3.352571] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    3.352663] ahci 0000:00:1f.2: version 3.0
[    3.352676]   alloc irq_desc for 19 on node 0
[    3.352677]   alloc kstat_irqs on node 0
[    3.352682] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.352716]   alloc irq_desc for 27 on node 0
[    3.352718]   alloc kstat_irqs on node 0
[    3.352726] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    3.352799] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    3.352802] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pio slum part ems
[    3.352807] ahci 0000:00:1f.2: setting latency timer to 64
[    3.352965] ACPI: Battery Slot [BAT1] (battery absent)
[    3.410056] scsi0 : ahci
[    3.410135] scsi1 : ahci
[    3.410188] scsi2 : ahci
[    3.410239] scsi3 : ahci
[    3.410300] scsi4 : ahci
[    3.410357] scsi5 : ahci
[    3.410467] ata1: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04100 irq 27
[    3.410471] ata2: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04180 irq 27
[    3.410472] ata3: DUMMY
[    3.410473] ata4: DUMMY
[    3.410476] ata5: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04300 irq 27
[    3.410479] ata6: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04380 irq 27
[    3.411195] Fixed MDIO Bus: probed
[    3.411225] PPP generic driver version 2.4.2
[    3.411299] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.411340] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    3.411351] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.411355] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.411399] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.415310] ehci_hcd 0000:00:1a.7: debug port 1
[    3.415317] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.415328] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf4a04800
[    3.430012] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.430071] usb usb1: configuration #1 chosen from 1 choice
[    3.430098] hub 1-0:1.0: USB hub found
[    3.430105] hub 1-0:1.0: 6 ports detected
[    3.430188]   alloc irq_desc for 23 on node 0
[    3.430190]   alloc kstat_irqs on node 0
[    3.430194] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.430203] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.430206] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.430231] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.434138] ehci_hcd 0000:00:1d.7: debug port 1
[    3.434144] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.434155] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4a04c00
[    3.450013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.450072] usb usb2: configuration #1 chosen from 1 choice
[    3.450094] hub 2-0:1.0: USB hub found
[    3.450099] hub 2-0:1.0: 6 ports detected
[    3.450158] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.450170] uhci_hcd: USB Universal Host Controller Interface driver
[    3.450239] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.450245] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.450249] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.450277] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.450309] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    3.450380] usb usb3: configuration #1 chosen from 1 choice
[    3.450401] hub 3-0:1.0: USB hub found
[    3.450407] hub 3-0:1.0: 2 ports detected
[    3.450475]   alloc irq_desc for 21 on node 0
[    3.450477]   alloc kstat_irqs on node 0
[    3.450480] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.450486] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.450489] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.450514] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.450544] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    3.450611] usb usb4: configuration #1 chosen from 1 choice
[    3.450632] hub 4-0:1.0: USB hub found
[    3.450637] hub 4-0:1.0: 2 ports detected
[    3.450709] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    3.450715] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.450719] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.450753] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    3.450777] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    3.450844] usb usb5: configuration #1 chosen from 1 choice
[    3.450869] hub 5-0:1.0: USB hub found
[    3.450876] hub 5-0:1.0: 2 ports detected
[    3.450947] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.450953] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.450956] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.450981] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    3.451005] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    3.451070] usb usb6: configuration #1 chosen from 1 choice
[    3.451091] hub 6-0:1.0: USB hub found
[    3.451096] hub 6-0:1.0: 2 ports detected
[    3.451163] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.451169] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.451172] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.451197] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.451224] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    3.451290] usb usb7: configuration #1 chosen from 1 choice
[    3.451310] hub 7-0:1.0: USB hub found
[    3.451316] hub 7-0:1.0: 2 ports detected
[    3.451383]   alloc irq_desc for 18 on node 0
[    3.451384]   alloc kstat_irqs on node 0
[    3.451388] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.451394] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.451397] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.451425] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.451457] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    3.451523] usb usb8: configuration #1 chosen from 1 choice
[    3.451544] hub 8-0:1.0: USB hub found
[    3.451552] hub 8-0:1.0: 2 ports detected
[    3.451640] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.454135] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.455200] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.455204] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.455207] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.455209] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.455211] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.455256] mice: PS/2 mouse device common for all mice
[    3.455346] rtc_cmos 00:05: RTC can wake from S4
[    3.455377] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.455405] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.455483] device-mapper: uevent: version 1.0.3
[    3.455562] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    3.455629] device-mapper: multipath: version 1.1.0 loaded
[    3.455632] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.455842] cpuidle: using governor ladder
[    3.455939] cpuidle: using governor menu
[    3.456277] TCP cubic registered
[    3.456383] NET: Registered protocol family 10
[    3.456748] lo: Disabled Privacy Extensions
[    3.456989] NET: Registered protocol family 17
[    3.457006] Bluetooth: L2CAP ver 2.13
[    3.457007] Bluetooth: L2CAP socket layer initialized
[    3.457011] Bluetooth: SCO (Voice Link) ver 0.6
[    3.457012] Bluetooth: SCO socket layer initialized
[    3.457040] Bluetooth: RFCOMM TTY layer initialized
[    3.457042] Bluetooth: RFCOMM socket layer initialized
[    3.457044] Bluetooth: RFCOMM ver 1.11
[    3.457671] PM: Resume from disk failed.
[    3.457682] registered taskstats version 1
[    3.457784]   Magic number: 6:806:554
[    3.457820] pci_link PNP0C0F:05: hash matches
[    3.457868] rtc_cmos 00:05: setting system clock to 2010-04-12 23:31:04 UTC (1271115064)
[    3.457871] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.457872] EDD information not available.
[    3.484639] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.752541] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    3.762554] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.762578] ata5: SATA link down (SStatus 0 SControl 300)
[    3.762606] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.762626] ata6: SATA link down (SStatus 0 SControl 300)
[    3.763224] ACPI Warning: \_SB_.PCI0.SAT0.PRT0._GTF: Return type mismatch - found Integer, expected Buffer 20090521 nspredef-940
[    3.763237] ata1.00: _GTF unexpected object type 0x1
[    3.764181] ata2.00: ATAPI: MATSHITADVD-RAM UJ862AS, 1.50, max UDMA/33
[    3.766404] ata2.00: configured for UDMA/33
[    3.835402] ata1.00: ATA-8: TOSHIBA MK3252GSX, LV010M, max UDMA/100
[    3.835405] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.836446] ata1.00: _GTF unexpected object type 0x1
[    3.836596] ata1.00: configured for UDMA/100
[    3.836701] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3252GS LV01 PQ: 0 ANSI: 5
[    3.836833] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.836877] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    3.836917] sd 0:0:0:0: [sda] Write Protect is off
[    3.836919] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.836940] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.837053]  sda:
[    3.839182] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ862AS  1.50 PQ: 0 ANSI: 5
[    3.840838] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.840842] Uniform CD-ROM driver Revision: 3.20
[    3.840927] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.840974] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.886036]  sda1 sda2 <
[    3.902586] usb 1-2: configuration #1 chosen from 1 choice
[    3.916113]  sda5 sda6 >
[    3.936857] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.936896] Freeing unused kernel memory: 660k freed
[    3.937079] Write protecting the kernel read-only data: 7580k
[    4.002521] Clocksource tsc unstable (delta = -386461094 ns)
[    4.014007] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    4.014995] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[    4.017080] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    4.024131] sky2 driver version 1.23
[    4.024207] sky2 0000:07:00.0: enabling device (0000 -> 0003)
[    4.024218] sky2 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.024237] sky2 0000:07:00.0: setting latency timer to 64
[    4.024272] sky2 0000:07:00.0: unsupported chip type 0xff
[    4.024283] sky2 0000:07:00.0: PCI INT A disabled
[    4.024732] sky2: probe of 0000:07:00.0 failed with error -95
[    4.091879] [drm] Initialized drm 1.1.0 20060810
[    4.103738] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.103743] i915 0000:00:02.0: setting latency timer to 64
[    4.121387] Initializing USB Mass Storage driver...
[    4.129774] scsi6 : SCSI emulation for USB Mass Storage devices
[    4.130660] usbcore: registered new interface driver usb-storage
[    4.130663] USB Mass Storage support registered.
[    4.132539] usb-storage: device found at 2
[    4.132541] usb-storage: waiting for device to settle before scanning
[    4.133934] ohci1394 0000:0a:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.137187]   alloc irq_desc for 28 on node 0
[    4.137190]   alloc kstat_irqs on node 0
[    4.137198] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    4.202549] hub 2-0:1.0: unable to enumerate USB device on port 3
[    4.240401] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[ff501000-ff5017ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.248079] [drm] i2c_init DPDDC-B
[    4.257694] [drm] i2c_init DPDDC-D
[    4.322538] usb 2-4: new high speed USB device using ehci_hcd and address 5
[    4.386363] i2c-adapter i2c-2: unable to read EDID block.
[    4.386366] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    4.486291] usb 2-4: configuration #1 chosen from 1 choice
[    4.720736] [drm] TV-20: set mode NTSC 480i 0
[    4.762512] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    4.845349] [drm] fb0: inteldrmfb frame buffer device
[    4.940131] usb 6-1: configuration #1 chosen from 1 choice
[    4.946935] usbcore: registered new interface driver hiddev
[    4.959303] input: MosArt Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input5
[    4.959364] generic-usb 0003:13EE:0003.0001: input,hidraw0: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:1d.0-1/input0
[    4.959375] usbcore: registered new interface driver usbhid
[    4.959378] usbhid: v2.6:USB HID core driver
[    5.220075] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    5.392127] usb 6-2: configuration #1 chosen from 1 choice
[    5.562807] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b2400013b9c66]
[    9.130239] usb-storage: device scan complete
[    9.130946] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 8GB    8.07 PQ: 0 ANSI: 2
[    9.131295] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    9.132526] sd 6:0:0:0: [sdb] 15687680 512-byte logical blocks: (8.03 GB/7.48 GiB)
[    9.133017] sd 6:0:0:0: [sdb] Write Protect is off
[    9.133019] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    9.133021] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    9.135016] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    9.135020]  sdb:
[    9.252816] acpi device:05: registered as cooling_device2
[    9.252978] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input6
[    9.253005] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.253033] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.427170]  sdb1
[    9.429483] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    9.429486] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    9.496176] [drm] LVDS-8: set mode 1280x800 1d
[    9.518773] Console: switching to colour frame buffer device 160x50
[   12.881336] PM: Starting manual resume from disk
[   12.881339] PM: Resume from partition 8:6
[   12.881341] PM: Checking hibernation image.
[   12.881481] PM: Resume from disk failed.
[   13.241537] EXT4-fs (sda5): barriers enabled
[   13.262392] kjournald2 starting: pid 512, dev sda5:8, commit interval 5 seconds
[   13.262456] EXT4-fs (sda5): delayed allocation enabled
[   13.262460] EXT4-fs: file extents enabled
[   13.265134] EXT4-fs: mballoc enabled
[   13.265145] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   14.069076] type=1505 audit(1271115075.102:2): operation="profile_load" pid=539 name=/usr/share/gdm/guest-session/Xsession
[   14.071005] type=1505 audit(1271115075.112:3): operation="profile_load" pid=540 name=/sbin/dhclient3
[   14.071676] type=1505 audit(1271115075.112:4): operation="profile_load" pid=540 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.071999] type=1505 audit(1271115075.112:5): operation="profile_load" pid=540 name=/usr/lib/connman/scripts/dhclient-script
[   14.136544] type=1505 audit(1271115075.172:6): operation="profile_load" pid=541 name=/usr/bin/evince
[   14.145818] type=1505 audit(1271115075.182:7): operation="profile_load" pid=541 name=/usr/bin/evince-previewer
[   14.151304] type=1505 audit(1271115075.192:8): operation="profile_load" pid=541 name=/usr/bin/evince-thumbnailer
[   14.170314] type=1505 audit(1271115075.212:9): operation="profile_load" pid=543 name=/usr/lib/cups/backend/cups-pdf
[   14.171032] type=1505 audit(1271115075.212:10): operation="profile_load" pid=543 name=/usr/sbin/cupsd
[   14.173247] type=1505 audit(1271115075.212:11): operation="profile_load" pid=544 name=/usr/sbin/tcpdump
[   14.963605] Adding 2192832k swap on /dev/sda6.  Priority:-1 extents:1 across:2192832k
[   15.031842] udev: starting version 147
[   15.516510] lp: driver loaded but no devices found
[   16.452348] EXT4-fs (sda5): internal journal on sda5:8
[   17.112626] Linux video capture interface: v2.00
[   17.115945] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   17.116979] sdhci: Secure Digital Host Controller Interface driver
[   17.116982] sdhci: Copyright(c) Pierre Ossman
[   17.144706] sdhci-pci 0000:0a:01.2: SDHCI controller found [1217:7120] (rev 2)
[   17.144726] sdhci-pci 0000:0a:01.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.144766] mmc0: Unknown controller version (2). You may experience problems.
[   17.144808] Registered led device: mmc0::
[   17.144843] mmc0: SDHCI controller on PCI [0000:0a:01.2] using DMA
[   17.146903] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input7
[   17.146950] usbcore: registered new interface driver uvcvideo
[   17.146953] USB Video Class driver (v0.1.0)
[   17.241015] cfg80211: Calling CRDA to update world regulatory domain
[   17.271606] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   17.271609] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   17.271953] iwlagn 0000:08:00.0: enabling device (0000 -> 0002)
[   17.271963] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.271975] iwlagn 0000:08:00.0: setting latency timer to 64
[   17.272020] iwlagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0xFFFFFFFF
[   17.424932] iwlagn 0000:08:00.0: Failed, HW not ready
[   17.424952] iwlagn 0000:08:00.0: PCI INT A disabled
[   17.463423] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.474636] cfg80211: World regulatory domain updated:
[   17.474638]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.474641]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.474643]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.474645]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.474647]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.474649]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.829010] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1e0b1, caps: 0xd04711/0xa00000
[   17.870049] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   19.073221]   alloc irq_desc for 22 on node 0
[   19.073224]   alloc kstat_irqs on node 0
[   19.073232] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.073278] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.312300] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   19.312364] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   19.312416] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   19.910986] type=1505 audit(1271104280.944:12): operation="profile_replace" pid=1052 name=/usr/share/gdm/guest-session/Xsession
[   19.912395] type=1505 audit(1271104280.944:13): operation="profile_replace" pid=1053 name=/sbin/dhclient3
[   19.913081] type=1505 audit(1271104280.954:14): operation="profile_replace" pid=1053 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.913426] type=1505 audit(1271104280.954:15): operation="profile_replace" pid=1053 name=/usr/lib/connman/scripts/dhclient-script
[   19.916368] type=1505 audit(1271104280.954:16): operation="profile_replace" pid=1054 name=/usr/bin/evince
[   19.925553] type=1505 audit(1271104280.964:17): operation="profile_replace" pid=1054 name=/usr/bin/evince-previewer
[   19.931044] type=1505 audit(1271104280.964:18): operation="profile_replace" pid=1054 name=/usr/bin/evince-thumbnailer
[   19.938685] type=1505 audit(1271104280.974:19): operation="profile_replace" pid=1056 name=/usr/lib/cups/backend/cups-pdf
[   19.939375] type=1505 audit(1271104280.974:20): operation="profile_replace" pid=1056 name=/usr/sbin/cupsd
[   19.941527] type=1505 audit(1271104280.974:21): operation="profile_replace" pid=1057 name=/usr/sbin/tcpdump
[   22.066469] ppdev: user-space parallel port driver
[   25.187147] i2c-adapter i2c-2: unable to read EDID block.
[   25.187151] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   25.191581] i2c-adapter i2c-2: unable to read EDID block.
[   25.191583] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   25.236657] [drm] TV-20: set mode NTSC 480i 0
[   25.378360] [drm] TV-20: set mode NTSC 480i 0
[   25.699111] i2c-adapter i2c-2: unable to read EDID block.
[   25.699115] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   25.703562] i2c-adapter i2c-2: unable to read EDID block.
[   25.703564] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   25.749536] [drm] TV-20: set mode NTSC 480i 0
[   25.891072] [drm] TV-20: set mode NTSC 480i 0
[   26.116413] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   26.116419] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[   26.116425] Info fld=0x5662e
[   26.116427] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   26.116434] end_request: I/O error, dev sr0, sector 1415352
[   26.116439] Buffer I/O error on device sr0, logical block 176919
[   26.285703] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   26.285708] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[   26.285713] Info fld=0x5662e
[   26.285715] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   26.285721] end_request: I/O error, dev sr0, sector 1415352
[   26.285724] Buffer I/O error on device sr0, logical block 176919
[   26.851779] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   26.851785] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[   26.851791] Info fld=0x5662e
[   26.851793] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   26.851800] end_request: I/O error, dev sr0, sector 1415352
[   26.851805] Buffer I/O error on device sr0, logical block 176919
[   27.057969] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   27.057976] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[   27.057981] Info fld=0x5662e
[   27.057983] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   27.057990] end_request: I/O error, dev sr0, sector 1415352
[   27.057995] Buffer I/O error on device sr0, logical block 176919
[   27.262278] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   27.262284] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[   27.262289] Info fld=0x5662e
[   27.262291] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   27.262298] end_request: I/O error, dev sr0, sector 1415352
[   27.262302] Buffer I/O error on device sr0, logical block 176919
[   28.344575] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   28.344581] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[   28.344587] Info fld=0x5662e
[   28.344589] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   28.344596] end_request: I/O error, dev sr0, sector 1415352
[   28.344601] Buffer I/O error on device sr0, logical block 176919
[   28.539694] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   28.539700] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[   28.539705] Info fld=0x5662e
[   28.539707] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   28.539713] end_request: I/O error, dev sr0, sector 1415352
[   28.539717] Buffer I/O error on device sr0, logical block 176919
[   28.829210] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   28.829216] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[   28.829222] Info fld=0x5662e
[   28.829224] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   28.829231] end_request: I/O error, dev sr0, sector 1415352
[   28.829236] Buffer I/O error on device sr0, logical block 176919
[   29.022213] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.022220] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[   29.022225] Info fld=0x5662e
[   29.022227] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   29.022234] end_request: I/O error, dev sr0, sector 1415352
[   29.022239] Buffer I/O error on device sr0, logical block 176919
[   30.347136] i2c-adapter i2c-2: unable to read EDID block.
[   30.347140] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   30.351675] i2c-adapter i2c-2: unable to read EDID block.
[   30.351677] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   30.397670] [drm] TV-20: set mode NTSC 480i 0
[   30.538604] [drm] TV-20: set mode NTSC 480i 0
[   30.789292] i2c-adapter i2c-2: unable to read EDID block.
[   30.789296] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   30.793739] i2c-adapter i2c-2: unable to read EDID block.
[   30.793742] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   30.839710] [drm] TV-20: set mode NTSC 480i 0
[   30.980885] [drm] TV-20: set mode NTSC 480i 0
[   31.249215] i2c-adapter i2c-2: unable to read EDID block.
[   31.249219] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   31.253670] i2c-adapter i2c-2: unable to read EDID block.
[   31.253672] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   31.299643] [drm] TV-20: set mode NTSC 480i 0
[   31.440820] [drm] TV-20: set mode NTSC 480i 0
[   42.870332] Intel AES-NI instructions are not detected.
[   42.913583] padlock: VIA PadLock not detected.
[   45.189407] i2c-adapter i2c-2: unable to read EDID block.
[   45.189413] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   45.194041] i2c-adapter i2c-2: unable to read EDID block.
[   45.194044] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   45.240067] [drm] TV-20: set mode NTSC 480i 0
[   45.381866] [drm] TV-20: set mode NTSC 480i 0
[   45.626756] i2c-adapter i2c-2: unable to read EDID block.
[   45.626760] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   45.631212] i2c-adapter i2c-2: unable to read EDID block.
[   45.631214] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   45.677184] [drm] TV-20: set mode NTSC 480i 0
[   45.818482] [drm] TV-20: set mode NTSC 480i 0
[   46.066858] i2c-adapter i2c-2: unable to read EDID block.
[   46.066862] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   46.071312] i2c-adapter i2c-2: unable to read EDID block.
[   46.071315] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   46.117295] [drm] TV-20: set mode NTSC 480i 0
[   46.258442] [drm] TV-20: set mode NTSC 480i 0
[   47.549356] i2c-adapter i2c-2: unable to read EDID block.
[   47.549359] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   47.554041] i2c-adapter i2c-2: unable to read EDID block.
[   47.554044] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   47.600018] [drm] TV-20: set mode NTSC 480i 0
[   47.741510] [drm] TV-20: set mode NTSC 480i 0
[   54.964207] UDF-fs: No VRS found
[   54.964211] UDF-fs: No partition found (1)
[   55.031982] ISO 9660 Extensions: Microsoft Joliet Level 3
[   55.118009] ISO 9660 Extensions: RRIP_1991A
[  445.128343] usb 1-2: USB disconnect, address 2
[  445.129147] FAT: bread failed in fat_clusters_flush
[  445.130769] FAT: bread failed in fat_clusters_flush
[  445.160720] FAT: bread failed in fat_clusters_flush
[  445.161153] FAT: bread failed in fat_clusters_flush
[  445.161187] FAT: bread failed in fat_clusters_flush

Module                  Size  Used by
nls_iso8859_1           5280  0
nls_cp437               6976  0
isofs                  36424  1
vfat                   13184  0
udf                    88136  0
fat                    59832  1 vfat
crc_itu_t               2336  1 udf
cbc                     4224  312
cryptd                  8008  0
aes_x86_64              8992  313
aes_generic            28480  1 aes_x86_64
ecb                     3296  1
binfmt_misc            10220  1
ppdev                   8232  0
dm_crypt               14888  0
snd_hda_codec_intelhdmi    14880  1
snd_hda_codec_conexant    25376  1
snd_hda_intel          31880  2
snd_hda_codec          87584  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
joydev                 13088  0
snd_hwdep               9352  1 snd_hda_codec
iptable_filter          3872  0
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
iwlagn                124832  0
iwlcore               133248  1 iwlagn
mac80211              210104  2 iwlagn,iwlcore
snd_pcm_oss            44704  0
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0
snd_seq_oss            33440  0
snd_seq_midi            8192  0
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              109144  3 iwlagn,iwlcore,mac80211
sdhci_pci               8928  0
sdhci                  20484  1 sdhci_pci
uvcvideo               65260  0
led_class               5256  2 iwlcore,sdhci
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
snd                    77096  17 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
psmouse                57124  0
serio_raw               6596  0
lp                     11908  0
parport                40528  2 ppdev,lp
fbcon                  41344  72
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
usbhid                 43968  0
ohci1394               33780  0
ieee1394              100896  1 ohci1394
usb_storage            65952  0
i915                  246984  3
drm                   193856  3 i915
i2c_algo_bit            7076  1 i915
video                  23612  1 i915
output                  3680  1 video
sky2                   55556  0
intel_agp              32816  2 i915


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

---

### Post by chili555 on 2010-04-12
Here is a post about an Intel 5100 and a Marvell ethernet not working and a solution that might work for you; see posts #6 and 7. Post back and let us know your result.

[http://ubuntuforums.org/showthread.php?t=1448721](http://ubuntuforums.org/showthread.php?t=1448721)

---

### Post by messie on 2010-04-12
Holly molly, I did what the poster said and it got fixed! I cannot thank you enough! I have no idea what happened and what the problem or what i did with the command line was but it got fixed!

---

### Post by chili555 on 2010-04-12
I am not too sure, either. I read it in a bug report and someone had nearly the identical hardware and symptoms and said it fixed his issue. It also fixed the poster I referred you to. I'm no kernel magician, I just repeat what I hear and it often, but not always works. I am glad it's working for you. I love problems that get fixed in a lightning fast three posts!

Welcome to the Ubuntu party. Have fun!

---

