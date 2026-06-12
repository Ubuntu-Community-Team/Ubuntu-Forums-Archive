---
title: "Two machines, common problem"
date: 2008-03-19
forum: Mythbuntu
---

### Post by Scott Atkinson on 2008-03-19
How do I start parsing this problem?

I'm running a standard issue, nuthin' fancy Mythbuntu box. I install the OS, hook up cable and it runs fine...

...for maybe three days, five days, a week and a half.

Then the machine freezes and the entire install is corrupted. I can't connect to the backend, and even at the desktop level menus don't work right or at all.

Given my extremely limited technical abilities, when I reach this point, all I've done is reinstall.

Here's the kicker:

I'm not talking about one box. I'm talking about two completely different machines, which use different motherboards, memory, etc.

Both behave in exactly the same way.

Thoughts?

Thanks,

Scott A.

---

### Post by amd-64 on 2008-03-19
Are you filling up the harddisk some how. When it happens again, boot from a liveCD, and check disk space and inpect log files in /var/log and ~/.xsession-errors for clues.

---

### Post by Scott Atkinson on 2008-03-19
Will do.

A few more details:

- all the machines do is play out live tv, day in and day out. I  seldom change channels or do much of anything else to the systems.

- I've experienced the same problem with two separate copies of the live cd install disc, so I'm assuming it's not a stupid problem, like a subtly corrupted download.

- The myth boxes are part of a mixed bag of Macs, Winboxen, Tivos and a replay tv, all of which do roughly the same job, and none of which have shown similar symptoms.

(At this point, ironically, my WinXP Media Center + my BTV are far more stable.)

best,

s.

---

### Post by amd-64 on 2008-03-21
Well, the log files as I mentioned before are the starting point to figuring out why this  is happening. Even if other OSes do not show the same symptoms, linux may be keeping a very detailed log or having some component crashing and in the process filling up the disk with cores and logs.

---

