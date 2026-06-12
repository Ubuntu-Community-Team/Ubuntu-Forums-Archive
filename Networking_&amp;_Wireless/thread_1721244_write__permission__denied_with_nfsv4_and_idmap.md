---
title: "write : permission  denied with nfsv4 and idmap"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by faitout17 on 2011-04-04
Hello, 

I would allow sharing of files between a server and multiple clients. Classic. 

To do that, I use nfsv4 and idmap to map users names between client and server. 

I can mount the shared folders on clients with a good mapping of users names (for example log below idmap 

> Apr  4 00:17:46 develop rpc.idmapd[8244]: Client 31: (user) name "thierry@localdomain" -> id "1000"
Apr  4 00:17:46 develop rpc.idmapd[8244]: Client 31: (group) name "thierry@localdomain" -> id "1000" ...
If iud's owner of the exported directory is the same as the client user's one, I have no problem.
 However, if the name's user is the same but the uid are not the same (number and order of creation of different users between server and clients), the client sees the mounted folder, also sees write permission, but a mkdir test returns a "permission denied".

 I thought idmap solves the access between different uids with same user names. Should we indeed go further and authenticate users with Kerberos or other stuff ?

 Thank you for your ideas.

---

### Post by twelve17 on 2011-04-10
I'm running into the exact same issue.

A folder has permissions 0755, owned by same user name on both machines, but different uid's.  I get permission denied trying to create a file on that directory.

---

### Post by Zeroedout on 2012-01-15
Hi, were either of you able to solve this issue?

---

### Post by SeijiSensei on 2012-01-16
I just make sure /etc/passwd and /etc/group are identical on all machines.  That's by far the simplest solution.

---

### Post by wintrmute on 2012-03-27
I'm having the same kind of problem, tested on Ubuntu Oneiric and the beta of Precise.

NFSv4 with the idmapper claims that directories are owned and writeable by the correct username, but attempts to actually write to them by that user results in a permission denied error.

Have any of the above users managed to solve this issue in the past year? I can find numerous threads with this problem via Google, but never any solutions..

---

### Post by wintrmute on 2012-03-27
Created this bug to track the issue:
[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/966734](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/966734)

---

### Post by twelve17 on 2012-03-28
> **wintrmute said:**
> Have any of the above users managed to solve this issue in the past year? I can find numerous threads with this problem via Google, but never any solutions..

I never found a solution, sorry.

---

