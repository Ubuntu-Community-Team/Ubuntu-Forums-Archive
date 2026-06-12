---
title: "Resolution, Xorg.conf and Nvidia [Gutsy]"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by El Zoido on 2007-10-24
Hello!

Don't know if this has been posted allready , but a quick search did turn up nothing.
I've got a question regarding the xorg.conf. I'm still somewhat new to Linux, but I thought that the xorg.conf(amongst other things) sets the availlabe screenmodes for the x-server.
So, after installing Gutsy and enabling the restricted Nvidia-drivers, I got some wierd screenmodes in the settings menu.
I tried to remove them by outcommenting them in the xorg.conf file, but they still show up.
Is the Nvidia driver somehow using another settings file?

However, when some games kept using 60Hz refresh-rate in the 800x600 Fullscreen mode, I tried to solve this (maybe not the most elegant way) by removing the mode in the xorg.conf and it worked...

---

