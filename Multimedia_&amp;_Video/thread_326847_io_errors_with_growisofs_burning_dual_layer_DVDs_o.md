---
title: "i/o errors with growisofs burning dual layer DVDs on edgy"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by ajkessel on 2006-12-28
I have been unable to burn a single dual layer DVD without premature termination on an I/O error. There are a lot of threads out there discussing similar problems, but I haven't been able to find any systematic approach to troubleshooting or any working solutions.

The burn usually fails pretty early on -- sometimes less than 1% in -- but I have made it up to 50% of the disc.

I've tried growisofs, and also tried using cdrecord directly on a pre-mastered ISO. I've tried both ubuntu's standard cdrecord, as well as Joerg Schilly's latest pseudo-upstream cdrecord at <ftp://ftp.berlios.de/pub/cdrecord/alpha/> built from source.

I've tried using the undocumented -poor-man option.

I've tried setting -speed=1, although that seems to have no effect.

I've been through about a dozen dual-layer DVD-R's so far, all have turned into coasters.

The system is generally all from Edgy except I grabbed the kernel from Feisty.

The drive identifies itself as a "MATSHITA DVD-RAM UJ-842S." It is brand new, and works fine for reading and burning single-layer DVD-R's.

I suspect if there were a ready solution to this sort of problem, I would have found it, but I thought it wouldn't hurt to post here to see if there are any ideas.

---

