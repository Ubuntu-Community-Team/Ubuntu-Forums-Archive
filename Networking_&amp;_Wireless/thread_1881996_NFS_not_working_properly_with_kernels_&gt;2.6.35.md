---
title: "NFS not working properly with kernels &gt;2.6.35"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by hitausmomentti on 2011-11-16
After downgrading to a 2.6.35 kernel because of the problems described in an older thread [1], I tested other kernel versions to see which one is the newest that still works properly. 2.6.35 is the last one. The NFS problem is that while everything appears to be fine in the way that applications don't break, the authentication has to be refreshed for each call, which is easily over 10000 times in a few seconds while opening desktop session when /home is on NFS. File transfers and other heavier operations are slower than on 2.6.35 and the iowait cpu usage either increases a lot or goes through the roof. 

I've looked at what nfsstat -rc says on a few machines, and every single one running anything >2.6.35 has shown the same problem. 2.6.35 was fine in all cases, with the authrefrsh value 0. Different NICs, virtualization or NFS servers also don't seem to affect this. This has mostly gone unnoticed in most of the machines I tried because they have  little NFS traffic and in many cases no desktop at all. I only noticed the NFS problem when I had to use NFS after CIFS broke on a desktop system.

1. [http://ubuntuforums.org/showthread.php?t=1877636](http://ubuntuforums.org/showthread.php?t=1877636)

---

