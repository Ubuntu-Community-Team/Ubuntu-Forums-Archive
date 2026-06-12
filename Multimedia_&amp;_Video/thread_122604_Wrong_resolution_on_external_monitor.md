---
title: "Wrong resolution on external monitor"
date: 2006-01-28
forum: Multimedia &amp; Video
---

### Post by jrohde on 2006-01-28
Hi,

I have successfully installed Ubuntu Breezy 64 bit on my Acer Ferrari 4000. 

I have added these lines:

Option "CRT2Position" "clone"
Option "MonitorLayout" "LVDS,CRT"

to the "Device" section in xorg.conf. The lines were taken from a thread in this forum. My External monitor (LCD) now shows a correct image, except that it is far too big (I can only see a portion of the screen, but I can scroll around with the mouse). 

How do I specify the width, height etc. for the external monitor?

TIA,

Jakob

---

### Post by lcg on 2006-01-28
[QUOTE=jrohde]I have added these lines:

Option "CRT2Position" "clone"
Option "MonitorLayout" "LVDS,CRT"

to the "Device" section in xorg.conf. The lines were taken from a thread in this forum. My External monitor (LCD) now shows a correct image, except that it is far too big (I can only see a portion of the screen, but I can scroll around with the mouse). 

How do I specify the width, height etc. for the external monitor?[/QUOTE]
You want the external Monitor to show the same picture as the internal panel (the "clone" above), so it actually has to be the same resolution. If you want to change the resolution, you have to change it for both displays (or rather, you change the resolution and this change will affect both devices).
Of course, all this only applies for clone mode.

HTH,
Lars

---

### Post by jrohde on 2006-01-28
[QUOTE=lcg]
Of course, all this only applies for clone mode.
[/QUOTE]

Hi.

I need two different resolutions. The laptop monitor is 1800x1050 and the external LCD monitor is 1280x1024. But I only need one monitor at any one time. The laptop's lid is closed when I use the external monitor.

Is this scenario supported? 

Jakob

---

