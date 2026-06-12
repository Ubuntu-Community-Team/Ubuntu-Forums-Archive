---
title: "ATI Radeon 6850 Drivers?"
date: 2011-03-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Cam! on 2011-03-18
There was a pretty significant XORG/XServer update today, and I was wondering if I was able to properly install drivers for my ATI Radeon HD 6850 graphics card.

Currently, the full screen resolution, animations/shadowing, etc. is enabled, but I can't enable/install proprietary drivers.

---

### Post by Harry33 on 2011-03-19
> **Cam! said:**
> There was a pretty significant XORG/XServer update today, and I was wondering if I was able to properly install drivers for my ATI Radeon HD 6850 graphics card.

Currently, the full screen resolution, animations/shadowing, etc. is enabled, but I can't enable/install proprietary drivers.

Like so many times in a number of threads here is said:
The fglrx (ATI porprietary drivers) do not support new xserver 1.10.

You can only use open source drivers:
xserver-xorg-video-ati

---

### Post by Cam! on 2011-03-19
If I install them, will they work with my card?

---

### Post by Harry33 on 2011-03-19
> **Cam! said:**
> If I install them, will they work with my card?

Well that is the only thing you can try.
If this high-end ATI does not work with that one, there is a bit newer git version in xorg-edgers PPA.

---

