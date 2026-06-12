---
title: "Dual monitors exceed my maximum resolution"
date: 2012-10-22
forum: Multimedia Software
---

### Post by Phasmus on 2012-10-22
I have a 2560x1600 and a 1600x1200 monitor which I would like to arrange side-by side with the 1600x1200 rotated so it acts as a horizontal extension of the larger monitor.  This nearly works, except when I try to use this configuration I get the following error:

"The selected configuration for displays could not be applied

requested position/size for CRTC 144 is outside the allowed limit: position=(2560, 0), size=(1600, 1200), maximum=(4096, 4096)"

Side by side the resolution is 4160, I'm only a few pixels over my limit.  In the configuration I actually want, with the small monitor rotated, I am below the limit (3760 horizontal).  This configuration actually worked with the Nvidia driver and xrandr but my performance with nouveau is much better.  (And newer Nvidia drivers don't allow xrandr and xinerama at the same time)

Do I have any hope?  Is there a way to trick X into giving me another 64 pixels, or to make it detect my 1600x1200 monitor as 1200x1600?

---

### Post by Phasmus on 2012-10-24
Additional info: Currently I am able to configure my smaller desktop below the larger.  Having to navigate between desktops up and down instead of left to right (when the monitors themselves are physically positioned left to right) is surprisingly annoying.

---

### Post by Phasmus on 2012-10-26
Additional additional info: if I reduce the resolution of my smaller monitor the the side-by-side configuration is permitted.  This doesn't look very good though.  

Is there a Linux forum more specifically devoted to Nouveau/gnome-desktop configuration that I ought to check out?

---

