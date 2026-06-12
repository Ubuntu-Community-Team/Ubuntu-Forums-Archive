---
title: "Feisty nVidia setup for Asus A7N-266 mobo"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by rotorcraig on 2007-04-22
I'm trying to get Feisty set up on an Asus A7N-266 based PC.

The "restricted drivers" feature does appear to be trying to install the Legacy nVidia accelerated drivers...

> craig@asus:~$ dpkg-query -l | grep nvidia
ii  nvidia-glx                                 1.0.9631+2.6.20.5-15.20                NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
craig@asus:~$ 


... but when the system restarts it hangs before the login prompt with Num Lock, Caps Lock, Shift Lock lights all flashing :( 

The only way to recover is to reset the X11 config to "nv" drivers.

Has anyone else run into this and managed to fix it?

Craig

---

