---
title: "view webcam with mplayer"
date: 2009-08-02
forum: Multimedia Software
---

### Post by nihilum on 2009-08-02
The following command works to save the webcam output to an avi file:
```
zack@jzp:~$ mencoder tv:// -tv device=/dev/video0 -nosound -ovc lavc -o foo.avi
MEncoder 2:1.0~rc2-0ubuntu19+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (046d:0991)
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
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
[V] filefmt:9  fourcc:0x32595559  size:640x480  fps:  nan  ftime:=   nan
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0xe20930]SwScaler: BICUBIC scaler, from yuyv422 to yuv420p using MMX2
[swscaler @ 0xe20930]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xe20930]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xe20930]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0xe20930]SwScaler: 640x480 -> 640x480
videocodec: libavcodec (640x480 fourcc=34504d46 [FMP4])
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Forcing audio preload to 0, max pts correction to 0.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.2s      1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.2s      2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.5s      4f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.5s      5f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.5s      6f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.8s      8f ( 0%)  7.99fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
^Cs:   0.8s      9f ( 0%)  8.47fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.8s     10f ( 0%)  8.88fps Trem:   0min   0mb  A-V:0.000 [0:0]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 1439.723 kbit/s  (179965 B/s)  size: 134974 bytes  0.750 secs  10 frames
Floating point exception
```Now how do I just view the webcam with mplayer? This is mplayer's output when I try:
```
zack@jzp:~$ mplayer -cache 128 -tv device=/dev/video1 -vc rawi420 -vo xv tv://
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
Cache fill:  0.00% (0 bytes)   
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: Microsoft LifeCam NX-3000
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
FPS not specified in the header or invalid, use the -fps option.
No stream found.

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)
```

---

### Post by kedarm on 2009-11-05
> Now how do I just view the webcam with mplayer? 

This is what worked for me -
```
mplayer -tv driver=v4l2:gain=1:width=640:height=480:device=/dev/video0:fps=10:outfmt=rgb16 tv://
```

You can (of course) replace the rgb16 with any outfmt of your choice. Read the man pages for a list of all the options.

---

