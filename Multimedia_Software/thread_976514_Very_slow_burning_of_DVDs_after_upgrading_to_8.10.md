---
title: "Very slow burning of DVDs after upgrading to 8.10"
date: 2008-11-09
forum: Multimedia Software
---

### Post by ekot on 2008-11-09
Hi

I have a problem after upgrading to 8.10 and new kernel 2.6.27, burning DVDs in K3B became very slow and CPU load very high. Notice difference in speed in following logs.
Any idea how to fix it?

Here is the log for kernel 2.6.27

```

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-7-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-116D 1.03 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, &#1054;&#1075;&#1088;&#1072;&#1085;&#1080;&#1095;&#1077;&#1085;&#1085;&#1072;&#1103; &#1087;&#1077;&#1088;&#1077;&#1079;&#1072;&#1087;&#1080;&#1089;&#1100;, Layer Jump]

Burned media
-----------------------
DVD+RW

K3bIsoImager
-----------------------
mkisofs print size result: 2090495 (4281333760 bytes)
Pipe throughput: 1024159360 bytes read, 1024154880 bytes written.

Used versions
-----------------------
mkisofs: 1.1.8
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 4.1x1352KBps.
    1605632/4281333760 ( 0.0%) @0.0x, remaining 266:32 RBU 100.0% UBU   2.0%
    1605632/4281333760 ( 0.0%) @0.0x, remaining 399:49 RBU 100.0% UBU 100.0%
    1605632/4281333760 ( 0.0%) @0.0x, remaining 577:30 RBU 100.0% UBU 100.0%
    4620288/4281333760 ( 0.1%) @0.7x, remaining 246:50 RBU 100.0% UBU  20.4%
    8421376/4281333760 ( 0.2%) @0.8x, remaining 169:07 RBU 100.0% UBU  46.9%
   12222464/4281333760 ( 0.3%) @0.8x, remaining 133:53 RBU  99.9% UBU  12.2%
   16285696/4281333760 ( 0.4%) @0.9x, remaining 113:29 RBU 100.0% UBU  24.5%
   20283392/4281333760 ( 0.5%) @0.9x, remaining 105:02 RBU 100.0% UBU  14.3%
   24051712/4281333760 ( 0.6%) @0.8x, remaining 97:21 RBU 100.0% UBU  28.6%
   27918336/4281333760 ( 0.7%) @0.8x, remaining 91:24 RBU  99.9% UBU  14.3%
   31981568/4281333760 ( 0.7%) @0.9x, remaining 88:34 RBU 100.0% UBU  26.5%
...

```

and here for kernel 2.6.24

```

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-21-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-116D 1.03 (/dev/hdb, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, &#1054;&#1075;&#1088;&#1072;&#1085;&#1080;&#1095;&#1077;&#1085;&#1085;&#1072;&#1103; &#1087;&#1077;&#1088;&#1077;&#1079;&#1072;&#1087;&#1080;&#1089;&#1100;, Layer Jump]

Burned media
-----------------------
DVD+RW

K3bIsoImager
-----------------------
mkisofs print size result: 2089947 (4280211456 bytes)
Pipe throughput: 4280211456 bytes read, 4280211456 bytes written.

Used versions
-----------------------
mkisofs: 1.1.8
growisofs: 7.1

growisofs
-----------------------
WARNING: /dev/hdb already carries isofs!
About to execute 'builtin_dd if=/dev/fd/0 of=/dev/hdb obs=32k seek=0'
/dev/hdb: "Current Write Speed" is 4.1x1352KBps.
    1605632/4280211456 ( 0.0%) @0.0x, remaining 266:28 RBU 100.0% UBU   2.0%
    1605632/4280211456 ( 0.0%) @0.0x, remaining 444:07 RBU 100.0% UBU 100.0%
    1605632/4280211456 ( 0.0%) @0.0x, remaining 577:21 RBU 100.0% UBU 100.0%
   16842752/4280211456 ( 0.4%) @3.3x, remaining 71:43 RBU 100.0% UBU  55.1%
   35192832/4280211456 ( 0.8%) @4.0x, remaining 40:12 RBU 100.0% UBU  53.1%
   54263808/4280211456 ( 1.3%) @4.1x, remaining 29:51 RBU  99.1% UBU  57.1%
   72482816/4280211456 ( 1.7%) @3.9x, remaining 26:07 RBU 100.0% UBU  57.1%
   90669056/4280211456 ( 2.1%) @3.9x, remaining 23:06 RBU 100.0% UBU  53.1%
  109772800/4280211456 ( 2.6%) @4.1x, remaining 20:53 RBU 100.0% UBU  55.1%
  127860736/4280211456 ( 3.0%) @3.9x, remaining 20:01 RBU 100.0% UBU  59.2%
  146079744/4280211456 ( 3.4%) @3.9x, remaining 18:52 RBU 100.0% UBU  55.1%
  164954112/4280211456 ( 3.9%) @4.1x, remaining 17:52 RBU  99.5% UBU  53.1%
...

```

---

### Post by Machiavelli on 2008-11-25
I'm experience the same issue.

---

### Post by djbushido on 2008-11-25
I'm not sure why this is happening for you, but try another utility, like brasero, just to make sure that this is happening across programs. It may just be k3b. I doubt it, but it could be.

---

### Post by slimjim8094 on 2008-11-25
I'm having (every) burn fail, with a known-good CD drive.

It *may* be related to "wodim" which due to a pissing contest^W^W licensing issue replaced the cdrecord by Schilling.

Though for what it's worth, non-clone cdrecord is not working either.

EDIT: Try different/new CDs. I made literally 20 coasters before I just went and got some new disks (nothing special, just Staples). They seem to be working fine *crosses fingers on verify*

---

### Post by jekkil on 2008-11-27
I have a pioneer DVR-112 and I get the same problem.
Extremely slow to burn any DVD with brasero.
I am using the same ubuntu (8.10 workstation) version on my laptop (asus W7J) and there burning has no problem.

Anyone has an idea how to solve this ?

---

### Post by BentSlightly on 2009-01-05
I have the same issue totally slow, and not many people are talking about it. 


HALP!:popcorn:

---

### Post by aL3xandar on 2009-03-06
Well, to be honest, I don't think that slow DVD-burning has to do something with upgrading to 8.10, although I rather prefer fresh install... Anyway, I didn't have that problem back on Hardy, and I've experienced it on Intrepid. It has something to do with DMA support, and I managed to improve DVD burning performance on my machine, although it's still not quite satisfactory - I need approximately 15 minutes on 8x, and on Puppy linux, which has older kernel, I need less than 8 minutes!

However, you should check out [this link]("http://ubuntuforums.org/showthread.php?p=4615284")!

Once again, this change did improve DVD burning, but still didn't "fix" it the proper way!!

I hope this helps somehow!

Please send feedback!

---

### Post by Freudi on 2009-07-16
Could you please repost the link or give any hint which post you where referring to ? The link to the other forum entry doesn't seem to be valid anymore :(

Thanks !

---

