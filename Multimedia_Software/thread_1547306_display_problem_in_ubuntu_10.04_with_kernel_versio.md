---
title: "display problem in ubuntu 10.04 with kernel version 2.6.32-24.38"
date: 2010-08-06
forum: Multimedia Software
---

### Post by Prateek Fulzele on 2010-08-06
My Dell XPS 400 is running Lucid Lynx 10.04 with the ubuntu kernel 
version 2.6.32-24.38 (mainline kernel version 2.6.32.15+drm33.5). Since
moving to the latest 10.04, I was having problem with my ATI Radion Card:

1. frozen screen after startup [but goes away after doing ctrl-alt-f1]
2. try switching users in the GNOME would spill garbage on the screen 
   and hang the screen [need to do the same trick as in #1]
 
The ubuntu release notes does mention about the issues with the certain 
video cards and I guess my video card would be one of them. That's because
since adding the fix/hack, I was able to get things working. But it came 
with added cost: slow window refresh and scroll.

I was wondering if any of you knows about the final fix and when that will
be available or hack in certain xorg config to get it working in the current
kernel.

My video card:
$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60]

Thanks a lot.

---

