---
title: "Where'd Automatic Defrag Go?"
date: 2010-03-20
forum: Mythbuntu
---

### Post by uncle hammy on 2010-03-20
I installed Mythbuntu 9.10 pretty much on release day.  I went through my typical installation routine, and never gave it much more thought.  Today for some unknown reason I had a thought to check the fragmentation level of my xfs drives and discovered them all 90%+.  

"Weird" I thought, so I went into the Mythbuntu Control Panel to make sure I had the old "enable daily XFS defragmentation" enabled....to discover the option is no longer there.

So, my question is....Where did it go?

---

### Post by superm1 on 2010-03-22
> **uncle hammy said:**
> I installed Mythbuntu 9.10 pretty much on release day.  I went through my typical installation routine, and never gave it much more thought.  Today for some unknown reason I had a thought to check the fragmentation level of my xfs drives and discovered them all 90%+.  

"Weird" I thought, so I went into the Mythbuntu Control Panel to make sure I had the old "enable daily XFS defragmentation" enabled....to discover the option is no longer there.

So, my question is....Where did it go?

By default the filesystem is ext4 for the installs these days, so the option is less beneficial to the default case.  You can still manually set up a cron job to do it though.

---

### Post by uncle hammy on 2010-03-22
> **superm1 said:**
> By default the filesystem is ext4 for the installs these days, so the option is less beneficial to the default case.  You can still manually set up a cron job to do it though.
I did set it up manually.  Though I would argue that it is less beneficial to new installs (and I mean completely fresh) only.  Anyone who upgrades and has a whack of stuff recorded is likely to still have an XFS file system, unless they want to lose everything, or spend a lot of time moving things around.  For example, I have 2.5TB of existing XFS drives....not likely to delete all that and start over, or spend hours trying to off load it, convert to EXT4, then bring it all back.

That is unless of coarse, I am missing something and there is a way to convert an XFS system to EXT4.

---

### Post by Dewey_Oxberger on 2010-03-22
Is ext4 working okay for myth?  Is it fast enough?  No delete performance issues?

If so my next install will just use it.

---

### Post by superm1 on 2010-03-23
> **uncle hammy said:**
> I did set it up manually.  Though I would argue that it is less beneficial to new installs (and I mean completely fresh) only.  Anyone who upgrades and has a whack of stuff recorded is likely to still have an XFS file system, unless they want to lose everything, or spend a lot of time moving things around.  For example, I have 2.5TB of existing XFS drives....not likely to delete all that and start over, or spend hours trying to off load it, convert to EXT4, then bring it all back.

That is unless of coarse, I am missing something and there is a way to convert an XFS system to EXT4.
No, no way to convert.  We haven't done XFS by default for a few releases now.  So probably won't be reinstating that option.

> **Dewey_Oxberger said:**
> Is ext4 working okay for myth?  Is it fast enough?  No delete performance issues?

If so my next install will just use it.

Works great for me.  Performance appears fine. Hence why it's the default now :)

---

### Post by tgm4883 on 2010-03-23
Bug filed for this at [https://bugs.edge.launchpad.net/mythbuntu/+bug/545232](https://bugs.edge.launchpad.net/mythbuntu/+bug/545232)

---

