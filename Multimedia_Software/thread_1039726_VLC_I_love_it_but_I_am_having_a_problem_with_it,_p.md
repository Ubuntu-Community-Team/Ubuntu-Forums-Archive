---
title: "VLC: I love it but I am having a problem with it, please help."
date: 2009-01-14
forum: Multimedia Software
---

### Post by brjoon1021 on 2009-01-14
solved-

Ubuntu 32 bit 8.10 -

When I tried to change the VLC skin I broke the application. It has started with this error ever since: 

VLC could not open the file "/usr/share/vlc/skins2/text.bmp"

As a stab at fixing it, I completely uninstalled VLC and dependencies with synaptic, reinstalled and rebooted several times. The reinstallation always has the same problem. I even deleted the VLC folder in usr/share as root and I still get the same error. Sure enough, there is no /usr/share/vlc/skins2/text.bmp in the folder

Any ideas on how to fix this... I really like and miss VLC ?

B.

---

### Post by mc4man on 2009-01-14
Start vlc from the terminal with
vlc --reset

---

### Post by brjoon1021 on 2009-01-14
You're a small god.

thanks.

---

