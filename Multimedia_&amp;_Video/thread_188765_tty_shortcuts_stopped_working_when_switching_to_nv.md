---
title: "tty shortcuts stopped working when switching to nvidia driver"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by jojopaderes on 2006-06-04
I just upgraded successfully to Ubuntu 6.06 (from a 5.10 setup) and upgraded as well my nvidia driver. The desktop graphics and 3d effects are working properly (even the XGL and Compiz effects), however, I can't switch to tty console view when using the shorcuts keys (CTRL + ALT + F*). If I switch back to 'nv' driver by hand-editing the xorg.conf file, the tty shortcut keys work well again.

Also, if I'm using the 'nvidia' driver I don't see anymore the usplash shutdown display. Again, switching to 'nv' driver it goes back to normal.

This is really weird. What seems to be causing this problem? ](*,)

---

### Post by simplyw00x on 2006-06-04
AFAIK this problem was caused for me by the xmodmap command that we are told to use to stop the shift-bksp bug. Possibly leave that out and see if it works then?

---

### Post by tseliot on 2006-06-04
See point 13 of the Problems Section of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by jojopaderes on 2006-06-04
[QUOTE=tseliot]See point 13 of the Problems Section of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")[/QUOTE]

Thanks tseliot! Your useful guide fixed the problem! :p 

I just hope this bug will get fixed in future patch releases for Dapper. I still prefer having the nice usplash display for aesthetic purposes. Btw, I'm using NVIDIA Corporation NV43 [GeForce Go 6600] video hardware on my Toshiba Satellite M40 laptop.

---

### Post by jdk_ on 2006-06-04
Hi, I also had this problem with both breezy and dapper, I disabled the graphical boot in breezy and it worked but I didn't remember how it is done, so this thread was very useful. Thank you tseliot.
-- I'll keep a log of my changes this time

By the way, my card is an NVIDIA GeForce Go 6400 on a vaio fs315m.

---

