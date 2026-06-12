---
title: "Mount a samba NAS"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by MathSWE on 2009-08-17
Hi,

I cant make a simple mount work in linux. Im trying to mount my QNAP TS-209 II in the fstab but it just wont work properly. Many have tried to help me, NONE have suceeded. Needless to say, in XP this would be no problemo.

The shares gets mounted without any errors and I can browse them with Nautilus. Have hade full read/write access to them

But, If I create a folder in the share, inside that new created folder I get read only rights. So... for instance, importing photos with f-spot doesnt work since f-spot creates folders with dates, and I want it to....

My fstab entry:

 //192.168.0.194/Qmultimedia  /media/QMultiMedia  cifs  guest,uid=1000,gid=1002,iocharset=utf8,codepage=unicode,unicode,dir_mode=0777,file_mode=0777  0  0

Can ANYONE PLEASE help me with this. It seems so basic... i CANT get it to work. This is killing me.... :( :( :( :(

Thanks! //Mathias

---

### Post by Iowan on 2009-08-17
Dunno if [this]("http://ubuntuforums.org/showthread.php?t=288534") one will help...

---

### Post by simonpcook on 2009-08-17
Could this be related to your having a space in the middle of the word "unicode" in your fstab entry.

---

