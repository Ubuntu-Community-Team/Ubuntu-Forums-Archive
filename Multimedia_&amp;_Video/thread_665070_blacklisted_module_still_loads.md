---
title: "blacklisted module still loads"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by drjimmy42 on 2008-01-11
I'm trying to blacklist fglrx by creating

/etc/modprobe.d/blacklist-fglrx

which contains

blacklist fglrx

I'm doing this because I want my laptop to suspend and ATI bites.  I know this will disable 3d but I need suspend more than I need 3d.  

Anyway, I do this and reboot and fglrx loads every time.  I've resorted to renaming the module file itself but this seems hacky and doesn't survive a kernel update. 

Is there anything else I can do to stop fgrlx from loading? I thought blacklist was supposed to do that.

---

### Post by lonniehenry on 2008-01-11
Don't create a new file that way.  Instead try in terminal sudo gedit /etc/modprobe.d/blacklist    Then add  blacklist fglrx and save.  reboot and you should be good.

---

