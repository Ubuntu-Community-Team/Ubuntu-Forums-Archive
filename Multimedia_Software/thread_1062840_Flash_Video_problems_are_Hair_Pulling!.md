---
title: "Flash Video problems are Hair Pulling!"
date: 2009-02-07
forum: Multimedia Software
---

### Post by celem on 2009-02-07
Can anybody play the video at the link, just below, smoothly and correctly. i.e. without the flickering lines that I see?
[http://tinyurl.com/2hbl25](http://tinyurl.com/2hbl25)

After years of dual-booting, I switched to 100% Linux a few months ago. However, problems with video, mostly, but not entirely flash based may force me back to Windows, unless I can find a cure. I have tried all of the hints in the sticky of this help section, plus lots of other's hints, as well, including tweaks to the Compiz settings manager, etc. I have Ubuntu 8.10 on an AMD dual-core machine with 4GB RAM, a 19-inch 1440x600 LCD driven by Nvidia's latest 180.22 driver on a GeForce 8200 graphics card. I have Shockwave Flash 10.0 r15 loaded as well as all of the various non-free packages recommended by the sticky note in the section.

Most flash based video plays haltingly or with tears or flickering lines. [http://www.hulu.com](http://www.hulu.com) plays with pauses and YouTube plays with tears on motion and occasional pauses. I have a 5MB DSL and the videos are fully downloaded very quickly and resident locally. 

Can anyone play videos on Linux as well as they play on Windows?

---

### Post by gandaran on 2009-02-07
no problem here with the link, the flash videos play very well with flash 10
now what package(s) have you installed for flash and is ubuntu 32-bits or 64-bits? ubuntu 8.04 or 8.10?

---

### Post by celem on 2009-02-07
Shockwave Flash 10.0 r15 loaded on 32 bit Ubuntu 8.10

---

### Post by gandaran on 2009-02-07
> **celem said:**
> Shockwave Flash 10.0 r15 loaded on 32 bit Ubuntu 8.10
okay, just in case you have some other flash installed run this command to remove them.
**sudo apt-get purge gnash gnash-common mozilla-plugin-gnash swfdec-mozilla && sudo apt-get update**
if still no go, all I can advise is to disable compiz and try the flash video again.
another useful trick is to right click the flash video window and disable the hardware acceleration option, sometimes it works, if all this won't help you'll have to look what video card driver is installed.

---

