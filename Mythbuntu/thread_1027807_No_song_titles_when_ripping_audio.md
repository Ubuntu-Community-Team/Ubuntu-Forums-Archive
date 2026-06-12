---
title: "No song titles when ripping audio"
date: 2009-01-01
forum: Mythbuntu
---

### Post by korgman on 2009-01-01
Started ripping more music today and all of a sudden the song titles aren't appearing when I do a scan CD. Myth is finding the artist and the first track. If I manually rescan the CD, I lose the info for the first track. It's getting the album name and artist. Thoughts?

Matt

---

### Post by korgman on 2009-01-02
Well, this was just a symptom of a much larger problem. /sda1 was 100% full. mythtvfrontend.log was absolutely huge filled with this:

2008-12-29 10:59:57.397 NVP: Prebuffer wait timed out 10 times.
2008-12-29 10:59:58.847 NVP: Prebuffer wait timed out 10 times.
2008-12-29 11:00:00.314 NVP: Prebuffer wait timed out 10 times.
2008-12-29 11:00:01.830 NVP: Prebuffer wait timed out 10 times.
2008-12-29 11:00:02.224 LiveTV forcing JumpTo 1
2008-12-29 11:00:02.239 LiveTV forcing JumpTo 1
2008-12-29 11:00:02.240 LiveTV forcing JumpTo 1
2008-12-29 11:00:02.240 LiveTV forcing JumpTo 1
2008-12-29 11:00:02.240 LiveTV forcing JumpTo 1
2008-12-29 11:00:02.240 LiveTV forcing JumpTo 1
2008-12-29 11:00:02.240 LiveTV forcing JumpTo 1

And that repeated a few millions times.

---

