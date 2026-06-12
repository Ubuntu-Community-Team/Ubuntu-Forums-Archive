---
title: "How to Watch the recorded program from Dish TV Plus on PC"
date: 2015-01-12
forum: Multimedia Software
---

### Post by ramakanta on 2015-01-12
I has recorded TV shows on my Dish TV+ using  USB drive and i wants to watch that shows on my PC but when I am using that PEN Drive on pc ,
it is giving the Message of format disk . Any idea how to Play recorded file in PC . Please help me . Thank you. 

in windows it shows look like  
[[img]http://s28.postimg.org/k447x6qyh/image.jpg[/img]](http://postimg.org/image/k447x6qyh/)
[[img]http://s28.postimg.org/ca3mbsj5l/image.jpg[/img]](http://postimg.org/image/ca3mbsj5l/)

---

### Post by ajgreeny on 2015-01-12
With that pen drive attached show the output from Ubuntu of command **sudo parted -l**.

I wonder if the disk is formatted as ext3 or ext4, as that would explain why Windows wants to format it; Windows can not use or even read Linux ext partitions.  Can you watch the recorded shows using Ubuntu instead of Windows?

---

### Post by ramakanta on 2015-01-12
> **ajgreeny said:**
> ........... Can you watch the recorded shows using Ubuntu instead of Windows?

yes sir , it is unable to mount this pen drive .

---

### Post by ajgreeny on 2015-01-12
And what about the **sudo parted -l** output?

---

### Post by MartyBuntu on 2015-01-12
> **ramakanta said:**
> I has recorded TV shows on my Dish TV+ using  USB drive and i wants to watch that shows on my PC

It's likely that the Dish TV box encrypts the drive the recordings are stored on. You probably won't be able to transfer the files or view them on any device.

---

### Post by mc4man on 2015-01-12
> **MartyBuntu said:**
> It's likely that the Dish TV box encrypts the drive the recordings are stored on. You probably won't be able to transfer the files or view them on any device.
I would think so, likely - 
[http://www.mydish.com/support/use-ehd](http://www.mydish.com/support/use-ehd)
Example - 
[http://www.mydish.com/support/setup-612-622-722-722k](http://www.mydish.com/support/setup-612-622-722-722k)
Which makes this thread worthless..

---

### Post by ramakanta on 2015-01-14
> **ajgreeny said:**
> And what about the **sudo parted -l** output?


```


Model: SanDisk U3 Cruzer Micro (scsi)
Disk /dev/sdb: 2001MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start  End     Size    Type     File system  Flags
 1      131kB  2001MB  2001MB  primary


```

---

### Post by ajgreeny on 2015-01-14
As you can see from that output, the partition is seen but not in any meaningful way; no filesystem type is shown, so as mac4man says, we will not be able to do anything here to help you.

---

