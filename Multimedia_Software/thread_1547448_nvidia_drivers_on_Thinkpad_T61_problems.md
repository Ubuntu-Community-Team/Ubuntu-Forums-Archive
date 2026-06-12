---
title: "nvidia drivers on Thinkpad T61 problems"
date: 2010-08-06
forum: Multimedia Software
---

### Post by mike4ubuntu on 2010-08-06
It seems the latest nvidia drivers (255.44) don't seem to work on my Lenovo Thinkpad T61 in Lucid.  Has anybody gotten it to work?  I've tried to just use the System -> Drivers control panel to install and activate the current nvidia drivers as well as installing it from the command line.  However, when I reboot, I see the nvidia splash screen come up for a second, then the screen goes blank, and then the nvidia splash screen pops up again, and then the screen goes blank again, over and over.  It seems to be in some kind of infinite initialization loop.  My T61 has the nvidia NVS 140m chipset.  This is frustrating since the previous drivers seemed to work ok.  When I try to revert to older drivers, it complains now that they're no longer compatible with the latest kernel headers, etc.  I've had to boot up into the failsafe graphics mode to be able to use the laptop, which is kind of a pain.  Any ideas?

---

### Post by Zeike on 2010-08-06
The nvidia chip in my T61 melted some time ago rendering it inoperable, but I'm glad you've escaped that fate.

I don't know specifically about your problem, but I'll share with you this website that is quite helpful for thinkpads + linux, in case you don't know about it already.

[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

---

### Post by mike4ubuntu on 2010-08-20
well, as it turns out, I had Lucid 32 bit installed.  Since the T61 has an AMD64 dual core processor, I installed the AMD64 version of Lucid, and the proprietary nVidia drivers seem to work better.  It appears that the nVidia drivers are not compatible with Lucid 32 bit on the T61, but are compatible with Lucid AMD64 on the T61.

---

