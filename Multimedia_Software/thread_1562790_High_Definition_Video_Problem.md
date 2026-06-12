---
title: "High Definition Video Problem"
date: 2010-08-28
forum: Multimedia Software
---

### Post by linuxyogi on 2010-08-28
Hi, I recently purchased a monitor capable of displaying HD (1920 by 1080) resolutions.

So, to test how it performs I downloaded some HD trailers from 

[http://www.demo-world.eu/trailers/]("http://www.demo-world.eu/trailers/")


The problem is the video playback isn't exactly smooth. Playback often stalls for say a 2-3 secs or so.

This is the "messages" from vlc player ---

main warning: late picture skipped (-9392 > -10257)
main warning: late picture skipped (-9336 > -10423)
main warning: late picture skipped (-7104 > -10423)
main warning: late picture skipped (-2471 > -10341)
main warning: late picture skipped (-8741 > -10341)
main warning: late picture skipped (-8010 > -13364)
main warning: late picture skipped (-8159 > -13364)
main warning: late picture skipped (-7631 > -12619)
main warning: late picture skipped (-11104 > -12619)
main warning: late picture skipped (-11079 > -12619)
main warning: late picture skipped (-11036 > -12368)
main warning: late picture skipped (-10473 > -10575)
main warning: late picture skipped (-6397 > -10575)
main warning: late picture skipped (-572 > -10771)
main warning: late picture skipped (4224 > -10771)
main warning: late picture skipped (21794 > -10529)
main warning: late picture skipped (28219 > -10529)
main warning: late picture skipped (33631 > -11355)
main warning: late picture skipped (39950 > -11355)+

This is the codec info (From Vlc)

Video

Codec: H.264
Resolutions : 1920 by 1080
Frame Rate : 59.940060

_System Info_
Graphics: Integrated Nvidia 7025 /// Video Ram: 512 MB
Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+

I am using Nvidia proprietary driver.
Tried disabling compiz, didn't help.
I tried Smplayer but same result.
This is the first time I am attempting to play HD videos.
Please reply.

---

### Post by Linuxforall on 2010-08-28
Try playing them with mplayer.

---

### Post by linuxyogi on 2010-08-28
> **Linuxforall said:**
> Try playing them with mplayer.

Thanks a lot for your reply.
mplayer is playing them fine.

I didn't try mplayer before because I thought smplayer is just a frontend of mplayer.

But one thing, although mplayer is playing them smoothly but it says the following ----------

```
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
No bind found for key 'MOUSE_BTN0'.                         4% 1 0 
A: 671.3 V: 670.8 A-V:  0.440 ct:  0.020 846/846 90%  7%  1.7% 158 0 

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

```

So does that mean that my present CPU/GPU is not capable of playing HD videos?

Thanks again.

---

### Post by linuxyogi on 2010-08-28
Please someone tell me how to configure smplayer to play HD videos under my configuration.

If mplayer can play it. I am sure smplayer also will be able to play it, There must be some configuration changes that needs to be done.

I sometimes need audio equalizer & other commonly used audio video filters.
I know there are keyboard shortcuts for video adjustments but are there any keyboard shortcuts for audio equalizer for mplayer?

---

### Post by linuxyogi on 2010-09-07
LATEST: Not only the 1080s, 720p videos are also getting stuck now.
Previously I used play them without any problem.
Not only vlc, Smplayer is acting the same way now.

Please help.

---

