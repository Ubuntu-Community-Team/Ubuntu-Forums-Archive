---
title: "Mythbuntu 10.04 minor installer issue"
date: 2010-04-19
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2010-04-19
Sorry for this post on beta 1 - I just noticed beta 2 is out - dang:

1)  Minor install issue.  On the summary screen where it shows what install actions are about to happen (screen 13/13 as I recall).  Mythbuntu says it won't be changing the partition table when it sure will be changing the table.

To recreate: I did a dual boot with Win XP (just for giggles).  Used Mythbuntu 10.04 beta 1 as a partition editor.  Created a 100 G partition, 900 G left unused. Installed Win XP (took four freaking hours - loads of driver trouble!), then did a Mythbuntu 10.04 beta 1 install (took 20 minutes - nice!).  

I told the installer it was dual boot with xp, full auto partitioning of the unused space.  The summary page showed "no partition changes."  That doesn't seem right.  It was going to make a swap partition and EXT4 partition.  That sounds like a change to me.

---

### Post by superm1 on 2010-04-20
> **Dewey_Oxberger said:**
> Sorry for this post on beta 1 - I just noticed beta 2 is out - dang:

1)  Minor install issue.  On the summary screen where it shows what install actions are about to happen (screen 13/13 as I recall).  Mythbuntu says it won't be changing the partition table when it sure will be changing the table.

To recreate: I did a dual boot with Win XP (just for giggles).  Used Mythbuntu 10.04 beta 1 as a partition editor.  Created a 100 G partition, 900 G left unused. Installed Win XP (took four freaking hours - loads of driver trouble!), then did a Mythbuntu 10.04 beta 1 install (took 20 minutes - nice!).  

I told the installer it was dual boot with xp, full auto partitioning of the unused space.  The summary page showed "no partition changes."  That doesn't seem right.  It was going to make a swap partition and EXT4 partition.  That sounds like a change to me.
Hi,

This sounds like a bug in the generic portion of the installer (we have plugins that layer on it otherwise).

Can you please do the following:

1) Boot up the live disk again
2) Choose the "Try Mythbuntu" option
3) Open a terminal and type the following to run ubiquity in debug mode:
ubiquity -d
4) Make it to the summary screen to reproduce the bug
5) Close ubiquity
6) From a terminal again, type the following to file a bug report:
ubuntu-bug ubiquity

Thanks!

---

### Post by Dewey_Oxberger on 2010-04-20
Nice!  I learned something.  Dang this ubuntu thing is getting cooler and cooler.  Ubuntu-bug and the tie-in to launchpad is way handy.  I've been cutting and pasting all this time.

Turns out this issue has been reported by the zillions so I jumped on the lead bug.

Does myth control centre have a debug mode that will work with ubuntu-bug?

---

### Post by superm1 on 2010-04-20
> **Dewey_Oxberger said:**
> Nice!  I learned something.  Dang this ubuntu thing is getting cooler and cooler.  Ubuntu-bug and the tie-in to launchpad is way handy.  I've been cutting and pasting all this time.

Turns out this issue has been reported by the zillions so I jumped on the lead bug.

Does myth control centre have a debug mode that will work with ubuntu-bug?
There are ways to put it into debug mode, but it's not nearly as useful as ubiquity is in debug mode.  Something we can try to improve upon for 10.10 though :)

But a lot of packages will automatically upload the right logs if you use ubuntu-bug to file a bug on them (including mythtv and mythplugins!)

---

