---
title: "DVD movie playback garbled; menues and trailers play fine..."
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by diablo75 on 2007-10-23
I just picked up a copy of Meet the Robinsons and while the menu, trailers, and otherwise rest of the DVD play fine, the main feature looks like a garbled mess; like it's not being decoded correctly.  (See screen shot)

What's wrong?

---

### Post by Stemp on 2007-10-23
is package libdvdcss2 installed ?

---

### Post by diablo75 on 2007-10-23
Yes, it is installed.

---

### Post by diablo75 on 2007-10-23
Bump....

By the way, I just tried this same DVD out on my laptop and it played back perfectly fine.  Anyone know which packages I should try to reinstall to clear this up?

---

### Post by haraldmilz on 2008-03-31
Try reinstalling libdvdcss2 and libdvdread3. If that won't work, I would reinstall the gstreamer or xine plugins. KR, Harald

---

### Post by TheOtherShoe on 2008-05-03
I have the same problem. I have tried two different copies of "Meet the Robinsons" from Netflix with identical results.

I'm worried that the problem is due to some new security feature that isn't handled by libdvdcss.

diablo75: Is the laptop that you were able to play the movie on also running Linux?

Edit: I forgot to mention that I have been able to play all other DVDs that I have tried without problems; and I have not fiddled with anything recently.

---

### Post by face00 on 2008-07-08
I ran into the same problem and got it to play.   It appears to be something with the viewing angle.     I played it with xine, and when I got to the garbled menus, I launched the xine Navigation menu (N in the lower right).   From there click on angle, and vuala, a sub menu appears ungarbled.   Click on main menu and you have the movie ungrabled and ready to play.

---

### Post by Stemp on 2008-07-08
Did you tried with VLC ?

---

### Post by face00 on 2008-07-09
> **Stemp said:**
> Did you tried with VLC ?


Ah yes, VLC had no problem.    So, mythtvfrontend does not work, dvd::rip does not work for backups, xine doesn't work without fiddling, and VLC works flawlessly.

Thanks.

---

