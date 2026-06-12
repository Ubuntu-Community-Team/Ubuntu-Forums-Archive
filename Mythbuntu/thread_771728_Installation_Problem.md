---
title: "Installation Problem"
date: 2008-04-27
forum: Mythbuntu
---

### Post by the[V]oid on 2008-04-27
Hi! I'm just trying to install Mythbuntu 8.04 and having a problem: When selecting a DVB-DTV-Card (v3.x) as Capture-Device, it is not possible to change (or even set) the DVB Device Number: It's not possible to write anything into the appropriate field!

Please help!

---

### Post by superm1 on 2008-04-27
> **'the[V]oid said:**
> Hi! I'm just trying to install Mythbuntu 8.04 and having a problem: When selecting a DVB-DTV-Card (v3.x) as Capture-Device, it is not possible to change (or even set) the DVB Device Number: It's not possible to write anything into the appropriate field!

Please help!
Try to just finish mythtv-setup and ignore this currently.  After the system reboots, try to do mythtv-setup then and see if it works.

---

### Post by the[V]oid on 2008-04-28
Thanks that did it :D

---

### Post by superm1 on 2008-04-28
Although you have a workaround/solution, It would be interesting to debug the root cause of this problem.  You aren't the first one to encounter it, but I haven't the hardware to determine what is happening.

Theoretically, the live environment should perform identically to the resultant system.  A lot of stuff happens with bind mounting the target directory and such to try to make it happen.

---

