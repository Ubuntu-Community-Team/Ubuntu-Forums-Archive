---
title: "Previously functional RV620 (R600) Radeon card can't run Compiz without freezing."
date: 2011-05-13
forum: Multimedia Software
---

### Post by murderslastcrow on 2011-05-13
So, I had Ubuntu 10.04 installed with great compositing performance on my Radeon HD 3450 card, and I installed Ubuntu 11.04 last night. I can't get into anything but Ubuntu Classic (No Effects) to actually use the computer.

Whenever I log into Ubuntu Classic (w/ Effects), I can hear the start sound, the panels and some shadows show up, but immediately after they first render, I can't touch anything, shadows disappear wherever I click, and it freezes, forcing me to drop to a tty and kill X.

Whenever I try to start Unity, I hear the start sound, but never see anything but the wallpaper. Also, the screen will sometimes go black for a second or so before returning to the same frozen graphics available previously, and sometimes I can't even drop to a tty after it does this.

From glxinfo, everything seems to be in order. Here is the relevant data.

> direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on AMD RV620
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20


So far as I know, Unity should support OpenGL 1.5+ capable drivers/cards, and compiz should support even lower requirements. As I said, on the LTS release the drivers performed admirably well, far better than fglrx on the same card- much more fluid, no jerkiness.

I can get Unity working with fglrx, but it's quite depressing to watch, and I don't plan on using it when I have an open card that should work well. I am aware that there were recent changes to the kernel to bring in the Gallium driver for R600 cards- I've read something about r600g and r600c and one of them being used in Ubuntu. I'm supposing the recent change is what's causing these issues, and I'm curious about how to change them back or correct whatever is causing these problems.

Thank you in advance for reading this huge post and giving feedback.

---

### Post by murderslastcrow on 2011-05-13
Well, the helpful folks over at the radeon IRC channel helped me figure this out. By default, the kernel sets your mode to AGP (at least on my card), so you have to add the following to your linux boot command line in grub- radeon.agpmode=-1. This changes it from AGP to PCI, which performs very well, even compared to the fglrx driver (which is actually really bad this release).

So, thanks for reading- hopefully if anyone else has a similar issue they'll find this post.

---

