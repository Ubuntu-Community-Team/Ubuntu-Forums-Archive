---
title: "fglrx broken with 2.6.24.19-rt kernel?"
date: 2008-09-10
forum: Multimedia Software
---

### Post by bwanab on 2008-09-10
I've noticed that the latest rt kernel 2.6.24.19-rt doesn't seem to have been built with the necessary's to support fglrx for the proprietary nvidia driver. Since I've been running this regularly on every kernel prior to 2.6.24.19, I don't think it's a configuration problem with my setup. The generic kernel still works fine and the rt kernel works fine if I remove the glx/nvidia specific stuff from xorg.conf.

Is this a bug in 2.6.24.19-rt or is this a shift in policy? I ask because if it's a bug, I can wait for the fix and just manually ensure that I'm using the right xorg.conf when I boot into rt, but if it's a shift in policy such that fglrx won't be supported in rt mode from now on, I'll want to put in some code that automatically picks the right xorg.conf at boot time.

---

