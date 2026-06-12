---
title: "No ATI drivers, but fps of 1200+ ???"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by fapapa on 2006-06-19
Newby. I have an ati radeon 9250 pro (detected as 9200 pro) with 128mb ram. I had hardware accell working a few days ago with the ati prop. drivers. Then I decided to play around with compiz. It is a little flakey on my system, so I decided to remove it. When I tried to remove the installed packages, there were a couple I could not remove (or rather roll back) because of dependencies on gdm and other critical components. Well I've been trying to get hardware accelleration working again ever since by installing ati's driver as well as the package from the repository. I followed every how-to on this and other sites, with no luck. Finally I removed all ati drivers and happened to run glxgears and I got the following:

fabio@methusela:~$ glxgears
6130 frames in 5.0 seconds = 1225.993 FPS
6321 frames in 5.0 seconds = 1264.116 FPS
6308 frames in 5.0 seconds = 1261.438 FPS
6315 frames in 5.0 seconds = 1262.998 FPS
6311 frames in 5.0 seconds = 1262.180 FPS
6317 frames in 5.0 seconds = 1263.265 FPS
6330 frames in 5.0 seconds = 1265.929 FPS
6333 frames in 5.0 seconds = 1266.494 FPS
6314 frames in 5.0 seconds = 1262.787 FPS
6323 frames in 5.0 seconds = 1264.520 FPS
6319 frames in 5.0 seconds = 1263.790 FPS
6306 frames in 5.0 seconds = 1261.086 FPS
6320 frames in 5.0 seconds = 1263.835 FPS
6321 frames in 5.0 seconds = 1264.156 FPS
6330 frames in 5.0 seconds = 1265.891 FPS
6323 frames in 5.0 seconds = 1264.503 FPS
6279 frames in 5.0 seconds = 1255.703 FPS

Is it possible that I have hardware accelleration without the ati driver from their site or from the repos? With the driver installed I was getting fps of around 130!

The version of libgl1-mesa I have is 6.5.1, which is the package I could not roll back after installing compiz. My system is a celleron 2GHz with 512MB ram, if that helps.  Thanks


fabio

---

### Post by kthakore on 2006-06-19
wow if only my card did that!! Talk about a stumble upon.

---

### Post by Hezekiah on 2006-06-19
That's probably the xorg Radeon driver kicking in - it's peak performance isn't as good as the ATI binary driver (at least not from my experience) but it still does reasonably well on many things.

Also, remember that glxgears is a very poor benchmark :-)  That said, those do seem like pretty sweet results from a 92xx card.

---

