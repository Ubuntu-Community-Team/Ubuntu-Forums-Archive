---
title: "Poor EPG performance"
date: 2009-05-11
forum: Mythbuntu
---

### Post by bruk on 2009-05-11
I've recently done a clean install of 9.04 to replace my previous functional, but somewhat doddering, 8.04 install. After doing all the necessary fix up work for this clean install, I've now got my box working better than ever, except for the EPG.

There are a couple of threads dotted around mentioning poor performance in the EPG, but either seem restricted to old versions of myth or just during live tv. The actual slowness is, I'm fairly confident, a performance issue, as if I do a complete scroll of the channels (top to bottom) the browse speed will be back to what it used to be.

I imagine there are two possibilities, there's a bug in the latest myth epg(caching not turned on when it should be, or it's disabled because of said bug), or the more likely possibility, that on my previous system I'd tweaked some kind of performance value (in MySQL) that magically pre-caches all of the epg data to avoid the per channel view read operations.

Any ideas folks?

---

### Post by mathog on 2009-05-11
> **bruk said:**
> 
Any ideas folks?

Were you running VDPAU before, and not now?  On my system the EPG is unusable unless VDPAU is used.

---

### Post by bruk on 2009-05-12
> **mathog said:**
> Were you running VDPAU before, and not now?  On my system the EPG is unusable unless VDPAU is used.

Thanks for the suggestion, but after going and finding out what VDPAU actually is, my graphics card, a 7600 GS, isn't listed in the compatible devices. So I guess I wasn't using it previously, and I'm not using it currently.

But as I said, the only actual slowness is caused by looking at a channel that hasn't already been looked at, once they've all been looked at once, the speed is as it should be. It's also worth mentioning that browsing forwards in time on a channel isn't affected by this slowdown.

---

