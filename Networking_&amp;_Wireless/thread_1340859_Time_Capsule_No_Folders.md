---
title: "Time Capsule No Folders"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by Mooseking on 2009-11-29
Im running new 9.10 but quite new to it all and was wondering f any1 could help me regarding timecapsule and not being able to see folders or do anything for that matter in my timecapps dir. im using the command "sudo mount.cifs //10.0.1.1/"Moosemoon"/brett /media/capsule -o pass=secret" if any1 could help much appreciated. :p

---

### Post by mortuk on 2009-12-18
am having the same problem, however i mounted slightly differently

//ip/tc_name/diskname didnt work for me, kept getting mount error 6
in the end had to do //ip/diskname which mounts but get empty dir. however it resports free space correctly, and if i mount with rw and make a folder it reflects that change on the TC when viewed from a mac

---

### Post by mortuk on 2010-04-07
Anyone?

---

### Post by lgl5853 on 2010-04-07
Had the same problem.  This solution worked for me:
[http://ubuntuforums.org/showthread.php?t=1320918](http://ubuntuforums.org/showthread.php?t=1320918)

Also, if you want it to permanently mount, just add noserverino into the options in your etc/fstab
I tried it and now my Time Capsule and all folders & files show up when I boot.

---

### Post by mortuk on 2010-04-08
thanks, worked a treat :)

---

