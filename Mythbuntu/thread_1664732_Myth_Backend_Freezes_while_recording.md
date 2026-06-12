---
title: "Myth Backend Freezes while recording"
date: 2011-01-11
forum: Mythbuntu
---

### Post by dtaylorl on 2011-01-11
I've been running this MythTV box for ~10 months now, but it just recently started having a problem where the system freezes during recording. This is getting really frustrating as it has caused me to miss key parts of the Seahawks Saints game and BCS Championship...  The backend logs don't seem to show anything interesting.  The only *possible* thing is that it looks like it was auto-expiring an old recording at the time it froze.  Any ideas on what how I should go about troubleshooting this?

---

### Post by ian dobson on 2011-01-11
Hi,

Do you have comm flagging enabled? If so try disabling it, atleast temporally. Could the problem be high CPU load/high temperatures?

Freeze ups are usually hard to find. Could it be some hardware problem? Fan's full of dust or something like that.

Regards
Ian Dobson

---

### Post by dtaylorl on 2011-01-11
I haven't been able to check CPU load at the time of the freeze, but normally I'm only at about 30% CPU usage.  I'll check the fans to see if temperature might be an issue.  It froze again this morning while I wasn't recording and once again the last thing in the log was about auto expiry.  My hard drive is almost full, so I'm going to see if freeing up some space takes care of the problem.  Has anyone else ever experienced freezing when myth is auto expiring programs?

---

### Post by ian dobson on 2011-01-11
Hi,

What filesystem are you using for your recording drive? Do you have "slow delete" enabled for your recordings?

Regards
Ian Dobson

---

### Post by dtaylorl on 2011-01-12
I'll have to double-check, but I'm pretty sure its XFS (the other possibility is JFS).  My impression that was "slow delete" is only necessary when using a less efficient filesystem like ext3... should I still try turning it on to see if that solves the issue?

---

### Post by ian dobson on 2011-01-12
Hi,

Yes slow delete is mainly to help the really bad delete code in the ext4 file system. I don't realy know about XFS/JFS I've only really used ext2/3/4.

Regards
Ian Dobson

---

