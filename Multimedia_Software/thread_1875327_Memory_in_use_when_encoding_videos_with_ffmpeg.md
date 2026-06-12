---
title: "Memory in use when encoding videos with ffmpeg"
date: 2011-11-04
forum: Multimedia Software
---

### Post by dcmsky on 2011-11-04
I don't know much about memory usage in ubuntu.  I'm hosting a server on rackspace to processing videos using ffmpeg.  Am I ok here according to this?

this is while 5 videos are encoding:

top - 20:15:06 up 42 days,  5:44,  1 user,  load average: 4.22, 1.93, 1.29
Mem:   1022536k total,  1000744k used,    21792k free,     2744k buffers
Swap:  2097148k total,   158872k used,  1938276k free,   575588k cached

the only things I've installed on this server are apache, php & ffmpeg.

---

### Post by gordintoronto on 2011-11-04
It's using swap, which might slow things down. What do the figures look like when you are encoding four videos?

---

