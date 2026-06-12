---
title: "[SOLVED] iPod Nano is not recognized - intermitent"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by victorbrca on 2007-06-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54419](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54419) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi there,


  I'm having many different bugs with a recent purchased iPod nano 4G 1st gen...

  It's recognized once in a while, but most of the time is not, and there's nothing I can do to mount it.

  It's not even charging, or showing that is connected on the iPod. The screen blinks, but that's all.

  There's an open file for similar issue on notepad too, [**_link_**]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54419")

  Here are some dsmeg outputs of another iPod connected, them my iPod connected, them my iPod not being recognized.

```
####  PLUGGED IPOD NANO 2G #### 

[17184139.068000] usb 5-5: new high speed USB device using ehci_hcd and address 8
[17184139.200000] usb 5-5: configuration #1 chosen from 2 choices
[17184139.436000] usbcore: registered new driver libusual
[17184139.524000] SCSI subsystem initialized
[17184139.528000] Initializing USB Mass Storage driver...
[17184139.528000] scsi0 : SCSI emulation for USB Mass Storage devices
[17184139.528000] usbcore: registered new driver usb-storage
[17184139.528000] USB Mass Storage support registered.
[17184139.528000] usb-storage: device found at 8
[17184139.528000] usb-storage: waiting for device to settle before scanning
[17184144.528000] usb-storage: device scan complete
[17184144.528000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17184144.528000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17184144.628000] SCSI device sda: 3999743 512-byte hdwr sectors (2048 MB)
[17184144.632000] sda: Write Protect is off
[17184144.632000] sda: Mode Sense: 68 00 00 08
[17184144.632000] sda: assuming drive cache: write through
[17184144.636000] SCSI device sda: 3999743 512-byte hdwr sectors (2048 MB)
[17184144.636000] sda: Write Protect is off
[17184144.636000] sda: Mode Sense: 68 00 00 08
[17184144.636000] sda: assuming drive cache: write through
[17184144.640000]  sda: sda1 sda2
[17184144.644000] sd 0:0:0:0: Attached scsi removable disk sda
[17184144.740000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17184145.496000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!





####  PLUGGED IPOD NANO 4G #### 

[17184468.684000] usb 5-5: new high speed USB device using ehci_hcd and address 10
[17184468.816000] usb 5-5: configuration #1 chosen from 2 choices
[17184468.816000] scsi2 : SCSI emulation for USB Mass Storage devices
[17184468.816000] usb-storage: device found at 10
[17184468.816000] usb-storage: waiting for device to settle before scanning
[17184473.816000] usb-storage: device scan complete
[17184473.816000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17184473.816000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17184473.820000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17184473.820000] sda: Write Protect is off
[17184473.820000] sda: Mode Sense: 68 00 00 08
[17184473.820000] sda: assuming drive cache: write through
[17184473.820000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17184473.824000] sda: Write Protect is off
[17184473.824000] sda: Mode Sense: 68 00 00 08
[17184473.824000] sda: assuming drive cache: write through
[17184473.824000]  sda: sda1 sda2
[17184473.828000] sd 2:0:0:0: Attached scsi removable disk sda
[17184473.828000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17184474.384000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!







####  PLUGGED IPOD NANO 4G AGAIN #### 

[17185099.752000] usb 5-5: new high speed USB device using ehci_hcd and address 11
[17185099.884000] usb 5-5: configuration #1 chosen from 2 choices
[17185099.884000] scsi3 : SCSI emulation for USB Mass Storage devices
[17185099.884000] usb-storage: device found at 11
[17185099.884000] usb-storage: waiting for device to settle before scanning
[17185104.884000] usb-storage: device scan complete
[17185104.884000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17185104.884000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17185104.888000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17185104.888000] sda: Write Protect is off
[17185104.888000] sda: Mode Sense: 68 00 00 08
[17185104.888000] sda: assuming drive cache: write through
[17185104.888000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17185104.892000] sda: Write Protect is off
[17185104.892000] sda: Mode Sense: 68 00 00 08
[17185104.892000] sda: assuming drive cache: write through
[17185104.892000]  sda: sda1 sda2
[17185104.896000] sd 3:0:0:0: Attached scsi removable disk sda
[17185104.896000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[17185105.528000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17185410.712000] sda : READ CAPACITY failed.
[17185410.712000] sda : status=0, message=00, host=7, driver=00 
[17185410.712000] sda : sense not available. 
[17185410.712000] sda: Write Protect is off
[17185410.712000] sda: Mode Sense: 00 00 00 00
[17185410.712000] sda: assuming drive cache: write through
[17185410.716000] sda : READ CAPACITY failed.
[17185410.716000] sda : status=0, message=00, host=7, driver=00 
[17185410.716000] sda : sense not available. 
[17185410.716000] sda: Write Protect is off
[17185410.716000] sda: Mode Sense: 00 00 00 00
[17185410.716000] sda: assuming drive cache: write through
[17185410.716000]  sda:<3>Buffer I/O error on device sda, logical block 0
[17185410.716000] Buffer I/O error on device sda, logical block 0
[17185410.716000]  unable to read partition table
[17185410.724000] sda : READ CAPACITY failed.
[17185410.724000] sda : status=0, message=00, host=7, driver=00 
[17185410.724000] sda : sense not available. 
[17185410.728000] sda: Write Protect is off
[17185410.728000] sda: Mode Sense: 00 00 00 00
[17185410.728000] sda: assuming drive cache: write through
[17185410.728000] sda : READ CAPACITY failed.
[17185410.728000] sda : status=0, message=00, host=7, driver=00 
[17185410.728000] sda : sense not available. 
[17185410.728000] sda: Write Protect is off
[17185410.728000] sda: Mode Sense: 00 00 00 00
[17185410.728000] sda: assuming drive cache: write through
[17185410.728000]  sda:<3>Buffer I/O error on device sda, logical block 0
[17185410.740000] Buffer I/O error on device sda, logical block 0
[17185410.740000]  unable to read partition table
[17185410.740000] Buffer I/O error on device sda, logical block 0
[17185410.740000] Buffer I/O error on device sda, logical block 1
[17185410.740000] Buffer I/O error on device sda, logical block 2
[17185410.740000] Buffer I/O error on device sda, logical block 3
[17185410.740000] Buffer I/O error on device sda, logical block 0
[17185410.740000] Buffer I/O error on device sda, logical block 4
[17185410.824000] usb 3-1: new full speed USB device using uhci_hcd and address 7
[17185410.944000] usb 3-1: device descriptor read/64, error -71
[17185411.188000] usb 3-1: not running at top speed; connect to a high speed hub
[17185411.232000] usb 3-1: configuration #1 chosen from 2 choices
[17185411.236000] scsi4 : SCSI emulation for USB Mass Storage devices
[17185411.236000] usb 5-5: USB disconnect, address 11
[17185411.236000] usb-storage: device found at 7
[17185411.236000] usb-storage: waiting for device to settle before scanning
[17185414.576000] usb 3-1: USB disconnect, address 7
[17185421.740000] usb 3-1: new full speed USB device using uhci_hcd and address 8
[17185421.860000] usb 3-1: device descriptor read/64, error -71
```


  Most of the times you get this msg from dmesg:

```
[17187493.808000] usb 3-1: new full speed USB device using uhci_hcd and address 24
[17187493.928000] usb 3-1: device descriptor read/64, error -71
[17187494.152000] usb 3-1: device descriptor read/64, error -71
[17187494.368000] usb 3-1: new full speed USB device using uhci_hcd and address 25
[17187494.488000] usb 3-1: device descriptor read/64, error -71
[17187494.712000] usb 3-1: device descriptor read/64, error -71
[17187494.928000] usb 3-1: new full speed USB device using uhci_hcd and address 26
[17187495.336000] usb 3-1: device not accepting address 26, error -71
[17187495.448000] usb 3-1: new full speed USB device using uhci_hcd and address 27
[17187495.856000] usb 3-1: device not accepting address 27, error -71
```


  Can someone please help me?????  Please...  ](*,)

Thanks,


Vic.

---

### Post by victorbrca on 2007-07-04
I solved my problem!!!  Was something as simple as a defective cable....    :(


Vic.

---

