---
title: "Grip using external CD drive."
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by imboden on 2008-01-23
Hey All.

Hoping someone might be able to help out here.  I'm using Grip to rip and encode my cds to my hard drive.  My internal DVD drive might be on its way out (occasionally hearing weird noises from it when in use), so I'm trying to use my external CD drive that is connected via USB.  When a disk is in the drive, it does show up on the desktop, The device is also found in Sound Juicer.  

The problem is Grip does not want to use the drive.  Under the CONFIG tab, I do see where I am to specify the CDRom drive, and currently it has /dev/cdrom.  Any ideas what I need to put in here for it to work?

Thanks

---

### Post by logos34 on 2008-01-23
check 

sudo lshw 

look under usb and disk>cdrom.

Thing is, '/dev/cdrom' is just a link pointing to your internal optical drive (which may be listed as /dev/scd0, for instance)...You need to replace that with whatever the usb drive is being seen as in lshw

---

### Post by imboden on 2008-01-23
That got it.  Thanks for that.

---

