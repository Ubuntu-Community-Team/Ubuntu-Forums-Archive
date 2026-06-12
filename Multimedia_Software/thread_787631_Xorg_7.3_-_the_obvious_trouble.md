---
title: "Xorg 7.3 - the obvious trouble"
date: 2008-05-09
forum: Multimedia Software
---

### Post by Lamb Chop on 2008-05-09
Hello people,

Since ubuntu 8.04 (and debian testing too) the Xserver packages have been upgraded to xorg 7.3 which has started a whole load of trouble here. After installing my nvidia drivers X will only allow a maximum resolution of 640x480 which is hardly useful, to make it worse. At that resolution I cannot  edit my resolution through the nvidia-settings app because it simply just doesnt fit on the screen. Is there a way to get back to Xorg 7.2 because that worked just perfect. With 7.2 i just had to run "dpkg-reconfigure xserver-xorg" select my drivers and max resolution and everything went fine. Now i can only select my keyboard through this tool. Also setting resolution and sync rates manually in my /etc/X11/xorg.conf file messes things up and KDE (gnome as well) somehow can only set my monitor to 50Hz something which is not supported by my screen, I need at least 60Hz. After having set the resolution manually in xorg.conf and then setting the refresh rate with nvidia-settings my screen gets less blurry and everything seems normal. Until I start Enemy Territory which parses the KDE settings (50Hz) and starts using these settings, resulting in a black screen.

I hope anyone can help me, I'd rather go back to Xorg 7.2. Ubuntu 8.04 turned out to be a great disappointment for me because of this. What was wrong with the good old debian xconfig script? Why autodetection?

---

### Post by joegiampaoli on 2008-05-09
Yes, I totally agree, with good old xconf.org I could tweak everything to my own likes, if I wanted to blow my monitor right on my face I could do it straight from there. Now the file is so damn small and "untweakable" I don't even know why it's there to begin with.

---

