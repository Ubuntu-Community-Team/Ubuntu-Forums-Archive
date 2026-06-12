---
title: "Logitech QuickCam Connect works OOB with Skype!"
date: 2009-06-27
forum: Multimedia Software
---

### Post by shreepads on 2009-06-27
Got Logitech QuickCam Connect, plugged it in and working smoothly with Skype.. No config, no make...

Strangely enough working better in Skype than in Ekiga (better res, picture), but maybe I didn't do the Ekiga startup wizard settings properly...

[B]
Details:[/B]
Logitech QuickCam Connect model, bought for Rs 1100 (India)
lsusb: Bus 003 Device 002: ID 046d:08af Logitech, Inc. 
Ubuntu 8.04.2, kernel 2.6.24-24-generic
Skype 2.0.0.72
Intel C2D E7200 on Intel DG33FB motherboard, 2 GB RAM
ADSL broadband, Ping 118ms, Down 1.66 Mbps, Up 0.41 Mbps to closest gateway (as per speedtest.net)

Did some research before buying that seemed to suggest this may not work as smoothly or without config etc so thought I'll post this...

---

### Post by shreepads on 2009-06-27
Output from lsmod | grep videodev:
```
videodev               29440  1 gspca
v4l2_common            18304  1 videodev
v4l1_compat            15492  1 videodev

```

---

### Post by shreepads on 2009-06-27
Also ran gstreamer-properties and Tested via the Video tab. 

First got an error re Video for Linux 2 (v4l2), so switched to v4l and tested. Surprisingly image was poorer (lower res, darker) than that in Skype.

gstreamer-properties output:
```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver. [v4l2_calls.c(85): gst_v4l2_get_capabilities (): /pipeline0/v4l2src3:
system error: Invalid argument]

```

---

### Post by philcamlin on 2009-06-27
seems like it all works fine but your missing some plugins...:D

---

### Post by shreepads on 2009-07-01
Yes indeedy! I think the moral of the story is research and then just plug it in and see before you start messing around with modules, config files etc...

---

### Post by kjaspan on 2009-10-31
I have had no luck with the Logitech Quickcam Connect with Jaunty or Kosmic. It works well with accursed Win XP=, but Skype and X crash when I try to test the cam with Skype. I have installed Kosmic with all updates curent as of 10/31/2009.

Here is my lsmod:
lsmod|grep video
videodev               36736  1 gspca_main
v4l1_compat            14496  1 videodev
video                  19380  1 i915
output                  2780  1 video

lsusb:
Bus 003 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:0a01 Logitech, Inc. USB Headset
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:089d Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by clandel on 2009-11-09
I have the same cam on Ubuntu Karmic (9.10), at least the same chip (046d:08af in lsusb), but I don't get a useful image from it (green screen with some distortion). I used it on Debian with kernel version 2.6.26 and it worked fine, but when I upgraded to version 2.6.30, I had the same issue there.

Any insights? Do we need to make a bug report?

---

### Post by jazeekat on 2010-09-06
Can you help  me install my Logitech Cam?  I am new to Unbuntu.. a total Ubuntu virgin!  I have 10.4 on my system and my logitec cam is 8/04.   I installed Skype that works fine and Cheese is installed.  I cannot get the system to recognize my cam.

help please

hopeless in unbuntu land

---

### Post by shreepads on 2011-01-13
Did a fresh install of 64-bit Lucid 10.04.1 LTS and installed Skype (Beta 2.1) from the Software Centre...

Exactly same hardware config as the first post and now the Logitech Quickcam Connect is no longer working. Although working in Cheese, with very grainy video.

Spent a lot of time messing around with *LD_PRELOAD* and *export XLIB_SKIP_ARGB_VISUALS=1* commands with no success. (BTW in the default install via Software Centre in Lucid 10.04.1 LTS the Skype shortcut in the desktop applications menu points to a wrapper script that already runs the appropriate command line invocations).

In the end it was a very simple thing indeed. No need to mess around with all those command line invocations/ parameters, just open your Skype config file:

```
gedit ~/.Skype/YourSkypeUsername/config.xml
```

And in there, just before the last </Lib> tag, insert the following (or modify if the file already contains a <Video> tag):

```
<Video>
<CaptureHeight>240</CaptureHeight>
<CaptureWidth>320</CaptureWidth>
<RecvPolicy>callpolicy</RecvPolicy> 
</Video>
```

Of course this is with my particular system and hardware so YMMV....

---

### Post by shreepads on 2011-06-05
Here we go again... After one or two updates from the standard Update Manager, Skype video is not working...

Skype version now 2.2.0.25

First I tried with a fresh config.xml file, basically I renamed the existing user folder:

```
mv ~/.Skype/yourusername ~/.Skype/yourusernamebak
```

Then ran Skype, logging in with my username. This created a new username folder and config.xml file but still no video.

So I opened up the new config.xml file. Added the <Video> tag same as in the previous post, but still no luck.

Then realised that some genius had, in the update, changed the default Skype menu-item so that it pointed directly at skype instead of the skype-wrapper as before. And the skype-wrapper script was gone as well...

Luckily I had created a script before as follows:

```
#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so  QT_PLUGIN_PATH=/usr/lib32/qt4/plugins /usr/bin/skype "$@"
exit 0
```

Ran it and the video test is working... Although the terminal does show the following error, it doesn't crash skype or anything

```
libv4l2: error allocating conversion buffer
```

Haven't tried a video conf as everyone is offline right now...

Copied menu-item to desktop, changed the command to point to the script and voila...

I then changed the Video tag Height, Width to 480 by 640 and the test video works!! Earlier it would only work at 240 by 320, so the update HAS made things better is some ways!

---

### Post by no2498 on 2011-06-05
you need a file called something like v4l so v4l2 compat

---

