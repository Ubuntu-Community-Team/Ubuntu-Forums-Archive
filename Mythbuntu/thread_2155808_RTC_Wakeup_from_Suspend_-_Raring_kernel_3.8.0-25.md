---
title: "RTC Wakeup from Suspend - Raring kernel 3.8.0-25"
date: 2013-06-19
forum: Mythbuntu
---

### Post by billstei on 2013-06-19
I use an RTC wakeup event to allow my MythTV based DVR to sleep/suspend during periods of inactivity, and recently had this function break in Ubuntu 12.04 running Raring backported kernels 3.8.0-x (via package linux-image-generic-lts-raring).  I tracked down the problem to 3.8.0-25 and removed it (which also removes package linux-image-generic-lts-raring) and reverted back to 3.8.0-23-generic and it is working OK now, so I thought I would pass this along to see if anyone else has experienced this problem, and to provide a workaround.  The Changelog for 3.8.0-25 mentions the following and is a possible source of the regression:

* drivers/rtc/rtc-cmos.c: don't disable hpet emulation on suspend
    - LP: #1178361

---

### Post by bazsi77 on 2013-06-27
I experienced the same issue with 3.8.0-25, reverting to 3.8.0-23 which fixed the issue for me.

Is there a launchpad bug about this?

---

