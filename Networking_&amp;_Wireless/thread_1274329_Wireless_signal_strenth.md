---
title: "Wireless signal strenth"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by tad1073 on 2009-09-24
I have 9.04 32 bit jaunty with server kernel and 9.10 karmic 64 bit on my machine. My signal strength in 9.04 does not get above 15%. In 9.10 my signal strength ranges between 40% and 60%. What can I do to improve signal strength in 9.04, besides moving closer because that is not an option.

---

### Post by jml on 2009-09-24
When a new netbook I bought from system 76 had wireless issues, it was related to the driver used by Ubuntu.  In fact, System 76 said that they had to utilize drivers from the backports repository to get the wireless working at all.  Once a new driver was developed, the problem improved.  Since you are noticing improved performance with 9.10, its likely that that version is using an updated driver for your wireless card.  One option may be to enable the backports repository, and download the updated driver and see if it improves performance in 9.04.  Warning, though, doing this is not really encouraged by Cannonical, and the possibility of breakage is real.  So try at your own risk.  Good luck.

Joe

---

### Post by W2IBC on 2009-09-24
> **tad1073 said:**
> I have 9.04 32 bit jaunty with server kernel and 9.10 karmic 64 bit on my machine. My signal strength in 9.04 does not get above 15%. In 9.10 my signal strength ranges between 40% and 60%. What can I do to improve signal strength in 9.04, besides moving closer because that is not an option.

well another question to ask yourself is speed?

do you notice any speed changes between the 2. dose a 10MB file download faster with 9.10 then 9.04?

i noticed on mine i could be connected to the same wifi on 9.04 or 9.10 and the signal might be say 10dbm stronger with 9.10 but speed still the same.

---

### Post by tad1073 on 2009-09-24
the speed is affected also, in 9.04 my max speeds are 350/kbs and in 9.10 my max speeds are 650/kbs

I am just doing an upgrade from 9.04 32 to 9.10 32, 9.10 64 seem to process things a littler slower

---

