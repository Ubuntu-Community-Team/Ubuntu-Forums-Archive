---
title: "Unable to sync time clock"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by lotech on 2009-10-15
I am running Karmic on USB flash boot, I installed NTP for synchronizing the time clock, but nothing happened to the time clock it is still wrong, when I check back the setting I saw the time zone is empty, I changed it back to my time zone but the time clock still wrong, I reboot again and the time zone is cleared  again, but the time servers I selected stay on, I've this problem in previous versions as well, and it will be fixed after reboot, but this time not, what's going on !?

---

### Post by leorolla on 2009-11-26
I got the same problem.

It does not forget the Time Zone, but synchronisation does not work either.

After waiting for ages without synchronisation, I googled how to do it manually and here is the result:

```
$ sudo ntpdate swisstime.ethz.ch
26 Nov 10:11:05 ntpdate[2893]: no server suitable for synchronization found
$
```

Anyone else with same problem?
Should we file a bug?

Can someone tell us the solution?

---

