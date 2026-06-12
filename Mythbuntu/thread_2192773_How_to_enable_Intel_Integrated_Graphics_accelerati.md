---
title: "How to enable Intel Integrated Graphics acceleration for Myth?"
date: 2013-12-09
forum: Mythbuntu
---

### Post by scstanton1337 on 2013-12-09
I'm running Myth 0.27 with two different front ends that use Intel Integrated Graphics for the video hardware.  With the base Mythbuntu install, only the "Normal" profile with software-based rendering works.  Selecting VAAPI or OpenGL as the rendering methods lead to various errors or stuttering.  My question is, is there an appropriate way to set up Mythbuntu to utilize the Intel drivers for hardware acceleration?  I can give more detail on what my errors are if needed, but I'm hoping for some more specific guidance if this is a known issue that takes certain steps to resolve.  Thanks!

P.S. vainfo shows the Intel i965 driver being loaded, so I don't think it's a package issue.  Possibly dependencies or X/Myth configuration?

---

### Post by aelfric55 on 2013-12-10
It still may be a package issue. The myth VAAPI page lists 4 specialized packages (libva1, i965-va-driver, libva-intel-vaapi-driver, vainfo), one or more of which your plain-vanilla installation may be lacking. See [http://www.mythtv.org/wiki/VAAPI](http://www.mythtv.org/wiki/VAAPI) also for configuration info.

---

### Post by scstanton1337 on 2013-12-10
I seem to have read just about every Wiki page, mailing list post, etc. regarding video drivers and what packages need to be installed.  The ones you mention are present.

My thinking is that with the Intel chipset, using VAAPI is the proper way to leverage hardware acceleration.  However configuring the OpenGL/Auto painter and using the VAAPI settings for video rendering just lead to a black screen and locked up mythfrontend when I try to use it.  I see lots of other posts where that happens to others as well and no clear explanation of how to fix it.  Are the Mythbuntu devs not aware that this is a problem?  Or are they lacking info on how to debug and fix the issue?

---

### Post by aelfric55 on 2013-12-11
You're right. There appear to have been problems with VAAPI and Intel graphics off and on all the way back to Myth 0.25. Whether it's a driver issue with the Intel drivers or a Mythfrontend issue is unclear (so you might want to report your issues also to the mythtv devs over at gossamer-threads, if you haven't done so).

I don't use VAAPI, but I began to have other unresolvable issues with Intel video drivers and mythfrontend beginning with the 3.x.x kernels, and so kept my one intel video myth frontend on 2.6.38.x kernels for as long as I used it. Which worked fine. So in these situations I tend to suspect the Intel video drivers.

Good luck.

---

### Post by topcat5 on 2013-12-27
If you have the room in your system, it's really worth it to stick a $45 Nvidia card in it.  VDPAU on these cards is quite flawless and won't give you any issues.

---

