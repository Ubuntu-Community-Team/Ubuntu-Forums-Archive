---
title: "how do i connect a laptop to the tv using a s video cable"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by jwalkeraz84 on 2007-01-23
i have a dell inspiron 630m, it has a s-video hookup on the left handside, so i ran it from the laptop to the tv, when the turn the tv to the correct video setting i get a black screen, i was wondering what i need to do to make this work?

i am new to ubuntu and i really need some help

---

### Post by josesanders on 2007-02-01
You need to find Linux drivers for the video card, which may not be easy for a video device on your motherboard.  What does it say about the video card when you run the command:
$ lspci -v

Support for TV out in linux is just horrible, though, so I wouldn't get your hopes up.

---

