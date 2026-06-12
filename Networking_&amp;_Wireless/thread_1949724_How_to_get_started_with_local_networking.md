---
title: "How to get started with local networking?"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by jcobban on 2012-03-30
I have two computers (and my television set) plugged into the router that connects my home to the outside world.

How do I get the 2 Ubuntu systems to talk to each other?  One system has a host name of 'jcobban-laptop' and the other has a host name of 'linux-server', but those names do not appear to be visible to each other.  Even ping cannot find them.  So I cannot telnet or ftp or http or anything between the systems.  When I browse the router itself it shows both Ubuntu systems.

Every tutorial I have found seems to be excessively complicated.  I do not understand why this doesn't work out of the box.  For example why do I have to set up a Samba server to share files, when the original purpose of Samba was to support Windoze in its implementation of the ancient Netware protocols?  The tutorials on setting up either a Samba server or an NTFS server are daunting.  I just want to share files.

---

### Post by Bucky Ball on 2012-03-30
Are the machines using static IP addresses? Not sure what release you're running but have you got the option in 'Places' to 'Connect to Server'? I use Filezilla personally ...

I prefer NFS; when I first set it up was because you can mount a network partition at boot so it is used like a regular local drive (as long as the external device is switched on, of course ...). ;)

---

### Post by jerome1232 on 2012-03-30
Hmmm, right click a file, click share, samba will be installed, and the share created by nautilus black magic.

On the other computer, click your home folder on the launcher, click on network in the left hand pane, you should be able to browse to the share, if not, try pressing control+l, type smb://nameofmachine/sharename or alternatively smb://ipofmachine/sharename

---

