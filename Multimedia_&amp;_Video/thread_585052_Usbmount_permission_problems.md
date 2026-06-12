---
title: "Usbmount permission problems"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by mamep on 2007-10-21
Hello i'm having some problems with usbmount.

I have nis server for users and trying to automount usb devices at /media/usb0-7


But my usb0-7 dirs are written only by the root.


```
drwxr-xr-x  9 root root  264 Oct 21 15:27 ./
drwxr-xr-x 28 root root  736 Oct  1 18:46 ../
lrwxrwxrwx  1 root root    6 Jun 26  2006 cdrom -> cdrom0/
drwxr-xr-x  2 root root   48 Jun 26  2006 cdrom0/
lrwxrwxrwx  1 root root    7 Jun 26  2006 floppy -> floppy0/
drwxr-xr-x  2 root root   48 Jun 26  2006 floppy0/
drwxr-xr-x  2 root   46   48 Oct 21 15:27 usb/
drwxr-xr-x 15 root root 4.0K Jan  1  1970 usb0/
drwxr-xr-x  2 root   46   48 Oct 21 15:27 usb1/
drwxr-xr-x  2 root   46   48 Oct 21 15:27 usb2/
drwxr-xr-x  2 root   46   48 Oct 21 15:27 usb3/

```

Any chance to give access to all the users?


thx,

mamep

---

### Post by mamep on 2007-10-27
Anyone?

---

