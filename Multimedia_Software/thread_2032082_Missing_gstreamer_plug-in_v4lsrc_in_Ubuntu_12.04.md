---
title: "Missing gstreamer plug-in v4lsrc in Ubuntu 12.04"
date: 2012-07-23
forum: Multimedia Software
---

### Post by mightylion on 2012-07-23
[FONT=Arial]I am running Ubuntu 12.04.

[/FONT] [FONT=Arial]Trying to connect a [/FONT][FONT=Arial]Micro Innovations IC 50C[/FONT][FONT=Courier New][FONT=Arial] web cam to Skype, but getting just noise instead of a picture.

Tried running *cheese*, same result.[/FONT] [FONT=Arial]
Tried running* gstreamer*, same result.

After reading the Ubuntu forums and the Ubuntu Wiki about webcam setup and doing a bit of Google search, it seems that since I have an older webcam, I need the v4lsrc plug-in for gstreamer to be able to decode the picture correctly.  [/FONT] [FONT=Arial]

Using gstreamer-tools, I found that the[COLOR=Olive] v4l2src [COLOR=Black]plug-in is[/COLOR] present[/COLOR] but not the v4lsrc.  Running gstreamer-properties also displays a message saying that [COLOR=Red]v4lsrc[COLOR=Black] is [/COLOR]missing[/COLOR].[/FONT] 

$ gstreamer-properties 
(gstreamer-properties:11947): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
(gstreamer-properties:11947): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
[COLOR=Red]gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
[/COLOR]gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'

[/FONT][FONT=Arial]I have double checked that I have all the gstreamer plugins - base, good, bad, etc.  gstreamer0.10-gconf is already the newest version.  I have gstreamer.0.10.36 for i386.

[/FONT]  [FONT=Arial][COLOR=Red]Has this plug-in been dropped from the Ubuntu 12.04 gstreamer base plug-ins package? [/COLOR][/FONT][FONT=Arial] According to the gstreamer website, it is supposed to be included in the gstreamer base plug-in package. 

[/FONT]  [FONT=Arial][COLOR=Red]Could there be any other reason why this plug-in would be reported as missing?[/COLOR][/FONT][FONT=Arial]

Thanks a lot for your help.[/FONT]

---

### Post by BicyclerBoy on 2012-07-23
[https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting)

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

Could be a new skype (4.0?) with this fixed & more..or did the purchase by microsoft put an end to it?
The new skype service/servers do not look very secure from a privacy/espionage viewpoint.

---

### Post by mightylion on 2012-07-23
Thanks for the reply.  That did not work either.  Produces the same noise and static as the screenshot I had posted.

---

### Post by BicyclerBoy on 2012-07-25
Assuming you used a terminal to launch skype (with the LD_PRELOAD etc)..
Post the std output errors from the terminal..

---

### Post by von Stalhein on 2012-10-23
Getting exactly the same issue with a Logitech webcam and gstreamer too  - did you find a solution or a workaround??
Thanks.

---

### Post by pvfloripa on 2012-11-27
Hi guys,

Did anybody find a solution? I am also having this problem now.

Thanks!!

---

### Post by BicyclerBoy on 2012-11-27
from terminal run:
gstreamer-properties

select <video> tab
click on the plugin drop down selector...

Is the "Video for linux (1) (v4l1)" missing ?

It is missing here..

---

### Post by von Stalhein on 2012-11-28
Yep, missing here too.

Reports  Video for Linux 2 (v4l2)

---

### Post by alexmoon on 2013-02-23
Did anyone work this out? I'm having a similar issue.

---

### Post by BicyclerBoy on 2013-02-23
V4l1 was marked for removal in 2010. Drivers were meant to be rebuilt before then.

The repos package "libv4l-0" is meant to provide:
> libv4l is a collection of libraries which adds a thin abstraction layer on
top of video4linux2 devices. The purpose of this (thin) layer is to make it
easy for application writers to support a wide variety of devices without
having to write separate code for different devices in the same class. libv4l
consists of 3 different libraries: libv4lconvert, libv4l1 and libv4l2.

libv4l1 offers the (deprecated) v4l1 API on top of v4l2 devices, independent
of the drivers for those devices supporting v4l1 compatibility (which many
v4l2 drivers do not).

libv4l2 offers the v4l2 API on top of v4l2 devices, while adding for the
application transparent libv4lconvert conversion where necessary.

That reads as if the v4l1 compatibility is to do with supporting v4l1 abi applications interfacing with v4l2 driver layer..

The problem faced by posters in this thread is their v4l2 h/w driver does not work.

If you build v4l-dvb from source you get a v4l1 compatibility library.
[http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git)
I do not have any h/w requiring the old v4l1 api so don't know if it is a soln..

Note you have to rebuild this after every kernel update..

---

### Post by alexmoon on 2013-02-23
Thanks! Can you recommend a way to test if this is the problem without making permanent changes?

---

### Post by BicyclerBoy on 2013-02-23
I doubt I was being that helpful..

The driver (SPCA50X USB Camera) support for the OPs webcam:
[http://linux.about.com/gi/o.htm?zi=1/XJ&zTi=1&sdn=linux&cdn=compute&tm=53&f=01&su=p284.13.342.ip_p504.6.342.ip_&tt=2&bt=1&bts=1&zu=http%3A//spca50x.sourceforge.net/spca50x.php](http://linux.about.com/gi/o.htm?zi=1/XJ&zTi=1&sdn=linux&cdn=compute&tm=53&f=01&su=p284.13.342.ip_p504.6.342.ip_&tt=2&bt=1&bts=1&zu=http%3A//spca50x.sourceforge.net/spca50x.php)
seem to have stopped..or just gone into v4l-dvb (which is part of the kernel).

Without the OPs or your h/w I can't comment about the success of any solution..
Could be easier to buy a new webcam..

---

### Post by alexmoon on 2013-02-23
Hmm. Okay. Well, hopefully I'll work something out.

---

