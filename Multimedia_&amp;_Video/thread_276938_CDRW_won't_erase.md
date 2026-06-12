---
title: "CDRW won't erase"
date: 2006-10-13
forum: Multimedia &amp; Video
---

### Post by quyne on 2006-10-13
Hi,
I have no problems burning to cdrw or any other problems, but I always get this output when trying to erase a cdrw.
The disk drive is not even flashing the light to show it's being accessed/read,
however I can open the cd from nautilus and it shows all the rw contents with no problems.

Have you any advice?
Maybe I should install some other rpm of k3b...

Thanks!

---

### Post by klytu on 2006-10-14
> **quyne said:**
> Hi,
I have no problems burning to cdrw or any other problems, but I always get this output when trying to erase a cdrw.
The disk drive is not even flashing the light to show it's being accessed/read,
however I can open the cd from nautilus and it shows all the rw contents with no problems.

Have you any advice?
Maybe I should install some other rpm of k3b...

Thanks!

Try unmounting the CD-RW 

```
sudo umount /dev/hdb
```

and then blanking it with K3B.

---

