---
title: "what do i do with this driver?  (somewhat of a newbie)"
date: 2005-12-24
forum: Multimedia &amp; Video
---

### Post by jmxhgyZN8wK7 on 2005-12-24
gnome runs really slow on my computer, but so do xfce4 and icewm (!!!)  i thought maybe using a different driver would help... so i found the driver for my video card (s3 twister) on opendrivers.com.  it came in a .tgz file, which i extracted into my home folder.  there were only two files:
[LIST=1]
[*]s3switch, identified as an "executable" in "properties."  i double-clicked it and nothing happened.
[*]savage_drv.o, identified as "object code."  i double-clicked it and got a "can't display location" message.
[/LIST]
so... what do i do?

---

### Post by xmastree on 2005-12-24
What's the chipset?
Have a look through this file:
**/usr/X11R6/lib/X11/cards**
to see if it's mentioned there. If it is, take a look at your xorg.conf and make sure you're using the correct driver.

From what you posted, I suspect it ought to be **savage**

---

### Post by afhp on 2005-12-24
[QUOTE=jmxhgyZN8wK7]
[LIST=1]
[*]s3switch, identified as an "executable" in "properties."  i double-clicked it and nothing happened.
[*]savage_drv.o, identified as "object code."  i double-clicked it and got a "can't display location" message.
[/LIST]
so... what do i do?[/QUOTE]

Last time I checked, the savage_drv.o driver in xorg was more recent than the one from ATI and worked better, so you might not get much from it. 

In any case, you'll need to put it in the proper location and restart X. 

Make a backup copy of /usr/X11R6/lib/modules/drivers/savage_drv.o (you'll need it if the other one bombs...) and copy the one from ATI to that directory ; no guarantee that it works though. 

s3switch is a command-line utility which (AFAIR) applies only if you're on a laptop.

---

### Post by jmxhgyZN8wK7 on 2005-12-24
wow!  i never expected to get responses that fast...

thanks!

i haven't tried either of your suggestions yet, but thanks!

---

