---
title: "Interesting tearing problem!"
date: 2010-02-09
forum: Multimedia Software
---

### Post by Muminboll on 2010-02-09
I got a pretty interesting tearing problem I would like to share.

First of all, my "tearing" might not really be tearing, its more about unsynched horizontal lines across the screen when its sweeping horizontally or when there is a lot of white in the picture.

Anyways, ive tried pretty much all known media players for both gnome and KDE, tried every single video output in all of them, with and without compiz installed, with radeonHD drivers, the default drivers and the latest ati drivers. With sync to Vblank and probably with all other settings known to man (well not really :D).

The ONLY, and I really mean ONLY way to have the video look perfect is to run MPlayer with gl output in fullscreen! It doesn't work with gl in SMplayer or VLC or KPlayer or any other player, no matter if its a front-end of MPlayer or not. Only thing that works is MPlayer + gl output + fullscreen.

Isn't this a bit odd? Isn't the VLC gl output pretty much supposed to be the same thing? And SMplayer should definitly be the same thing!

A problem is that MPlayer is a bit buggy. It hangs when i try to stream, it flickers with subtitles and other things. Is there any way to use the MPlayer specific gl output for VLC or any front-end for Mplayer?

I got a radeon HD 4600 card btw, running karmic and the latest ATI drivers. 

Any helpful comments would be very much appreciated :)

---

