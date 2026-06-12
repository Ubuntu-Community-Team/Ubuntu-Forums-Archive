---
title: "WICD Client"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by pramod1561 on 2010-06-11
HI All,

I am trying to create a cron job to continuously monitor the network connection and whenever it is down, I want the wicd-client to show up. I have written a bash scrpt to do this. I use **wicd-client -n** to show it up. 
When I run the script freely(without the cron job) the wicd-client shows up but with the following warning :
[B]/usr/share/wicd/wicd/wicd-gui.py:1166: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
self.wTree = gtk.glade.XML(gladefile)
[/B]
However with the cron job on, it doesn't show up at all. Any hunch as to what the problem could be?

Any suggestions is appreciated.

Regards
Pramod

---

