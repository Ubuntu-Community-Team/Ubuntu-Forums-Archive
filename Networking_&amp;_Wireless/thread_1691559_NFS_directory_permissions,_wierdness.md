---
title: "NFS directory permissions, wierdness"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by 8Kuula on 2011-02-20
Here is server side exports settings:
```
/storage      192.168.1.10(rw,sync,subtree_check)
```
client side groups:
```
$ groups
bunbun
```
server side groups:
```
$ ssh server
$ groups
bunbun storage
```

So, way I understand how nfs works is that user and group permissions is handled with ids (uid, gid). Both server and client uid and gid have same numbers and names.

Client side that is connected to servers nfs share
```
$ ls -ld storage
rwxrwsr-x 13 root      storage   4,0K 2011-02-20 10:18 storage
```
since im not member of 'storage' group I should not have write permissions to that directory, right?
```
$ cd storage
$ touch testfile
$ ls -l testfile
-rw-r--r--  1 bunbun storage    0 2011-02-20 11:20 testfile
```
How that can be possible?

When I ssh to server and do same it works, since on that computer I am member of 'storage' group.

---

### Post by Jose Catre-Vandis on 2011-02-20
I may be wrong, but I think your answer is in your question. Because your uid and gid are the same for both client and server, you adopt the permissions on the server when you access as the client. This is how it seems to work for me, as anything I can do on the server as "jose" I can do from the client as "jose".

To test, set up a different user on the client then try to access the share, a different bundle of fun altogether!

---

### Post by 8Kuula on 2011-02-20
Added 'testuser' to client side.

on client side:
now on 'testuser' it do not allow me to create file, ok, 'testuser' is not in 'storage' group.

I add 'testuser' to storage group:
```
$ groups
testuser storage
```
Do not allow to create file, hmm...

Added 'testuser' in server (same uid).
client and server 'testuser' not in group 'storage': no permission: OK.
client in group 'storage', server not: no permission: Not what I expected.
client not in group 'storage', server in group 'storage: has permission: Not what I expected.
client and server in group 'storage': has permission: OK.

Conclusion: when server side has same uid then server side permissions take efect over client side permissions.

Bleh...

---

