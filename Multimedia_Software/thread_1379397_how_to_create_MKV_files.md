---
title: "how to create MKV files"
date: 2010-01-12
forum: Multimedia Software
---

### Post by nixIT on 2010-01-12
Hello all,

I received a popcorn hour set top box for Xmas, and I am trying to figure out the best way to convert my extensive DVD collection to MKV files to play on the PCH.

I know I could just create an ISO of the DVD, but that would take up 4-8 gig per movie, where from what I've read, MKV offers GREAT audio and video quality at a fraction of the space.

Is there any software packages out there for linux that would allow me to rip my DVD's to MKV?  if so, will they allow me to just rip the movie part of the disc, and not the extra's or menu?

--nixIT

---

### Post by lovinglinux on 2010-01-12
Although MKV is great and I love it, specially because it allows multiple streams, including subtitles, it is just a container. It is not responsible for the size/quality of the video. What makes the difference is that usually people encode videos with h.264, when using mkv format, which gives you great quality on less space.

You can convert the DVD vob files using mencoder. See [http://ubuntuforums.org/showthread.php?p=8541939](http://ubuntuforums.org/showthread.php?p=8541939)

---

### Post by techstop on 2010-01-12
I've used handbrake too, it's very easy.

[http://handbrake.fr/](http://handbrake.fr/)

There's .debs for ubuntu in the download section.

---

### Post by llama320 on 2010-01-12
> **techstop said:**
> I've used handbrake too, it's very easy.

[http://handbrake.fr/](http://handbrake.fr/)

There's .debs for ubuntu in the download section.

+1 for handbrake. If you want a repository for it you can add the following to sources.list:

```

deb http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu karmic main

```
More info here: 
[https://launchpad.net/~handbrake-ubuntu/+archive/ppa]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa")

---

### Post by nixIT on 2010-01-13
Thanx for the info. 

I tried handbrake for windows in the past, and it would just stop responding.  I will give it a shot on my ubunut box.

--nixIT

---

