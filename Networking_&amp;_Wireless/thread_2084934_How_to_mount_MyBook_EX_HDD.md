---
title: "How to mount MyBook EX HDD"
date: 2012-11-16
forum: Networking &amp; Wireless
---

### Post by BStrizzy on 2012-11-16
Hey guys, I am running Ubuntu 10.04 on a headless unit and using ssh shell to communicate with it on my ubuntu desktop. I am trying to mount my  new 2tb to this server and not sure how to do it.

Good news is, it does reconize the harddrive i mounted when i do lsub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

wht to do next?
THANKSS!

---

### Post by papibe on 2012-11-17
Hi BStrizzy.

Here are a couple of way you can try:

1. Disconnecting the disk, wait a few seconds, connecting it again, and checking the dmesg and syslog:
```
dmesg | tail

tail /var/log/syslog
```
2. Once is connected and recognized, check this directories:
```
/dev/disk/by-id/

/dev/disk/by-label/
```
There, there should be symlinks to the actual devices.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by BStrizzy on 2012-11-19
ata-Maxtor_6L100P0_L24AMJTG
ata-Maxtor_6L100P0_L24AMJTG-part1
ata-Maxtor_6L100P0_L24AMJTG-part2
ata-Maxtor_6L100P0_L24AMJTG-part5
scsi-SATA_Maxtor_6L100P0_L24AMJTG
scsi-SATA_Maxtor_6L100P0_L24AMJTG-part1
scsi-SATA_Maxtor_6L100P0_L24AMJTG-part2
scsi-SATA_Maxtor_6L100P0_L24AMJTG-part5
usb-WD_My_Book_1140_574D415A4138303032313332-0:0
usb-WD_My_Book_1140_574D415A4138303032313332-0:0-part1


this is what I got when i ran the code 
bstrizzy@nova:~$ cd /dev/disk/by-id/
bstrizzy@nova:/dev/disk/by-id$ ls


how do i actually mount it so i can store even more files on it?

---

### Post by papibe on 2012-11-19
Try listing using the long option:
```
ls -l /dev/disk/by-id/
```
That should display the actual device they are linked to.

Regards.

---

### Post by BStrizzy on 2012-11-19
> **papibe said:**
> Try listing using the long option:
```
ls -l /dev/disk/by-id/
```That should display the actual device they are linked to.

Regards.
[SIZE=2]

bstrizzy@nova:~$ ls -l /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root  9 2012-11-16 20:44 ata-Maxtor_6L100P0_L24AMJTG -> ../../sda
lrwxrwxrwx 1 root root 10 2012-11-16 20:44 ata-Maxtor_6L100P0_L24AMJTG-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2012-11-16 20:45 ata-Maxtor_6L100P0_L24AMJTG-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2012-11-16 20:44 ata-Maxtor_6L100P0_L24AMJTG-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 2012-11-16 20:44 scsi-SATA_Maxtor_6L100P0_L24AMJTG -> ../../sda
lrwxrwxrwx 1 root root 10 2012-11-16 20:44 scsi-SATA_Maxtor_6L100P0_L24AMJTG-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2012-11-16 20:45 scsi-SATA_Maxtor_6L100P0_L24AMJTG-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2012-11-16 20:44 scsi-SATA_Maxtor_6L100P0_L24AMJTG-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 2012-11-16 20:44 usb-WD_My_Book_1140_574D415A4138303032313332-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2012-11-16 20:44 usb-WD_My_Book_1140_574D415A4138303032313332-0:0-part1 -> ../../sdb1
[/SIZE]

I am a newb at linux server so , not sure what anyof this. I am just trying to mount the external to add extra memory to the server its self.

---

### Post by papibe on 2012-11-19
```
usb-WD_My_Book_1140_574D415A4138303032313332-0:0 -> ../../sdb

usb-WD_My_Book_1140_574D415A4138303032313332-0:0-part1 -> ../../sdb1
```
There you go.

Your disk was assigned to the device /dev/sdb and the useful partition is on /dev/sdb1

To mount the disk you need to create a mount point first (a directory):
```
sudo mkdir /media/MyBook
```
Then you can mount the disk like this:
```
sudo mount -t ntfs /dev/sdb1 /media/MyBook
```
Let us know how it goes.
Regards.

---

### Post by BStrizzy on 2012-11-20
> **papibe said:**
> ```
usb-WD_My_Book_1140_574D415A4138303032313332-0:0 -> ../../sdb

usb-WD_My_Book_1140_574D415A4138303032313332-0:0-part1 -> ../../sdb1
```There you go.

Your disk was assigned to the device /dev/sdb and the useful partition is on /dev/sdb1

To mount the disk you need to create a mount point first (a directory):
```
sudo mkdir /media/MyBook
```Then you can mount the disk like this:
```
sudo mount -t ntfs /dev/sdb1 /media/MyBook
```Let us know how it goes.
Regards.

awsome awsome, this worked. however, i am currently the only user on my server and would like this mounted to my home folder. how do i unmount? and im assuming i re mount by using same code just different destination

---

### Post by papibe on 2012-11-20
Yes. Sort of.

First, you un mount it:
```
sudo umount /media/MyBook
```
Then create a new mount point in your home directory:
```
mkdir /home/youruser/MyBook
```
(replace 'youruser' for your actual username).

Then mount it on the new location:
```
sudo mount -t ntfs /dev/sdb1 /home/youruser/MyBook
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by BStrizzy on 2012-11-20
> **papibe said:**
> Yes. Sort of.

First, you un mount it:
```
sudo umount /media/MyBook
```Then create a new mount point in your home directory:
```
mkdir /home/youruser/MyBook
```(replace 'youruser' for your actual username).

Then mount it on the new location:
```
sudo mount -t ntfs /dev/sdb1 /home/youruser/MyBook
```Hope it helps. Let us know how it goes.
Regards.

awsome man, worked like a charm. this is why i appreciate ubuntu forums. solid instructions. Now I have a question. Where can i learn what the commands mean such as dev and ntfs and sdb? I am not taking a unix course and my university so I am sort of self taught.

---

### Post by papibe on 2012-11-21
:) Great!

Please mark the thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Here's a few ideas to get more information:
[LIST]
[*]Visit the forums frequently. Search for similar threads and ask questions when you don't find any tips.
[*]Visit [help.ubuntu.com]("https://help.ubuntu.com/") for tutorials and wikis. Take a special attention to this page: [CommandLine Resources]("https://help.ubuntu.com/community/CommandLineResources").
[*]For individual commands use the pre installed help system called 'man'. For instance run:```
man mount
```
[*]Check out this [thread]("http://ubuntuforums.org/showthread.php?t=1909108") with lots of useful links.
[*]Have fun with it all!
[/LIST]
Kind Regards.

---

### Post by BStrizzy on 2012-11-21
> **papibe said:**
> :) Great!

Please mark the thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Here's a few ideas to get more information:
[LIST]
[*]Visit the forums frequently. Search for similar threads and ask questions when you don't find any tips.
[*]Visit [help.ubuntu.com]("https://help.ubuntu.com/") for tutorials and wikis. Take a special attention to this page: [CommandLine Resources]("https://help.ubuntu.com/community/CommandLineResources").
[*]For individual commands use the pre installed help system called 'man'. For instance run:```
man mount
```
[*]Check out this [thread]("http://ubuntuforums.org/showthread.php?t=1909108") with lots of useful links.
[*]Have fun with it all!
[/LIST]
Kind Regards.


Will do man, I will be looking over these asap! thanks a bunch!:)

---

### Post by BStrizzy on 2012-11-21
> **BStrizzy said:**
> Will do man, I will be looking over these asap! thanks a bunch!:)

I also wanted to know, how do I check my threads that I post? Recently I have been just using the search "myBook" to find my recent post. There has got to be another way.

---

### Post by papibe on 2012-11-22
Sure there is ;)
```
Search -> Find All your Threads
```
Or
```
Search -> Find All your Post
```
Alternatively, you can go:
```
Search -> Advance Search
``` 
And then search using the field:
```
User Name:
```
Regards.

---

### Post by BStrizzy on 2012-11-25
> **papibe said:**
> Sure there is ;)
```
Search -> Find All your Threads
```Or
```
Search -> Find All your Post
```Alternatively, you can go:
```
Search -> Advance Search
```And then search using the field:
```
User Name:
```Regards.


Awesome got it! Thanks man

---

