---
title: "Installing G'MIC for Gimp 2.10 (flatpack)"
date: 2018-06-12
forum: Multimedia Software
---

### Post by claus on 2018-06-12
Hi,

a few weeks ago, I installed the new Gimp 2.10 with flatpack. Now I want to install the 'G'MIC plug-in, but I don't know, where (I can't find the Gimp 2.10 plug-ins directory, only the old .gimp-2.8 directory).
Can anybody give me a clue on how to install G'MIC?

TIA,

Claus

---

### Post by Holger_Gehrke on 2018-06-12
I don't know anything about flatpack, but I do know that ppa:otto-kesselgulasch/gimp has both gimp 2.10 and G'MIC for Ubuntu 17.10 and 18.04 ...

Holger

---

### Post by deadflowr on 2018-06-12
Insane
the plugin directories I found for flatpak-gimp are in
/var/lib/flatpak/app/org.gimp.GIMP/current/active/files//lib/gimp/2.0/plug-ins/ 
and 
~/.var/app/org.gimp.GIMP/config/GIMP/2.10/plug-ins
and another at
~/.var/app/org.gimp.GIMP/data/gegl-0.4/plug-ins

Don't know whether that helps.
It's just what I found.

Hopefully you can make sense of that.

---

### Post by mc4man on 2018-06-12
See [https://www.gimp-forum.net/Thread-ubuntu-xenial-and-flatpak?pid=7741#pid7741](https://www.gimp-forum.net/Thread-ubuntu-xenial-and-flatpak?pid=7741#pid7741)
Scroll down a bit

---

