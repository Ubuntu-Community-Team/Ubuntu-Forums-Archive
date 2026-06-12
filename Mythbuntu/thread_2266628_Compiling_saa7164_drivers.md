---
title: "Compiling saa7164 drivers"
date: 2015-02-24
forum: Mythbuntu
---

### Post by sylvester3 on 2015-02-24
I am trying to compile a kernel module saa7164 for current Mythbuntu (3.13) Kernel. I'm hoping someone can shed some light on this.dmesg output (see attachment).This is how I compiled:sudo apt-get install gitsudo apt-get install libproc-processtable-perlmkdir media_buildcd media_buildgit clone git://linuxtv.org/media_build.gitcd media_buildgit clone --depth=1 [https://github.com/trsqr/media_tree.git](https://github.com/trsqr/media_tree.git) -b hvr2205 ./media./buildWait 30mins to complete. I did not run make install, just copied the result .ko file over the existing one.sudo rmmod saa7164, then modprobe saa7164 gave the output shown.Sorry about the line breaks, it appears my browser is doing something funny with them which is why the post was kept brief.

---

### Post by aelfric55 on 2015-02-24
You may want to run depmod.

---

### Post by sylvester3 on 2015-02-24
> **aelfric55 said:**
> You may want to run depmod.Care to elaborate? Do I run sudo depmod -a after install and before modprobe?Will that resolve X disagrees about version of symbol Y and Unknown symbol for X (err -22)It's my first time compiling a kernel module. It's taken me 3 days to get this far.

---

### Post by aelfric55 on 2015-02-24
> **sylvester3 said:**
> Care to elaborate? Do I run sudo depmod -a after install and before modprobe?Will that resolve X disagrees about version of symbol Y and Unknown symbol for X (err -22)It's my first time compiling a kernel module. It's taken me 3 days to get this far.

Checking man depmod would have taken less time than writing the question. You've added a new kernel module, more recent than the active modules.dep. After adding a new module, you normally need to run "sudo depmod" (defaults are fine) to fix the changed module dependencies and mapping. Then you should be ready for modprobe.

---

### Post by sylvester3 on 2015-02-25
Thank you so much for your help!

I ran across a thread [http://forums.gentoo.org/viewtopic-p-5782952.html?sid=fb29022aec95d3bbe7642ec5d091c428](http://forums.gentoo.org/viewtopic-p-5782952.html?sid=fb29022aec95d3bbe7642ec5d091c428) which almost had me ready to recompile my kernel, your tip saved me days/weeks of frustration. In the end I probably would have given up.

I was trying your suggestion to run depmod, rebooting, unloading / loading etc, but kept getting the same error. Then it dawned on me - the module has all these dependencies. By not running make install I was shooting myself in the foot.

For the benefit of others, this is how I got it to work:

following on from steps in initial post ...
sudo make rmmod
sudo make install

then modprobe, etc as usual, /dev/dvb becomes available, dmesg shows everything is happening. I guess the lesson learned is don't be creative, have faith in the developers, try everything

tuning is still not working, but that is for another day. Thank you [COLOR=#000000]aelfric!![/COLOR]

---

