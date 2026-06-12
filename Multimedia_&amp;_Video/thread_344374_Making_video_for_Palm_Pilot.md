---
title: "Making video for Palm Pilot"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by Keith_Beef on 2007-01-22
I've been trying to make an ASF file, using the mencoder and the msmpeg4 codec, as described in 
[http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/encoding.html](http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/encoding.html)

My palm still won't play the video, though.

Has anybody managed to get this working, and can help me out?


Beef.

---

### Post by crispy_420 on 2007-01-23
is it a plam os or windows?

most palms use a player called kinoma player. it uses it's own special format. the way to make files is through kinoma producer that is windows only and it will cost you.

---

### Post by Keith_Beef on 2007-01-23
> **crispy_420 said:**
> is it a plam os or windows?

most palms use a player called kinoma player. it uses it's own special format. the way to make files is through kinoma producer that is windows only and it will cost you.

It's a PalmOS model (a tungsten T5).

When I look at a short video that was already on the Palm, it says:
$ file /media/hdb6/TungstenT5.asf
/media/hdb6/TungstenT5.asf: Microsoft ASF



Beef.

---

### Post by timseal on 2007-01-25
Have you tried The Core Pocket Media Player? (TCPMP)
It works very well on my (somewhat aged) Tungsten E.
It might not play ASF files though.   I have had good results with ffmpeg: two pass, xvid, bitrate ~ 200, resize to whatever your palm screen size is (mine is 320x320, yours is either that or 320x480) and most importantly change the frames per second to 12.5 or 15. 

hope that helps,

tim

---

### Post by Bigdeath on 2007-11-11
Anyone know where to get kinoma for a discount (free)?

---

### Post by Bigdeath on 2007-12-07
tcpmp is good for video i have found. But for youtube videos the best place to go is a website called blueapple.mobi

---

