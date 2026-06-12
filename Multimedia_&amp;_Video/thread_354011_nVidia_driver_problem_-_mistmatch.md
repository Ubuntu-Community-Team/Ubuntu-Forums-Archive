---
title: "nVidia driver problem - mistmatch"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by Anessen on 2007-02-05
Hey

My system is:
2.0ghz AMD X2 64 3800+ processor
nVidia 7950GT (512mb, PCI-E x16) graphics card
MSI K9VGM-V motherboard
1gb DDR2 533mhz RAM
Ubuntu 6.10

I have the nVidia proprietary driver working - sort of. I can install the latest driver (from the nVidia website), and it finds my graphics card (the one in the ubuntu repository won't). I can get all the resolutions/refresh rates working through the nVidia x config, as well as 3D acceleration working.

However, after I restart my computer (not just the X server, the whole OS), I get an X Server error.

It says something about an API Mismatch, a difference between the version of the Kernel driver module and the X driver module.

It reports that my nVidia kernel module is of version "1.0-7184", while my X module is "1.0-9746".

At this point, I need to go into a text terminal, close GDM, edit xorg.conf to use the "nv" driver, and restart GDM. Each time I start the OS.

How can I stop this from happening?

---

### Post by ehowell on 2007-02-05
I have almost the same setup as you and was having nvidia driver troubles.

I ended up using the program Envy to install the drivers as the repository nvidia ones didn't work for me. 

It might be worth giving that program a try.

Info on how to get envy is in this thread  [AMD dual core -- but am I using both?]("http://ubuntuforums.org/showthread.php?t=347107")

---

### Post by OffHand on 2007-02-05
[http://www.ubuntuforums.org/showpost.php?p=2110951&postcount=2](http://www.ubuntuforums.org/showpost.php?p=2110951&postcount=2)

---

