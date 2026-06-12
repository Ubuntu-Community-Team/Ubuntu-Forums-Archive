---
title: "Ubuntu 12.04 won't play videos, even after installin Ubuntu Restricted Extras."
date: 2013-10-19
forum: Multimedia Software
---

### Post by Stevensthunar on 2013-10-19
Tried all players. Every of them play the sound, but they wont play the video.

---

### Post by TheFu on 2013-10-19
Which video codecs are failing?  h.264, mpeg4, mpeg2, mpeg1, AVC, xvid, divx, or some proprietary files like mov, qt, rm, wmv?

Does VLC play the videos? ( If VLC can't play it, I don't need to see it.)  Seriously, VLC should handle most video codecs.

Does youtube work?

If the resolution for the files are relatively low - 480 or less - and the video codecs are open, pretty much any computer should play them fine. Of course, video drivers can get in the way.

---

### Post by Dean28 on 2013-10-19
> **Stevensthunar said:**
> Tried all players. Every of them play the sound, but they wont play the video.
Did you install libdvdcss?
```
[COLOR=#333333][FONT=UbuntuMono]sudo /usr/share/doc/libdvdread4/install-css.sh[/FONT][/COLOR]
```

---

### Post by Stevensthunar on 2013-10-19
Hi. I fixed the problem. Installed x264 package and everything works fine. (except bluray videos, (sadly) i have a 1024x768 monitor)
:KS

---

