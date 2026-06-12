---
title: "vlc problem"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by kinpower on 2008-03-15
Hi, i'm having a problem with VLC, whenever I try to play a music file in VLC it just closes itself, i've opened it in the terminal and when i do that i get

Creating link /home/nik/.kde/socket-Nik-Laptop.
can't create mcop directory

Anyone know what to do

Also i'm using Ubuntu 7.10 Gutsy Gibbon

Thanks in advance,
Nik

---

### Post by xc3RnbFO8P on 2008-03-15
Here is a simple solution hope it works:

> sudo gedit /etc/libao.conf

Chance **default_driver=alsa09** to **default_driver=alsa**

If it don't works, just chance it back.

Another solution is to create > **.mcop** folder in home folder  (I think you should try that first)

---

### Post by kinpower on 2008-03-15
thanks for the suggestions, but the 1st didnt work, and there is already a .mcop folder

---

### Post by xc3RnbFO8P on 2008-03-15
And do yu have this socket folder?

---

### Post by kinpower on 2008-03-15
i can't beleive i didn't think of that, i just created the socket folder and now it works fine

Thanks

---

### Post by xc3RnbFO8P on 2008-03-15
Mistake

---

### Post by kinpower on 2008-03-16
firstly i don't know how, and secondly, theres a new thing, not major, but the quality is bad, and i know its not the MP3 because it comes out brilliant when I listen to it anywhere else
Anyway when I load through the terminal, when i start a song i get this
[00000468] oss audio output error: cannot open audio device (/dev/dsp)
[00000468] arts audio output error: arts_init failed (can't connect to aRts soundserver)
any idea how to fix it?

Thanks in Advance Nik

---

### Post by xc3RnbFO8P on 2008-03-16
We are talking about Amarok?

In Amarok settings> engine choose alsa.
Hope it helps.

---

### Post by kinpower on 2008-03-16
No, i'm still talking about vlc, every media player apart from vlc just froze when i tried to play anything

---

### Post by xc3RnbFO8P on 2008-03-16
In VLC, preferences> Audio> Output Modules  check advance box and choose alsa

---

### Post by xc3RnbFO8P on 2008-03-16
Did you install w64codec:
> sudo apt-get install w64codecs

---

