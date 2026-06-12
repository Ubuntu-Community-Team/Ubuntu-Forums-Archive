---
title: "Trouble creating .iso file."
date: 2011-02-15
forum: Multimedia Software
---

### Post by Hobbyist on 2011-02-15
I'm trying to create an iso file in a terminal with the following command:

$cat /dev/sr0 > nameofdisk.iso

I get the following error

cat: /dev/sr0: Input/output error

I already checked and my optical drive is indeed /dev/sr0. I've hunted google a few hours trying to figure it out. Does anyone know why I'd be getting this error?

---

### Post by Hobbyist on 2011-02-18
bump. By the way I got the same input output error using the following command
```
 dd if=/dev/sr0 bs=2048 count=332850 > disk.iso
```
The error message is as follows:
```
dd: reading `/dev/sr0': Input/output error
808+0 records in
808+0 records out
1654784 bytes (1.7 MB) copied, 11.6613 s, 142 kB/s
```

---

### Post by aeiah on 2011-02-18
is it a permissions issue (does it work with sudo?)

are you trying to copy a protected disc, such as a retail dvd?

---

### Post by Hobbyist on 2011-02-18
It's not a permission issue I have run both with sudo that was actually the first thing I tried lol. I didn't even consider the fact it was protected which is more than a little annoying. Looks like I can at least create isos from unprotected disks however. Thank you so much for your time, it was much appreciated and very helpful.

---

### Post by Hobbyist on 2011-02-18
It's not a DVD though, but it is a game installation disk. That I would presume is probably protected correct?

---

