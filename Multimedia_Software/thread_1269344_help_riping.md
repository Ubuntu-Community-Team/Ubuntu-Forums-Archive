---
title: "help riping"
date: 2009-09-18
forum: Multimedia Software
---

### Post by doctor who on 2009-09-18
howdy all.
i want to rip my CD's  with sound juicer (audio CD extractor)

I found this topic (which was very helpful)
[http://ubuntuforums.org/showthread.php?t=1095428](http://ubuntuforums.org/showthread.php?t=1095428)

I don't need 320 KBPS because it takes allot of place on my player, but i do want high brite
so i tried vbr-quality 0 (what should be the best) but it seems as i get constant 150 KBPS :confused:

this is my pipeline :

> audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1 vbr=4 vbr-quality=0 ! id3v2mux 

---

### Post by doctor who on 2009-09-21
wsup

---

### Post by doctor who on 2009-10-01
why is there no answer? where are everybody?

---

### Post by ron999 on 2009-10-01
Hi
Other people have had these problems too.
Read this thread, see if there's a solution:- [http://ubuntuforums.org/showthread.php?t=599883]("http://ubuntuforums.org/showthread.php?t=599883")

---

