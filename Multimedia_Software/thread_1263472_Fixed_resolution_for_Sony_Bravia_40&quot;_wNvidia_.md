---
title: "Fixed resolution for Sony Bravia 40&quot; w/Nvidia 260GTX"
date: 2009-09-11
forum: Multimedia Software
---

### Post by halgorhythm on 2009-09-11
Hi all,
I just signed up and came here to report how I fixed my resolution on a Sony Bravia 40" TV. I am using the 260GTX Nvidia GPU. It is currently connected via DVI-to-HDMI cable to the TV. I've been waiting months to fix the resolution problem I stumbled across as soon as I installed 9.04.
The problem is, when logged in, the gnome panels and part of the screens are outside the viewport of the TV. I tried really hard fumbling with the drivers/xorg.conf to no avail.
After weeks of failure, I came across this thread ( [http://ubuntuforums.org/showthread.php?p=7864401](http://ubuntuforums.org/showthread.php?p=7864401) ) which suggests trying to see if there are any size-adjustable options on my TV settings.

To my surprise, thats what fixed it. On the Sony Bravia TV there is a submenu under picture properties called 'Screen'. From there, all I had to do was set the 'Display area' option to 'full pixel'. And voila! It worked.

Ubuntu had nothing to do with it after all. I came across another LCD tv (no-name brand that supports native 1080p), and the same problem had persisted. A similar option in his TV-settings worked. 

Hope this helps.

---

