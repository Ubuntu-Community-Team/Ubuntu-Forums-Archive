---
title: "Help Needed Badly - Read-only file system!"
date: 2009-03-03
forum: Mythbuntu
---

### Post by jMon54 on 2009-03-03
In trying to resolve an issue I had with my DVD drive asking for superuser in order to mount I now find myself unable to start MythBuntu.  I am seeing a lot of errors relating to read-only file system.  How can I set the permissions back to what they should be?  How can I unlock folders such as TMP?

---

### Post by theophile on 2009-03-04
Sounds like they're being mounted read-only. Were you messing around with /etc/fstab ?

---

### Post by jMon54 on 2009-03-04
I did alter the line for the dvd drive from auto to noauto but it worked after that.  That was a good idea you had about checking fstab though.  I was hoping to find a typo or some obvious error there but it looks good: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=82b57c28-02df-49a0-846a-fe2a60bd96f0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=318023f3-935d-44b0-988e-e39af70bf9a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by jMon54 on 2009-03-04
I noticed something last time I tried to start my system.  It seems my hard drive is not being mounted.  The error I get is that only root can do that.  Something is missing here.  Can someone help me out on where I can make a change to get drive mounted at start-up?

---

### Post by mathog on 2009-03-04
> **jMon54 said:**
> In trying to resolve an issue I had with my DVD drive asking for superuser in order to mount I now find myself unable to start MythBuntu.  I am seeing a lot of errors relating to read-only file system.  How can I set the permissions back to what they should be?  How can I unlock folders such as TMP?

Before doing anything drastic, perhaps you should boot with Knoppix (or an equivalent) and run an e2fsck (assuming you have an e2fs/e3fs file system) on your unmounted root partition.  If that's clean then you can mount the partition r/w using that distro, modify /etc/fstab, and then try too boot mythbuntu again.

---

### Post by jMon54 on 2009-03-04
I have solved this problem.  I had changed the permissions on /bin/mount and /bin/umount in an effort to fix a problem I had moutning DVDs.  Using a live CD, I checked the permissions and compared with another desktop install I have of Ubuntu and noted that root was not the owner so I changed that and I was able to get to the login screen... Yay!  Unfortunately, I had had my system logging me automatically and now it's back to this screen where it does not take my password and I am forced to go to the console to get into Mythbuntu.

---

### Post by nickrout on 2009-03-04
at the console can you log in? If so you can change the password with the passwd command.

---

### Post by Ptero-4 on 2009-03-04
Have you tried doing a disk check ("sudo fsck -t ext3" in your case) in your "/" partition from the liveCD. Linux tend to mount partitions read-only if they have been improperly unmounted (probably the PC was taken off by a power outage, or it just crashed).

---

### Post by jMon54 on 2009-03-04
I'm way overdue for a re-install.  I've been keeping this thing going with tweaks and fixes for too long.  Had it near perfect.  But sometimes a fresh install is the best medicine.  I only hope I can get my remote working again (it took me a while) and that I can figure out how to copy my recordings schedules and videos over.

Thanks everyone!

---

