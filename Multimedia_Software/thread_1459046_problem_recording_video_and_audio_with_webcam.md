---
title: "problem recording video and audio with webcam"
date: 2010-04-20
forum: Multimedia Software
---

### Post by beliyyal on 2010-04-20
Hi guys, I am having a problem recording audio *and* video with my webcam, and I was wondering if someone could help me out here. I am using this command:

```
mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
```

I got this command from [this](https://help.ubuntu.com/community/Webcam) page.

And when I input it, I get this:

```
******@Astaroth:~$ mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
=================================================================
 WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
 As the V4L1 compatibility layer is broken, this may not work.
 If you encounter any problems, use driver=v4l2 instead.
 Bugreports on driver=v4l with v4l2 drivers will be ignored.
=================================================================
Selected device: UVC Camera (046d:0802)
 Capabilites: capture 
 Device type: 1
 Supported sizes: 48x32 => 640x480
 Inputs: 1
  0: Camera 1:  (tuner:0, norm:pal)
Unable to open '/dev/dsp1': No such file or directory
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
******@Astaroth:~$
```

I am not exactly sure what the problem is. I can use the alternate command which does not use audio, and it works perfectly fine. Does anyone have an idea what the problem might be?

---

### Post by beliyyal on 2010-04-22
Ok guys, I just noticed something. It says if VL1 doesn't work, use driver=v4l2. Well, I did that, inputted the command:
```
mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
```

but I am still having problems. Now I get this in terminal:

```
******@Astaroth:~$ mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: UVC Camera (046d:0802)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Unable to open '/dev/dsp1': No such file or directory
Unable to open '/dev/dsp1': No such file or directory
Unable to open '/dev/dsp1': No such file or directory
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
******@Astaroth:~$
```

Ok, so now I am really confused here. I know the solution is probably simple, I'm just too stupid to figure it out, but could someone help me?

---

### Post by no2498 on 2010-04-22
have you ever had your cam working before 
does it work in cheese or ekiga softphone
did you try it in gstreamer-properties

---

### Post by beliyyal on 2010-04-22
> **no2498 said:**
> have you ever had your cam working before 
does it work in cheese or ekiga softphone
did you try it in gstreamer-properties

Oh yeah, the cam works. I use cheese to take pics, I also used it in gyache and skype. I just don't know what the problem is.

---

### Post by no2498 on 2010-04-23
type this in googl Cannot open demuxer ubuntu

---

### Post by no2498 on 2010-04-24
you can get sound to work in this program wxcam read and install what the page tells you

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by beliyyal on 2010-04-26
> **no2498 said:**
> you can get sound to work in this program wxcam read and install what the page tells you

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

Thank you so much for your help. I got the program installed, it works great. The only problem is the sound is a bit distorted, but I can try to clear it up. Thanks again though.

---

