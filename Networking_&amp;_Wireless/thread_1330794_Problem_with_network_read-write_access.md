---
title: "Problem with network read-write access"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by jthompson1 on 2009-11-18
I am new to Ubuntu 9.10, learning lots quickly but have come up against a problem that I cannot figure out.

I run a separate machine in the garage that acts as a server for the house with Fedora as the OS and also run Amahi for the file, user and media server.

Trying to access the shares from my desktop is where I am having the problem. 

In order to mount the drives I have put the following into fstab:
 //hda/Music /home/jthompson/Network/Music smbfs username=xxx,password=yyy 0 0

This mounts the drives successfully in the desired location, but this only gives me read access. If I go to the same network location in the file browser through Network>Home>HDA etc... I get full read-write access.

The username and password entered is the same for both and is what has been configured.

Any help would be appreciated!!

Thanks,
James.

---

