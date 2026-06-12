---
title: "Dumb question: When is the fallback deinterlacer used?"
date: 2008-11-24
forum: Mythbuntu
---

### Post by gdir on 2008-11-24
Hello,

I'm fairly new to MythTV and so this may be a dumb question, but I didn't find an answer by reading the docs or searching the forums.

If I specify a primary and a fallback deinterlacer for TV playback, in which cases will the fallback deinterlacer be used instead of the primary deinterlacer?

Thanks,

Guenther

---

### Post by ian dobson on 2008-11-24
Hi,

From the way I understand it (I've played about abit in the source code) the frontend tries the first deinterlacer and if the deinterlacer returns an error (Cannot handle format, driver not installed, hardware not supported) then it tries the fallback deinterlacer.

Regards
Ian Dobson

---

### Post by laga on 2008-11-24
A common case of failure is probably with the "2x" (frame doubling) deinterlacers. These require the refresh rate of the display to be twice as high as the video frame rate. The fallback deinterlacer is probably also used when fast forwarding when a 2x deinterlacer is used by default.

AFAIK :)

---

### Post by gdir on 2008-11-25
Thank you both!

---

