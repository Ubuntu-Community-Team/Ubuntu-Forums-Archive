---
title: "VAAPI Acceleration H264 possilbe in Mythtv? Trough ffmpeg?"
date: 2010-06-15
forum: Mythbuntu
---

### Post by seppl82 on 2010-06-15
Is it possible to get VAAPI Acceleration in Mythtv?
I've installed all libs and the mplayer from here:

[http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/)

But in Mythtv internaly (for instance if i watch TV) i can't get hardware acceleration.
Is there a trick to get this Working?

I've read that ffmpeg will be also patched with the installation of mplayer.
Does this mean if i use ffmpeg as decoder i'll get HW Acceleration im mythtv?

here a quote from 
[http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/) (Scroll down to see this)
```
These patches add VA API support to FFmpeg and MPlayer.

HW video decode capabilities depend on the actual VA API implementation. Besides, from an MPlayer perspective, only full-offload (VLD) of the video is supported for the following codecs:

    * MPEG-2
    * MPEG-4 ASP (DivX)
    * H.263 (MPEG-4 short-video header variant)
    * MPEG-4 AVC (H.264)
    * Windows Media Video 9 (WMV3)
    * Windows Media Video 9 Advanced (VC-1 Advanced profile)
```

---

### Post by ian dobson on 2010-06-15
Hi,

Mythtv will need to be patched/updated to support VAAPI, just as it was for VDPAU on NVidia cards. I've not seen any posts on the dev mailing list about VAAPI so I don't know if anyone is working on it.

As Mythtv doesn't use the normal ffmpeg libraries (mythtv compiles it's own local copy) as the devs find it too hard to support multiple versions of ffmpeg just installing ffmpeg won't help.

The only solution would be to use mplayer with VAAPI support as the default for TV/Video playback.

Regards
Ian Dobson

---

### Post by seppl82 on 2010-06-15
Is it possible to configure Mplayer for TV playback in mythtv?

I don't think so.

---

