---
title: "How do I check CD-R(W) for errors?"
date: 2008-02-12
forum: Multimedia Production
---

### Post by newnet on 2008-02-12
I burned an image into the disk, but it would not work properly.  I did a checksum and it matched.  So it has lead me to believe that it is the disks itself.  How do I check if the disks I am using have errors/defects or not?

Can it be checked with cdrecord?  That is what I used and I do not want to download additional stuff.  If additional stuff is needed to check, please suggest something very small in size.

---

### Post by gsmanners on 2008-02-12
The smallest thing I can think of is in a console:

df
(look at 1K-blocks for count)
dd if=/dev/hda of=disc.iso bs=1024 count=<insert count here>
md5sum disc.iso

---

### Post by siddartha on 2008-02-13
There is a small specialised tool cdck. You will find it in the standard ubuntu repositories if you enable universe.

---

### Post by jms830 on 2008-02-20
when i try to use cdck on an audio CD, I get this message,
 "Unable to read disc because disc_status != CDS_DATA_1"
does anyone know how to fix this?

---

