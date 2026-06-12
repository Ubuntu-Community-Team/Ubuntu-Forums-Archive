---
title: "How to get montor running 1280 x 1024?"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by Bios Nova on 2007-04-30
Hey,  i'm totally new to Ubuntu and i installed it yesterday and i am loving it (one of my friends showed it me on his laptop so i gave it a go). all is running smoothly (as far as i know), but i have one question. How can i get the resolution to run at 1280 x 1024? at the moment it is running at 1280 x 768? (with the Nvidia graphics driver enabled in the restricted driver menu) Also, if i were to download a driver from the Nvidia website, how would i install it because i did this and Ubuntu says it cannot read the file (it is a .run file)

Thanks  (I'm running Ubuntu 7.04 ):)

---

### Post by alienexplorers on 2007-05-01
Try running:
> sudo dpkg-reconfigure -phigh xserver-xorg

---

