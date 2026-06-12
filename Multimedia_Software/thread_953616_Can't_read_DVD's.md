---
title: "Can't read DVD's"
date: 2008-10-20
forum: Multimedia Software
---

### Post by rune0077 on 2008-10-20
I've been having this problem with Hardy for a while now. My DVD-rw drive plays CD's just fine, but it won't read DVD's. It's not that it reads them wrong or some such, it doesn't even seem to register that a DVD has been inserted. 

I found some suggestions with google:
1) set "noapic" kernel parameter and reboot - didn't work.
2) create a dvd0 symlink to dvd1 in /dev - also didn't work.

I have an external dvd-drive as well, and this plays DVD's just fine, no sweat. It may be a hardware problem, but the drive used to work under Windows, and worked fine in Gutsy as well.

I'm pretty much stuck. Any help would be greatly appreciated.

Output from hdparm /dev/scd0:

```
/dev/scd0:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

I have no idea what that means.

---

