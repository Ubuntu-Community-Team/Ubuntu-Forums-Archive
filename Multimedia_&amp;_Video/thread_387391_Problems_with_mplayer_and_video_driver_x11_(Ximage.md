---
title: "Problems with mplayer and video driver x11 (Ximage/Shm)"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by romaluca on 2007-03-18
I must use the driver x11 (Ximade/Shm) in mplayer beacuse it is the only driver that works with my compiz

However some day ago i have delete all settings in home directory and now when i try to resize the video, it not resize. 
It remain in the original size.

What i can do to resolve this problem?

The actually settings of my mplayer are:

-- AUDIO: alsa
--VIDEO:  X11  (Ximage/Shm)   and Enable double buffering is checked
--CODEC & DEMUXER: video codec family: Win32/VfWex video codec;  audio codec family: FFmpeg
--MISC are checked:
Enable post processing, Save window position, Stop XScreenSaver,AutoSynch On/Off

---

### Post by romaluca on 2007-03-19
up

---

### Post by DraconPern on 2008-01-11
Same problem here.

---

### Post by ubuntu-freak on 2008-01-11
Do you have intel graphics? If so you should 
 
sudo dpkg-reconfigure xserver-xorg
 
I did that and now I can use the superior xv video driver. 
 
Nathan

---

### Post by dogson on 2008-01-11
add this to your ~/.mplayer/config

vo=x11
zoom=true

---

