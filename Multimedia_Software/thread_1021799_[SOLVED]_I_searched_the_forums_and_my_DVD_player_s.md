---
title: "[SOLVED] I searched the forums and my DVD player still &amp;quot;cannot read from resource&amp;quot;"
date: 2008-12-25
forum: Multimedia Software
---

### Post by punkbohemian on 2008-12-25
I tried everything in the [comprehensive media and video how-to]("http://ubuntuforums.org/showthread.php?t=766683"), installed the restricted extras and libdvdcss2, but I still get a "cannot read from resource error" when trying to play a DVD in Totem and VLC just crashes when I try to open a DVD. I also wasted a reset changing the region setting on my DVD-ROM (for some reason it was set to RC2 in Linux even though it was RC1 when I got my system).

Can anyone advise me on what to do from here? Thanks.

---

### Post by albinootje on 2008-12-26
> **punkbohemian said:**
> I tried everything in the [comprehensive media and video how-to]("http://ubuntuforums.org/showthread.php?t=766683"), installed the restricted extras and libdvdcss2, but I still get a "cannot read from resource error" when trying to play a DVD in Totem and VLC just crashes when I try to open a DVD. I also wasted a reset changing the region setting on my DVD-ROM (for some reason it was set to RC2 in Linux even though it was RC1 when I got my system).

Can you confirm that libdvdcss2 is installed ? Just in case.
```

dpkg -l|grep libdvd

```
Do you see any errors in the /var/log/kernel.log* and /var/log/syslog* files ?
And can you try smplayer and xine for playing a DVD ?

---

### Post by punkbohemian on 2008-12-29
I do have libdvdcss2 installed, as well as libdvdread4 (I think that's what it's called, it was in one of the fix suggestions I found in the official docs).

I managed to get some DVD playback, but it was working a little wonky at first. The only program that lets me access menus (kinda important for TV series) is gxine, though it has a habit of displaying everything as if there was a blue filter. I searched the forums, and figured out that it was because of NVIDIA's drivers and all I needed to do was min/max the hue in the video settings.

I think everything is working ok (for now), though I'm not a big fan of gxine (due to certain characteristics of the toolbar). Are there any other programs that will recognize DVD menus? Thanks.

---

### Post by albinootje on 2008-12-29
> **punkbohemian said:**
>  I think everything is working ok (for now), though I'm not a big fan of gxine (due to certain characteristics of the toolbar). Are there any other programs that will recognize DVD menus? Thanks.

Which other players did you try ? Ogle can do DVD menus.

---

### Post by punkbohemian on 2008-12-29
I've tried Totem (generally my fav), VLC, SMPlayer, Gnome MPlayer, and MPlayer Movie Player. I haven't heard of Ogle, I'll check it out.

---

### Post by mc4man on 2008-12-29
Totem-xine and vlc both support dvd menus quite fine. If your having problems with disk navigation maybe post what version of vlc your using and what release of ubuntu.

---

