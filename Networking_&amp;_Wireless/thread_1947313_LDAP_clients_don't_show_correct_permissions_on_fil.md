---
title: "LDAP clients don't show correct permissions on files"
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by lisanels47 on 2012-03-26
Permissions and ownership of files on the ldap server works fine.  All systems running ubuntu 11.10.

Clients authenticate and have their home directories mounted via nfs3/autofs5 to the server.

When clients create files on the server, they show owned by them when I check them on the server.  But when I check them from the client, they show strange numbers like -2 or huge numbers.  

Also, from withing Nautilus on the clients, you can click on one of the files you create, and choose permissions.  It shows the owner of the file as -2 and the group as well.  So, you can't change what group the file belongs to or anything.

All changes like that I have to do on the server.

---

### Post by sdmike6 on 2012-03-26
Those numbers you are seeing are the IDs for the LDAP groups.

Go on the server where the files are kept and run this command:
$ getent group

if you don't see your LDAP groups then LDAP isn't importing groups into the server. For example ID 513 is the Domain Users group in LDAP.

---

### Post by lisanels47 on 2012-03-28
The permissions show fine on the server, and such.  It's on the ldap clients I'm trying to get fixed.

I'd like the clients to be able to create a file, and through the GUI change the group and permissions on that file.  Right now, they can't.  I have to connect to the server and do it.  

Must be missing some part of the ldap setup... Maybe related to NFS.  I'm looking into NFS v4 to see if maybe something is added to address this.

---

### Post by lisanels47 on 2012-04-16
This problem seems to come and go.  Maybe with updates that are run.  Here's an example of what I see:

root@hic-05:~# ls -l /data
-rw-rw---- 1 root root 202526 2012-03-29 15:21 Jen.list
-rw-rw---- 1 amy users 415218 2012-03-29 15:56 junk


From a non-working client (almost all clients):

root@hic-02:~# ls -l /data
-rw-rw---- 1 4294967294 4294967294 202526 2012-03-29 15:21 Jen.list
-rw-rw---- 1 4294967294 4294967294 415218 2012-03-29 15:56 junk

---

### Post by lisanels47 on 2012-04-16
Found the solution. 

In /etc/default/nfs-common 

Set NEED_IDMAPD="yes"

---

