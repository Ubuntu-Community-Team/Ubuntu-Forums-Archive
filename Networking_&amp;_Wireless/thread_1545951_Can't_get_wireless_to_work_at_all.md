---
title: "Can't get wireless to work at all"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by Zozma on 2010-08-04
I've installed Ubuntu 10.04 on a computer.    I can't get the wireless to work. I looked into it, and I believe the problem is that I don't have the right driver to work with the wireless card, but I wasn't able to tell what my wireless card is properly.  And when I got the bcmwl-kernel-source package and installed it, the driver still didn't appear under &quot;hardware drivers&quot;.    Compounding the problem, I can't use any sudo commands for some reason because when it prompts me to enter the sudo password, the keys other than &quot;enter&quot; don't seem to work.  I probably don't have the right information up there. Apologies- I'm clueless.

---

### Post by ajgreeny on 2010-08-04
Let's see what your wireless adapter is and go from there.
Enter ```
lspci
``` in terminal and hit enter, then copy the output back here and we may be able to help you more.

It may also be worth using a cable ethernet to update your system if you can do that, then trying the  **System -> Administration  ->Hardware Drivers** again

---

