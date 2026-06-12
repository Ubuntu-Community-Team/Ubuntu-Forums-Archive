---
title: "Problems mounting and unmounting cds"
date: 2009-12-02
forum: Multimedia Software
---

### Post by fattom23 on 2009-12-02
I've been having trouble with mounting and ejecting optical discs since and upgrade to Karmic.  When I insert a cd, the system SOMETIMES puts up an error message stating that it is unable to mount audio disc (the location is already mounted).  Then, the hardware eject button on the drive stops working, and I have to either use the eject command, or select eject from the disc icon on my desktop.  I have no idea if this is related, but since the upgrade, I've been having a strange issue that most of the time, when I push the hardware eject button, the drive opens and immediately closes again.  A second push then works properly.

Below is the dmesg output from directly following insertion of the CD and the displaying of the error message.  I have no idea how to read all that stuff, so I don't know what part is relevant.  If anyone out there has any further ideas for testing or what the problem could be, I would really like to get this issue straightened out.  Thanks a million for any help you can offer.

```
[    2.115753] scsi6 : SCSI emulation for USB Mass Storage devices
[    2.115824] usbcore: registered new interface driver usb-storage
[    2.115827] USB Mass Storage support registered.
[    2.115927] usb-storage: device found at 6
[    2.115929] usb-storage: waiting for device to settle before scanning
[    2.440029] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    2.707627] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80001343c56]
[    2.718084] usb 2-1: configuration #1 chosen from 1 choice
[    2.730409] usbcore: registered new interface driver hiddev
[    2.737992] PM: Starting manual resume from disk
[    2.737996] PM: Resume from partition 8:24
[    2.737997] PM: Checking hibernation image.
[    2.738143] PM: Resume from disk failed.
[    2.739659] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
[    2.739722] generic-usb 0003:046E:5542.0001: input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:02.0-1/input0
[    2.741607] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[    2.741612] EXT4-fs (sdb1): write access will be enabled during recovery
[    2.760224] EXT4-fs (sdb1): barriers enabled
[    2.764086] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.1/input/input4
[    2.764174] generic-usb 0003:046E:5542.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:02.0-1/input1
[    2.764191] usbcore: registered new interface driver usbhid
[    2.764194] usbhid: v2.6:USB HID core driver
[    3.062513] usb 2-2: new low speed USB device using ohci_hcd and address 3
[    3.294120] usb 2-2: configuration #1 chosen from 1 choice
[    3.309515] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input5
[    3.309586] generic-usb 0003:046D:C50E.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:02.0-2/input0
[    3.503564] kjournald2 starting: pid 412, dev sdb1:8, commit interval 5 seconds
[    3.503583] EXT4-fs (sdb1): delayed allocation enabled
[    3.503585] EXT4-fs: file extents enabled
[    3.503748] EXT4-fs: mballoc enabled
[    3.503761] EXT4-fs (sdb1): orphan cleanup on readonly fs
[    3.503767] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 130
[    3.503798] EXT4-fs (sdb1): 1 orphan inode deleted
[    3.503800] EXT4-fs (sdb1): recovery complete
[    3.634780] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[    3.643049] usb 2-4: new full speed USB device using ohci_hcd and address 4
[    3.872111] usb 2-4: configuration #1 chosen from 1 choice
[    4.065885] type=1505 audit(1259716171.868:2): operation="profile_load" pid=437 name=/usr/share/gdm/guest-session/Xsession
[    4.068220] type=1505 audit(1259716171.868:3): operation="profile_load" pid=438 name=/sbin/dhclient3
[    4.068435] type=1505 audit(1259716171.868:4): operation="profile_load" pid=438 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.068557] type=1505 audit(1259716171.868:5): operation="profile_load" pid=438 name=/usr/lib/connman/scripts/dhclient-script
[    4.114576] type=1505 audit(1259716171.918:6): operation="profile_load" pid=439 name=/usr/bin/evince
[    4.118292] type=1505 audit(1259716171.918:7): operation="profile_load" pid=439 name=/usr/bin/evince-previewer
[    4.120493] type=1505 audit(1259716171.918:8): operation="profile_load" pid=439 name=/usr/bin/evince-thumbnailer
[    4.131249] type=1505 audit(1259716171.928:9): operation="profile_load" pid=441 name=/usr/lib/cups/backend/cups-pdf
[    4.131519] type=1505 audit(1259716171.928:10): operation="profile_load" pid=441 name=/usr/sbin/cupsd
[    4.212522] usb 2-7: new full speed USB device using ohci_hcd and address 5
[    4.437103] usb 2-7: configuration #1 chosen from 1 choice
[    4.717354] Adding 1124508k swap on /dev/sdb8.  Priority:-1 extents:1 across:1124508k 
[    5.002832] udev: starting version 147
[    5.665724] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    5.665729] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    5.665733] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    5.665740] end_request: I/O error, dev sr0, sector 0
[    5.665743] __ratelimit: 3 callbacks suppressed
[    5.665745] Buffer I/O error on device sr0, logical block 0
[    5.665747] Buffer I/O error on device sr0, logical block 1
[    5.665750] Buffer I/O error on device sr0, logical block 2
[    5.665752] Buffer I/O error on device sr0, logical block 3
[    5.665754] Buffer I/O error on device sr0, logical block 4
[    5.665756] Buffer I/O error on device sr0, logical block 5
[    5.665758] Buffer I/O error on device sr0, logical block 6
[    5.665760] Buffer I/O error on device sr0, logical block 7
[    5.665762] Buffer I/O error on device sr0, logical block 8
[    5.665764] Buffer I/O error on device sr0, logical block 9
[    5.667159] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    5.667161] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    5.667163] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    5.667210] end_request: I/O error, dev sr0, sector 0
[    5.700016] EXT4-fs (sdb1): internal journal on sdb1:8
[    5.811963] parport_pc 00:0a: reported by Plug and Play ACPI
[    5.811989] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[    5.823309] ppdev: user-space parallel port driver
[    5.980802] kjournald starting.  Commit interval 5 seconds
[    5.980950] EXT3 FS on sda1, internal journal
[    5.980954] EXT3-fs: mounted filesystem with writeback data mode.
[    6.276581] nvidia: module license 'NVIDIA' taints kernel.
[    6.276585] Disabling lock debugging due to kernel taint
[    6.313271] EDAC MC: Ver: 2.1.0 Nov 10 2009
[    6.347063] usblp0: USB Bidirectional printer dev 4 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0F11
[    6.347082] usbcore: registered new interface driver usblp
[    6.380600] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    6.411268] lp0: using parport0 (interrupt-driven).
[    6.440611] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[    6.440630] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[    6.534302] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    6.534308]   alloc irq_desc for 18 on node 0
[    6.534310]   alloc kstat_irqs on node 0
[    6.534319] nvidia 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    6.534325] nvidia 0000:05:00.0: setting latency timer to 64
[    6.534565] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[    6.545346] EDAC amd64_edac:  Ver: 3.2.0 Nov 10 2009
[    6.545654] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    6.545660] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    6.545662] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    6.545663]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    6.545664]     Might be a BIOS bug, if BIOS says ECC is enabled
[    6.545665]     Use of the override can cause unknown side effects.
[    6.545679] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    6.824065] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.839424] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.839428] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.839432] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.839440] end_request: I/O error, dev sr0, sector 0
[    6.840414] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.840416] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.840419] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.840422] end_request: I/O error, dev sr0, sector 0
[    6.841382] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.841384] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.841387] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.841390] end_request: I/O error, dev sr0, sector 0
[    7.110181] usb-storage: device scan complete
[    7.117420] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[    7.124407] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[    7.131282] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[    7.138406] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[    7.138791] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    7.138868] sd 6:0:0:1: Attached scsi generic sg4 type 0
[    7.138945] sd 6:0:0:2: Attached scsi generic sg5 type 0
[    7.139025] sd 6:0:0:3: Attached scsi generic sg6 type 0
[    7.145535] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    7.153763] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[    7.154557] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[    7.156458] sd 6:0:0:2: [sde] Attached SCSI removable disk
[    8.681422] usbcore: registered new interface driver snd-usb-audio
[    9.053703] kjournald starting.  Commit interval 5 seconds
[    9.053932] EXT3 FS on sdb3, internal journal
[    9.053936] EXT3-fs: mounted filesystem with writeback data mode.
[   10.713286] EXT4-fs (sdb5): barriers enabled
[   10.745319] kjournald2 starting: pid 1011, dev sdb5:8, commit interval 5 seconds
[   10.745561] EXT4-fs (sdb5): internal journal on sdb5:8
[   10.745563] EXT4-fs (sdb5): delayed allocation enabled
[   10.745566] EXT4-fs: file extents enabled
[   10.745647] EXT4-fs: mballoc enabled
[   10.745661] EXT4-fs (sdb5): mounted filesystem with ordered data mode
[   12.293284] EXT4-fs (sdb6): barriers enabled
[   12.325228] kjournald2 starting: pid 1084, dev sdb6:8, commit interval 5 seconds
[   12.325445] EXT4-fs (sdb6): internal journal on sdb6:8
[   12.325448] EXT4-fs (sdb6): delayed allocation enabled
[   12.325451] EXT4-fs: file extents enabled
[   12.325550] EXT4-fs: mballoc enabled
[   12.325572] EXT4-fs (sdb6): mounted filesystem with ordered data mode
[   14.939964] kjournald starting.  Commit interval 5 seconds
[   14.940206] EXT3 FS on sdb7, internal journal
[   14.940210] EXT3-fs: mounted filesystem with writeback data mode.
[   15.496189] __ratelimit: 68 callbacks suppressed
[   15.496194] type=1505 audit(1259716183.298:12): operation="profile_replace" pid=1175 name=/usr/share/gdm/guest-session/Xsession
[   15.497601] type=1505 audit(1259716183.298:13): operation="profile_replace" pid=1176 name=/sbin/dhclient3
[   15.497820] type=1505 audit(1259716183.298:14): operation="profile_replace" pid=1176 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.497946] type=1505 audit(1259716183.298:15): operation="profile_replace" pid=1176 name=/usr/lib/connman/scripts/dhclient-script
[   15.502735] type=1505 audit(1259716183.308:16): operation="profile_replace" pid=1177 name=/usr/bin/evince
[   15.506490] type=1505 audit(1259716183.308:17): operation="profile_replace" pid=1177 name=/usr/bin/evince-previewer
[   15.508702] type=1505 audit(1259716183.308:18): operation="profile_replace" pid=1177 name=/usr/bin/evince-thumbnailer
[   15.514012] type=1505 audit(1259716183.318:19): operation="profile_replace" pid=1179 name=/usr/lib/cups/backend/cups-pdf
[   15.514286] type=1505 audit(1259716183.318:20): operation="profile_replace" pid=1179 name=/usr/sbin/cupsd
[   15.515932] type=1505 audit(1259716183.318:21): operation="profile_replace" pid=1180 name=/usr/sbin/tcpdump
[   15.805253] EXT4-fs (sdb9): barriers enabled
[   15.818971] kjournald2 starting: pid 1196, dev sdb9:8, commit interval 5 seconds
[   15.819199] EXT4-fs (sdb9): internal journal on sdb9:8
[   15.819202] EXT4-fs (sdb9): delayed allocation enabled
[   15.819205] EXT4-fs: file extents enabled
[   15.819365] EXT4-fs: mballoc enabled
[   15.819381] EXT4-fs (sdb9): mounted filesystem with ordered data mode
[   17.829075] usplash:367 freeing invalid memtype fffffffff9000000-fffffffff9e00000
[   23.000284] RPC: Registered udp transport module.
[   23.000287] RPC: Registered tcp transport module.
[   24.271931] svc: failed to register lockdv1 RPC service (errno 97).
[   29.412508] eth0: no IPv6 routers present
[   29.635219] usb 2-4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  161.332514] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[  517.330021] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 1113.320016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 1321.320015] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 1563.332515] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 1787.332513] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 2093.330021] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 2383.330017] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 2700.332514] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 2897.330017] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 2901.320018] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 3733.330019] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 4699.320030] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 5945.330017] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 6007.320016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 8655.330017] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 8841.322517] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[ 9355.330016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[10429.320014] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[11721.330017] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[12063.332516] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[12405.332516] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[12591.320015] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[13541.332517] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[13727.320017] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[13789.330016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[14069.320015] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[14131.330017] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[14615.330018] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[16293.330017] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[18329.330016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[19663.320015] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[19819.332516] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[20751.330013] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[21347.330015] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[24231.320016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[24573.322515] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[25071.330016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[26135.330017] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[26483.330018] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[26527.330018] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[27655.332531] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[28815.332516] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[29095.321457] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[29157.332528] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[29361.330028] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[29669.422525] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[30415.332516] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[30757.332650] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[30993.336838] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[31739.340013] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[33993.332530] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[34629.332533] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[34971.330018] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[37181.320017] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[37403.332525] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[38489.332514] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[38671.322524] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[39381.330023] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[39443.332516] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[39625.330028] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[40007.330030] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[40015.322537] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[40419.340368] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[40555.352514] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[41307.332526] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[41311.320016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[41489.332515] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[41493.322514] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[41759.332517] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[41795.427353] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[41945.340016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[43355.362516] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[43533.320016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[43595.332521] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[43755.330030] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[43981.362542] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[44283.342963] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[44389.330186] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[44731.332516] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[45157.320042] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[45277.332516] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[45415.320016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[45509.332526] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[45581.342517] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[45659.320027] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[46027.332515] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[46551.332531] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[47439.330015] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[47687.320016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[47967.329198] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[48371.333036] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[48983.330023] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[49103.330022] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[49165.332517] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[49513.342514] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[51107.332536] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[51205.320017] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[51885.330028] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[53219.322515] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[54985.360025] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[55329.332527] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[55979.322524] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[56847.330029] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[57359.322533] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[58167.330016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[58261.332521] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[58287.332515] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[58923.330027] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[59313.322525] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[59655.338789] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[59925.320020] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[60045.332521] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[60169.332516] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[60901.330016] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[60963.322732] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[61123.332541] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[61243.320033] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[61305.330030] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[62015.331061] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[62652.332524] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[62794.332524] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[62804.320906] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[62996.332197] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[63582.330324] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[63730.332526] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[63846.332527] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[64124.330030] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[64339.330587] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[64978.332532] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[65046.330437] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[65442.332517] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[66704.332519] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[66848.332516] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[67230.332515] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[67613.342558] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[67620.387788] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[67620.387793] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[67620.387797] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[67620.387804] end_request: I/O error, dev sr0, sector 0
[67620.387808] Buffer I/O error on device sr0, logical block 0
[67620.387811] Buffer I/O error on device sr0, logical block 1
[67620.387814] Buffer I/O error on device sr0, logical block 2
[67620.387817] Buffer I/O error on device sr0, logical block 3
[67620.387819] Buffer I/O error on device sr0, logical block 4
[67620.387821] Buffer I/O error on device sr0, logical block 5
[67620.387823] Buffer I/O error on device sr0, logical block 6
[67620.387825] Buffer I/O error on device sr0, logical block 7
[67620.387828] Buffer I/O error on device sr0, logical block 8
[67620.387830] Buffer I/O error on device sr0, logical block 9
[67620.389220] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[67620.389222] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[67620.389225] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[67620.389229] end_request: I/O error, dev sr0, sector 0
[67620.547285] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[67620.547290] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[67620.547294] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[67620.547301] end_request: I/O error, dev sr0, sector 0
[67620.551317] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[67620.551319] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[67620.551322] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[67620.551329] end_request: I/O error, dev sr0, sector 0
[67734.480219] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[67734.480224] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[67734.480227] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[67734.480234] end_request: I/O error, dev sr0, sector 0
[67734.480238] __ratelimit: 60 callbacks suppressed
[67734.480240] Buffer I/O error on device sr0, logical block 0
[67734.480243] Buffer I/O error on device sr0, logical block 1
[67734.480247] Buffer I/O error on device sr0, logical block 2
[67734.480249] Buffer I/O error on device sr0, logical block 3
[67734.480251] Buffer I/O error on device sr0, logical block 4
[67734.480254] Buffer I/O error on device sr0, logical block 5
[67734.480256] Buffer I/O error on device sr0, logical block 6
[67734.480258] Buffer I/O error on device sr0, logical block 7
[67734.480260] Buffer I/O error on device sr0, logical block 8
[67734.480262] Buffer I/O error on device sr0, logical block 9
[67734.483877] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[67734.483883] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[67734.483887] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[67734.483893] end_request: I/O error, dev sr0, sector 0
[67734.629125] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[67734.629130] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[67734.629134] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[67734.629141] end_request: I/O error, dev sr0, sector 0
[67734.630117] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[67734.630119] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[67734.630122] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[67734.630125] end_request: I/O error, dev sr0, sector 0
[67734.631086] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[67734.631088] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[67734.631091] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[67734.631094] end_request: I/O error, dev sr0, sector 0
[68129.361914] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[68331.330027] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[68381.342556] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[68413.468622] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68413.468628] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68413.468631] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68413.468639] end_request: I/O error, dev sr0, sector 0
[68413.468643] __ratelimit: 68 callbacks suppressed
[68413.468645] Buffer I/O error on device sr0, logical block 0
[68413.468648] Buffer I/O error on device sr0, logical block 1
[68413.468651] Buffer I/O error on device sr0, logical block 2
[68413.468653] Buffer I/O error on device sr0, logical block 3
[68413.468655] Buffer I/O error on device sr0, logical block 4
[68413.468657] Buffer I/O error on device sr0, logical block 5
[68413.468660] Buffer I/O error on device sr0, logical block 6
[68413.468662] Buffer I/O error on device sr0, logical block 7
[68413.468664] Buffer I/O error on device sr0, logical block 8
[68413.468667] Buffer I/O error on device sr0, logical block 9
[68413.472290] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68413.472294] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68413.472297] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68413.472301] end_request: I/O error, dev sr0, sector 0
[68413.531181] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68413.531187] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68413.531190] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68413.531198] end_request: I/O error, dev sr0, sector 0
[68413.532143] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68413.532145] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68413.532148] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68413.532151] end_request: I/O error, dev sr0, sector 0
[68454.332524] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[68462.470774] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68462.470779] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68462.470783] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68462.470790] end_request: I/O error, dev sr0, sector 0
[68462.470794] __ratelimit: 60 callbacks suppressed
[68462.470796] Buffer I/O error on device sr0, logical block 0
[68462.470800] Buffer I/O error on device sr0, logical block 1
[68462.470802] Buffer I/O error on device sr0, logical block 2
[68462.470804] Buffer I/O error on device sr0, logical block 3
[68462.470806] Buffer I/O error on device sr0, logical block 4
[68462.470808] Buffer I/O error on device sr0, logical block 5
[68462.470810] Buffer I/O error on device sr0, logical block 6
[68462.470813] Buffer I/O error on device sr0, logical block 7
[68462.470815] Buffer I/O error on device sr0, logical block 8
[68462.470817] Buffer I/O error on device sr0, logical block 9
[68462.471946] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68462.471949] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68462.471952] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68462.471956] end_request: I/O error, dev sr0, sector 0
[68462.531669] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68462.531674] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68462.531677] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68462.531684] end_request: I/O error, dev sr0, sector 0
[68462.532629] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68462.532631] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68462.532634] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68462.532637] end_request: I/O error, dev sr0, sector 0
[68462.533896] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68462.533898] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68462.533901] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68462.533905] end_request: I/O error, dev sr0, sector 0
[68510.473957] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68510.473961] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68510.473965] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68510.473972] end_request: I/O error, dev sr0, sector 0
[68510.473976] __ratelimit: 29 callbacks suppressed
[68510.473978] Buffer I/O error on device sr0, logical block 0
[68510.473983] Buffer I/O error on device sr0, logical block 1
[68510.473986] Buffer I/O error on device sr0, logical block 2
[68510.473988] Buffer I/O error on device sr0, logical block 3
[68510.473991] Buffer I/O error on device sr0, logical block 4
[68510.473993] Buffer I/O error on device sr0, logical block 5
[68510.473995] Buffer I/O error on device sr0, logical block 6
[68510.473997] Buffer I/O error on device sr0, logical block 7
[68510.474000] Buffer I/O error on device sr0, logical block 8
[68510.474002] Buffer I/O error on device sr0, logical block 9
[68510.475006] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68510.475009] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68510.475011] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68510.475015] end_request: I/O error, dev sr0, sector 0
[68510.537700] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68510.537706] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68510.537709] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68510.537716] end_request: I/O error, dev sr0, sector 0
[68510.538660] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68510.538662] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[68510.538665] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[68510.538668] end_request: I/O error, dev sr0, sector 0
[68578.332523] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[69041.471615] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[69041.471621] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[69041.471625] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[69041.471632] end_request: I/O error, dev sr0, sector 0
[69041.471636] __ratelimit: 25 callbacks suppressed
[69041.471639] Buffer I/O error on device sr0, logical block 0
[69041.471643] Buffer I/O error on device sr0, logical block 1
[69041.471645] Buffer I/O error on device sr0, logical block 2
[69041.471647] Buffer I/O error on device sr0, logical block 3
[69041.471649] Buffer I/O error on device sr0, logical block 4
[69041.471651] Buffer I/O error on device sr0, logical block 5
[69041.471653] Buffer I/O error on device sr0, logical block 6
[69041.471656] Buffer I/O error on device sr0, logical block 7
[69041.471658] Buffer I/O error on device sr0, logical block 8
[69041.471660] Buffer I/O error on device sr0, logical block 9
[69041.473910] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[69041.473913] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[69041.473916] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[69041.473922] end_request: I/O error, dev sr0, sector 0
[69041.533296] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[69041.533301] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[69041.533305] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[69041.533311] end_request: I/O error, dev sr0, sector 0
[69041.534260] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[69041.534262] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[69041.534265] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[69041.534268] end_request: I/O error, dev sr0, sector 0
[69041.535228] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[69041.535231] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[69041.535233] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[69041.535236] end_request: I/O error, dev sr0, sector 0
[69079.473434] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[69079.473439] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[69079.473443] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[69079.473450] end_request: I/O error, dev sr0, sector 0
[69079.473453] __ratelimit: 29 callbacks suppressed
[69079.473456] Buffer I/O error on device sr0, logical block 0
[69079.473460] Buffer I/O error on device sr0, logical block 1
[69079.473462] Buffer I/O error on device sr0, logical block 2
[69079.473465] Buffer I/O error on device sr0, logical block 3
[69079.473467] Buffer I/O error on device sr0, logical block 4
[69079.473469] Buffer I/O error on device sr0, logical block 5
[69079.473472] Buffer I/O error on device sr0, logical block 6
[69079.473474] Buffer I/O error on device sr0, logical block 7
[69079.473476] Buffer I/O error on device sr0, logical block 8
[69079.473479] Buffer I/O error on device sr0, logical block 9
[69079.479985] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[69079.479988] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[69079.479990] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[69079.479995] end_request: I/O error, dev sr0, sector 0
[69079.544102] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[69079.544107] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[69079.544111] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[69079.544118] end_request: I/O error, dev sr0, sector 0
[69079.545161] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[69079.545163] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[69079.545166] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[69079.545169] end_request: I/O error, dev sr0, sector 0

```

---

