---
title: "ndiswrapper ndiswrapper.conf"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2009-06-22
I think this is a BUG because all modprobe.d files need to end in .conf but ndiswrapper just creates a file called ndiswrapper there.  

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.

So I don't know how to get this working.  The ath5k driver 'works' sort of with eee-pc 701 but gives exceptionally crappy performance even with jaunty.  I just use the windows driver and it runs at full speed and it doesn't crap out on me.  I can install my driver

ifconfig wlan0 down
rmmod ath5k
ndiswrapper install /home/701/ndis5k/net5211.inf
ndiswrapper -ma
ndiswrapper -mi
depmod -a
modprobe ndiswrapper

[B]WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.[/B]

I tried this 

sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf

nope

so then i edited /usr/sbin/ndiswrapper-1.9 and changed the one reference of /etc/modprobe.d/ndiswrapper to ndiswrapper.conf and reran the 

ndiswrapper -ma
ndiswrapper -mi 

and it wrote to ndiswrapper.conf instead but I cannot modprobe ndiwsrapper still.  now I just get

FATAL: Module ndiswrapper not found.


HELP

---

### Post by Ayuthia on 2009-06-22
The /etc/modprobe.d/ndiswrapper warning is not an issue at this time.  The system will still use it but will provide the warning.  However, the FATAL message is saying that it is missing the ndiswrapper.ko kernel module.

How did you install ndiswrapper?  Was it from Ubuntu or did you compile it?

---

### Post by maestrobwh1 on 2009-06-22
Thanks for the quick help.  I didn't see any other issues with unbuntu users so I went back to the basics: I was using eeebuntu, so I downgraded to an earlier kernel of theirs and ndiswrapper inserted fine (with the error) and wireless came up.

---

