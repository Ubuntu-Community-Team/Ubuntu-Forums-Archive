---
title: "Radeon 9250.. nothing works"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by akira666 on 2006-10-09
I have followed countless guides/forum posts/etc in regards to this issue and I end up with the same result every time. I'm just hoping someone has seen it before and knows whats up. It may be relevant that this system was initially set up with an nvidia card, and I am now trying to install an ATI card.

The card is a Gigabyte Radeon 9250 with 128 megs of ram. No matter what guide I follow in regards to setting up an ATI card I end up with one of two results:

1) When  i run glxinfo it spits out the MESA business and says direct rendering is not enabled, anything that is 3d at all, even simple screen savers chugs along hopelessly

2) When I run glxinfo it spits out a whole whackload of API errors, anything that would be in 3d just displays a blank white screen.

Any ideas as to what might fix this?

Thanks in advance.
-Tom

---

### Post by colo on 2006-10-09
Well, seems like your Nvidia-Install installed Nvidia's own OpenGL-libs, just as it's supposed to do. Unfortunately, I don't know how to switch OpenGL-interfaces on Ubuntu, but maybe getting rid of every package you've installed containing "nvidia" (use the --purge option for apt*), and reinstalling MESA does the trick.

You might want to have a look at my xorg.conf which is powering the Radeon 8500 in here just fine, too: [http://gnulords.org/~colo/tmp/xorg.conf.r2XX](http://gnulords.org/~colo/tmp/xorg.conf.r2XX)

---

