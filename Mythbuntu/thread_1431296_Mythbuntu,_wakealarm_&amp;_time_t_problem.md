---
title: "Mythbuntu, wakealarm &amp; time_t problem"
date: 2010-03-16
forum: Mythbuntu
---

### Post by tobiz on 2010-03-16
I've been trying to get my Mythbuntu 8.10 system to use wakealarm as per [http://www.mythtv.org/wiki/ACPI_Wakeup]("http://www.mythtv.org/wiki/ACPI_Wakeup").
I've run the manual (non-local time variant) wakeup test on my m/b and it works correctly. However, when I try this in mythtv as specified the system does shut down but I've found that /proc/driver/rtc has alrm_date set to  "****-03-**" and therefore won't wakeup (I use wakeonlan to restart it). I've also tried wakeup time in mythbackendsetup as: yyyy-MM-ddThh:mm:ss but this is no better than time_t.  Any ideas what the problem is?

---

