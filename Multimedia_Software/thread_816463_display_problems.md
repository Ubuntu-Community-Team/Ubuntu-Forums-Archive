---
title: "display problems"
date: 2008-06-02
forum: Multimedia Software
---

### Post by fatfriar101 on 2008-06-02
my display on the desktop is all fuzzy. i cant use my mouse or keyboard to navigate, but the ubuntu loading screen is fine.  once it gets to the desktop, the screen gets really wavy and fuzzy.  here's a couple pictures to show you what i mean.
[IMG]http://Camera-0019[1].JPG[/IMG]
[IMG]http://Camera-0021[1].JPG[/IMG]

---

### Post by overdrank on 2008-06-02
> **fatfriar101 said:**
> my display on the desktop is all fuzzy. i cant use my mouse or keyboard to navigate, but the ubuntu loading screen is fine.  once it gets to the desktop, the screen gets really wavy and fuzzy.  here's a couple pictures to show you what i mean.
[IMG]http://Camera-0019[1].JPG[/IMG]
[IMG]http://Camera-0021[1].JPG[/IMG]

Hi and you can try using the ctrl, lat, F1 keys and reach the command line. Login and then use this command to reconfigure your xorg. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then use the command sudo reboot when the configure is complete.

---

