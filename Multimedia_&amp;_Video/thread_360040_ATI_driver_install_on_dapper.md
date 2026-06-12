---
title: "ATI driver install on dapper"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by eradicator_006 on 2007-02-12
I'm trying to install the latest ATI drivers from ati.com and am having some difficulties.  First off, I'm running a vanilla 2.6.19.3 kernel.  I followed the guide at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and when I do a 'm-a build,install fglrx --kernel-dir /usr/src/linux-2.6.19.3-k7-0559-12022007' it fails and the last few lines in the log view are:

KERNEL_PATH=/usr/src/linux-2.6.19.3-k7-0559-12022007 uname_r= ./make.sh -- x  
x /bin/sh: ./make.sh: Permission denied                                      x  
x make: *** [build] Error 126  

I can manually run sh ./make.sh fine.

lspci output:

0000:02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]

---

