---
title: "xdpyinfo reporting wrong resolution for xinerama after upgrading to 6.10"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by wjbaird on 2006-12-13
Hey all,

Under 6.06 I had a perfectly functioning xinerama configuration - I have a dell d410 laptop (with intel i915 graphics), and I use the internal laptop monitor at 1024x768, and an external 19" CRT at 1600x1200 arranged side by side.  I know that under 6.06 xdpyinfo reported the expected resolution of 2624x1200, and everything worked fine.

I upgraded to 6.10 on the weekend, and I've been having some strange problems since then - both monitors start up fine, but it seems like the X server is reporting the resolution wrong - xdpyinfo now reports the resolution as 1024x768, even though both monitors are clearly working fine.

This has resulted in two annoying symptoms that I've noticed so far; Metacity won't let me drag windows completely off the internal monitor, and wine programs don't refresh properly if I make the window larger than 1024x768.   

I can work around the metacity issue - I've verified that xfwm4 doesn't exhibit the same problem, but the wine limitation is *much* more annoying - there's a few windows apps for work that I use with cross-over office, and not being able to make full use of my 1600x1200 monitor for them is pretty annoying.

The only change the upgrade process made to my xorg.conf file was to remove the GLcore extension.  I tried adding it back in and it didn't make any difference.

Any suggestions on how to convince X to report the right resolution would be greatly appreciated.

Thanks!

---

