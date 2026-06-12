---
title: "How Do I Mount My Media Folder?"
date: 2013-02-27
forum: Multimedia Software
---

### Post by Taurus MC on 2013-02-27
Not sure about what forum this belongs in, so please relocate if it isn't.

My dad recently upgraded Ubuntu Linux of 11.04 to 12.10 and we had a few issues regarding after we had to re-install since we couldn't boot up properly. As it may seem we have a 247 GB and a 63 GB which is mainly we're trying to have everything on the 247 GB moved over to our new solution of folfders awaiting to be filled. But, there seems to be an issue with this.
Yesterday while we were preparing to install, a few question came up asking if should try to force to I believe 'unmount' or 'mount' certain files or continue because it wouldn't delete, create or resize if we said yes. So we went with no and now we can't open these files. Everything on the 247 I believe are photos, downloads, music, etc. The 63 bit just has my dads business stuff and when I tried clicking on them I got this error.

"Unable to mount 63 GB Volume"
Adding read ACL for uid 1000 to '/media/ken' failed: Operation not supported.

This was also the same message we received for the 247 GB Volume.

Please help in any way and if we can repair this manually? Because all my photos that I uploaded from my digital are on here and a majority of them are, well not on my camera itself any more. Besides, it's other information for our business that we need. Please help and Thank You!

---

### Post by kevdog on 2013-02-27
You'd have to give more infomation -- is the media folder supposed to represent a separate parition or usb stick or some other type of media?  How is this formatted -- fat32, ntfs, ext3/4?

---

### Post by Morbius1 on 2013-02-27
Gnome is over thinking the plumbing again and managed to plug up the drain. Anywho, it's a bug: [https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1048059](https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1048059)

It should be fixed so update your system and see if it goes away. If not take things into your own hands:

Create a /media/ken directory:
```
sudo mkdir /media/ken
```Then take possession of the "ken" directory:
```
sudo chown ken:ken /media/ken
```

---

