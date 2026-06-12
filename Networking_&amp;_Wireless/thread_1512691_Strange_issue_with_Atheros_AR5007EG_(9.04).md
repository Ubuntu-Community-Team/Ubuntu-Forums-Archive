---
title: "Strange issue with Atheros AR5007EG (9.04)"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by w0ss4g3 on 2010-06-18
Hi,

Im aware that the problems of getting the AR5007EG with the various versions is well documented, however I was originally having no problems on my samsung NC10 under ubuntu 9.04.

However, a while ago there was a kernel update and I've been having issues ever since, although I tried to fix it for good today and have found some odd things...

First of all, it seemed to work fine using the default ath5k driver, but would sometimes stop working. A reboot usually cured this. The madwifi drivers did originally work, but I found them less reliable and they no longer work at all with the current kernel (-19)

The next thing I noticed is that after using linux, then booting into windows, I wouldn't be able to see any networks in windows and would also experience the strange mouse lag problem that some people have mentioned in some threads.

The odd thing is that when it refused to work in windows, it would also refuse to work in linux again, and no matter how many times I rebooted or reinstalled drivers, nothing worked. I would then usually turn on a day later and all would be fine.

I have just done some testing and found that if I have the issue of wifi not working at all (in linux or windows), then I can fix it by turning off entirely, unplugging the power and then rebooting into windows. This leads me to think that there may be some issue with the ath5k driver causing some leftover state in the chipset. I guess this would make sense as when I fully power down, this then reverts back to the default state, and then everything magically works again.

I currently have working drivers in windows and linux, although I haven't been in linux long enough to be sure that it'll stay working from now on.

I just thought I'd share this with anyone who's been having problems with Atheros based chipsets.. maybe this will fix some issues temporarily?

Anyone have any other ideas on using the ath5k drivers or getting the madwifi drivers without having to compile the latest release (and also have to reinstall every kernel update)?

Cheers for any suggestions :)

---

