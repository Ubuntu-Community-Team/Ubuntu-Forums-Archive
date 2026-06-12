---
title: "File deletion speed with ext4"
date: 2009-12-10
forum: Mythbuntu
---

### Post by ubnewbie2 on 2009-12-10
I have experienced the slow delte times of ext3 on my current installation on mythtv.   When I rebuild the box, I believe the latest mythbuntu defaults to ext4, so my question is whether ext4 improves/fixes the slow delete performance, or should I use some other file system, then if so, what's the latest recommendations.

---

### Post by jaakan on 2009-12-11
> **ubnewbie2 said:**
> I have experienced the slow delte times of ext3 on my current installation on mythtv.   When I rebuild the box, I believe the latest mythbuntu defaults to ext4, so my question is whether ext4 improves/fixes the slow delete performance, or should I use some other file system, then if so, what's the latest recommendations.

here is a good place to look

[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1]("http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1")

I'm currently using /boot/ = ext3 , / = ext4. Because of a bug related to my nvraid controller I could not use just / = ext4.

---

### Post by ian dobson on 2009-12-11
Hi,

Those results are from an old kernel (2.6.28) things have changed abit since then. I'd say that ext4 is quicker than ext3 at deleting but not as fast as XFS.

Regards
Ian Dobson

---

### Post by ubnewbie2 on 2009-12-11
Sounds like it may be fast enought then, thanks for the advice.

---

