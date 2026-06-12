---
title: "Determining ATI Catalyst Driver version"
date: 2009-01-20
forum: Multimedia Software
---

### Post by Tom T on 2009-01-20
How can I found out what version of the Catalyst driver is installed on my machine?  In particular, how do I know if it is Catalyst 8.12?

In the release notes for Catalyst 8.11, I see a mention of:
"This particular driver updates the software version to 8.452"

In the release notes for Catalyst 8.12, it becomes:
"This particular driver updates the software version to 8.561"

My fglrx version is 8.543, and I can't find anything referencing 8.11 or 8.12 on my machine.  Basically, I just want to see that the latest and greatest Catalyst 8.12 really was installed when ubuntu prompted me to install a proprietary video driver.

---

### Post by Eddie Wilson on 2009-01-21
Ubuntu's restricted drivers manager will not install Catalyst 8.12. It installs 8.11. Catalyst 8.12 is installed by using a driver downloaded from the Amd/ATI website. If you installed using the restricted drivers manager then you should be able to go to Accessories and the Ati Catalyst program should be listed in the menu.

---

### Post by Tom T on 2009-01-22
Thanks for the info.  I did install using the restricted drivers manager and I do have Catalyst Control Center on the Accessories menu.  I just could not find anything in the Control Center that told me it was 8.11

Anyway, now I know -- and I will use the ATI download to install 8.12.
Thanks again.

---

### Post by Eddie Wilson on 2009-01-22
You're welcome.

---

