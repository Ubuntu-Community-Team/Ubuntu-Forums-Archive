---
title: "Converting video formats (xvid to divx)"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by BightningLug on 2008-03-22
I have several video files that I want to put on cd or dvd and play them in my dvd player. It is divx compatable and does a really good job of playing divx files. I just tried putting an xvid file on a cd to see if it would play it, and sadly, it doesn't.

I'm wanting a way to convert these xvid files into compatable divx files so that I can play them on my dvd player. I've searched for Linux programs to do such a task and haven't been able to find any. Searching for xvid to divx didn't get any results on this forum either, so I'm a bit lost.

Are there any freely available programs for Linux that will do the job I'm wanting done? If so, where can I find/install it?

---

### Post by gambrjl on 2008-03-22
pretty sure mencoder will do the job for ya

[Mencoder](http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html)

---

### Post by rsambuca on 2008-03-22
> **BightningLug said:**
> I have several video files that I want to put on cd or dvd and play them in my dvd player. It is divx compatable and does a really good job of playing divx files. I just tried putting an xvid file on a cd to see if it would play it, and sadly, it doesn't.

I'm wanting a way to convert these xvid files into compatable divx files so that I can play them on my dvd player. I've searched for Linux programs to do such a task and haven't been able to find any. Searching for xvid to divx didn't get any results on this forum either, so I'm a bit lost.

Are there any freely available programs for Linux that will do the job I'm wanting done? If so, where can I find/install it?

Xvid simply uses the same mpeg4 asp video that DivX uses, so there shouldn't be any problems using them in your player.  What is the player, and what are the files?

---

### Post by BightningLug on 2008-03-22
> **gambrjl said:**
> pretty sure mencoder will do the job for ya

[Mencoder](http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html)
I installed MEncoder, but it doesn't list divx as one of the available video codecs. How do I go about installing that?

> Xvid simply uses the same mpeg4 asp video that DivX uses, so there shouldn't be any problems using them in your player. What is the player, and what are the files?
Even though you say Divx and Xvid use the same mpeg4 asp video, the DVD player won't play the xvid file. I doubt it is due to the file extention being avi instead of divx or xvid, but could it be? Anyway, here's the information you asked for.

The player is a Magnavox DVD Player MWD7006 with Progressive Scan.

The file is a movie with these properties-
Duration: 1 hour 24 minutes 44 seconds

Video:
Dimensions: 624 x 352
Codec: XVID MPEG-4
Framerate: 25 frames per second
Bitrate: N/A

Audio:
Codec: MPEG-1 layer 3
Channels: Stereo
Sample rate: 48000 Hz
Bitrate: 128 kbps

---

### Post by BightningLug on 2008-03-23
I did a second test with a different Xvid file and it seemed to play just fine. I guess there's just a problem with the one. I compared the properties of both files and the only differences are the duration and dimensions.

---

