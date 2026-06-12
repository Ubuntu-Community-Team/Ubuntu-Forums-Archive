---
title: "Slow CIFS (Samba) speeds"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by Enigmatic on 2010-05-24
I have a fileserver running Debian, which has worked well for me in the past. I've now upgraded to Ubuntu 10.04, and Samba speeds seem way down. While over FTP I can download at 80MB/s and upload at ~50MB/s, while over a CIFS mount (through fstab) I can only manage about 30 and 15. That seems like far too large of a performance delta, and is really far slower than what should be possible.

Any ideas of where to start? I've tried changing wsize and rsize, but it didn't seem to make much of an improvement, and often resulted in slower speeds.

---

