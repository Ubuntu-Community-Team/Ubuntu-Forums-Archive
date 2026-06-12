---
title: "NFS User ID / Group ID (uid/gid) mapping"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by philpem on 2010-02-13
Hi,
I'm trying to connect to an old Hewlett-Packard logic analyser over NFS. The machine supports NFSv2, which isn't too bad considering it was designed in the early 1990s.

The problem is, when I mount the NFS export on my desktop system, I can access it only as root -- if I try and access it as another user, I get an I/O error. For example:
```
$ sudo mount 10.0.0.64:/data /mnt/work -o proto=udp,nfsvers=2
$ sudo ls -la /mnt/work
total 3
dr-xr-xr-x 7 daemon daemon 894 2010-02-13 22:18 .
dr-xr-xr-x 2 daemon daemon 638 2010-02-13 22:18 slot_d
dr-xr-xr-x 3 daemon daemon 766 2010-02-13 22:18 slot_e
dr-xr-xr-x 2 daemon daemon 766 2010-02-13 22:18 status
dr-xr-xr-x 4 daemon daemon 894 2010-02-13 22:18 system
$ sudo umount /mnt/work
```

But if I run the same command again without the sudo:
```
$ sudo mount 10.0.0.64:/data /mnt/work -o proto=udp,nfsvers=2
$ ls -la /mnt/work
ls: reading directory /mnt/work: Input/output error
total 0
$ sudo umount /mnt/work
```

It looks like the analyser is only willing to accept RPC / NFS requests from uid/gid 0 -- a wireshark trace reveals that when the RPC packets have uid/gid set to 0/0, the requests are accepted (and processed) correctly. When the uid/gid is set to 1000/1000 (my UID and GID), the RPC requests are rejected as "AUTH_ERROR: bad credential (seal broken)".

I want to use the NFS control interface to, well, control this thing -- run automated tests and so forth. I don't want to have to suid-root my test-runner application and let it wreak havoc on the disk if Something Bad Happens (tm).

So my question: how can I set NFS to send a specific uid and gid to the server, no matter who (on the local machine) the request is coming from?

Thanks,
Phil.

---

