---
title: "sh nvidia-173 issues..."
date: 2008-09-19
forum: Multimedia Software
---

### Post by vec on 2008-09-19
So... The drivers that were being used, 169 by the restricted drivers was working fine, however minor issues occur... such as can't drop into command line. (Weird lines and stuff are the only thing I see). Also get this problem with rebooting. Not a huge deal. However my real problem is when earlier today I felt risky and tried to install the 173 drivers straight from the nvidia site. I just did sh nvidia****.run and let it do its thing. However, now when I boot into ubuntu, it drops me straight to a command line... startx just says stopping on signal 11 and it tells me it failed to connect to an x server. I want to just go back to using the 169 drivers, but this seems to be impossible. How do I undo the sh command or restore my system back to this morning before I did this?

---

### Post by cariboo on 2008-09-19
There are a lot of howtos concerning installing the nvidia drivers. A quick search using google and you could have found the correct way of doing it. That being said, now that X won't start, it is a good time to install the drivers. First remove all previously install nvidia drivers, make sure you are using the open source nv driver, then run the nvidia script. This should compile and install the modules. Then you can reboot and things should work as you expect them to.

Jim

---

