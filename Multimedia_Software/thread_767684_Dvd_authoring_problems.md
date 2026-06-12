---
title: "Dvd authoring problems"
date: 2008-04-25
forum: Multimedia Software
---

### Post by zaius55 on 2008-04-25
Hello,

DVD flick is a great program, does everything I want except create menus.  It runs well in wine, except the beta version (which creates menus).  I'm happy with Tovid to create dvd suitable MPEGS, however qdvdauthor is giving me problems.

Whenever I try to add videos to a project All the videos just say "error" and cannot be added.  I'm running 8.04 on AMD64.  Anyone have this issue?

Thanks!

---

### Post by wltdwiz on 2008-05-05
try mandvd :guitar: it works good

---

### Post by lngndvs on 2008-05-06
I have the same problem on an AMD 64 system.  I found the following note, but I will have to compile from source to fix this. 

[http://www.nabble.com/Re%3A-New-user---Add-Movie-displays-Error-to15039670.html](http://www.nabble.com/Re%3A-New-user---Add-Movie-displays-Error-to15039670.html)

[INDENT]
I had the same problem. In qplayer/engines/xineinfo.cpp (using
qdvdauthor-1.0.0-4) I changed line 371 from
    if (iMSecOffset == 0)
to
    if (iMSecOffset != 0)

That solved the problem for an uncached file where the == test prevents
 an initial play/stop of the xine engine. I am not sure whether this the
right place for this change but it works sofar.

[/INDENT]

I just burned manually, without a menu, using dvdauthor and mkisofs.


Not sure how to report this, or whether it is really a bug.
Alan

---

### Post by gbasped on 2008-05-08
MANDVD does not convert multiple videos. It will only do on, the others donot get encoded. Could some one tell me why?:confused:

---

