---
title: "Sound stopped working! Even after reinstall!"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by alex-desktop79 on 2007-02-08
I have an Audigy 2 LS and yesterday morning, the sound just wouldnt work anymore. It had perfectly in the live cd and after the installation.

But now it wont play. I tried everything here  but that was no help.
I tried posting in absolute beginners talk but that was no help either.
Neither was IRC

I even tried reinstalling linux after reformating my ext3 partition. Sound worked in live cd but I still have the same problem.

And Analog Front (the one it was) is not muted. I tried them all.


Please help me.

---

### Post by wocket on 2007-02-20
I have had the same problem.  I'm running the 64bit Edgy (which I just upgraded to Feisty in hopes of fixing it)  The problem seems to persist regardless of the kernel in use.  I have a SB Audigy Platinum.  Any help would be much appreciated.

---

### Post by wocket on 2007-02-20
ok, go into alsamixer and make sure that IEC958 Optical raw is muted (set to off)   That fixed everything with my digital connection.  Hope that helps!

---

