---
title: "NFSv3 really slow?"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by finite9 on 2009-05-31
My server shares out NFS mount points with:

```
/mnt/raid1/backups	192.168.1.10*(rw,sync,no_subtree_check)
```

my laptop connects to the share using:

```
sudo mount -t nfs -o proto=tcp,nfsvers=3,sync montblanc:/mnt/raid1/backups /media/backups
```

It's transferring files to the server at half the speed of what it should be.  I compare it to an SSH (SCP) file transfer of a 18GB file to the server.  SCP reports 11-12MB/s and takes 27 mins according to /usr/bin/time.  this is over a wired 100mbit network.

Transferring the same file over NFS mount takes 47mins according to time ( I do not see transfer rate with 'cp' but it is probably 6-7MB/s.

Why is it so slow?  Do I need to tweak the mount settings and if so how?

---

### Post by finite9 on 2009-06-08
I find I get zero replies to my posts these days.  If you want to do a job right, you need to do it yourself:

Noone spotted the 'sync' option?

God it's slow as a zombie without legs.  async may cause dataloss if export unmounted unexpectedly blah blah blah, but if you have read only exports anyway, then does not matter.  enabling async went up to 100MBit LAN speeds immediately.  Enabling rsize and wsize=32768 helped as well, but this was not the main issue.

Dont even get me started on NFSv4.  what a mess.

---

