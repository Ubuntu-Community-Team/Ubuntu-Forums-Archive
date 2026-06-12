---
title: "can't figure out how to share mounted hard drive"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2009-12-15
I figured out how to automatically mount a secondary IDE hard drive that had been previously formatted with NTFS by adding this line to the /etc/fstab file:

```
/dev/sdb1  /mnt/media_drive  ntfs auto  0  0
```

Now I can't figure out how to share that directory (drive) with the other computers on my network. One of those computers is running Ubuntu and the other one is running WindozeXP, so I figured I need to run samba. To simplify things, I just right clicked on the folder in Nautilus and selected the 'Share This Folder' option. It complained that only root could do that. 

I tried using

```
sudo chmod -R derek:derek /mnt/media_drive
```

to change the owner of that folder from root to myself. That didn't work. The owner and group are still reported as root. I even unmounted that drive, deleted the mount point and recreated the directory, verifying that the folder had derek as both owner and group. When I rebooted and the drive remounted, the folder was once again branded as root.

I ran Nautilus as root (sudo Nautilus from terminal) and shared the folder that way, but I wasn't sure that was a good idea, so I unselected that for the time being. 

Can someone tell me what I need to do to insure that this folder can be read and written to from all computers by all users?

Thanks...

---

### Post by oldfred on 2009-12-15
Ownership on Fat & NTFS do not mean anything since they do not support it.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by dmizer on 2009-12-16
Take a look here: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/971582.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/971582.html)

---

### Post by rebeltaz on 2009-12-17
I added uid=derek,gid=derek to /etc/fstab and it worked great. Thank you.

---

