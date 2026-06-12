---
title: "MCC Doesn't Properly Display Status of MySQL Daily Optimization Setting"
date: 2009-05-13
forum: Mythbuntu
---

### Post by uncle hammy on 2009-05-13
I have just upgraded my backend to 9.04.  I went into the MCC, and checked "Enable daily MythTV database optimization/repair".  After applying, it goes through the motions, however they checkbox always remains unchecked.

It does appear that it worked, because /etc/cron.daily does have a job "optimize_mythdb" in it.

However, the down side would be that it would be tough to decide not to do daily optimization through the GUI, because you would always be checking it again because it's always unchecked.

---

