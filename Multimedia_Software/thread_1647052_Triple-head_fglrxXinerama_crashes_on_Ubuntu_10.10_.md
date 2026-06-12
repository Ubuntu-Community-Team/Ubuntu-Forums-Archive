---
title: "Triple-head: fglrx/Xinerama crashes on Ubuntu 10.10 amd64"
date: 2010-12-16
forum: Multimedia Software
---

### Post by dsjstc on 2010-12-16
System specs: Ubuntu 10.10, 2.6.35-23-generic, x86_64. Multihead, 1 monitor on onboard Radeon HD4290, 2 monitors on PCI-E Radeon HD5850.

Whenever Xinerama is enabled, many applications (amdcccle, vlc, VirtualBox) cause an immediate hard X crash.  And by "hard", I mean all my gnome processes are still there, and I have an unkillable X process.  Requires a reboot every time.

This appears to happen whether or not I disable RandR in the amdpcsdb.  It happens with the standard restricted repository fglrx, the ubuntu-x/swat package (2:8.791-0ubuntu1~xup~maverick), and the Catalyst 10.12 package (driver version 8.8) straight from ATI.

I haven't yet managed to make the open source radeon driver enable both adapters, so I'm making do with three independent desktops for now.

Here's my crash:
> [ 84.650] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
[ 84.650] 1: /usr/bin/X (0x400000+0x60fcd) [0x460fcd]
[ 84.650] 2: /lib/libpthread.so.0 (0x7f31308b7000+0xfb40) [0x7f31308c6b40]
[ 84.650] 3: /usr/bin/X (0x400000+0xbb22f) [0x4bb22f]
[ 84.650] 4: /usr/bin/X (0x400000+0x2c2d9) [0x42c2d9]
[ 84.650] 5: /usr/bin/X (0x400000+0x2184b) [0x42184b]
[ 84.650] 6: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f312f822d8e]
[ 84.650] 7: /usr/bin/X (0x400000+0x213d9) [0x4213d9]
[ 84.650] Segmentation fault at address 0x4
[ 84.650] 
Caught signal 11 (Segmentation fault). Server aborting

---

### Post by dsjstc on 2010-12-16
This was caused by a bug in xorg 1.9.
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539)


Solved by updating xserver-xorg-core and xserver-common from PPA:
[https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539](https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539)

---

### Post by antonis21 on 2011-03-17
Hello my friend.

Can you please tell me how you fixed it because the files you posted are only compatible for i386. I currently have  64 bit version of ubuntu 10.10 and when I try to apply the fix it complains 


thanks in advance

---

### Post by dsjstc on 2011-03-17
> **antonis21 said:**
> Hello my friend.

Can you please tell me how you fixed it because the files you posted are only compatible for i386. I currently have  64 bit version of ubuntu 10.10 and when I try to apply the fix it complains 

Try again; I'm running AMD64.

---

