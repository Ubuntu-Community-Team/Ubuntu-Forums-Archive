---
title: "mencoder cam recording script no longer works"
date: 2011-03-20
forum: Multimedia Software
---

### Post by steve_c on 2011-03-20
I have been using mencoder to record audio and video from my Logitech Quickcam Pro 9000. I've been using the following wrapper script under 10.04:
```
#!/bin/bash

outFile=$(date +%Y-%m-%d)

mencoder tv:// -tv driver=v4l2:width=800:height=600:device=/dev/video0:forceaudio:adevice=/dev/audio1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o ~/projects/webcam/$outFile.avi
```
However I updated to 10.10 the other day and now this script no longer works.

When I run it I get the following output from mencoder:
> user@host:~$ mencoder tv:// -tv driver=v4l2:width=800:height=600:device=/dev/video0:forceaudio:adevice=/dev/audio1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o ~/projects/webcam/test.avi
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: UVC Camera (046d:0990)
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
Unable to open '/dev/audio1': No such file or directory
Unable to open '/dev/audio1': No such file or directory
Unable to open '/dev/audio1': No such file or directory
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...


Can anyone please help me figure out what's going on? The video and audio work in other applications, but for some reason mencoder isn't using them. I don't like Cheese because it seems like I can't get equally high framerates at good resolution, and besides I want to be able to run this from the command line.

Thanks for any help!

---

### Post by steve_c on 2011-04-23
This is still giving me fits. I tried to work on it again today and I'm hitting a wall.

I understand that some of it is that the audio devices have changed for Ubuntu 10.10 and the /dev/audio1 device no longer exists but I'm having a hard time figuring out what device (from a mencoder perspective) has replaced it.

Help anyone?

---

### Post by dozycat on 2011-05-24
They changed the channel of sound

you must use:

alsa:adevice=hw.1

---

### Post by no2498 on 2011-05-25
open a terminal type dmesg click enter
should install a cam graber
after it stops type lsusb click enter
did it find your cam

---

### Post by dozycat on 2011-05-25
maybe this will help:

mencoder tv:// -tv driver=v4l2:norm=NTSC:fps=25:outfmt=yuy2:quality=0:input=0:width=720:height=578:chanlist=us-bcast:volume=80:amode=1:normid=0:audiorate=32000:alsa:adevice=hw.1:channel=3 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1500:keyint=25 -oac mp3lame -lameopts cbr:br=128:mode=0 -endpos 00:01:00 -vf pp=hb/vb/dr/al/lb,denoise3d -o videocap.avi

I use that with my kworld pvr-tv 7134se

---

### Post by steve_c on 2011-05-30
> **dozycat said:**
> They changed the channel of sound

you must use:

alsa:adevice=hw.1
Thank you! I now have audio, but for some reason my video is now going insanely fast and is therefore out of sync with my audio. It looks like it's playing back 2x or faster.

Thanks for your command line. I'm trying to parse through the options there to see if any of those might help.

---

### Post by steve_c on 2011-06-27
Does anyone else use mencoder from the command line? Is this a problem for anyone else?

I've been trying various options (using -fps and -ofps both at 30, used -MC 0 as recommended by another site) to no avail.

Thanks for any help.

---

