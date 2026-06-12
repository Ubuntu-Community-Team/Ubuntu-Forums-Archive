---
title: "Multiple frame buffer creation problem"
date: 2008-11-20
forum: Multimedia Software
---

### Post by nightwatchman on 2008-11-20
Hello..

I'am sort of new on ubuntu...hardy heron 8.04

My problem is:

I want to create 2 frame buffer devices on my ubuntu in /dev/. --> /dev/fb0 and /dev/fb1
I did changes in grub & by default system is creating /dev/fb0 in /dev, now how can I create /dev/fb1 ?
Actually fb1 is present in /dev/.static/dev/fb1 but how can I make it available in /dev.

I did tried running mknod command (mknod /dev/fb1 c 29 32) , it created fb1 in /dev but then how to point it meaningfully to video driver.

Any help is g8ly appreciated.

~Nish

---

