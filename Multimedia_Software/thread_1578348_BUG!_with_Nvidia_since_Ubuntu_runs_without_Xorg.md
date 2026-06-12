---
title: "BUG! with Nvidia since Ubuntu runs without Xorg"
date: 2010-09-20
forum: Multimedia Software
---

### Post by IronArjen on 2010-09-20
There appears to be a, rather serious problem with Ubuntu for certain machines with an Nvidia video card. I have been trying to get lucid working on one of my machines. It worked a number of times but most of the times it does not boot. I found several threads describing the problem but nothing really helps. I decided to get back to 9.10, installed it with no problem except that the resolution could not go beyond 800 x 600. Hence I installed the propietary driver and....it no longer boots. 

I suspect that 9.10 is the first Ubuntu that no longer requires an Xorg.conf, once you install the propietary driver, it does put an Xorg.conf but here it goes wrong. Lucid automatically detects the video card and tries to do arrange it and there it goes wrong. Lucid has the problem also on Live CD. Is there anybody who has an idea how to solve this? Can I report this as a Bug somewhere?

The annoying thing is that somehow I can not login in terminal mode and fix the Xorg. I mean I could install 9.04 (which I believe still requires an Xorg.conf) get it up an running and copy the Xorg.conf on a memory stick and later correct the problem in Lucid, but I cannot enter in terminal mode anymore.

---

