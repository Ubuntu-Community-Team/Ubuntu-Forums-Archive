---
title: "ati rage"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by g5reen on 2006-06-12
hey guys , i have a compaq armada m700 has ati rage mobility p/m agp video . wtf ever that is? anyway i ws wondering if there is a open gl driver for that .. any feed back would be greatly appreacited...

---

### Post by az on 2006-06-12
[QUOTE=g5reen]hey guys , i have a compaq armada m700 has ati rage mobility p/m agp video . wtf ever that is? anyway i ws wondering if there is a open gl driver for that .. any feed back would be greatly appreacited...[/QUOTE]
How much video memory does it have?

If it has less than 32 megs of video ram, you will have to lower the amount of memory the driver consumes for 2D to get 3D to work.  For example, if I use an ATI rage with 8 megs of video ram, I have to exit X, and reconfigure the xserver to not use (allocate memory to) more than 800x600 at 15-bit color depth.

Boot into recovery mode and run

dpkg-reconfigure xserver-xorg

and select those setting in the monitor config.

run

init 2

and see if you have DRI by running

run
glxinfo
from a terminal.

---

### Post by patrick295767 on 2006-06-23
not working ... :-(
[http://ubuntuforums.org/showthread.php?p=1174847#post1174847](http://ubuntuforums.org/showthread.php?p=1174847#post1174847)
  
Since it 's not a bad video card : 
we coudl try to install  xorg-aiglx + compiz (packages)  [http://ubuntuforums.org/showthread.php?t=145068](http://ubuntuforums.org/showthread.php?t=145068)   , no ??
 what would you think ??
  
thank you

---

