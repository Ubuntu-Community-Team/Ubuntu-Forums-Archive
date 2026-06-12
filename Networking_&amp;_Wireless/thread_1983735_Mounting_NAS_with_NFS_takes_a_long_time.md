---
title: "Mounting NAS with NFS takes a long time"
date: 2012-05-20
forum: Networking &amp; Wireless
---

### Post by sdp on 2012-05-20
On ubuntu 12.04 the first mount of my Synology NAS using nfs takes a long time (appr. 45 sec). On Ubuntu 10.04 (same computer) it takes only 1-2 secs. The mount line in fstab is the same:

  192.168.254.98:/volume1/Svend /media/SvendDS nfs nouser,atime,auto,rw,dev,exec,suid 0 0

I have examined the mount process. In 10.04 the verboose-option gives this information:

  mount.nfs: timeout set for Sun May 20 12:30:32 2012
  mount.nfs: text-based options: 'addr=192.168.254.98'
  192.168.254.98:/volume1/Svend on /media/SvendDS type nfs (rw)

and in 12.04 this:

  mount.nfs: timeout set for Sun May 20 13:58:16 2012
  mount.nfs: trying text-based options   'vers=4,addr=192.168.254.98,clientaddr=192.168.254.103'
  mount.nfs: mount(2): No such file or directory
  mount.nfs: trying text-based options 'addr=192.168.254.98'
  mount.nfs: prog 100003, trying vers=3, prot=6
  mount.nfs: trying 192.168.254.98 prog 100003 vers 3 prot TCP port 2049
  mount.nfs: prog 100005, trying vers=3, prot=17
  mount.nfs: trying 192.168.254.98 prog 100005 vers 3 prot UDP port 892
  192.168.254.98:/volume1/Svend on /media/SvendDS type nfs (rw)

It turns out to be the second line ("trying text-based options 'vers=4 ..") that takes all the time.

Any idea how to solve the problem?

Svend Daugaard Pedersen

---

### Post by papibe on 2012-05-20
Hi sdp.

It looks like 12.04 tries to connect using NSFv4 instead of the usual version3. When your server is an Ubuntu server (or any recent Linux distribution), it goes gracefully to version3 if the server doesn't support it.

My guess is that your 'Synology NAS' doesn't know how to handle the request, so the client side tries again using version3.

I haven't been able to find the correct documentation to ground my assessment, and although I found a solution, it was by guessing.

This force in my system (Ubuntu Server 12.04) to use nfs version3:
```
 sudo mount -v -t nfs server:/path/to/share  /mnt  -o**vers=3**
```
note the option **vers=3**

Try that you yours and let us know how it goes.
Regards.


EDIT: I found the documentation. It's on the nfs man (silly me). The official option is called **nfsvers**, but **vers** works the same.

---

### Post by sdp on 2012-05-21
Thank you very much for the answer. Setting the version did it!

My fstab line now looks:

  192.168.254.98:/volume1/Svend /media/SvendDS nfs nouser,atime,auto,rw,dev,exec,suid,nfsvers=3 0 0

Svend Daugaard Pedersen

PS How do you mark the problem solved?

---

### Post by papibe on 2012-05-21
> **sdp said:**
> How do you mark the problem solved?

Like [this]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

:) Regards.

---

### Post by btodd01 on 2013-02-16
> **sdp said:**
> On ubuntu 12.04 the first mount of my Synology NAS using nfs takes a long time (appr. 45 sec). On Ubuntu 10.04 (same computer) it takes only 1-2 secs. The mount line in fstab is the same:

  192.168.254.98:/volume1/Svend /media/SvendDS nfs nouser,atime,auto,rw,dev,exec,suid 0 0

I have examined the mount process. In 10.04 the verboose-option gives this information:

  mount.nfs: timeout set for Sun May 20 12:30:32 2012
  mount.nfs: text-based options: 'addr=192.168.254.98'
  192.168.254.98:/volume1/Svend on /media/SvendDS type nfs (rw)

and in 12.04 this:

  mount.nfs: timeout set for Sun May 20 13:58:16 2012
  mount.nfs: trying text-based options   'vers=4,addr=192.168.254.98,clientaddr=192.168.254.103'
  mount.nfs: mount(2): No such file or directory
  mount.nfs: trying text-based options 'addr=192.168.254.98'
  mount.nfs: prog 100003, trying vers=3, prot=6
  mount.nfs: trying 192.168.254.98 prog 100003 vers 3 prot TCP port 2049
  mount.nfs: prog 100005, trying vers=3, prot=17
  mount.nfs: trying 192.168.254.98 prog 100005 vers 3 prot UDP port 892
  192.168.254.98:/volume1/Svend on /media/SvendDS type nfs (rw)

It turns out to be the second line ("trying text-based options 'vers=4 ..") that takes all the time.

Any idea how to solve the problem?

Svend Daugaard Pedersen


Hi I am trying to do the same thing (use nfs to mount my Synology  NAS.

I found an FAQ that shows how to set up NFS but it looks way different then what you are showing. What is the best doc for setting up NFS. Also your debugging, is that in an nfs error log or ....
what did you do to set up debugging NFS?

when NFS is set up, for the client do I use ipaddress:/homes/user ?? is the remote directory?

Any help would be greatly appreciated

The Synology docs are pretty sparse for using rsync from linux

---

