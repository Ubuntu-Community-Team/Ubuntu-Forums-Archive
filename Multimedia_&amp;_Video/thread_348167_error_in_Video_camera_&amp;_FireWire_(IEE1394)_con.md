---
title: "error in Video camera &amp; FireWire (IEE1394) configuring"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by ubunlilluz on 2007-01-28
hi,
i'm trying to import video from my dv camera. i've a firewire port in ati radeon 9200 sound card that in windows worked. Unfortunately kino sees that i kernel module for raw1934 isn't loaded or is wrong so i'm following the guide [http://www.bxlug.be/en/articles/220](http://www.bxlug.be/en/articles/220) found in this forum to solve the problem.
Unfortunately i've this error:

lillux@lilluxoctavius:~$ modprobe video1394
FATAL: Error inserting video1394 (/lib/modules/2.6.17-10-generic/kernel/drivers/ieee1394/video1394.ko): Operation not permitted

anyone can help me
thanks

---

### Post by TKill on 2008-01-30
try putting "sudo" in front of the command:
```
# sudo modprobe video1394
```

---

### Post by linuxfan3 on 2008-03-30
hi,
i had the same problem with the access permission on the raw 1394 device. But When i installed "dvgrab" it worked. Make sure you tried to install "dvgrab" 
now restart Ubuntu and try kino again
hope that helps,
linuxfan

---

