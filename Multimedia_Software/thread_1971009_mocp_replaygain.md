---
title: "mocp replaygain?"
date: 2012-05-02
forum: Multimedia Software
---

### Post by altbdoor on 2012-05-02
hi everyone

i've been using mocp as my music player for quite some time, up to several months. not too advance as to compile and build moc. 

from [this thread]("http://moc.daper.net/node/81") in moc, it was stated that replaygain was made possible with a [patch]("http://paste.ubuntu.com/850296/") posted, however, no one really explained how to apply this patch into moc. does anyone here in ubuntuforums know?

thanks in advance.

---

### Post by Toz on 2012-05-02
The patch works with  moc-2.5.0-alpha4.tar.bz2 so you need to download that file. Bunzip and untar the file. In the directory that the source is untared into, save the patch file as patch.txt. Then from that directory:
```
patch -p1 < patch.txt
```
...then build the newly patched source.

---

### Post by altbdoor on 2012-05-02
alright, thanks!

---

