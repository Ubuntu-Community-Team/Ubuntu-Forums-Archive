---
title: "cifs + windows 7 = no WRITE access after mount"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by tigerstripedcat on 2010-04-19
I've tried all the solutions posted by others I could find.  I have a windows 7 system connecting from a 9.10 system.  


On the windows side:
* Folder in drive is set to sharing
* NOT set to read-only 
* the login user has FULL access to folder and drive

on the linux side my mount command:

mount -t cifs //julia/D /home/USER/julia/D -o username=USER,password=PASS,rw,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777


The files even seem to be mounted correctly I think: 

-rwxrwxrwx 1 USER USER       8192 1995-07-03 14:21 EMU2DISK.BIN


I've tried just about every option under the sun and I tried going over dmizer's guide ([http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)) but I constantly get:

USER@spike:~/julia/D$ touch sfs
touch: cannot touch `sfs': Permission denied

I have a guess that this is a windows 7 thing but I'm not sure. All I know is that I'm sick at looking into this problem.
any help will be appreciated
James

---

### Post by Iowan on 2010-04-19
I presume you've seen **dmizer's** [other]("http://ubuntuforums.org/showthread.php?t=1169149") Samba How-To...

---

### Post by tigerstripedcat on 2010-04-21
I just did:

* wins disabled
* set to "WORKGROUP", windows uses "WORKGROUP"
* disabled all firewalls
* followed directions on windows 7, double checked permissions.
* restart samba

Still cant write to windows shares. So annoying! ](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

