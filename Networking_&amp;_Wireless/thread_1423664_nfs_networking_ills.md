---
title: "nfs networking ills"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by lei kalaka on 2010-03-06
I've got 2 computers one wireless one wired.
Both running 9.10
I just had them talking/sharing through nfs.
Now they still see each other ,but they won't connect.
This is the message that i get

mount.nfs: access denied by server while mounting james1:/home/trey

Any help would be appreciated

---

### Post by r939ick on 2010-03-07
> **lei kalaka said:**
> 
mount.nfs: access denied by server while mounting james1:/home/trey


What do the logs say server side?  What does your /etc/exports look like?

---

### Post by lei kalaka on 2010-03-07
/etc/exports as follows

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

 /home/trey james1(rw)
as for logs could you specify which one.
Thanks

---

### Post by lei kalaka on 2010-03-07
Okay
Reconnected
Had to exportfs again from server
Had to mount again from client.
I had assumed that adding       /home/trey james1(rw) to /etc/exports in server
and adding        james1:/home/trey  /james1/files nfs rw 0 0    in client fstab
would make this be networked upon boot. Am i wrong?
How do I make it do that?
Thanks

---

### Post by r939ick on 2010-03-08
> **lei kalaka said:**
> .
I had assumed that adding       /home/trey james1(rw) to /etc/exports in server
and adding        james1:/home/trey  /james1/files nfs rw 0 0    in client fstab
would make this be networked upon boot. Am i wrong?


/etc/exports wants a list of client machines that are allowed to mount the directory.  It looks like james1 is the hostname of the server, though, not the client.  Try replacing "james1" in /etc/exports on the server with the hostname of the client machine.

Log messages will probably end up in /var/log/messages on the server, but if that turns up empty, grep for "nfs" in /var/log/*.

---

