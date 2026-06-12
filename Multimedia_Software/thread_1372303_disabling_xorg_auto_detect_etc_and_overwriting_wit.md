---
title: "disabling xorg auto detect etc and overwriting with xorg.conf"
date: 2010-01-04
forum: Multimedia Software
---

### Post by madsporkmurderer on 2010-01-04
I have an xorg.conf that contains all the settings for how I want my 4 monitor setup to work. It used to work fine, then I went to uni and only took 2 monitors with me; now I have reconnected the other monitors only one of them will work.

Xorg is obviously doing something itself as when the other 2 monitors weren't plugged in it intelligently didn't extend the desktop to them, I have a feeling that it is this cleverness that is going wrong causing my current problem. Is there a way to tell xorg to do exactly what xorg.conf says regardless of what it thinks is the best thing to do?

Thanks,
Mike

---

### Post by themtx on 2010-01-04
I've found that just placing the modified xorg.conf in /etc/X11 and restarting gdm does the trick - in a terminal, sudo /etc/init.d/gdm restart. I migrated my tweaked 8.x config file to 9.10 this way.

---

