---
title: "make recordings start ans end on time by default"
date: 2013-09-28
forum: Mythbuntu
---

### Post by itlarson2 on 2013-09-28
Sometime last summer I noticed some of my shows weren't recording because of schedule conflicts when they shouldn't have been conflicting.  Recently I figured out this is because any new recording rule I created by default starts five minutes early, and ends five minutes late.  Mythtv refuses to disregard this, so any two programs in adjacent timeslots cause a conflict if there's not another tuner available. 

Obviously this is BAD BAD BAD!

 Because of this, for years, I used to have everything set to start on time by default.  However this setting no longer seems to exist.  How can I fix this?  I don't trust myself to remember to manually change this every time.

---

### Post by tgm4883 on 2013-09-28
Setup > Video > General, 4th screen in

The settings you want are

Time to record before start of show (secs)
Time to record past end of show (secs)

---

### Post by itlarson2 on 2013-09-29
No- that's a completely separate setting.  It's the one I actually use, since it DOESN'T create a conflict when two recordings are in adjacent time slots.  The setting I am looking for wil cause the "start recording on time" and "end recording on time" to be the default under "schedule options" when I create a recording rule.  I found an old post which told where this setting is, but it isn't there any more.  I am hoping this setting has been moved somewhere where I'm not finding it, or at least there's a hack to work around this problem.  If the latter is the case, I'm reporting this as a bug, since there's no way a default setting should cause shows to be not recorded for no good reason.  Ideally there would an additional setting in "schedule options" which would allow you to choose whether the record early/late times can be ignored or not, with the default being to let them to be ignored.  Then the setting you refer to could then be removed, since it would be redundant.

---

