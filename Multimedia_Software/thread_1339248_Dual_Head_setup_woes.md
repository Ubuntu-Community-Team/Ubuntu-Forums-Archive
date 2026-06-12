---
title: "Dual Head setup woes"
date: 2009-11-27
forum: Multimedia Software
---

### Post by chuck.mindrup on 2009-11-27
I am a noob.  Now that we have settled that, here is what I have,

Dell PC, integrated Intel 82Q35 Express Integrated Graphics Controller as well as nVidia GeForce 8400 GS card.  I cannot get anything but the nVidia card running, and I want both screens.  doesn't have to be a shared desktop.

Using Ubuntu 9.10, when I use the nVidia display settings gui, and hit detect displays, it doesn't detect anything else.

Also, some results in the console, but I do not know what to do with them (i have truncated them to contain only graphics info):
[SIZE=2]
[/SIZE][SIZE=2]myname@hostname[/SIZE][SIZE=2]:~$ lspci -x | grep VGA
04:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

[/SIZE][SIZE=2]myname@hostname[/SIZE][SIZE=2]:~$ lspci
00:02.0 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
04:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
[/SIZE]
If anyone can point me to the next step, it would fill me with glee...

---

