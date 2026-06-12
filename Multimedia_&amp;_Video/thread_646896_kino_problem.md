---
title: "kino problem"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by brandon333 on 2007-12-21
I just downloaded kino and hooked up digtal cam and in kino it says "the raw 1494 must be loaded, and you must have read and write access"

what? huh? english?

---

### Post by Tuxi on 2007-12-21
You need to have the raw1394 module active -- "sudo insmod raw1394"

Also, you may need to change the owner of /dev/raw1394.  I changed mine as follows "sudo chown owner /dev/raw1394"

I hope this helps.

---

### Post by brandon333 on 2007-12-21
> **Tuxi said:**
> You need to have the raw1394 module active -- "sudo insmod raw1394"

Also, you may need to change the owner of /dev/raw1394.  I changed mine as follows "sudo chown owner /dev/raw1394"

I hope this helps.

no such file

---

