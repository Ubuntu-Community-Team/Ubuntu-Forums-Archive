---
title: "Screen goes black after 2/3 hours"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by fjrodriguez on 2008-03-17
Hello,

I`m using Ubuntu 7.04. I`ve disabled screensaver and power management. And I`ve added this in the xorg.conf file:

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection


But the screen goes black after a few hours and I need the screen always on to show several information. Any idea?

Thanks

---

