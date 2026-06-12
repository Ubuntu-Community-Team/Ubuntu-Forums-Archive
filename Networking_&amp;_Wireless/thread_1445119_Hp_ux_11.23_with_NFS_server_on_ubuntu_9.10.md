---
title: "Hp ux 11.23 with NFS server on ubuntu 9.10"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by erictioh on 2010-04-02
Hi, I have already setup nfs server version 3 at ubuntu 9.10 and shared it a a Hp ux server successfully.
 
I can cp large files, do anything using unix standard commands like cp, mv, etc..
 
The hpux server is also my oracle db server, so i tried to create a new tablespace dbf file on the nfs share mount point, it just keep hanging after i issue the command. I run the create table command from sqlplus.
 
I did anohter experiment which is to use anohter hpux server as nfs server instead of using the ubuntu. after mounted the nfs, oracle create tablespace works fine without hanging.
 
Does anyone has idea what's going on?

---

### Post by big_sigh on 2011-03-23
I am seeing a very similar problem with a HP-UX 11.23 client mounting NFS from my Ubuntu 10.10 server.

However, my problem is running swinstall when the depots are on the NFS server.

The Install is so slow, that it takes hours. However if I copy the files to the local server, from the same NFS location and it takes a few seconds.

The line from my /etc/exports is

/raid/2/depot    *(rw,nohide,insecure,no_subtree_check,async)


I do remember fixing this problem on a long gone server, and kicking myself for not taking proper notes.  I think it is something to do with Locking .. but not totally sure

---

