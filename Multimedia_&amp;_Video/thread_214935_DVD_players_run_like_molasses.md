---
title: "DVD players run like molasses"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by Shrindi on 2006-07-13
I can't figure out for the life of me why even after I install the xine backend with all the codecs it takes forever for *any* of the dvd frontends to load up the dvd for playback. I have tried gxine, totem-xine, vlc, and even mplayer. 

I ditched Debian Stable because it takes forever for up to date digicam programs to hit stable (I'm looking at *you* F-Spot!). 

Now, I have the latest digicam goodness without the dvd coolness.](*,) 

Any ideas out there?:confused:

---

### Post by Paerez on 2006-07-13
run:
```
# sudo hdparm /dev/cdrom
```
to see if dma is enabled. If dma is off it can severly reduce performance.

[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by Shrindi on 2006-07-14
DMA is enabled. I verified that it is enabled in the config file. All the codecs are installed. I also went and tested video under Systems-Preferences-Multimedia Systems Selector. Mplayer, Xine ui, Gxine, Totem-Xine, VLC all hang. 

](*,) 

I've had a better time with "configure Xorg/Xfree86 yourself" distros.

---

### Post by Paerez on 2006-07-14
do you have this in your xorg.conf device section?
```
Option 		"VideoOverlay" 		"on"
```

---

