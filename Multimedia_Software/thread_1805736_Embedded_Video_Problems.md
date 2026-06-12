---
title: "Embedded Video Problems"
date: 2011-07-16
forum: Multimedia Software
---

### Post by bovisrex on 2011-07-16
Hi! I installed 11.04 from 10.04 about two months ago and I have not been able to get embedded video to work. Generally, surfing directly to YouTube will work, but Hulu doesn't, and most embedded video does NOT work at all... I usually get a black box or sometimes a flashing icon in the center. It doesn't make a difference if I use Chromium or Firefox. In addition to loading the plug-ins (and the restricted extras) from Software Center and Synaptec, I've also tried these commands:

sudo add-apt-repository ppa:sevenmachines/flash                                   and
sudo apt-get update && sudo apt-get install flashplugin64-installer

And still no joy. Destop environment (classic vs. Unity) also doesn't make a difference.

Any ideas?

---

### Post by lovinglinux on 2011-07-16
Install [version 2.2.0 of Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/") and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance and fix common issues.

Also see [YouTube Problems Mega Thread]("http://ubuntuforums.org/showthread.php?t=1799217")

---

### Post by bovisrex on 2011-07-17
Thanks! That worked perfectly, both browsers and both environments.

---

### Post by lovinglinux on 2011-07-17
> **bovisrex said:**
> Thanks! That worked perfectly, both browsers and both environments.

You are welcome.

---

