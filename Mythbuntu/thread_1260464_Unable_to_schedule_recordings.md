---
title: "Unable to schedule recordings"
date: 2009-09-07
forum: Mythbuntu
---

### Post by gilesjuk on 2009-09-07
Hi,

I have Mythbuntu back and frontend installed on the same box.

I have tried scheduling using Mythweb and using the frontend, the changes appear to save but when reloading the page in Mythweb the settings have reset.

If I look at the Schedules page I see the schedules, if I look in upcoming recordings I see nothing.

The tuners work and I can record programs my pressing R on the keyboard while watching a programme.
[B]
Kernel details:[/B]

Linux mythtv 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64

**Package details:**

mythtv-backend           0.21.0+fixes19961-0ubunt
mythtv-frontend          0.21.0+fixes19961-0ubunt
mythweb                  0.21.0+fixes19556-0ubunt

**Mysql:**

mysql-server             5.1.30really5.0.75-0ubun

---

### Post by gilesjuk on 2009-09-07
Solved.

Cleared out the record table, set MasterBackIP to be the actual IP address of the machine (instead of 127.0.0.1).

---

