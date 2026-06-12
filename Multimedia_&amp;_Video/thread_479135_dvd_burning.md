---
title: "dvd burning"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by rickycodie on 2007-06-20
i am tring to burn a .avi to a dvd to be watched on a dvd player. i am tring to use gnome baker and k3b and neither can do it. 

here is the output
mkisofs
-----------------------
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-ricky/k3bVideoDvd0/'.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-ricky/k3bVideoDvd0/'.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Apocalypto[2006]DvDrip[Eng.Hard. -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-ricky/k3bgUbd6a.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-ricky/k3bSgGr7b.tmp -dvd-video -f /tmp/kde-ricky/k3bVideoDvd0 


any ideas?

output is from k3b. gnomebaker i just can't figure out.

---

### Post by cchester on 2007-06-20
Hi,

Try and get Mandvd I used it for just such a thing and when it finishes it will let you burn the dvd with K3B.

---

