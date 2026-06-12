---
title: "Philips Fun Cam recognized but no /dev/video0"
date: 2010-05-23
forum: Multimedia Software
---

### Post by fotydrnka on 2010-05-23
I've got an old Philips fun cam I'm trying to connect in a fresh i386 install of Lucid (10.04):

```

root@camdeed:~# uname -a
Linux camdeed 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

```Here's the diff of dmesg before and after plugging the cam in:

```

root@camdeed:~# dmesg >before.txt
root@camdeed:~# dmesg >after.txt
root@camdeed:~# diff before.txt after.txt 
529a530,531
> [43002.300051] usb 4-2: new full speed USB device using uhci_hcd and address 3
> [43002.459407] usb 4-2: configuration #1 chosen from 1 choice

```When I plug it in, it gets recognized:

```

root@camdeed:~# lsusb
**Bus 004 Device 002: ID 0471:0321 Philips FunCam**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```From what I've read, it's supposed to use the pwc driver and register it by creating /dev/video0, but:

```

root@camdeed:~# ls /dev/video*
ls: cannot access /dev/video*: No such file or directory

```Obviously test programs like cheese and xawtv are failing: 

```

root@camdeed:~# xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-21-generic)
xinerama 0: 1920x1200+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

```It also looks like I have the pwc driver:

```

root@camdeed:~# locate pwc
/lib/modules/2.6.32-21-generic/kernel/drivers/media/video/pwc
/lib/modules/2.6.32-21-generic/kernel/drivers/media/video/pwc/pwc.ko
/usr/bin/setpwc
/usr/share/doc/setpwc
/usr/share/doc/setpwc/changelog.Debian.gz
/usr/share/doc/setpwc/copyright
/usr/src/linux-headers-2.6.32-21/drivers/media/video/pwc
/usr/src/linux-headers-2.6.32-21/drivers/media/video/pwc/Kconfig
/usr/src/linux-headers-2.6.32-21/drivers/media/video/pwc/Makefile
/usr/src/linux-headers-2.6.32-21/include/media/pwc-ioctl.h
/usr/src/linux-headers-2.6.32-21-generic/include/config/usb/pwc
/usr/src/linux-headers-2.6.32-21-generic/include/config/usb/pwc.h
/usr/src/linux-headers-2.6.32-21-generic/include/config/usb/pwc/input
/usr/src/linux-headers-2.6.32-21-generic/include/config/usb/pwc/input/evdev.h
/var/cache/apt/archives/setpwc_1.2-3_i386.deb
/var/lib/dpkg/info/setpwc.list
/var/lib/dpkg/info/setpwc.md5sums

```I also tried running setpwc:

```

root@camdeed:~# setpwc -d /dev/video0
setpwc v1.2, (C) 2003-2006 by folkert@vanheusden.com
root@camdeed:~# setpwc -p
setpwc v1.2, (C) 2003-2006 by folkert@vanheusden.com
Error while accessing device /dev/video0: No such file or directory

```Any ideas?  Any information would be helpful.  I don't really understand the process of registering usb devices and googling isn't helping much.

Thanks in advance.

---

### Post by no2498 on 2010-05-23
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file

hope this helps

---

### Post by fotydrnka on 2010-05-23
> **no2498 said:**
> open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file

hope this helps

Thanks for the reply. No luck on gstreamer either.  Here is the output:

```

root@camdeed:~# gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc1]

```I don't think any software is going to work until I figure out how to get the device registered as /dev/video0.

---

### Post by no2498 on 2010-05-23
this looks odd to me  this is what mine skips

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

---

### Post by no2498 on 2010-05-23
you have the, good bad and ugly gstreamer's installed

i have also seen the there is a gstreamer 10 that dont load

also see if you have this installed libv4l/v4l1compat.so

---

### Post by fotydrnka on 2010-05-23
Is this related to what's causing /dev/video0 not being loaded?  I was under the impression that v4l was the codecs that are used *after* the webcam is registered as /dev/video0

It looks like I have libv4l/libv4l1compat.so

```

root@camdeed:~# locate libv4l
/usr/lib/libv4l
/usr/lib/libv4l1.so.0
/usr/lib/libv4l2.so.0
/usr/lib/libv4lconvert.so.0
/usr/lib/libv4l/ov511-decomp
/usr/lib/libv4l/ov518-decomp
**/usr/lib/libv4l/v4l1compat.so**
/usr/lib/libv4l/v4l2convert.so
/usr/share/doc/libv4l-0
/usr/share/doc/libv4l-0/README.gz
/usr/share/doc/libv4l-0/README.multi-threading
/usr/share/doc/libv4l-0/TODO
/usr/share/doc/libv4l-0/changelog.Debian.gz
/usr/share/doc/libv4l-0/changelog.gz
/usr/share/doc/libv4l-0/copyright
/usr/share/lintian/overrides/libv4l-0
/var/lib/dpkg/info/libv4l-0.list
/var/lib/dpkg/info/libv4l-0.md5sums
/var/lib/dpkg/info/libv4l-0.postinst
/var/lib/dpkg/info/libv4l-0.postrm
/var/lib/dpkg/info/libv4l-0.shlibs
/var/lib/dpkg/info/libv4l-0.symbols
root@camdeed:~# aptitude search libv4l
i   libv4l-0                                                            - Collection of video4linux support libraries                                   
p   libv4l-dev                                                          - Collection of video4linux support libraries (development files)               
p   libv4l-ruby1.8                                                      - an extension library for capture pictures in Ruby using Video4Linux           

```

---

### Post by reloweb on 2010-07-15
I've the same your problem...

---

### Post by no2498 on 2010-07-16
this is all that comes up on this computer with hardy 804

no2498@no2498-desktop:~$ locate libv4l
/usr/lib/vlc/access/libv4l_plugin.so



on my other computer with 910 on it it gives a very long list 


put this in a terminal


LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 


hope that helps

---

