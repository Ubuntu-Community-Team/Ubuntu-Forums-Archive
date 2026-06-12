---
title: "Video files randomly stopping."
date: 2010-01-07
forum: Mythbuntu
---

### Post by Gamblor74 on 2010-01-07
Hi,

I have many AVI files, mostly converted from DVD's over the last few years, when watching an AVI using the Internal Player, it often randomly stop and goes back to the menu. Sometimes I can click play and the start again (from the beginning), sometime I have to restart the system to get it to play again.

I have Mythbuntu 9.10 (fresh install) as a standalone system. 

Anyone able to help??

Thanks

---

### Post by klc5555 on 2010-01-07
> **Gamblor74 said:**
> Hi,

I have many AVI files, mostly converted from DVD's over the last few years, when watching an AVI using the Internal Player, it often randomly stop and goes back to the menu. Sometimes I can click play and the start again (from the beginning), sometime I have to restart the system to get it to play again.

I have Mythbuntu 9.10 (fresh install) as a standalone system. 

Anyone able to help??

Thanks

I'll say straightaway that I don't know whether this has changed in mythtv 0.22. But in 0.21, the Myth internal player often has real trouble if a DVD ripped file does not have a proper frame index specially built for it in the database. The play length may turn out to be way wrong, can't jump forward and backward in the recording, etc. For each individual ripped video file, this could be fixed from a prompt with mythtranscode:

mythtranscode --mpeg2  --buildindex  --video -i [/path_and/filename]

In addition to a proper frame index, this procedure also produces a zero-length temp file, /../filename.tmp which you should eventually delete. 

You might want to give this a try on one of your troublesome videos.

---

