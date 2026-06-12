---
title: "Switching from secondary to primary backend"
date: 2010-11-17
forum: Mythbuntu
---

### Post by zaurus on 2010-11-17
Hello

I recently installed Mythbuntu 10.10 and defined the machine as a secondary backend. I realized then that the primary backend was not compatible with the secondary one because of previous release. I switched from secondary to primary backend on Mythbuntu 10.10 machine using control center. I cannot login to the database when running mythtv backend setup.
What should I do in that situation?

Thanks

---

### Post by LowSky on 2010-11-17
I think you need to update the address on the frontend to the new backend location.

---

### Post by zaurus on 2010-11-17
> **LowSky said:**
> I think you need to update the address on the frontend to the new backend location.

It does not help. It seems to me that it is something with database password to do. When using as a secondary backend I used a password of  the  primary backend on another machine. I probably need to reset it in someway.

---

### Post by tgm4883 on 2010-11-17
Likely you don't have mysql installed on that machine (it's not installed usually on secondary backends).

---

