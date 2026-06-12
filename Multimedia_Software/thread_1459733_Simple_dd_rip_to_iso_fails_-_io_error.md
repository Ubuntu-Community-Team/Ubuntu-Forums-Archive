---
title: "Simple dd rip to iso fails - i/o error"
date: 2010-04-21
forum: Multimedia Software
---

### Post by jenllip on 2010-04-21
I like to rip DVDs to iso before taking my laptop on long bus/train rides and am at a complete loss as to why I can no longer rip.

First, dvd::rip failed. Then `dd if=/dev/cdrom of=file.iso` failed. Then right clicking the cd icon on desktop and clicking copy (via brasero) failed. Each of the above worked at some point, and now all are giving me an i/o error like:

> dd: reading `/dev/cdrom': Input/output error
130784+0 records in
130784+0 records out
66961408 bytes (67 MB) copied, 41.6633 s, 1.6 MB/sHave also tried /dev/dvd to no avail. Any help greatly appreciated; I don't think I'm trying to do anything complicated!

---

### Post by takisan on 2010-04-21
I usually do the same thing with floppy diskettes just so I don't have to take one out and put it back in again, but what I usually do is ```
$ sudo cat /dev/fdd > ~/image.img
```
That might work with a DVD drive, but I wouldn't guarantee anything.

---

### Post by jenllip on 2010-04-24
Thanks, but that didn't work either... still getting an i/o error:

cat: /dev/cdrom: Input/output error

---

### Post by FiReSTaRT on 2010-04-27
I found a solution that worked like a charm for me: [http://ubuntuforums.org/showpost.php?p=4902376&postcount=41](http://ubuntuforums.org/showpost.php?p=4902376&postcount=41) First thing I'll do after upgrading to Lucid.

---

