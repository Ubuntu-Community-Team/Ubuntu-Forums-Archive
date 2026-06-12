---
title: "K3B problem burning Blu-Ray"
date: 2011-06-15
forum: Multimedia Software
---

### Post by Corn Flake on 2011-06-15
I'm just getting started burning data Blu-Ray discs.  I've burned two, and both times, K3B stops at 99% with the error "Fatal error during recording: Input/Output error".  Debug shows these at the end:
```

<SNIP>
 99.98% done, estimate finish Wed Jun 15 17:43:57 2011
 99.99% done, estimate finish Wed Jun 15 17:43:57 2011
 99.99% done, estimate finish Wed Jun 15 17:43:58 2011
100.00% done, estimate finish Wed Jun 15 17:43:58 2011
Total translation table size: 0
Total rockridge attributes bytes: 21961
Total directory bytes: 61222
Path table size(bytes): 662
Max brk space used 33000
11729514 extents written (22909 MB)

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Gerardo Home Videos -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-gerardo/k3bjI2683.tmp -rational-rock -hide-list /tmp/kde-gerardo/k3bgs2683.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-gerardo/k3bVY2683.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-gerardo/k3bKA2683.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Gerardo Home Videos -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-gerardo/k3bOD2683.tmp -rational-rock -hide-list /tmp/kde-gerardo/k3bId2683.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-gerardo/k3bfq2683.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-gerardo/k3bqu2683.tmp

```

This makes me think that the burning was successful, despite the error.  The files seem to be there.  How can I verify that everything was burned properly?  Any help will be appreciated.

---

