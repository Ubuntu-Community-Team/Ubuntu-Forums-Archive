---
title: "Is there any way to do a drive to drive dvd copy"
date: 2009-12-21
forum: Multimedia Software
---

### Post by shofstetter on 2009-12-21
I have some video dvd's that I composed in the past that I no longer have images for.  I can remeber when I use to use windows I could clone a cd/dvd from one drive right to another.  I have two drives a  dvd/cdrw /dev/scd1 and a dvd+rw /dev/scd0  if I mounted the dvd in scd1 and placed a blank disk in scd0 could I copy from one to the other?

maybe something like this:

mount /dev/scd1 /media/dvd1
growisofs -Z /dev/scd0 -dvd-video /media/dvd1


?????

---

### Post by garryknight on 2009-12-21
If you've got plenty of blank DVDs to try it on, try this:
dd if=/dev/scd1 of=/dev/scd0
Should do a straightforward disc-to-disc bitcopy.

---

### Post by shofstetter on 2009-12-23
Did not work I get a read only file system error?  I think I will need to do it using growisofs somehow

---

### Post by garryknight on 2009-12-24
If it's telling you that your DVD writer is read-only then it's not mounted correctlly.

---

