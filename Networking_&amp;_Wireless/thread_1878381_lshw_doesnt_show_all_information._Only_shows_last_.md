---
title: "lshw doesnt show all information. Only shows last line,"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by jonnohudski on 2011-11-09
Hi, i am trying to fix my wireless card in Ubuntu 11.10 (am RTL 8192E) and one of the commands suggested to show my hardware (lshw) shows all of the information on 1 line and then hangs (needs ctrl-c) to escape.
 
The last (and only) line that it shows PCI (sysfs).
 
Please somebody help!

---

### Post by papibe on 2011-11-09
Best results are with sudo:
```
sudo lshw
```
and yes, it is a slow command, it display a couple (or one) line, and after sometime the rest of the information.

Hope it helps,
Regards.

---

### Post by jonnohudski on 2011-11-09
Thanks Papibe, i feel a right plonker, I thought it had hanged. Having patience was all that was required.
 
I was already sudo su'd so didn;t need the sudo.
 
Thanks.

---

