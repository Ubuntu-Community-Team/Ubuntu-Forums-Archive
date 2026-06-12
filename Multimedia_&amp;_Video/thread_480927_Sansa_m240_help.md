---
title: "Sansa m240 help?"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by Chris Lappe on 2007-06-21
I installed Ubuntu today, and have been able to resolve almost everything but my Sansa m240 MP3 player.

I can't get it to show the MP3's that were put on with XP.

I have switched the player to MSC and Rythmbox shows it there, but not the MP3's.

Not sure what to do next???

---

### Post by Chris Lappe on 2007-06-22
I found a solution that worked really easy, I reset the m240 to MTP and connected it to an XP box long enough to reformat the device and completely wipe it.

Then put it back to MSC and I can now drag and drop MP3's in Ubuntu and they are playing fine.

---

### Post by Boomy on 2007-06-22
Can you use playlists with it? I have a Sansa C250 and I can write to it without a problem, but when I save a playlist to it, it won't show up, so it's not very useful to me. :(

---

### Post by Chris Lappe on 2007-06-22
> **Boomy said:**
> Can you use playlists with it? I have a Sansa C250 and I can write to it without a problem, but when I save a playlist to it, it won't show up, so it's not very useful to me. :(

I've never tried it with the m240 to be honest, I just let it play them by the artist and album information in the ID tags.

---

### Post by Shawn Reist on 2008-01-11
Hello,

I recently switched to Ubuntu and I am trying to get my Sansa c250 to work with Ubuntu.

the device is recognized but I can't write to it.It appears that items are dragged to it but are not actually written to the device. and if I use the file browser it says that I only have read only access. or files are read only, even with Rythmbox.

_Sansa c250 information_

Product: c250
FW: 01.01.05P
Region: America and Pacific Asia
Build Date: 2007.04.16
Serial: 

Version Info: Product Rev.: PP5022BF-06.10-S301-06.10-S301.01.05PRT
Base Code: 06.10-S301-06.10-S301.01.05PRT
ODM Ver.: S301-06.10-S301.01.05PRT
OEM Ver.: S301.01.05PRT
Build Type: RT
Build Date: 2007.04.16
Build Number: (Build 13.26)

_var/log/message _

Jan 11 15:28:59 Icabaud kernel: [58568.642803] usb 3-1: USB disconnect, address 17
Jan 11 15:29:15 Icabaud kernel: [58584.572231] usb 3-1: new full speed USB device using ohci_hcd and address 18
Jan 11 15:29:15 Icabaud kernel: [58584.787224] usb 3-1: configuration #128 chosen from 1 choice
Jan 11 15:29:15 Icabaud kernel: [58584.808260] scsi14 : SCSI emulation for USB Mass Storage devices
Jan 11 15:29:26 Icabaud kernel: [58595.473820] usb 3-1: reset full speed USB device using ohci_hcd and address 18
Jan 11 15:29:28 Icabaud kernel: [58597.693221] scsi 14:0:0:0: Direct-Access     SanDisk  Sansa c250       Sans PQ: 0 ANSI: 0
Jan 11 15:29:34 Icabaud kernel: [58603.362288] usb 3-1: reset full speed USB device using ohci_hcd and address 18
Jan 11 15:29:34 Icabaud kernel: [58603.559755] usb 3-1: device firmware changed
Jan 11 15:29:34 Icabaud kernel: [58603.559810] scsi 14:0:0:1: scsi: Device offlined - not ready after error recovery
Jan 11 15:29:34 Icabaud kernel: [58603.559962] usb 3-1: USB disconnect, address 18
Jan 11 15:29:34 Icabaud kernel: [58603.567531] sd 14:0:0:0: [sdd] READ CAPACITY failed
Jan 11 15:29:34 Icabaud kernel: [58603.567546] sd 14:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jan 11 15:29:34 Icabaud kernel: [58603.567554] sd 14:0:0:0: [sdd] Sense not available.
Jan 11 15:29:34 Icabaud kernel: [58603.567628] sd 14:0:0:0: [sdd] Write Protect is off
Jan 11 15:29:34 Icabaud kernel: [58603.567753] sd 14:0:0:0: [sdd] Attached SCSI removable disk
Jan 11 15:29:34 Icabaud kernel: [58603.567844] sd 14:0:0:0: Attached scsi generic sg5 type 0
Jan 11 15:29:35 Icabaud kernel: [58604.625093] usb 3-1: new full speed USB device using ohci_hcd and address 20
Jan 11 15:29:36 Icabaud kernel: [58604.840746] usb 3-1: configuration #128 chosen from 1 choice
Jan 11 15:29:36 Icabaud kernel: [58604.853808] scsi15 : SCSI emulation for USB Mass Storage devices
Jan 11 15:29:41 Icabaud kernel: [58609.856998] scsi 15:0:0:0: Direct-Access     SanDisk  Sansa c250       Sans PQ: 0 ANSI: 0
Jan 11 15:29:41 Icabaud kernel: [58609.864004] scsi 15:0:0:1: Direct-Access     SanDisk  Sansa c250       Sans PQ: 0 ANSI: 0
Jan 11 15:29:41 Icabaud kernel: [58609.874965] sd 15:0:0:0: [sdd] 4013056 512-byte hardware sectors (2055 MB)
Jan 11 15:29:41 Icabaud kernel: [58609.881933] sd 15:0:0:0: [sdd] Write Protect is off
Jan 11 15:29:41 Icabaud kernel: [58609.900923] sd 15:0:0:0: [sdd] 4013056 512-byte hardware sectors (2055 MB)
Jan 11 15:29:41 Icabaud kernel: [58609.907928] sd 15:0:0:0: [sdd] Write Protect is off
Jan 11 15:29:41 Icabaud kernel: [58609.907956]  sdd: sdd1 sdd2
Jan 11 15:29:41 Icabaud kernel: [58609.946003] sd 15:0:0:0: [sdd] Attached SCSI removable disk
Jan 11 15:29:41 Icabaud kernel: [58609.946105] sd 15:0:0:0: Attached scsi generic sg5 type 0
Jan 11 15:29:41 Icabaud kernel: [58609.957216] sd 15:0:0:1: [sde] Attached SCSI removable disk
Jan 11 15:29:41 Icabaud kernel: [58609.957316] sd 15:0:0:1: Attached scsi generic sg6 type 0

----------------------

I also installed Amarok, and it can see the device but can't write or delete items from the Sansa.

Any assistance would be appreciated.

---

### Post by Shawn Reist on 2008-03-09
Hello,

Well I would like to thank Chris Lappe for his suggestion about formating the device.

I hooked up my Sansa c250 to an XP machine and selected format.

I am now able to transfer music, read,write and erase.

It appears that writing is slow, as well as reading,  it seems to prefetch the information and then I can play the songs with Rythmbox.

---

