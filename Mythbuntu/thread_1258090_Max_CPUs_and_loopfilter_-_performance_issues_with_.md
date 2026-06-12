---
title: "Max CPUs and loopfilter - performance issues with 0.22"
date: 2009-09-04
forum: Mythbuntu
---

### Post by red321 on 2009-09-04
All,

I have been happily using my front end on a dual core processor, using the 0.21-fixes branch of mythbuntu binaries. 

When I tried out 0.22-trunk, I found that my frontend couldn't run BBC-HD without glitching. When I checked the playback options, the Loopfilter dissable option had disappeared from the menu screens.  The patch is no longer applied in trunk mythbuntu builds. So I've spent way too much time allready trying to bring the patch back up to date.


**However, I came across somthing odd.** The load sharing across processors that max CPUs is supposed to let you do, seems dependent on my skiploop patch. That makes no sense, because the max CPUs setting is a long standing mythtv "official" setting.

I've reverted back to 0.21-fixes, which does include the loopfilter disable checkbox. It seems to display the same behaviour. Before I take this back to the mythtv mailing list, can anybody confirm this behaviour?

If you are watching BBC-HD using ffmpeg, and a multicore cpu, can you check what the cpu loadbalancing is like, on either trunk or fixes with loopfilter dissabled.

Be nice to know if I am just losing my mind .....;-)

John

---

