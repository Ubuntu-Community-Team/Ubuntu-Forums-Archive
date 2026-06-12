---
title: "Problem with guitar pro"
date: 2011-06-29
forum: Multimedia Software
---

### Post by tivatranquio on 2011-06-29
I have a problem with guitar pro in linux, i've tried both 5.2 (on wine) and 6 (for linux) but I had problems in all two.
In guitar pro 5.2 the midi works great but often those errors occour
[[IMG]http://img706.imageshack.us/img706/9813/errorgp2.png[/IMG]]("http://img706.imageshack.us/img706/9813/errorgp2.png")

And in guitar pro 6 there is a problem with latency: if I open the program and press play for the first time, the music is synchronized with the graphical interface, then if I click in an another point of the song, I heard for few seconds the music from the old position of the cursor. After that I heard the right music but it's too late, the graphical interface is no synchronized.

I use ubuntu 10.10 and qsynth for the midi.

(Sorry for my english)

---

### Post by cchhrriiss121212 on 2011-06-29
Have you tried tuxguitar?

---

### Post by tivatranquio on 2011-07-01
Yes, I've tried it, but I prefer Guitar pro.

---

### Post by cchhrriiss121212 on 2011-07-02
Try posting in the WINE sub-forum.

---

### Post by tivatranquio on 2011-07-07
I've resolve the problem with guitar pro 5.2 and wine:

sh winetricks gdiplus

---

