---
title: "Ubuntu Studio package upgrade now crashed Nvidia driver"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by Shlomir on 2007-09-01
Looks like this is becoming a Common Bug with Ubuntu Studio upgrades and NVIDIA drivers, hopefully someone can fix it.. But I've noticed some interesting behaviors... Here is what I did until everything CRASHED...my system boots up, but when it goes to the Ubuntu Studio spalsh scree...well it doesn't actually appear, screen goes black until the Xconfig server or whatever just cacks it.. SO what I did

1. Installed Fiesty Fawn 7.04
2. Install Nvidia GX5700 card
3. Fiesty crashed, but was able to reinstall Nvidia driver from command line \sudo apt-get blah blah NVidia' and the driver installed beautifully

THING Is, I really wanna do multimedia open-source, so I trued to upgrade to Ubuntu Studio via command line, and got a fail due to a depency in GIMP 'gimp-swc' that failed as it couldn't sync with new GIMP files BUGGER!!

4. Installed all the Ubuntu studio packages via Synapic Package manager, and skipped the gimp-svc bit, all finished OK
5. Rebooted machine and got the BLACK SCRREN OF DEATH HORROR and then the XServ error like some other users got, but it said can't find module 'nfb'...???
6. Uninstalled and re-installed Nvidia driver from command line, but still failed

7. Pulled hair out, screamed, wasted a whole weekend, and wondered, WHO SAID UBUNUTU IS now easier than ever to install and configure?

8. Would greatly appreciate some advice to fix tis, or is ity a full-on Bug with Ubuntu Studio?? 

NOTE: Had to post this through Windoze partition, becuase, well, it works and Ubuntu doesn't

NOTE NOTE: Would prefer to go to Ubuntu Studio for long term, but getting it *working*  nicely is another thing.

Cheers :guitar:

---

### Post by Shlomir on 2007-09-01
Ok, I found some other forum link, and found the one that mentioned installing the 2.2.0.15 or -whatever low-latency kernel if you are running an Nvidia card...

WELL, I did this, uninstall and re-installed the driver, AND.....

STILL HAVE THE BLACK SCREEN OF UBUNTU-Studio DEATH!!

When the text error windows came up, I've noticed it says failed to load module 'wfb'..What is this module and how do you install...

Thanks:lolflag:

---

