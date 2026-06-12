---
title: "Playing DVD with VLC enhances CPU usage"
date: 2006-12-04
forum: Multimedia &amp; Video
---

### Post by xoai on 2006-12-04
Each time I play DVD with VLC, my laptop fan speed increases. I checked System monitor and found out XGL uses 60-70% CPU >_< and after 15 minutes, my laptop becomes very hot. Anyone know how to solve this problem >_<

---

### Post by Azakus on 2006-12-04
Try this. Run vlc with this code
```
DISPLAY=:0 vlc
```
This will force vlc to not use XGL.

---

### Post by xoai on 2006-12-04
Thank you. Now it plays well but there are some problems. The titlebar does not appear and my keyboard does not work (it only works on VLC). I have to logout and re-login to back normal. Can we force an application run under a specific GUI?

---

### Post by Azakus on 2006-12-05
I don't know actually. Xgl causes that high CPU usage with video and games because it makes all the nice effects happen through software calls instead of hardware calls, making the CPU do all the effort instead of the graphics card. There is no real way around this that I know of. Are you using Xgl for something like Beryl? If so, Edgy has AIGLX built-in, which does the same thing as Xgl, but with better code and MUCH lower CPU usage. It does require the newer graphics drivers, so here's the best guide I know of for the installs.
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
{Do the Method 1 version for Nvidia drivers, it is MUCH easier that way}

---

### Post by ubunter1 on 2006-12-05
ive the same problem,but on mine all players do this.heres my thread asking for a solution. [http://www.ubuntuforums.org/showthread.php?t=311738](http://www.ubuntuforums.org/showthread.php?t=311738)

---

### Post by xoai on 2006-12-05
Great! thanks Azakus. Now it works excellently. I am using AIGLX and it is really better than XGL. I dont know what diffirences between XGL and AIGLX?

---

### Post by Azakus on 2006-12-06
AIGLX works with the X window system that does all the GUI and everything on Linux without replacing it, it just does all the calls in the background. Xgl uses a completely different system, separate from X, to do all the work, which adds to the complexity of the system, but a freedom from hardware specific problems (causing high CPU usage). For more info, try the Wikipedia articles for both:
[http://en.wikipedia.org/wiki/AIGLX](http://en.wikipedia.org/wiki/AIGLX)
[http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl)

---

