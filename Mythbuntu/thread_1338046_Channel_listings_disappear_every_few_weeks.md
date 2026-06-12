---
title: "Channel listings disappear every few weeks"
date: 2009-11-26
forum: Mythbuntu
---

### Post by HW_Hack on 2009-11-26
I've got mythbuntu working fine for 4 months - even did an update in the past 3 weeks which fixed some minor things. But all along I've had this issue where every 3 - 4 weeks the channel listings are gone. So I have to go out and run the backend tools / setup - rescan and all is well for a while. I'm using Schedules Direct.


Any ideas or hints on what to look at ??

Thanks !

---

### Post by azmyth on 2009-11-26
I ran into a similar issue. Mythfilldatabase wasn't ending properly so the backend wouldn't start another myfdb. I could tell by looking at the system status from the FE as the days of listings wasn't staying at 14 days. I ended up running a cron job to kill any hung myfdb every morning.

---

### Post by OffAxis on 2009-11-26
in the MCC there's a checkbox under 'Advanced' for 'Enable daily mysql fix/repair'.
You could try enabling that.

---

