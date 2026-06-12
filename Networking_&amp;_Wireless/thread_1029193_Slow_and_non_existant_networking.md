---
title: "Slow and non existant networking"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by Rockhoppers1964 on 2009-01-03
Firstly guys, many thanks for the endless help that i have got from this forum, which has got me to where i am now, which is a hell of a lot further than i got the last time i tried Ubuntu, (version6.10)

I love this program, and if i can just get this last bit working properly, then it is here to stay.

I have a network setup in my home consisting of the following

Dlink router G604T
Dell 4100 wired Windows Vista Premium, as media server / center
Dell Vostro wired Ubuntu 8.1
Samsung Q70 laptop wireless Dual boot XP and Ubuntu 8.10
Sony Vaio laptop wireless Ubuntu 8.1

Samba installed on Ubuntu machines with workgroup set on all to MSHOME, all machines updated to latest release.

A couple of points.

1. Both the wired and wireless Ubuntu machines can see the Vista machine but with varying levels. The sony and the samsung can sit beside each other, one will see it the other will not.

2. The Vostro can see all the networks, but is very slow to open the folders and show contents. Also to copy from the Vista machine to the Vostro, even a simple mp3 file takes ages at a max speed of 3kb ! ! !

3. The vostro has a 500gb hard disk and i want to partition it and format it it to act as a music server, but the partition tool says it will delete all files if i try to do this.

If a partition is not an option, i will install another 500gb hard disk and use that, can that be set up as a windows friendly file system NTFS ?

4. how do you modify the smb.conf file, i can use samba to change the workgroup, but the forum talks of making other changes, but it will not let me save any, i can not a log on as root either despite allowing a root logon in the relevant screen.

Lastly, and on a good note, Ubuntu was great at finding my hard wired networked HP officejet, so simple and fast to spool the prints... 

So many questions, so little time, but if i can just sort out the networking, i have a winner.

Thanks again for your support.

---

### Post by superprash2003 on 2009-01-03
to edit smb.conf in the terminal type sudo gedit /etc/samba/smb.conf
 yes you could use NTFS

---

