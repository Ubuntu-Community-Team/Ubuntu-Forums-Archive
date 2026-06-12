---
title: "can't get 3d rendering, trying to get fglrx driver but will not work, help!!!"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by Nibblet606 on 2006-09-05
hi! im trying to use the 3ddesktop thing, and i figured out that i don't have 3d rendering.... i try to run it and it says:

Attempting to start 3ddesktop server.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

So i followed another thread, and it said i needed to download a driver using the sudo apt-get install fglrx-driver  command, but when i type that in, this is what i get:

Reading package lists... Done
Building dependency tree... Done
Package fglrx-driver is a virtual package provided by:
  xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-3
You should explicitly select one to install.
E: Package fglrx-driver has no installation candidate


so i cannot download the driver.... i switched the thing from ATI to fglrx in my xorg.config file, but it wouldn't load up the GUI after that so i ahd to change it back to ATI. 

help anyone?? i'd really apreciate it, this is bugging my ](*,) ](*,) :-?

---

### Post by nin82 on 2006-09-05
M8 I did everything u did a couple of months ago..... LOL just to find out that my 9600se ATI was close to impossible to get running ANY 3d acceleration.... and i say impossible because it could be possible if the damn company would support us a little bit more.... my suggestion to you is get an Nvidia card... thats what i did and right now am not even using its full power since Im still having problems with the drivers so if u want something hustle free get the Nvidia 7800 or the 7600gt but not the 7600gs thats what i got and it hasnt been nice on me JET! good luck. sorry I couldnt help u any more.

---

### Post by Toxicity999 on 2006-09-05
Well assuming there were no complications, and no human error on your part it means the card just isn't supported. What card do you have? If you want some swanky effects Compiz-Vanilla works okay on lower end radeon cards assuming you gte out of the box direct rendering with the Open Source drivers. Probably just threw way too much at you... sorry about that.

---

