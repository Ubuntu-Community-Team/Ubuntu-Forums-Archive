---
title: "Episode Limit and re-record"
date: 2009-02-20
forum: Mythbuntu
---

### Post by ForgivenByJC on 2009-02-20
Searching mythtv "episode limit" I have found this:

> [FONT="Courier New"]Episode Limit
An episode limit can also be configured to limit the maximum number of episodes recorded of a single series, to restrict that series' disk usage. If this is set, you can further decide what to do when this limit is reached; either stop recording that series, or to delete the oldest episodes in favor of the new ones.
[/FONT]
I have selected a limit and "Delete oldest if this would exceed the max episodes" option.  Does it re-record episodes it has deleted which where not watched?  What if "auto expire" deletes an unwatched program, will it be re-recorded?

The idea is to have a stack of recently recorded unwatched episodes of my favorite shows including the re-runs I have not seen yet.  Is there a section of the documentation which covers this scenario?
Thanks,
John

---

### Post by itlarson on 2009-02-20
I'm about 90% sure stuff re-records.

---

### Post by ForgivenByJC on 2009-02-23
Is anyone able to verify this?

---

### Post by ForgivenByJC on 2009-04-17
:D Good news!  Was able to verify this (finally!) by watching a recording, marking the recording as unwatched, setting the episode limit for that show to be deleted, and then checking Manage Recordings -> Previously Recorded to verify it was scheduled to "re-record."  Whew!
I hope this helps people.  Thanks itlarson for your help.  If anyone with influence with MythTV is reading this, I would like to suggest clarifying this in the documentation.

CONCLUSION:
If an episode limit deletes a recording marked as unwatched, it will record the episode again (re-record).  If the episode limit deletes a recording marked as watched, it will not record the episode again (recorded/previously recorded).
aka
When episode limit deletes
watched = recorded or previously recorded
UNwatched = Re-Record

---

