---
title: "Help with Catalyst fglrx-installer"
date: 2009-09-18
forum: Multimedia Software
---

### Post by humphreybc on 2009-09-18
Hi there,

I'm currently running 9.4 Catalyst but want to upgrade to 9.8 as I have heard that the newer linux drivers add better support for HDMI out and dual monitors. I have just bought a Dell 24" monitor and so I'm keen to use it with my laptop in dual monitor mode. I've used HDMI out on my laptop previously with our Sony TV, and although it did appear to work okay, it wasn't completely pain free.

Anyway, I tried to upgrade to 9.8 a while ago and I had a problem, so I reported this bug:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/423711](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/423711)

Then "Bryce Harrington" fixed the bug in the package fglrx-installer, and I saw that this new package was available. But I have been running Update Manager every day for the past two weeks and have never seen this updated, most likely because this new package is going to be released with karmic.

I asked Bryce how I can install the new FIXED version of fglrx-installer on JAUNTY, but he never replied, so I've come here.

Question: How do I install the latest version of [this package]("https://launchpad.net/ubuntu/+source/fglrx-installer") in Ubuntu Jaunty 9.04?

---

### Post by superm1 on 2009-09-22
> **humphreybc said:**
> Hi there,

I'm currently running 9.4 Catalyst but want to upgrade to 9.8 as I have heard that the newer linux drivers add better support for HDMI out and dual monitors. I have just bought a Dell 24" monitor and so I'm keen to use it with my laptop in dual monitor mode. I've used HDMI out on my laptop previously with our Sony TV, and although it did appear to work okay, it wasn't completely pain free.

Anyway, I tried to upgrade to 9.8 a while ago and I had a problem, so I reported this bug:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/423711](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/423711)

Then "Bryce Harrington" fixed the bug in the package fglrx-installer, and I saw that this new package was available. But I have been running Update Manager every day for the past two weeks and have never seen this updated, most likely because this new package is going to be released with karmic.

I asked Bryce how I can install the new FIXED version of fglrx-installer on JAUNTY, but he never replied, so I've come here.

Question: How do I install the latest version of [this package]("https://launchpad.net/ubuntu/+source/fglrx-installer") in Ubuntu Jaunty 9.04?
Bryce is away on paternity leave for a bit.  You're best bet is to grab the source package from Karmic (dsc,diff.gz,orig.tar.gz) and built it on jaunty and install those binary debs.

---

### Post by humphreybc on 2009-09-22
That's cool, I think that I need a whole heap of other karmic packages to get the newer drivers working, so it looks like i'm stuck with 9.4 till the official release of karmic. Thanks

---

