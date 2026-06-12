---
title: "Need help setting up NFS"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by ZLance on 2009-06-24
So I have 2 computers on the LAN.

I have NFS server daemon with portmap daemon running on one, I have the 
/files (client-ip)(tags) 
in /etc/export on the server

I have the client and server ip -> hostname in /etc/hosts on the server

The nfs-kernel-daemon starts normally on the server

I have the client and server ip -> hostname in /etc/hosts on the client as well.

Both client and the server are on eachother's hosts.allow, and hosts.deny is set to all.

Both the shared directory on the server and client mount point are in /home/corresponding-username/shared-directory.

The name of shared directory is same as the mount-point directory.

When I try to mount like this on the client:
~$sudo mount (server-ip):/home/server-username/shared-directory /home/client-username/shared-directory

It freezes for about 20-30 secs and prints out the line:
mount.nfs: mount system call failed

What can be the problem here?
Do I need to do something about user groups?

---

### Post by quixote on 2009-06-25
Just guessing here, because I'm bad at networking, but I do have an nfs server running.  I had to install nfs-common and winbind (both are in synaptic), as well as edit /etc/nsswitch.conf by adding "wins" to the hosts line:```
hosts:          **wins** files mdns4_minimal [NOTFOUND=return] dns mdns4
```
I don't know if this has any relevance to your situation, but just thought I'd mention it.

---

### Post by dmizer on 2009-06-25
Have a look at the 4th link in my sig. It should give you some tips on what to look for.

Otherwise, you may be interested in this bug: [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/322744](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/322744)

WINS has nothing to do with this problem, as it involves netbios name resolution for Windows shares.

---

