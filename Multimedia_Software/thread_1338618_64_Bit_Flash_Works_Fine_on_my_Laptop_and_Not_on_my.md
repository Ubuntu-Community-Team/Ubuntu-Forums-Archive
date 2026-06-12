---
title: "64 Bit Flash Works Fine on my Laptop and Not on my Desktop"
date: 2009-11-26
forum: Multimedia Software
---

### Post by gerowen on 2009-11-26
I am using Ubuntu 9.10 64 bit edition on both of the machines with all of the updates installed.  I downloaded the 64 bit version of flash and moved the .so file into /usr/lib64/mozilla/plugins.  On my laptop it works great, no issues whatsoever.  On the desktop however when I try to visit youtube or some pages on MySpace firefox crashes.  It doesn't do this when I remove the flash plugin file, and it doesn't do this on "all" flash based websites.  I even tried making a copy of the flash plugin file I have on my laptop just in case there was a hiccup in the download, and it still acts the same.  These websites perform just fine on the laptop, and I have tried disabling compiz to make sure it's not a glitch with the video driver and that didn't work either.  I don't know what else to try.

---

### Post by gerowen on 2009-11-26
Well I installed KDE just to let my wife play with it and see which one she preferred and for some reason Firefox works just fine in KDE with the same version of Flash.  Maybe something with the Gnome extension for Firefox?

---

### Post by efflandt on 2009-11-27
What cpu do you have?  Does cat /proc/cpu info show that your cpu has lahf_lm instruction.  See this sticky on the 64 bit forum [http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102) and scroll down and see the part about illegal instruction.

My Athlon64 3200+ (earlier version 2 GHz, 1024K cache) does not have lahf_lm and tended to "sometimes" vaporize Firefox on some flash until I did the flashplugin-lahf-fix.so thing.

---

### Post by gerowen on 2009-11-28
That thread fixed it thanks for pointing it out, :-)  It's a 2.8 Ghz dual core 64 bit Pentium D so it never hit me that it might be considered an "older" processor and would be missing an instruction.

---

