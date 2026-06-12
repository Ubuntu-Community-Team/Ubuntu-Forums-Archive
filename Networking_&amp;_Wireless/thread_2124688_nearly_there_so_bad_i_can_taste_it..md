---
title: "nearly there so bad i can taste it."
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by sparklyballs on 2013-03-11
after much deliberation and hair pulling, of which i don't have much left, i have finally got hd-audio passthrough working on my dual booted mac mini late 2012. 

i've had to push up to kernel 3.8 to do it, and that now has thrown up another issue i was having that was previously solved. 

i used the info here 

[http://ubuntuforums.org/showthread.php?t=2078320](http://ubuntuforums.org/showthread.php?t=2078320)

to get my ethernet card working but when i try and do it again under 3.8 it throws up this error.

ERROR (dkms apport): binary package for tg3: 3.124c not found
ERROR! Bad return status for module build on kernel: 3.8.0.030800-generic

i was wondering whether this is happening because i previously had it install under another kernel (i did dksm remove'd it prior to the kernel update, cos it crashed an earlier kernel update on another fresh install attempt on this machine.) or this trick will just no longer work on this high a kernel. 

can someone tell me how to flush all traces of tg3 module from the system so i can do a completely fresh go at it, cos i'd rather not have to go for another fresh installation. 

thanks for any help.

---

### Post by iponeverything on 2013-03-11
```
sudo rm /lib/modules/`uname -r`/kernel/drivers/net/tg3.ko
```

---

