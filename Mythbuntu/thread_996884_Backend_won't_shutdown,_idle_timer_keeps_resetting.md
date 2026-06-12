---
title: "Backend won't shutdown, idle timer keeps resetting"
date: 2008-11-29
forum: Mythbuntu
---

### Post by SiHa on 2008-11-29
Been following the 'ACPI/Whatnext' guide to auto shutdown / wake, and am so nearly there.

In fact, if I set the idle timeout to something really low, like 120s, it all works beautifully.

But if I set it so something a bit longer, say 600s, I keep getting **'Reschedule requested for id -1'** entries in the backend log - each one resets the idle timer:

```
2008-11-29 14:11:19.477 I'm idle now... shutdown will occur in 600 seconds.
2008-11-29 14:14:06.375 Reschedule requested for id -1.
2008-11-29 14:14:06.495 Scheduled 24 items in 0.1 = 0.03 match + 0.08 place
2008-11-29 14:14:07.500 I'm idle now... shutdown will occur in 600 seconds.
2008-11-29 14:15:46.340 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-29 14:15:46.346 Expiring 589 MBytes for 1005 @ Fri Nov 28 13:45:00 2008 => Neighbours
2008-11-29 14:16:19.497 New DB connection, total: 4
2008-11-29 14:16:19.500 Connected to database 'mythconverg' at host: localhost
2008-11-29 14:17:24.990 Reschedule requested for id -1.
2008-11-29 14:17:25.130 Scheduled 24 items in 0.1 = 0.04 match + 0.10 place
2008-11-29 14:17:26.142 I'm idle now... shutdown will occur in 600 seconds.
2008-11-29 14:21:07.079 Reschedule requested for id -1.
2008-11-29 14:21:07.199 Scheduled 24 items in 0.1 = 0.03 match + 0.08 place
2008-11-29 14:21:08.203 I'm idle now... shutdown will occur in 600 seconds.
2008-11-29 14:26:20.890 Reschedule requested for id -1.
2008-11-29 14:26:21.026 Scheduled 24 items in 0.1 = 0.04 match + 0.09 place
2008-11-29 14:26:22.545 I'm idle now... shutdown will occur in 600 seconds.
2008-11-29 14:30:20.898 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-29 14:30:20.924 UPnpMedia: BuildMediaMap Done. Found 22 objects
2008-11-29 14:30:46.389 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-29 14:31:06.411 Reschedule requested for id -1.
2008-11-29 14:31:06.535 Scheduled 24 items in 0.1 = 0.04 match + 0.08 place
2008-11-29 14:31:07.539 I'm idle now... shutdown will occur in 600 seconds.
2008-11-29 14:34:52.497 Reschedule requested for id -1.
2008-11-29 14:34:52.615 Scheduled 24 items in 0.1 = 0.03 match + 0.08 place
2008-11-29 14:34:53.619 I'm idle now... shutdown will occur in 600 seconds.
2008-11-29 14:37:26.051 Reschedule requested for id -1.
2008-11-29 14:37:26.167 Scheduled 24 items in 0.1 = 0.03 match + 0.08 place
2008-11-29 14:37:27.172 I'm idle now... shutdown will occur in 600 seconds.
2008-11-29 14:41:04.936 Reschedule requested for id -1.
2008-11-29 14:41:05.057 Scheduled 24 items in 0.1 = 0.04 match + 0.08 place
2008-11-29 14:41:06.062 I'm idle now... shutdown will occur in 600 seconds.

```

Does anyone have any idea what this is about, and how I can stop it?

As I say - it's not the end of the world, I can just set the idle timeout to <4 minutes, but it's annoying.

TIA

Simon

---

### Post by laga on 2008-12-01
Are you using EIT?

---

### Post by SiHa on 2008-12-01
Hmm - I am as it happens.

When I first started experimenting with Myth back awhile, I had a few problems with setting up the grabbers & Mythfilldatabase --manual. EIT was far easier. But if it's causing problems, perhaps I should try again (and risk the wrath of the Wife)?

Or is there something simple I can do to stop the reschedules happening quite so often?

TIA,

Simon

---

### Post by Lil_Pete on 2009-12-19
Did you ever find a solution to this problem? I'm having an identical problem, although the computer does eventually shut itself down (at about 4 in the morning though!)

Thanks,

Peter

---

### Post by SiHa on 2009-12-19
As Laga alluded to, I believe it's the Active EIT Scan that causes this. In the end, I just left the idle timer at 2 minutes. As the frontend was running all day, it wouldn't shutdown until a cronjob killed the frontend @ 23:00, so the idle timer wasn't an issue, really.

---

