---
title: "Help needed adding pre formatted 2nd hard drive"
date: 2010-10-19
forum: Mythbuntu
---

### Post by rflook on 2010-10-19
Hi there,

A few days ago I updated my mythbuntu system 8.04 to 10.10. While most things worked it seemed to slow my system down to a crawl. No matter i think, as i have two hard drives installed ill just do a fresh install of 9.04 instead. Installation works no problems at all. Problem is that I cant not for the life of me figure out how to get to my second hd.

I have installed gparted and its telling me that its labelled at /dev/sda. So i thought id try the mount command

mount -t ext3 /dev/sda /media/HD2 

but that tells me i have the wrong fs type, so i have tried ext4 and ext2 which throw the same error and fat32 which says unknown filesystem. I tried adding a line to the fstab file 

/dev/sda /media/HD2 defaults 0 0

but that does nowt as well :-( Id be really grateful if someone could help me out here as while the music and videos are easily replaced, the photos not so much.

---

### Post by Lazaruss on 2010-10-19
doesn't gparted tell you what filesystem it is?

---

### Post by rflook on 2010-10-19
Nope it just says msdos, which is weird because it says the same for my main HD :-/

---

### Post by sikander3786 on 2010-10-19
If gparted says simply sda, it is referring to the HDD not the partition. The partition should look like sda**n** where n is the number of partition.

Please post the output of

```
sudo fdisk -l
```

---

### Post by rflook on 2010-10-19
Sorry the msdod part i was talking about was the disklabeltype. Gparted is stating that the filetype is unallocated? Guessing that means that it doesnt think it is formatted? 

Anyways here is the output from fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x670b0cbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1459    11719386   83  Linux
/dev/sdb2            1460       38913   300849255    5  Extended
/dev/sdb5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sdb6            1584       38913   299853193+  83  Linux
root@Mythbox:/home/rflook# 


Theres the bad boy at the top - sda. Does this help?

---

### Post by sikander3786 on 2010-10-19
Unallocated means it doesn't contain any partitions. Create partitions, format them accordingly and it will be ready to go.

---

### Post by rflook on 2010-10-19
Sounds like a grand plan BUT will this cause me to lose any/all data that was on the HD in the first place. This does hold a lot of personal photos to me which are the only copies i have (though that will soon change assuming i can get them back)

---

### Post by oldfred on 2010-10-19
If you had partitions testdisk may find them.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by rflook on 2010-10-20
Ugh this isnt going so well, tried to use testdisk but to no avail, it just cant seem to find any partition. Weird. I know the data is there, i can only assume that something has gone very wrong with my partition table. 

Just to be sure here are the steps i am following with testdisk

1) Choose correct HD (sda)
2) Select analyse
3) Choose quick search
4) It does its thing and returns the msg "No partition found for selected recovery" (for the file type i chose the intel option)
5) Deeper search returns exactly the same message

Really could do with some extra pointers here :-(

---

### Post by rflook on 2010-10-20
OK, i have no idea if this makes any difference but I ran testdisk a 2nd time, and when testdisk asked me what file type i was using i selected the none option. This gave me the following output

Partition     Start          End        Size in sectors
P ext3        0  6  60800    211  17    976764928 [myth]

Though if i try to then view the files using the 'p' option testdisk tells me 

'Cant open file system. Filesystem seems damaged

---

### Post by oldfred on 2010-10-20
Since fdisk will not see it I do not know if you can try repairs.

[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

From liveCD so everything is unmounted ( sudo may not be required from liveCD)
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by rflook on 2010-10-20
Will try that soon, but in the mean time i have left photorec (prog that comes with testdisk) running on the hunt for jpgs, so far it is finding them but incredibly slowly. This is enough to get some of my files back but photorec doesnt have all the file extensions that i need. So the files (at least some of them) are definitely there, its just a case of making the damned hd work/recognised again properly :-(

---

### Post by rflook on 2010-10-20
> **oldfred said:**
> Since fdisk will not see it I do not know if you can try repairs.

[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

From liveCD so everything is unmounted ( sudo may not be required from liveCD)
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

You sir are the greatest. That second line worked an absolute treat and i can now mount my hd - brilliant. So happy and all my files still appear to be there. If i could i would hug you :-D

---

### Post by oldfred on 2010-10-20
Glad we found something that worked. 

It was just a shot in the dark as I was not sure it would 'see' the partition to try to repair it.
Good to know for future users with similar issues.

You can add solved so if someone is searching they may find this thread.

---

