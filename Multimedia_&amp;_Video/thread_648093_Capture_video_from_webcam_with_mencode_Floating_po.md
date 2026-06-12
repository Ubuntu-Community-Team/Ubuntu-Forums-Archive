---
title: "Capture video from webcam with mencode: Floating point exception"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by vollkorn on 2007-12-23
Hi,

I got a Logitech "QuickCam Deluxe for Notebooks" (046d:09c1) and use it with the uvcdriver which just supports v4l2. So far it works and I can use the webcam for example with ekiga, skype (2.0 beta) and grab from it with
```
mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0 -fps 30
```
But when I try to capture a video (with or without sound) it doesn't work for me:
```
mencoder tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0:fps=30:forceaudio:adevice=hw.0:alsa -ovc lavc -o test.avi
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1500MHz (Family: 6, Model: 9, Stepping: 5)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (046d:09c1)
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
Floating point exception (core dumped)

```

Since I rarely understand what I typed in there and I have no clue which of the output lines actually is the one describing the problem, I ask here for your help to solve this problem.
My goal is to record a video including sound.

TIA
Jan

---

### Post by jbuberel on 2008-03-03
Jan,

I am having/experiencing the same problem using a Logitech USB Notebook Pro webcam. While I can use mencoder for video-only capture, as soon as I add an alsa audio input device, I get the same floating point exception.

If you do come across an answer or fix, please post it here!

Regards,
Jason

PS For what it is worth, I have had more luck using gstreamer, with only slight problems in audio synchronization. The command I am currently using is:
```
gst-launch-0.10 v4l2src ! queue ! videorate ! video/x-raw-yuv,width=800,height=600,framerate=15/1 ! ffmpegcolorspace ! theoraenc quality=60 !  queue ! oggmux name=mux alsasrc device="hw:1,0" ! audiorate ! audio/x-raw-int,rate=16000,channels=1,depth=16 ! queue ! audioconvert ! vorbisenc !  mux. mux. ! queue ! filesink sync=true location=test.ogg qos=true

```

---

