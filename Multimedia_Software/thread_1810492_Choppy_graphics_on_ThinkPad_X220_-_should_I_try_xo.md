---
title: "Choppy graphics on ThinkPad X220 - should I try xorg-edgers?"
date: 2011-07-23
forum: Multimedia Software
---

### Post by waldo000000 on 2011-07-23
Hi,

I've just installed 11.04 on a ThinkPad X220. I've noticed Google Earth is "choppy", i.e. while flying around, it's nice and smooth for a few seconds, then it will freeze for about 1 second, etc.

I'm presuming it's a driver issue. Have you got any suggestions for further testing/debugging? I've recently heard of the "xorg-edgers" PPA (via Google), but still don't really understand what it is. Should I try installing that? ([http://www.ubuntuupdates.org/ppas/87](http://www.ubuntuupdates.org/ppas/87))

By the way, via lspci, my display card appears to be listed as:
"00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)"

Thanks!
Roy

**Edit 1:** A clue! In /var/log/syslog, the hanging corresponds with entries like these:
> 
Jul 23 12:11:56 ted kernel: [ 7102.834339] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 651435, at 651435], missed IRQ?
Jul 23 12:12:08 ted kernel: [ 7114.762950] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 659142, at 659142], missed IRQ?
Jul 23 12:12:10 ted kernel: [ 7116.844278] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 659425, at 659425], missed IRQ?
Jul 23 12:12:41 ted kernel: [ 7147.660402] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 678335, at 678335], missed IRQ?


**Edit 2:** OK, as far as I can tell I'm experiencing the following bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/794658](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/794658)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065)

Will try enabling the natty-proposed repo...

**Edit 3:** Upgrading packages from natty-proposed fixed the problem! (From the comments in the previous bugs, I suspect the important upgrade was the kernel from version 2.6.38-10 to 2.6.38-11). FWIW, I tried installing packages from "xorg-edgers", but this led to even worse instability (Xorg crashes when opening placemarks in Google Earth). So I "ppa-purge"'ed that, and everything's nice now :) Hope this post can help someone else in future.

Cheers,
Roy

---

