---
title: "AC3 passthrough Envy24 surround sound working but small glitch"
date: 2009-04-20
forum: Multimedia Software
---

### Post by kharn on 2009-04-20
Ok. I've tried to google this as much as I can, but haven't found an answer, so I'll have to do a post. I'm using mplayer with the hwac3 passthrough and alsa on an envy24 chip card. The surround works, but once every 5 to even 60 seconds, there's a small break in the sound. Total silence for about 0.5 seconds. I've tried running mplayer with -vo null to test if my cpu gets exhausted, but top says usage doesn't jump over 50% and still the sound breaks. I found this solution [HTML]http://lists.mplayerhq.hu/pipermail/mplayer-users/2003-February/029583.html[/HTML]but I can't find a sensible reference to why my svn-mplayer doesn't have mmap as an option, only noblock. Here's mplayer output
```
mplayer test.mkv -ao alsa:noblock
MPlayer SVN-r29081-4.3.2 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3) "US", -aid 0, -alang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x528  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[VO_SDL] Using driver: x11.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: hwac3
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 640000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
Starting playback...
[h264 @ 0x8937960]Cannot parallelize deblocking type 1, decoding such frames in sequential order
VDec: vo config request - 1280 x 528 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.42:1 - prescaling to correct movie aspect.
VO: [sdl] 1280x528 => 1280x528 Planar YV12  [fs]
[VO_SDL] Info - please use -vm or -zoom to switch to the best resolution.
[ASPECT] Warning: No suitable new res found!
A:   7.8 V:   7.8 A-V:  0.003 ct:  0.002   0/  0 40%  5%  0.3% 0 0 
Exiting... (Quit)
```

My mplayer configfile
```
cat .mplayer/config 
# Write your default config options here!
vo=sdl
stop-xscreensaver="yes"
monitoraspect="4:3"
subfont-text-scale=2.3
ac="hwac3,hwdts,"
channels=6
dr=yes
mc=0.00001
slang=fi,fin,en,eng
fs=yes
channels=6
af=scaletempo,lavcac3enc=1:640:3
#subfont-encoding=unicode
#unicode=yes
#utf8=yes
lavdopts="threads=2"
#lavdopts="fast=1"
#lavdopts="skiploopfilter=all"

#framedrop="1"
#hardframedrop="0"

```
My alsa set
```
aplay -L
front:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    Front speakers
surround40:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    4.0 Surround output to Front and Rear speakers
surround41:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```
/etc/asound.conf has just
```
pcm.!default iec958:M2496
```

---

### Post by kharn on 2009-07-15
3 months passed. Shameless bump

---

### Post by igorzwx on 2009-07-15
O.K., let us make an experiment to make it more clear.

Take an old box and try this solution:
[http://www.4front-tech.com/forum/viewtopic.php?t=3237](http://www.4front-tech.com/forum/viewtopic.php?t=3237)

it is another sound system, but Ubuntu and mplayer are the same

---

### Post by igorzwx on 2009-07-15
or small partion 10GB for another Ubuntu on the same box

---

### Post by kharn on 2009-10-14
Just an update. I added a nvidia graphics card with the PV3-chip, so I get to use mplayer -vo vdpau. This way the processor usage on videos is really low (4%) on 1080p movies aswell. Even then the sound breaks every 5-50 seconds. 

I felt the above test environment to be a bit overkill, since I'm running other services on the server as well.

---

