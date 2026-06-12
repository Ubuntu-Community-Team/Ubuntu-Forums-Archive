---
title: "Asus EEE webcam and Xubuntu 7.10 troubles."
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by minksj on 2008-01-06
Hi everyone.

I'm running Xubuntu 7.10 on Asus EEE 701. I seem to have two separate problems running the webcam, one of them caused by (???) direc rendering, the other I'm unable to track down. I've posted the problem at [EEEuser forum]("http://forum.eeeuser.com/viewtopic.php?id=8225") with no luck. To avoid redundancy, please find the outputs of various apps I found relevant in the posts mentioned above.

Setting aside the problem with Compiz-fusion, I'd really like to know, why am I able to run USB cam using v4l (/dev/video1):
```
$ mplayer tv:// -tv driver=v4l:width=352:he ght=288:device=/dev/video1 
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) M processor          900MHz (Family: 6, Model: 13, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
Selected device: Creative Live Cam Video IM
 Capabilites: capture 
 Device type: 1
 Supported sizes: 176x144 => 640x480
 Inputs: 1
  0: ZC301-2:  (tuner:0, norm:pal)
Using input 'ZC301-2'
Selected input hasn't got a tuner!
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 352x288 => 352x288 Planar YV12 
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Audio: no sound
Starting playback...
V:   0.3   8/  8 ??% ??% ??,?% 0 0 

MPlayer interrupted by signal 2 in module: video_read_frame
  MJP: returning! 

```

but unable to run internal cam w/ v4l2 (/dev/video0), as documented for example by mplayer:

```
mplayer tv:// -tv driver=v4l2:width=352:height=288:device=/dev/video0 
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) M processor          900MHz (Family: 6, Model: 13, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (eb1a:2761)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: UYVY
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
FPS not specified in the header or invalid, use the -fps option.
No stream found.

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)

```

finally, adding xawtv  output:
```
xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
looking for available devices
port 73-88
    type : Xvideo, image scaler
    name : Intel(R) Textured Video

port 89-89
    type : Xvideo, image scaler
    name : Intel(R) Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : UVC Camera (eb1a:2761)
    flags:  capture  

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l
    name : Creative Live Cam Video IM
    flags:  capture  

```

Any help will be strongly appreciated! Thank you!

---

