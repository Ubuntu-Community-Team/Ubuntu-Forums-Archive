---
title: "Problem with Microsoft LifeCam NX-6000 in Hardy"
date: 2009-07-02
forum: Multimedia Software
---

### Post by ManoloM on 2009-07-02
Hi there,

I have a Microsoft LifeCam NX-6000 and I can't run Skype and/or Cheese with Hardy (8.04).

The luvcview program runs fine. These are some responses:

manuel@johnson-miranda-laptop:~$ lsusb
Bus 007 Device 004: ID 045e:00f8 Microsoft Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 046d:c018 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0b97:7772 O2 Micro, Inc. 
Bus 005 Device 002: ID 0b97:7761 O2 Micro, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

manuel@johnson-miranda-laptop:~$ lsmod | grep videodev
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev 

So the device is being detected as ID 045e:00f8 Microsoft Corp. and the uvc driver seems to be ok, that's why luvcview runs fine:

manuel@johnson-miranda-laptop:~$ luvcview
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 

HOWEVER, when I use dmesg, this is what I get:

[   73.536875] Linux video capture interface: v2.00
[   73.554804] uvcvideo: Found UVC 1.00 device Microsoft&#65533; LifeCam NX-6000 (045e:00f8)
[   73.555150] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   73.556592] usbcore: registered new interface driver uvcvideo
[   73.556596] USB Video Class driver (v0.1.0)
[  240.824323] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

Finally I can't get any test to work using gstreamer-properties. For example:

manuel@johnson-miranda-laptop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'

(gstreamer-properties:8648): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(gstreamer-properties:8648): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not negotiate format [gstbasesrc.c(2387): gst_base_src_start (): /pipeline0/v4l2src3:
Check your filtered caps, if any]

The fact that gstreamer-properties isn't detecting the webcam may be the reason why cheese and skype can't detect it either.

Any ideas on how to fix this problem?

Thanks,
Manuel

---

### Post by newbunterquicklrnr on 2009-07-13
--------BUMP---------


Hey.. I'm a new Ubuntu user and I chose this webcam for it's price/feature and the fact that it was on a compatability chart for ubuntu... however when i plug it in an use different apps to view the video it's horrible chopping loosing parts of the screen and flashing colors occassionally

I'm using the most recent version of ubuntu just curious if anyone already knows the fix....

---

### Post by daniel.hartman on 2009-09-24
This is just an update with Jaunty Jackalope (Ubuntu 9.04).

I purchased a Microsoft LifeCam NX-6000 based on its compatibility and support with linux that is reported here:

  [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

Unfortunately, Skype and Camorama do not work, but luvcview does.

So, I downloaded the latest USB Video Class Linux device driver from:

  [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
  [http://linuxtv.org/hg/~pinchartl/uvcvideo/archive/tip.tar.bz2](http://linuxtv.org/hg/~pinchartl/uvcvideo/archive/tip.tar.bz2)

and followed the directions for compiling and installing:

  [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

Still no luck with Skype or Camorama.

---

### Post by daniel.hartman on 2009-10-28
A follow-up from last month's post.  

After some scouring of the various forums, it appears that some people have been successful with prepending the following before invoking skype:

  $ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

However this generated the following error:

  ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

I am running the 64-bit version of Ubuntu 9.04 - the Jaunty Jackalope.  Therefore, I had to install the 32-bit libraries of video4linux support libraries (lib32v4l-0), since Skype is a 32-bit app, from Synaptic Package Manager.  Once I did this, the following command worked fine:

  $ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

and video started working as it should in Skype!

---

