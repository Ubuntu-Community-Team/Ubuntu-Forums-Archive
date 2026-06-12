---
title: "Ubuntu 10.10 not booting."
date: 2010-09-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ksihawk7 on 2010-09-04
Today I upgraded to 10.10, and when it restarted the computer, I get to the version selector thing(Sorry, not sure what it's called), and when I select the one that is 10.10, it goes, but the underscore blinks for a while, then it says "gave up waiting for root device. Common problems include...then says the root may not have waited long enough. Did the system wait for the right root?""

---

### Post by ksihawk7 on 2010-09-05
Anyone?

---

### Post by Sef on 2010-09-05
1) Moved to MMTnD.

2) Please wait until 24 hours have passed before bumping your thread.  Thank you.

---

### Post by VMC on 2010-09-05
> **ksihawk7 said:**
> Today I upgraded to 10.10, and when it restarted the computer, I get to the version selector thing(Sorry, not sure what it's called), and when I select the one that is 10.10, it goes, but the underscore blinks for a while, then it says "gave up waiting for root device. Common problems include...then says the root may not have waited long enough. Did the system wait for the right root?""

That "version selector thing". Do you mean the kernel version coming from gurb2 menu?

If so then type 'e' to edit and write down the UUID, root=info. And come back here with that info. Also type two commands from a linux terminal:

```
sudo blkid
sudo fidsk -l
```

---

### Post by nicpillinger on 2010-10-10
I'm having exactly the same issue, upgraded from 10.04. Can boot up 10.10 with the 2.6.32 kernel but the new kernel results in the same message as above.

Here's the output from blkid and fdisk -l any help appreciated.

nic@nic-ubuntu:~$ sudo blkid
[sudo] password for nic: 
/dev/sda1: UUID="e4e304bf-651e-4d17-8e61-9d2e7bb33810" TYPE="ext4" 
/dev/sda5: UUID="72f9b985-c83e-4646-b3b3-799ad0e5df60" TYPE="swap" 
/dev/sdb1: LABEL="Data" UUID="82BCB646BCB6350F" TYPE="ntfs" 
nic@nic-ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aeec5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150212608   83  Linux
/dev/sda2           18701       19453     6034433    5  Extended
/dev/sda5           18701       19453     6034432   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb14fb14f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19930   160083968    7  HPFS/NTFS

---

### Post by kansasnoob on 2010-10-10
I'd begin by running a few common commands while booted into the older kernel:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

Sometimes the terminal output of those will reveal a problem or provide clues.

It also couldn't hurt to run:

```
sudo update-grub
```

The output of the following commands might also be helpful to us:

```
ls /boot
```

```
cat /boot/grub/grub.cfg
```

Also, I'd expect this sub-forum to be shutting down very soon so we may have to continue this elsewhere.

---

