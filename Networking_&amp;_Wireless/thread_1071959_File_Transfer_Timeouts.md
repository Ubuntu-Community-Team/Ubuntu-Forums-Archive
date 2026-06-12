---
title: "File Transfer Timeouts"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by berencamlost on 2009-02-16
I'm having trouble transferring files between my downstairs and upstairs computers. The downstairs computer is running Ubuntu 8.10 and has a samba share called "music". I've been trying to transfer the files wirelessly to my upstairs computer running Ubuntu 8.04.2. I run into timeout problems when transferring my 30 gigs or so of flacs to the upstairs computer and I'm wondering if anything can be done to prevent this. Can i change samba settings to prevent timeouts (or at least the amount of time that must pass before a timeout occurs)? Or is there a way to have Ubuntu retry downloading the file it t/o on instead of having to skip it? 
Thanks for any help.

---

### Post by dzark on 2009-02-16
If you're sharing between two linux boxes, try using NFS.. Quite a bit more reliable that SMB(Samba), and a lot faster.. 

Check out:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Else failing that, here's the options for Samba TTL :)

[http://oreilly.com/catalog/samba/chapter/book/ch07_03.html](http://oreilly.com/catalog/samba/chapter/book/ch07_03.html)

---

### Post by berencamlost on 2009-02-17
ya I've been kicking around the idea of using nfs for awhile. I miss the days when you could just right click in Ubuntu and click share with nfs. The reason that i've been using samba though is because a.) I can click connect to server and hop on/off the share quickly b.) the media center pc i have in the living room is an old p4 running XP.
Is there a quick way to mount an NFS folder on another computer?

---

