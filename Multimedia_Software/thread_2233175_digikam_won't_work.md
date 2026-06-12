---
title: "digikam won't work"
date: 2014-07-06
forum: Multimedia Software
---

### Post by RyeMan on 2014-07-06
When I try to execute digiKam, I can see the hard drive working for a few seconds but then it stops and no digikam. I've uninstalled and reinstalled it to no avail.  DigiKam IS in the Lubuntu Software Center.  Would appreciate any ideas.

-Version-
Kernel        : Linux 3.13.0-30-generic (i686)
Compiled        : #55-Ubuntu SMP Fri Jul 4 21:43:42 UTC 2014
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) 
Distribution        : Ubuntu 14.04 LTS
Desktop Environment        : LXDE (Lubuntu)
-Computer-
Processor        : 2x Intel(R) Pentium(R) 4 CPU 3.00GHz
Memory        : 2575MB (1076MB used)
Operating System        : Ubuntu 14.04 LTS
-Display-
Resolution        : 1366x768 pixels

---

### Post by kc1di on 2014-07-07
Could you go to a terminal and try to launch from there: ```
digikam
``` 
then post any error messages you get here.

---

### Post by RyeMan on 2014-07-07
Thanks so much KC!  It works from the terminal but not from the menu for whatever reason. Thanks again!

---

### Post by monkeybrain20122 on 2014-07-07
So there is something wrong with your .desktop file.  Open it with a text editor and see what is in the EXEC= line. The .desktop file should be in /usr/share/applications and probably called digikam.desktop. You need to invoke the editor with sudo from the terminal in order to edit or copy from it (not sure which editor Lubuntu use, maybe leafpad of something..)

---

