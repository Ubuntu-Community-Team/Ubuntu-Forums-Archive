---
title: "cannot start xawtv in gusty"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by val67 on 2007-10-30
if i try xawtv i got:

val@val-ubuntu:~$ xawtv
[: 12: (opcode:: unexpected operator
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
xinerama 0: 1280x1024+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  69
  Current serial number in output stream:  69
val@val-ubuntu:~$ 


anybody has a solution?

TIA.

---

### Post by banjo man on 2007-10-30
Also getting this problem...
> 
$ xawtv
[: 12: (opcode:: unexpected operator
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
xinerama 0: 1680x1050+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  69
  Current serial number in output stream:  69


---

### Post by brel on 2007-11-06
See [http://ubuntuforums.org/showthread.php?t=334508](http://ubuntuforums.org/showthread.php?t=334508)

---

### Post by val67 on 2007-11-10
Perfect,

Works now and can record video from my webcam.

Thanks!

---

