---
title: "Mounting jpeg images on cd?"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by upchucky on 2007-07-14
I have a couple of cds full of birthday jpeg images, they are viewable in windows xp, both edgy and feisty will not mount the cd so i can view them.

I can play DVD's,and mount other cd with various files just fine.

Is there a special command parameter i am missing to force the cd to mount when it only has jpeg images on it?

---

### Post by wolfen69 on 2007-07-14
what did you use to burn the cd's?

---

### Post by earobinson on 2007-07-14
what happens when you do the following in the terminal```
sudo mount /media/cdrom
sudo mount /media/cdrom0
```Also FYI the you dont mount the data type so the subject of your post should have been mounting a cd with jpgs? (just letting you know)

---

### Post by upchucky on 2007-07-14
Thanks, the jpegs were created in an unknown windows Vista environment by a relative and mailed to me.
Windows picture and fax viewer and thumbsplus can open the cd just fine on my other pc.

Automount says the following error when the cd is placed into the drive,
invalid mount option when attempting to mount the volume "UDF Volume"

here are the results of the mount attempts you asked about.


electric@XPS-Laptop:~$ sudo mount /media/cdrom
Password:
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

electric@XPS-Laptop:~$ sudo mount /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

electric@XPS-Laptop:~$

---

### Post by upchucky on 2007-07-14
srry forgot to include the dmesg.

electric@XPS-Laptop:~$ dmesg | tail
[17331.756000] Buffer I/O error on device sr0, logical block 72991
[17332.432000] end_request: I/O error, dev sr0, sector 583928
[17332.432000] Buffer I/O error on device sr0, logical block 72991
[17332.696000] end_request: I/O error, dev sr0, sector 583928
[17332.696000] Buffer I/O error on device sr0, logical block 72991
[17332.912000] end_request: I/O error, dev sr0, sector 583928
[17332.912000] Buffer I/O error on device sr0, logical block 72991
[17333.620000] Unable to identify CD-ROM format.
[17423.552000] Unable to identify CD-ROM format.
[17452.816000] Unable to identify CD-ROM format.
electric@XPS-Laptop:~$

---

### Post by upchucky on 2007-07-14
phoned relative,

apparently the jpegs were just a copy/paste done from a windows file folder to the cd.

---

