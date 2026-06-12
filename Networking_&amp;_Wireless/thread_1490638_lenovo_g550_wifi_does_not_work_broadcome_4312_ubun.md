---
title: "lenovo g550 wifi does not work broadcome 4312 ubuntu 10.04"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by gabak on 2010-05-22
I recently bought a Lenovo G550 and have not yet to get the Broadcom 4312 card to work using Ubuntu 10.04 (Karmic). The lspci command says I have the BCM4312 802.11 b/g card. So, beware buyers. This card is not trivial to get running in LInux. If I figure it out I'll post back. 
Please if somebody know who to make it work , i need some help.
i did install the sta broadcom and bw43 and i tried some things but i could nt make ir work.
The light it off ( the one that say that wifi is on or off)

---

### Post by leclerc65 on 2010-05-22
Did you try NDISGTK to install its Windows driver ?

---

### Post by gabak on 2010-05-22
no  i did nt try.
how can i use that? i have no idea.
do u have a step by step?

---

### Post by ajgreeny on 2010-05-22
If you can connect by a wired connection for now use that to install ndisgtk from the repos.  Then go to **System -Administration -Windows Wireless Drivers** and use that to install the *driver*.INF file from the windows driver CD.

Hopefully that will do the trick.

---

