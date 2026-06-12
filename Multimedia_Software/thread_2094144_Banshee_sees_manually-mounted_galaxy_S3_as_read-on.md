---
title: "Banshee sees manually-mounted galaxy S3 as read-only"
date: 2012-12-12
forum: Multimedia Software
---

### Post by patmalcolm91 on 2012-12-12
Hello,

I am trying to get banshee to sync wirelessly with my galaxy s3, since MTP support for the s3 is terrible in linux and my sd card reader has recently stopped working.

I'm using sshfs to mount the phone's external SD card. I have to mount the phone to a blank USB drive to force Banshee to detect the device. This works (albeit slowly), and Banshee can see the device and the music stored on it.

The line in /etc/fstab is: "sshfs#root@x.x.x.x:/storage/extSdCard /media/CRUZER/ fuse user,allow_other,port=2222" where "x.x.x.x" is my phone's IP address and CRUZER is the name of the flash drive that acts as a "proxy" to the phone. I then mount using "mount /media/CRUZER" 

My problem is that the "Sync with Music Library" option for the device is no longer present in the right-click menu. I've manually set the mount directory permissions so all users have rwx access, but it still doesn't work. I can move files onto the phone using nautilus just fine, so I do actually have write access to the phone.


Any ideas why Banshee still thinks it's read-only?

Thanks

---

