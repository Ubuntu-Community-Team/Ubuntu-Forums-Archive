---
title: "How to remove region encoding on a DVD"
date: 2008-06-29
forum: Multimedia Software
---

### Post by DPic on 2008-06-29
Hi, 

I was wondering how to make a copy of a DVD with region encoding while keeping all the files on it the same but removing the region encoding. No compression, etc.

---

### Post by mc4man on 2008-06-30
For 99% of your titles I'd use vobcopy. a decent command would be
```
vobcopy -v -m -F 16
``` If you have 2 drives you may need to specify the device. Ex.
```
vobcopy -v -m -F 16 /media/cdrom1
``` If you wanted to save somewhere other than home Ex. (in this case a partition
```
vobcopy -v -m -o /media/rips -F 16 
```
Another way or if there is structure protection present (and you don't know how or want to fix it manually), would be to use k9copy. Just set the target size bigger than the disk and it will rip with no compression.

---

### Post by kumarnarain on 2008-06-30
The previous post is very good...else you can also try a package called dvdrip by running 
sudo apt-get install dvdrip
The settings in the application allow you to make a wide variety of choices

---

### Post by DPic on 2009-07-25
Thanks! Now does there exist a program like DVD decrypter that can keep it as an ISO image, but only stripping away the region lock? If i rip using these other programs, will it just create a video file and i lose all the DVD menu's and such?

---

