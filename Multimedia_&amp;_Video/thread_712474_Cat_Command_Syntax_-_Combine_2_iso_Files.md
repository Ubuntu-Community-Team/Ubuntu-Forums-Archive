---
title: "Cat Command Syntax - Combine 2 iso Files"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by dontgetshocked on 2008-03-01
Can someone please tell me the correct code to use to combine 2 files named    1.iso  and 2.iso    into  games.iso    using the cat command?


I have tried using IsoMaster with no luck and neither the Cat command so far.

Thanks,

---

### Post by srt4play on 2008-03-01
cat 1.iso 2.iso > games.iso

---

### Post by asmoore82 on 2008-03-01
This cannot work as you seem to intend unless the files are either
plain text files -OR- were intentionally split from the same file earlier

You cannot simply concatenate 2 arbitrary ISO files.
If they are indeed arbitrary, autonomous ISOs,
you must either "extract" the files out of or mount both ISOs
and re-master a single ISO.

---

### Post by dontgetshocked on 2008-03-02
Well, Thanks all, I got it done.The original file was an iso and was split into 2 files. So this worked.
cat 1.iso 2.iso > games.iso


Yeah!

---

