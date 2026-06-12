---
title: "error reading file input/ouput?"
date: 2009-12-15
forum: Multimedia Software
---

### Post by chrissy.millichamp on 2009-12-15
I have ubuntu 9.10 I want to copy some video files from my ipod harddisk but I get this message error reading file input/ouput. Could it be simply the videos that been damage or something? How do I fix this?

---

### Post by lodp on 2009-12-15
What's the exact error message?

I don't want to scare you, but ran into this kind of thing when copying files to/from damaged pen drives. Do those files play alright on your ipod, all the way through?

---

### Post by chrissy.millichamp on 2009-12-16
Well thats the exact message it gaved me. I tried second time and the video files are corrupted or sketchy like when i play them.

---

### Post by lodp on 2009-12-16
Do those files play alright on your ipod itself? Do you have similar problems copying stuff TO your ipod?

Here's another way you could give us more info. Plug in the ipod, do some copying to and from the device, and immediately afterward enter the following command in a terminal:

> dmesg|tail -n 30

.. and post the response here.

---

### Post by chrissy.millichamp on 2009-12-17
thats what appeared on the terminal
chrissy@chrissy:~$ dmesg|tail -n 30 
[190677.097437] FAT: bread failed in fat_clusters_flush
[190677.176966] FAT: bread failed in fat_clusters_flush
[190677.177342] FAT: bread failed in fat_clusters_flush
[190677.177378] FAT: bread failed in fat_clusters_flush
[203183.884038] usb 1-9: new high speed USB device using ehci_hcd and address 25
[203184.018902] usb 1-9: configuration #1 chosen from 2 choices
[203184.019797] scsi26 : SCSI emulation for USB Mass Storage devices
[203184.019974] usb-storage: device found at 25
[203184.019978] usb-storage: waiting for device to settle before scanning
[203184.575763] usb 1-9: USB disconnect, address 25
[203184.848026] usb 1-9: new high speed USB device using ehci_hcd and address 26
[203184.983209] usb 1-9: configuration #1 chosen from 2 choices
[203184.987599] scsi27 : SCSI emulation for USB Mass Storage devices
[203184.990061] usb-storage: device found at 26
[203184.990066] usb-storage: waiting for device to settle before scanning
[203189.988466] usb-storage: device scan complete
[203189.990702] scsi 27:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[203189.991870] sd 27:0:0:0: Attached scsi generic sg4 type 0
[203189.998794] sd 27:0:0:0: [sdd] 39075372 2048-byte logical blocks: (80.0 GB/74.5 GiB)
[203190.003559] sd 27:0:0:0: [sdd] Write Protect is off
[203190.003566] sd 27:0:0:0: [sdd] Mode Sense: 68 00 00 08
[203190.003570] sd 27:0:0:0: [sdd] Assuming drive cache: write through
[203190.006050] sd 27:0:0:0: [sdd] 39075372 2048-byte logical blocks: (80.0 GB/74.5 GiB)
[203190.008567] sd 27:0:0:0: [sdd] Assuming drive cache: write through
[203190.008577]  sdd: sdd1 sdd2
[203190.037558] sd 27:0:0:0: [sdd] 39075372 2048-byte logical blocks: (80.0 GB/74.5 GiB)
[203190.040564] sd 27:0:0:0: [sdd] Assuming drive cache: write through
[203190.040572] sd 27:0:0:0: [sdd] Attached SCSI removable disk
[203191.992541] FAT: invalid media value (0x2f)
[203191.992549] VFS: Can't find a valid FAT filesystem on dev sdd1.
chrissy@chrissy:~$ 
Im talking more precisely about the video files on the drive of my ipod that looks damaged therefore the videos being sketchy.

---

### Post by lodp on 2009-12-17
I'm still not sure I understand .. where are the damaged files - on your ipod or on the harddisk of your computer? Is it that the files were fine on your ipod, but turned out corrupted after you copied them to your computer? Or the reverse?

---

### Post by chrissy.millichamp on 2009-12-18
My files were fine on my ipods hardisk, but turned out corrupted when i had to restart my pc while my video files were being played.

---

### Post by chrissy.millichamp on 2009-12-18
sorry if i wasnt enough clear in the first place.

---

### Post by lodp on 2009-12-18
so the corrupted files are now on your ipod or on your pc?

---

### Post by chrissy.millichamp on 2009-12-18
theyve always been on my ipod and ive been always playing them on my ipod thats my point. now for some reason the video files on my ipod video hard disk seems to be corrupted or something...

---

