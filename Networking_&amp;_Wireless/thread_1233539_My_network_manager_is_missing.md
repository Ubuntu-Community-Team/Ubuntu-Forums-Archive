---
title: "My network manager is missing"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by elelemahmood on 2009-08-06
I just installed Ubuntu 9.04 two days ago, I'm new to the Linux family. Was using a lAN Connectiotion some two hours ago @ my office. When I got home and tried to connect to the internet via a 3G stick I discovered that my Network connection icon was missing.
Geek & Gurus what do I do to restore it? Thank you.

---

### Post by SoftwareExplorer on 2009-08-06
try going to Applications->Accessories->Terminal
paste this in: ```
sudo killall nm-applet&&nm-applet&
```If it works now close the terminal.
If it disappears when you close the terminal, do ```
Alt + F2
``` then ```
nm-applet
```

By the way, welcome to ubuntuforums.

---

### Post by Topher88 on 2009-08-06
Had the same problem, and the above didn't work for me.  The fix is actually pretty simple; right click the panel, click "add to panel," and then add "Notification Area."  It's the last place I would have looked, but it worked for me, lol.

---

### Post by Katalog on 2009-08-06
> **Topher88 said:**
> Had the same problem, and the above didn't work for me.  The fix is actually pretty simple; right click the panel, click "add to panel," and then add "Notification Area."  It's the last place I would have looked, but it worked for me, lol.

That was my first thought - that they had somehow inadvertently removed the notification area from the panel (or accidentally deleted the panel altogether).

---

### Post by Topher88 on 2009-08-06
Oh, and if adding Notification Manager doesn't work at first, then try the Alt + F2 and adding "nm-applet" fix mentioned above to start it up again in case it was somehow aborted.

---

### Post by aibaena on 2009-08-21
Thanks Topher88!!!. lol. It worked for me.

---

