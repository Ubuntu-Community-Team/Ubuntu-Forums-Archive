---
title: "No Network Manager Applet/Wireless broken?"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by Cthulhu_Dreams on 2010-05-08
I'm not sure if I have two seperate issues or one inter-related issue.  The Network Manager applet wasn't appearing in the tray, found out it wasn't installed.  Installed, still didn't appear.  Tried installing WiCd, WiCd did appear but couldn't find any networks.  I had installed restricted drivers previous, decided it was worth another look.  Found that Broadcom STA Wireless Driver wasn't installed.  Tried to install, it said it couldn't and said I should review the var/log/jockey which is....excessively long.  Ideas?

---

### Post by Cthulhu_Dreams on 2010-05-09
Bump

---

### Post by cchhrriiss121212 on 2010-05-10
Studio does not have network manager installed by default as wireless connections interfere with audio latencies/stability. If it did not appear in the tray then you either did not install the right packages, or you have not set it to start when you boot (go to system>startup applications).
To see whether you have it installed run this in a terminal:
```
nm-applet
```

After that you can search for configuring your broadcom card.

---

