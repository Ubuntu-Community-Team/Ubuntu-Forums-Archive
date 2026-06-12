---
title: "Intel video card, wrong default aspect ratio"
date: 2008-11-15
forum: Multimedia Software
---

### Post by Tobyb on 2008-11-15
Original problem posted: I did a fresh 8.10 install on a Sony desktop running an Intel graphics card, where Ubuntu 7.x and PCLinuxOS have installed no problem, but now on 8.10 while it installs okay I have 1152x864 (4:3) as the default resolution and while I can switch to 1280x1024 the aspect ratio is wrong at 5:4, which leaves a black space. I noticed the xorg config file seems blank, some text but no settings. Is there an Intel video configuration tool similar to the Nvidia settings tool?

Resolved: I installed via a KVM video switch. I re-installed with a direct monitor connection and it's fine. And I was wrong, the correct aspect is 5:4 for 1280.

---

