---
title: "Intel G35 board, 8.10 upgrade broke XWindows"
date: 2008-10-30
forum: Multimedia Software
---

### Post by fitten on 2008-10-30
I used the 'update' method for upgrading from 8.04 to 8.10 and it broke XWindows.  It was working fine in 8.04 but now I get (when I try to start it manually):

  
(EE) Failed to load module 'vesa'.
(EE) Failed to load module 'mouse'.
(EE) No drivers available.

Fatal server error:
no screens found
giving up

---

### Post by Newport on 2008-11-01
I have a similar problem. I get the command line prompt but Gnome does not start on my Toshiba laptop. 
When I use the startx command, I get EE "Intel" module does not exist.
Similarly for "mouse" and "Synaptics".
It said third party repositories had been disabled during the upgrade.

Can someone explain how to get these modules using the command line and how to enable third party repositories?

---

