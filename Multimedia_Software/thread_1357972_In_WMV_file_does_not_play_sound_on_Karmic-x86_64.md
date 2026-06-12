---
title: "In WMV file does not play sound on Karmic-x86_64"
date: 2009-12-17
forum: Multimedia Software
---

### Post by inspirra on 2009-12-17
```
$ mplayer -ac help | grep wma
wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]
ffwmav1     ffmpeg    untested  DivX audio v1 (FFmpeg)  [wmav1]
ffwmav2     ffmpeg    untested  DivX audio v2 (FFmpeg)  [wmav2]
``````
$ aptitude --disable-columns -F '%c %p %v' search codec ^mplayer$ ^ffmpeg$ | grep ^i
i ffmpeg 4:0.5+svn20090706-2ubuntu2
i gnome-codec-install 0.4.1ubuntu1
i libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3+medibuntu1
i mplayer 2:1.0~rc3+svn20090426-1ubuntu10.1
i non-free-codecs 4medibuntu1
i w64codecs 20071007-0medibuntu2
``````
$ mplayer Amazing_Caves_1080.wmv
<...>
Requested audio codec family [wma9dmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wmadmo] (afm=dmo) not available.
Enable it at compilation.
Cannot find codec for audio format 0x162.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
<...>

```Sound in this file does not play on Karmic-x86_64:
```
- Linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64
- w64codecs 20071007-0medibuntu2
```But played perfectly on Karmic-i686
```
- Linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
- w32codecs 20071007-0medibuntu5
```Also, the sound in this wmv-file plays perfectly in Jaunty-x86_64.

---

### Post by mc4man on 2009-12-17
You'll need to either get an mplayer from a ppa or build your own

W64codecs is pretty much worthless, but mplayer can decode wma3 (0x162) thru avcodec (ffwmapro

The problem is that in karmic the ffmpeg libraires have been stripped out of the repo build of mplayer, so now mplayer depends on the system installed shared ffmpeg libs. 
The version of ffmpeg used in karmic does not support wma3

Example of any recent mplayer build decoding wma3
> doug@doug-laptop:~$ mplayer -ac ffwmapro '/home/doug/Desktop/wmat/w3.wma' 
MPlayer SVN-r29948-4.3.4 (C) 2000-2009 MPlayer Team

Playing /home/doug/Desktop/wmat/w3.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: Flyaway
 author: Joan Osborne
==========================================================================
Forced audio codec: ffwmapro
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, floatle, 192.0 kbit/6.80% (ratio: 24002->352800)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)



---

