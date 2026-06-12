---
title: "Panasonic UJ-255 USB Blu Ray Issue"
date: 2010-11-07
forum: Mythbuntu
---

### Post by silvanet on 2010-11-07
I just purchased a external Panasonic UJ-255 Blu-Ray Burner and plugged it into my Mythbuntu 10.04 System.  It does not seem to be working correctly.  I am trying to play a regualr DVD.  It seems to recognize that the DVD is there and shows the title on the linux desktop, but not much further than that.  If I plug the UJ-255 into my windows laptop, it works fine there so the issues is not the UJ-255.  My Mythbuntu system alreadys has a dvd player and that works fine as well, it just not playing  external blu ray player.  Any ideas?
 
In syslog I get the following:
Nov  7 17:04:51 myth-main kernel: [ 1424.620015] usb 2-5: new high speed USB device using ehci_hcd and address 5
Nov  7 17:04:51 myth-main kernel: [ 1424.771459] usb 2-5: configuration #1 chosen from 1 choice
Nov  7 17:04:51 myth-main kernel: [ 1424.771825] scsi7 : SCSI emulation for USB Mass Storage devices
Nov  7 17:04:51 myth-main kernel: [ 1424.771929] usb-storage: device found at 5
Nov  7 17:04:51 myth-main kernel: [ 1424.771931] usb-storage: waiting for device to settle before scanning
Nov  7 17:04:56 myth-main kernel: [ 1429.771502] usb-storage: device scan complete
Nov  7 17:04:56 myth-main kernel: [ 1429.773614] scsi 7:0:0:0: CD-ROM            MATSHITA BD-MLT UJ-225S   Q110 PQ: 0 ANSI: 0
Nov  7 17:04:56 myth-main kernel: [ 1429.787400] sr1: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda caddy
Nov  7 17:04:56 myth-main kernel: [ 1429.787528] sr 7:0:0:0: Attached scsi CD-ROM sr1
Nov  7 17:04:56 myth-main kernel: [ 1429.787604] sr 7:0:0:0: Attached scsi generic sg2 type 5
Nov  7 17:07:08 myth-main kernel: [ 1561.847231] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  7 17:07:08 myth-main kernel: [ 1561.847236] sr 7:0:0:0: [sr1] Sense Key : Illegal Request [current]
Nov  7 17:07:08 myth-main kernel: [ 1561.847241] Info fld=0x401
Nov  7 17:07:08 myth-main kernel: [ 1561.847243] sr 7:0:0:0: [sr1] Add. Sense: Read of scrambled sector without authentication
Nov  7 17:07:08 myth-main kernel: [ 1561.847249] sr 7:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
Nov  7 17:07:08 myth-main kernel: [ 1561.847257] end_request: I/O error, dev sr1, sector 4096
Nov  7 17:07:08 myth-main kernel: [ 1561.847261] Buffer I/O error on device sr1, logical block 512
Nov  7 17:07:08 myth-main kernel: [ 1561.849732] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  7 17:07:08 myth-main kernel: [ 1561.849736] sr 7:0:0:0: [sr1] Sense Key : Illegal Request [current]
Nov  7 17:07:08 myth-main kernel: [ 1561.849740] Info fld=0x401
Nov  7 17:07:08 myth-main kernel: [ 1561.849741] sr 7:0:0:0: [sr1] Add. Sense: Read of scrambled sector without authentication
Nov  7 17:07:08 myth-main kernel: [ 1561.849746] sr 7:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
Nov  7 17:07:08 myth-main kernel: [ 1561.849754] end_request: I/O error, dev sr1, sector 4096
Nov  7 17:07:08 myth-main kernel: [ 1561.849757] Buffer I/O error on device sr1, logical block 512
Nov  7 17:07:08 myth-main kernel: [ 1561.852105] sr 7:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  7 17:07:08 myth-main kernel: [ 1561.852109] sr 7:0:0:0: [sr1] Sense Key : Illegal Request [current]
Nov  7 17:07:08 myth-main kernel: [ 1561.852113] Info fld=0x401
Nov  7 17:07:08 myth-main kernel: [ 1561.852114] sr 7:0:0:0: [sr1] Add. Sense: Read of scrambled sector without authentication
Nov  7 17:07:08 myth-main kernel: [ 1561.852119] sr 7:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
Nov  7 17:07:08 myth-main kernel: [ 1561.852127] end_request: I/O error, dev sr1, sector 4096
Nov  7 17:07:08 myth-main kernel: [ 1561.852130] Buffer I/O error on device sr1, logical block 512
Nov  7 17:07:09 myth-main kernel: [ 1562.129124] UDF-fs: Partition marked readonly; forcing readonly mount
Nov  7 17:07:09 myth-main hald: mounted /dev/sr1 on behalf of uid 1000
Nov  7 17:07:09 myth-main kernel: [ 1562.171874] UDF-fs INFO UDF: Mounting volume 'LORD_OF_THE_BEANS', timestamp 2005/09/06 16:35 (1e98)

---

### Post by silvanet on 2010-11-07
I have a resolution.
1)  Setup the Auto-Build [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)
2) configure the Front End to use /dev/sr1 for the dvd player instead of /dev/dvd (in my case, i do not plan on using /dev/sr0 anymore)

---

