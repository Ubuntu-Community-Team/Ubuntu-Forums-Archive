---
title: "Enabling restricted nvidia drivers (i.e. 173, 177 or 180)"
date: 2009-03-23
forum: Mythbuntu
---

### Post by davidstoll on 2009-03-23
I have just reinstalled MythBuntu because I had so many strange things going on.  Well, I can't seem to get nvidia 180 drivers installed.  How do I get them to show up in the restricted drivers list?  I've tried apt-get install nvidia-glx-180, but they aren't found.

I am running 8.04 because if I try to install 8.10 from scratch (from a CD), the drivers to get basic video to my monitor doesn't work.  So, something broke between 8.04 and 8.10 with my Nvidia 8500.

Thanks for any help you can give me.  :)

---

### Post by davidstoll on 2009-03-23
By the way, right now, in the restricted drivers window, it says...
"NVIDIA accelerated graphics driver (latest cards)"
and it is enabled.

I believe it is 169, but it doesn't say it directly.  Before, it specifically listed 173, 177 and 180.  How do I get those to show up?

Thanks!

---

### Post by utar on 2009-03-23
You can check which version you are running via the Nvidia control panel.

---

### Post by davidstoll on 2009-03-23
> **utar said:**
> You can check which version you are running via the Nvidia control panel.

169.12


I tried to download directly from nvidia and run in a shell, but it said I didn't have libc headers for my kernel...or something like that.  I'd prefer to just add it through the normal repository, but I'll take any help I can get.

---

### Post by davidstoll on 2009-03-26
I upgraded to Intrepid Ibex 8.10 and now those drivers show up in my restricted drivers manager.

[http://packages.ubuntu.com/search?keywords=nvidia-glx](http://packages.ubuntu.com/search?keywords=nvidia-glx)

---

