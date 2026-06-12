---
title: "Maverick shows jumbled graphics on startup"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by smoosh on 2010-09-09
Hey, when I first boot 10.10 it looks jumbled. I can easily fix it by CTRL+ALT+F1 then CTRL+ALT+F7, but I'd like to get it so it I don't have to work around anything. I am using Compiz with the open source ATI Radeon driver, on a Sony Vaio FW139E. See attached screenshot.

Just for clarification - the screenshot doesn't look that bad, but please note that firefox and terminator were both quit, but the image of the window stays there. The AWN dock is where it is most evident, but all windows leave trails if you move them around. I tried doing "compiz --replace" at startup, but it does nothing.

Thanks!

Smoosh

---

### Post by Rubi1200 on 2010-09-09
Beta=bugs

I hope this not an attempt to install as a stable environment.

Maybe try passing the xforcevesa parameter at boot.

---

### Post by cariboo on 2010-09-09
When asking questions about a testing version, please ask them in the correct sub-forum. Moved to Maverick Testing & Discussion

---

### Post by VMC on 2010-09-09
> **smoosh said:**
> Hey, when I first boot 10.10 it looks jumbled. I can easily fix it by CTRL+ALT+F1 then CTRL+ALT+F7, but I'd like to get it so it I don't have to work around anything. I am using Compiz with the open source ATI Radeon driver, on a Sony Vaio FW139E. See attached screenshot.

Just for clarification - the screenshot doesn't look that bad, but please note that firefox and terminator were both quit, but the image of the window stays there. The AWN dock is where it is most evident, but all windows leave trails if you move them around. I tried doing "compiz --replace" at startup, but it does nothing.

Thanks!

Smoosh
Have you looked at any log files. Try in home dir ".xsession-errors", then check "/var/log" files.

---

### Post by smoosh on 2010-09-28
Sorry for the late reply...

I believe this has to do with the Compiz plugin "wallpaper", as it only happens when that is enable. I looked through the logs, but I don't really know what to look for. I will file a bug report.

---

### Post by smoosh on 2010-09-28
Also, when I disable "wallpaper", the "desktop cube deformation" plugin stops working. weird.

---

