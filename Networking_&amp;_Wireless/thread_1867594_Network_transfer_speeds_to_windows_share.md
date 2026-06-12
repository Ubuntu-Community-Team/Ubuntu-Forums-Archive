---
title: "Network transfer speeds to windows share"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by magpettersson on 2011-10-23
Ubuntu 11.10.

I have a windows server 2008 R2 with shares and i have a gigabit router. When i boot my desktop machine in windows 7 i have around 80-90MB/s transfer speed for big files which is pretty awesome since its almost topping out my gigabit router.

But.. The less awesome is when i boot into ubuntu 11.10. When i copy something using nautilus (from network location smb:// and not mounted) i get around 38MB/s which is half of what i get in windows!

Even worse is that i get around 20MB/s when copy after i mount to a local folder like /mnt/fileking/ which is half of what i get when copying from smb:// location. Whats going on here? 20MB/s vs 80-90MB/s that i get from booting in windows 7 is a huuuge difference!

I might be doing something wrong in my fstab when mounting to the folder but since im not a linux guru i dont really know how to problem solve this issue, heres whats in my fstab:

//fileking/pool /mnt/fileking cifs auto,uid=magnus,gid=users,dir_mode=0775,username=magnus,password=mypasswordhere 0 0

and the name fileking is put into the hosts file with right ip adress

So any ideas what i can do to get my 80-90MB/s using linux??

---

### Post by Gyokuro on 2011-10-23
Hi,

Windows 7 and Windows 2008r2 are speaking SMB 2.1 and MS optimized with this release the SMB protocol. On Linux samba 3.6 supports SMB 2.X all other releases are using an older protocol which is not optimized and is slower. However you can try to play with following setting in your smb.conf (Global section) in case you use samba:

socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536

or command line /etc/fstab mounting:

rsize=65536,wsize=65536

---

### Post by magpettersson on 2011-10-23
Hello :)

I tested and added that line in the /etc/samba/smb.conf and also added the options for /etc/fstab but no real difference.

I still get 40MB/s by going nautilus -> browse network -> fileking/sharedfolder and copy a file and paste it to local drive (/tmp).

But when mounting /mnt/fileking/folder and copying a file and paste it in /tmp it goes half speed (around 20-28MB/s). Im not sure whats going on when im copy pasting from the network directly since it goes much faster than the mounted location (which i want to be as fast).

I didnt understand the version things, is windows 7 and server2008 r2 using older version of samba but have optimized it for that 2.1 version, or is ubuntu having an older version which make it slow? Would I be able to have 80-90MB/s transfer speed between two linux boxes?

---

### Post by kid1000002000 on 2012-06-21
Having the same problem and am curious if this is getting solved.
I've found the following:
[INDENT][https://bugzilla.samba.org/process_bug.cgi](https://bugzilla.samba.org/process_bug.cgi)
[http://www.overclockers.com/forums/showthread.php?t=683188](http://www.overclockers.com/forums/showthread.php?t=683188)
[/INDENT]

---

