---
title: "wlassistant in jaunty"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by lither on 2009-05-20
A coffee shop I frequent will only work with wlassistant, which disappeared somewhere between hardy and jaunty. apt-get doesn't recognize wlassistant, and I have tried reinstalling it from a .deb file with no success. I would be grateful for any advice.

Rick Litherland.

---

### Post by chili555 on 2009-05-21
wlassistant was built to run under KDE 3. Jaunty uses KDE 4. The developers of wlassistant have not produced, as far as I can see, a new version since 2007, or 50 years ago in Ubuntu time.

Have you tried WICD? [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by lither on 2009-05-21
> **chili555 said:**
> wlassistant was built to run under KDE 3. Jaunty uses KDE 4. The developers of wlassistant have not produced, as far as I can see, a new version since 2007, or 50 years ago in Ubuntu time.

Have you tried WICD? [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

No, I  hadn't. Still haven't, yet. I installed WICD, and then noticed that this had removed KNetworkManager. Reinstalling KNetworkManager removed WICD. Apparently, they're like the Hatfields and the McCoys. Is there any reason that they can't coexist, so I can choose whichever one works with any given network? 

Rick L.

---

### Post by chili555 on 2009-05-22
> Is there any reason that they can't coexistYes, the bus can only be driven by one driver. There is really no mechanism that I am aware of for these two to share the duties. Many here, including me, would argue that WICD will always work better.

---

### Post by lither on 2009-05-22
> **chili555 said:**
> Yes, the bus can only be driven by one driver. 
I realize it would make no sense to have them both running at the same time; I just wanted them both available. However, this is now moot. Of the three networks I regularly use, WICD works with all of them, as opposed to two for KNetworkManager. Many thanks for the excellent advice.

Rick.

---

