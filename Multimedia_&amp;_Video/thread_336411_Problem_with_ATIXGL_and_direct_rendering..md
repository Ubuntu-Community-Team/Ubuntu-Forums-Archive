---
title: "Problem with ATI/XGL and direct rendering."
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by novaraz on 2007-01-11
Hi everyone!

I have Ubuntu 6.10 running on my Core2, ATI X1400 ThinkPad.  I have Beryl/XGL up and running, but for some reason its using software rendering.  If I log into a standard GNOME session, "glxinfo" returns "Direct rendering: Yes."  But when I switch to an XGL session, direct rendering goes off.  The Xorg.0.log has no clues (has "(II) fglrx(0): Direct rendering enabled" in log...)  I have Composite and AIGLX turned off in xorg.conf.  "fglrxinfo" returns OpenGL vendor: ATI in both situations.  Any ideas where to look next?

---

### Post by eZoulou on 2007-03-20
Yeap, it is the same for me here... Beryl kinds of work though. But it crashes so often! 
as soon as you ask too much, like zoom or rotating the cube without windows being minimalised. 
Does beryl work the same for you?

---

### Post by rushinge on 2007-04-12
I'm having the same problem on my Presario V5000 laptop.  It has a built in ATI Radeon xpress 200M.  Direct rendering works in a gnome session but not in an XGL session.  Beryl works quite well for me, no crashes or slowdowns.  However my DVD's are simply unplayable in my Beryl/XGL session using MPLayer.  Anybody know how to enable direct rendering in XGL?

---

