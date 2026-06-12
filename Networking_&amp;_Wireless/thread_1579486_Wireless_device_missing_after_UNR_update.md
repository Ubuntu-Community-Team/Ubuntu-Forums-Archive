---
title: "Wireless device missing after UNR update"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by ebix on 2010-09-21
I am running UNR on an Asus T91MT and everything was working great until an update yesterday, my OS froze while updating and I had to do a hard reboot. Since, I have not been able to get wireless, and lshw does not even recognize the presence of a wireless device on the system. :(

Help!

---

### Post by Irritated on 2010-10-01
Exact same thing happened to me.  Try this: 

sudo apt-get install linux-backports-modules-wireless-lucid-generic

sudo reboot

---

