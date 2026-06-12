---
title: "Kdenlive video encoding not encoding the red colour"
date: 2012-03-15
forum: Multimedia Software
---

### Post by lukjad on 2012-03-15
I'm using Ubuntu 11.10 with Kdenlive Version 0.8.3 Using KDE Development Platform 4.7.4 (4.7.4)

I did try rebooting and searching on the internet, but nothing seemed to show this issue.

The only thing I can think of is that I ran up updates with Ubuntu Tweak, but they were not on kdenlive so I don't see the connection, though who knows, since it did update Avidemux and VLC. Yesterday everything encoded perfectly, no issues at all.

EDIT: As suggested, a few things I tested:

Different formats within kdenlive. They all had the same issue.

Different programs.

I tried exporting with Openshot, that worked fine. No colour issues at all. So this seems related to kdenlive.

I reverted back to Version 0.8.3 from the repos, same issue.

EDIT: Found the source, a corrupted save file. Removed and tested with fresh one, now works.

---

