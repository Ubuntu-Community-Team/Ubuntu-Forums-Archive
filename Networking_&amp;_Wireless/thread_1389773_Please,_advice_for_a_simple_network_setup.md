---
title: "Please, advice for a simple network setup"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by JC Cheloven on 2010-01-24
Hi, the situation is: two pcs, both ubuntu.

The boss pc, which is phisically connected to the router. The files to share will be stored in this computer.

The secretary pc. Wireless connection . She has to be able to access the documents in the other pc, modify them, save them... in practice do the daily work on the files stored in the other pc.

I devise a simple setup: 
- install openssh-server in the boss pc
- create a user (say 'enterprise') in the boss pc
- the needed files will be at that home directory
- both, boss & secretary, will usually login as 'enterprise'
- the secretary will use 'connect to server' in nautilus for login
- she will access the files from nautilus. 
- Network printing and such has nothing to do with the file share, true?

I'm not expert in networking. The users will be those at a small family bussines, so (internal) security and privacy is not a big deal. I wonder if that setup should work just fine, or if for example, something can go terribly wrong if both users (using the same account) try to modify the same document at the same time.

Any input would be appreciated.

---

### Post by johnson.d on 2010-01-25
This is how you can setup a secure file sharing server and setup your network.

1) Installing open-ssh server

Ubuntu desktop doesnt install open-ssh by default during OS installation
You can install it by running the command
$ sudo apt-get install ssh

2) A new user named 'enterprise' can be created using the command

$ useradd enterprise

3) While connecting through nautilus the secretary can use SSH option and use the the following credentials to connect

(i) Server
(ii) Port no (Default is 22)
(iii) Folder (/home/enterprise in this case)
(iv) username
(v) Password

yes, Network printing has nothing to do with samba share.

Accessing the same file by 2 users at the same time is not recommended as it may corrupt the file.

You can also use other options like samba for file sharing.

---

