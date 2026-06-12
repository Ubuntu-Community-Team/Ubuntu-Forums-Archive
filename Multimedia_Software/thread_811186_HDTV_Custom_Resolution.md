---
title: "HDTV Custom Resolution"
date: 2008-05-28
forum: Multimedia Software
---

### Post by losl2 on 2008-05-28
I have a 720P Sony Television hooked up to my recently formatted Ubuntu 8.04 Box with a Radeon 9600SE. I have had no problem setting the card to 1280x720 resolution, however, the screen then cuts off a bit of the top and bottom as well as the sides. 

When the box had Windows XP, the Catalyst control center had an option to slightly decrease the resolution, which made it display properly. I used Envy-NG to install the ATi 8.3 drivers for Ubuntu, but they did not have this feature.

I have attempted to set this from Xorg, and from monitors.xml (By changing the resolution to be slightly less than what was already in the file), and neither worked for me. I don't really know where to go from here, so any input would be helpful

Thank You

---

### Post by pather on 2008-06-19
[http://ubuntuforums.org/showthread.php?p=5221878](http://ubuntuforums.org/showthread.php?p=5221878)

you may want to try this post, for me works just partionaly, but others seems to have succes...

---

### Post by markbuntu on 2008-06-19
You can try setting the overscan option on or off with aticonfig. Many tvs use overscan to fill the screen. But definitely check out those threads above.

The list of options for aticonfig can be got by typing aticonfig --help. There is a lot there for setting up a tv.

The list of available modelines for your tv you can find in your /var/log/Xorg.0.log file.

---

