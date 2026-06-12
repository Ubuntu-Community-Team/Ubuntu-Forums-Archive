---
title: "HTPC graphics"
date: 2010-03-27
forum: Multimedia Software
---

### Post by kens8 on 2010-03-27
I'm planning on converting an old PC into a Mythbuntu box.  It's got an AMD Athlon 3200+, 2GB RAM, and a Geforce 6600LE graphics card.  I'm going to be hooking it up to a Hanns·G HH-281HPB 28-inch LCD monitor, which has a resolution of 1920x1200.  The 6600LE only scales up to 1080i, and sometimes struggles with 720p, so I'm looking to upgrade the video card on the cheap.  This will be strictly a HTPC and won't be used for gaming.  I'm looking at Geforce 210, Geforce 8500GT, and Geforce 9500GT.  There's a lot to recommend the 210, but it appears that there are quite a few people having issues getting it up and running in Ubuntu.  Does anyone have any suggestions for graphics cards, preferably in the sub-$50 range?  Thanks

---

### Post by efflandt on 2010-03-28
I cannot recommend a video card.  I am using ATI Radeon X1300 AGP with DVI to HDMI cable and default X modules, which AMD now considers legacy.

But I was just curious if your 3200+ is the earlier version (2 GHz 1024K cache) or later version (2.2 GHz 512K cache)?  Mine is the earlier version (circa 2004), so it lacks the lahf_lm instruction used by real 64-bit flash, and I had to use the flashplugin-lahf-fix that someone posted on these forums.  But some time ago Hulu broke 64-bit flash in a browser and Hulu Desktop is unaware of flashplugin-lahf-fix, so I reverted to flashplugin-installer (32-bit flash with nswrapper).

Hulu is a bit slow blown up to 1080p full screen, so I switch to 720p when using that.  But the source is 480p anyway, except some movies at 720p.  I have a separate BluRay player for streaming Netflix HD (which I hear does not work in Linux at this time anyway).

---

