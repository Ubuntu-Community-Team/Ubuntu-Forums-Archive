---
title: "Desktop screen resolution"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by cpd747 on 2006-06-03
I tried the Ubuntu GNOME 6.06 Live CD, and it doesn't detect my monitors refresh rate correctly. The settings are stuck on 60hz refresh rate. I can't get it to change.

Another thing is that I can't change the color depth from 24bit to 16bit through the control panel. Its just too simple! :)

Anywho, is there any other way to change these settings to the ones I want without editing the Xorg Conf file?

---

### Post by cpd747 on 2006-06-05
Bump. (sorry, but it looks like this thread has gone down the tube a bit)

---

### Post by Pejalo on 2006-06-05
What's wrong with editing xorg.conf?
Search the forums; there are many threads where people were stuck with certain resolutions, and editing xorg.conf as described by those who replyed worked perfectly. I bet the same methods will apply to your refresh rate and color depth.

---

### Post by cpd747 on 2006-06-06
Sorry, its just I was afraid that if I goofed up a bit, the system would be unbootable. But, Im gonna be brave and try it when I get around to installing Ubuntu. Thanks.

---

### Post by ghee22 on 2006-06-13
[QUOTE=cpd747]Sorry, its just I was afraid that if I goofed up a bit, the system would be unbootable. But, Im gonna be brave and try it when I get around to installing Ubuntu. Thanks.[/QUOTE]


Instead of installing ubuntu and then trying it, you can edit your xorg config
open terminal
sudo gedit /etc/X11/xorg.conf
edit to include your res.

CTRL-ALT-BKSP to restart X

good luck!

---

