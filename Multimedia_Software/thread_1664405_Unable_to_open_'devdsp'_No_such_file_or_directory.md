---
title: "Unable to open 'dev/dsp': No such file or directory"
date: 2011-01-10
forum: Multimedia Software
---

### Post by cessusbangy on 2011-01-10
Hey, just wondering if I could have some assistance.
Whenever I try to record a video stream, my terminal says that error message.
I also do not understand why it would say that, as the command I used DID NOT EVEN MENTION that directory.

mencoder tv:// -tv device=/dev/video0:input=1:norm=PAL-60:width=1280: height=720 -vf pp=md -o Recording -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=8000

---

### Post by notturno995 on 2011-03-25
Im getting this too.
```
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: EasyCAP DC60
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = PAL_BGHIN; 1 = NTSC_N_443; 2 = PAL_Nc; 3 = NTSC_N; 4 = SECAM; 5 = NTSC_M; 6 = NTSC_M_JP; 7 = PAL_60; 8 = NTSC_443; 9 = PAL_M; 10 = PAL_BGHIN_SLOW; 11 = NTSC_N_443_SLOW; 12 = PAL_Nc_SLOW; 13 = NTSC_N_SLOW; 14 = SECAM_SLOW; 15 = NTSC_M_SLOW; 16 = NTSC_M_JP_SLOW; 17 = PAL_60_SLOW; 18 = NTSC_443_SLOW; 19 = PAL_M_SLOW;
 inputs: 0 = CVBS0; 1 = CVBS1; 2 = CVBS2; 3 = CVBS3; 4 = CVBS4; 5 = S-VIDEO;
 Current input: 0
 Current format: UYVY
tv.c: norm_from_string(NTSC): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
Unable to open '/dev/dsp': No such file or directory
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

```
Help ?

---

