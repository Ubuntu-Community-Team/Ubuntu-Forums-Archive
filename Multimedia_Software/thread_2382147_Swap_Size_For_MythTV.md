---
title: "Swap Size For MythTV"
date: 2018-01-09
forum: Multimedia Software
---

### Post by jamoody on 2018-01-09
I'm doing a new 64-bit MythTV combined frontend/backend build with 16G RAM.  According to [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) the latest Ubuntu recommendation for swap size is 4G-32G which is a pretty wide range, with the higher end desirable for video editing.  I see no specific MythTV recommendations with regard to swap.  Does commercial flagging count as video editing and thus desirable for the larger swap?  This machine is dedicated to always on MythTV operation (no hibernation) with 4 HD tuners and multiple 2T drives.  Allocating even large amounts of swap space is not really an issue, but 32G swap seems like an awful lot.  My current 32-bit MythTV uses 4G RAM and 4G swap with around 30% swap use according to top.  I seem to recall that buffers will consume as much RAM as available which might explain the 25% (1G) swap use.

Any suggestions on the amount of swap needed for 16G MythTV frontend/backend system?

---

### Post by cruzer001 on 2018-01-09
I have 24G of ram and 2G of swap and swappiness set to zero.

[https://www.google.com/search?client=ubuntu&channel=fs&q=Is+SWAP+necessary&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=Is+SWAP+necessary&ie=utf-8&oe=utf-8)

---

### Post by jamoody on 2018-01-30
I settled on 8G swap which is probably overkill for 16G RAM.  So far 0% swap used but I'm still in the early stages of testing MythTV.  We'll see how it goes.

---

