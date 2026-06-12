---
title: "Analog camcorder video capture"
date: 2008-05-16
forum: Multimedia Software
---

### Post by Luke3026 on 2008-05-16
I think I originally posted in the wrong forum, so I'll post this again here.

My setup:
Ubuntu 8.04 Hardy
P4 3.4GHz 2GB RAM
ATI Radeon X600 Video card

Old Canon Hi8 camcorder with composite RCA out's.

I'm trying to capture the video from Hi8 tapes for editing and burning to DVD without much success.  I've been trying mencoder, with the following command:

$ mencoder -oac mp3lame -ovc lavc -lameopts mode=1:vbr=2:q=4 -lavcopts vcodec=mpeg4 -tv driver=v4l2:norm=ntsc:input=4:adevice=/dev/dsp:width=640:height=480 -af volume=-10 -o vid.avi tv://

And this in turn returns this-->

MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.40GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9 data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
name: Video 4 Linux 2 input
author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
comment: first try, more to come
Selected device: Hauppauge WinTV PVR-150
Tuner cap:
Tuner rxs:
Capabilites: video capture VBI capture device tuner audio read/write
supported norms: 0 = PAL-BGH; 1 = PAL-DK; 2 = PAL-I; 3 = PAL-M; 4 = PAL-N; 5 = PAL-Nc; 6 = SECAM-BGH; 7 = SECAM-DK; 8 = SECAM-L; 9 = SECAM-L'; 10 = NTSC-M; 11 = NTSC-J; 12 = NTSC-K;
inputs: 0 = Tuner 1; 1 = S-Video 1; 2 = Composite 1; 3 = S-Video 2; 4 = Composite 2;
Current input: 2
Current format: unknown (0x4745504d)
v4l2: current audio mode is : MONO
tv.c: norm_from_string(ntsc): Bogus norm parameter, setting default.
Audio block size too low, setting to 8192!
v4l2: ioctl request buffers failed: Invalid argument
v4l2: ioctl set mute failed: No such device
v4l2: 0 frames successfully processed, 0 frames dropped.
Segmentation fault

Any ideas?

---

