---
title: "I can't play videos in my ubuntu !&#1613;"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by Saleh on 2008-02-08
Hi, :)

When I run any video file through any program (i.e. tetom or VLC) the program suddenly closed !

Even before the move starts !

I've tried to open lot of videos, with different types ( avi, wmv, ogg) and the same problem  occurs 

And i am a new for Ubuntu, So can any one Please help me :(

---

### Post by yangyuruc on 2008-02-08
using terminal to open player
post the error messages.
when playing avi and other windows format video
make sure you have installed w32codes

---

### Post by eye208 on 2008-02-08
Turn off Compiz (=desktop effects)

or

configure your media player to use X11 output (=software rendering) instead of XVideo. OpenGL output might work too, depending on your graphics card.

---

### Post by Saleh on 2008-02-08
Thanks yangyuruc for your replay, 

But I have a quite stupid question: How can I run it from the terminal ?

---

### Post by Saleh on 2008-02-08
> **eye208 said:**
> Turn off Compiz (=desktop effects)

or

configure your media player to use X11 output (=software rendering) instead of XVideo. OpenGL output might work too, depending on your graphics card.

You're right !

When I trun off the GL desktop, every thing works will !

So how can I have both, GL & Videos ?

---

### Post by eye208 on 2008-02-08
> **Saleh said:**
> So how can I have both, GL & Videos ?
As I said before, switch the player to X11 or OpenGL output instead of XVideo.

---

### Post by Saleh on 2008-02-08
> **eye208 said:**
> As I said before, switch the player to X11 or OpenGL output instead of XVideo.

OK ... Now every thing works well,

Thanks eye208 :)

---

