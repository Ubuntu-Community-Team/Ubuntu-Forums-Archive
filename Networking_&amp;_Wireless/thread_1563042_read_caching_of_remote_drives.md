---
title: "read caching of remote drives?"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by iaw4 on 2010-08-28
I have two linux computers.  I prefer to use a network drive (could be sshfs or nfs mounted) as the home directory for both.  this drive will sit on one linux computer, which I shall just call the server.  the reason is that I want to maintain only one definitive copy of /home, and have everything be transparently available on both server and client  most data on /home/ tends to change only very slowly.  I have a choice of file systems, although I like common standards (such as ext4).  I presume this is a fairly common setup.

now, the clieny has a large local hard drive that is mostly empty.  I mean gigabytes.  is it possible to use this local drive on the client for aggressive read caching of the remote network drive on the server?  this way, most of the read access by the client is likely to be a confirmation of whether the local file is still current.  of course, writes still have to be executed remotely.  and a slow daemon could update the local disk read cache of the remote drive.

how would I do this?

/iaw

---

### Post by Lars Noodén on 2010-08-28
AFS automatically caches data locally.  It is a bit heavier than NFS, however.

---

### Post by iaw4 on 2010-08-28
thank you.  is there a ubuntu installation guide for AFS?  is it easy to set up for a one-server one-client type of installation?  is the server in the linux kernel, too, or just the client (or nothing)?

wikipedia states that "A fourth implementation exists in the Linux kernel source code since at least version 2.6.10[3]. Committed by Red Hat, this is a fairly simple implementation still in its early stages of development and therefore incomplete.[4]"  incomplete is fine.  hope it is stable, though.

actually, I just found a guide:  [http://bobcares.com/blog/?p=501](http://bobcares.com/blog/?p=501) .  so I can play with it...

/iaw

---

### Post by iaw4 on 2010-08-28
just found another answer---http://lwn.net/Articles/100321/ (cacheFS).  it seems to be in the kernel, and do this sort of caching.

---

