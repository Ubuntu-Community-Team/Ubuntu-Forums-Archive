---
title: "amarock :&quot;ticks&quot; and stutter when playing flac"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by zeltak on 2007-11-15
hi

im in the process of changing from kde to gnome and giving ubuntu a real try (ive always used kubuntu). I have most of my music collection in flac. In kubuntu gutsy 64 it works great. In ubuntu gutsy 64 bit mp3 plays fine yet i get this annoying tick or stutter in flac files every 304 seconds...is there any solution for this

thx 

zeltak

---

### Post by zeltak on 2007-11-18
anyone? it really drives my nuts..most of my collection is FLAC and i cant listen to music in Gnome :-k

thx in advance

zeltak

---

### Post by LondoMollari on 2007-11-18
Hey.  I know Amarok is a great player, but personally I like XMMS better. You could try to install it together with libflac7 and XMMS-flac. I hope it works out for you. If not, you may want have a look at this thread [http://ubuntuforums.org/showthread.php?t=272625&highlight=flac](http://ubuntuforums.org/showthread.php?t=272625&highlight=flac) about some issues regarding the latest versions of the packages I just mentioned. (I know XMMS with it's default skin looks terrible, but it is compatible with winampskins... just in case looks are important to you)

... actually I just got an idea... maybe the soundproblems you are having are related to the the latest libflac7 package... you could try to downgrade to 1.1.2-5ubuntu2 ... just a thought...

---

### Post by zeltak on 2007-11-19
thx

how do you downgrade btw? ive never done that

thx

zeltak

---

### Post by LondoMollari on 2007-11-19
There's an explanation on how to downgrade the the packages i mentioned in the thread i linked to.
If  you are not familiar with the package manager, it is located under System -> Administration -> Synaptic Package Manager...

Hope it works out for you!

---

### Post by zeltak on 2007-11-20
Hi again

Ok..an update. I couldn't do the flac downgrade (i dont have the libflac7 installed at all..its not in the repositories..all i have is libflac8)  But....i noticed that when i change the engine to Oss instead of Alsa FLAC works?!? so i guess the problem is with Alsa but i have no idea what to do next...


thx

Zeltak

---

