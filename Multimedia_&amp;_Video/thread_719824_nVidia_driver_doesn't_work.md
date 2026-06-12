---
title: "nVidia driver doesn't work"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by vze4p6c2 on 2008-03-09
Hey guyes,

I've tried to install the nvidia driver from the nvidia's site and got everything working, however after a restart, X didn't start.  Then I had to back up the xorg.conf file and it worked fine.  The nvidia's xorg config file seems the problem.  However when I bring back the old configuration and try to change nv to nvidia, it failes to work.

Does anyone have any ideas how to fix this?  Maybe there's some apt-get things to do?

thanks in advance,
Vlad

---

### Post by pbcartwright on 2008-03-09
you either need to install envy, and let it install the nvidia driver, or go to nvidia.com and download the latest driver and install it. You will need the kernel headers  for this.. envy is the easiest method OR follow the README with the nvidia.com driver download..

---

### Post by pbcartwright on 2008-03-09
I forgot to add, the ENVY web site is:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

