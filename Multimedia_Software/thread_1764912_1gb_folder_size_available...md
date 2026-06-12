---
title: "1gb folder size available.."
date: 2011-05-22
forum: Multimedia Software
---

### Post by backitdownnow on 2011-05-22
I don't really know where to post this, so bear with me as i find my way around the forums please.

I went to go put my music into my music folder, but i only have 1gb free space. I have looked at the properties, but no luck finding anything out. Anyone know why it is only allowing me to have 1gb? I have a 500gb hard drive, and 140 allocated to ubuntu.

---

### Post by ajgreeny on 2011-05-22
Can we see the output of ```
df -hT
```in terminal please.  It will show the size of partitions, the current use and available space.

---

### Post by backitdownnow on 2011-05-22
tj@ubuntu:~$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/loop0    ext4     17G   15G  947M  94% /
none      devtmpfs    1.5G  672K  1.5G   1% /dev
none         tmpfs    1.5G  420K  1.5G   1% /dev/shm
none         tmpfs    1.5G  100K  1.5G   1% /var/run
none         tmpfs    1.5G     0  1.5G   0% /var/lock
/dev/sda3  fuseblk    148G   18G  130G  12% /host
/dev/sr0   iso9660    686M  686M     0 100% /media/Ubuntu 11.04 i386
/dev/sda2  fuseblk    149G   49G  100G  33% /media/664CE6134CE5DDB5
/dev/sda1  fuseblk    100M   25M   76M  25% /media/System Reserved
tj@ubuntu:~$ ^C
tj@ubuntu:~$

---

### Post by ajgreeny on 2011-05-22
I am confused!!  Are you running that command from a live CD/USB?  That is how it appears to be according to your output.

Are you sure you actually installed ubuntu to a hard disk?  Can you now show the output please of ```
sudo fdisk -l
```(lower case L at the end) either from a live version or a hard disk install, both will give the info I'm looking for.

---

### Post by backitdownnow on 2011-05-22
> **ajgreeny said:**
> I am confused!!  Are you running that command from a live CD/USB?  That is how it appears to be according to your output.

Are you sure you actually installed ubuntu to a hard disk?  Can you now show the output please of ```
sudo fdisk -l
```(lower case L at the end) either from a live version or a hard disk install, both will give the info I'm looking for.


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       19348   155305984    7  HPFS/NTFS
/dev/sda3           19348       38539   154152960    7  HPFS/NTFS
tj@ubuntu:~$ 


I have it installed on my computer, as when i go to boot i have either the chance to boot unbuntu, or windows 7...

---

### Post by SecretCode on 2011-05-22
> **backitdownnow said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       19348   155305984    7  HPFS/NTFS
/dev/sda3           19348       38539   154152960    7  HPFS/NTFS
tj@ubuntu:~$ 


I have it installed on my computer, as when i go to boot i have either the chance to boot unbuntu, or windows 7...

Given the above, you have installed it using WUBI, where the Ubuntu "disk" is a file inside the windows drive. From your previous post, it looks like it's only 17GB. Which is fine for the OS of an Ubuntu install, but you'll need to keep music etc on another partition. You can perfectly well leave it where it is in the windows file system and access it from Ubuntu.

Did you mean to install it that way?

---

### Post by oldfred on 2011-05-22
Wubi is not a full partitioned install. It is just a file running inside a windows NTFS partition to give you an extended test on whether you like Ubuntu or not. It is easy then to uninstall as you can just delete the file or uninstall like a windows program (which it is not).

wubi has limits on how large it can be:
Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

