---
title: "Crashing xsupplicant and v 1.2.5"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by srijith on 2006-06-02
After upgrading to 6.06 (from 5.10), my xsupplicant was segfaulting (EAP-TTLS, PAP setup). 

If this is happening to you, try version 1.2.5 of xsupplicant from 
[http://sourceforge.net/project/showfiles.php?group_id=60236&package_id=56416&release_id=420900](http://sourceforge.net/project/showfiles.php?group_id=60236&package_id=56416&release_id=420900)

When I tried to compile the source, I got errors about undeclared "IW_ENCODE_ALG_WEP" and "iwee". Check out this diff to remove the "IW_ENCODE_ALG_WEP" error (lines 586 and 593): 
[http://open1x.cvs.sourceforge.net/open1x/xsupplicant/src/cardif/linux/cardif_linux_wext.c?r1=1.78&r2=1.79](http://open1x.cvs.sourceforge.net/open1x/xsupplicant/src/cardif/linux/cardif_linux_wext.c?r1=1.78&r2=1.79)
 
To remove the "iwee" error I just commented that couple of lines of codes out :) I know, I know, bad hack, but hey, it works!

BTW, when I tried v1.2.4, I was able to compile the source without all these problems, but my EAP-TTLS (PAP) setup was not authentication properly. V 1.2.5 does the trick.

Hope that helps someone.

---

