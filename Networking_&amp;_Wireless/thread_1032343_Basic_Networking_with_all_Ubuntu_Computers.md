---
title: "Basic Networking with all Ubuntu Computers"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by iheartubuntu on 2009-01-06
I'm looking for help creating an ubuntu network. If there are any walk throughs or howto's available for basic networking of Ubuntu computers I would really appreciate it.

At work, we have a main Windows XP computer and three Ubuntu computers network into it no problem. I was able to see the windows network and log on.

At home, I have three Ubuntu systems, no windows anymore. How do I do a network with just Ubuntu / linux systems? 

Thank you for any help!

---

### Post by timcredible on 2009-01-06
what are you looking to do?  have them share files?  just connect them all to a switch and go to places->home folder (or wherever you have your files) and right-click on a directory and choose 'sharing options', and you can share files.  basically the same thing as a windows network.

---

### Post by tech9 on 2009-01-06
you should be able to mount the share...

as /IP/Share /mnt/"name of your share"

---

### Post by superprash2003 on 2009-01-06
you could use samba or NFS.. NFS Is usually used for linux only network
1)configuring NFS - [http://www.prash-babu.com/2008/11/how-to-setup-nfs-server-and-client-in.html](http://www.prash-babu.com/2008/11/how-to-setup-nfs-server-and-client-in.html)
2)Configuring samba - [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html) 

 NFS is for linux only network.. samba can be used for linux only machines.. samba is easier to setup though..

---

### Post by iheartubuntu on 2009-01-06
I'll try these out, thanks :)

---

