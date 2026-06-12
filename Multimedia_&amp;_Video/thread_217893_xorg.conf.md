---
title: "xorg.conf"
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by BrokeBody on 2006-07-17
I was messing around with /etc/x11/xorg.conf and in the line about monitor name there was "Generic Monitor". In that line I entered something else and now, X can't start up. I logged in without X and tried with sudo gedit /etc/x11/sotg.conf but it can't be displayed.

How can I get the things like before?:-?

---

### Post by lizzard on 2006-07-17
Try: sudo nano /etc/X11/xorg.conf
gedit won't work without a X environment.

---

### Post by BrokeBody on 2006-07-17
Thanks.

---

