---
title: "BCM4311 not working using STA Drivers"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by lucacerone on 2010-08-26
Dear all,
I'm having a strange problem with my wireless
card (I never had troubles with it so I'd be glad if you could help
me in making it work again).

I have installed the restricted STA driver for my Broadcom BCM4311 wireless card, and apparently the card is recognized, and in fact I can "see" the available wireless networks and connect to my one.

The strange things is that even if I connect to my network I can't navigate. If I link an ethernet cable, start navigating and after disconnect the ethernet and keep using only the wireless,
I can navigate without problems.

Can you please help me in solving this issue? I have no idea where I should start.

Cheers, 
-Luca

---

### Post by dineshs on 2010-08-27
Are you using 9.10?(Maybe you have done this already)
[http://ubuntuforums.org/showpost.php?p=8578859&postcount=4](http://ubuntuforums.org/showpost.php?p=8578859&postcount=4)

Another point ,The following link also suggests to install bcmwl-kernel-source for broadcom 4312 
[http://ubuntuforums.org/showthread.php?t=1307995](http://ubuntuforums.org/showthread.php?t=1307995)

---

### Post by promet on 2010-08-27
Also, this may help?

[http://ubuntuforums.org/forumdisplay.php?f=336]("http://ubuntuforums.org/forumdisplay.php?f=336")

---

### Post by lucacerone on 2010-08-27
Thanks guys,
I forgot to say I'm with Ubuntu 10.04,
the drivers are installed and the kernell module
as well...
None of the links helped though, any other suggestion?

---

### Post by dineshs on 2010-08-27
please post the output of
```
sudo lshw -C network
```and ```
iwconfig
```

---

### Post by lucacerone on 2010-08-27
Thanks for your help,
unfortunately I was in a hurry and fount easier to re-install (it was a fresh
OS no many data on it, so it has been quicker like this).
now I have no problem.
I think the issue arose because when I installed Ubuntu the first time,
I had no access to internet, so the Alternate CD configured the ethernet
network in a wrong way.
Just for my own knowledge: how could I have uninstalled (including configuration
files), all the packages abouth ethernet and wireless and re-install them as 
it happens from installation?
Thanks a lot for your help in any case,
Cheers, -Luca

---

