---
title: "Pinnacle PCTV 300i analog + DVB-T"
date: 2010-02-04
forum: Multimedia Software
---

### Post by lospo on 2010-02-04
Good morning to all of you!

Does th Pinnacle 300i PCTV works under ubuntu (and  mythbuntu)??

Is there some strange congigs?

Thank you!!!

---

### Post by lospo on 2010-02-05
no one know? :(

---

### Post by xc3RnbFO8P on 2010-02-05
Read this:
[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_(310i)]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_(310i)")
In Terminal show the output of:
> dmesg

---

### Post by lospo on 2010-02-05
that's the output:

> 
[    1.340274] hub 1-0:1.0: unable to enumerate USB device on port 4
[    1.353501]  sda1 sda2 < sda5 sda6 sda7 > sda3
[    1.387119] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.650291] ata2: SATA link down (SStatus 0 SControl 300)
[    1.650343] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    1.650422] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.651006] sd 2:0:0:0: [sdb] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    1.651035] sd 2:0:0:0: [sdb] Write Protect is off
[    1.651037] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.651052] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.651129]  sdb: sdb1 sdb2 <
[    1.674525] scsi 2:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-111D 1.23 PQ: 0 ANSI: 5
[    1.692150]  sdb5 >
[    1.698565] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.710984] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.710987] Uniform CD-ROM driver Revision: 3.20
[    1.711042] sr 2:0:1:0: Attached scsi CD-ROM sr0
[    1.711074] sr 2:0:1:0: Attached scsi generic sg2 type 5
[    1.711100] ata4: port disabled. ignoring.
[    1.711126] Freeing unused kernel memory: 660k freed
[    1.711412] Write protecting the kernel read-only data: 7596k
[    1.858291] usb 2-3: new full speed USB device using ohci_hcd and address 2
[    1.882173] Initializing USB Mass Storage driver...
[    1.882262] scsi4 : SCSI emulation for USB Mass Storage devices
[    1.882327] usbcore: registered new interface driver usb-storage
[    1.882329] USB Mass Storage support registered.
[    1.882434] usb-storage: device found at 2
[    1.882435] usb-storage: waiting for device to settle before scanning
[    2.287102] usb 2-3: configuration #1 chosen from 1 choice
[    2.620021] usb 2-4: new full speed USB device using ohci_hcd and address 3
[    2.762828] xor: automatically using best checksumming function: generic_sse
[    2.812516]    generic_sse:  9112.800 MB/sec
[    2.812518] xor: using function: generic_sse (9112.800 MB/sec)
[    2.814593] device-mapper: dm-raid45: initialized v0.2594b
[    2.847038] usb 2-4: not running at top speed; connect to a high speed hub
[    2.865135] usb 2-4: configuration #1 chosen from 1 choice
[    3.167901] PM: Starting manual resume from disk
[    3.167905] PM: Resume from partition 8:21
[    3.167907] PM: Checking hibernation image.
[    3.168153] PM: Resume from disk failed.
[    3.202369] kjournald starting.  Commit interval 5 seconds
[    3.202377] EXT3-fs: mounted filesystem with writeback data mode.
[    4.554807] type=1505 audit(1265364395.427:2): operation="profile_load" pid=464 name=/usr/share/gdm/guest-session/Xsession
[    4.596644] type=1505 audit(1265364395.467:3): operation="profile_load" pid=465 name=/sbin/dhclient3
[    4.596852] type=1505 audit(1265364395.467:4): operation="profile_load" pid=465 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.596970] type=1505 audit(1265364395.467:5): operation="profile_load" pid=465 name=/usr/lib/connman/scripts/dhclient-script
[    4.769799] type=1505 audit(1265364395.638:6): operation="profile_load" pid=466 name=/usr/bin/evince
[    4.773330] type=1505 audit(1265364395.647:7): operation="profile_load" pid=466 name=/usr/bin/evince-previewer
[    4.775404] type=1505 audit(1265364395.647:8): operation="profile_load" pid=466 name=/usr/bin/evince-thumbnailer
[    4.803118] type=1505 audit(1265364395.677:9): operation="profile_load" pid=468 name=/usr/lib/cups/backend/cups-pdf
[    4.803375] type=1505 audit(1265364395.677:10): operation="profile_load" pid=468 name=/usr/sbin/cupsd
[    6.870156] usb-storage: device scan complete
[    6.870517] scsi 4:0:0:0: Direct-Access     USB2.0   CardReader CF    0100 PQ: 0 ANSI: 0
[    6.870882] scsi 4:0:0:1: Direct-Access     USB2.0   CardReader SM XD 0100 PQ: 0 ANSI: 0
[    6.871258] scsi 4:0:0:2: Direct-Access     USB2.0   CardReader MS    0100 PQ: 0 ANSI: 0
[    6.871632] scsi 4:0:0:3: Direct-Access     USB2.0   CardReader SD    0100 PQ: 0 ANSI: 0
[    6.872001] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    6.872065] sd 4:0:0:1: Attached scsi generic sg4 type 0
[    6.872128] sd 4:0:0:2: Attached scsi generic sg5 type 0
[    6.872194] sd 4:0:0:3: Attached scsi generic sg6 type 0
[    6.875972] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    6.876624] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[    6.877379] sd 4:0:0:2: [sde] Attached SCSI removable disk
[    6.878130] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[   24.932462] udev: starting version 147
[   25.168244] nvidia: module license 'NVIDIA' taints kernel.
[   25.168248] Disabling lock debugging due to kernel taint
[   25.345607] EDAC MC: Ver: 2.1.0 Jan  8 2010
[   25.373359] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.420032] Linux video capture interface: v2.00
[   25.424246] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   25.424263] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xd800
[   25.426454] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   25.428348] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 20
[   25.428355]   alloc irq_desc for 20 on node 0
[   25.428357]   alloc kstat_irqs on node 0
[   25.428364] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 20 (level, low) -> IRQ 20
[   25.428369] nvidia 0000:00:0d.0: setting latency timer to 64
[   25.428576] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   25.439006] saa7130/34: v4l2 driver version 0.2.15 loaded
[   25.439405] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   25.439410]   alloc irq_desc for 16 on node 0
[   25.439412]   alloc kstat_irqs on node 0
[   25.439419] saa7134 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   25.439424] saa7134[0]: found at 0000:01:06.0, rev: 1, irq: 16, latency: 32, mmio: 0xf5008000
[   25.439429] saa7134[0]: subsystem: 11bd:002d, board: Pinnacle PCTV 300i DVB-T + PAL [card=50,autodetected]
[   25.439446] saa7134[0]: board init: gpio is c806000
[   25.439463] IRQ 16/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   25.444915] lp: driver loaded but no devices found
[   25.466102] parport_pc 00:09: reported by Plug and Play ACPI
[   25.466146] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   25.470999] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   25.471120] usbcore: registered new interface driver btusb
[   25.475029] ppdev: user-space parallel port driver
[   25.477065] EDAC amd64_edac:  Ver: 3.2.0 Jan  8 2010
[   25.477158] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   25.477161] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   25.477163] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   25.477164]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   25.477165]     Might be a BIOS bug, if BIOS says ECC is enabled
[   25.477166]     Use of the override can cause unknown side effects.
[   25.477190] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   25.480202] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5617
[   25.480227] usbcore: registered new interface driver usblp
[   25.488081] usbcore: registered new interface driver wacom
[   25.488085] wacom: v1.51:USB Wacom Graphire and Wacom Intuos tablet driver
[   25.551269] lp0: using parport0 (interrupt-driven).
[   25.559689] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   25.559695] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   25.559727] HDA Intel 0000:00:05.0: setting latency timer to 64
[   25.604974] cfg80211: Calling CRDA to update world regulatory domain
[   25.630022] saa7134[0]: i2c eeprom 00: bd 11 2d 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[   25.630030] saa7134[0]: i2c eeprom 10: 00 f0 04 04 ff 20 ff ff ff ff ff ff ff ff ff ff
[   25.630037] saa7134[0]: i2c eeprom 20: 01 40 01 02 03 ff 03 01 08 ff 00 25 ff ff ff ff
[   25.630043] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.630049] saa7134[0]: i2c eeprom 40: ff 16 00 c0 86 3c 01 01 ff ff ff ff ff ff ff ff
[   25.630056] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.630062] saa7134[0]: i2c eeprom 60: 0c 22 17 44 02 a7 06 a7 ff ff ff ff ff ff ff ff
[   25.630068] saa7134[0]: i2c eeprom 70: 00 30 8d 16 4c 80 ff ff 74 8c ff ff ff ff ff ff
[   25.630074] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.630080] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.630086] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.630092] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.630098] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.630105] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.630111] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.630117] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.630126] i2c-adapter i2c-2: Invalid 7-bit address 0x7a
[   25.637162] cfg80211: World regulatory domain updated:
[   25.637165]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.637168]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.637170]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.637172]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.637173]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.637175]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.756964] EXT3 FS on sdb1, internal journal
[   25.890098] tuner 2-0043: chip found @ 0x86 (saa7134[0])
[   25.895219] tda9887 2-0043: creating new instance
[   25.895223] tda9887 2-0043: tda988[5/6/7] found
[   25.970022] Chip ID is not zero. It is not a TEA5767
[   25.970084] tuner 2-0060: chip found @ 0xc0 (saa7134[0])
[   26.030011] mt20xx 2-0060: microtune: companycode=3cbf part=42 rev=2f
[   26.110109] mt20xx 2-0060: microtune MT2050 found, OK
[   26.191038] __ratelimit: 6 callbacks suppressed
[   26.191042] type=1505 audit(1265360817.057:13): operation="profile_replace" pid=1313 name=/usr/share/gdm/guest-session/Xsession
[   26.192562] type=1505 audit(1265360817.067:14): operation="profile_replace" pid=1314 name=/sbin/dhclient3
[   26.192772] type=1505 audit(1265360817.067:15): operation="profile_replace" pid=1314 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   26.192897] type=1505 audit(1265360817.067:16): operation="profile_replace" pid=1314 name=/usr/lib/connman/scripts/dhclient-script
[   26.196620] type=1505 audit(1265360817.067:17): operation="profile_replace" pid=1315 name=/usr/bin/evince
[   26.200211] type=1505 audit(1265360817.067:18): operation="profile_replace" pid=1315 name=/usr/bin/evince-previewer
[   26.202314] type=1505 audit(1265360817.067:19): operation="profile_replace" pid=1315 name=/usr/bin/evince-thumbnailer
[   26.207220] type=1505 audit(1265360817.077:20): operation="profile_replace" pid=1317 name=/usr/lib/cups/backend/cups-pdf
[   26.207479] type=1505 audit(1265360817.077:21): operation="profile_replace" pid=1317 name=/usr/sbin/cupsd
[   26.266212] type=1505 audit(1265360817.137:22): operation="profile_replace" pid=1318 name=/usr/sbin/mysqld
[   26.273082] saa7134[0]: registered device video0 [v4l2]
[   26.273104] saa7134[0]: registered device vbi0
[   26.273633] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   26.273639]   alloc irq_desc for 17 on node 0
[   26.273640]   alloc kstat_irqs on node 0
[   26.273648] rt61pci 0000:01:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   26.278141] saa7134 ALSA driver for DMA sound loaded
[   26.278154] IRQ 16/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   26.278173] saa7134[0]/alsa: saa7134[0] at 0xf5008000 irq 16 registered as card -2
[   26.295100] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   26.316159] phy0: Selected rate control algorithm 'minstrel'
[   26.316703] Registered led device: rt61pci-phy0::radio
[   26.316717] Registered led device: rt61pci-phy0::assoc
[   26.331067] rt61pci 0000:01:07.0: firmware: requesting rt2561s.bin
[   26.362621] dvb_init() allocating 1 frontend
[   26.410883] DVB: registering new adapter (saa7134[0])
[   26.410891] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...
[   26.462942] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.020086] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input5
[   27.683792] kjournald starting.  Commit interval 5 seconds
[   27.683798] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[   27.683933] EXT3 FS on sda6, internal journal
[   27.683936] EXT3-fs: mounted filesystem with writeback data mode.
[   27.712843] EXT4-fs (sda3): barriers enabled
[   27.726336] kjournald2 starting: pid 1837, dev sda3:8, commit interval 5 seconds
[   27.726390] EXT4-fs (sda3): warning: maximal mount count reached, running e2fsck is recommended
[   27.726499] EXT4-fs (sda3): internal journal on sda3:8
[   27.726501] EXT4-fs (sda3): delayed allocation enabled
[   27.726503] EXT4-fs: file extents enabled
[   27.731148] EXT4-fs: mballoc enabled
[   27.731162] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   28.042582] usplash:390 freeing invalid memtype ffffffffe0000000-ffffffffe4000000
[   29.356429] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   29.356432] vboxdrv: Successfully done.
[   29.356434] vboxdrv: Found 2 processor cores.
[   29.356486] VBoxDrv: dbg - g_abExecMemory=ffffffffa0cfd480
[   29.356500] vboxdrv: fAsync=1 offMin=0x2fa23e offMax=0x2fa23e
[   29.356544] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   29.356546] vboxdrv: Successfully loaded version 3.0.12 (interface 0x00110000).
[   29.596250] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0e9c220
[   29.598449] VBoxNetAdp: dbg - g_abExecMemory=ffffffffa0eb5b20
[   29.685610] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.685612] Bluetooth: BNEP filters: protocol multicast
[   29.697597] Bridge firewalling registered
[   31.530463] usb 2-4: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   34.752558] wlan0: authenticate with AP 00:04:0e:d2:72:c8
[   34.754236] wlan0: authenticated
[   34.754237] wlan0: associate with AP 00:04:0e:d2:72:c8
[   34.761802] wlan0: RX AssocResp from 00:04:0e:d2:72:c8 (capab=0x411 status=0 aid=1)
[   34.761804] wlan0: associated
[   34.762356] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.781313] Intel AES-NI instructions are not detected.
[   34.820900] padlock: VIA PadLock not detected.
[   44.890011] wlan0: no IPv6 routers present
[   93.002536] Clocksource tsc unstable (delta = -165568952 ns)
[ 3371.431156] usblp0: removed
lospo@bobogrigio:~$



---

### Post by xc3RnbFO8P on 2010-02-05
> DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...
Install **Kaffeine** and scan for channels, you will find it in
Synaptic Package Manager.

---

### Post by lospo on 2010-02-08
> **Ringi said:**
> Install **Kaffeine** and scan for channels, you will find it in
Synaptic Package Manager.


Thank you so much, but i've read that Kaffeine is for KDE, not for Gnome. Is there something working for gnome????

Thanks!

---

### Post by xc3RnbFO8P on 2010-02-08
**Kaffeine** works fine in Gnome.
You can also install **Me-TV**.

---

### Post by lospo on 2010-02-09
> **Ringi said:**
> **Kaffeine** works fine in Gnome.
You can also install **Me-TV**.

Sounds better than Kaffeine, i will try it ! Thanks

---

