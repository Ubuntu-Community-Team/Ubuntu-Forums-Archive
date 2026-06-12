---
title: "MPlayer display not full screen [screenpic]"
date: 2010-06-25
forum: Multimedia Software
---

### Post by Moozillaaa on 2010-06-25
I think it's either my X configuration, or syntax, or both...

This is what displays:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=161558&d=1277497484[/IMG]


I see a couple of things in the CLI message window, but what to attack first?

chucknb@chucknb-desktop:~$ mplayer -fs -vo x11 /media/F+_Main/05_31a/movie.ts
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) II X3 440 Processor (Family: 16, Model: 5, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/F+_Main/05_31a/movie.ts.
TS file format detected.
VIDEO MPEG2(pid=7202) AUDIO MPA(pid=7204) NO SUBS (yet)!  PROGRAM N. 0
VIDEO:  MPEG2  544x480  (aspect 2)  29.970 fps  15000.0 kbps (1875.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 544 x 480 (preferred colorspace: Mpeg PES)
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
AUDIO: 48000 Hz, 2 ch, s16le, 96.0 kbit/6.25% (ratio: 12000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 544 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 544x480 => 640x480 Planar YV12  [fs]
[swscaler @ 0xf3a530]SwScaler: using unscaled yuv420p -> rgb32 special converter
No bind found for key 'c'.                          3% 50%  0.3% 0 0 
GNOME screensaver enabled 0.004 ct: -0.254 226/225  3% 50%  0.3% 0 0 

Exiting... (Quit)
chucknb@chucknb-desktop:~$

---

### Post by mc4man on 2010-06-25
Try with a
 -vo xv
If you can't get xv output look into your video drivers (installed or not ?) or try another output
-vo gl2 

this can show, though note many aren't suitable and or available
mplayer -vo help

---

### Post by andrew.46 on 2010-06-26
If you are dead keen on x11, which is perhaps not the best choice, it will run full screen with the following:

```
mplayer **[COLOR="Red"]-zoom[/COLOR]** -fs -vo x11 /media/F+_Main/05_31a/movie.ts
```

But as mc4man has suggested you would be better selecting a more tractable video out device if possible...

Andrew

---

### Post by Moozillaaa on 2010-06-26
I tried a bunch of different output device configs (from mplayer -vo --help list), and a few others gave an audio output, but no video.

I'm away from the machine now - I'll try them again, and post CLI text returns; I suppose this will tell me my configuration errors?

---

### Post by mc4man on 2010-06-26
You may want to post what your video adapter is
```
sudo lshw -C display
```
plus 
```
glxinfo
```

If only x11 is available then use the -zoom option as Andrew suggested

(a -vo of sdl should  work but the keyboard controls could be limited
(here with sdl n returns to window, c returns to fullscreen, q doesn't work - I've mapped esc to something else

---

