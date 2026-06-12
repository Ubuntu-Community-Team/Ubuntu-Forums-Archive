---
title: "Sharing"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by Gwaro on 2011-09-12
Hi everybody
I would like to know how to connect and share with a windows computer on a point-to-point connection.
Thanks.

---

### Post by cap10Ibraim on 2011-09-12
if wireless 
you can use  adhoc connection click on the network icon on ubuntu
click on the create new wireless connection , the windows machine should see this connection available and connect to it 
you can see the public files from the windows box , but you must enable network discovery and file sharing on windows 
if wired just connect the  ethernet cable to both pcs they will both use auto aconfigured ips 
so they will be in the same subnet and "you can see the public files from the windows box , but you must enable network discovery and file sharing on windows"

---

### Post by Basher101 on 2011-09-12
another way would be setting up a Samba network. There are alot of good guides just google

---

### Post by cap10Ibraim on 2011-09-12
> **Basher101 said:**
> another way would be setting up a Samba network. There are alot of good guides just google
yes that's on the application layer

---

### Post by Lars Noodén on 2011-09-12
Also, [SSHFS](http://fuse.sourceforge.net/sshfs.html) can be used even on Windows to share files.  All it requires is a login, so while less flexible and powerful than Samba, it far easier to set up.

---

