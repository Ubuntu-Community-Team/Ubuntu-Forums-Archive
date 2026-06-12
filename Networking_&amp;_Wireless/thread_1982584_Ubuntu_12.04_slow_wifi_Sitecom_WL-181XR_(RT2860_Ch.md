---
title: "Ubuntu 12.04 slow wifi Sitecom WL-181XR (RT2860 Chipset)"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by DFKT on 2012-05-18
After upgrading to Ubuntu 12.04 my wifi turned out to be terribly slow. I spent quite some time trying to figure out what was wrong. Mind you, I'm a complete Linux n00b.

As it turned out, for my wifi card, only the rt2800 drivers had been installed, while according to the ubuntu hardware wiki, my WL-181XR is actually a RT2860 chipset?

So, I manually installed the drivers using the step-by-step from [ this post]("http:// http://ubuntuforums.org/showpost.php?p=9255730&postcount=1"). Then I disabled the rt2800 drivers using the input from [this post]("http:// http://ubuntuforums.org/showpost.php?p=11001329&postcount=5").

After a reboot, I now get a nice 40Mbps downstream, where with the Rt2800 drivers it was a minimal 2Mbps.

Hope this perhaps helps others as well... Of course, input is always welcome (e.g. when I actually did something really stupid, which I'm not yet aware of, lol)

---

### Post by jackdale on 2012-05-29
Thanks DFKT!  You are a great example to the community.

I had a bit of trouble following the links, so here they are again just in case:

[http://ubuntuforums.org/showpost.php?p=9255730]("http://ubuntuforums.org/showpost.php?p=9255730")

and

[http://ubuntuforums.org/showpost.php?p=11001329]("http://ubuntuforums.org/showpost.php?p=11001329")

---

