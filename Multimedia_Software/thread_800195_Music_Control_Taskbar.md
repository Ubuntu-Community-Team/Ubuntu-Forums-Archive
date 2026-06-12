---
title: "Music Control Taskbar"
date: 2008-05-19
forum: Multimedia Software
---

### Post by doubad on 2008-05-19
Anyone know of some software that can be added to make my audio controls (play/stop/next/previous) show up on my taskbar? Or if theres a player that does it on its own?

---

### Post by diaa on 2008-05-19
Assuming you are using GNOME

> Music Applet currently supports Rhythmbox, Banshee and Muine and many others.

```
sudo apt-get install music-applet
```

---

### Post by doubad on 2008-05-19
is there an applet like that that supports audacious?

---

### Post by diaa on 2008-05-19
> **doubad said:**
> is there an applet like that that supports audacious?

Who said music-applet doesn't?

[B]From the website
[/B]>                          Music Applet currently supports the following music players:                     
       
[LIST]
[*]           [Amarok]("http://amarok.kde.org/")
[*]           [Audacious]("http://audacious-media-player.org/")
[*]           [Banshee]("http://banshee-project.org/")
[*]           [Exaile]("http://www.exaile.org/")
[*]           [MPD]("http://www.musicpd.org/")
[*]           [Muine]("http://muine-player.org/")
[*]           [Quod Libet]("http://www.sacredchao.net/quodlibet")
[*]           [Rhythmbox]("http://www.gnome.org/projects/rhythmbox/")
[*]           [VLC]("http://www.videolan.org/vlc/")
[*]           [XMMS]("http://www.xmms.org/")
[*]           [XMMS2]("http://wiki.xmms2.xmms.se/")
[/LIST]


---

### Post by Stochastic on 2008-05-20
Audacious support only came into Music Applet in the 2.3.0 release, Hardy's repos carry the 2.2.1 release.  If you'd like audacious support, you'll need to download from the website and compile from source, which can add a bunch of overhead to your computer as the compilation process will require a bunch of python dev packages.

---

