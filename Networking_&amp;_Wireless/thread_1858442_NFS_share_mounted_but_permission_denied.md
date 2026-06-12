---
title: "NFS share mounted but permission denied"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by mikeyw on 2011-10-12
Hi,

I've recently mounted a netapp NFS share to our ubuntu server as follows :-


x.x.x.x:/vol/vol_nfs_cnf1
                      52428800       136  52428664   1% /confbackup

However when i tried to cd into the share i get permission denied :-

root@xxxxx:/var/log# cd /confbackup
bash: cd: /confbackup: Permission denied

This fails as a non root user as well.

From the netapp side the share is exported only to the IP address :-

/vol/vol_nfs_cnf1 Read-Write Access (x.x.x.x)
Security (sys) 

Any ideas ?

tia
M

---

### Post by mikeyw on 2011-10-13
Any thoughts here guys ?

---

### Post by tigerrrcat on 2011-10-13
I am having the same problem.  Does anyone have any ideas?

---

### Post by mikeyw on 2011-10-14
There's a :KS out there with a fix for this im sure :)

---

### Post by Rizup on 2011-10-14
Same problem here, but the funny thing is that I have one NFS share working fine and one that doesn't.  I have the one that doesn't working on another box just fine though.  :confused:

---

### Post by mikeyw on 2011-10-17
lol - loads of people with the symptoms.....nobody with the cure :lol:

---

### Post by tigerrrcat on 2011-10-24
From an ubuntu box, I'm trying to mount shares from a Solaris 9 server, an OpenStorage (Fishworks) appliance and a NetApp appliance. 

All three mount with no error. 

Accessing the files on the Solaris server and OpenStorage device works fine.

However, accessing the files on the NetApp fails with "permission denied". 

All are set up the same way (root=ubuntubox,rw=ubuntubox) but the NetApp doesn't react the way the others do.

Does anyone have any pointers or ideas?

---

### Post by mikeyw on 2011-10-26
Yes i'm fairly certain this is to do with the way Netapp presents it's NFS storage...

---

