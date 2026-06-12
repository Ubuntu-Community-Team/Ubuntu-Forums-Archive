---
title: "smb share ntfs"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by Andreas1 on 2009-03-15
trying to share a folder on my external usb ntfs drive i got the following error message (255):
net usershare add: cannot share path /media/usb-hd-andreas/Videos as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

so i added the line to smb.conf, but i keep getting the error. also, i am not sure about the syntax in smb.conf, because other options have the values "yes" or "no" while this one is supposed to be "false" :confused:

btw is this the way to go? or is there a way to change the ownership of an ntfs folder or drive?

---

### Post by nour214 on 2009-03-15
i have ubuntu installed with wubi. whenever i want to see MS Home network, nothing comes up. But i used to see all the computers in the network.

help please

---

### Post by Andreas1 on 2009-03-15
> **nour214 said:**
> i have ubuntu installed with wubi. whenever i want to see MS Home network, nothing comes up. But i used to see all the computers in the network.

help please

this is not related to my question. please open a new thread or search for one that fits your problem. ;)

---

### Post by Andreas1 on 2009-03-15
OK, i went the other way: i created an fstab entry for that partition with the options users,uid=1000,gid=1000 so now i own it.

solved.

---

