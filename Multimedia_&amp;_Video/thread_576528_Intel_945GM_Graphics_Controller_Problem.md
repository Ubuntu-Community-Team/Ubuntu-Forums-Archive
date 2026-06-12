---
title: "Intel 945GM Graphics Controller Problem"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by jaywalker13 on 2007-10-15
Problems with using an external monitor.

Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller.

Using Feisty.

The best I can do is install xserver-xorg-video-intel (via Synaptic) each time I want to connect my Dell Inspiron 6400 laptop to an external monitor. This results in xserver-xorg-video-i810 being uninstalled. Consequently, the Dell laptop's own screen partly clones the larger external screen, with a lot of things not visible. So I have to reinstall xserver...i810 when I want to use the laptop without the external monitor. This means xserver-xorg-video-intel is uninstalled again.

Even this only works on my Viewsonic VX2235 22 inch screen. A Dell 22 inch external screen that I have to use on another site is more oblong in shape and distorts all the resolution settings. Either the picture is squashed down in lower resolutions or leaves a wide black stripe on the largest setting, with stuff off the screen to the right. No resolutions work right on the Dell external screen.

Anyone have similar issues with Intel 945GM?

Any ideas on what I could try?

Maybe the xorg.conf file needs to be changed?

Jay

---

