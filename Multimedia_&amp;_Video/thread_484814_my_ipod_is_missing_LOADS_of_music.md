---
title: "my ipod is missing LOADS of music"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by lunarcloud on 2007-06-26
I transer my music over (with amarok) but a lot of music isnt on the ipod, though it seems to take up the physical space.

I've heard of something to do with "stale and orphaned" but that option just makes amarok lock up.

NVM people. If you transfer your music in small doses, the ipod doesn't complain.

---

### Post by singlemalt on 2007-07-19
> **zarquad said:**
> I transer my music over (with amarok) but a lot of music isnt on the ipod, though it seems to take up the physical space.

I've heard of something to do with "stale and orphaned" but that option just makes amarok lock up.

NVM people. If you transfer your music in small doses, the ipod doesn't complain.

Similar problem here.

I have found the following information

The most likely reason for this is a version of libgpod that is incompatible with your Amarok binary. This happens mainly if your distributor compiled Amarok against libgpod 0.3.2 and later on upgrades libgpod to 0.4.0 without providing an updated Amarok binary, which is compiled against libgpod 0.4.0. The solution for this problem is to downgrade libgpod to 0.3.2.

So can anyone tell me how to downgrade libgpod?

---

### Post by penno on 2007-11-07
anyone?

---

