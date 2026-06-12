---
title: "Problem mounting Nokia CS-17 wireless modem"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by cimex on 2011-01-11
Hi,

I'm trying to cmount a Nokia CS-17 wireless modem on Lubuntu 10.10, but it doesn't seem to mount. When I run dmesg I get:

[  994.384164] usb 1-5: new high speed USB device using ehci_hcd and address 9
[  994.531675] scsi9 : usb-storage 1-5:1.0
[  995.537078] scsi 9:0:0:0: CD-ROM            Nokia    Datacard CD-ROM  0001 PQ: 0 ANSI: 0
[  995.544792] sr1: scsi3-mmc drive: 0x/0x caddy
[  995.545147] sr 9:0:0:0: Attached scsi CD-ROM sr1
[  995.545346] sr 9:0:0:0: Attached scsi generic sg2 type 5
[  995.573419] sr1: CDROM (ioctl) error, command: Get event status notification 4a 01 00 00 10 00 00 00 08 00
[  995.573453] sr: Sense Key : Hardware Error [current] 
[  995.573465] sr: Add. Sense: No additional sense information
[  996.795719] sr1: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
[  996.795752] sr: Sense Key : Hardware Error [current] 
[  996.795763] sr: Add. Sense: No additional sense information

---

### Post by jb68 on 2011-01-12
Hi,
I have the same error with Nokia CS-18

 12 20:30:55 jb-laptop kernel: [ 1787.941768] scsi9 : SCSI emulation for USB Mass Storage devices
Jan 12 20:31:00 jb-laptop kernel: [ 1792.940865] scsi 9:0:0:0: CD-ROM            Nokia    Datacard CD-ROM  0001 PQ: 0 ANSI: 0
Jan 12 20:31:00 jb-laptop kernel: [ 1792.941376] scsi 9:0:0:1: Direct-Access     Nokia    Datacard CD-ROM  0001 PQ: 0 ANSI: 0
Jan 12 20:31:00 jb-laptop kernel: [ 1792.944943] sr0: scsi3-mmc drive: 0x/0x caddy
Jan 12 20:31:00 jb-laptop kernel: [ 1792.945681] sr 9:0:0:0: Attached scsi generic sg1 type 5
Jan 12 20:31:00 jb-laptop kernel: [ 1792.946637] sd 9:0:0:1: Attached scsi generic sg2 type 0
Jan 12 20:31:00 jb-laptop kernel: [ 1792.952945] sd 9:0:0:1: [sdb] Attached SCSI removable disk
Jan 12 20:31:00 jb-laptop kernel: [ 1792.975473] sr: Sense Key : Hardware Error [current] 
Jan 12 20:31:00 jb-laptop kernel: [ 1792.975479] sr: Add. Sense: No additional sense information

---

### Post by alexfish on 2011-01-13
hi

ensure the system has latest usb_modeswitch

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

this is the listing from latest device_reference

[COLOR=Blue]#######################################################
# Nokia CS-17
#
# Contributor: Juho Frits

;DefaultVendor= 0x0421
;DefaultProduct=0x0622

;TargetVendor=  0x0421
;TargetProduct= 0x0623

;MessageContent="5553424312345678000000000000061b000000020000000000000000000000"


#######################################################[/COLOR]

if using this , remove the ";"

can try usb_modeswitch directly with the above info 

also if there is no listing in the /etc/usb_modeswitch.d

or make a file in the /etc/usb_modeswitch.d

**code:**

[COLOR=Blue]sudo gedit /etc/usb_modeswtch.d/0421:0622[/COLOR]

paste the contents of the above , don't forget to remove the "[COLOR=Blue] ;[/COLOR] "

---

### Post by alexfish on 2011-01-13
> **jb68 said:**
> Hi,
I have the same error with Nokia CS-18

 12 20:30:55 jb-laptop kernel: [ 1787.941768] scsi9 : SCSI emulation for USB Mass Storage devices
Jan 12 20:31:00 jb-laptop kernel: [ 1792.940865] scsi 9:0:0:0: CD-ROM            Nokia    Datacard CD-ROM  0001 PQ: 0 ANSI: 0
Jan 12 20:31:00 jb-laptop kernel: [ 1792.941376] scsi 9:0:0:1: Direct-Access     Nokia    Datacard CD-ROM  0001 PQ: 0 ANSI: 0
Jan 12 20:31:00 jb-laptop kernel: [ 1792.944943] sr0: scsi3-mmc drive: 0x/0x caddy
Jan 12 20:31:00 jb-laptop kernel: [ 1792.945681] sr 9:0:0:0: Attached scsi generic sg1 type 5
Jan 12 20:31:00 jb-laptop kernel: [ 1792.946637] sd 9:0:0:1: Attached scsi generic sg2 type 0
Jan 12 20:31:00 jb-laptop kernel: [ 1792.952945] sd 9:0:0:1: [sdb] Attached SCSI removable disk
Jan 12 20:31:00 jb-laptop kernel: [ 1792.975473] sr: Sense Key : Hardware Error [current] 
Jan 12 20:31:00 jb-laptop kernel: [ 1792.975479] sr: Add. Sense: No additional sense information


Hi

 as for CS18, here is the listing:

[COLOR=Blue]#######################################################
# Nokia CS-18
#
# Contributor: Thomas Behan

DefaultVendor= 0x0421[/COLOR] [COLOR=Blue]
DefaultProduct=0x0627

TargetVendor=  0x0421[/COLOR] [COLOR=Blue]
TargetProduct= 0x0612

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"[/COLOR] [COLOR=Blue]

#######################################################[/COLOR]

---

