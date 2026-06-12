---
title: "Missing misc notification area icons"
date: 2011-03-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Mblackwell on 2011-03-24
I noticed that nm-applet and policykit are both missing icons. They exist but the icons don't show. If I add the indicator-applet(s) to my panel I see the icons there that should appear in the notification area.

Everything was fine until yesterday.

---

### Post by Harry33 on 2011-03-25
> **Mblackwell said:**
> I noticed that nm-applet and policykit are both missing icons. They exist but the icons don't show. If I add the indicator-applet(s) to my panel I see the icons there that should appear in the notification area.

Everything was fine until yesterday.

This is due to the bug in the package libappindicator1_0.3.0-0ubuntu1.
See more info in this thread:
[http://ubuntuforums.org/showthread.php?t=1713317](http://ubuntuforums.org/showthread.php?t=1713317)

---

