---
title: "Mplayer Info - Help me get my PVR-150 working it's best.  Dont know how to title this"
date: 2008-07-04
forum: Multimedia Software
---

### Post by Mysticle31 on 2008-07-04
Does this info look good?  I can see a white and black line on the top of the video and what looks like interlace lines in the video when there is movement.  I would like to start copying my VHS tames to MPEG2 and transcode to MPEG4 files.  I would like to get this working as well as I can.  Does this look good?  What about all the failed loads and things.  Sometimes it says my system is too slow to play and it's a 2.8ghz 800mhz fsb with 1024megs.

2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
No bind found for key 'MOUSE_BTN0'.-MOUSE_BTN0_DBL                         
No bind found for key 'MOUSE_BTN0_DBL'.                          0 
No bind found for key 'MOUSE_BTN0'.-MOUSE_BTN0_DBL                         
No bind found for key 'MOUSE_BTN0_DBL'.                          1 0 
gnome_screensaver_control()00 ct: -0.494 4676/4676 10%  1%  3.0% 2 0 
Exiting... (Quit)

---

### Post by wolfen69 on 2008-07-05
are you trying to watch tv, or something else?

---

### Post by Mysticle31 on 2008-07-05
I'm going to be converting old VHS tapes to mpeg files and editing/compressing them from there.  

I will use mplayer to preview the tape and cat to make the file.  Unless anyone has a better suggestion.

Can I play the device video0 over the LAN if I shared the /dev folder?  I know of video lan - this option just occurred to me.

---

