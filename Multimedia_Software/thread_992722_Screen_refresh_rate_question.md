---
title: "Screen refresh rate question"
date: 2008-11-25
forum: Multimedia Software
---

### Post by mjpatey on 2008-11-25
Hi, all-

I've been wracking my brain trying to figure out why my new home-brew computer feels sluggish, and came across the following disparity while sizing things up...  In my Screen Resolution settings, my only refresh rate options at 1440x900 are 50 and 51Hz.  Yet my monitor's OSD reports 1440x900 at 60Hz, regardless of which I choose.  I'm connected to the digital input.

Without enabling the proprietary nVidia driver, I have no access to the monitor's native resolution at all, and the max available resolution is 800x600, I believe.  So it's only by installing the proprietary nVidia driver that I'm getting 1440x900.  But still, my only refresh rate options at that resolution are 50 and 51 HZ.

One of the problems I'm having is a somewhat jerky video response.  Could this be fixed by somehow setting the refresh rate to 60HZ, and if so, how do I go about it?

Thanks for any suggestions you may have!

-Mark

---

### Post by djbushido on 2008-11-25
the jerky response could be your screen, if so I'm not sure on how to fix that. it would probably be something in xorg.conf. as a benchmark, make sure your cpu isn't running too high, because this can also cause problems.

---

