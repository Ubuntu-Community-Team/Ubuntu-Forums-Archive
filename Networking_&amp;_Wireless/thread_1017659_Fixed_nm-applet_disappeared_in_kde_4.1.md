---
title: "Fixed: nm-applet disappeared in kde 4.1"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by goneskiing on 2008-12-21
after updating, nm-applet disappeared in KDE (4.1.3).  there were other threads suggesting editing /etc/xdg/autostart/nm-applet.desktop - looking in Nautilus, this file is not visible (who knows?)  but if you ls you will see it - open it with sudo vim and edit line:
OnlyShowIn=GNOME;KDE;XFCE;

good to go after that.

---

