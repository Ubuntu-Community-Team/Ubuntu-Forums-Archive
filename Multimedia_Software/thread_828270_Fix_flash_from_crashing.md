---
title: "Fix flash from crashing"
date: 2008-06-13
forum: Multimedia Software
---

### Post by magnus0 on 2008-06-13
Flash tends to crash browsers in Ubuntu very often. I have a fix for that.
I tried it and I couldn't get Firefox to crash.

Go to terminal and execute this whole big command:

```
wget http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb && sudo dpkg -i nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb && sudo apt-get remove --purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree libflashsupport

```

---

