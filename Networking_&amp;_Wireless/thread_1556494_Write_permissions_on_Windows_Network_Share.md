---
title: "Write permissions on Windows Network Share"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by ljzmcm on 2010-08-19
Hi all,

I was able to successfully mount a Windows Network Share (after joining domain with likewise-open).

Here's what my fstab looks like:

----------------------------------------

//psr_nts2/dp1 /media/dp1 cifs rw,_netdev,user=<USERNAME>,password=<PASSWORD>,uid=1000,gid=100 0 0

----------------------------------------

with of course <USERNAME> and <PASSWORD> filled out respectively. They mount just fine like that. 


it's set to rw, but still it is read-only. Any idea how to circumvent this?

I tried using this:

----------------------------------------
//psr_nts2/dp1 /media/dataprocessing smbfs iocharset=utf8,credentials=/home/likewise-open/PSR_GROUP/<USERNAME>/.smbcredentials,uid=1000 0 0
----------------------------------------

from another tutorial with the .smbcredentials file filled out correctly, but that fails to even mount.

Any help is appreciated!

---

### Post by ljzmcm on 2010-08-19
shameless bump - anyone?

---

### Post by nulldozer on 2010-08-20
Not the best solution, but it should work for now
```
//psr_nts2/dp1 /media/dp1 cifs rw,_netdev,user=<USERNAME>,password=<PASSWORD>,uid=1000,gid=100,**noperm** 0 0
```

---

