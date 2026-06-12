---
title: "Video playing in 64 bit kubuntu"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by Gokee2 on 2008-01-07
Hello all,
I installed kubuntu a few days ago on my new 64 bit dual core computer.  I had not really used ubuntu much but had used debian for quite a while.  I figured I should give ubuntu a try. I installed gutsy and last night when trying to get flash to work moved to hardy.   I have a .wmv file (2Fast_2Furious_1080p23.976_51_8Mbps.wmv from the HD on [http://www.drfoster.f2s.com/](http://www.drfoster.f2s.com/)).  When I try to play it mplayer I get:

Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[wmv3 @ 0xf41d80]Extra data: 8 bits left, value: 0
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg M$ WMV3/WMV9)
==========================================================================
==========================================================================
Forced audio codec: mad
Requested audio codec family [wma9dmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wmadmo] (afm=dmo) not available.
Enable it at compilation.
Cannot find codec for audio format 0x162.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...


Some files like oiteaser1080.mov (from [http://www.outsideinthemovie.com/](http://www.outsideinthemovie.com/)) play just fine. 

I have followed [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and added the sources from Medibuntu as it said.  I have w64codecs installed.  I also downloaded some codecs from mplayer and put them in /usr/lib/codecs

Any idea how I can fix this?

Thanks

---

