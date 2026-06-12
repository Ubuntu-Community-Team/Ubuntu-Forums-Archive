---
title: "ATI Radeon Mobility 7500 (agp failed to initialize?)"
date: 2005-12-16
forum: Multimedia &amp; Video
---

### Post by kpturvey on 2005-12-16
I can't seem to get DRI (direct rendering) to work with my Inspiron 5100 laptop.  It has a Radeon Mobility 7500 in it and I know that others have gotten it to work.  The problem seems to be with the AGP bus.  I'm getting the following error in Xorg.0.log

(WW) RADEON(0): [agp] AGP not available
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module.
(II) RADEON(0): [drm] removed 1 reserved context for kernel

Now, I've already made sure that agpgart is loading early and it seems to be detecting the intel chipset used by the agp bus.  So I'm at a bit of a loss on how to handle this?  Any ideas?

Thanks.

---

### Post by kpturvey on 2005-12-17
I figured this out.  There are four modules that need to be loaded and they need to be loaded in a specific order (for my setup).  Two of them are needed to get the AGP bus to work.  The first is agpgart and the second is intel_agp (this one may be different for your setup, it depends on the PCI->AGP bridge chipset you are using).  They both must be loaded before the radeon and radeonfb modules.  So I put this in my /etc/modules file:

intel_agp
agpgart
radeon
radeonfb

Now everything works great.  I should note that everything works great even with 24 bit color.  I read somewhere on the web that it wouldn't work unless I dropped the colors down to 16 bits.  This is erroneous.  

Good luck.

(This configuration is for my Dell Inspiron 5100)

---

