---
title: "wine restarts X"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by ragnar_123 on 2007-01-16
Hi there!

Every time I start wine (Warcraft Frozen Throne or World of Warcraft) the X restarts and I am back at the login screen. If I open a simple application (such as microsoft notepad) the X wont restart, just show me black screen, which I can switch from (using alt+tab).

After searching the forum I found out that I where not the only one with these issues. I use the nVidia beta driver, and when using the driver control panel i can choose OpenGL/GLX Information. when I choose that the X restarts once again. :-k 

Anyone willing to help me figure this one out?

My graphics card is a nVidia 7800 gtx. I use edgy eft, and I have wine version 0.9.19. My kernel version is: 2.6.17-10-386. 
Further info is available by request.

UPDATE:

running glxgears does also break X

---

### Post by miceagol on 2007-01-16
I have the same problem, but my card is 8800GTS. Since my card is so new, I thought that might be it, but I don't know. For me it's not only Wine. Among the things I've tested, also the screen savers and nvclock_gdk restarts x. :confused:

---

### Post by ragnar_123 on 2007-01-16
I figured it out myself.
I just reinstalled the graphics driver :D

---

### Post by miceagol on 2007-01-16
> **ragnar_123 said:**
> I figured it out myself.
I just reinstalled the graphics driver :D

Weird that it helps, but I'll try it myself when I get home. :) Probably wise to follow [this thread]("http://www.ubuntuforums.org/showthread.php?t=336412").

---

### Post by ragnar_123 on 2007-01-16
well, I just followed [http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

---

### Post by miceagol on 2007-01-16
> **ragnar_123 said:**
> well, I just followed [http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

I don't know if I'm right, but the method doesn't seem to give you the latest of the latest drivers. I'm totally dependent on that for 8800 GTS support.

---

### Post by miceagol on 2007-01-16
Thanks, you saved me a lot of extra work. Just uninstalled the drivers, and installed them again. Now all previous problemmakers are working fine. :D I used method 2 of [this page]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy") btw.

---

