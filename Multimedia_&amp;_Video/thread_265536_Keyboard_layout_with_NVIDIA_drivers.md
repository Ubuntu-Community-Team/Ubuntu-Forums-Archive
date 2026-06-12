---
title: "Keyboard layout with NVIDIA drivers"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by derbaschti on 2006-09-26
Hi,

I installed the NVidia drivers following this guide: [http://http://www.ubuntuforums.org/showthread.php?t=255929]("http://http://www.ubuntuforums.org/showthread.php?t=255929")

Everything went O.K. But from time to time (I guess with every update of the drivers) my keyboard layout falls back to default settings. The keyboard settings are not affected by what I set in System --> Preferences --> Keyboard.

Can anybody tell me how I can prevent this?

---

### Post by Gotterdammerung on 2006-09-26
nvidia-xconfig seems to be changing your /etx/X11/xorg.conf file. you don't have to execute it everytime you update nvidia drivers.

---

