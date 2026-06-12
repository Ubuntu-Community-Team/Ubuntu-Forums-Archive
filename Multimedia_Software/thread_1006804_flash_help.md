---
title: "flash help"
date: 2008-12-09
forum: Multimedia Software
---

### Post by mscout2004 on 2008-12-09
When I open a website that has flash items all i see is a circle with a play button in the middle. When I click on it, it hangs the flash app and wont load. I am using Ubuntu 8.04 with firefox 3. I have flash 9 and 10 plug-ins installed and have tryed the ubuntu-restricted-extras package, no help. When i disable the flash 9 plug-in all flash goes away eventhough the flash 10 plug-in is still active. I can enable/disable the flash 10 plug-in with no changes in the pages I load.  The websites I am having trouble with are campus.ctuoline.com  and  hulu.com..

How can I fix this to be able to have my flash chat session for college work properly in firefox????

---

### Post by spiderbatdad on 2008-12-09
did you try to install multiple versions of flashplayer? This can cause problems. You should remove previous versions prior to installing newer versions.

---

### Post by mikewhatever on 2008-12-09
> **mscout2004 said:**
> When I open a website that has flash items all i see is a circle with a play button in the middle. When I click on it, it hangs the flash app and wont load. I am using Ubuntu 8.04 with firefox 3. I have flash 9 and 10 plug-ins installed and have tryed the ubuntu-restricted-extras package, no help. When i disable the flash 9 plug-in all flash goes away eventhough the flash 10 plug-in is still active. I can enable/disable the flash 10 plug-in with no changes in the pages I load.  The websites I am having trouble with are campus.ctuoline.com  and  hulu.com..

How can I fix this to be able to have my flash chat session for college work properly in firefox????

I'd recommend un-installing all versions of flash installed so far and sticking with the flashplugin-nonfree package from the repositories. The current problem is, most probably, different versions of flash conflicting with each other.

---

### Post by mscout2004 on 2008-12-09
It came with 9 on here so I installed 10 but it does absolutely nothing. I dont think the flash 10 i installed is working. Other then that the firefox 3 is untouched. I tryed unistalling 9 and just using 10 and it doesnt even reconize the flash is there.

---

### Post by mscout2004 on 2008-12-09
I tried uninstalling both 9 and 10 and reinstalling  the nonfree flash plug-in and it still doesnt work.

---

### Post by cariboo on 2008-12-09
When you uninstalled flash, are you shure it was removed from /usr/lib/mozilla/plugins? Simply marking it for removal will not always remove it, If you mark it for complete removal it will remove the program. If worse comes to worse, download the tarball from adobe, extract it and copy libflashplayer.so to /usr/lib/mozilla/plugins. Restart firefox and you should be OK.

Jim

---

