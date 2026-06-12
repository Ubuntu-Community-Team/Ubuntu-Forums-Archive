---
title: "Direct Rendering on ATI Mobility Radeon 9000 (M9) with open source radeon driver"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by wk2001 on 2006-11-04
Hello,

maybe someone can help me with my problem, that direct rendering doesn't want to work on my graphics adapter with the (open source) radeon driver although it is definitely supported.

problem: direct rendering doesn't work... 
my system: edgy... (upgraded from dapper upgraded from breezy)
my graphics adapter: ati mobility radeon 9000 (M9) with 64mb ram
driver: i want to get open source radeon driver running

here my xorg.conf: [http://www.ubuntuusers.de/paste/4867/](http://www.ubuntuusers.de/paste/4867/)
here my Xorg.0.log: [http://www.ubuntuusers.de/paste/4868/](http://www.ubuntuusers.de/paste/4868/)
and the output of glxinfo: [http://www.ubuntuusers.de/paste/4869/](http://www.ubuntuusers.de/paste/4869/)

enabling "GLcore" in the xorg.conf caused X-restart on glxinfo or glxgears... that's why i disabled it.

ps: the fglrx driver was working with accelaration but i want to get running aigxl and i need the radeon driver for this...

i hope, someone could help me...

thank you very much!

---

### Post by warjowuch on 2006-11-04
Have you got this weird error that after 5 seconds glx-gears the thing suddenly stops being fluently?
I have a radeon 9200SE, having likewise problems with opensource radeon driver (xserver-xorg-video-ati)

---

### Post by wk2001 on 2006-11-07
no, i didn't noticed such phenomenon but as i said direct rendering actually does not work for me.
is direct rendering working with your graphics adapter?

---

### Post by warjowuch on 2006-11-16
Yeah, it is working, but I am back on fglrx now. Had some trouble with ppracer and glx, but that is resolved.
I also wanted to go back to the open-source ones, to prepare for 3D-desktop, but now it suddenly stopped working. Weird. So, fglrx for now, but I'd like to try, I think you have to mess around a bit with options in your xorg.conf in the section where you have defined your driver.

Oh, I just found this: [ https://help.ubuntu.com/community/RadeonDriver ](https://help.ubuntu.com/community/RadeonDriver)
Might beinteresting, I will try this myself tomorrow

---

### Post by misiu_mp on 2006-11-29
run LIBGL_DEBUG=verbose glxinfo to see if you have some errors there

See [http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting) for dealing with it. Your X.log shows your driver supports DRI so skip to "Userspace setup" section.


BTW, did you get the xv video overlay to work properly (in mplayer for instance) with the raeon driver?

---

### Post by wk2001 on 2006-11-30
i have solved the problem... :)

in one of my previous installations in which i used the fglrx driver there was a problem with one version of fglrx. the problem was that a wrong or buggy libGL.so was installed, which i manually replaced with an other version.
after removing frglrx the file was still there...
so i removed the file and reinstalled some packages with apt, which were related to this file (e.g. mesa-dri and some others, i think also beginning with mesa-*).
after that the radeon driver works perfectly... beryl is running with about 115-130 fps :)

---

