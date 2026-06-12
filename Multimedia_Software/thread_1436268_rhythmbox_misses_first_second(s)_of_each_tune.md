---
title: "rhythmbox misses first second(s) of each tune"
date: 2010-03-22
forum: Multimedia Software
---

### Post by karrank% on 2010-03-22
Apologies if this has been covered, my search hasn't pulled anything up, so here goes: rhythmbox drops the first moment, or second, of each tune I play on it. Can't figure how to fix it. Any ideas?

Thanks for looking. -Oh, v 0.11.5

hardy 8.04  btw. old, I know (like me) but works, mostly (like me)

---

### Post by tgalati4 on 2010-03-22
Do you have the crossfade plug-in enabled?  It fades two songs together seemlessly and that could chop the first couple of seconds off of the first song.

Open up a terminal; stretch it wide, look for errors in:

rhythmbox --debug

---

### Post by karrank% on 2010-03-22
> **tgalati4 said:**
> Do you have the crossfade plug-in enabled?  It fades two songs together seemlessly and that could chop the first couple of seconds off of the first song.

Open up a terminal; stretch it wide, look for errors in:

rhythmbox --debug

I hadn't enabled crossfade until I noticed this problem, after which I enabled it, without any apparent change in the initial second missing.

Opened terminal and followed directions, and now have hundreds(?) of lines of characters. Pardon my ignorance--and not sure I'm allowed to post something that big--but what would an error look like? 

Thanks for taking an interest.

-embarrassed n00b

---

### Post by karrank% on 2010-03-22
Mark this one as solved, I guess. Went back into preferences, maxed out network buffer size, unchecked both crossfade option boxes, went back in, tested a few tracks, and bingo, problem gone.

Thanks for pointing me in the right direction. 

Hope I can help someone else sometime.

---

