---
title: "mp3 player not detected?"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by merwizard on 2007-06-15
I recently bought a Canyon  CN MP3SOF mp3 player. This device acts like any other USB mass storage device, conequently it should be detected and mounted automatically like i.e. any  USB stick. Well, it gets NOT mounted at all. No new device icon on the desktop, no new device notification.

However the kernel recognizes it and assigns the /dev/sdb device to it

If I do the classic approach and mount it manually using "mount /dev/sdb1 /media/somefolder" it works flawlessly. So, I guess it is a dbus problem or something.

I am sure there is somenthing that needs to be tweaked there. I'll appreciate any help

---

### Post by stchman on 2007-06-15
> **merwizard said:**
> I recently bought a Canyon  CN MP3SOF mp3 player. This device acts like any other USB mass storage device, conequently it should be detected and mounted automatically like i.e. any  USB stick. Well, it gets NOT mounted at all. No new device icon on the desktop, no new device notification.

However the kernel recognizes it and assigns the /dev/sdb device to it

If I do the classic approach and mount it manually using "mount /dev/sdb1 /media/somefolder" it works flawlessly. So, I guess it is a dbus problem or something.

I am sure there is somenthing that needs to be tweaked there. I'll appreciate any help

Do you have auto mount in your removable devices under preferences checked?

---

### Post by trippinnik on 2007-06-15
try unplugging and then plug it back in the type dmesg in the terminal and post the last few lines, it should report what's happening with the device.

---

### Post by merwizard on 2007-06-16
I do indeed have automount devices set. Automount works fine with my card reader and my Sony Ericsson K750i

> **trippinnik said:**
> try unplugging and then plug it back in the type dmesg in the terminal and post the last few lines, it should report what's happening with the device.

Did that. Everything seems fine

[ 5587.458604] usb 2-2: new full speed USB device using ohci_hcd and address 3
[ 5588.184876] usb 2-2: configuration #1 chosen from 1 choice
[ 5588.377259] usbcore: registered new interface driver libusual
[ 5588.409134] Initializing USB Mass Storage driver...
[ 5588.426130] scsi2 : SCSI emulation for USB Mass Storage devices
[ 5588.427170] usbcore: registered new interface driver usb-storage
[ 5588.427177] USB Mass Storage support registered.
[ 5588.428205] usb-storage: device found at 3
[ 5588.428212] usb-storage: waiting for device to settle before scanning
[ 5593.418571] usb-storage: device scan complete
[ 5593.426553] scsi 2:0:0:0: Direct-Access     Canyon   MP3 Player       0100 PQ: 0 ANSI: 4
[ 5593.437511] SCSI device sdb: 487936 2048-byte hdwr sectors (999 MB)
[ 5593.444495] sdb: Write Protect is off
[ 5593.444499] sdb: Mode Sense: 3e 00 00 00
[ 5593.444502] sdb: assuming drive cache: write through
[ 5593.463462] SCSI device sdb: 487936 2048-byte hdwr sectors (999 MB)
[ 5593.470447] sdb: Write Protect is off
[ 5593.470451] sdb: Mode Sense: 3e 00 00 00
[ 5593.470454] sdb: assuming drive cache: write through
[ 5593.470458]  sdb: sdb1
[ 5593.484476] sd 2:0:0:0: Attached scsi removable disk sdb
[ 5593.484531] sd 2:0:0:0: Attached scsi generic sg1 type 0

---

### Post by merwizard on 2007-07-02
Two weeks have passed, and due to the fact I gave away the player as a present, I am now not able to test the gizmo any more. However, I had the opportunity to connect it to a computer running OpenSUSE 10.2 and it there too, it was not automounted. However, as it is possible to be mounted manually, in  the old-fashioned way, the device can be still used in Linux, but sadly, only by power users. Bad enough :(

---

### Post by Slammer64 on 2007-07-02
It might be new enough that there is no entry in the "pciids" so it's not recognized as anything but a generic flash harddrive, as to automounting I use Kubuntu and don't have a problem with that.

---

### Post by merwizard on 2007-07-04
I think I got the point. Thank you Slammer64. So, the system thinks it's a generic hard disk drive, and acts consequently. It doesn't mount it, as it doesn't know what it is,  if it is needed to be mounted  and where to mount it.

---

### Post by zero244 on 2007-10-19
Try This!

[http://ubuntuforums.org/showthread.php?t=506034](http://ubuntuforums.org/showthread.php?t=506034)

---

### Post by nithin933 on 2008-07-11
> **merwizard said:**
> I recently bought a Canyon  CN MP3SOF mp3 player. This device acts like any other USB mass storage device, conequently it should be detected and mounted automatically like i.e. any  USB stick. Well, it gets NOT mounted at all. No new device icon on the desktop, no new device notification.

However the kernel recognizes it and assigns the /dev/sdb device to it

If I do the classic approach and mount it manually using "mount /dev/sdb1 /media/somefolder" it works flawlessly. So, I guess it is a dbus problem or something.

I am sure there is somenthing that needs to be tweaked there. I'll appreciate any help
   

OR just try to change the usb mode of the mp3player (mtp-msc) i case of ubuntu 8.04

---

