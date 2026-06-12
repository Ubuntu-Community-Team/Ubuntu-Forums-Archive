---
title: "networking icon disappeared after running update"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by kalimojo on 2012-01-28
hi i ran the suggested update to the latest version of ubuntu and the network icon in the top right corner disappeared. networking is working fine but id like the icon back.
any ideas ?

ps
eth0 is working fine but my wifi ra0 isnt.

---

### Post by kalimojo on 2012-01-28
[this worked]("http://ubuntuforums.org/showthread.php?t=1311790")

[http://ubuntuforums.org/showthread.php?t=1311790](http://ubuntuforums.org/showthread.php?t=1311790)
When you have problems with NM icon pl check these
1) Go to system-preferences-startup applications and see that Network Manager is ticked
2) Right click on panel and click add to panel then add "Notification Area" from the list.
3) I have observed NM icon missing when
a)nm-system-settings.conf says *managed=false*
To solve
     Code:
     gksudo gedit /etc/NetworkManager/nm-system-settings.conf 
and set
     Code:
     managed=true

---

