---
title: "after I upgraded, I lost sound!"
date: 2008-06-30
forum: Multimedia Software
---

### Post by endtheembargo on 2008-06-30
I upgraded from feisty fawn to ubuntu version 8.04, and everything is great except that I no longer have sound. What should I do?

---

### Post by xc3RnbFO8P on 2008-06-30
What are the specifications of your computer?

---

### Post by endtheembargo on 2008-06-30
I have a toshiba satellite A135

---

### Post by xc3RnbFO8P on 2008-06-30
If you can start the old kernel (Feisty)
and look into /etc/modules,
then compare it with the new in Hardy.

---

### Post by endtheembargo on 2008-06-30
I'm sorry, but I'm VERY new to linux, and not even the most experienced computer user.. could you break that down into steps for me?

---

### Post by xc3RnbFO8P on 2008-06-30
When you restart you get option 
first line: kernel 2.6.2......
next line:  kernel 2.6.2...... fail save
line no. 3 should be Feisty old kernel 
use arrow key to get there <return>
In Terminal (you will find it in Application> Accessories)
copy/paste into Terminal:
> gedit /etc/modules  
<return>
you will see something like this:
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
??????? 
Show the output here.

---

