---
title: "device id for sshfs device"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by TeleSG on 2008-12-06
Hello, all!  This is my first post.  I've been an Ubuntu user for about 5 months. Thanks to the Ubuntu community for having already answered all my questions on these forums up to this point. My question is: 

I've got an external hard drive attached to my iMac on which I've created a partition for backing up my Intrepid system.  I've got said partition mounted on my Intrepid system via sshfs.  How to I discover the device id of the drive, i.e. it's file in /dev when mounted in this manner?

Thanks!

---

### Post by jmoorse on 2008-12-07
cat /proc/mounts should do the trick

---

