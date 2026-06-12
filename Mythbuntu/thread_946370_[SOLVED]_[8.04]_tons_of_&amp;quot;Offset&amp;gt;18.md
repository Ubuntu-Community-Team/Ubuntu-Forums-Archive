---
title: "[SOLVED] [8.04] tons of &amp;quot;Offset&amp;gt;181&amp;quot; errors"
date: 2008-10-13
forum: Mythbuntu
---

### Post by Verzweifler on 2008-10-13
I receive a lot of errors on my MasterBackend obviously caused by the EIT.

```
michael@mythserver:~$ tail -f /var/log/mythtv/mythbackend.log
2008-10-13 14:44:17.874 Error: offset>181, pes length & current can not be queried
2008-10-13 14:44:24.846 Error: offset>181, pes length & current can not be queried
2008-10-13 14:44:24.996 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-10-13 14:44:24.999 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-10-13 14:44:26.198 Error: offset>181, pes length & current can not be queried
2008-10-13 14:44:33.170 Error: offset>181, pes length & current can not be queried
2008-10-13 14:44:34.574 Error: offset>181, pes length & current can not be queried
2008-10-13 14:44:41.542 Error: offset>181, pes length & current can not be queried
2008-10-13 14:44:42.894 Error: offset>181, pes length & current can not be queried
2008-10-13 14:44:49.862 Error: offset>181, pes length & current can not be queried
2008-10-13 14:44:51.218 Error: offset>181, pes length & current can not be queried
2008-10-13 14:44:58.186 Error: offset>181, pes length & current can not be queried
2008-10-13 14:44:59.538 Error: offset>181, pes length & current can not be queried
2008-10-13 14:45:06.522 Error: offset>181, pes length & current can not be queried
2008-10-13 14:45:07.878 Error: offset>181, pes length & current can not be queried
2008-10-13 14:45:09.497 Reschedule requested for id -1.
2008-10-13 14:45:10.161 Scheduled 134 items in 0.7 = 0.03 match + 0.63 place
2008-10-13 14:45:11.164 I'm idle now... shutdown will occur in 90 seconds.
2008-10-13 14:45:14.854 Error: offset>181, pes length & current can not be queried
2008-10-13 14:45:16.210 Error: offset>181, pes length & current can not be queried

```

Does this look familiar to anybody? If so, please let me know...

---

### Post by mrand on 2008-10-13
> **Verzweifler said:**
> I receive a lot of errors on my MasterBackend obviously caused by the EIT.

```
michael@mythserver:~$ tail -f /var/log/mythtv/mythbackend.log
2008-10-13 14:44:17.874 Error: offset>181, pes length & current can not be queried

```Does this look familiar to anybody? If so, please let me know...

Google searches seem to turn up some hints that it is maybe related to poor reception or corrupted EIT listings.  I'm sorry I can't be of more help.

[INDENT]Marc[/INDENT]

---

### Post by Verzweifler on 2008-10-18
I finally found the reason for the error messages:
My DVB-S cards were trying to retrieve EIT information from channels actually not providing such... 

I updated my channels-table and after setting "useonairguide" to "0" for the channels in question, the errors were gone.

---

