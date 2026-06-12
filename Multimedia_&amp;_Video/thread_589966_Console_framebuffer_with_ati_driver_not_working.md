---
title: "Console framebuffer with ati driver not working"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by matthias_k on 2007-10-24
Hi,

since the fglrx driver for my Radeon 9800 card doesn't work at all, I have to fall back to the 'ati' driver module. It works just fine, even compositing, but the console framebuffer modes don't work: During boot or when switching to console from X11, I only see a black screen. The framebuffer mode is set to 1024x768x24 which should be fine.

Is that because the ati driver module does not support VESA framebuffer modes?

---

