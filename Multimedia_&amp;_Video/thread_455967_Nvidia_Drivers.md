---
title: "Nvidia Drivers"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by ksudbury on 2007-05-27
For best results should I install the restricted driver in ubuntu or use the Nvidia driver? 

I have tried the Ubuntu restricted at the moment  and get around 2000 fps in glxgears, I know the card is no show stopper but is this the best I can expect? my old 9800 pro will do around 3500 and that card is 4 years old. 

I have a NVIDIA GeForce 6150 128mb 


Many thanks

---

### Post by heldal on 2007-05-27
> **K31TH said:**
> For best results should I install the restricted driver in ubuntu or use the Nvidia driver? 


Usually that doesn't matter so much unless you've got the very latest hardware (in which case you may even have to use a beta-driver from nvidia to make it work). Each new distribution (ubuntu as any other) tend to incorporate the latest official driver distributed by nvidia at the time of release.

It is important to remember to link a new kernel module each time the kernel is updated If you choose to install the original Nvidia-driver. The ubuntu-packaged-version OTOH is handled with upgrades through package dependencies.

PS! 8800GTX/GTX owners should note that the current version of the driver distributed with ubuntu (nvidia-glx-new version 1.0.9755+2.6.20.5-16.28) is missing an extension to the xserver (libwfb.so) that is necessary to make the driver work with these recent GPUs.

---

### Post by _simon_ on 2007-05-27
Are you running Beryl or Compiz? If so, turn them off and try again.

Just to put things in perspective, my 7900GS KO 256MB (PCI-E)  gives on average 16484 FPS

---

### Post by Error1312 on 2007-05-27
I have the best results with the drivers downloaded from the NVIDIA site. 

My Geforce 7300 Go also gives about 2000 fps, but I notice little or no difference between it's performance in games on windows and linux, so it isn't a problem for me.

---

