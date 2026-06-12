---
title: "fs-driver refuses to recognize Mandriva partition"
date: 2008-06-22
forum: Mandriva/Mageia
---

### Post by logos34 on 2008-06-22
fs-driver in windows simply refuses to mount ext3 mandriva partitions (wants to 'format' it), even though I can access all the other ext3 linux partitions, primary and logical (so that's not it).  Ran the  'mountdialog.exe' but it either disappears or says it cannot determine the problem.

The drive letter is not the issue.

I tried this on both an 32-bit XP Home machine and on my mine with x64 XP Pro. (it's only temporary for test purposes--no more dual-booting windows!)

---

### Post by AdamWill on 2008-06-23
This is a known issue. Between 2008 and 2008 Spring, upstream ext filesystem developers changed the default inode size for ext3 partitions from 128 bytes to 256 bytes. This is to ease future migration to ext4. So ext3 partitions created with 2008 Spring have 256 byte inodes.

Unfortunately, quite a lot of third party utilities that handle ext2/ext3 partitions cannot cope with 256 byte inodes. You really have three options: get the app developer to update it to handle 256 byte inodes, find another app that does the same that can handle 256 byte inodes, or reinstall Mandriva using 128 byte inode partitions (create them beforehand, manually).

---

### Post by logos34 on 2008-06-23
Thanks for the extremely enlightening response!  Seems that 256 inode change has caused more than a little trouble. (grub too)

>  or reinstall Mandriva using 128 byte inode partitions (create them beforehand, manually).

I'll try that right now.

thanks again, adamwill

---

### Post by logos34 on 2008-06-23
Works perfectly now!

I did:

> ~$ **sudo mkfs.ext3 -I 128 -m 0 -L Mandriva /dev/sda3**
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=Mandriva
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
453376 inodes, 1811328 blocks
0 blocks (0.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1858076672
56 block groups
32768 blocks per group, 32768 fragments per group
8096 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 33 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

Except when you reinstall Mandriva, after designating the partition mount point as '/', you have to be careful on the next screen ('Choose to format') to NOT format (untick the box)--otherwise it would probably reformat it with default 256 bytes inodes.

So now I can access mandriva with fs-driver fine, and I can boot it with any of the grub formats ('configfile,' 'symlink', direct, as well as chainloader).

Thanks a bunch

---

### Post by AdamWill on 2008-06-24
"Except when you reinstall Mandriva, after designating the partition mount point as '/', you have to be careful on the next screen ('Choose to format') to NOT format (untick the box)--otherwise it would probably reformat it with default 256 bytes inodes."

Yup, that's exactly right. Glad you got it sorted out :)

---

