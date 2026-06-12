---
title: "Aagh. Drive has disappeared?"
date: 2009-11-09
forum: Mythbuntu
---

### Post by SiHa on 2009-11-09
I rebooted my BE server via SSH.

I have a 500GB drive mounted on /var/lib/mythtv for all my recordigs etc.

my fstab:```
mythbox@mythbox-desktop:/backup$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4a5599f5-d409-42b5-a74f-0c689f15d73d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=46107d9b-d161-4a3f-9890-b9db0bdcc924 none            swap    sw              0       0

#/dev/sdb Samsung500GB
#/dev/sdb1 
UUID=13dc6de8-4255-432d-80ad-ebcf048aeaac /var/lib/mythtv            ext3     relatime,errors=remount-ro 0       1
#/dev/sdb2
UUID=f8ec4154-05f2-4183-a9ca-bf71f630360c /backup                    ext3     relatime,errors=remount-ro 0       1

```


Except it's not mounted.```
sudo mount -a
/dev/sdb1 already mounted or /var/lib/mythtv busy
```

Edit: They've come back now. Bit of a worry, any idea why it was doing this?

---

### Post by gwagchunks on 2009-11-11
Hi SiHa

I had a similar problem with my external 1TB hard drive. It's defined in fstab and works fine. BUT if I boot up and the usb cable has fallen out or not powered on it will not show. When I plug it back in and try and access it, I get some sort of permissions error. I found I had to remove the entry from fstab, save it, shut down, make sure the drive is plugged in and powered up and then add the line back to the fstab. Then when I reboot all is good.

---

### Post by SiHa on 2009-11-11
Thanks, I'll bear that in mind if it happens again. Although this is with an internal SATA drive. The new one, it's only about 2 months old!

It was very odd. At first I was getting the 'already mounted or busy' error. Then after messing around a bit, I tried to mount it and was told that /var/lib/mythtv was already mounted, and it was.

I did have my old frontend powered up at the time and networked (to copy off a few configuration files). It has some nfs shares mounted on subdirectories of this mountpoint. I'm hoping it was this causing the problems. Fingers crossed it doesn't happen again.

---

