---
title: "routing issue"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by ryanfx on 2010-09-13
Hello,

I am running into an issue where I seem to lose routes on one individual wireless network I need to connect to for school.  When using Windows this never happens and also never happens on any other network (when using Ubuntu).  Are there some logs I can look at for hints?

I wind up needing to disconnect for about 5 seconds, then reconnect to the wireless network.  Sometimes this lasts for another 2 hours before another reconnect, sometimes it only lasts for 2 minutes, it seems quite random.

Is there a way to statically set routes after acquiring them?

---

### Post by BkkBonanza on 2010-09-13
You can use the **route** command to view and alter the kernel routing tables.

---

### Post by Iowan on 2010-09-13
> **BkkBonaza said:**
> You can use the **route** command to view and alter the kernel routing tables.**man route** should provide more details about the command. :)

---

### Post by ryanfx on 2010-09-13
> **BkkBonaza said:**
> You can use the **route** command to view and alter the kernel routing tables.

I understand the route command, that's why I can tell I am losing routes.  I looked through the man pages and did not know how to proceed.

---

### Post by utilitytrack on 2010-09-13
> **ryanfx said:**
> Are there some logs I can look at for hints?

```
/var/log/debug
/var/log/kern.log
/var/log/messages
/var/log/daemon.log
```

---

