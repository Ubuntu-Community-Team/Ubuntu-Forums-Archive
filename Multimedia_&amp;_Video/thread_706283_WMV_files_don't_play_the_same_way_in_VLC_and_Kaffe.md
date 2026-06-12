---
title: "WMV files don't play the same way in VLC and Kaffeine"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by Tosa on 2008-02-24
I use both VLC and Kaffeine. I guess that both players use same codecs, but very often the same wmv file that plays correctly in VLC is distorted in Kaffeine.

Does anyone know how to remedy this? I must admit that I prefer Kaffeine, love the feature that it stops plying when minimized...

---

### Post by kaens on 2008-02-24
VLC uses it's own, internal codecs. As far as I know, there's nothing that can be done about this.

---

### Post by gunksta on 2008-02-24
Kaffeine (by default) uses libxine for rendering video. As mentioned previously, VLC uses libvlc to render videos. The only kaffeine will be able to use libvlc to render video is if someone writes a a wrapper to allow Kaffeine to use libvlc. 

At this point, I really doubt this will happen. KDE4 is going to use Phonon as a common abstraction layer between things like libxine and libvlc and KDE apps like Kaffeine. I agree that VLC often does a better job rendering wmv files but I think it's probably a better use of time to enable phonon to use vlc rather than to focus on Kaffeine at this point.

---

### Post by ajgreeny on 2008-02-24
I have the same problem as you with some wmv version 9 files, which do play fine in vlc, but not in totem or kaffeine.  I dislike vlc, however, and find its sound quality is usually pretty poor and jumpy, so I always use mplayer for those difficult files and that is much, much better.  Give it a try and I think you'll like it.

---

### Post by Tosa on 2008-02-24
I was hopping I would be able to fix Kaffeine somehow. I really like it, but it's not that big deal. I'll give mplayer a try.

Thanks everybody for your input.

---

### Post by gunksta on 2008-02-25
If you are trying to use KDE integrated apps, KMplayer uses mplayer while sporting a spiffy KDE GUI.

---

