---
title: "[SOLVED] downgrade nvidia driver"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by KingWilliam on 2008-01-23
Hi, 

I use wine to play Day of Defeat and Counter-Strike. This went great untill I used the program "Envy" to install the latest nvidia drivers (167.07). It installed these drivers without any problem, but I cant play these games anymore. Does anyone know how i back to the standard nvidia-glx-new? When I try installing the new one, when i reboot i get crap resolution.

anyone?

---

### Post by KingWilliam on 2008-01-23
OK nevermind. Its fixed now. For anyone with the same problem:

I used envy version 9.10 to install the drivers. I found envy version 9.9 somewhere on the net. 
-So i used envy 9.10 first do uninstall all nvidia drivers (make sure you got all of them).
-I uninstalled envy 9.10
-installed envy 9.9
-used 9.9 to install the nvidia driver
-reboot
-now xorg.conf was completely messed up, so i went to /etc/X11 and replaced xorg.conf with an older version. (Yippie I had back-ups from the days before troubles started)
-another reboot
-All fixed

---

