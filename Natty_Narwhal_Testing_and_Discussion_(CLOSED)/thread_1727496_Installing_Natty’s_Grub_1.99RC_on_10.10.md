---
title: "Installing Natty’s Grub 1.99RC on 10.10?"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Hedgehog1 on 2011-04-12
11.04 has become stable enough that I have moved my Natty testing install from an isolated PC to a partition on my primary (and much faster) PC.  This has yielded a very workable triple boot using Natty’s Grub 1.99RC.

In particular, I like that the extra kernels for both 10.10 and 11.04 are placed in a secondary menu that says ‘Additional Kernels’, making it all easier to read and less cluttered looking.

**Does anyone see any issue with doing a ‘grub purge’ on the 10.10 partition, and then installing Grub 1.99RC from the Natty LiveUSB on the 10.10 partition?**

Until Vbox is ready for Natty, I cannot make the jump so I don’t expect to migrate to it for a little while yet, but I would like the cleaner Grub 1.99RC.

***The Hedge***

:KS

---

### Post by drs305 on 2011-04-12
I have done it on one of my previous releases without issue. I did it a bit differently - I just changed the sources.list temporarily to Natty and then specifically installed only grub-common and grub-pc (1.99).  **Added: See Harry33's post below. You probably have to install grub-gfxpayload-lists as well.**

The only drawback for me was that since I returned sources.list to it's original state I don't get any G 1.99 updates. Since 1.99 is now at 1.99RC, it's not a major factor.

---

### Post by Harry33 on 2011-04-13
The latest grub2 version 1.99~rc1-12ubuntu1 depends (for the first time) on the package grub-gfxpayload-lists.
This is done to overcome the gfx boot errors on graphics cards that only work with booting in text mode.

---

