---
title: "Looking for help with MTP/MSC mp3 player connection"
date: 2009-02-27
forum: Multimedia Software
---

### Post by inspired on 2009-02-27
Hi folks,
I have spent have the day today trying to figure out how to get a Sandisk Sansa e280 (v.1) to operate correctly (reliably) with Ubuntu 8.10

I have read more posts and threads than I care to count. Most seem to date back to 2006 - 2007, and often refer to things that aren't directly applicable any more, like installing libmtp where in fact I find I have libmtp8 installed and libmtp is not available. That's a small example.

I would like to sort this out and would appreciate the help of someone who knows how to pinpoint hardware, usb, and mounting issues.

I would like to use the device in MTP mode if possible (and I read that it is possible) because then the player does not have to restart and refresh its database every time it is connected and disconnected.

I have installed a range of MTP and MSC related things.

Here is what happens so far:
1) If I plug connect in MSC mode it connects and two mounts (one for device, one for microSD card) appear. I can access these in Nautilus and change files etc.
When I try to access the device via any of the media apps that support devices, it disconnects and the app will typically hang (Banshee, for example, will show the both drives of the sansa but immediately the device disconnects and banshee becomes unresponsive). It has extensions that allow it to access all kinds of media devices (MTP, MSC, iPod, etc.) as far as I can tell.

2) If I put the device into MTP mode and plug it in, the device shows it is connected but nothing happens on Ubuntu. There is a log entry as follows:
```
Feb 27 14:14:27 jonathan-ubuntu kernel: [19862.900792] usb 4-1: new full speed USB device using uhci_hcd and address 4
Feb 27 14:14:28 jonathan-ubuntu kernel: [19863.865441] usb 4-1: configuration #128 chosen from 1 choice
```]

Following instructions [here]("http://www.micahcarrick.com/05-21-2008/sansa-view-ubuntu.html") I tried manually mounting it using: 
```
sudo mtpfs -o allow_other /media/Sansa
```
That gives me a mount point to the drive, but it was really not reliable. After a few seconds of viewing the device in Nautilus it is no longer accessible. Gives the following error:
```
**Could not display "/media/sansa".**
Error: Error stating file '/media/sansa': Transport endpoint is not connected
Please select another viewer and try again.
```
Still shows as a mount though, but not accessible. Had to manually unmount it.

Oddly, I have no issues accessing the device over MSC using Mediamonkey which I installed into Wine. It was reported (by other MM wine users) that there would be no device support in a wine installation of MM, but I managed to get that working fine. I want, however, to get it working with my linux media apps.

If I run Qlix it does not work. Nothing appears. Program self terminates before loading to a point where I can see it. OR it might load up and then lock up. If I start Qlix before connecting device in MTP mode, and then connect it whilst it is running (it's asking me to connect a device) nothing happens and Qlix can't be closed normally... becomes unresponsive and must be forced to close.

If I run syncropated!, it's the same story...nothing happens at all.

So I am not sure what to do. I've read about and tried a lot of things. Where to start?

Below is some system log data from the last while of trying to access the device.

Any help would be great. Thanks.

Jonathan

UPDATE: I have found that Amarok is able to handle the MSC mounts without locking up or causing the mounts to unmount. I have tried (ignore those without device support, just listing everything I have and tried) BMPx, Rhythmbox, Exaile, Banshee, Gnomad 2 (fine if microSD not inserted), and others. 
Syslog
```
Feb 27 14:04:31 jonathan-ubuntu kernel: [19266.544282] usb 4-1: USB disconnect, address 2
Feb 27 14:04:44 jonathan-ubuntu kernel: [19280.148085] usb 4-1: new full speed USB device using uhci_hcd and address 3
Feb 27 14:04:45 jonathan-ubuntu kernel: [19281.165149] usb 4-1: configuration #128 chosen from 1 choice
Feb 27 14:04:45 jonathan-ubuntu kernel: [19281.236089] scsi15 : SCSI emulation for USB Mass Storage devices
Feb 27 14:04:45 jonathan-ubuntu kernel: [19281.239919] usb-storage: device found at 3
Feb 27 14:04:45 jonathan-ubuntu kernel: [19281.239928] usb-storage: waiting for device to settle before scanning
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.238107] usb-storage: device scan complete
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.241278] scsi 15:0:0:0: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.244130] scsi 15:0:0:1: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.269063] sd 15:0:0:0: [sdd] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.276139] sd 15:0:0:0: [sdd] Write Protect is off
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.276149] sd 15:0:0:0: [sdd] Mode Sense: 45 00 00 00
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.276152] sd 15:0:0:0: [sdd] Assuming drive cache: write through
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.321181] sd 15:0:0:0: [sdd] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.324184] sd 15:0:0:0: [sdd] Write Protect is off
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.324191] sd 15:0:0:0: [sdd] Mode Sense: 45 00 00 00
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.324195] sd 15:0:0:0: [sdd] Assuming drive cache: write through
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.324678]  sdd: sdd1 sdd2
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.341163] sd 15:0:0:0: [sdd] Attached SCSI removable disk
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.341610] sd 15:0:0:0: Attached scsi generic sg3 type 0
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.355786] sd 15:0:0:1: [sde] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.362656] sd 15:0:0:1: [sde] Write Protect is off
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.362665] sd 15:0:0:1: [sde] Mode Sense: 45 00 00 00
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.362669] sd 15:0:0:1: [sde] Assuming drive cache: write through
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.373046] sd 15:0:0:1: [sde] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.376085] sd 15:0:0:1: [sde] Write Protect is off
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.376092] sd 15:0:0:1: [sde] Mode Sense: 45 00 00 00
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.376095] sd 15:0:0:1: [sde] Assuming drive cache: write through
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.376602]  sde: sde1
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.385170] sd 15:0:0:1: [sde] Attached SCSI removable disk
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.385655] sd 15:0:0:1: Attached scsi generic sg4 type 0
Feb 27 14:04:53 jonathan-ubuntu hald: mounted /dev/sdd1 on behalf of uid 1000
Feb 27 14:04:58 jonathan-ubuntu hald: mounted /dev/sde1 on behalf of uid 1000
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.913208] __ratelimit: 118 callbacks suppressed
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.913217] Buffer I/O error on device sdd1, logical block 30577
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.913222] lost page write due to I/O error on sdd1
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927097] Buffer I/O error on device sde1, logical block 275601
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927107] lost page write due to I/O error on sde1
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927874] Buffer I/O error on device sde1, logical block 413063
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927880] lost page write due to I/O error on sde1
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927885] Buffer I/O error on device sde1, logical block 413064
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927888] lost page write due to I/O error on sde1
Feb 27 14:07:29 jonathan-ubuntu hald[5965]: forcibly attempting to lazy unmount /dev/sdd1 as enclosing drive was disconnected
Feb 27 14:07:29 jonathan-ubuntu kernel: [19445.030104] scsi 15:0:0:0: rejecting I/O to dead device
Feb 27 14:07:29 jonathan-ubuntu hald: unmounted /dev/sdd1 from '/media/Sansa e280' on behalf of uid 0
Feb 27 14:07:29 jonathan-ubuntu hald[5965]: forcibly attempting to lazy unmount /dev/sde1 as enclosing drive was disconnected
Feb 27 14:07:29 jonathan-ubuntu kernel: [19445.459727] scsi 15:0:0:1: rejecting I/O to dead device
Feb 27 14:07:29 jonathan-ubuntu hald: unmounted /dev/sde1 from '/media/SANSA MSD' on behalf of uid 0
Feb 27 14:07:39 jonathan-ubuntu kernel: [19455.060043] usb 4-1: reset full speed USB device using uhci_hcd and address 3
Feb 27 14:07:39 jonathan-ubuntu kernel: [19455.252029] scsi16 : SCSI emulation for USB Mass Storage devices
Feb 27 14:07:39 jonathan-ubuntu kernel: [19455.280142] usb-storage: device found at 3
Feb 27 14:07:39 jonathan-ubuntu kernel: [19455.280148] usb-storage: waiting for device to settle before scanning
Feb 27 14:09:20 jonathan-ubuntu kernel: [19555.748081] usb 4-1: reset full speed USB device using uhci_hcd and address 3
Feb 27 14:09:20 jonathan-ubuntu kernel: [19555.918373] scsi17 : SCSI emulation for USB Mass Storage devices
Feb 27 14:09:20 jonathan-ubuntu kernel: [19555.940295] usb-storage: device found at 3
Feb 27 14:09:20 jonathan-ubuntu kernel: [19555.940309] usb-storage: waiting for device to settle before scanning
Feb 27 14:09:41 jonathan-ubuntu kernel: [19577.216087] usb 4-1: reset full speed USB device using uhci_hcd and address 3
Feb 27 14:09:41 jonathan-ubuntu kernel: [19577.392449] scsi18 : SCSI emulation for USB Mass Storage devices
Feb 27 14:09:41 jonathan-ubuntu kernel: [19577.416166] usb-storage: device found at 3
Feb 27 14:09:41 jonathan-ubuntu kernel: [19577.416180] usb-storage: waiting for device to settle before scanning
Feb 27 14:11:31 jonathan-ubuntu kernel: [19686.904117] usb 4-1: USB disconnect, address 3
Feb 27 14:14:27 jonathan-ubuntu kernel: [19862.900792] usb 4-1: new full speed USB device using uhci_hcd and address 4
Feb 27 14:14:28 jonathan-ubuntu kernel: [19863.865441] usb 4-1: configuration #128 chosen from 1 choice
Feb 27 14:17:01 jonathan-ubuntu /USR/SBIN/CRON[2738]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 27 14:22:29 jonathan-ubuntu kernel: [20344.856067] usb 4-1: reset full speed USB device using uhci_hcd and address 4
Feb 27 14:24:21 jonathan-ubuntu kernel: [20456.944100] usb 4-1: USB disconnect, address 4
Feb 27 14:25:04 jonathan-ubuntu kernel: [20500.212075] usb 4-1: new full speed USB device using uhci_hcd and address 5
Feb 27 14:25:05 jonathan-ubuntu kernel: [20501.337605] usb 4-1: configuration #128 chosen from 1 choice
Feb 27 14:26:12 jonathan-ubuntu kernel: [20568.221261] nautilus[23878]: segfault at 4a000018 ip b7604c46 sp bfa25b30 error 4 in libgconf-2.so.4.1.5[b75e4000+2e000]
Feb 27 14:27:14 jonathan-ubuntu kernel: [20630.052074] usb 4-1: USB disconnect, address 5
```
User log
```
Feb 27 09:42:23 jonathan-ubuntu usbmount[13119]: cannot acquire lock /var/run/usbmount/.mount.lock
```
Auth.log
```
Feb 27 13:03:40 jonathan-ubuntu sudo: jonathan : TTY=pts/1 ; PWD=/ ; USER=root ; COMMAND=/usr/bin/mtpfs -o allow_other /media/sansa
Feb 27 13:06:37 jonathan-ubuntu sudo: jonathan : TTY=pts/1 ; PWD=/ ; USER=root ; COMMAND=/usr/bin/mtpfs -o allow_other /media/sansa
Feb 27 13:08:41 jonathan-ubuntu sudo: jonathan : TTY=pts/1 ; PWD=/ ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
Feb 27 13:10:25 jonathan-ubuntu sudo: jonathan : TTY=pts/1 ; PWD=/ ; USER=root ; COMMAND=/sbin/modprobe -r ehci_hcd
Feb 27 13:10:34 jonathan-ubuntu sudo: jonathan : TTY=pts/1 ; PWD=/ ; USER=root ; COMMAND=/sbin/modprobe
Feb 27 13:17:01 jonathan-ubuntu CRON[31468]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 27 13:17:01 jonathan-ubuntu CRON[31468]: pam_unix(cron:session): session closed for user root
Feb 27 13:46:49 jonathan-ubuntu gnome-keyring-daemon[6532]: adding removable location: volume_label_Hyperhealth_Pro at /media/cdrom0
Feb 27 14:04:11 jonathan-ubuntu sudo: jonathan : TTY=pts/1 ; PWD=/ ; USER=root ; COMMAND=/bin/fusermount -u /media/sansa
Feb 27 14:04:54 jonathan-ubuntu gnome-keyring-daemon[6532]: adding removable location: volume_uuid_3499_B0D9 at /media/Sansa e280
Feb 27 14:04:58 jonathan-ubuntu gnome-keyring-daemon[6532]: adding removable location: volume_uuid_3030_3764 at /media/SANSA MSD
Feb 27 14:07:29 jonathan-ubuntu gnome-keyring-daemon[6532]: removing removable location: volume_uuid_3499_B0D9
Feb 27 14:07:29 jonathan-ubuntu gnome-keyring-daemon[6532]: removing removable location: volume_uuid_3030_3764
Feb 27 14:17:01 jonathan-ubuntu CRON[2729]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 27 14:17:01 jonathan-ubuntu CRON[2729]: pam_unix(cron:session): session closed for user root
Feb 27 14:19:03 jonathan-ubuntu sudo: jonathan : TTY=pts/1 ; PWD=/ ; USER=root ; COMMAND=/usr/bin/mtpfs -o allow_other /media/SansaView
Feb 27 14:19:10 jonathan-ubuntu sudo: jonathan : TTY=pts/1 ; PWD=/ ; USER=root ; COMMAND=/usr/bin/mtpfs -o allow_other /media/sansa
Feb 27 14:22:28 jonathan-ubuntu sudo: jonathan : TTY=pts/1 ; PWD=/ ; USER=root ; COMMAND=/bin/fusermount -u /media/sansa
```
Debug log
```
Feb 27 12:01:43 jonathan-ubuntu kernel: [11898.990459] usb-storage: device found at 13
Feb 27 12:01:43 jonathan-ubuntu kernel: [11898.990466] usb-storage: waiting for device to settle before scanning
Feb 27 12:01:55 jonathan-ubuntu kernel: [11911.240215] usb-storage: device found at 13
Feb 27 12:01:55 jonathan-ubuntu kernel: [11911.240229] usb-storage: waiting for device to settle before scanning
Feb 27 13:10:25 jonathan-ubuntu kernel: [16021.413942] usb-storage: device found at 3
Feb 27 13:10:25 jonathan-ubuntu kernel: [16021.413946] usb-storage: waiting for device to settle before scanning
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.414178] usb-storage: device scan complete
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.441125] sd 14:0:0:0: [sdb] Mode Sense: 34 00 00 00
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.469121] sd 14:0:0:0: [sdb] Mode Sense: 34 00 00 00
Feb 27 13:46:49 jonathan-ubuntu kernel: [18204.936982] ISO 9660 Extensions: Microsoft Joliet Level 3
Feb 27 13:46:49 jonathan-ubuntu kernel: [18204.943215] ISOFS: changing to secondary root
Feb 27 14:04:45 jonathan-ubuntu kernel: [19281.239919] usb-storage: device found at 3
Feb 27 14:04:45 jonathan-ubuntu kernel: [19281.239928] usb-storage: waiting for device to settle before scanning
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.238107] usb-storage: device scan complete
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.276149] sd 15:0:0:0: [sdd] Mode Sense: 45 00 00 00
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.324191] sd 15:0:0:0: [sdd] Mode Sense: 45 00 00 00
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.362665] sd 15:0:0:1: [sde] Mode Sense: 45 00 00 00
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.376092] sd 15:0:0:1: [sde] Mode Sense: 45 00 00 00
Feb 27 14:07:39 jonathan-ubuntu kernel: [19455.280142] usb-storage: device found at 3
Feb 27 14:07:39 jonathan-ubuntu kernel: [19455.280148] usb-storage: waiting for device to settle before scanning
Feb 27 14:09:20 jonathan-ubuntu kernel: [19555.940295] usb-storage: device found at 3
Feb 27 14:09:20 jonathan-ubuntu kernel: [19555.940309] usb-storage: waiting for device to settle before scanning
Feb 27 14:09:41 jonathan-ubuntu kernel: [19577.416166] usb-storage: device found at 3
Feb 27 14:09:41 jonathan-ubuntu kernel: [19577.416180] usb-storage: waiting for device to settle before scanning
```

---

### Post by inspired on 2009-02-27
I tried attaching some data from the kern log into a txt file but the file size limit is tiny. So here it is inline...
```
Feb 27 09:03:17 jonathan-ubuntu kernel: [ 1192.768053] usb 1-5: reset high speed USB device using ehci_hcd and address 4
Feb 27 09:03:17 jonathan-ubuntu kernel: [ 1192.922926] scsi4 : SCSI emulation for USB Mass Storage devices
Feb 27 09:03:17 jonathan-ubuntu kernel: [ 1192.956577] usb-storage: device found at 4
Feb 27 09:03:17 jonathan-ubuntu kernel: [ 1192.956591] usb-storage: waiting for device to settle before scanning
Feb 27 09:06:43 jonathan-ubuntu kernel: [ 1398.733547] usb 1-5: USB disconnect, address 4
Feb 27 09:07:28 jonathan-ubuntu kernel: [ 1443.960077] usb 1-5: new high speed USB device using ehci_hcd and address 5
Feb 27 09:07:28 jonathan-ubuntu kernel: [ 1444.016309] hub 1-0:1.0: unable to enumerate USB device on port 5
Feb 27 09:09:35 jonathan-ubuntu kernel: [ 1570.776082] usb 1-5: new high speed USB device using ehci_hcd and address 6
Feb 27 09:09:36 jonathan-ubuntu kernel: [ 1571.661564] usb 1-5: config 128 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 100, changing to 10
Feb 27 09:09:36 jonathan-ubuntu kernel: [ 1571.719917] usb 1-5: configuration #128 chosen from 1 choice
Feb 27 09:10:08 jonathan-ubuntu kernel: [ 1604.280347] exaile[9055]: segfault at 70000 ip b7e1e2c3 sp b01fa16c error 4 in libc-2.8.90.so[b7da7000+158000]
Feb 27 09:10:26 jonathan-ubuntu kernel: [ 1622.340901] usb 1-5: USB disconnect, address 6
Feb 27 09:10:42 jonathan-ubuntu kernel: [ 1637.808063] usb 1-5: new high speed USB device using ehci_hcd and address 7
Feb 27 09:10:43 jonathan-ubuntu kernel: [ 1638.836087] usb 1-5: configuration #128 chosen from 1 choice
Feb 27 09:10:43 jonathan-ubuntu kernel: [ 1638.871610] scsi5 : SCSI emulation for USB Mass Storage devices
Feb 27 09:10:43 jonathan-ubuntu kernel: [ 1638.875027] usb-storage: device found at 7
Feb 27 09:10:43 jonathan-ubuntu kernel: [ 1638.875039] usb-storage: waiting for device to settle before scanning
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.872721] usb-storage: device scan complete
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.874342] scsi 5:0:0:0: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.875955] scsi 5:0:0:1: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.893266] sd 5:0:0:0: [sdc] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.894759] sd 5:0:0:0: [sdc] Write Protect is off
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.894771] sd 5:0:0:0: [sdc] Mode Sense: 45 00 00 00
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.894780] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.899005] sd 5:0:0:0: [sdc] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.900507] sd 5:0:0:0: [sdc] Write Protect is off
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.900518] sd 5:0:0:0: [sdc] Mode Sense: 45 00 00 00
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.900526] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.901615]  sdc: sdc1 sdc2
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.910589] sd 5:0:0:0: [sdc] Attached SCSI removable disk
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.911349] sd 5:0:0:0: Attached scsi generic sg3 type 0
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.916457] sd 5:0:0:1: [sdd] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.918132] sd 5:0:0:1: [sdd] Write Protect is off
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.918145] sd 5:0:0:1: [sdd] Mode Sense: 45 00 00 00
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.918154] sd 5:0:0:1: [sdd] Assuming drive cache: write through
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.923284] sd 5:0:0:1: [sdd] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.925104] sd 5:0:0:1: [sdd] Write Protect is off
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.925109] sd 5:0:0:1: [sdd] Mode Sense: 45 00 00 00
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.925112] sd 5:0:0:1: [sdd] Assuming drive cache: write through
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.926381]  sdd: sdd1
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.929188] sd 5:0:0:1: [sdd] Attached SCSI removable disk
Feb 27 09:10:48 jonathan-ubuntu kernel: [ 1643.929843] sd 5:0:0:1: Attached scsi generic sg4 type 0
Feb 27 09:32:44 jonathan-ubuntu kernel: [ 2960.062142] scsi 5:0:0:0: rejecting I/O to dead device
Feb 27 09:32:44 jonathan-ubuntu kernel: [ 2960.340861] scsi 5:0:0:1: rejecting I/O to dead device
Feb 27 09:32:54 jonathan-ubuntu kernel: [ 2969.852150] usb 1-5: reset high speed USB device using ehci_hcd and address 7
Feb 27 09:32:54 jonathan-ubuntu kernel: [ 2970.012109] scsi6 : SCSI emulation for USB Mass Storage devices
Feb 27 09:32:54 jonathan-ubuntu kernel: [ 2970.017225] usb-storage: device found at 7
Feb 27 09:32:54 jonathan-ubuntu kernel: [ 2970.017238] usb-storage: waiting for device to settle before scanning
Feb 27 09:33:13 jonathan-ubuntu kernel: [ 2988.795334] usb 1-5: USB disconnect, address 7
Feb 27 09:35:22 jonathan-ubuntu kernel: [ 3117.984277] usb 1-5: new high speed USB device using ehci_hcd and address 8
Feb 27 09:35:23 jonathan-ubuntu kernel: [ 3119.065954] usb 1-5: config 128 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 100, changing to 10
Feb 27 09:35:23 jonathan-ubuntu kernel: [ 3119.127716] usb 1-5: configuration #128 chosen from 1 choice
Feb 27 09:36:14 jonathan-ubuntu kernel: [ 3170.023298] exaile[12205]: segfault at 70000 ip b7eb42c3 sp b56a016c error 4 in libc-2.8.90.so[b7e3d000+158000]
Feb 27 09:37:03 jonathan-ubuntu kernel: [ 3218.912870] usb 1-5: USB disconnect, address 8
Feb 27 09:37:13 jonathan-ubuntu kernel: [ 3229.532080] usb 1-5: new high speed USB device using ehci_hcd and address 9
Feb 27 09:37:15 jonathan-ubuntu kernel: [ 3230.552112] usb 1-5: configuration #128 chosen from 1 choice
Feb 27 09:37:15 jonathan-ubuntu kernel: [ 3230.586563] scsi7 : SCSI emulation for USB Mass Storage devices
Feb 27 09:37:15 jonathan-ubuntu kernel: [ 3230.594492] usb-storage: device found at 9
Feb 27 09:37:15 jonathan-ubuntu kernel: [ 3230.594506] usb-storage: waiting for device to settle before scanning
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.592747] usb-storage: device scan complete
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.594368] scsi 7:0:0:0: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.595981] scsi 7:0:0:1: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.608554] sd 7:0:0:0: [sdc] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.610036] sd 7:0:0:0: [sdc] Write Protect is off
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.610050] sd 7:0:0:0: [sdc] Mode Sense: 45 00 00 00
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.610059] sd 7:0:0:0: [sdc] Assuming drive cache: write through
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.616161] sd 7:0:0:0: [sdc] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.618531] sd 7:0:0:0: [sdc] Write Protect is off
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.618544] sd 7:0:0:0: [sdc] Mode Sense: 45 00 00 00
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.618551] sd 7:0:0:0: [sdc] Assuming drive cache: write through
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.622006]  sdc: sdc1 sdc2
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.635990] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.637570] sd 7:0:0:0: Attached scsi generic sg3 type 0
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.642990] sd 7:0:0:1: [sdd] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.645537] sd 7:0:0:1: [sdd] Write Protect is off
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.645549] sd 7:0:0:1: [sdd] Mode Sense: 45 00 00 00
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.645558] sd 7:0:0:1: [sdd] Assuming drive cache: write through
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.651901] sd 7:0:0:1: [sdd] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.654403] sd 7:0:0:1: [sdd] Write Protect is off
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.654415] sd 7:0:0:1: [sdd] Mode Sense: 45 00 00 00
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.654422] sd 7:0:0:1: [sdd] Assuming drive cache: write through
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.654435]  sdd: sdd1
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.661201] sd 7:0:0:1: [sdd] Attached SCSI removable disk
Feb 27 09:37:20 jonathan-ubuntu kernel: [ 3235.661519] sd 7:0:0:1: Attached scsi generic sg4 type 0
Feb 27 09:38:23 jonathan-ubuntu kernel: [ 3298.990194] scsi 7:0:0:0: rejecting I/O to dead device
Feb 27 09:38:23 jonathan-ubuntu kernel: [ 3299.204114] scsi 7:0:0:1: rejecting I/O to dead device
Feb 27 09:38:33 jonathan-ubuntu kernel: [ 3309.032071] usb 1-5: reset high speed USB device using ehci_hcd and address 9
Feb 27 09:38:33 jonathan-ubuntu kernel: [ 3309.186024] scsi8 : SCSI emulation for USB Mass Storage devices
Feb 27 09:38:33 jonathan-ubuntu kernel: [ 3309.200182] usb-storage: device found at 9
Feb 27 09:38:33 jonathan-ubuntu kernel: [ 3309.200196] usb-storage: waiting for device to settle before scanning
Feb 27 09:39:39 jonathan-ubuntu kernel: [ 3375.193319] usb 1-5: USB disconnect, address 9
Feb 27 09:41:45 jonathan-ubuntu kernel: [ 3501.144067] usb 1-5: new high speed USB device using ehci_hcd and address 10
Feb 27 09:41:46 jonathan-ubuntu kernel: [ 3502.158751] usb 1-5: configuration #128 chosen from 1 choice
Feb 27 09:41:46 jonathan-ubuntu kernel: [ 3502.208855] scsi9 : SCSI emulation for USB Mass Storage devices
Feb 27 09:41:46 jonathan-ubuntu kernel: [ 3502.212247] usb-storage: device found at 10
Feb 27 09:41:46 jonathan-ubuntu kernel: [ 3502.212254] usb-storage: waiting for device to settle before scanning
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.212716] usb-storage: device scan complete
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.215193] scsi 9:0:0:0: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.216831] scsi 9:0:0:1: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.239021] sd 9:0:0:0: [sdc] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.240502] sd 9:0:0:0: [sdc] Write Protect is off
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.240514] sd 9:0:0:0: [sdc] Mode Sense: 45 00 00 00
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.240523] sd 9:0:0:0: [sdc] Assuming drive cache: write through
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.245632] sd 9:0:0:0: [sdc] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.249134] sd 9:0:0:0: [sdc] Write Protect is off
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.249147] sd 9:0:0:0: [sdc] Mode Sense: 45 00 00 00
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.249156] sd 9:0:0:0: [sdc] Assuming drive cache: write through
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.252583]  sdc: sdc1 sdc2
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.261230] sd 9:0:0:0: [sdc] Attached SCSI removable disk
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.262152] sd 9:0:0:0: Attached scsi generic sg3 type 0
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.272098] sd 9:0:0:1: [sdd] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.280079] sd 9:0:0:1: [sdd] Write Protect is off
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.280084] sd 9:0:0:1: [sdd] Mode Sense: 45 00 00 00
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.280087] sd 9:0:0:1: [sdd] Assuming drive cache: write through
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.283152] sd 9:0:0:1: [sdd] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.286322] sd 9:0:0:1: [sdd] Write Protect is off
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.286329] sd 9:0:0:1: [sdd] Mode Sense: 45 00 00 00
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.286333] sd 9:0:0:1: [sdd] Assuming drive cache: write through
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.287639]  sdd: sdd1
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.290312] sd 9:0:0:1: [sdd] Attached SCSI removable disk
Feb 27 09:41:51 jonathan-ubuntu kernel: [ 3507.290696] sd 9:0:0:1: Attached scsi generic sg4 type 0
Feb 27 09:42:23 jonathan-ubuntu kernel: [ 3539.220070] usb 1-5: reset high speed USB device using ehci_hcd and address 10
Feb 27 09:47:13 jonathan-ubuntu kernel: [ 3829.332074] usb 2-1: reset low speed USB device using uhci_hcd and address 2
Feb 27 09:47:29 jonathan-ubuntu kernel: [ 3845.168147] usb 2-1: reset low speed USB device using uhci_hcd and address 2
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.565598] Buffer I/O error on device sdc1, logical block 1079152
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.565607] lost page write due to I/O error on sdc1
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.565612] Buffer I/O error on device sdc1, logical block 1079153
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.565615] lost page write due to I/O error on sdc1
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.565627] Buffer I/O error on device sdc1, logical block 5046136
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.565630] lost page write due to I/O error on sdc1
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.565634] Buffer I/O error on device sdc1, logical block 5046137
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.565637] lost page write due to I/O error on sdc1
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.572205] Buffer I/O error on device sdc1, logical block 1
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.572214] lost page write due to I/O error on sdc1
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.579490] Buffer I/O error on device sdd1, logical block 275601
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.579508] lost page write due to I/O error on sdd1
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.581478] Buffer I/O error on device sdd1, logical block 275602
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.581488] lost page write due to I/O error on sdd1
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.581492] Buffer I/O error on device sdd1, logical block 275603
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.581495] lost page write due to I/O error on sdd1
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.581499] Buffer I/O error on device sdd1, logical block 275604
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.581502] lost page write due to I/O error on sdd1
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.581505] Buffer I/O error on device sdd1, logical block 275605
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.581508] lost page write due to I/O error on sdd1
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.602069] FAT: Directory bread(block 487) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.602371] FAT: Directory bread(block 488) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.602523] FAT: Directory bread(block 489) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.602670] FAT: Directory bread(block 490) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.602816] FAT: Directory bread(block 491) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.602961] FAT: Directory bread(block 492) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.603107] FAT: Directory bread(block 493) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.603252] FAT: Directory bread(block 494) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.603398] FAT: Directory bread(block 495) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.603554] FAT: Directory bread(block 496) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.603701] FAT: Directory bread(block 497) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.603846] FAT: Directory bread(block 498) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.603992] FAT: Directory bread(block 499) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.604176] FAT: Directory bread(block 500) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.604321] FAT: Directory bread(block 501) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.604501] FAT: Directory bread(block 502) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.604649] FAT: Directory bread(block 503) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.604806] FAT: Directory bread(block 504) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.604953] FAT: Directory bread(block 505) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.605098] FAT: Directory bread(block 506) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.605244] FAT: Directory bread(block 507) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.605389] FAT: Directory bread(block 508) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.605535] FAT: Directory bread(block 509) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.605681] FAT: Directory bread(block 510) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.605826] FAT: Directory bread(block 511) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.605983] FAT: Directory bread(block 512) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.606129] FAT: Directory bread(block 513) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.606274] FAT: Directory bread(block 514) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.606419] FAT: Directory bread(block 515) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.606565] FAT: Directory bread(block 516) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.606711] FAT: Directory bread(block 517) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.606873] FAT: Directory bread(block 518) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.621448] FAT: Directory bread(block 30576) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.622072] FAT: Directory bread(block 30577) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.622487] FAT: Directory bread(block 30578) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.622899] FAT: Directory bread(block 30579) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.623309] FAT: Directory bread(block 30580) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.623720] FAT: Directory bread(block 30581) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.624217] FAT: Directory bread(block 30582) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.624861] FAT: Directory bread(block 30583) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.626164] FAT: Directory bread(block 30576) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.632433] FAT: Directory bread(block 30577) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.632985] FAT: Directory bread(block 30578) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.633400] FAT: Directory bread(block 30579) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.633812] FAT: Directory bread(block 30580) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.634223] FAT: Directory bread(block 30581) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.634636] FAT: Directory bread(block 30582) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.635049] FAT: Directory bread(block 30583) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.635537] FAT: Directory bread(block 30576) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.635952] FAT: Directory bread(block 30577) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.636435] FAT: Directory bread(block 30578) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.636847] FAT: Directory bread(block 30579) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.637261] FAT: Directory bread(block 30580) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.637674] FAT: Directory bread(block 30581) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.638606] FAT: Directory bread(block 30582) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.638778] FAT: Directory bread(block 30583) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.639183] FAT: Directory bread(block 30576) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.639344] FAT: Directory bread(block 30577) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.639518] FAT: Directory bread(block 30578) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.639669] FAT: Directory bread(block 30579) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.640126] FAT: Directory bread(block 30580) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.650392] FAT: Directory bread(block 30581) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.651159] FAT: Directory bread(block 30582) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.651582] FAT: Directory bread(block 30583) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.679616] scsi 9:0:0:0: rejecting I/O to dead device
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.921143] FAT: Directory bread(block 487) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.924077] FAT: Directory bread(block 488) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.924236] FAT: Directory bread(block 489) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.924385] FAT: Directory bread(block 490) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.924532] FAT: Directory bread(block 491) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.924679] FAT: Directory bread(block 492) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.924826] FAT: Directory bread(block 493) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.924972] FAT: Directory bread(block 494) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.925167] FAT: Directory bread(block 495) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.925317] FAT: Directory bread(block 496) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.925465] FAT: Directory bread(block 497) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.925611] FAT: Directory bread(block 498) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.925757] FAT: Directory bread(block 499) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.925903] FAT: Directory bread(block 500) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.926049] FAT: Directory bread(block 501) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.926195] FAT: Directory bread(block 502) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.926341] FAT: Directory bread(block 503) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.926488] FAT: Directory bread(block 504) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.926634] FAT: Directory bread(block 505) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.926780] FAT: Directory bread(block 506) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.926926] FAT: Directory bread(block 507) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.927072] FAT: Directory bread(block 508) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.927218] FAT: Directory bread(block 509) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.927364] FAT: Directory bread(block 510) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.927509] FAT: Directory bread(block 511) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.927656] FAT: Directory bread(block 512) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.927802] FAT: Directory bread(block 513) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.927948] FAT: Directory bread(block 514) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.928176] FAT: Directory bread(block 515) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.928575] FAT: Directory bread(block 516) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.928973] FAT: Directory bread(block 517) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.929371] FAT: Directory bread(block 518) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.929793] FAT: Directory bread(block 487) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.930196] FAT: Directory bread(block 488) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.930618] FAT: Directory bread(block 489) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.931015] FAT: Directory bread(block 490) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.931414] FAT: Directory bread(block 491) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.931811] FAT: Directory bread(block 492) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.932126] FAT: Directory bread(block 493) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.932523] FAT: Directory bread(block 494) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.932975] FAT: Directory bread(block 495) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.933372] FAT: Directory bread(block 496) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.933768] FAT: Directory bread(block 497) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.934164] FAT: Directory bread(block 498) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.934559] FAT: Directory bread(block 499) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.934956] FAT: Directory bread(block 500) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.935350] FAT: Directory bread(block 501) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.935747] FAT: Directory bread(block 502) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.936113] FAT: Directory bread(block 503) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.936511] FAT: Directory bread(block 504) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.936930] FAT: Directory bread(block 505) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.937326] FAT: Directory bread(block 506) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.937738] FAT: Directory bread(block 507) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.938136] FAT: Directory bread(block 508) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.938532] FAT: Directory bread(block 509) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.938929] FAT: Directory bread(block 510) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.939325] FAT: Directory bread(block 511) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.939722] FAT: Directory bread(block 512) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.940102] FAT: Directory bread(block 513) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.940513] FAT: Directory bread(block 514) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.940912] FAT: Directory bread(block 515) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.941310] FAT: Directory bread(block 516) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.941707] FAT: Directory bread(block 517) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.942103] FAT: Directory bread(block 518) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.942517] FAT: Directory bread(block 487) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.942919] FAT: Directory bread(block 488) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.943316] FAT: Directory bread(block 489) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.943714] FAT: Directory bread(block 490) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.944141] FAT: Directory bread(block 491) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.944539] FAT: Directory bread(block 492) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.944939] FAT: Directory bread(block 493) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.945340] FAT: Directory bread(block 494) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.945741] FAT: Directory bread(block 495) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.946139] FAT: Directory bread(block 496) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.946538] FAT: Directory bread(block 497) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.946938] FAT: Directory bread(block 498) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.947338] FAT: Directory bread(block 499) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.947738] FAT: Directory bread(block 500) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.948182] FAT: Directory bread(block 501) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.948583] FAT: Directory bread(block 502) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.948983] FAT: Directory bread(block 503) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.949425] FAT: Directory bread(block 504) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.949824] FAT: Directory bread(block 505) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.950222] FAT: Directory bread(block 506) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.950622] FAT: Directory bread(block 507) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.951020] FAT: Directory bread(block 508) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.951418] FAT: Directory bread(block 509) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.951817] FAT: Directory bread(block 510) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.952244] FAT: Directory bread(block 511) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.952641] FAT: Directory bread(block 512) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953039] FAT: Directory bread(block 513) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953438] FAT: Directory bread(block 514) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953837] FAT: Directory bread(block 515) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953847] FAT: Directory bread(block 516) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953855] FAT: Directory bread(block 517) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953862] FAT: Directory bread(block 518) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953886] FAT: Directory bread(block 487) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953894] FAT: Directory bread(block 488) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953901] FAT: Directory bread(block 489) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953909] FAT: Directory bread(block 490) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953916] FAT: Directory bread(block 491) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953923] FAT: Directory bread(block 492) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953931] FAT: Directory bread(block 493) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953938] FAT: Directory bread(block 494) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953946] FAT: Directory bread(block 495) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953953] FAT: Directory bread(block 496) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953960] FAT: Directory bread(block 497) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953968] FAT: Directory bread(block 498) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953975] FAT: Directory bread(block 499) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953982] FAT: Directory bread(block 500) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953990] FAT: Directory bread(block 501) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.953997] FAT: Directory bread(block 502) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954005] FAT: Directory bread(block 503) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954012] FAT: Directory bread(block 504) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954019] FAT: Directory bread(block 505) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954027] FAT: Directory bread(block 506) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954034] FAT: Directory bread(block 507) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954042] FAT: Directory bread(block 508) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954049] FAT: Directory bread(block 509) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954056] FAT: Directory bread(block 510) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954064] FAT: Directory bread(block 511) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954071] FAT: Directory bread(block 512) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954079] FAT: Directory bread(block 513) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954086] FAT: Directory bread(block 514) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954093] FAT: Directory bread(block 515) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954101] FAT: Directory bread(block 516) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954108] FAT: Directory bread(block 517) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8835.954115] FAT: Directory bread(block 518) failed
Feb 27 11:10:40 jonathan-ubuntu kernel: [ 8836.076337] scsi 9:0:0:1: rejecting I/O to dead device
Feb 27 11:10:50 jonathan-ubuntu kernel: [ 8845.732059] usb 1-5: reset high speed USB device using ehci_hcd and address 10
Feb 27 11:10:50 jonathan-ubuntu kernel: [ 8845.902857] scsi10 : SCSI emulation for USB Mass Storage devices
Feb 27 11:10:50 jonathan-ubuntu kernel: [ 8845.920133] usb-storage: device found at 10
Feb 27 11:10:50 jonathan-ubuntu kernel: [ 8845.920140] usb-storage: waiting for device to settle before scanning
Feb 27 11:14:20 jonathan-ubuntu kernel: [ 9056.476066] usb 1-5: USB disconnect, address 10
Feb 27 11:46:18 jonathan-ubuntu kernel: [10974.180073] usb 1-5: new high speed USB device using ehci_hcd and address 11
Feb 27 11:46:19 jonathan-ubuntu kernel: [10975.289674] usb 1-5: config 128 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 100, changing to 10
Feb 27 11:46:19 jonathan-ubuntu kernel: [10975.356083] usb 1-5: configuration #128 chosen from 1 choice
Feb 27 11:59:04 jonathan-ubuntu kernel: [11739.573674] usb 1-5: USB disconnect, address 11
Feb 27 11:59:40 jonathan-ubuntu kernel: [11776.460397] usb 1-5: new high speed USB device using ehci_hcd and address 12
Feb 27 11:59:41 jonathan-ubuntu kernel: [11777.504066] usb 1-5: configuration #128 chosen from 1 choice
Feb 27 11:59:42 jonathan-ubuntu kernel: [11777.568036] scsi11 : SCSI emulation for USB Mass Storage devices
Feb 27 11:59:42 jonathan-ubuntu kernel: [11777.573467] usb-storage: device found at 12
Feb 27 11:59:42 jonathan-ubuntu kernel: [11777.573478] usb-storage: waiting for device to settle before scanning
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.572654] usb-storage: device scan complete
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.580156] scsi 11:0:0:0: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.581882] scsi 11:0:0:1: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.605452] sd 11:0:0:0: [sdc] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.607075] sd 11:0:0:0: [sdc] Write Protect is off
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.607087] sd 11:0:0:0: [sdc] Mode Sense: 45 00 00 00
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.607096] sd 11:0:0:0: [sdc] Assuming drive cache: write through
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.624207] sd 11:0:0:0: [sdc] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.625698] sd 11:0:0:0: [sdc] Write Protect is off
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.625710] sd 11:0:0:0: [sdc] Mode Sense: 45 00 00 00
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.625718] sd 11:0:0:0: [sdc] Assuming drive cache: write through
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.626888]  sdc: sdc1 sdc2
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.648310] sd 11:0:0:0: [sdc] Attached SCSI removable disk
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.648726] sd 11:0:0:0: Attached scsi generic sg3 type 0
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.652426] sd 11:0:0:1: [sdd] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.653546] sd 11:0:0:1: [sdd] Write Protect is off
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.653552] sd 11:0:0:1: [sdd] Mode Sense: 45 00 00 00
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.653555] sd 11:0:0:1: [sdd] Assuming drive cache: write through
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.656548] sd 11:0:0:1: [sdd] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.657681] sd 11:0:0:1: [sdd] Write Protect is off
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.657687] sd 11:0:0:1: [sdd] Mode Sense: 45 00 00 00
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.657691] sd 11:0:0:1: [sdd] Assuming drive cache: write through
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.658162]  sdd: sdd1
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.713427] sd 11:0:0:1: [sdd] Attached SCSI removable disk
Feb 27 11:59:47 jonathan-ubuntu kernel: [11782.713931] sd 11:0:0:1: Attached scsi generic sg4 type 0
Feb 27 12:01:27 jonathan-ubuntu kernel: [11883.379413] __ratelimit: 17 callbacks suppressed
Feb 27 12:01:27 jonathan-ubuntu kernel: [11883.379430] Buffer I/O error on device sdc1, logical block 30577
Feb 27 12:01:27 jonathan-ubuntu kernel: [11883.379440] lost page write due to I/O error on sdc1
Feb 27 12:01:28 jonathan-ubuntu kernel: [11883.801140] scsi 11:0:0:1: rejecting I/O to dead device
Feb 27 12:01:37 jonathan-ubuntu kernel: [11893.516078] usb 1-5: reset high speed USB device using ehci_hcd and address 12
Feb 27 12:01:43 jonathan-ubuntu kernel: [11898.672225] usb 1-5: failed to restore interface 0 altsetting 0 (error=-110)
Feb 27 12:01:43 jonathan-ubuntu kernel: [11898.678686] usb 1-5: USB disconnect, address 12
Feb 27 12:01:43 jonathan-ubuntu kernel: [11898.796062] usb 1-5: new high speed USB device using ehci_hcd and address 13
Feb 27 12:01:43 jonathan-ubuntu kernel: [11898.938912] usb 1-5: configuration #128 chosen from 1 choice
Feb 27 12:01:43 jonathan-ubuntu kernel: [11898.988721] scsi12 : SCSI emulation for USB Mass Storage devices
Feb 27 12:01:43 jonathan-ubuntu kernel: [11898.990459] usb-storage: device found at 13
Feb 27 12:01:43 jonathan-ubuntu kernel: [11898.990466] usb-storage: waiting for device to settle before scanning
Feb 27 12:01:55 jonathan-ubuntu kernel: [11911.080083] usb 1-5: reset high speed USB device using ehci_hcd and address 13
Feb 27 12:01:55 jonathan-ubuntu kernel: [11911.229132] scsi13 : SCSI emulation for USB Mass Storage devices
Feb 27 12:01:55 jonathan-ubuntu kernel: [11911.240215] usb-storage: device found at 13
Feb 27 12:01:55 jonathan-ubuntu kernel: [11911.240229] usb-storage: waiting for device to settle before scanning
Feb 27 12:02:46 jonathan-ubuntu kernel: [11962.162049] usb 1-5: USB disconnect, address 13
Feb 27 12:06:02 jonathan-ubuntu kernel: [12157.924085] usb 1-5: new high speed USB device using ehci_hcd and address 14
Feb 27 12:06:03 jonathan-ubuntu kernel: [12158.985559] usb 1-5: config 128 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 100, changing to 10
Feb 27 12:06:03 jonathan-ubuntu kernel: [12159.020063] usb 1-5: configuration #128 chosen from 1 choice
Feb 27 12:20:37 jonathan-ubuntu kernel: [13032.916817] usb 1-5: USB disconnect, address 14
Feb 27 12:20:44 jonathan-ubuntu kernel: [13039.708080] usb 1-5: new high speed USB device using ehci_hcd and address 15
Feb 27 12:20:45 jonathan-ubuntu kernel: [13040.585484] usb 1-5: config 128 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 100, changing to 10
Feb 27 12:20:45 jonathan-ubuntu kernel: [13040.645647] usb 1-5: configuration #128 chosen from 1 choice
Feb 27 13:03:52 jonathan-ubuntu kernel: [15628.516554] mtpfs[30487]: segfault at 0 ip b7e532c3 sp b6d1305c error 4 in libc-2.8.90.so[b7ddc000+158000]
Feb 27 13:06:05 jonathan-ubuntu kernel: [15760.652453] usb 1-5: USB disconnect, address 15
Feb 27 13:06:10 jonathan-ubuntu kernel: [15765.636074] usb 1-5: new high speed USB device using ehci_hcd and address 16
Feb 27 13:06:11 jonathan-ubuntu kernel: [15766.721209] usb 1-5: config 128 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 100, changing to 10
Feb 27 13:06:11 jonathan-ubuntu kernel: [15766.747794] usb 1-5: configuration #128 chosen from 1 choice
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.775915] ehci_hcd 0000:03:00.2: remove, state 4
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.776568] usb usb5: USB disconnect, address 1
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.779653] ehci_hcd 0000:03:00.2: USB bus 5 deregistered
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.780284] ehci_hcd 0000:03:00.2: PCI INT C disabled
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.780717] ehci_hcd 0000:00:1d.7: remove, state 1
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.781121] usb usb1: USB disconnect, address 1
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.781125] usb 1-2: USB disconnect, address 3
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.910204] usb 1-5: USB disconnect, address 16
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.949758] Buffer I/O error on device sdb1, logical block 55177720
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.949770] Buffer I/O error on device sdb1, logical block 55177721
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.949774] Buffer I/O error on device sdb1, logical block 55177722
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.949778] Buffer I/O error on device sdb1, logical block 55177723
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.949782] Buffer I/O error on device sdb1, logical block 55177724
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.949786] Buffer I/O error on device sdb1, logical block 55177725
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.949790] Buffer I/O error on device sdb1, logical block 55177726
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.949794] Buffer I/O error on device sdb1, logical block 55177727
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.949798] Buffer I/O error on device sdb1, logical block 55177728
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.949802] Buffer I/O error on device sdb1, logical block 55177729
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.981098] ehci_hcd 0000:00:1d.7: USB bus 1 deregistered
Feb 27 13:10:25 jonathan-ubuntu kernel: [16020.981795] ehci_hcd 0000:00:1d.7: PCI INT D disabled
Feb 27 13:10:25 jonathan-ubuntu kernel: [16021.212134] usb 2-2: new full speed USB device using uhci_hcd and address 3
Feb 27 13:10:25 jonathan-ubuntu kernel: [16021.385157] usb 2-2: configuration #1 chosen from 1 choice
Feb 27 13:10:25 jonathan-ubuntu kernel: [16021.413409] scsi14 : SCSI emulation for USB Mass Storage devices
Feb 27 13:10:25 jonathan-ubuntu kernel: [16021.413942] usb-storage: device found at 3
Feb 27 13:10:25 jonathan-ubuntu kernel: [16021.413946] usb-storage: waiting for device to settle before scanning
Feb 27 13:10:25 jonathan-ubuntu kernel: [16021.528071] usb 4-1: new full speed USB device using uhci_hcd and address 2
Feb 27 13:10:26 jonathan-ubuntu kernel: [16021.698246] usb 4-1: configuration #128 chosen from 1 choice
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.414178] usb-storage: device scan complete
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.417173] scsi 14:0:0:0: Direct-Access     BUFFALO  External HDD          PQ: 0 ANSI: 2 CCS
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.438103] sd 14:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.441111] sd 14:0:0:0: [sdb] Write Protect is off
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.441125] sd 14:0:0:0: [sdb] Mode Sense: 34 00 00 00
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.441134] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.465146] sd 14:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.469106] sd 14:0:0:0: [sdb] Write Protect is off
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.469121] sd 14:0:0:0: [sdb] Mode Sense: 34 00 00 00
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.469129] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.470315]  sdb: sdb1 sdb2 < sdb5 >
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.519733] sd 14:0:0:0: [sdb] Attached SCSI disk
Feb 27 13:10:30 jonathan-ubuntu kernel: [16026.520228] sd 14:0:0:0: Attached scsi generic sg2 type 0
Feb 27 13:46:49 jonathan-ubuntu kernel: [18204.715748] UDF-fs: No VRS found
Feb 27 13:46:49 jonathan-ubuntu kernel: [18204.936982] ISO 9660 Extensions: Microsoft Joliet Level 3
Feb 27 13:46:49 jonathan-ubuntu kernel: [18204.943215] ISOFS: changing to secondary root
Feb 27 14:04:31 jonathan-ubuntu kernel: [19266.544282] usb 4-1: USB disconnect, address 2
Feb 27 14:04:44 jonathan-ubuntu kernel: [19280.148085] usb 4-1: new full speed USB device using uhci_hcd and address 3
Feb 27 14:04:45 jonathan-ubuntu kernel: [19281.165149] usb 4-1: configuration #128 chosen from 1 choice
Feb 27 14:04:45 jonathan-ubuntu kernel: [19281.236089] scsi15 : SCSI emulation for USB Mass Storage devices
Feb 27 14:04:45 jonathan-ubuntu kernel: [19281.239919] usb-storage: device found at 3
Feb 27 14:04:45 jonathan-ubuntu kernel: [19281.239928] usb-storage: waiting for device to settle before scanning
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.238107] usb-storage: device scan complete
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.241278] scsi 15:0:0:0: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.244130] scsi 15:0:0:1: Direct-Access     SanDisk  Sansa e280            PQ: 0 ANSI: 0
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.269063] sd 15:0:0:0: [sdd] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.276139] sd 15:0:0:0: [sdd] Write Protect is off
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.276149] sd 15:0:0:0: [sdd] Mode Sense: 45 00 00 00
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.276152] sd 15:0:0:0: [sdd] Assuming drive cache: write through
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.321181] sd 15:0:0:0: [sdd] 15708160 512-byte hardware sectors (8043 MB)
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.324184] sd 15:0:0:0: [sdd] Write Protect is off
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.324191] sd 15:0:0:0: [sdd] Mode Sense: 45 00 00 00
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.324195] sd 15:0:0:0: [sdd] Assuming drive cache: write through
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.324678]  sdd: sdd1 sdd2
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.341163] sd 15:0:0:0: [sdd] Attached SCSI removable disk
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.341610] sd 15:0:0:0: Attached scsi generic sg3 type 0
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.355786] sd 15:0:0:1: [sde] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.362656] sd 15:0:0:1: [sde] Write Protect is off
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.362665] sd 15:0:0:1: [sde] Mode Sense: 45 00 00 00
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.362669] sd 15:0:0:1: [sde] Assuming drive cache: write through
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.373046] sd 15:0:0:1: [sde] 3970048 512-byte hardware sectors (2033 MB)
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.376085] sd 15:0:0:1: [sde] Write Protect is off
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.376092] sd 15:0:0:1: [sde] Mode Sense: 45 00 00 00
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.376095] sd 15:0:0:1: [sde] Assuming drive cache: write through
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.376602]  sde: sde1
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.385170] sd 15:0:0:1: [sde] Attached SCSI removable disk
Feb 27 14:04:50 jonathan-ubuntu kernel: [19286.385655] sd 15:0:0:1: Attached scsi generic sg4 type 0
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.913208] __ratelimit: 118 callbacks suppressed
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.913217] Buffer I/O error on device sdd1, logical block 30577
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.913222] lost page write due to I/O error on sdd1
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927097] Buffer I/O error on device sde1, logical block 275601
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927107] lost page write due to I/O error on sde1
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927874] Buffer I/O error on device sde1, logical block 413063
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927880] lost page write due to I/O error on sde1
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927885] Buffer I/O error on device sde1, logical block 413064
Feb 27 14:07:29 jonathan-ubuntu kernel: [19444.927888] lost page write due to I/O error on sde1
Feb 27 14:07:29 jonathan-ubuntu kernel: [19445.030104] scsi 15:0:0:0: rejecting I/O to dead device
Feb 27 14:07:29 jonathan-ubuntu kernel: [19445.459727] scsi 15:0:0:1: rejecting I/O to dead device
Feb 27 14:07:39 jonathan-ubuntu kernel: [19455.060043] usb 4-1: reset full speed USB device using uhci_hcd and address 3
Feb 27 14:07:39 jonathan-ubuntu kernel: [19455.252029] scsi16 : SCSI emulation for USB Mass Storage devices
Feb 27 14:07:39 jonathan-ubuntu kernel: [19455.280142] usb-storage: device found at 3
Feb 27 14:07:39 jonathan-ubuntu kernel: [19455.280148] usb-storage: waiting for device to settle before scanning
Feb 27 14:09:20 jonathan-ubuntu kernel: [19555.748081] usb 4-1: reset full speed USB device using uhci_hcd and address 3
Feb 27 14:09:20 jonathan-ubuntu kernel: [19555.918373] scsi17 : SCSI emulation for USB Mass Storage devices
Feb 27 14:09:20 jonathan-ubuntu kernel: [19555.940295] usb-storage: device found at 3
Feb 27 14:09:20 jonathan-ubuntu kernel: [19555.940309] usb-storage: waiting for device to settle before scanning
Feb 27 14:09:41 jonathan-ubuntu kernel: [19577.216087] usb 4-1: reset full speed USB device using uhci_hcd and address 3
Feb 27 14:09:41 jonathan-ubuntu kernel: [19577.392449] scsi18 : SCSI emulation for USB Mass Storage devices
Feb 27 14:09:41 jonathan-ubuntu kernel: [19577.416166] usb-storage: device found at 3
Feb 27 14:09:41 jonathan-ubuntu kernel: [19577.416180] usb-storage: waiting for device to settle before scanning
Feb 27 14:11:31 jonathan-ubuntu kernel: [19686.904117] usb 4-1: USB disconnect, address 3
Feb 27 14:14:27 jonathan-ubuntu kernel: [19862.900792] usb 4-1: new full speed USB device using uhci_hcd and address 4
Feb 27 14:14:28 jonathan-ubuntu kernel: [19863.865441] usb 4-1: configuration #128 chosen from 1 choice
Feb 27 14:22:29 jonathan-ubuntu kernel: [20344.856067] usb 4-1: reset full speed USB device using uhci_hcd and address 4
Feb 27 14:24:21 jonathan-ubuntu kernel: [20456.944100] usb 4-1: USB disconnect, address 4
Feb 27 14:25:04 jonathan-ubuntu kernel: [20500.212075] usb 4-1: new full speed USB device using uhci_hcd and address 5
Feb 27 14:25:05 jonathan-ubuntu kernel: [20501.337605] usb 4-1: configuration #128 chosen from 1 choice
Feb 27 14:26:12 jonathan-ubuntu kernel: [20568.221261] nautilus[23878]: segfault at 4a000018 ip b7604c46 sp bfa25b30 error 4 in libgconf-2.so.4.1.5[b75e4000+2e000]
Feb 27 14:27:14 jonathan-ubuntu kernel: [20630.052074] usb 4-1: USB disconnect, address 5
```

---

