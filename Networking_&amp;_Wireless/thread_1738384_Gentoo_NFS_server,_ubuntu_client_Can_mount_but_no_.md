---
title: "Gentoo NFS server, ubuntu client: Can mount but no files"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by dylanthomasfan on 2011-04-24
Hello,

I am running gentoo-2.6.37-r4 on an AMD64 machine A=10.10.1.3. I am sharing this with another machine, a Ubuntu maverick, with IP 10.10.1.4 (B). So, I export my filesystem like so on machine A.

```
MACHINE-A # more /etc/exports
/storage/    10.10.1.4(async,ro,no_subtree_check,all_squash,anonuid=1000,anongid=1000)

MACHINE-A # ls -l /storage
total 12
drwxrwxrwx 41 someuser someuser 4096 Apr 13 21:30 mp3
drwxrwxrwx 33 someuser someuser 4096 Apr 18 21:54 music
drwxrwxrwx  4 someuser someuser 4096 Apr 12 21:12 photos
```I then ```
exportfs -av
``` and then ```
/etc/init.d/nfs restart
``` and confirm that nfs is running and will accept both NFS version 2 and 3:

```

MACHINE-A # rpcinfo -p
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  46481  status
    100024    1   tcp  54519  status
    100005    1   udp  47437  mountd
    100005    1   tcp  48181  mountd
    100005    2   udp  47768  mountd
    100005    2   tcp  53891  mountd
    100005    3   udp  42775  mountd
    100005    3   tcp  44776  mountd
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100021    1   udp  34369  nlockmgr
    100021    3   udp  34369  nlockmgr
    100021    4   udp  34369  nlockmgr
    100021    1   tcp  56195  nlockmgr
    100021    3   tcp  56195  nlockmgr
    100021    4   tcp  56195  nlockmgr

```On my Ubuntu machine, I mount the share like so:

```
UBUNTUMACHINE-B # mount MACHINE-A:/storage/ /nfs/
```Then, I am able to see directories music, photos and mp3 when I do

```
UBUNTUMACHINE-B # ls /nfs/
```but when I get into one of the directories, I don't see any files. I suspect this is a file permissions issue, but how do I go about fixing this?

---

### Post by dylanthomasfan on 2011-04-25
It happens to be a rather silly error on my part. I have now resolved the problem, and I see the remote files on the client exactly with the same permissions etc. The key idea is that on the NFS server, each mount point gets an export--at least that's how I re-cast the exports and now I see all the files. Let me explain.

On MACHINE-A, I have the following mount points:
```

/dev/sdb1           /storage/music
/dev/sdb2           /storage/mp3
/dev/sdb3           /storage/photos

```Now, the /etc/exports file should read
```

/storage/music/   10.10.1.4(async,ro,no_subtree_check,all_squash,anonuid=1000,anongid=1000)
/storage/mp3/   10.10.1.4(async,ro,no_subtree_check,all_squash,anonuid=1000,anongid=1000)
/storage/photos/   10.10.1.4(async,ro,no_subtree_check,all_squash,anonuid=1000,anongid=1000)

```You will note that earlier, I was (incorrectly) exporting /storage like so:
```
/storage/    10.10.1.4(async,ro,no_subtree_check,all_squash,anonuid=1000,anongid=1000) 
```I have the same user with the same UID/GID on both machines, so I don't need the anonuid and anongid clauses in the exports.

I think it is easy to make this mistake, so I wanted to post this resolution to help other folks. Thanks for your time.

---

