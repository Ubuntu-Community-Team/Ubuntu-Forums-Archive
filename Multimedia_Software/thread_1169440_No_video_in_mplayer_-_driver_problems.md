---
title: "No video in mplayer - driver problems?"
date: 2009-05-25
forum: Multimedia Software
---

### Post by aidanb on 2009-05-25
Hi, I have a spring 2006 black MacBook with Core Duo 2.0 GHz processor and 2 GB of RAM @ 667 MHZ. I recently installed the latest version of Ubuntu due to extreme frustrations caused by the OS X 10.5.7 update.
 
I'm having troubles that seem to be connected to driver issues (?)
First of all, it doesn't let me turn on any visual effects, and I think it should be able to support this...
 
More importantly, when I open files with MPlayer, it plays audio but no video. Details: I downloaded the latest sources for MPlayer, did ./configure, make, sudo make install, also installed FFMPEG. When I do ```
mplayer -vo help
``` it gives me:
```
MPlayer SVN-r29318-snapshot-4.3.3 (C) 2000-2009 MPlayer Team
Available video output drivers:
    fbdev    Framebuffer Device
    fbdev2    Framebuffer Device
    v4l2    V4L2 MPEG Video Decoder Output
    cvidix    console VIDIX
    null    Null video output
    mpegpes    MPEG-PES to DVB card
    yuv4mpeg    yuv4mpeg output for mjpegtools
    tga    Targa output
    pnm    PPM/PGM/PGMYUV file
    md5sum    md5sum of each frame

```
But when I play a file, it gives the following message:
```
MPlayer SVN-r29318-snapshot-4.3.3 (C) 2000-2009 MPlayer Team
 
Playing [Eclipse] Fullmetal Alchemist Brotherhood - 07 (1280x720 h264) [B9AA0038].mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Fullmetal Alchemist Brotherhood - 07", -vid 0
[mkv] Track ID 2: audio (A_VORBIS) "2.0 Vorbis", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***) "***", -sid 0, -slang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8) "SRT", -sid 1, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Can't open /dev/fb0: No such file or directory
[fbdev2] Can't open /dev/fb0: No such file or directory
VO: [v4l2] No such file or directory
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[cyberblade] Error occurred during pci scan: Operation not permitted
[mach64] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[nvidia_vid] Error occurred during pci scan: Operation not permitted
[pm3] Error occurred during pci scan: Operation not permitted
[radeon] Error occurred during pci scan: Operation not permitted
[rage128] Error occurred during pci scan: Operation not permitted
[s3_vid] Error occurred during pci scan: Operation not permitted
[SiS] Error occurred during pci scan: Operation not permitted
[unichrome] Error occurred during pci scan: Operation not permitted
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
DVB card number must be between 1 and 4
AO: [null] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [null] 1280x720 => 1280x720 Planar YV12 
A:   4.5 V:   4.5 A-V: -0.001 ct:  0.000   0/  0 78%  0%  1.1% 4 0              
  =====  PAUSE  =====

```
 
Is /dev/fb0 something I should have?
I think the GPU on my MacBook is an Intel GMA 950, but I'm having trouble finding drivers for it using Google.. perhaps I'm not searching for the right thing?
 
My apologies for a long post, I would really appreciate any pointers.
 
edit again: still have troubles, though now visual effects work.

---

### Post by aidanb on 2009-05-25
Something I just noticed is that X11 says it has Xvideo, but mplayer's configure script did not find it.  Is it safe to install a new version of X11, ie XFree86 4.8.0?  (How do I check what version I have?)

---

### Post by xzero1 on 2009-05-25
You don't seem to have all the required libraries. You should at least have X11. This thread should help (Jaunty): [http://ubuntuforums.org/showthread.php?t=1081070&highlight=mplayer+compile](http://ubuntuforums.org/showthread.php?t=1081070&highlight=mplayer+compile)

---

### Post by aidanb on 2009-05-25
Thanks for the link!  Very useful, that'll most likely do the trick.  I guess I need to get better at searching for threads.

---

