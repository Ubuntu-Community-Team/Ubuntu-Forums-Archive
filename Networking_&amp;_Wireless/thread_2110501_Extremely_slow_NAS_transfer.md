---
title: "Extremely slow NAS transfer"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by dryicebomb on 2013-01-30
Hello,

I'm having some trouble with very poor performance with some NFS shares that I have. I'm running an ubuntu 12.04 LTS 64-bit Desktop with nfs-kernel-server 1.2.0. I have a Volume called /Videos that is formatted with btrfs. I'm typically transferring files larger than 500MB, and when doing so, i'm getting speeds of around 250kb/s (according to rsync) The machine that I'm transferring from is an ubuntu 12.10 Desktop as well, and the share is mounted via fstab. When I unmount the share, and mount it as a cifs share, it transferes very fast, around 15MB/s which is a huge improvement over mounting it as NFS. Both machines are connected to a 10/100 switch. For testing purposes, I tried connecting them with a crossover cable to rule out switch problems and the results were the same. Any help would be appreciated. Here is my /etc/exports line

/Videos      10.30.50.0/24(rw,sync,no_root_squash,no_subtree_check)

Thanks,

---

### Post by dannyboy79 on 2013-01-30
have you optimized your NFS server and client settings? [http://nfs.sourceforge.net/nfs-howto/ar01s05.html](http://nfs.sourceforge.net/nfs-howto/ar01s05.html)

PS you're referring to the NFS protocol (network file system) as NAS. NAS is merely an abbreviation for "network attached storage". A NAS is a device and not a protocol. NAS can have various protocols like ftp, nfs, samba, sftp. Just a heads up so you refer to it correclty in the future.

---

### Post by dryicebomb on 2013-01-30
I have not tried the optimization yet. I will try that tonight. Thank you.

---

### Post by dryicebomb on 2013-01-30
> **dannyboy79 said:**
> have you optimized your NFS server and client settings? [http://nfs.sourceforge.net/nfs-howto/ar01s05.html](http://nfs.sourceforge.net/nfs-howto/ar01s05.html)

PS you're referring to the NFS protocol (network file system) as NAS. NAS is merely an abbreviation for "network attached storage". A NAS is a device and not a protocol. NAS can have various protocols like ftp, nfs, samba, sftp. Just a heads up so you refer to it correclty in the future.

:redface: Your right, I have edited my original post as to not confuse others.

---

### Post by dryicebomb on 2013-01-30
> **dannyboy79 said:**
> have you optimized your NFS server and client settings? [http://nfs.sourceforge.net/nfs-howto/ar01s05.html](http://nfs.sourceforge.net/nfs-howto/ar01s05.html)

PS you're referring to the NFS protocol (network file system) as NAS. NAS is merely an abbreviation for "network attached storage". A NAS is a device and not a protocol. NAS can have various protocols like ftp, nfs, samba, sftp. Just a heads up so you refer to it correclty in the future.

:redface: Your right, I have edited my original post as to not confuse others.

---

### Post by dryicebomb on 2013-01-30
That guide helped quite a bit, Also after changing it from sync to async things really started moving quite fast.

Thank you for the help

---

### Post by saejin on 2013-02-20
I duplicated your set up, and your results.  With NFS  I see a very fast transfer across the directly connected wire that slows down eventually to bits per hour with large files.

I can not seem to find out what it is either.  Have you made any progress?

---

### Post by dryicebomb on 2013-02-21
saejin,

What ultimately fixed the issue for me was a small change in my /etc/exports file. I changed sync to async, and that really increased the speed. Please read section 5.9 for the differences between sync and async, There is also other good information about optimizing NFS in this article. [http://nfs.sourceforge.net/nfs-howto/ar01s05.html](http://nfs.sourceforge.net/nfs-howto/ar01s05.html)

---

