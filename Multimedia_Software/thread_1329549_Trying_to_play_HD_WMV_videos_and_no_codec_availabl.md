---
title: "Trying to play HD WMV videos and no codec available..."
date: 2009-11-17
forum: Multimedia Software
---

### Post by ovimunt on 2009-11-17
Hi,

I've got some HD WMV videos I'm trying to play but I can't get any sound in them. It's MPlayer is telling me that not codecs are available to play Windows Media Player 9 format. Is there any way around it, can you somehow wrap the original Windows codecs into Ubuntu?

Thanks

---

### Post by andrew.46 on 2009-11-17
Hi ovimunt,

> **ovimunt said:**
> I've got some HD WMV videos I'm trying to play but I can't get any sound in them. It's MPlayer is telling me that not codecs are available to play Windows Media Player 9 format. Is there any way around it, can you somehow wrap the original Windows codecs into Ubuntu?

I suspect you may mean 'Windows Media *Video* 9'? The 32 bit MPlayer has support for this through the w32codec pack from Medibuntu:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep 'Windows Media Video 9'[/COLOR]**

wmv9dmo     dmo       working   Windows Media Video 9 DMO  [wmv9dmod.dll]

```

There is a nice sample here:

[http://samples.mplayerhq.hu/V-codecs/WMV9/trailers/pinball.wmv](http://samples.mplayerhq.hu/V-codecs/WMV9/trailers/pinball.wmv) 

that also highlights the new MPlayer implementation of wmapro, although for the life of me I am not sure if ffwmapro is available in the repository MPlayer :). I attach a screenshot of this playing using:

```

Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))

```

All the best,

Andrew

---

### Post by mc4man on 2009-11-17
If you're on a 32 bit install then it should suffice to install 32codecs from here
[http://packages.medibuntu.org/karmic/w32codecs.html](http://packages.medibuntu.org/karmic/w32codecs.html)

If you're on 64 bit or want a bit more control then install a newer non repo mplayer
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

Ex.
using ffmpegs wmapro and vlc1 decoders instead on the dmo (w32codecs) decoders

> doug@doug-laptop:~$ mplayer -fs -vc ffvc1 -vo xv '/home/doug/Downloads/Elephant'\''s Dream_10-25_440.wmv' -vo xv
MPlayer SVN-r29821-4.3.4 (C) 2000-2009 MPlayer Team

Playing /home/doug/Downloads/Elephant's Dream_10-25_440.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVC1]  1920x1080  24bpp  1000.000 fps  10155.7 kbps (1239.7 kbyte/s)
Clip info:
 title: Elephant's Dream
 author: Encoded by Ben Waggoner
 copyright: (c) copyright 2006, Blender Foundation / Netherlands Media Art Institute / [www.elephantsdream.org](www.elephantsdream.org)
 comments: Elephant's Dream, encoded to Windows Media VC-1 using the v11 codecs and optimal settings
==========================================================================
Forced video codec: ffvc1
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, floatle, 440.0 kbit/4.77% (ratio: 55000->1152000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
AO: [pulse] 48000Hz 6ch floatle (4 bytes per sample)
Starting playback...


vs (i have to force the dmo audio, 

> Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12  [fs]
Selected video codec: [wmvvc1dmo] vfm: dmo (Windows Media Video (VC-1) Advanced Profile)
==========================================================================
==========================================================================
Forced audio codec: wma9dmo
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 48000 Hz, 2 ch, s16le, 440.0 kbit/28.65% (ratio: 55000->192000)
Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)
==========================================================================


redundant post, very slow typer, ect.

---

### Post by madjinji on 2010-01-07
> **mc4man said:**
> If you're on a 32 bit install then it should suffice to install 32codecs from here
[http://packages.medibuntu.org/karmic/w32codecs.html](http://packages.medibuntu.org/karmic/w32codecs.html)

If you're on 64 bit or want a bit more control then install a newer non repo mplayer
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

Thanx it really helps

---

