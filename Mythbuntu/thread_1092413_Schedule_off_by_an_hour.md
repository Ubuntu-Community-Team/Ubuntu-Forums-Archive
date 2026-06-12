---
title: "Schedule off by an hour"
date: 2009-03-10
forum: Mythbuntu
---

### Post by itlarson on 2009-03-10
When I went to watch recordings last night, I found that I had recordings, but not of the right things.  All of my recordings for Monday night were of the previous hour.  I checked the system time, but it was correct.  I checked the schedule, and found that all the times were wrong-  it showed Jay Lenno coming on at 9:30 for example.  The schedules for upcoming nights are correct.  Is this a problem with my system, or a schedules direct screwup?

---

### Post by klc5555 on 2009-03-10
> **itlarson said:**
> When I went to watch recordings last night, I found that I had recordings, but not of the right things.  All of my recordings for Monday night were of the previous hour.  I checked the system time, but it was correct.  I checked the schedule, and found that all the times were wrong-  it showed Jay Lenno coming on at 9:30 for example.  The schedules for upcoming nights are correct.  Is this a problem with my system, or a schedules direct screwup?

Probably neither.

I noticed yesterday afternoon that Comcast's own tv listings on the web at comcast.net were off by an hour. In fact, they still are for my area. So I suspect that Schedules Direct are actually downstream from the real daylight-savings-time screwup, and likely were (or are) getting bad data like everyone else.

---

### Post by sports fan Matt on 2009-03-10
Ive noticed the same thing with over the air converter boxes so you arent alone.

---

### Post by Caps18 on 2009-03-10
Check to make sure your system time is correct.  It may not have changed when Daylight Saving Time occurred.

My Schedule Direct TV guide for over the air correctly recorded my TV show last night.  If your cable provider is giving them bad info, then it might be that.

---

### Post by itlarson on 2009-03-10
Thanks-  I was concerned it was something with my system.

---

### Post by itlarson on 2009-03-10
I was still finding some of the channels to be off by an hour, so I tried  "sudo mythfilldatabase --refresh-all" and it seems to have worked.

---

