---
title: "Screen Resolution Issue"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by The Pinny Parlour on 2006-11-14
Hi,

Just turned on my PC and the resolution is jumped from 1680x1050 to 1680x1200.  I go to change it back in System>Preferences>Screen Resolution, but it won't change to any resolution I try. Very strange.  Can anyone help.

Thanks

---

### Post by LsrLine on 2006-11-14
try sudo dpkg-reconfigure xserver-xorg from the terminal.  From there when the screen arrives select the right resolution by hitting the space bar on it, finish the wizard, and then reboot. :)

---

### Post by The Pinny Parlour on 2006-11-14
Thanks for the help.  I just get the following after all that and nothing changes:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061114173010


   	

Not sure what to do now, I really don't want to have to reinstall again.  Configuring X is one of the biggest pain-in-the-*** things about linux.

---

### Post by The Pinny Parlour on 2006-11-14
Resolved:  Turned machine off for 30 mins, then turned it on and it's all good.  Weird.  

Thanks for the effort LsrLine.  ;)

---

