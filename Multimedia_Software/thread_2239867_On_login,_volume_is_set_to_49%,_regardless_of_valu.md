---
title: "On login, volume is set to 49%, regardless of value saved"
date: 2014-08-16
forum: Multimedia Software
---

### Post by scholz-thispla on 2014-08-16
On every login, the master volume is set to 49%, regardless of the value saved.  In fact, during login, the volume has the correct (i.e., saved) value, which I can verify by opening the speaker symbol in the bar on the lower right.  Then, at the end of the login process, the volume jumps to 49%.

So, it's not that the correct volume is not saved. Neither that it is not correctly restored. Some mechanism overwrites the correct value in some step.

Can anyone shed light on this issue? 


I'm always using the latest updates.

scholz@Herzberg:~$ uname -a
Linux Herzberg 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:49:09 UTC 2014 i686 athlon i686 GNU/Linux

scholz@Herzberg:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"

---

