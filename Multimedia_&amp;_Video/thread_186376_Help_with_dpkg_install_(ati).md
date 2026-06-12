---
title: "Help with dpkg install (ati)"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by majkmil on 2006-06-01
I get this error when trying to installl the debs with the proprietary drivers from ATI.
mark@ubuntu:~/ati$ sudo dpkg -i xorg-driver-fglrx_8.25.18-1_i386.deb
(Reading database ... 135622 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.24.8-1 (using xorg-driver-fglrx_8.25.18-1_i386.deb) ...
Removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
  different file `/usr/share/fglrx/diversions/libGL.so.1.2', not allowed
dpkg: error processing xorg-driver-fglrx_8.25.18-1_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx_8.25.18-1_i386.deb

Can anyone help with this please.

---

### Post by karthik085 on 2006-06-01
Try with -f option

---

