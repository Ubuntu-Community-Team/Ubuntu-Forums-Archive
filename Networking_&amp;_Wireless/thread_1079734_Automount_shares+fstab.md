---
title: "Automount shares+fstab"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by KrGAce on 2009-02-24
Hello,

I am wondering if someone can help me with the following.  I am trying to auto mount shares to my freenas server.  I have the shares setup and can browse to them, but I want them to automount everytime I login.  Can someone tell me what is wrong with my entries.  I got these from searching the web.  Many thanks in advance.

AceMan (please see below)

kfreenasg is the name of my server
/Documents and /Music are the correct shares.
I have also created the directories after /home/krgace..
krgace is the right user name.

# my smbfs shares:
//kfreenasg/Documents /home/krgace/mounts/Documents smbfs username=krgace,password= 0 0
//kfreenasg/Music /home/krgace/mounts/Music smbfs username=krgace,password= 0 0

---

### Post by Iowan on 2009-02-24
[This]("http://ubuntuforums.org/showthread.php?t=288534") is one of my favorite How-To's for mounting Samba shares.
[Here]("http://ubuntuforums.org/showthread.php?&t=283131") is an FSTAB How-To for good measure...)

---

### Post by KrGAce on 2009-02-24
That's all fine and good, and there's a bunch of info here, but I think I have read the same thing on other sites.  It just basically doesn't tell me why mine doesn't work.

It's like someone asking a question why doesn't this work, and someone else saying "oh that's because you need to read this 1000 page book".  Don't get me wrong I am grateful for the site, however it just doesn't tell me what/where I am going wrong.


AceMan

---

### Post by johnson8707 on 2009-02-24
Instead of using the server's short name, try its IP address. I had to do that to get my boxes to mount SMB shares.

---

