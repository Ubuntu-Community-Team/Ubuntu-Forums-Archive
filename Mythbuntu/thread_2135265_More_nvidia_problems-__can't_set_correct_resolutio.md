---
title: "More nvidia problems-  can't set correct resolution"
date: 2013-04-13
forum: Mythbuntu
---

### Post by itlarson on 2013-04-13
I have a Toshiba flatscreen with a native 1366x768 resolution, which is what I have always run it at.  Since the recent driver upgrade, this resolution has disappeared from Nvidia-settings, and it is defaulting to 1080p.  Is there a way to fix this, and if not, how do I revert to the old driver?

---

### Post by The Toastcutter on 2013-04-15
My video modes went bad after the recent nvidia driver update.

I fixed it by *removing* this line from my /etc/X11/xorg.conf file:
[INDENT]Option "DynamicTwinView" "False"
[/INDENT]
 
I'd originally added that line to get the refresh rates working properly in xbmc.

See: [http://www.mythtv.org/pipermail/mythtv-users/2012-December/344670.html](http://www.mythtv.org/pipermail/mythtv-users/2012-December/344670.html)

---

