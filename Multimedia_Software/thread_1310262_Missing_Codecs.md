---
title: "Missing Codecs"
date: 2009-11-01
forum: Multimedia Software
---

### Post by glennric on 2009-11-01
How can you get totem, mplayer, or vlc to play videos that use the intel indeo 5 codec?  None of them can play these videos since the upgrade to Karmic.  I have all of the restricted formats and such installed.  I also am having trouble playing 3gp files.  I used to be able to do this with mplayer.

---

### Post by epek on 2009-11-01
I don´t know, but I too would like to know where especially vlc gets it´s codec from. Are they all in /usr/lib/vlc/codec? How can vlc "learn" more codecs?

totem could be using ffmpeg or gstreamer, afaik.

Mplayer used to have separate binary codecs, which usually where windows codecs, installed in /usr/lib/codecs or similar. see:
[http://www.mplayerhq.hu/design7/dload.html#binary_codecs](http://www.mplayerhq.hu/design7/dload.html#binary_codecs)
I don´t think that those available as a debian package.

---

### Post by wilee-nilee on 2009-11-01
With a quick Google search I found this, I don't know if it's the answer. You might try looking for 3rd party open source stuff with Google to fix your problem, or just reformat it with the several devices that are available if they will reread the original. [http://ubuntuforums.org/showthread.php?t=713054](http://ubuntuforums.org/showthread.php?t=713054)

---

### Post by mc4man on 2009-11-01
In karmic mplayer will play both formats but you'd probably need to either build mplayer, guide 
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

Or  install a pre-built from the smplayer related ppa
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Vlc should play indeo 5 but the use of some dshow codecs (dmo) seems broken in 1.02, it will play 3gp, though probably not the repo version

I also have an operating totem-xine in karmic that plays both 

Your best bet is thru mplayer (w32codecs installed for indeo 5, if using the ppa mplayer then install the opencore amr libs (libopencore-amrnb, ect. for 3gp

Ex.with built mplayer
...........
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 IYUV UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2f)
VDec: vo config request - 836 x 500 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 836x500 => 836x500 Planar YV12 
Selected video codec: [indeo5ds] vfm: dshow (Intel Indeo 5)

3gp
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh263] vfm: ffmpeg (FFmpeg H.263+)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, s16le, 0.0 kbit/0.00% (ratio: 0->16000)
Selected audio codec: [ffamrnb] afm: ffmpeg (AMR Narrowband)

---

### Post by glennric on 2009-11-01
Thanks mc4man.  I kind of suspected I would need to rebuild one of them or find someone else's build.

---

### Post by glennric on 2009-11-01
By the way, what happened to totem-xine?  Did they just discontinue it for karmic?  Where can I find information about building it for Karmic?  I always used that before.

---

### Post by mc4man on 2009-11-01
> what happened to totem-xine

it's been removed and is just a dummy package

Atm the jaunty totem source (2.26) can be built and just the totem-xine package used

Atm means as long as the current totem-common is compatible

The re-built totem-xine can only be used as a media player for local files and dvd's, can't be set as the default totem player, nor used with plugins (and you wouldn't want to anyway

It's best to build as pakage, changing the name to current totem version-1

see screen

(am expecting totem to go to 2.28.2 shortly so will have to rebuild or hack the package name and re-install

(would make avail. upon request or tips to build

---

### Post by glennric on 2009-11-01
I knew that totem-xine is now a dummy package, but I was just wondering why they have quit building totem with the xine alternative backend.  

I probably won't mess with rebuilding totem.  It wouldn't be hard to download the jaunty source and modify it as you did.  I most likely will go for a recompilation of mplayer instead.

---

### Post by andrew.46 on 2009-11-02
Hi epek,

> **epek said:**
> 
[http://www.mplayerhq.hu/design7/dload.html#binary_codecs](http://www.mplayerhq.hu/design7/dload.html#binary_codecs)
I don´t think that those available as a debian package.

As a small sidenote these codecs are in fact packaged by Medibuntu as *w32codecs* and *w64codecs*.

Andrew

---

