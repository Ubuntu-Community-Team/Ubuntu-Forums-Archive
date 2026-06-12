---
title: "network share"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by windowsfree on 2009-10-21
How can I mount a Windows share on the network automatically when my PC boots up.  I am using Ubuntu 9.04, the windows is XP media center.  I don't want to have to go to networks, then the network, then the share to mount.  I would like to map it like windows does it with its networking.

---

### Post by windowsfree on 2009-10-21
How can I mount a Windows share on the network automatically when my PC boots up. I am using Ubuntu 9.04, the windows is XP media center. I don't want to have to go to networks, then the network, then the share to mount. I would like to map it like windows does it with its networking.

---

### Post by swerdna on 2009-10-21
Hi Bob

Put a mount command line in the file fstab located at /etc/fstab, like this:```
//server_name/share_name   /path_to/mount_point   cifs   password=,_netdev   0 0
```

---

### Post by swerdna on 2009-10-21
It's bad netiquette to post the same question multiple times.

Try the answer on your other thread: [http://ubuntuforums.org/showthread.php?p=8141487#post8141487](http://ubuntuforums.org/showthread.php?p=8141487#post8141487)

---

### Post by Iowan on 2009-10-21
That pretty much covers it... but for some in-depth treatment, see [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To.

---

### Post by cariboo on 2009-10-21
Please don't double post, I have merged your two threads.

---

