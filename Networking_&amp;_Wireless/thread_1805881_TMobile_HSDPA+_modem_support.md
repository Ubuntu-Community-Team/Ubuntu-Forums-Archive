---
title: "TMobile HSDPA+ modem support"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by vipulbhandari82 on 2011-07-16
Hi 

I am running Ubuntu 11.04. When I try to connect t-mobile(USA) modem dongle to my computer, I get this error in dmesg.
My comuter is Lenovo Y460p Core i7 2630M, 8 GB Ram, AMD Graphics. Can provide, if other details are needed.

[ 2131.447343] usb 1-1.3: new high speed USB device using ehci_hcd and address 3
[ 2131.559930] scsi7 : usb-storage 1-1.3:1.0
[ 2132.558215] scsi 7:0:0:0: CD-ROM            T-Mobile USB SCSI CD-ROM  0001 PQ: 0 ANSI: 0
[ 2132.558824] scsi 7:0:0:1: Direct-Access     T-Mobile MMC Storage      0001 PQ: 0 ANSI: 0
[ 2132.561753] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2132.562106] sr 7:0:0:0: Attached scsi CD-ROM sr1
[ 2132.562390] sr 7:0:0:0: Attached scsi generic sg2 type 5
[ 2132.562879] sd 7:0:0:1: Attached scsi generic sg3 type 0
[ 2132.568385] sd 7:0:0:1: [sdb] Attached SCSI removable disk
[ 2132.586818] sr1: CDROM (ioctl) error, command: Get event status notification 4a 01 00 00 10 00 00 00 08 00
[ 2132.586843] sr: Sense Key : Hardware Error [current] 
[ 2132.586851] sr: Add. Sense: No additional sense information
[ 2132.623553] sr1: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
[ 2132.623579] sr: Sense Key : Hardware Error [current] 
[ 2132.623587] sr: Add. Sense: No additional sense information
[ 2498.712286] usb 1-1.3: USB disconnect, address 3
[ 2516.754639] usb 2-1.6: new high speed USB device using ehci_hcd and address 5
[ 2516.867364] scsi8 : usb-storage 2-1.6:1.0
[ 2517.865590] scsi 8:0:0:0: CD-ROM            T-Mobile USB SCSI CD-ROM  0001 PQ: 0 ANSI: 0
[ 2517.866139] scsi 8:0:0:1: Direct-Access     T-Mobile MMC Storage      0001 PQ: 0 ANSI: 0
[ 2517.869661] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2517.870053] sr 8:0:0:0: Attached scsi CD-ROM sr1
[ 2517.870362] sr 8:0:0:0: Attached scsi generic sg2 type 5
[ 2517.870982] sd 8:0:0:1: Attached scsi generic sg3 type 0
[ 2517.880395] sd 8:0:0:1: [sdb] Attached SCSI removable disk
[ 2517.894264] sr1: CDROM (ioctl) error, command: Get event status notification 4a 01 00 00 10 00 00 00 08 00
[ 2517.894293] sr: Sense Key : Hardware Error [current] 
[ 2517.894301] sr: Add. Sense: No additional sense information
[ 2517.936149] sr1: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
[ 2517.936186] sr: Sense Key : Hardware Error [current] 
[ 2517.936197] sr: Add. Sense: No additional sense information

---

### Post by ieee488 on 2011-07-16
I have an older T-mobile mobile broadband USB device.

I have found that it works best when I plug the device in, then boot up the laptop.

---

### Post by vipulbhandari82 on 2011-07-18
Did that too but it didn't work.

---

