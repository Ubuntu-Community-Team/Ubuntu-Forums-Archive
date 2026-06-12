---
title: "Need to install NVIDIA drivers after every boot"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by Anagonda on 2007-07-12
Ok, first, I tried to search.

This didn't help:
[http://ubuntuforums.org/showthread.php?t=290790](http://ubuntuforums.org/showthread.php?t=290790)  -because it was allready like this.
Neither this:
[http://ubuntuforums.org/showthread.php?t=276745](http://ubuntuforums.org/showthread.php?t=276745)

So what's the problem? After every boot of the system or every time I restart gdm I need to install nvidia drivers again.
It wasn't a big deal when I was living in last apartment because I restarted my machine every 2 months. But now I have moved to a new place and have had many hardware problems. So about 2 boots(/gdm restarts) each day for a week now.

And it won't work if I try to install the drivers (nvidia-kernel-common) from apt. I need to install them from a package that I downloaded from nvidias site.

Now I'm running 2.6.22-7-generic(gutsy you now), but this same problem was with feisty..

Any help?

---

### Post by thespinesplitter on 2007-07-12
try removing nv from the disabled modules file and restarting your Xserver with CRTL+ALT+Backspace next time this happens in any case, i hope your uninstalling before trying to reinstall.
it sounds to me like there may be two clashing installations but i dont know much about Nvidia drivers i run an ATI card

---

