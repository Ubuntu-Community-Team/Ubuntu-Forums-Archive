---
title: "VLC as the default player for audio cd's"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by almalaci on 2007-03-05
I'd like to use VLC as the default player for audio cd'd. I set VLC to play audio cd's when inserted under Removable Drives and Media and VLC starts but it doesn't start playing the cd. Any help on that?

---

### Post by kerry_s on 2007-03-06
Check here-> [http://www.videolan.org/](http://www.videolan.org/)
Your going to want skins any way. :)

---

### Post by almalaci on 2007-03-06
Sure, I've been through that but haven't found anything helpful..

---

### Post by kerry_s on 2007-03-06
I cant get it to work, sorry.

I think gxine can autoplay.

---

### Post by almalaci on 2007-03-06
> **kerry_s said:**
> I cant get it to work, sorry.

I think gxine can autoplay.

I tried --play-and-stop but it doesn't work for me either. It's interesting that rhythmbox, gxine and gnome-cd all have the same behaviour. They all start but no playback. I couldn't find a command line switch for rhythmbox and gxine like VLC's --start-and-stop. Gnome-cd has a --play switch and it's also in the GUI but still it doesn't play.
Could it be something with my system?

---

### Post by tassoman on 2007-03-15
I think gnome-cd is enough but i dunno how to make it default player on autolay :confused:

---

### Post by arcx.rw on 2008-01-17
> **almalaci said:**
> I'd like to use VLC as the default player for audio cd'd. I set VLC to play audio cd's when inserted under Removable Drives and Media and VLC starts but it doesn't start playing the cd. Any help on that?
Try ```
vlc cdda:///dev/scd0
``` in Removable Drives and Media. Replace "/dev/scd0" with your device. If you want dvd's to be auto-played with VLC:
```
vlc dvd:///dev/dvd

```.

---

### Post by mc4man on 2008-01-17
deleted - redundant

---

