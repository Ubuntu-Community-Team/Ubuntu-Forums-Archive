---
title: "x11vnc startup parameters in Mythbuntu"
date: 2015-02-01
forum: Mythbuntu
---

### Post by Alan_Baker on 2015-02-01
I installed Mythbuntu 14.04.1-Desktop-AMD64, which included x11vnc.  :p

x11vnc starts automatically and runs just fine.  Where is the file containing its startup parameters?  I don't find it in /etc/init/ or etc/init.d or /etc/rc.local.  :confused:

advTHANKSance

---

### Post by steeldriver on 2015-02-02
At least in 12.04, it's started from /usr/share/mythbuntu/session.sh (which itself is referenced from the /usr/share/xsessions/mythbuntu.desktop file, so maybe start there if you don't find it)

---

### Post by Alan_Baker on 2015-02-03
Thanks, steeldriver--just what I needed!

---

