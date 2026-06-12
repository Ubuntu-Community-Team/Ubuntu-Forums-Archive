---
title: "1080p desktop/screen not centered"
date: 2009-06-29
forum: Multimedia Software
---

### Post by qaskari on 2009-06-29
Hi,
 
I am running Ubuntu 9.04 completely upto-date. I have an ATI X1800 card that I am running on 1920 x 1080 resolution on a SHARP AQUOS 1080p LCD TV. I have not installed any proprietary drivers.
 
The problem I am having is that the screen/desktop is not centered. The display is shifted to the right. The shift is enough to hide the "restore down" and "close" buttons on the top right of a maximised window. I can still see the minimize button. I can also click things that are off the screen by estimating where they might be.
 
I downloaded the Linux driver/catalyst from ATI for my card but could not install it. I received an error which was something like "unsupported version in policy".
 
Any ideas of how I can shift/centre the screen? Is there a pixel offset line I can enter in config or something? Any help would be appreciated.
 
Thanks in advance.

---

### Post by qaskari on 2009-06-29
anyone able to help with this? Thanks.

---

### Post by qaskari on 2009-06-30
ok so I have found out this much that I cannot use proprietary ati driver for the X1800 if I am using Jaunty and I should use radionhd instead. The problem with the uncentered screen still exists though. Can I create modelines for radionhd? There was a post I saw somewhere that showed what to do to fix uncentered screen with an nvidia card and it involved creating modelines while telling the OS to not ask the monitor for its specs and let xorg.conf override and determine Hz vsync etc. Is that code common for all cards?

---

