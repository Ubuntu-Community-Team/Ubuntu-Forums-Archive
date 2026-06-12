---
title: "GFX card error"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by hasek522 on 2008-02-21
I was messing around with which gfx card driver i was choosing from one of the ubuntu options menu and upon restart i guess i picked the wrong one because now i see a triple screen that is all blury with lines all over.  How can i reset the driver to the default driver it was using?   I am a complete linux newb so please bare with me.  Also i dont think i will be able to do it graphicaly as all the menus are so scrambled i cant tell which one is which.

---

### Post by renzokuken on 2008-02-21
hit Ctrl+Alt+F1 when the screens go blurry.

you should now be at a terminal screen. log in and run

```
sudo dpkg-reconfigure xserver-xorg
``` making sure to choose the correct resolutions and driver (most other settings can be left as is)

exit and reboot and see if it helped

---

