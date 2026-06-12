---
title: "nfs mount time-out during boot sequence"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by Hawkoon on 2010-10-26
I mount some NFS shares via fstab
```

192.100.100.4:/media/SERVER /media/SERVER nfs rw,addr=192.100.100.4 0 0
```which is working fine at home where I have my wired network, but when I am on the go those NFS shares are not available and it is taking ages to complete the boot sequence.

Is there a way to define a shorter time-out period whilst attempting to mount a non-existing NFS folder?

thanks,
Hawkoon

---

### Post by Hawkoon on 2012-01-08
Seems like that issue got fixed via regular system updates. I run 10.04 and 11.10 and none of them hangs during boot-up any more.

~H

---

