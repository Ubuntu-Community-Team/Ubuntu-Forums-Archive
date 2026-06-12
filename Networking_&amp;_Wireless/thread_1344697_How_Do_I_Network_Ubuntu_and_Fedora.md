---
title: "How Do I Network Ubuntu and Fedora?"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by fourtyseven on 2009-12-03
Hello.
I would like to network my computer (Ubuntu) with a friends computer (Fedora) but I dont know what to do. I've heard that one should use Samba or NFS but Im not sure how to go about it. I've googled it but any information I am able to find is too complicated for me. Anyone know what I should do or where I can find an easy to follow tutorial?

---

### Post by puppywhacker on 2009-12-03
If you want to copy files up and down, it's best to set some static ip-addresses in both in the same range like

192.168.0.2 and 192.168.0.3

Then you can sftp between the two systems by clicking "places" / "connect to server..." and select the service type "SSH" and for server use the ip-address of the other system, then use the username of the other server and you should be good to do.

---

### Post by Iowan on 2009-12-03
You will probably need to install a server on whichever machine will be providing files - if you want to share both ways, both will need server installed. Which server depends on which protocol you choose - Samba (CIFS), FTP, NFS, SSH,...

---

### Post by Fire_Chief on 2009-12-03
Here's a guide to using NFS to share files. Should provide you with some direction.
[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

Cheers!

---

