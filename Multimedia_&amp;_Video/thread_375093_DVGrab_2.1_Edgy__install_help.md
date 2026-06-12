---
title: "DVGrab 2.1 Edgy  install help"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by quackking on 2007-03-03
Hi. I have a Canon HV10 camcorder, which supports HDV video. I am hoping to connect the cam to my  AMD Athlon 64 X2 Dual Core Processor 4600+ box, which is running Edgy. I believe that the newest dvgrab is an essential part of this, but the Ubuntu repositories only have dvgrab 1,83 (which I have installed, and which does not work.)

I downloaded the dvgrab2.1 source file,  and issued ./configure, but I get this (tailed) output:

-----------------------

.
.
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBRAW1394... configure: error: Package requirements (libraw1394 >= 1.1.0) were not met:

No package 'libraw1394' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBRAW1394_CFLAGS
and LIBRAW1394_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
-----------------------

I do have libraw1394-8 installed, though, courtesy of Synaptic!

Here is output from dpkg:

-------

Package: libraw1394-8
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 68
Maintainer: Ben Collins <bcollins@debian.org>
Architecture: i386
Source: libraw1394
Version: 1.2.1-0ubuntu1
Depends: debconf, makedev (>= 2.3.1-49), libc6 (>= 2.4-1)
Description: library for direct access to IEEE 1394 bus (aka FireWire)
 libraw1394 is the only supported interface to the kernel side raw1394
 of the Linux IEEE-1394 subsystem, which provides direct access to the
 connected 1394 buses to user space.  Through libraw1394/raw1394,
 applications can directly send to and receive from other nodes without
 requiring a kernel driver for the protocol in question.


-------


What am I doing wrong?

---

### Post by quackking on 2007-03-09
Help? Anyone?

---

### Post by nim278 on 2007-04-12
Try installing libraw1394-dev

---

