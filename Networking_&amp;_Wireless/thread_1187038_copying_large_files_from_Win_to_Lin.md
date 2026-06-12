---
title: "copying large files from Win to Lin"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by stonebit on 2009-06-14
I have a Windows2003 server used as a file share. When I move large files (700 Mb to 8 Gb) over to my Linux (Kubu 9.04 x64) box (ext4 on a spare drive), the md5 sums do not match. I have tried just a straight copy in Dolphin and rsync. I am using Kdiff3 to check after copying. Most of the files show small differences. Here is my share in fstab: 
//192.168.0.32/raid /mnt/server cifs  sername=xxx,password=xxx,iocharset=utf8 0 0

I'm thinking it's an issue with my share setup, but I'm stuck.
Any ideas as to how I can get exact copies? 
Thanks.

BTW, I'm working on moving the server over to Linux. That's why I'm making such large copies.

---

### Post by expelledboy on 2009-06-14
Use samba.. install samba on the server if necessary as it seems you are going to bomb it anyway.

links;
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by stonebit on 2009-06-14
What do you mean by installing samba on the server?
I have file sharing setup on the windows server. Samba is for the linux side no? 

BTW, I was using Linux as the client. I have also tried setting up a samba server on the Linux box and connecting/copying files to the linux share in windows. The same type of errors appear. 

The errors happen at different places in the files. Windows does a verification of each packet (win2win sharing) to make sure it was transferred correctly, then adds that portion of the file to the destination. This is the kind of copying I'd like to do. I'm sure this is just a problem with windows not playing fair, but there's got to be a way around this.

---

### Post by superprash2003 on 2009-06-15
you might want to try playing around with MTU , that could be the issue..

---

### Post by expelledboy on 2009-06-15
Oops.. sorry I posted to the wrong thread.

I can though give you some advice on your problem. I would move the physical harddisk to the machine you want to copy to for any collective data larger than 200gb (that is if you have access to the server.) Advantages include faster copy times and a more reliable shift. Use rsyncs checksum option to ensure exact copies of all your files, **man rsync** for more info on that.

I messed up 1/4 of my music and my entire photo library once trying to copy windows media to linux! That was awhile ago I must admit..

---

### Post by stonebit on 2009-06-15
Yeah-I thought about moving the drives too, but most of the stuff is on an old raid 5 w/NTSC and I want it on my new 2TB HD, which is ext4. So the network will be easier. I don't mind waiting whilst I sleep.

Anyway, I decided to rule out the network and test some large file transfers across HDs within my box. To my suprise, the errors are still occurring. A bit of googling and I found someone else with similar errors. It appears that my problem is in my RAM. I have 4 x 2GB of RAM (all the same model /speed /etc). I ran memtest last night and BOOM!!! I got two errors in less than an hour. I'm flip flopping chips around to try to determine which one is faulty. I'm wondering if a channel is bad too (not sure yet though). I've already ruled out two chips, so at least I have 4GB of RAM that are surely good. 

With the 2 confirmed good chips installed, I tried a transfer and checked it with Kdiff3. All of my files were exact copies. Those are the sweetest words I've read in a long time. I had issues before, but chocked it up to a goofy RAID 0 I was playing with on super old hardware. It appears the RAM may have been going down hill for the last few months, giving me more and more issues.

The only mystery remains is such: I never had this issue with Windows. What is it that MS does that ensures file integrity but Linux does not do? This may be the 1 thing MS has done well (at least between 2 MS boxes) besides market garbage.

Thanks everyone for your help and input! It is much appreciated!

---

### Post by dmizer on 2009-06-15
Try using a different protocol. I suggest FTP, but you could also try SSH since the [putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/) ssh tool runs without installing.

There may be a file size limit (or something similar) at work with samba.

---

