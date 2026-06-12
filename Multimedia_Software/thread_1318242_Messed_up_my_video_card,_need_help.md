---
title: "Messed up my video card, need help"
date: 2009-11-07
forum: Multimedia Software
---

### Post by monkeymind90 on 2009-11-07
Last week I was attempting to get my computer to output to TV through the S-Video port. Problem is, it didn't work. I gave it up after putting everything back the way it was before (by running "lasudo dpkg-reconfigure -phigh xserver-xorg" to return my xorg.conf to its original state) but now I can't play any games. Is it possible that I altered the way my computer uses its video card? The menu for the video card is no longer the Nvidia specific one, but instead it is the generic ubuntu menu. I'm not sure how to fix this, my card is a GeForce 8400 GS, I'd appreciate any advice.
Ethan

---

### Post by monkeymind90 on 2009-11-12
Nevermind guys, I figured it out. I'll close the thread, but if you have the same problem, you can restore your driver by running "sudo nvidia-xconfig" then restarting. Good luck and thanks!

---

