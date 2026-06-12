---
title: "Best DVD App?"
date: 2011-10-13
forum: Multimedia Software
---

### Post by mattyjm on 2011-10-13
Hi Guys, I am new to the Linux platform and I have recently installed ubuntu 11.

I am wondering what is the best soft ware/app to install to play DVD's? as I cant play them with the standard app that come with ubuntu.

Cheers

---

### Post by yooozy on 2011-10-13
you got various alternatives to the default video player, I personally use totem and vlc
however you have to install "ubuntu restricted extras" it's a package of different codecs

you're welcome among us

---

### Post by mc4man on 2011-10-13
You are going to need libdvdcss2 to decrypt commercial dvds

So **after** installing ubuntu-restricted-extras and or vlc then open a terminal, copy & paste this in.
ctrl+alt+t will open a terminal or search terminal in the dash
```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by alphacrucis2 on 2011-10-13
VLC. Same as I use on Windows. Yes you will need to install libdvdcss2 to play commercial DVD's.

---

### Post by andrew.46 on 2011-10-14
Another vote here for vlc although some might prefer the commandline MPlayer or its guis SMPlayer or UMPlayer...

---

### Post by hsoulen on 2011-10-14
1 Vote for SMPlayer.

Mplayer as a backend is awesome, VDPAU and I get 1080p video through HDMI on a netbook (comes in handy in hotels).

Cheers,

---

### Post by Perfect Storm on 2011-10-14
Gnome Mplayer got my vote.

---

