---
title: "Is that possible for Mplayer to repeat a part of movie when it's running?"
date: 2008-11-24
forum: Multimedia Software
---

### Post by Kelen.Chang on 2008-11-24
some times i want repeat the part of movie, when it's running. is that possible for Mplayer?
But i hope that all works on it's running.

---

### Post by andrew.46 on 2008-11-26
Hi,

I guess that would not be a problem with the gui gmplayer or the best of all MPlayer gui: smplayer.

From the command line I don't believe that this is possible on the fly. It can certainly be planned by using the -loop option:

> -loop <number>
Loops movie playback <number> times.  0 means forever.

together with options like seek (-ss), end position (-endpos) and looking at single chapters (-chapter).

Not quite what you are after though?

  Andrew

---

