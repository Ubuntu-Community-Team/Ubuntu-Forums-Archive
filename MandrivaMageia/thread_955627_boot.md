---
title: "boot"
date: 2008-10-22
forum: Mandriva/Mageia
---

### Post by n8ek on 2008-10-22
I just installed 2009 set up the graphics so they looked right loged out then went to log back in and all iget is a black screen then it returns to the login screen and thats as far as i can get, the graphics card is nvidia, whats happened?

Thanks in advance

---

### Post by AdamWill on 2008-10-23
What settings did you change, exactly? In what app? Thanks.

---

### Post by n8ek on 2008-10-23
I just re-installed 2009 set up the graphics including compiz in mcc and its happened again, not sure if its something to do with compiz or the wrong graphics driver ( i chose a random again)through mcc.

Thanks

---

### Post by AdamWill on 2008-10-24
Um. You...really shouldn't go choosing random graphics drivers. Mandriva automatically detects and uses the right driver for your card.

Hit ctrl-alt-f1 and you can log in to a console (log in as root). You can run drak3d and drakx11 in text mode. Run drakx11 and re-configure your card using the default (auto-detected) settings, then run drak3d and disable the 3D desktop. Then run 'service dm stop', wait five seconds, and run 'service dm start', and your desktop should come up. Then you can try enabling Compiz again, if you like, but don't go fiddling around with the graphics driver setting for no good reason. :)

---

### Post by Vulpus on 2008-10-27
If you are using KDE4 then I suggest you turn off Compiz.  KDE4 has more than enough fancy graphics of its own. and seems more stable than compiz.

---

