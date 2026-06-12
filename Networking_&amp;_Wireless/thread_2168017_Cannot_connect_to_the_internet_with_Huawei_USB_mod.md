---
title: "Cannot connect to the internet with Huawei USB modem"
date: 2013-08-16
forum: Networking &amp; Wireless
---

### Post by jwkungfu on 2013-08-16
Hi there,

Can someone please advise what I should do after this error message;

Error mounting /dev/sr1 at /media/john/Virgin Mobile: Command-line `mount -t "iso9660" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500" "/dev/sr1" "/media/john/Virgin Mobile"' exited with non-zero exit status 32: mount: special device /dev/sr1 does not exist

I have had a look at sr1;

cd /dev
ls -l sr1

brw-rw----+ 1 root cdrom 11, 1 Aug 16 16:02 sr1

I have tried (successfully) to connect using a different laptop running Windoze XP.
I can connect to the net using wireless (tethered through my phone).
I have tried (multiple times) to reconfigure my wireless settings and make a new connection.
I have tried (unsuccesfully) using Linux Mint (booted from a CD) on both of my laptops.

Thanks in advance for your help!

Cheers!!

---

### Post by jwkungfu on 2013-08-16
Please see my original post below before reading this post (Thanks!)

john@john-Satellite-Pro-L650:/dev$ sudo chmod +777 sr1
[sudo] password for john: 
john@john-Satellite-Pro-L650:/dev$ ls -l sr1
brwxrwxrwx+ 1 root cdrom 11, 1 Aug 16 16:32 sr1
john@john-Satellite-Pro-L650:/dev$ getfacl sr1
# file: sr1
# owner: root
# group: cdrom
user::rwx
user:john:rw-
group::rw-
mask::rwx
other::rwx

I guess the USB modem is read only...?

I had the internet working fine until this problem came up...

---

### Post by jwkungfu on 2013-08-19
Edit Connections...
(Select your Internet connection) Edit
PPP Settings
Authentication
[Configure Methods]
Untick all 'EXCEPT' PAP
OK

Try again!

Good luck!

---

