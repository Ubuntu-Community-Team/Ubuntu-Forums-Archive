---
title: "Intrepid Joining Windows Workgroup"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by banstaman on 2009-05-04
I have searched and I haven't found anything about Intrepid joining a Windows workgroup. I have tried installing Samba both from terminal and from "add/remove". I have no idea how to do each of them. Although the smb.conf, is becoming more and more common to me, but it just is very different. The Samba from "add/remove", has nothing that I know about. I have tried the smb.conf many times, and I have gotten to the point where it takes me to the Windows workgroup, although I cannot see Windows computers, and they can't see the Ubuntu system. I have entered the same workgroup name and all, but just no luck at all. I am fairly new to Ubuntu and I really cannot get this to work! I'm trying to use it as a media server. I desperately need anybody's help on this!

---

### Post by mattgyver83 on 2009-05-08
This sounds like an issue similar to what im experiencing in 9.04 that im still trying to figure out but im not certain.  When i have this problem i have to restart the samba service, 

sudo /etc/init.d/samba restart

and then i can finally browse the samba network.  Just in case you havent gotten this far already make sure that you have a samba user created so you can access the ubuntu file system

sudo smbpasswd -a <USERNAME>
then specify a password.

---

