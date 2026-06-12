---
title: "[SOLVED] Video without Sound in MPlayer"
date: 2008-07-05
forum: Multimedia Software
---

### Post by sfink16 on 2008-07-05
I haven't tried my video software since my upgrade to Hardy until now.  I thought since I can view and hear videos in FireFox I'd be fine but it's not the case.  

I'm trying to open an AVI video from downloaded from my digital camera.  The video starts at a very slow speed but has no sound then freezes completely.  The only software that I can view and hear the sound is Gwenview.   More importantly, I can't run any of my video editing  software.

Nothing has changed as far as hardware since was previously working on Ubuntu 7.10.  I am up to date with the latest kernel (2.6.24.19-386).

Any help would greatly be appreciated!

Steve

---

### Post by sfink16 on 2008-07-05
With further research I found using the terminal may help and it did.  Somehow my settings must've changed since the last time I used mplayer.  Perhaps it was during the upgrade to Hardy, I don't know.  Any, it solved!  Here is what was return to me for anyone interested in the error messages I was returned (had to switch to Alsa sound):

```
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.93GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing P7040680.AVI.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  640x480  24bpp  30.000 fps  13784.8 kbps (1682.7 kbyte/s)
Clip info:
 Digitization Time: Fri Jul  4 13:58:01 2008

 Software: OLYMPUS SP560UZ
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 8000 Hz, 1 ch, u8, 64.0 kbit/100.00% (ratio: 8000->8000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 1ch u8 (1 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0x8934890]SwScaler: BICUBIC scaler, from yuv422p to yuv420p using MMX2
[swscaler @ 0x8934890]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x8934890]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x8934890]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0x8934890]SwScaler: 640x480 -> 640x480
VO: [xv] 640x480 => 640x480 Planar YV12 
A:   6.7 V:   6.3 A-V:  0.394 ct:  0.002 189/189 105% 24% 46.7% 59 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A: 116.3 V: 116.3 A-V: -0.000 ct:  0.002 3491/3491 24% 21% 19.4% 789 0 
GNOME screensaver enabled

Exiting... (End of file)

```

---

