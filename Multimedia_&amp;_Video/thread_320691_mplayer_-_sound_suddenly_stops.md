---
title: "mplayer - sound suddenly stops"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by Ghosty.be on 2006-12-17
Hello,

first a small description of my setup:
i got a wintv pvr 150 working for watching tv (ivtv driver)
i use this one for the moment with just the command:
mplayer /dev/video0
since this card gives immediate mpeg 2 output afaik.
Now while watching tv it sometimes just stops giving sound, it is at random times (had it like 3 time in about an hour and a half and afterwards it played 2 hours just fine and then i got it again)

i added an output redirect to a file, which you can from find the output underneath (skipped a bit of the junk, hope i left in the important stuff):
> 
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(TM) XP 2600+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Terminal type `unknown' is not defined.
Opening joystick device /dev/input/js0
Setting up LIRC support...

Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9600.0 kbps (1200.0 kbyte/s)
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffmp2] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio decoder)
==========================================================================
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
....
alsa-uninit: pcm closed

I will try to make a more extensive output with more verbose and post it here (but this could take a couple of days) 
any suggestions are welcome to get this thing fixed. As far as i googled the last error it seems like some audio codec problem maybe, but it seems not really clear.

---

