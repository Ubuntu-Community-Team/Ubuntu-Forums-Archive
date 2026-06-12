---
title: "[SOLVED] Proplems with mplayer after reboot"
date: 2008-07-26
forum: Multimedia Software
---

### Post by Daktar on 2008-07-26
When I try to play the video file the frame freezes, I can use the arrow keys to go seek forward then it plays some frames then freezes again but when I added the "-ac -mad" option the video played but then it can't find an audio codec and I get no sound. The file played fine until I rebooted yesterday.

Here's the output in the console:
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing file.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  640x480  24bpp  29.000 fps  950.9 kbps (116.1 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2542/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x8934890]SwScaler: using unscaled yuv420p -> bgr24 special converter
VO: [xv] 640x480 => 640x480 Planar YV12  [fs]
GNOME screensaver enabled.090 ct: -0.004 1816/1816 ??% ??% ??,?% 0 0 

Exiting... (Quit)

---

### Post by Daktar on 2008-07-26
Nevermind I just rebooted the comp again and it fixed the problem.

---

