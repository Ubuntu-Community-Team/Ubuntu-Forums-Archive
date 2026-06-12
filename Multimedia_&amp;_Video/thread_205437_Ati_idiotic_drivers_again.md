---
title: "Ati idiotic drivers again"
date: 2006-06-28
forum: Multimedia &amp; Video
---

### Post by master17r@yahoo.com on 2006-06-28
Sorry if some posts already had topics like this one, but i just can't handle installing ATI (and not MESA) drivers for my Radeon 9250...I've tried first the latest drivers but they seem to be broken for Radeon 8500 to 9500. I've tried installing older drivers but i can't get rid of the old fglrx without breaking my xorg. I've disabled fglrx but when i tried to install a possibly good driver (older) my package installer warns me of a conflict with an already installed fglrx. Any ideas anyone ???

---

### Post by Klemik on 2006-06-28
You need to replace new libs with the old ones. Search forum for that lib download and guide. Or just unpack old drivers and copy that libs over new ones.
GL.

---

### Post by master17r@yahoo.com on 2006-06-30
Got it working finally, it was just of matter of replacing libGL.so.1.2 with an older one. This might be the answer for all the users who have ATI Radeon 8500-9500.Thx.

---

