---
title: "Hercules webcam not working in ubuntu 11.04 64 bit"
date: 2011-08-03
forum: Multimedia Software
---

### Post by mrmrmrmrmr on 2011-08-03
Hi!  I have ubuntu 11.04 64 bit and I am not able to make my webcam, a Hercules silver classic, work.

After installing ubuntu, I ran cheese and was only able to see the first frame.
Then, I tried to follow the suggestions at:
[http://ubuntuforums.org/showthread.php?t=1020873](http://ubuntuforums.org/showthread.php?t=1020873)
but got stuck installing v4l-dvb because of this error while running make:

/opt/src/v4l-dvb/v4l/flexcop-i2c.c: In function 'flexcop_i2c_init':
/opt/src/v4l-dvb/v4l/flexcop-i2c.c:253:39: error: 'I2C_CLASS_TV_DIGITAL' undeclared (first use in this function)

At present, I have (ubuntu 11.04 64bit):
$ lsusb | grep 06f8:3004
Bus 001 Device 008: ID 06f8:3004 Guillemot Corp. Hercules Classic Silver
$ uname -r
2.6.38-10-generic
$ lsmod | grep gspca
$ cheese
** Message: Error: stream contains no data.
gsttypefindelement.c(948): gst_type_find_element_activate (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind:
Can't typefind empty stream

totem-video-thumbnailer couldn't open file 'file:///home/francesco/Video/Webcam/2011-07-29-100726.ogv'
Reason: stream contains no data

** (cheese:3182): WARNING **: could not generate thumbnail for /home/francesco/Video/Webcam/2011-07-29-100726.ogv (video/ogg)
[after removing videodev module not even the first frame is now shown)

Could you help me, please?

Thank you very much!
Marc

---

### Post by no2498 on 2011-08-05
the first ? in cheese FAQ'S is 

in a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

### Post by mrmrmrmrmr on 2011-08-06
Thank you for your reply.

I solved the issue! 

Here is a description on how I did it.

a) I tried to follow instructions here:
[http://ubuntuforums.org/showthread.php?t=1020873](http://ubuntuforums.org/showthread.php?t=1020873)
b) I got stuck at the make of v4l-dvb package
because of incompatibility with my kernel:
2.6.38-10-generic 64bit
c) I replaced that package with the one found at:
[http://linuxtv.org/wiki/index.php/S2-liplianin](http://linuxtv.org/wiki/index.php/S2-liplianin)
that has patches for newer kernels. This was not enough for mine, however. I had to edit the c source of quite a few files because of other incompatibilities with 2.6.38 kernel (mostly commenting lines that give errors during make).
d) call make install and follow the procedure as described originally in 
[http://ubuntuforums.org/showthread.php?t=1020873](http://ubuntuforums.org/showthread.php?t=1020873)
e) to get skype to work instead of using:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype                      
use the 32bit library:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype                      

Now skype, cheese and gstream-properties work wonderfully.

NOTE: it would be nice if these issues with the newer kernel (64bit) could be fixed and found in the repository. 

Thank you!
Marc

---

