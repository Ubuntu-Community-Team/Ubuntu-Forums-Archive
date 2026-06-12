---
title: "Update to 2.6.27-14 borked Intel 3945 abg wireless"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by David Valentine on 2009-03-18
After I updated my Lenovo T61 to the 2.6.27-14 kernel, my Intel 3945abg wireless card could "see" my 802.11bg router but could not successfully connect to it.  When I restarted using 2.6.27-13 kernel, everything worked fine.  Anyone else having this experience?  Chalk one up for keeping the old kernels available after updates...

---

### Post by dugh on 2009-03-18
> **David Valentine said:**
> After I updated my Lenovo T61 to the 2.6.27-14 kernel, my Intel 3945abg wireless card could "see" my 802.11bg router but could not successfully connect to it.  When I restarted using 2.6.27-13 kernel, everything worked fine.  Anyone else having this experience?  Chalk one up for keeping the old kernels available after updates...


Seeing the same thing.

See also:
[http://ubuntuforums.org/showthread.php?p=6920016#post6920016](http://ubuntuforums.org/showthread.php?p=6920016#post6920016)
[http://ubuntuforums.org/showthread.php?p=6920020#post6920020](http://ubuntuforums.org/showthread.php?p=6920020#post6920020)

and maybe others are having the same problem

---

### Post by David Valentine on 2009-03-19
> **dugh said:**
> and maybe others are having the same problemSo I gather it's not just the Intel 3945 abg chipset, and so far it's a relatively small number of systems that are affected by this.  This is strange, given how consistently good my system has been with Linux up until now, and how consistently I can reproduce the problem, or fix it, by simply switching between kernel versions and doing nothing else.

---

### Post by ussndmac on 2009-03-19
Been fooling with the same issue since forever, various kernels, same wifi chipset.

---

### Post by Myrtti on 2009-04-22
> **David Valentine said:**
> After I updated my Lenovo T61 to the 2.6.27-14 kernel, my Intel 3945abg wireless card could "see" my 802.11bg router but could not successfully connect to it.  When I restarted using 2.6.27-13 kernel, everything worked fine.  Anyone else having this experience?  Chalk one up for keeping the old kernels available after updates...

I've got the same problem on x86_64 and I haven't been able to pinpoint where the problem is. Fortunately(?) Jaunty is now just behind the corner, so I might try it as well, but not having high hopes yet.

---

