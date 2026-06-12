---
title: "Two tuners, cant record two programs at the same time ??"
date: 2008-01-09
forum: Mythbuntu
---

### Post by styrofoam cup on 2008-01-09
Two tuners, cant record two programs at the same time ??

The tuners seem to setup ok and I can do picture in picture. But if I try to schedual two programs I get a conflict.

Tuners are USB twin, so they are two seperate devices, plugged onto the same motherboard header.

What can I do to record two programs??

Thank you.
:KS

---

### Post by newlinux on 2008-01-10
Can you watch them both for live TV? Are they setup with the same set of channels?

---

### Post by styrofoam cup on 2008-01-10
I can watch live tv on both tuners, and both have done a full scan to find channels when I set up the backend.
However I have noticed that only one seems to get the guide data over the air and the other tuner shows 'unknown' for all the guide data.

Also when  I start to watch tv I see '1: DVB Input' in the top left - this tuner gets the guide data. If I record a show with '1: DVB Input' then stop watching tv, then start watching tv again the top left corner has 'USB0' and I can watch and record other channels (but the guide data show only 'unknown'.

I had a look at the backend when I noticed this problem and the made sure both video inputs were called 'USB0' and 'USB1'

Note : I just checked the backend again (while typing this), and found 'USB0' was not set to get guide data, so fixed that.

Hopefully that fixes the problem. Would it be correct to assume that Mythtv records the shows by name, not by time of show ?? If not, can you suggest anything else that I might try to fix the problem ??

Thanks,
:KS

---

### Post by newlinux on 2008-01-11
If you are scheduling based on guide data, both tuners need to have guide data setup for them (make sure they are properly setup in mythtv-setup, if they have the same set of channels they should be tied to the same video source). Sounds like you fixed that. What was happening was that since only one of your tuners was tied to guide data, when looking to record those programs it could only find one tuner that had the shows, and if they were on at the same time it picked the higher priority one to record. To see if you are still having a problem, look at your upcoming recordings in the Manage Recordings menu to see what it plans on recording and on what tuner.

Manual recordings can be based on time. Other recordings are based on name of show, channel, episode, subtitle, priority, even tuner (you can specify which tuner will record which show) etc. depending on what options for recording you have setup.

---

### Post by styrofoam cup on 2008-01-11
Yep, it works ok now.

The guide data being setup for only one tuner was the problem just like you explained.

Thanks for your help.
:KS

---

