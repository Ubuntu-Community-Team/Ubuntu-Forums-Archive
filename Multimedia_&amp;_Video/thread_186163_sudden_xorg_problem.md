---
title: "sudden xorg problem"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by timothyparker@gmail.com on 2006-06-01
This morning I rebooted and now my screen resolution is limited to 640x480. I have:

A S3/Savage video card which has worked expected until now
*Not* altered the xorg.conf file for several months

The only "irregular" setting I have in xorg.conf is:
Option          "UseBios" "Off"
This was added to allow for > 1024 resolution.

BTW, my system is fully up to date as of yesterday's additions to the Dapper repositories.

---

### Post by El Menda on 2006-06-01
Try: sudo dpkg-reconfigure xserver-xorg
but make a copy of your old file first:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

---

### Post by timothyparker@gmail.com on 2006-06-01
[QUOTE=El Menda]Try: sudo dpkg-reconfigure xserver-xorg
but make a copy of your old file first:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old[/QUOTE]

That took care of it.
Many thanks.

---

