---
title: "mplayer works properly only after reboot"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by BetterSense on 2008-04-17
I'm having the strange issue where mplayer opens the file, but doesn't play it; however you can scroll through the video with the arrow keys and page up and so on. It's not paused either, because you can pause and unpause (with no effect) with the spacebar. Rebooting the system usually fixes it, but that is to windows for me. Any ideas?

```
chaz@brutus:~/Videos/Torrents/CowboyBebop$ mplayer *
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ (Family: 15, Model: 107, Ste
pping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [KB]_Cowboy_Bebop_Remix_01.DVD_(H264.AC3_5.1)[0B265C96].mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3) "Japanese AC3 5.1", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***) "English ***", -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  640x480  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12
GNOME screensaver enabled.278 ct: -0.042  17/ 17 ??% ??% ??,?% 0 0

Exiting... (Quit)
chaz@brutus:~/Videos/Torrents/CowboyBebop$
```

Also, is it possible that I could pipe this with SPDIF to my surround reciever and have it decode into surround sound?

---

### Post by BetterSense on 2008-04-18
bump for great justice

---

