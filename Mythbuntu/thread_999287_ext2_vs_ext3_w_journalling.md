---
title: "ext2 vs ext3 w/ journalling"
date: 2008-12-01
forum: Mythbuntu
---

### Post by netslacker on 2008-12-01
I'm currently running ext3 on my default storage drive (where I store all the recorded tv shows) but I have found that deleting a show can take a real long time due to journalling on the ext3 file system.  What do others use?  Should I convert the drive to ext2?  I have seen multiple how-to's on going to ext2 but I was curious if others see this same thing w/ ext3.

Thanks.

---

### Post by ian dobson on 2008-12-02
Hi,

Have you enabled the "Slow delete" option in Myth-setup. Regardless of the name this actually speeded up deleting for me on my ext3 file system.

Regards
Ian Dobson

---

### Post by uncle hammy on 2008-12-02
I always use XFS on my storage drives, and make sure I check the "Daily Defrag of XFS" option in the Mythbuntu Control Center Advanced Options.  Super fast for deleting.

---

### Post by netslacker on 2008-12-02
I will try the "slow delete" checkbox and see what that does.
  
Going to XFS isn't an option since that would require that I re-format the drive and lose 100+ hours of recordings (uh, no).

---

### Post by fatmonk on 2008-12-03
> **uncle hammy said:**
> I always use XFS on my storage drives, and make sure I check the "Daily Defrag of XFS" option in the Mythbuntu Control Center Advanced Options.  Super fast for deleting.

Do you use commercial flagging in your system?

I've started a thread regarding commercial flagging killing my xfs drive, and have found other posts on other forums about the same thing, so would be interested to know if it works ok for other people.

-FM

---

### Post by netslacker on 2008-12-03
Yes, I run commercial flagging on my system w/ ext3 and have had NO problems with it whatsoever.  It just runs and completes every time.

---

