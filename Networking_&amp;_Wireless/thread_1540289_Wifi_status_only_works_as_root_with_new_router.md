---
title: "Wifi status only works as root with new router"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by ChrisMP1 on 2010-07-27
I recently bought a new wireless router (Cisco E1000) to use in my house. The E1000 supports mixed-mode 802.11n/g/b, which is what I have enabled. It is the first 802.11n router I've had. My netbook (an HP/Compaq Mini 110) only supports b/g.

When connected to this new router, I can only see my status as root. NetworkManager shows a little red exclamation point, and 'iwconfig' shows nothing. It's missing in the 'iwlist scanning' list. Even still, I'm connected and can do everything just fine.

However, everything shows up fine when I run 'sudo iwconfig' or 'sudo iwlist scanning'. These have always worked as a standard user before. Any ideas?

---

### Post by DEVIL DOG on 2010-07-27
Have you checked your user permissions in "Users and Groups"?

---

