---
title: "Video  Codec Help"
date: 2010-12-11
forum: Multimedia Software
---

### Post by beingrishy on 2010-12-11
I ve come across a few videos that have been encoded using the FMVC codec( video capture codec from FOX Magic)
Though i've been able to play these files in windows after installing the codec (given by  the makers at [http://www.fox-magic.com/download/fmvc_setup.zip]("http://www.fox-magic.com/download/fmvc_setup.zip%29;") ); i vE NOT FOUND A way to play these videos on Ubuntu, which is dissappointing.
Could someone suggest help??

---

### Post by mc4man on 2010-12-11
Your link goes nowhere useful, anyway - 
It's possible that a 32 bit mplayer with w32codecs can play your file. Can do so here with one sample I found.
To try you'd need to go to /usr/lib/codecs and rename fmcodec.DLL to fmcodec.dll

Ex.
> MPlayer SVN-r32678-4.5.2 (C) 2000-2010 MPlayer Team
Playing /home/doug/Videos/skrzyzowanie4.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [FMVC]  800x520  24bpp  10.000 fps  352.1 kbps (43.0 kbyte/s)
==========================================================================
Opening video decoder: [vfw] Win32/VfW video codecs
Loading codec DLL: 'fmcodec.dll'
Loaded DLL driver fmcodec.dll at 10000000
[PP] Using codec's postprocessing, max q = 9.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Opening video filter: [flip]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xac64b70] using unscaled bgr24 -> yuv420p special converter
VO: [xv] 800x520 => 800x520 Planar YV12 
Selected video codec: [foxmotion] vfm: vfw (fox motion video)


---

### Post by andrew.46 on 2010-12-11
Hi mc4man,

Thanks for the DLL --> dll tip, I have modified my own copy accordingly :)

Andrew

---

