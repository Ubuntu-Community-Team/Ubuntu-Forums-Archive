---
title: "Samba Share Requires Unmount/Remount After Restart"
date: 2011-08-04
forum: Networking &amp; Wireless
---

### Post by prcm311 on 2011-08-04
All,

I recently built a computer for a friend that is only going to be used to run a network share.  

The problem I am running into is that whenever the computer restarts the share, while visible, cannot be accessed by the two Windows 7 laptops in the house.  

If I run 'sudo umount /media/storage' followed by 'sudo mount /dev/sda1 /media/storage' the once visible but inaccessible share is now accessible.  

I do not understand why this would be.  Any ideas?  I have added the line 'usershare owner only = false' to my smb.conf file.

---

### Post by prcm311 on 2011-08-08
*BUMP*

I hate to post twice but I am still in need of a solution for this.  If it is in the wrong section could someone direct me to the correct section for a question like this?

I am still working on this.  I recently update samba and replaced my old config file with a default version.  I only added the line "usershare owner only = false" to the config.  I created a new folder /media/storage as the default user, chmod-ed it to 777, and edited fstab to point to the new folder.  Still on a reboot the share is inaccessible from a windows machine (haven't tried another ubuntu machine) unless I umount and mount the drive.

I find this to be very strange because I have done these steps on other machines without an issue.

Is it possible that this is an issue with the way fstab mounts the drive initially and when I run "sudo mount..." I am actually mounting the drive with different options?

Any help is appreciated.

---

### Post by prcm311 on 2011-08-08
More info:

**_On boot (pre-remount):_**
4 drwxrwx--- 1 root plugdev 4096 2011-08-08 20:35 **storage**


**_After remount:_**
4 drwxrwxrwx 1 root root 4096 2011-08-08 20:35 **storage**

Seems like I would want rw privileges initially.  The question is how?

---

