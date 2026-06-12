---
title: "Live TV starts and kicks back to main menu"
date: 2008-04-06
forum: Mythbuntu
---

### Post by agent5150 on 2008-04-06
Ok, mythbuntu working with just about all mythtv items except Live TV.
WHen I select LIve tv, I see a black screen and 2 secs later Main Menu is back.

What could be the reason.  PVR-350 is the card, shows up in mythtv setup and inputs have been defined.

Is there a log I can review?

---

### Post by volkswagner on 2008-04-06
Check backend and frontend logs.

/var/log/mythtv/mythbackend.log, and /var/log/mythtv/mythfrontend.log

You can also while in the frontend verify the tuner is available.
Information>System Information>System status>tuner status

Sound like you may have to adjust the playback settings.

---

### Post by agent5150 on 2008-04-07
Fixed.  mythbackend.log showed that mysql.txt was not readable.  I recreated the file and Live TV is working perfect.

Thanks.

---

