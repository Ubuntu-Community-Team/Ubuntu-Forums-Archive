---
title: "Cannot automount dvd-r"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by raskolnik on 2007-01-27
I'm having some trouble automounting dvd-r's I've burned. I use Edgy, and Gnomebaker 0.6.0. There are no errors while this is taking place, but when I insert the new burned disc, nothing happens. The following errors show up in “dmesg | tail”...

```
[17179655.884000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[17179655.884000] hdc: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
[17179655.884000] ide: failed opcode was: unknown
[17179655.884000] end_request: I/O error, dev hdc, sector 64
[17179655.884000] Buffer I/O error on device hdc, logical block 8

```

This happens 95% of the time. Sometimes it works properly, but I can't find any pattern to it. Running “dd if=/dev/cdrom of=image.iso” works every time, and I have no problem mounting these images. Dvd+r's I've burned still automount perfectly. Mounting the disc manually also works fine, but it will not update nautilus' “places” list. Does anyone know what the problem is? Is it possible these are just defective dvd-r's, or am I doing something wrong? Thanks.

---

