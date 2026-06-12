---
title: "Recompiling drivers"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-06-14
I would like to change the function of the keys on my remote for my saa7134 tv card.  I downloaded the source code and I believe I have found what I need to change, in the file:

usr/src/linux-source-2.6.17/drivers/media/common/ir-keymaps.c

but I don't know how to compile the drivers and apply them to my system.  I'm pretty experienced with programming, but I've never tried to compile drivers like this.  Any help would be much appreciated.

---

### Post by 5-HT on 2007-06-15
Hi,

You can make your changes to the module source and then compile that module alone (requires creating/copying then editing a makefile) for use with your kernel.
I had a great reference with a detailed walkthrough, but unfortunately cannot remember the link (found it with a google search; was a great guide on kernel hacking/compilation). 

Here are a few sources that should let you do what you want (only need to follow one. Depending on which one you follow, you may not even need to have the full kernel source available):
[http://www.faqs.org/docs/kernel/x204.html](http://www.faqs.org/docs/kernel/x204.html)
[http://www.captain.at/programming/kernel-2.6/](http://www.captain.at/programming/kernel-2.6/)
[http://tldp.org/LDP/lkmpg/2.6/html/x181.html](http://tldp.org/LDP/lkmpg/2.6/html/x181.html)
[http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html)
[http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html)

Hope you get it working!

---

### Post by josesanders on 2007-06-15
The last on is the one that seemed to make sense to me, so that is what I tried.  By adding some stuff to the existing makefile, it built the module ir-common.ko without any errors.  I'll try inserting it in my kernel when I get home.

Thanks for your help

---

