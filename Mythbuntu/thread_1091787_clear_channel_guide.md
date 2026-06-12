---
title: "clear channel guide"
date: 2009-03-09
forum: Mythbuntu
---

### Post by davidstoll on 2009-03-09
Does anyone know how to clear the channel guide?  I had mine originally to download from SchedulesDirect and to be updated by the "over the air" data from the providers (using HDHomeRun).  Recently, one of the channels is transmitting "DTV program" as the guide data, so it replaces the good data with the crap they are transmitting over the air.  I changed it to not override, but even after running mythbuild database, it remains.

I can confirm that it is sending crap because if I hook the antenna to my TV directly, it shows the same info.

Any way of forcing a clear (without affecting any weekly or future recordings) without deleting the input and re-scanning?

Thanks!

---

### Post by theophile on 2009-03-09
The "--refresh-all" option for mythfilldatabase will overwrite all old data with new data from the data source.

---

### Post by davidstoll on 2009-03-10
> **theophile said:**
> The "--refresh-all" option for mythfilldatabase will overwrite all old data with new data from the data source.

It doesn't appear to be working.  However, is there a way to simply clear the channel guide?  Then, I could check to make sure it is completely empty...and go from there.

I use schedules direct.

---

### Post by theophile on 2009-03-10
Sure, just drop the "program" table.

---

### Post by davidstoll on 2009-03-10
> **theophile said:**
> Sure, just drop the "program" table.

How is that done?

---

