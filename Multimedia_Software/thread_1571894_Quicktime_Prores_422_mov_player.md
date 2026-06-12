---
title: "Quicktime Prores 422 mov player?"
date: 2010-09-10
forum: Multimedia Software
---

### Post by OrangeVixen on 2010-09-10
Does anyone know of a player that will play Quicktime with Prores 422 streams on Ubuntu? I tried Totem and it I don't have the codec for that.

---

### Post by andrew.46 on 2010-09-11
Hi OrangeVixen,

Indeed the svn MPlayer should be able to play these files but I notice that this appears a little broken at the moment. I have [posted to MPlayer-users]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-September/081098.html") to see what the problem is...

Andrew

---

### Post by andrew.46 on 2010-09-11
Looks like it can be done with a 32 bit system + the svn MPlayer + an extra codec:

[http://samples.mplayerhq.hu/drivers32/new/AppleProResDecoder.qtx](http://samples.mplayerhq.hu/drivers32/new/AppleProResDecoder.qtx)

For example this sample file:

```

wget 'http://samples.mplayerhq.hu/V-codecs/HCPA/Boar__Apple_ProRes_422-partial.mov'

```

plays perfectly:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -demuxer mov -vf scale -xy 640 Boar__Apple_ProRes_422-partial.mov [/COLOR]**
MPlayer SVN-r32141-4.4.4 (C) 2000-2010 MPlayer Team

Playing Boar__Apple_ProRes_422-partial.mov.
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
[mov] Audio stream found, -aid 1
[mov] Audio stream found, -aid 2
[mov] Audio stream found, -aid 3
[mov] Audio stream found, -aid 4
VIDEO:  [apch]  960x720  24bpp  50.000 fps    0.0 kbps ( 0.0 kbyte/s)
Opening video filter: [scale]
==========================================================================
Opening video decoder: [qtvideo] Quicktime Video decoder
QuickTime6.3 DLLs found
QuickTime.qts patched!!! old entry=0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
WARNING! Invalid Ptr handle!
theQuickTimeDispatcher catched -> 0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
 76 00 00 00 61 70 63 68 00 00 00 00 00 00 00 00
 00 00 00 00 6C 70 70 61 00 00 00 00 FF 03 00 00
 C0 03 D0 02 00 00 48 00 00 00 48 00 00 00 00 00
 01 00 15 41 70 70 6C 65 20 50 72 6F 52 65 73 20
 34 32 32 20 28 48 51 29 00 00 00 00 00 00 00 00
 00 00 18 00 FF FF 00 00 00 12 63 6F 6C 72 6E 63
 6C 63 00 01 00 01 00 01 00 00 00 0A 66 69 65 6C
 01 00 00 00 00 00
=============== ImageDescription at 0x91908d8 ==================
idSize=0x76  fourcc=0x68637061
ver=0 rev=0 vendor=0x6170706C
tempQ=0 spatQ=1023  dim: 960 x 720  dpi: 72.00 x 72.00  depth: 24
dataSize=0 frameCount=1 clutID=-1
**[COLOR="Red"]name='Apple ProRes 422 (HQ)'[/COLOR]**
00 00 00 12 | 63 6F 6C 72 | 6E 63 6C 63 | 00 01 00 01
=========================================================
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[swscaler @ 0x91bf340] using unscaled yuyv422 -> yuyv422 special converter
VO: [xv] 960x720 => 640x360 Packed YUY2 
theQuickTimeDispatcher catched -> 0x6693c3e0
**[COLOR="Red"]Selected video codec: [qtprores] vfm: qtvideo (Apple ProRes 422 (HQ) decoder)[/COLOR]**
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 1 ch, s16le, 768.0 kbit/100.00% (ratio: 96000->96000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [oss] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
WARNING: CreateThread flags not supported
WARNING: CreateThread flags not supported
A:   6.7 V:   7.9 A-V: -1.143 ct:  0.468 395/395 106% 13%  0.1% 12 0 

WARNING! Invalid Ptr handle!

Exiting... (End of file)
andrew@skamandros~/Desktop$ 

```

Although there is a sound streams(s) with this file I get no sound so hopefully this is a quiet section :).

Andrew

---

### Post by OrangeVixen on 2010-09-12
Where does the codec go? (which directory?)

Does it have to be the mplayer from the svn? Does the latest for Ubuntu Karmic or Lucid work?

---

### Post by andrew.46 on 2010-09-12
Hi Orange,

> **OrangeVixen said:**
> Where does the codec go? (which directory?)

I believe this will only work with a 32 bit installation and the codec can be placed with a single command thus:

```

sudo wget \
     'http://samples.mplayerhq.hu/drivers32/new/AppleProResDecoder.qtx' \
     -O /usr/lib/codecs/AppleProResDecoder.qtx

```

> Does it have to be the mplayer from the svn? Does the latest for Ubuntu Karmic or Lucid work?

Support was only added to MPlayer in [March 2010 ]("http://git.ffmpeg.org/?p=mplayer;a=commit;h=c6c348c299cb6823c11287246f5c2580e8ce8382")so you will need the latest MPlayer, not the repository versions. There is a guide on these forums:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

The fellow that wrote this guide is usually pretty helpful :).

Andrew

---

