---
title: "ffmpeg webcam I/O error"
date: 2010-02-23
forum: Multimedia Software
---

### Post by scottch.eezem on 2010-02-23
there is a beer or coffee via paypal for whom ever can help me get this straightened out!!!

I'm using ubuntu 9.10, trying to get my webcam to work with ffmpeg via video4linux2
 lsusb give me 
Bus 002 Device 002: ID 046d:08da Logitech, Inc. QuickCam Messanger

any other v4l2 compatible program like vlc motion or cheese have no problems reading from the device

but when I run

ffmpeg -f video4linux2 -s 320x240 -i /dev/video1  out.mpg

I get

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[video4linux2 @ 0x98c8700][3]Capabilities: 5000001
[video4linux2 @ 0x98c8700]Cannot find a proper format.
/dev/video1: I/O error occurred
Usually that means that input file is truncated and/or corrupted.

or when using video4linux

 ffmpeg -f video4linux -s 320x240 -i /dev/video1  out.mpg
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
 ...
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[video4linux @ 0x9ec4700]Wrong time base (0)
/dev/video1: Error while opening file

other interesting things...
when I run cat /dev/video1 > tmp.img for a few seconds I do get a viewable image

---

### Post by FakeOutdoorsman on 2010-02-23
Perhaps you need to indicate the input frame rate as well:
```
ffmpeg -f video4linux2 -s 320x240 -r 15 -i /dev/video1 out.mpg
```

---

### Post by scottch.eezem on 2010-02-23
ah yes.  giving it a frame rate.  I only ever tried that at 15, also tried adjusting the size too but to no avail.

if I run ffmpeg without a format flag the light on the webcam comes on but I can't any sort output

like ffmpeg -i /dev/video1 > foo

just results in a file of size 0

I'm guessing that this actually has almost nothing to do with ffmpeg

---

### Post by farukkaya on 2010-03-09
I think your webcam is not providing raw video but instead its feeding mjpeg compressed video. I had the same problem and when i tried the following on my laptop it worked. So please try the following to force ffmpeg to use mjpeg

ffmpeg -f mjpeg -s 320x240 -r 30 -i /dev/video1 -r 30 out.mpg

---

### Post by huzia on 2010-05-01
> **farukkaya said:**
> I think your webcam is not providing raw video but instead its feeding mjpeg compressed video. I had the same problem and when i tried the following on my laptop it worked. So please try the following to force ffmpeg to use mjpeg

ffmpeg -f mjpeg -s 320x240 -r 30 -i /dev/video1 -r 30 out.mpg

I have the same problem, Using you method you providing, I can capture the video and the audio,

thanks , 

so I think, if you want to you laptop can worked well for ffmpeg -f video4linuxx, you shuold buy a webcam that provide raw video.....


soso

---

### Post by zair on 2011-04-30
Hi ,


I am using microsoft lifecam vx-500 with my latop having ubuntu 11.04...
I installed mplayer and used this command to get avi from my webcam..


sudo mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video1 -ovc lavc -o webcam.avi
 
where video0 is inbuilt camera on my laptop and video1 is lifecam..

am getting this error... pls help me.. pls...

MEncoder 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: Microsoft LifeCam
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
Unable to open '/dev/dsp': No such file or directory
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

how can i fix this problem...

---

