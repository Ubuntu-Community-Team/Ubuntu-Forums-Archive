---
title: "rip copy controlled cd"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by nomis3613 on 2008-04-04
Hi,
I can't find a way to rip a copy controlled cd. I've done some interweb searching and it seems cdparanoia is the way to go. But when I insert the copy controlled cd, I get:```
Verifying CDDA command set...
        Could not find any audio tracks on this disk.

Unable to open disc.
```(then my cd drive makes horrible noises)

A normal audio cd gives me:
```
Table of contents (audio satracks only):
track        length               begin        copy pre ch
===========================================================
  1.    18068 [04:00.68]        0 [00:00.00]    no   no  2
  2.    20442 [04:32.42]    18068 [04:00.68]    no   no  2
  3.    12820 [02:50.70]    38510 [08:33.35]    no   no  2
  4.    18390 [04:05.15]    51330 [11:24.30]    no   no  2
  5.    18343 [04:04.43]    69720 [15:29.45]    no   no  2
  6.    21647 [04:48.47]    88063 [19:34.13]    no   no  2
  7.    18078 [04:01.03]   109710 [24:22.60]    no   no  2
  8.    17025 [03:47.00]   127788 [28:23.63]    no   no  2
  9.    13135 [02:55.10]   144813 [32:10.63]    no   no  2
 10.    10790 [02:23.65]   157948 [35:05.73]    no   no  2
 11.    13640 [03:01.65]   168738 [37:29.63]    no   no  2
 12.     9679 [02:09.04]   182378 [40:31.53]    no   no  2
TOTAL  192057 [42:40.57]    (audio only)
```My laptop is old and only has a cd reader. I read somewhere that only burners can decypher Copy Controlled cds. Is this true? Or is there another way I can get MY MUSIC I HAVE PAID FOR converted to .ogg files?

Thanks,
Simon

---

### Post by nomis3613 on 2008-04-08
<bump>

---

### Post by andrew.46 on 2008-04-17
Hi,

 Sounds absolutely fascinating! Unfortunately I do not have access to a copy protected cd but I hear that the following works:

```
$ cdparanoia -vB
```

but of course I cannot test this without access to such a disk :confused:. It would be interesting to see what cdrdao made of the copy protection.

      Andrew

---

### Post by nomis3613 on 2008-05-24
Just updating the thread in case anyone else comes across it...
couldn't find a way to get it to work on my PC. Maybe because I only have a CD reading drive. My PC at work with a DVD burner ripped the CD fine using MediaMonkey (windows only at the moment, unforunately)

---

