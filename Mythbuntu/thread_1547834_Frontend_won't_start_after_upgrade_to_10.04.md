---
title: "Frontend won't start after upgrade to 10.04"
date: 2010-08-07
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-08-07
I have just upgraded my Mythbuntu 9.10 system to Mythbuntu 10.04. I did this via the upgrade option in the update manager, not a clean install.

The process seemed to go reasonably smoothly, but now I can't start MythTV frontend. If I try, I get screen with the background of my MythTV theme (but nothing else: just a blank background) that lasts for about 30 sec and then exits back to the Ubuntu desktop. The behaviour is the same whether I try to start it manually or whether it tries to start automatically on startup.

Here is what I believe to be the relevant extract from the mythfrontend log file:

```

2010-08-07 15:16:39.836 Starting update of BBC-Current-XML
2010-08-07 15:16:39.837 BBC-Current-XML recently updated, skipping.
2010-08-07 15:16:39.837 Starting update of BBC-3day-XML
2010-08-07 15:16:39.838 BBC-3day-XML recently updated, skipping.
2010-08-07 15:16:39.838 Cannot load language en_us for module mythweather
2010-08-07 15:16:39.841 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-08-07 15:16:39.944 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-08-07 15:16:39.946 Found mainmenu.xml for theme 'MythCenter-wide'
2010-08-07 15:16:39.969 MythContext: Connecting to backend server: 172.16.100.20:6543 (try 1 of 1)
2010-08-07 15:16:39.971 Using protocol version 56
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread

```

Any ideas what's going on and how I might fix it?

Thanks
NM

---

### Post by NautiusMaximus on 2010-08-07
Ah, after a bit more googling for similar problems, I've figured it out.

It turns out that I needed to install auto builds for MythTV. I have now done that, installed a whole bunch of updates, and now everything just works.

Hurrah!

---

