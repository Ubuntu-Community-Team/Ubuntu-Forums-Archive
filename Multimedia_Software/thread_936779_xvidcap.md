---
title: "xvidcap"
date: 2008-10-03
forum: Multimedia Software
---

### Post by Achilles124 on 2008-10-03
I am trying to use [COLOR="Red"]xvidcap[/COLOR] to capture some video. But when I press the record button, it vanishes from the screen. It starts recording though but I don't know how to stop it.

---

### Post by IllegalCharacter on 2008-10-03
I'll confirm this problem, tried it on two different Ubuntu 64-bit machines. One just segfaulted, the other gives the error:

xtoffmpeg.c guess_input_pix_fmt(): image depth 32 not supported ... aborting

I tried to compile xvidcap from source, but got a bunch of source code errors like "X not defined", didn't have time to check it out too much. If I have time this weekend I'll look into it and see if I can find a fix.

---

### Post by Achilles124 on 2008-10-06
And, Illegal Character, any luck?

---

