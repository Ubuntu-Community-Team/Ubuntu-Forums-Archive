---
title: "VERY Specific Wifi Boundaries With New Driver/Kernel"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by snowman4839 on 2009-09-21
I just installed madwifi trunk and kernel 2.6.31 on 9.04 and, for the first time, wifi actually works consistently. But there is a hitch... On the XP half of my dual-boot, I can get on the internet and as I move further away from the router, the signal degrades along with speed and that is all fine and dandy but with linux... I don't understand because at about half the distance of the longest distance XP will operate at, I will either get 400KBps and then move a foot away from the router and then get 0KBps. I don't understand why the range is so much more limited than on linux and why there is a specific boundary. It also does not work as I change floors (go upstairs) whereas XP would work. Does this have to do with signal strength data rate tolerances or something like that? Any ideas on how to remedy this?

---

### Post by falconindy on 2009-09-21
While you were setting options in the kernel config, did you get a chance to set Minstrel as the default rate control algorithm?

Out of curiosity, did you get your kernel from the Karmic kernel repo? Or from kernel.org? I've been looking into compiling the Karmic kernel for myself on 9.04, but I hit some snags and ran out of time...

---

### Post by snowman4839 on 2009-09-21
> **falconindy said:**
> While you were setting options in the kernel config, did you get a chance to set Minstrel as the default rate control algorithm?

Out of curiosity, did you get your kernel from the Karmic kernel repo? Or from kernel.org? I've been looking into compiling the Karmic kernel for myself on 9.04, but I hit some snags and ran out of time...

No I pretty much just went with all of the default settings so I'm not sure about Minstel. Is there a way I can check that?

I got mine from Kernel.org. I didn't check the Karmic repo and Jaunty is like 0.0.3 versions behind the current kernel. [http://easylinuxcds.com/blog/?p=3244](http://easylinuxcds.com/blog/?p=3244) is a fantastic guide on how to build and install the kernel.

---

### Post by snowman4839 on 2009-09-21
I just read around for a sec and Minstrel appears to be what I need. Like I said before is there a way to check if this is already enabled and how would I go about replacing it? or would I have to rebuild the entire kernel?

---

### Post by snowman4839 on 2009-09-22
Ok now I have it narrowed down to the ath_rate_minstrel module and the ath_rate_sample module. I can start the minstrel module but I don't know how to stop the sample module and make it auto-start the minstrel module

---

