---
title: "Ripping DVDs with bad sectors to .iso"
date: 2009-11-24
forum: Multimedia Software
---

### Post by justin99 on 2009-11-24
One big problem I had migrating to Linux was a way to truly rip a DVD.. often with deliberate bad sectors. I wrote a script that will repeatedly call dd and build up a .iso a bit at a time, hopefully avoiding the bad blocks and replacing them with zeros in the resulting .iso. It's a little raw at this point, but any help updating it is appreciated. In order to make it work correctly you'll need to change a couple variables at the beginning of the script (the number of blocks, and the input device).

[http://www.domain17.net/justin/linux/dvd_ripping/index.html](http://www.domain17.net/justin/linux/dvd_ripping/index.html)

~Justin

---

