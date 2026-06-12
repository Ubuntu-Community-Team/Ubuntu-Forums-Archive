---
title: "KINO media error?!"
date: 2009-01-23
forum: Multimedia Software
---

### Post by RX8volution on 2009-01-23
Hi all,
  I've been having one heck of a time burning DVDs (I can't)... K3b accepts all the files (VIDEO_TS and AUDIO_TS) and then starts the process only to error with:

[B]:-( media is not formatted or unsupported
Write error[/B]

What the heck does that mean?!  Ubuntu (8.10) can see the Blank DVDr, as can K3b... but it simply won't burn!  These DVDs have been used a bunch of times, and I'm down to about half-way down the spindle... are they "bad" somehow all of the sudden?

Thanks.

Here's the complete debug output:

```
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-11-generic
Devices
-----------------------
_NEC DVD_RW ND-2510A 2.05 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD-R Sequential

K3bIsoImager
-----------------------
mkisofs print size result: 2242941 (4593543168 bytes)
Pipe throughput: 33582848 bytes read, 33578496 bytes written.

Used versions
-----------------------
mkisofs: 1.1.8
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: engaging DVD-R DAO upon user request...
/dev/scd0: reserving 2242941 blocks
:-[ RESERVE TRACK failed with SK=5h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type
/dev/scd0: "Current Write Speed" is 1.0x1352KBps.
:-[ WRITE@LBA=0h failed with SK=5h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2242941 -use-the-force-luke=dao:2242941 -dvd-compat -speed=2 -overburn -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
2242941
Warning: -follow-links does not always work correctly; be careful.
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.02% done, estimate finish Fri Jan 23 17:07:47 2009
  0.04% done, estimate finish Fri Jan 23 17:07:47 2009
  0.07% done, estimate finish Fri Jan 23 17:07:47 2009
  0.09% done, estimate finish Fri Jan 23 17:07:47 2009
  0.11% done, estimate finish Fri Jan 23 17:07:47 2009
  0.13% done, estimate finish Fri Jan 23 17:07:47 2009
  0.16% done, estimate finish Fri Jan 23 17:07:47 2009
  0.18% done, estimate finish Fri Jan 23 17:07:47 2009
  0.20% done, estimate finish Fri Jan 23 17:07:47 2009
  0.22% done, estimate finish Fri Jan 23 17:07:47 2009
  0.25% done, estimate finish Fri Jan 23 17:07:47 2009
  0.27% done, estimate finish Fri Jan 23 17:07:47 2009
  0.29% done, estimate finish Fri Jan 23 17:07:47 2009
  0.31% done, estimate finish Fri Jan 23 17:07:47 2009
  0.33% done, estimate finish Fri Jan 23 17:07:47 2009
  0.36% done, estimate finish Fri Jan 23 17:07:47 2009
  0.38% done, estimate finish Fri Jan 23 17:07:47 2009
  0.40% done, estimate finish Fri Jan 23 17:07:47 2009
  0.42% done, estimate finish Fri Jan 23 17:07:47 2009
  0.45% done, estimate finish Fri Jan 23 17:07:47 2009
  0.47% done, estimate finish Fri Jan 23 17:07:47 2009
  0.49% done, estimate finish Fri Jan 23 17:07:47 2009
  0.51% done, estimate finish Fri Jan 23 17:07:47 2009
  0.54% done, estimate finish Fri Jan 23 17:07:47 2009
  0.56% done, estimate finish Fri Jan 23 17:07:47 2009
  0.58% done, estimate finish Fri Jan 23 17:07:47 2009
  0.60% done, estimate finish Fri Jan 23 17:07:47 2009
  0.62% done, estimate finish Fri Jan 23 17:07:47 2009
  0.65% done, estimate finish Fri Jan 23 17:07:47 2009
  0.67% done, estimate finish Fri Jan 23 17:07:47 2009
  0.69% done, estimate finish Fri Jan 23 17:07:47 2009
  0.71% done, estimate finish Fri Jan 23 17:07:47 2009

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Mama Mia! -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-rafal/k3bkSaaJb.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-rafal/k3bNS3xEa.tmp -dvd-video -f /tmp/kde-rafal/k3bVideoDvd0 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Mama Mia! -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-rafal/k3bdW5nPa.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-rafal/k3bI0skDa.tmp -dvd-video -f /tmp/kde-rafal/k3bVideoDvd0 
```

---

### Post by dasbooter on 2009-03-02
God help me I have this same problem...for months now. I swear when I first installed intrepid burning worked and then something broke. I have tried two different burners(pain in the but hauling out the other and putting it in this system). I recently installed vmware just to see what nero would say and it coughed up a wrong media error...A dvd I burned on the same dvd burner in a windows system mounts as a cd on this system... I think maybe this is fstab related but I am sure I dont know enough to say for sure. I swear to god my time with windows would be reduced to 5% if I could fix this why does this have to be so hard...Yes yes I know this thread is old but I am frustrated most similar searches on Google etc show exactly this one person asking a question and that is it!

---

