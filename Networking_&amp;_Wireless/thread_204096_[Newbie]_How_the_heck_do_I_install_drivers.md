---
title: "[Newbie] How the heck do I install drivers?"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by Sabacc on 2006-06-26
Blah blah, newbie to linux/ubuntu -- let's get that out of the way.

I'm running Dapper in a VIA M10000 mobo with the intention of turning it into a mythbox. I'm currently trying to upgrade all of my mobo's on-board capabilities -- LAN, audio/video, and USB. I went to the VIA website and downloaded drivers for non-distribution specific versions of Linux (on the x86 core). I untar'ed the files. I cd into the directories, I try to do make install, and I get 
Makefile:135: *** Linux kernel source not found.  Stop.

I've done some searching and I understand and see that I need kernel files in /usr/src -- but doesn't this only work for custom compiled kernels, not distributions like Ubuntu? If I'm wrong, where do I get the files, because I can't find them in Synaptic. If I'm ultra wrong and I need to download drivers for a specific distro, which one do I get? Because they only offer Fedora and Redhat core files.

Thanks for any help!

---

### Post by bruce89 on 2006-06-26
I don't see why you need specific drivers, but ```
sudo aptitude install build-essential
``` will install compilers.

---

### Post by Sabacc on 2006-06-26
Okay, then -- why wouldn't I? :p

Are you saying that if it works, it works?

---

### Post by GuitarHero on 2006-06-26
Ubuntu comes with all the drivers you should need.

---

### Post by christhemonkey on 2006-06-26
To get the latest version of the ubuntu kernel source:

```
sudo apt-get linux-source 
```


Although, updating the drivers might be a slightly pointless thing to do.
But its your computer i guess!

---

