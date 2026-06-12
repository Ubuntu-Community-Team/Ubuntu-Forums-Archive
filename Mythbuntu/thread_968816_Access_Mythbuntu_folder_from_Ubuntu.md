---
title: "Access Mythbuntu folder from Ubuntu"
date: 2008-11-03
forum: Mythbuntu
---

### Post by laffinet on 2008-11-03
Hi !

I'm planning to build a Mythbuntu HTPC (combined front/backend) which will eventually hold all my music etc.

What is the best way to access files and folders on the HTPC from my laptop ?

Laptop and HTPC will have a wireless connection to my router/DSL modem.

Thanks for any help.

---

### Post by volkswagner on 2008-11-03
NFS share works great.  I don't think you will have much joy with a "double" wireless setup.  It may be OK for music.  If you put a frontend on the laptop, you could select stream all content from backend.  This will reduce the required bandwidth.  You could also try other streaming clients like VLC or XBMC.

---

### Post by mrand on 2008-11-03
Samba works right out of the box when enabled.

For music, wireless should be fine.  For video, there are too many variables to predict.  I have my backend wired and then the desktop is wireless.  It plays standard definition videos over 802.11g via Samba to WinXP just fine.  

Have fun,

[INDENT]Marc[/INDENT]

---

### Post by laffinet on 2008-11-03
Thanks guys.

I'm not planning to stream any content via wireless.

I just want to be able to connect from my laptop to the frontend/backend (combined) to copy data.

---

