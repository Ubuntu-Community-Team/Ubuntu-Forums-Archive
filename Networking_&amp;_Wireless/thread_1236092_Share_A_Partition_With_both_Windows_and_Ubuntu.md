---
title: "Share A Partition With both Windows and Ubuntu"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by Jaesin on 2009-08-09
I need to share a partition on a second harddrive with my wifes Vista laptop and my Ubuntu desktop.  Im dual booting with 9.04 and windows 7.  I have it set in Windows, but I'm not sure how to get windows to see it when i boot into Jaunty.

---

### Post by aysiu on 2009-08-10
Format the partition on the second hard drive (is it external?) to FAT32.

---

### Post by Jaesin on 2009-08-11
no it is an internal IDE.  I have no problem with adding things to it, just getting windows to see it when im in linux.  I think i have to find more on Samba.

---

### Post by ForMar on 2009-08-11
Well i dont know what you have tried but one thing that you might be missing is the windows partition in fstab. edit fstab add the partition and make sure you give it a "home" such as /mnt/windows
or something of that nature. Another thing you might need to change is the permissions of the files through linux. unfortunately windows partitions dont support that so you need to change the fstab entry to include under options *umask=000*

Good luck and i hope this helps

---

### Post by Jaesin on 2009-08-11
Will fstab help windows see that partition when linux is running?  Because when I boot into Windows 7 everything is as it should be, but when I am not, for some reason the second computer on the network will not see my desktop at all.

Basically I am trying to create an internal network accessible storage drive so I can put avi files on it and have my wife's laptop running Vista access it.

As it stands, the only way to get the laptop to see the drive is to boot into Windows 7.

---

### Post by ForMar on 2009-08-11
I just wrote a huge expiation for a problem you already ruled out. So you said that you dont have problems adding stuff to the partition? If so how have you mounted the drive?

---

### Post by Jaesin on 2009-08-13
/mnt/shared

like i said, it has shared permissions and my computer can access it no matter what, it is my wife's laptop running vista that has the problem.

maybe i need a windows forum, as ubuntu is not the problem vista is.

---

