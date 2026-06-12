---
title: "Problems with an old ATI Rage 3D"
date: 2006-05-05
forum: Multimedia &amp; Video
---

### Post by martinrandau on 2006-05-05
I have an old ATI Rage 3D on a Pentium III computer with Ubuntu Breezy Badger which I can't get to work. I have tried with the fglrx module but clearly this card is too old to be supported by that module. The dri modules doesn't work either.

When I run glxgears I get an error saying that libGL.so was not found, etc.

Does anybody know how to fix this?

---

### Post by Jason_25 on 2006-05-05
Do you expect to have 3d acceleration?  The card is way too old for that.  I have one and it won't even run 24-bit color and 1280x1024 resolution.

---

### Post by martinrandau on 2006-05-06
Well, I do know that when there was windoze on it I could play simple games like The Sims 1. I would know how to solve this on gentoo ([http://www.gentoo.org/doc/en/dri-howto.xml](http://www.gentoo.org/doc/en/dri-howto.xml)) but I'm not that familiar with ubuntu.

---

### Post by Brinstar on 2006-05-10
I'm also having exactly the same problem on the latest Mepis (6.0 beta 2). The links to the opengl drivers are completely messed up. If anyone knows how to fix them by symlinking (if that's even possible) please post the solution here. BTW I think this issue only affects ATI but I could be wrong...

---

### Post by Brinstar on 2006-05-11
Okay, well, it looks like 3D acceleration for ATI is not supported in the current release:

[http://ftp.x.org/pub/X11R7.0/doc/html/ati7.html#29](http://ftp.x.org/pub/X11R7.0/doc/html/ati7.html#29)

I could be wrong, however.

---

