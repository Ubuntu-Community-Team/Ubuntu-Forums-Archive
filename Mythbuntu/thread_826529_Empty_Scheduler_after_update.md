---
title: "Empty Scheduler after update"
date: 2008-06-12
forum: Mythbuntu
---

### Post by straxus on 2008-06-12
I ran an update last night which updated a large number of packages.  Today, I rebooted the box.  Now, I notice that nothing recorded after the reboot, and my scheduled recordings are empty. What's going on, and what can I do about it?

---

### Post by straxus on 2008-06-12
My database was corrupted. The following fixed it:

Close all Myth frontends and backends.
 mysqlcheck -r -umythtv -p<password> mythconverg
Reboot.

---

