---
title: "How are lease times sent"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by lavinog on 2010-04-21
I am having an issue with my router not getting a valid ip address.  The problem seems to occur each day at the same time.  Manually renewing fixes it, but it is a pain.

After looking at the event logs in the modem, I have determined that the modem does not handle DST correctly.
My question is should this be affecting lease times?
Are lease times sent as a time delta (such as 3600 secs) or is a local time used?
It seems that it would make more sense if a delta is used, but a local time would explain my issue.

---

