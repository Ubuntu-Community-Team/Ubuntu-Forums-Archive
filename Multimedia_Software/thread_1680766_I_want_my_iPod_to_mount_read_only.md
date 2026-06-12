---
title: "I want my iPod to mount read only"
date: 2011-02-03
forum: Multimedia Software
---

### Post by thompson20 on 2011-02-03
Hello,
I want my iPod to automatically mount as read only. I am hoping this will prevent Rhythmbox from changing my playlist sort order while still allowing me to listen to my music.

I've tried a number of things this morning and never got it working properly. I'll try to remember what I tried:

gksu gedit fstab
I added UUID=5EFC-9810 /media/ipod vfat ro,noexec,noauto,user 0 0

cd /media
sudo mkdir ipod

Mounted the iPod and it showed up twice in Places (possibly as a result of this bug: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130)). Also, the directory iPod was always listed in Places even when I hadn't connected my iPod. So I listened to the advice there and tried:

/dev/disk/by-uuid/5EFC-9810 /media/ipod vfat ro,noexec,noauto 0 0

Now I couldn't get my iPod to mount at all. The error given was something like:
Error mounting: mount exited with exit code 1...only root can mount media/ipod

I was able to chown /ipod but it didn't solve my problem.

I started over and tried:
UUID=5EFC-9810 /media/ipod vfat ro 0 0

This time the iPod directory was only shown once, but I got the same "Error mounting..." message.

Any ideas?

---

### Post by matt_symes on 2011-02-03
Hi

```
/dev/disk/by-uuid/5EFC-9810 /media/ipod vfat ro,noexec,noauto 0 0
```

Interesting bug. I have not come across that one before. What about adding user as below.

```
/dev/disk/by-uuid/5EFC-9810 /media/ipod vfat ro,noexec,noauto,user 0 0
```

Kind regards

---

### Post by thompson20 on 2011-02-03
Perfect. Thank you very much.

---

### Post by thompson20 on 2011-02-03
Okay...this may be off topic now, but the iPod directory is still showing up in my Places menu after a reboot. Any idea how I can stop that from happening?

---

