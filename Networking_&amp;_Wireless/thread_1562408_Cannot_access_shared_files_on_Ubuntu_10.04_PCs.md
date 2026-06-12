---
title: "Cannot access shared files on Ubuntu 10.04 PCs"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by hookzilla on 2010-08-27
I've searched the forums, but have not found this particular issue.  I'm having a file sharing problem on my home network since installing Ubuntu 10.04.  My network has 4 PCs, 2 - Win XP, 2 - Ubuntu 10.04.  I can access the shared files on the WinXP PCs from any PC.  I cannot access the shared files on the Ubuntu PCs from any PC, except that each PC can access its own files.  ie. One Ubuntu PC can access files on the WinXP PCs but not on the other Ubuntu PC.  The folders are displayed, but cannot be accessed. I have checked to be sure the work groups are the same on each PC.  I have verified that of the intended folders is correctly marked for sharing. I don't know where to look next. Thanks in advance for any suggestions/

---

### Post by gdonwallace on 2010-08-27
My first thought would be, do you have samba installed on the Ubuntu boxes.  Also you might want to check the share names, they can only be so long before windows will not recognize them.  When checking the share information on the folder, be sure to check the guest box for guest access.  Don't know if this will actually change anything, but I did it on one machine I have and it seemed to fix the problem.

Also check the permissions on the folders and files in the share.  That could be part of the problem.

---

