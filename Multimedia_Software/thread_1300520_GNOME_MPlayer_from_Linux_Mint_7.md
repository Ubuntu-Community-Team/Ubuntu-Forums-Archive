---
title: "GNOME MPlayer from Linux Mint 7"
date: 2009-10-25
forum: Multimedia Software
---

### Post by oohbuntoo on 2009-10-25
Does anyone know if the GNOME MPlayer that comes with Linux Mint 7 is available for Jaunty 9.04?  I've got Linux Mint 7 installed on another laptop and it plays all my movie files perfectly.  No hangups or anything of the sort.  The Movie Player and VLC don't do a comparable job.  Maybe I'm missing some plugins; I doubt it.  What I do know is that GNOME MPlayer plays everything perfectly and I would like install that in Jaunty.

---

### Post by MelDJ on 2009-10-25
this: [http://packages.ubuntu.com/jaunty/gnome-mplayer-dbg](http://packages.ubuntu.com/jaunty/gnome-mplayer-dbg) ?

---

### Post by lidex on 2009-10-25
Do you have multiverse repository enabled? Then:
```
sudo apt-get install gnome-mplayer
```

---

### Post by vinutux on 2009-10-25
gnome-mplayer is a gtk front-end of mplayer. intsall it from repos... The real thing you missed is dome dills (windows media libraries) doenload and install it from here **[http://www.mplayerhq.hu/design7/dload.html]("http://www.mplayerhq.hu/design7/dload.html")** it called binaery codecs....

I think you need to install (extracting) some where like /user/libs/win32.... read documentation come with it.........

---

### Post by vinutux on 2009-10-25
Check this one too...perhaphs more simple..... [http://en.andregondim.eti.br/?p=62]("http://en.andregondim.eti.br/?p=62")

---

