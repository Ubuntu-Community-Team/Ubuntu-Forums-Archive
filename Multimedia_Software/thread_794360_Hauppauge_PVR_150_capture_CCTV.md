---
title: "Hauppauge PVR 150 capture CCTV?"
date: 2008-05-14
forum: Multimedia Software
---

### Post by Twizzle on 2008-05-14
I have a Hauppauge PVR 150 installed in a Hardy machine and have just tried to connect a cctv camera to the card using a composite cable.

This is the first time I have tried anything like this so have no idea what software is best to use or how to set it up to capture. I have tried using VLC Media Player but if I go File > Open Capture Device > Video4Linux > OK, the programs just shuts.

If I do the same but go to the PVR tab and press ok, I get a blue screen.

Can someone point me in the right direction at all?

---

### Post by Twizzle on 2008-05-15
Ok so far I have installed ivtv-utils and tried:

v4l2-ctl -i 0 through to 4

each time I run:

mplayer /dev/video0

and get this:

[PHP]MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 1500+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
MPEG-PS file format detected.
VIDEO:  MPEG2  384x288  (aspect 2)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 384 x 288 (preferred colorspace: Mpeg PES)
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
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 384 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 384x288 => 384x288 Planar YV12 
GNOME screensaver enabled.011 ct: -0.315 345/345 14%  6%  8.9% 6 0 [/PHP]

followed by a blue screen.

I know the camera works as I can plug it into a TV and use it via the composite lead.

Is it something to do with the error about the video codec?

---

### Post by MeKino on 2008-05-15
You might want to try this method:

[http://ubuntuforums.org/showthread.php?t=758845](http://ubuntuforums.org/showthread.php?t=758845)

---

### Post by MeKino on 2008-05-16
I've now ensured the correct link (see above)

---

