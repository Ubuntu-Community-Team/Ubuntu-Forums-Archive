---
title: "Noobuntu: Atheros AR5007EG Adapter"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by hey4ndr3w on 2008-12-06
Lifetime Windows user here, just nuked Windows Vista Home from orbit with 8.10. Install went very smoothly, except the built-in wireless adapter/receiver (Atheros AR5007EG adapter)does not seem to work. At all.

A search of the forums takes me to a wiki, which advises the use of a module called ath5k, to be found on linux-backports-modules-intrepid.

However, there does not seem to be a link to this module or backport for me to download. What am I missing?

Thanks, and sorry.

---

### Post by 2hot6ft2 on 2008-12-06
You would use that in a terminal like this
sudo apt-get install linux-backports-modules-intrepid
To open a terminal go to Applications>Accessories>Terminal then copy and paste it into it hit enter, then it will ask for your password type it in and hit enter.

What kernel are you using now?
Applications>System Tools>Sysinfo then top left click on System and it will show you.

---

