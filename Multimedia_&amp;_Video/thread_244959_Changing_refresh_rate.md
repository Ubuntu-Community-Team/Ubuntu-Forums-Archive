---
title: "Changing refresh rate"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by b3mt1 on 2006-08-27
witch nvidia driver & how i have to install so i can change my refresh rate! (now its 60Hz on 1024x768 resolutio)

pls help

thnx all

---

### Post by justugh on 2006-08-27
what op do u have and   the newest one for xp can do it

---

### Post by tseliot on 2006-08-27
Read this guide (use ONLY Method 1):
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Kameli on 2006-08-28
You must edit your /etc/X11/xorg.conf .
You must know your monitor Horiz and Sync rates (write name on your monitor to google).
There are lines like HorizSync 30-90 and VertRefresh 50-100 in Section "Monitor". So edit values for your monitor. And the startx and you can change your refresh rate higher, but ubuntu doesn't allow you put your refresh rate too high what can be dangerous for your monitor and maybe doesn't work. :)

---

