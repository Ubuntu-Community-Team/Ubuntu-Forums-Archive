---
title: "stuck in 640x480"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by pecha17 on 2007-06-17
I have an Intel 82845G/GL graphics adapter. I have tried 915resolution. It didn't work. Sometimes it will boot with higher resolutions but most of the time it won't. Any suggestions?

---

### Post by Reugen on 2007-06-17
try "sudo dpkg-reconfigure xserver-xorg" in a terminal .   It will ask about res, drivers etc and fill out the xorg configuration file accordingly.

---

### Post by pecha17 on 2007-06-21
Thank you! Thank you! :D Now my pc is SO screamin'!!!

---

### Post by NeilBlanchard on 2007-06-21
Hello,

The solution that worked for me was slightly different:

> sudo dpkg-reconfigure -phigh xserver-xorg

...which lets you actually edit the list of resolutions available in the Preferences.  You use the Space Bar to select  the resolutions that you want to have available.

---

