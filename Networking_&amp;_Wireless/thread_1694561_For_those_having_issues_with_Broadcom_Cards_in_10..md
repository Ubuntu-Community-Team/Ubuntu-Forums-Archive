---
title: "For those having issues with Broadcom Cards in 10.04 with Kernel 2.6.38, try this."
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by TuxIsAwesome on 2011-02-24
I thought this thread might be useful for those who are using Kernel 2.6.38 (Backported from Natty Narwhal) in Lucid Lynx, and cant get the Broadcom STA wireless driver to install. These instructions should also work for 2.6.36 and 2.6.37 as well.

Anyway, I could not get the Broadcom STA Drivers to work with Lucid Lynx running kernel 2.6.38, they just would refuse to install. Trying to reinstall bcmwl-kernel-source through Synaptic did not work either.

I then tried my luck and installed the same packages but for Natty in Lucid Lynx, when prompted that an older version was available in a software channel, I disregarded it and installed the Natty ones anyway (Seems they have no dependency issues). en 

I then went to the Hardware Drivers tab after they were done installing and it said that the Broadcom STA driver was installed but wasn't in use. I was not prompted to restart my computer at all, but I figured I needed to do that anyway.

So, I restarted, and booted back into Xubuntu, and low and behold, my Wireless was working.

My machine uses a Broadcom bcm4328 wireless a/b/g/n card, however to the best of my knowlege this procedure and these packages should work for any card that uses the Broadcom STA drivers.

Here are the packages, 

32-Bit [http://launchpadlibrarian.net/62008128/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu2_i386.deb](http://launchpadlibrarian.net/62008128/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu2_i386.deb)

64-Bit [http://launchpadlibrarian.net/62008106/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu2_amd64.deb](http://launchpadlibrarian.net/62008106/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu2_amd64.deb)

---

