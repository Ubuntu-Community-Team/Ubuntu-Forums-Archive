---
title: "Code required to delete the last 5 seconds of a video with using ffmpeg &amp; mencoder"
date: 2009-09-03
forum: Multimedia Software
---

### Post by Rytron on 2009-09-03
Hi.

How would i delete/snip the last 5 seconds of a flv file with ffmpeg?

How would i delete/snip the last 5 seconds of a flv file with mencoder?

Thanks.

---

### Post by stefangr1 on 2009-09-03
With mencoder:

mencoder -endpos hh:mm:ss -ovc copy -oac copy in.flv -o out.flv

Where you have to find out for yourself how long the new movie should be.

---

### Post by Rytron on 2009-09-03
> **stefangr1 said:**
> With mencoder:

mencoder -endpos hh:mm:ss -ovc copy -oac copy in.flv -o out.flv

Where you have to find out for yourself how long the new movie should be.

So for example if a file is 6:27 (6 minutes & 27 seconds) and I want only want to keep 6:05 (therefore cutting away the last 22 seconds) would I do this:

mencoder -endpos hh:6:05 -ovc copy -oac copy in.flv -o out.flv

---

### Post by mc4man on 2009-09-03
as to the suitability of mencoder with flv I'm not sure but you'd set the end position as such
-endpos 00:06:05

---

