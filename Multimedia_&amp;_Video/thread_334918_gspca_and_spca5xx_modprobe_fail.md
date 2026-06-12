---
title: "gspca and spca5xx modprobe fail"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by DESiBELi on 2007-01-09
I was trying to install Live! Cam Vista IM (reported to work) to my Ubuntu box...
So I downloaded [gspca]("http://mxhaard.free.fr/download.html"), make && make install it.

However, 'modprobe gspca' gave me:

FATAL: Error inserting gspca (/lib/modules/2.6.17-10-386/kernel/drivers/usb/media/gspca.ko): Unknown symbol in module, or unknown parameter (see dmesg)

'dmesg'
[17350718.968000] gspca: disagrees about version of symbol video_device_release
[17350718.968000] gspca: Unknown symbol video_device_release

Any ideas how to fix this?
I also tried with spca5xx, same problem.

Is there something wrong with my v4l or what?

'lsmod | grep v4l'
v4l2_common            24576  1 videodev
v4l1_compat            14340  1 videodev

'lsusb'
Bus 002 Device 008: ID 041e:4052 Creative Technology, Ltd

---

### Post by hal10000 on 2007-01-09
I guess you don't need to compile the spca5XX drivers, they are provided by standard kernel modules. The mess is that because you already compiled them, so the original module may be overwritten now.
Thus you have to reinstall the linux kernel image (linux-image-2.6.17-10-386 if this is you kernel version).

WHen reinstalled, then just try 
```

sudo modprobe spca5xx

``` 
and see what happens.

---

