---
title: "Problem with a DVD project in k3b"
date: 2010-03-03
forum: Multimedia Software
---

### Post by beliyyal on 2010-03-03
Hit guys, I am having a problem with k3b. I am trying to create a video DVD image using the dvd files. I copied the .vob, .ifo, and .bup files into the VIDEO_TS folder in k3b like I always do, but I am getting an error when I try to make the image. 

This is what's in the debugging output:
>  Devices
-----------------------
SONY CD-RW  CRX215E5 6.1G (/dev/sr0, CD-R, CD-RW, CD-ROM) [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, RAW/R16, RAW/R96R] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-19-generic

Used versions
-----------------------
mkisofs: 1.1.9

mkisofs
-----------------------
/usr/bin/genisoimage: Either VIDEO_TS.IFO or VIDEO_TS.VOB is not of correct size.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid SWE5 -volset  -appid K3B THE CD KREATOR (C) 1998-2007 SEBASTIAN TRUEG -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-dalton/k3bm28025.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-dalton/k3bN28025.tmp -dvd-video -f /tmp/kde-dalton/k3bVideoDvd0

And this is a screenshot of the dialogue:
[IMG]http://img28.imageshack.us/img28/8338/screenshotoxw.png[/IMG]


Any ideas?

---

### Post by beliyyal on 2010-03-03
bump

---

### Post by ferd on 2010-03-05
> **beliyyal said:**
> Hit guys, I am having a problem with k3b. I am trying to create a video DVD image using the dvd files. I copied the .vob, .ifo, and .bup files into the VIDEO_TS folder in k3b like I always do, but I am getting an error when I try to make the image. 

This is what's in the debugging output:


And this is a screenshot of the dialogue:
[IMG]http://img28.imageshack.us/img28/8338/screenshotoxw.png[/IMG]


Any ideas?

No ideas but I have the same exact problem. Found last night. Open to all suggestions. Thanks in advance.:([-o<

---

### Post by beliyyal on 2010-04-11
Damn, no one has yet to come up with a solution? Well, how about a suggestion for a program with similar feature?

---

### Post by beliyyal on 2010-04-20
I found a program that works pretty good, it will convert the files that k3b won't. It's called [imgburn]("http://www.imgburn.com/"). It will install through wine, and it works like a charm.

---

