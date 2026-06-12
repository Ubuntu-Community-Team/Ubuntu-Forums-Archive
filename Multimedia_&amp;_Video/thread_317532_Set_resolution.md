---
title: "Set resolution"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by rickmans on 2006-12-12
I just bought a new monitor (widescreen) and I cannot select the preferred resolution (1440*900). I tried o reconfigure xserver, however I can select the resolution while reconfiguring it, but I cannot select the resolution in gnome. Is there any other way to set the resolution?

---

### Post by Yopo on 2006-12-13
Did you change horizontal sync and vertical refresh?
$ sudo nano /etc/X11/xorg.conf
HorizSync       27-96  -> replace both with your monitors specs
VertRefresh     50-160 -> for this one also
I guess you know both specifications because you bought a new monitor, otherwise search for your monitor on:
[http://www.monitorworld.com](http://www.monitorworld.com)

---

