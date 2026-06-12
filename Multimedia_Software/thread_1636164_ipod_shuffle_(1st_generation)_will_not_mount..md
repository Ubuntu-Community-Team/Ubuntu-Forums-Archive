---
title: "ipod shuffle (1st generation) will not mount."
date: 2010-12-02
forum: Multimedia Software
---

### Post by Chris2691 on 2010-12-02
My ipod shuffle (1st generation) will not mount in Ubuntu 10.10 64 bit when I plug it into my usb port. 
When I plug in the ipod I do not get an icon being created for it on the desktop.
I have also checked nautilus and there is no storage device for the ipod showing when I click on computer in nautilus.
I have also checked /media in nautilus and there in no listing for the ipod.
The only way I can see the ipod in Ubuntu is if I open up a terminal window and use the command lsusb which then shows a listing for the ipod.
If I have the ipod plugged into my computer before I turn it on and then turn  on the computer to boot with Ubuntu, Ubuntu does not boot in the normal graphics mode but boots in text mode where I have to type in my name and password on a black terminal screen.
The ipod has the latest software on it as well as being reset back to original factory settings.
I have no problems using the ipod if boot up on windows 7 and plug in the ipod.

Any help will be greatly appreciated.

---

### Post by FreshP on 2010-12-15
I have the same problem with my Ubuntu 10.10. It worked fine in 9.10. Any solution to this problem?

---

### Post by FreshP on 2010-12-22
Ahhhh, still no solution to this ;-< Nobody else has the same problem?

---

### Post by FreshP on 2010-12-22
Finally, I managed to mount it manually like this

```

sudo mount -t vfat /dev/sdb1 /media/IPOD

```

I dont understand why it's not automatically mounted when plugged in.

---

### Post by netwerkingnut on 2011-04-29
I'm using Ubuntu 10.04 LTS the Lucid Lynx rel. 2010 April and I tried the command line describe in the previous post, but all I get is "mount: mount point /media/IPOD does not exist" I've been reading as much as I can to figure it out, but I'm just going in circles. Does anyone have another command I can try?

---

### Post by CdeSousaG on 2011-05-08
> **netwerkingnut said:**
> I'm using Ubuntu 10.04 LTS the Lucid Lynx rel. 2010 April and I tried the command line describe in the previous post, but all I get is "mount: mount point /media/IPOD does not exist" I've been reading as much as I can to figure it out, but I'm just going in circles. Does anyone have another command I can try?

First you have to create the folder where the Ipod will be mounter
 ```
$ sudo mkdir /media/IPod
```

Then you need to know the Ipod disk id. This will list all disks and you need to identify the Ipod (look at the sizes)
 ```
$ sudo fdisk -l 
```

In my case I have a 1GB Ipod and its info looked like

```
Disk /dev/sdd: 1040 MB, 1040711680 bytes
128 heads, 40 sectors/track, 397 cylinders
Units = cylinders of 5120 * 512 = 2621440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb86b5dee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         397     1016300    b  W95 FAT32
```

Then mount
```
$ sudo mount -t vfat /dev/sdd1 /media/IPod
```

---

### Post by Hat FM on 2011-08-25
> **Chris2691 said:**
> My ipod shuffle (1st generation) will not mount in Ubuntu 10.10 64 bit when I plug it into my usb port. 
When I plug in the ipod I do not get an icon being created for it on the desktop.
I have also checked nautilus and there is no storage device for the ipod showing when I click on computer in nautilus.
I have also checked /media in nautilus and there in no listing for the ipod.
The only way I can see the ipod in Ubuntu is if I open up a terminal window and use the command lsusb which then shows a listing for the ipod.
If I have the ipod plugged into my computer before I turn it on and then turn  on the computer to boot with Ubuntu, Ubuntu does not boot in the normal graphics mode but boots in text mode where I have to type in my name and password on a black terminal screen.
The ipod has the latest software on it as well as being reset back to original factory settings.
I have no problems using the ipod if boot up on windows 7 and plug in the ipod.

Any help will be greatly appreciated.


Hey Chirs, did you even solve this problem?

Because that is word for word, the same thing that's happening to me.
Including the starting up in text mode when shuffle is attached.

Cheers

---

### Post by madsector on 2011-10-16
Have you tried this? 

[https://bbs.archlinux.org/viewtopic.php?pid=823786](https://bbs.archlinux.org/viewtopic.php?pid=823786) 

Especially post 5 helped me to get my Ipod Shuffle (1. generation) to mount automatically. Here is the bugreport in this:

[https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/565971](https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/565971)

---

