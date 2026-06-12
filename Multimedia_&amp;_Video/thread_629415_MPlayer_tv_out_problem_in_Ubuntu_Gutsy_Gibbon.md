---
title: "MPlayer tv out problem in Ubuntu Gutsy Gibbon?"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by zoomphys on 2007-12-02
Hi, I would like to ask about a problem I have using
mplayer after upgrading to Ubuntu Gutsy Gibbon. If I
use mplayer to play a video file when I'm on TV
display, the TV screen would be scrambled. However, if
I play the same file on LCD display, and then switch
the display to TV, the TV screen displays fine. But if
as soon as I quit playing, the TV screen (which has
been showing the video fine) again gives me a
scrambled picture.

So the problem happens when mplayer starts or stop a
video file and it seems like mplayer tries something
and then fails (scaling, zooming or changing video
mode). I have tried different video output xv,x11,sdl
and different options fs, zoom, but to no avail. I
have better chance with -vm option though. The TV
screen displays video but occupies only 2/3 of the
size on fullscreen. Moreover, it gives me the
scrambled picture again on quitting mplayer.

Besides, totem (gstreamer) plays video fine on TV.
However, it takes a long time to start as if it tries
to find the right mode to display. I would prefer to
use mplayer since it seems to start almost instantly.

Another thing is MPlayer works with Ubuntu Edgy Eft
before I upgraded to Gutsy. I kept all the config
files after the upgrade so the conflict must come from
the new stuffs in the upgrade.

I would appreciate any hint at all and I can provide
further information if needed. Thank you.

---

### Post by zoomphys on 2007-12-05
I have a clue to my tvout problem. If I run "mplayer -vo dga video.file", I get an error message like this:

 > 
mythtv@Multimedia:~$ mplayer -vo dga Comptine.flv 
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, 
Model: 8, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick

Playing Comptine.flv.
libavformat file format detected.
VIDEO:  [FLV1]  320x240  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
vo_dga: Mode: depth=15, bpp=16, r=007c00, g=0003e0, b=00001f, native 
(-bpp 15)
vo_dga: Mode: depth=16, bpp=16, r=00f800, g=0007e0, b=00001f, native 
(-bpp 16)
vo_dga: Mode: depth=24, bpp=24, r=ff0000, g=00ff00, b=0000ff, native 
(-bpp 24)
vo_dga: Mode: depth=24, bpp=32, r=ff0000, g=00ff00, b=0000ff, native 
(-bpp 32)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 8.0 kbit/1.13% (ratio: 1000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, 
layer-3)
==========================================================================
AO: [oss] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar 
YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: using unscaled yuv420p -> rgb32 special converter
VO: [dga] 320x240 => 320x240 BGRA  [fs] [zoom]
vo_dga: DGA 2.0 available :-) Can switch resolution AND depth!
vo_dga: Selected hardware mode  512 x  384 @  75 Hz @ depth 24, 
bitspp 32.
vo_dga: Video parameters by codec: 320 x 240, depth 24, bitspp 32.
vo_dga: Aspect corrected size for SwScaler:  512 x  384.
vo_dga: Framebuffer mapping failed!!!
FATAL: Cannot initialize video driver.
VDec: vo config request - 320 x 240 (preferred colorspace: Planar 
YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [dga] 320x240 => 320x240 BGRA  [fs] [zoom]
vo_dga: DGA 2.0 available :-) Can switch resolution AND depth!
vo_dga: Selected hardware mode  512 x  384 @  75 Hz @ depth 24, 
bitspp 32.
vo_dga: Video parameters by codec: 320 x 240, depth 24, bitspp 32.
vo_dga: Aspect corrected size for SwScaler:  512 x  384.
vo_dga: Framebuffer mapping failed!!!
FATAL: Cannot initialize video driver.

FATAL: Could not initialize video filters (-vf) or video output 
(-vo).


Exiting... (End of file)


After getting this error, I can play video from TV display with correct fullscreen resolution!? I guess this has something to do with resolution as shown by part of the above output:

> vo_dga: DGA 2.0 available :-) Can switch resolution AND depth!
vo_dga: Selected hardware mode  512 x  384 @  75 Hz @ depth 24, 
bitspp 32.
vo_dga: Video parameters by codec: 320 x 240, depth 

I tried adding "512x384" resolution to the mode line in xorg.conf but it doesn't help. GDM still starts with 640x480 resolution. Does anybody know how to switch resolution, just like "mplayer -vo dga" does?

---

### Post by zoomphys on 2007-12-22
Could anyone help please? Or point to me where to look for answer? I wonder if my question is too long and complicated? Should I rephrase it?

---

