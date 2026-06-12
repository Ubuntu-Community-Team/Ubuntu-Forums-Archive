---
title: "mplayer2 and w32/64 codecs problem"
date: 2013-08-14
forum: Multimedia Software
---

### Post by kapetr on 2013-08-14
Hello,

on U12.04-64b I have installed w32 and w64 codecs from medibuntu repo.

mplayer -vc help gives now:
```

...
wmv9dmo     dmo       working   Windows Media Video 9 DMO  [wmv9dmod.dll]
wmvdmo      dmo       working   Windows Media Video DMO  [wmvdmod.dll]
wmv8        dshow     working   Windows Media Video 8  [wmv8ds32.ax]
wmv7        dshow     working   Windows Media Video 7  [wmvds32.ax]
wmvadmo     dmo       working   Windows Media Video Adv DMO  [wmvadvd.dll]
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile  [wvc1dmod.dll]
...

```

so - it seems to be ok.

But if I try to play wmv9 file: mplayer /tmp/720-304\ WMV9.WMV   (from [http://demo.archermind.com/Test%20Sample/Video/WMV/WMV9/](http://demo.archermind.com/Test%20Sample/Video/WMV/WMV9/) )
I get:
```

...
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
...

```

So - the W32 codec is NOT "working".
The Q is:

- why mplayer claims the wmv9dmo is working ?
- why mplayer do not use it - why it must be compiled again ? 
- Does it mean that to add codec, the mplayer must be every time again recompiled ?!

Thanks for help/explanation.

---

### Post by andrew.46 on 2013-08-14
The *-vc help* command simply parses the inbuilt codecs.conf and need not necessarily relate to the capabilities of your copy of MPlayer. As for recompiling, the 32bit codecs will only work with a 32bit installation of MPlayer.

---

