---
title: "mount.nfs: access denied by server while mounting"
date: 2012-09-12
forum: Networking &amp; Wireless
---

### Post by stlu on 2012-09-12
Hello,

Forgive me if I have targeted the wrong OS here, but I beleive 50% of the problem is with Ubuntu at least.

Situation: I have a Ubuntu client which fails to mount an NFS share on a CentOS 6.2 server.  Because the error relates to access of some sort, I added other-writable to the mode and it looks like "drwxr-xrwx".  The error message did not change, but I left the extra permission there just in case...  Although my username is the same on both systems, my uid on the server is 500, so I am essentially a different user.

Failed command:
[I]adam@Oneiric:~$ sudo mount -t nfs 192.168.0.12:/home/adam/Public /mnt
mount.nfs: access denied by server while mounting 192.168.0.12:/home/adam/Public[/I]

Failed command with -v:
[I]adam@Oneiric:~$ sudo mount -t nfs -v 192.168.0.12:/home/adam/Public /mnt
mount.nfs: timeout set for Wed Sep 12 13:12:26 2012
mount.nfs: trying text-based options 'vers=4,addr=192.168.0.12,clientaddr=192.168.0.11'
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.0.12:/home/adam/Public

[/I]After much Googling (actually, Yahooing) I saw a post about changing versions so, I used this:
*adam@Oneiric:~$ *[I]sudo mount -t nfs** -o vers=3** 192.168.0.12:/home/adam/Public /mnt
(Success...)
adam@[/I]*Oneiric*[I]:~$ mount
...
192.168.0.12:/home/adam/Public on /mnt type nfs (rw,vers=3,addr=192.168.0.12)
[/I]
So, I can at least assume that I correctly configured the server, and the problem occurs with the default version 4, but does not occur when the client uses version 3.

If this is a buggy version of NFS, then why isn't ver 3 still the default?  How can I set the client to always use version 3?

I will need to run this between two Ubuntu systems just in case there is a problem with the CentOS configuration, but I suspect that I will have the same problem, since no errors occured with the version 3 mount.

---

### Post by luvshines on 2012-09-19
Might be something wrong on your server side NFS export definition.

Does anything appear in your server's syslog ?

How has the export been defined ? Can you post the definition here ?

---

