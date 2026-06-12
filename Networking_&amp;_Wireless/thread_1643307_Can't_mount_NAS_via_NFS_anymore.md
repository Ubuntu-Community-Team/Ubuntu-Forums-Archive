---
title: "Can't mount NAS via NFS anymore"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by calande on 2010-12-11
Hello,

I can't mount my NAS anymore using NFS:

> $ sudo mount 192.168.0.13:/volume1/public /home/charles/diskstation/public
mount.nfs: requested NFS version or transport protocol is not supported

Do you know what the cause might be? It's supposed to automount at startup but now it doesn't anymore :(
Thanks,

---

### Post by calande on 2010-12-12
Any idea?

---

### Post by luvshines on 2010-12-12
> **calande said:**
> Any idea?

Though I am not sure, but can it be due to NFS V3 or V4 on the other side ?

---

### Post by calande on 2010-12-12
I didn't change anything, but I tried again, and it's working again...Any idea why this happened? Thanks.

---

### Post by calande on 2010-12-19
Funny... I noticed that if I try to mount my NAS with NFS while the NAS disk is idle, it won't mount, even if the NAS is on and connected, otherwise it will mount as expected :)

---

### Post by luvshines on 2010-12-20
Idle ?

---

### Post by calande on 2010-12-20
Yes, when the NAS is on, but the disk stopped spinning after a period of inactivity.

---

