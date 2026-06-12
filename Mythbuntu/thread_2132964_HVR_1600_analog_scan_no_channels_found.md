---
title: "HVR 1600 analog scan no channels found"
date: 2013-04-06
forum: Mythbuntu
---

### Post by qsilver7 on 2013-04-06
[HTML]HVR 1600 digital scans and plays well, but the analog scan comes up empty. Is there anything in 12.04 I need to enable to activate the analog side of this card?[/HTML]

Scanning was always coming up empty, so I used the import channels from schedules direct. It took about 20+ installs to get rid of all the bugs from trying to install drivers/firmware/config changes and what ever else I used from posts going back for years.I still can't scan the analog, but import works. Believe it or not, the remote was the easiest part. It only cost me about 6 or 7 re-installs. Once I found apt-get update and upgrade so update manager would quit hanging, I was away.
For some reason, dual monitor now freezes on boot. I found virtual memory allocated at 192 worked until the latest re-install yesterday. Now when I go into activate the new nvidia driver, there is now 2 choices instead of one like before, and the both hang. Even tried 256MB. No go. Hopefully I get it figured out before the kernel upgrade servers ban me. 

If anyone needs a simple remote solution, I'll give the short version of what I did.

---

