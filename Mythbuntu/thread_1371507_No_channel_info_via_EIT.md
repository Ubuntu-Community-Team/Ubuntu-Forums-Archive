---
title: "No channel info via EIT"
date: 2010-01-03
forum: Mythbuntu
---

### Post by stevanbt on 2010-01-03
Hi,
Further to my previous post [here]("http://ubuntuforums.org/showthread.php?t=1366221") I successfully re-scanned Astra and Eurobird channels... and all appeared to be ok (scheduled recordings all work, live-tv etc).

However, I now notice that the schedule information hasn't been updated since the scan.  I only had tomorrow's schedule information in the database... since I tried to fix it I now have no schedule information left LOL.

There are no EIT related errors in the backend log.

I guess I could remove all sources etc in mythtv-setup and start again, but I'd prefer not to.

Is there a way to check EIT information is being received correctly by my DVB-S cards?

Thanks, Steve.

---

### Post by stevanbt on 2010-01-04
Sorted out the missing EIT channel information.  I had to do a full scan of channels in mythtv-setup - using channel.conf or "existing transports" didn't work.

Thanks, Steve.

---

