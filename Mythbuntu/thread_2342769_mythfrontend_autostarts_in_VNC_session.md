---
title: "mythfrontend autostarts in VNC session"
date: 2016-11-09
forum: Mythbuntu
---

### Post by jamoody on 2016-11-09
I start vncserver via init.d which works fine, but mythfrontend also starts in the VNC session which results in 2 each mythfrontend/mythfrontend.re tasks.  After reboot I always have to login to the VNC session and close the mythfrontend there before using the local (TV) mythfrontend else the lirc remote signals are processed by both mythfrontend images causing conflict.  Any suggestions on where I should look to disable autostarting mythfrontend in the VNC session?  Of course I still want to autostart mythfrontend on the local (TV, non-VNC) session.  

Thanks in advance for any hints.

---

### Post by jamoody on 2016-11-10
Looks like it is ~/.config/autostart/mythtv.desktop
     [https://help.ubuntu.com/community/MythTV/FAQs](https://help.ubuntu.com/community/MythTV/FAQs)

---

### Post by jamoody on 2016-11-17
I worked around this by hacking /usr/share/mythtv/mythfrontend.sh to kick out if not running on the local display ("$DISPLAY" != ":0.0").  Seems to work.

---

