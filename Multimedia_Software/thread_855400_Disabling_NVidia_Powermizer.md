---
title: "Disabling NVidia Powermizer"
date: 2008-07-10
forum: Multimedia Software
---

### Post by NTolerance on 2008-07-10
NVidia has a nasty bug in their drivers in which Powermizer causes black screen flashes when using Compiz.  I would prefer to simply lock my GPU clockspeed to the lowest setting on my system (this is plenty fast to run Compiz) to prevent this problem and also save power and battery life.

I've seen plenty of methods for this such as PerfLevelSrc, adding Powermizer options to xorg.conf, and using Coolbits to underclock the GPU.  I've tried all of these and my 7400 GO insists on ignoring all of them.  Is there way to permanently brute force this?  Thanks.

Edit:  I'd also like to state that locking the GPU at the highest speed won't work due to excessive heat and power issues.

---

### Post by sdennie on 2008-07-10
There is no way to disable it that I'm aware of.  If PerfLevelSrc isn't working for you, you might be able to peg the GPU to maximum speed using something similar to this (just remove the on_ac_power parts): [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369) but, that's designed to peg the GPU at maximum speed.  The other option would be to update to the latest nvidia drivers and see if that fixes the problem for you.

---

### Post by NTolerance on 2008-07-23
In case anyone stumbles upon this thread via search, eznet provides the answer here:

[http://ubuntuforums.org/showpost.php?p=5401046&postcount=57](http://ubuntuforums.org/showpost.php?p=5401046&postcount=57)

---

