---
title: "network manager gone plz help .............."
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by jimmy.iceman on 2008-12-21
i tried everythin and after doing lots and lots of restarting and reinstalling & observations i found out that everytime i setup my pppoe connection via "pppoeconf" and restart the network manager in the top right is gone.

any1 got any ideas ???????????
thanx in advance

---

### Post by alan34 on 2008-12-21
Right click on top panel - then click add to panel and scroll down to "Notification Area" and add. Should come back.

---

### Post by superprash2003 on 2008-12-21
why do you always keep configuring pppoeconf .. you do it once its enough

---

### Post by jimmy.iceman on 2008-12-21
i have tried to enable notification well it didnt work nothing happened.

and 
i do not config my pppoe connection everytime . the very 1st time i configed it it worked like a dream untill i restarted mah system the network manager was gone.

help me out guys this is the only thing that is making me come back to windows

---

### Post by alan34 on 2008-12-21
Hi I do not use a ASDL modem so not much help to there but network manager is also under System - Preferences - Network Configuration.

Also if you go to Applications - Accessories - Terminal and type

sudo pppoeconf

I believe you can set it up that way but please type 

man pppoeconf 

first good luck

In a terminal you can also start the network manager by typing

nm-connection-editor

---

### Post by superprash2003 on 2008-12-23
post ifconfig output after you restart

---

