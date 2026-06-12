---
title: "Access a pc by ip address"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by abidmahmood on 2009-09-16
I have an ip address say 10.103.104.81 i used to acess shared file on this machine through windows. now i switch to ubuntu want to know how do now i access those files. i don't know where that pc is.. also don't know its network name or workgroup it just worked in windows like \\10.103.104.81.. i tried to ping 10.103.104.81 and it works fine.. but how to acess folders and files on that system ...???

---

### Post by uncle-c on 2009-09-16
HI Abid,
You will have to install and configure Samba on your Ubuntu machine if you want to share files with your XP. Here is an excellent tutorial by Stormbringer. If you follow it carefully it should work.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by Iowan on 2009-09-16
Ubuntu *should* have Samba client pre-installed, and you *should* be able to access the share by entering **smb://servername/sharename** in Nautilus address bar... but [here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To for some potential problems/solutions.

---

