---
title: "me-tv only works using sudo privileges for DVB tuner"
date: 2014-04-02
forum: Multimedia Software
---

### Post by sdowney717 on 2014-04-02
[https://bugs.launchpad.net/me-tv/+bug/619530](https://bugs.launchpad.net/me-tv/+bug/619530)

mentions a solution

> And now I figured it out properly.

The DVB adapters were in accessible by a special "video" group only. The MythTV daemon account was a member of this group.

My interactive a/c that I was using to test MeTV wasn't.

Either the MythTV setup did this itself, or I did it some ages ago and forgot about it.

When I added the interactive a/c to the right group it works without sudo.

My bug. Close as invalid.

How can I apply it to my case?
me-tv used to work without needing sudo. I setup mythtv and then me-tv started having this problem.

---

