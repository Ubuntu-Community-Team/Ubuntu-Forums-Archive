---
title: "ATI video acceleration fails when run w/o GDM"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by KaeseEs on 2006-09-05
I've been experiencing an odd problem with my ATI card on my Thinkpad T60.  It's a MobilityFire X1400, with the 8.27.10 fglrx drivers.  Basically, when I open up my WM (fluxbox) from an X-Session via GDM, everything works perfectly.  However, when I run it without gdm, via xinit or startx, some 3D programs run but are horrendously slow and choppy (ppracer) while others spit out errors and quit (America's Army).  I ran ```
sudo dpkg-reconfigure xserver-xorg
``` and manually selected fglrx as my driver, but the problem persisted.  I edited /etc/X11/xorg.conf and made sure VideoOverlay was enabled and OpenGLOverlay was disabled, but still no improvement.  I'm currently at a loss as to what's going on.  fglrxinfo returns the same output with my WM running in either mode.  My current workaround is (big surprise) just running Flux through a desktop manager, but it's rather a PIA as I login from the terminal, and it's rather annoying to have to login two extra times just to run X programs.  Any help would be greatly appreciated!

---

### Post by KaeseEs on 2006-09-06
Bump - any help greatly appreciated!

---

### Post by Ziox on 2006-09-06
check your home folder, does it have this file:

.xinitrc 

or this:

.xserverrc

---

### Post by KaeseEs on 2006-09-06
My home folder has a .xinitrc file which calls Fluxbox.  There is no .xserverrc  .

---

### Post by Ziox on 2006-09-06
so, does acceleration work if you remove(or rename) that file?

---

