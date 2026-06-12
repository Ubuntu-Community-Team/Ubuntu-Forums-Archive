---
title: "Something wrong with my Ipod or Amarok?"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by ssc351 on 2008-04-20
Hi everyone,

I was using gtkpod with my 4g ipod (black and white screen) and i was having problems with it so I thought I would try Amarok.  Now, I am thinking there may be something up with my ipod.  The ipod mounts as either "unknown scsi drive" or "unknown usb drive" in Gnome.  When plugged into the computer the ipod gives the "Do not disconnect" flashing screen and it never goes away.  Also I am running hardy.

Here is my dmesg:

 5623.488610] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 5623.519162] sd 2:0:0:0: [sdb] Spinning up disk.....ready
[ 5625.604004] sd 2:0:0:0: [sdb] 39063023 512-byte hardware sectors (20000 MB)
[ 5625.604999] sd 2:0:0:0: [sdb] Write Protect is off
[ 5625.605007] sd 2:0:0:0: [sdb] Mode Sense: 64 00 00 08
[ 5625.605011] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 5625.607502] sd 2:0:0:0: [sdb] 39063023 512-byte hardware sectors (20000 MB)
[ 5625.608390] sd 2:0:0:0: [sdb] Write Protect is off
[ 5625.608397] sd 2:0:0:0: [sdb] Mode Sense: 64 00 00 08
[ 5625.608401] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 5625.608408]  sdb: sdb1 sdb2
[ 5625.673798] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 5625.673852] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 5658.509756] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5658.509771] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 5658.509779] Info fld=0x0
[ 5658.509781] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 5658.509791] end_request: I/O error, dev sdb, sector 80359
[ 5658.509799] Buffer I/O error on device sdb2, logical block 17
[ 5658.509809] Buffer I/O error on device sdb2, logical block 18
[ 5658.509815] Buffer I/O error on device sdb2, logical block 19
[ 5658.509822] Buffer I/O error on device sdb2, logical block 20
[ 5658.509829] Buffer I/O error on device sdb2, logical block 21
[ 5658.509836] Buffer I/O error on device sdb2, logical block 22
[ 5658.509842] Buffer I/O error on device sdb2, logical block 23
[ 5658.509849] Buffer I/O error on device sdb2, logical block 24
[ 5658.509855] Buffer I/O error on device sdb2, logical block 25
[ 5658.509861] Buffer I/O error on device sdb2, logical block 26
[ 5681.957134] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5681.957144] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 5681.957149] Info fld=0x0
[ 5681.957151] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 5681.957156] end_request: I/O error, dev sdb, sector 80423
[ 5681.957159] printk: 21 messages suppressed.
[ 5681.957163] Buffer I/O error on device sdb2, logical block 49
[ 5681.957169] Buffer I/O error on device sdb2, logical block 50
[ 5681.957172] Buffer I/O error on device sdb2, logical block 51
[ 5681.957176] Buffer I/O error on device sdb2, logical block 52
[ 6418.196690] usb 5-7: USB disconnect, address 2
[ 6480.467972] usb 5-5: new high speed USB device using ehci_hcd and address 3
[ 6480.602173] usb 5-5: configuration #1 chosen from 1 choice
[ 6480.606001] scsi3 : SCSI emulation for USB Mass Storage devices
[ 6480.606326] usb-storage: device found at 3
[ 6480.606330] usb-storage: waiting for device to settle before scanning
[ 6485.603500] usb-storage: device scan complete
[ 6487.480717] scsi 3:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 6485.606791] sd 3:0:0:0: [sdb] 39063023 512-byte hardware sectors (20000 MB)
[ 6485.608041] sd 3:0:0:0: [sdb] Write Protect is off
[ 6485.608046] sd 3:0:0:0: [sdb] Mode Sense: 64 00 00 08
[ 6485.608049] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 6485.610287] sd 3:0:0:0: [sdb] 39063023 512-byte hardware sectors (20000 MB)
[ 6485.611165] sd 3:0:0:0: [sdb] Write Protect is off
[ 6485.611169] sd 3:0:0:0: [sdb] Mode Sense: 64 00 00 08
[ 6485.611171] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 6485.611175]  sdb: sdb1 sdb2
[ 6485.684320] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 6485.684376] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 6524.648062] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6524.648077] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6524.648085] Info fld=0x0
[ 6524.648088] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6524.648099] end_request: I/O error, dev sdb, sector 80423
[ 6524.648104] printk: 59 messages suppressed.
[ 6524.648126] Buffer I/O error on device sdb2, logical block 49
[ 6524.648136] Buffer I/O error on device sdb2, logical block 50
[ 6524.648143] Buffer I/O error on device sdb2, logical block 51
[ 6524.648152] Buffer I/O error on device sdb2, logical block 52
[ 6524.648159] Buffer I/O error on device sdb2, logical block 53
[ 6524.648165] Buffer I/O error on device sdb2, logical block 54
[ 6524.648171] Buffer I/O error on device sdb2, logical block 55
[ 6524.648177] Buffer I/O error on device sdb2, logical block 56
[ 6524.648183] Buffer I/O error on device sdb2, logical block 57
[ 6524.648189] Buffer I/O error on device sdb2, logical block 58
[ 6546.971539] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6546.971548] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6546.971554] Info fld=0x0
[ 6546.971555] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6546.971560] end_request: I/O error, dev sdb, sector 80663
[ 6546.971564] printk: 110 messages suppressed.
[ 6546.971569] Buffer I/O error on device sdb2, logical block 169
[ 6546.971577] Buffer I/O error on device sdb2, logical block 170
[ 6546.971580] Buffer I/O error on device sdb2, logical block 171
[ 6546.971584] Buffer I/O error on device sdb2, logical block 172
[ 6582.372466] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6582.372476] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6582.372481] Info fld=0x0
[ 6582.372484] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6582.372490] end_request: I/O error, dev sdb, sector 80365
[ 6582.372493] printk: 67 messages suppressed.
[ 6582.372497] Buffer I/O error on device sdb2, logical block 20
[ 6582.372504] Buffer I/O error on device sdb2, logical block 21
[ 6582.372508] Buffer I/O error on device sdb2, logical block 22
[ 6582.372512] Buffer I/O error on device sdb2, logical block 23
[ 6582.372519] Buffer I/O error on device sdb2, logical block 24
[ 6582.372523] Buffer I/O error on device sdb2, logical block 25
[ 6582.372527] Buffer I/O error on device sdb2, logical block 26
[ 6762.513807] Uhhuh. NMI received for unknown reason a1 on CPU 0.
[ 6762.513817] You have some hardware problem, likely on the PCI bus.
[ 6762.513820] Dazed and confused, but trying to continue
[ 7211.649487] usb 5-5: USB disconnect, address 3
[ 7505.571464] usb 5-5: new high speed USB device using ehci_hcd and address 4
[ 7503.827839] usb 5-5: configuration #1 chosen from 1 choice
[ 7503.828413] scsi4 : SCSI emulation for USB Mass Storage devices
[ 7503.828891] usb-storage: device found at 4
[ 7503.828900] usb-storage: waiting for device to settle before scanning
[ 7508.824371] usb-storage: device scan complete
[ 7508.825277] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 7508.834344] sd 4:0:0:0: [sdb] 39063023 512-byte hardware sectors (20000 MB)
[ 7508.835331] sd 4:0:0:0: [sdb] Write Protect is off
[ 7508.835336] sd 4:0:0:0: [sdb] Mode Sense: 64 00 00 08
[ 7508.835338] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 7508.837453] sd 4:0:0:0: [sdb] 39063023 512-byte hardware sectors (20000 MB)
[ 7510.714847] sd 4:0:0:0: [sdb] Write Protect is off
[ 7510.714852] sd 4:0:0:0: [sdb] Mode Sense: 64 00 00 08
[ 7510.714855] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 7510.714860]  sdb: sdb1 sdb2
[ 7510.789330] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 7510.789382] sd 4:0:0:0: Attached scsi generic sg2 type 0

---

### Post by ssc351 on 2008-04-22
anyone anyone?

---

### Post by ssc351 on 2008-04-23
Come on guys, someone must be able to help me out...also i should be more specific, its a 4th generation ipod not a 4gb.

---

