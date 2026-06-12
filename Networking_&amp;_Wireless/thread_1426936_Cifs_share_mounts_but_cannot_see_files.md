---
title: "Cifs share mounts but cannot see files?"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by mobi on 2010-03-10
Hey guys\gals,

I have a Buffalo Drivestation (model HD-CELU2, 1tb) attached to my network.  From my ubuntu desktop I can go to the menu, select "connect to server", put in the ip and share info, and it mounts perfectly.  I can open the share and browse\read\write, but when I try to mount it from a terminal or within fstab, it will still mount, but I cannot see any files that are on the drive.  I have about 12gb of data on it, but like I said when I mount it using "mount -t cifs 192.x.x.x/share blah blah blah" I do not see any of the files.  If I do a df I can see that the drive has files on it based on the free space available, but if I do an ls nothing shows.  Has anyone seen this?  Any advice?  Its probably something minor I'm missing but I'm kinda stumped.



Thanks in advance,

mobi

---

### Post by dmizer on 2010-03-11
> **mobi said:**
> Hey guys\gals,

I have a Buffalo Drivestation (model HD-CELU2, 1tb) attached to my network.  From my ubuntu desktop I can go to the menu, select "connect to server", put in the ip and share info, and it mounts perfectly.  I can open the share and browse\read\write, but when I try to mount it from a terminal or within fstab, it will still mount, but I cannot see any files that are on the drive.  I have about 12gb of data on it, but like I said when I mount it using "mount -t cifs 192.x.x.x/share blah blah blah" I do not see any of the files.  If I do a df I can see that the drive has files on it based on the free space available, but if I do an ls nothing shows.  Has anyone seen this?  Any advice?  Its probably something minor I'm missing but I'm kinda stumped.



Thanks in advance,

mobi

Take a look at the 2nd link in my sig, it includes troubleshooting tips. Pay particular attention to the "Files owned by root" section.

---

### Post by suseendran.rengabashyam on 2010-03-11
Hi,

A similar thread,

[http://ubuntuforums.org/showthread.php?t=1409720](http://ubuntuforums.org/showthread.php?t=1409720)

Hope this helps.

---

### Post by mobi on 2010-03-12
> **dmizer said:**
> Take a look at the 2nd link in my sig, it includes troubleshooting tips. Pay particular attention to the "Files owned by root" section.

That did not work for me dmizer.  I added in the uid\gid, that was the only thing I had not done.  No luck.  Lets me mount it but still can't see files.

---

### Post by dmizer on 2010-03-12
> **mobi said:**
> That did not work for me dmizer.  I added in the uid\gid, that was the only thing I had not done.  No luck.  Lets me mount it but still can't see files.

What is your current mount command?

---

### Post by mobi on 2010-03-12
> **dmizer said:**
> What is your current mount command?

Actually I just figured it out thanks to that link you sent.  I forgot to add in noserverino.  So my fstab looks like this: 

//NAS/share /home/user/mntpoint cifs  iocharset=utf8,noserverino,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0


I guess my box was expecting inodes...anyway THANKS SO MUCH for your help!

---

### Post by dmizer on 2010-03-12
> **mobi said:**
> Actually I just figured it out thanks to that link you sent.  I forgot to add in noserverino.

Fantastic. Glad to know you're working!

---

### Post by mobi on 2010-03-12
> **dmizer said:**
> Fantastic. Glad to know you're working!


Yup...thanks again for your guidance.

---

