---
title: "Experience with nVidia Optimus 319.12 Beta Drivers"
date: 2013-05-05
forum: Multimedia Software
---

### Post by Rhemat on 2013-05-05
Heya All,

  I was wondering if anyone here has any experience with the new proprietary drivers from nVidia, that support their Optimus Technology in Linux.  I'm thinking of installing them when I have a day off, but I've heard that there may be issues (one of which requires the user to have kernel 3.9 or later, or you get a blank screen), and don't want to potentially trash my system.  I wouldn't risk this since I have functional BumbleBee drivers, but they seem to hardly take advantage of the hardware.

  What should an individual know before installing them?  Is the performance good, or is it just energy saving drivers?  Do I have to know which GPU (Intel or nVidia) is handling the laptop's monitor, and if so, how do I find that out?

  Thanks for the information.

---

### Post by Bucky Ball on 2013-05-05
*Thread moved to **Multimedia & Video**.*

---

### Post by nPoc on 2013-05-05
> **Rhemat said:**
> Heya All,

  I was wondering if anyone here has any experience with the new proprietary drivers from nVidia, that support their Optimus Technology in Linux.  I'm thinking of installing them when I have a day off, but I've heard that there may be issues (one of which requires the user to have kernel 3.9 or later, or you get a blank screen), and don't want to potentially trash my system.  I wouldn't risk this since I have functional BumbleBee drivers, but they seem to hardly take advantage of the hardware.

  What should an individual know before installing them?  Is the performance good, or is it just energy saving drivers?  Do I have to know which GPU (Intel or nVidia) is handling the laptop's monitor, and if so, how do I find that out?

  Thanks for the information.

Currently simply installing any nvidia driver (including 319) for me under raring causes X to core, and throw warnings in the Xorg log 
5.118] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

I like you had optimus working great in 12.10.  In fact I had optimus/primus under raring working great up until the GA release.

---

### Post by pogopuschel on 2013-05-09
> **Rhemat said:**
> Heya All,
I was wondering if anyone here has any experience with the new proprietary drivers from nVidia, that support their Optimus Technology in Linux.
Optimus technology is not supported, there is no power saving by switching from integrated to discrete GPU. The 319 driver allows running the whole desktop on the Nvidia GPU, also on muxless machines.

> **Rhemat said:**
> 
  I'm thinking of installing them when I have a day off, but I've heard that there may be issues (one of which requires the user to have kernel 3.9 or later, or you get a blank screen), and don't want to potentially trash my system.  I wouldn't risk this since I have functional BumbleBee drivers,.. 
I strongly recommend to create an extra partition for this, if you want to test.
> **Rhemat said:**
> 
..but they seem to hardly take advantage of the hardware.

Yep, the loss due to bumblebee's 2nd X-Server copying frames around is tremendous. Nvidia 319 is round about 3 times faster than bumblebee.
> **Rhemat said:**
> 
  What should an individual know before installing them?  Is the performance good, or is it just energy saving drivers?  Do I have to know which GPU (Intel or nVidia) is handling the laptop's monitor, and if so, how do I find that out?
Eventually you have to check your Nvidia GPU's PCI device id and edit the xorg.conf. As mentioned, it is much faster than bumblebee, if you are a gamer, check it out. Battery life decreases, nviia GPU always on. There is a little tearing, maybe matters for videos. In our german wiki we already have an [article]("http://wiki.ubuntuusers.de/Baustelle/Nvidia_319.12/Optimus") about 319/optimus. Not so hard to understand/translate I guess.

  greetz, puschel

---

### Post by andrew.46 on 2013-05-11
A quick sidenote: 319.17 has been released...

---

