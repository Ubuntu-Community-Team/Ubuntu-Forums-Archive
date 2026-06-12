---
title: "Only one app can play sound at once on 6.10 (Edgy Eft) x86"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by jlblank on 2007-01-09
I'm running Edgy Eft, 6.10, on a fairly bog-standard Compaq laptop. This morning, I tried to install some packages which purported to let me browse iTunes shares over the LAN using Rhythmbox. Ever since then, I've noticed that once one application has grabbed control of the sound card, no other application can play sound at all (aside from PC Speaker bleeps / beeps, of course ;) ).

Yes, ESD is running.

No, I didn't bork up the settings under System > Preferences > Sound.

Yes, this is annoying. ;) Pleeeease help.

---

### Post by jpeddicord on 2007-01-09
Try installing the package 'libsdl1.2-debian-all'. It should gather all of the necessary dependencies and hopefully fix the sound problem. It will ask you to remove another package however, just ignore that and install it anyway.

Jacob

---

### Post by jlblank on 2007-01-09
Although I do appreciate you taking the time out of your routine to offer a suggestion, unfortunately, libsdl1.2debian-all (you had an extra hyphen in there ;) ) did not work. Even after a reboot, whenever one app grabs the use of the audio system, no other app can write to it. I feel like I'm back in 1998 again ;)

---

### Post by NT4usB on 2007-01-09
maybe [this]("http://www.ubuntuforums.org/showthread.php?t=205449") will help.

---

