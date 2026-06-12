---
title: "FAT32 External Hard Drive Issues..."
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by jdiehl on 2009-07-11
I have been able to share everything through Samba.  I am struggling with trying to utilize my 500GB Western Digital FAT32 external hard drive.  I have tried every suggestion out there and made some progress and regressed on other fronts.  I now cannot do anything and it is listed as "root" as the owner.  I attempted to enter into Windows to adjust this, but no luck.  

I am desperate!  

This is the one thing holding me back from creating a home network that is usable.  If anyone has any idea or can point me in the right direction please let me know.

Thanks!

---

### Post by EagleG33k on 2009-07-11
I unfortunately have never used samba, so I can't help you if that's the problem.  I have however, just fixed a problem where I wanted to share a FAT32 partition between my dual booting Windows and Ubuntu, so I'll post that here and hopefully it'll at least spark an idea for you to try.

For me - the FAT32 partition showed up fine and dandy under windows, but under ubuntu it was an unmounted drive.  So I added it to /etc/fstab and had it auto mount.  I quickly discovered that this will mount it as root, and that I couldn't write to it as a regular user.  I'm sure there are probably better workarounds, but I set up a small script to mount it as me, and put that in /etc/init.d .  If you want, I can post the whole script, but the important line for mounting is:
```
su -c "mount /dev/your-drive" username
```Which will mount your-drive according to the rules in /etc/fstab as username.

This works fine for me, since I'm a single user environment.  If you wanted to share it among others, you'd pry have to set up a new group, or make it world writable or something along those lines.

Hopefully I've managed to spark an idea that'll get you going.

---

### Post by superprash2003 on 2009-07-11
i dont think fat32 and samba play well together.. if possible do try making it to NTFS

---

### Post by jdiehl on 2009-07-19
Thank you so much for the replies.  Can anyone tell me if it is possible to reconfigure the hard drive to NTFS from FAT32 without losing the files on it?  I have about 250 gig of files on a 500 gig hd.

---

### Post by varun1786 on 2009-07-20
when u change the filesystem from FAT to ntfs you will loose all the data. backitup onto another disk and after conversion restore it. Don think there's any other way

---

