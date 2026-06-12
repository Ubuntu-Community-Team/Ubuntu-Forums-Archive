---
title: "Slow/jerky 720p playback in Karmic"
date: 2010-07-22
forum: Multimedia Software
---

### Post by sosaited on 2010-07-22
I have been reading a lot posts regarding slow HD video playback, but after applying an apparent fix that messed up my xorg, I am creating a separate topic so I can get some help specific to my system.

My system is an Old P4 3.0Ghz with HT, 1GB RAM and Intel GMA 900 (915GL) on Asus P5GL-MX. I am using Ubuntu 9.10 32bit, and have tried the videos on VLC, Totem and SMplayer. SMplayer is a bit worse than VLC, The same videos work fine on my WIndows XP (Though I have to close Firefox as my profile there uses 300MB of memory). I am only trying 720p MKV videos

CPU usage as shown in top never exceeds ~90%, which I think means ~50% as Ubuntu shows separate usage for both threads?

Any suggestions/solutions are welcome.

Thanks

---

### Post by lovinglinux on 2010-07-22
I had the same CPU a couple of months ago and I also couldn't watvh 720p. The main problem was lack of vdpau support for my video card, which forces the video to be processed by the single core CPU, which can't handle it.

I could only watch 720p videos after upgrading to Core2Duo.

---

### Post by sosaited on 2010-07-22
But they run fine on Windows with the same graphics. And I don't think it has GPU decoding there either.

---

### Post by lovinglinux on 2010-07-22
EDITED: not relevant

---

### Post by lovinglinux on 2010-07-22
I just realized you are not even using nVidia ](*,)

[http://en.wikipedia.org/wiki/Intel_GMA_900#Linux](http://en.wikipedia.org/wiki/Intel_GMA_900#Linux)

---

### Post by sosaited on 2010-07-23
I have just noticed that VLC 1.1 on Windows just uses 30%-50% CPU on my Windows XP, even though it sometimes used to go up 90% in some HD videos. So it is definitely not GPU or even CPU bottleneck.

And I have xorg intel drivers installed already.

Any settings recommendation?

---

