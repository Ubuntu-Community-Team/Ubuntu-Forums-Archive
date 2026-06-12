---
title: "newbie NFS problem."
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by muxecoid on 2009-06-21
I tried to follow the minimalistic NFS guide.
I installed nfs-kernel-server on server and nfs-common on clients. Here is the /etc/exports from the server:

> 
/sharedhome 192.168.0.0/255.255.255.0(rw,sync)
/usr/sgeroot/default 192.168.0.0/255.255.255.0(rw,sync)


Here is the fstab file on client (client is 192.168.1.2, server is 192.168.1.1)

> 192.168.1.1:/sharedhome /sharedhome nfs rw,hard,intr 0 0
192.168.1.1:/usr/sgeroot/default /usr/sgeroot/default nfs rw,hard,intr 0 0

Here is the error message:

> rabin@rabinnode1:~$ sudo mount -a
mount.nfs: access denied by server while mounting 192.168.1.1:/sharedhome
mount.nfs: access denied by server while mounting 192.168.1.1:/usr/sgeroot/default

What's wrong and how do I fix it?

---

### Post by dmizer on 2009-06-21
Your /etc/exports should look like this:
```
/sharedhome 192.168.[COLOR="Red"]**1**[/COLOR].0/255.255.255.0(rw,no_root_squash,async,no_subtree_check)
/usr/sgeroot/default 192.168.[COLOR="Red"]**1**[/COLOR].0/255.255.255.0(rw,no_root_squash,async,no_subtree_check)
```
Critical change marked in red.

---

### Post by muxecoid on 2009-06-21
> **dmizer said:**
> 
Critical change marked in red.

Huge thanks, it works!!!

Did I try to allow it mount local over network :(?

---

### Post by dmizer on 2009-06-21
> **muxecoid said:**
> Did I try to allow it mount local over network :(?

The example you followed was configured for a network with computers which have IP addresses of 192.168.0.x but your network has IP addresses of 192.168.1.x

The problem was that you configured your share for the wrong IP range.

---

