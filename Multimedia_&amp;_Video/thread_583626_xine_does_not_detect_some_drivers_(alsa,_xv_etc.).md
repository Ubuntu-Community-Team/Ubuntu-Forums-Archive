---
title: "xine does not detect some drivers (alsa, xv etc.)"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by AllesMeins on 2007-10-20
Hi,

since my upgrade to gutsy xine is missing some important drivers. xine --help presents me with the following possible drivers:

```

  -V, --video-driver <drv>     Select video driver by id. Available drivers:
                               aadxr3 none fb
  -A, --audio-driver <drv>     Select audio driver by id. Available drivers:
                               null oss none file

```

All other players (xmms, mplayer) are still working fine with alsa, only xine seems to have lost the ability to work with alsa. Same for the video drivers. The important drivers that are working flawless with mplayer are missing. Running xine --bug-report shows that this is indeed a problem:

```
main: probing <aadxr3> video output plugin
main: probing <none> video output plugin
main: probing <fb> video output plugin
main: all available video drivers failed.
```

The complete bug-report can be found [here]("http://ubuntuusers.de/paste/16512/").

Can anybody help me finding a way to get xine working again?

---

