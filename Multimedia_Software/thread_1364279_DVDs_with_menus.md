---
title: "DVDs with menus"
date: 2009-12-25
forum: Multimedia Software
---

### Post by MyR on 2009-12-25
Can totem play DVDs with menus?  The totem-xine backend is no longer available in Ubuntu 9.10.

Every thread I see about this issue says "Use VLC! Use VLC!"
One problem with vlc is that it doesn't recognize my multimedia keys.  Another is that it doesn't disable the screensaver.

Thanks

---

### Post by lovinglinux on 2009-12-25
I don't know about totem, because I don't use it, but [smplayer](apt:smplayer), which is another frontend for mplayer, can. It is my default video player. I only use VLC when the video doesn't play well on smplayer, which is pretty rare.

---

### Post by MyR on 2009-12-25
It doesn't look like smplayer supports dvd menus either.  Furthermore, it turns on subtitles by default.

On 9.04 it was as easy as installing the xine backend for totem, but now it's gone from the repo.

---

### Post by lovinglinux on 2009-12-25
> **MyR said:**
> It doesn't look like smplayer supports dvd menus either.  Furthermore, it turns on subtitles by default.

On 9.04 it was as easy as installing the xine backend for totem, but now it's gone from the repo.

Well, install xine player then.

---

### Post by Melcar on 2009-12-25
Totem with gstreamer (the Ubuntu default) does support menus.  Xine based players do as well.

---

### Post by MyR on 2009-12-25
> **Melcar said:**
> Totem with gstreamer (the Ubuntu default) does support menus.  Xine based players do as well.

Ah, right you are!  They must have added support.

---

### Post by rvm4000 on 2009-12-25
> **MyR said:**
> It doesn't look like smplayer supports dvd menus either.

Preferences -> Drives -> Enable DVD menus (experimental)

But yes, support for DVD menus is not good. Actually support for DVD menus **in mplayer** is not good. I can't do anything else until it's improved in mplayer.

> **MyR said:**
> 
Furthermore, it turns on subtitles by default.


That can be turned off: see Preferences -> Subtitles -> Select first available subtitle.

---

