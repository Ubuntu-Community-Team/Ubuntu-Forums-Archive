---
title: "Myth TV Frontend ethernet disconnect"
date: 2009-06-23
forum: Mythbuntu
---

### Post by emacdonald on 2009-06-23
I have a problem with myth TV on 9.04. A frontend only unit has been installed with 9.04 and Mythtv, everthing installs well, but when I come to viewing the recordings on the frontend unit from the Backend machine, Eth0 Drops in and out at regular intervals. Outwith this time, i.e. browsing internet etc everything is ok.
When I install using 7.10 or 8.04 everything is fine, eth0 does not drop out, though the issue also occurs in 8.10. BTW, the backend unit is running on 7.10 (without problems since October 2007)

Is there a problem between 7.10 running Mythtv backend and more up to date versions?

---

### Post by klc5555 on 2009-06-23
> **emacdonald said:**
> I have a problem with myth TV on 9.04. A frontend only unit has been installed with 9.04 and Mythtv, everthing installs well, but when I come to viewing the recordings on the frontend unit from the Backend machine, Eth0 Drops in and out at regular intervals. Outwith this time, i.e. browsing internet etc everything is ok.
When I install using 7.10 or 8.04 everything is fine, eth0 does not drop out, though the issue also occurs in 8.10. BTW, the backend unit is running on 7.10 (without problems since October 2007)

Is there a problem between 7.10 running Mythtv backend and more up to date versions?

Just a guess, but the current graphical interface Network Manager was introduced in 8.10, and has been the source of discontent on some other fronts. 

You may wish to try having your network connection initialize the normal old-fashioned way, at boot, and see if that helps. If so, the thread "mythbuntu 9.04 - NetworkManager too slow" [http://ohioloco.ubuntuforums.org/showthread.php?t=1159824](http://ohioloco.ubuntuforums.org/showthread.php?t=1159824)  will have the information you need.

---

