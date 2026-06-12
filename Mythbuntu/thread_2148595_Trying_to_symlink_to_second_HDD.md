---
title: "Trying to symlink to second HDD"
date: 2013-05-25
forum: Mythbuntu
---

### Post by gga96 on 2013-05-25
I have just completed installing a second HDD to store mythtv media and I have not succeeded with the symlink function.
The mount point for hdd2 is /media/hdd2. I then created /media/hdd2/mythtv with sub-dir livetv.
Eventually I would like to move all media to hdd2 but livetv is the first up test.

The current situation is:
> 
glen@backend-1:~$ sudo fdisk -l
[sudo] password for glen: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005a242

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   304801791   152399872   83  Linux
/dev/sda2       304803838   312580095     3888129    5  Extended
/dev/sda5       304803840   312580095     3888128   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003b2f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   312580095   156289024   83  Linux

Disk /dev/sdd: 128 MB, 128450048 bytes
8 heads, 32 sectors/track, 979 cylinders, total 250879 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5801eea7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              97      250623      125263+   6  FAT16

I then tried to symlink thinking myth will write to hdd2 when watching live tv:
> 
glen@backend-1:~$ ln -s /media/hdd2/mythtv/livetv /var/lib/mythtv/livetv

When playing live tv Myth continues to write files to /var/lib/mythtv/livetv?

What have I done wrong?

I will get the hang of linux one day, thanks for your help.
Glen

---

### Post by bleve on 2013-05-26
You kinda of have it backwards but the real solution is to go into mythtv-setup on the backend and change your recording directories.   I am in the middle of trying to fix something with my setup so I can't see the menus in the mythtv-setup but in there you can setup the directories you are recording to.  In there set livetv to /media/hdd2/livetv and it will start working after you make the setting change.

---

### Post by gga96 on 2013-05-27
> You kinda of have it backwards... 
My reading of ln --h is that "TARGET" refers to the directory being linked to, that is, the destination of the link. The File Manager says that "/var/lib/mythtv/livetv" is of type "link to /media/hdd2/mythtv/livetv", so I think the link aspect is correct. I think the permissions are correct also.

> ...mythtv-setup on the backend and change your recording directories.
I changed the setting of the BE Storage Directories>LiveTV to "link to /media/hdd2/mythtv/livetv" and that worked fine. 
This is not the best option, I would prefer to change the links to [SIZE=2]accommodate [/SIZE]changes rather than shutting down the backend to make the changes there.

Something is not right with what I have done. But What?
Glen

---

### Post by bleve on 2013-05-27
Well it sounds like you want to do the following.  

> 
$ mv /var/lib/mythtv/livetv /var/lib/mythtv/livetv.orig
$ ln -s /media/hdd2/mythtv/livetv /var/lib/mythtv/livetv 


After doing this you should see livetv files in both directories and they will be the same file.  A df should show the space in /media/hdd2 going down as you watch live tv.

---

### Post by newlinux on 2013-05-27
I think you should just use storage groups for this.

[http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)

---

### Post by gga96 on 2013-05-27
Thanks bleve,
Not long with linux but thanks to you the penny has dropped. It was obvious when looking at the output of df.
Glen

---

### Post by gga96 on 2013-05-27
Thanks for your input newlinux.
I will check it out.
Glen

---

