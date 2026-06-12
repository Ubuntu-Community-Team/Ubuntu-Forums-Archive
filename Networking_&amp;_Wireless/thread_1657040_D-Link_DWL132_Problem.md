---
title: "D-Link DWL132 Problem"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by The Eight-Bit Link on 2010-12-31
Jist today I got a new monitor. I plugged it into my computer, booted it, and found the wireless symbol was missing in the tray, preventing me from connecting to the network and the internet. ndiswrapper reports the wifi dongle is present and operating, it works on other machines, the light indicating an active software communication to the computer is on, what could have gone wrong?

---

### Post by PatchesTheCaveman on 2010-12-31
If the wireless icon is completely missing, it's likely it was accidentally removed.  Right-click on the panel, click Add to Panel, find the Notification Area applet in the list that appears, click on it, and hit add.

If that doesn't make the wireless icon appear, press ALT+F2 and type this in the Run dialog that appears:
```
nm-applet
```

---

### Post by The Eight-Bit Link on 2011-01-01
I tried those, but it didn't work. I had a recent update. although I don't think that would affect ndiswrapper. Is there a way to be sure ndiswrapper sees and recognizes it?

---

