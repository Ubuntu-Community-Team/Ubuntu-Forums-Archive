---
title: "NFS - slow write speed"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by marshmallow1304 on 2010-07-06
I just tried NFS for the first time after reading that it's considerably faster than SSHFS, which I currently use, but I'm experiencing slow write speeds and problems while copying files in nautilus.


Server (swaim) - Debian Lenny:
[QUOTE=/etc/exports]/data system76-pc(rw,sync,no_subtree_check)[/QUOTE]


Client (system76-pc) - Ubuntu 10.04
```
mount -t nfs swaim.local:/data Desktop/nfsmount
```


A 1.2 GB file over NFS:

Write:
```
dd if=Desktop/new\ downloads/Pioneer.One.S01E01.720p.x264-VODO/Pioneer.One.S01E01.720p.x264-VODO.mkv of=Desktop/nfsmount/pioneer-test.mkv
2289665+1 records in
2289665+1 records out
1172308607 bytes (1.2 GB) copied, 212.575 s, 5.5 MB/s
```

Read:
```
dd if=Desktop/nfsmount/pioneer-test.mkv of=Desktop/pioneer-test.mkv
2289665+1 records in
2289665+1 records out
1172308607 bytes (1.2 GB) copied, 115.838 s, 10.1 MB/s
```


Next I copied the same file in Nautilus:
sshfs write: 3:51  (~4.84 MB/s)
sshfs read:  3:42  (~5.04 MB/s)
nfs write:   3:46  (~4.85 MB/s)  (File Operations dialog (and nautilus) froze during the transfer, but it finished eventually)
nfs read:    2:28  (~7.55 MB/s)


Are these reasonable speeds?  I was excited after seeing these [benchmarks]("http://prokop.ae.krakow.pl/projects/fs_benchmark.html"), but I'm not seeing impressive results other than read speed.

---

### Post by marshmallow1304 on 2010-07-11
bump

Also, when copying files (client->server) in Nautilus, I get extremely heavy RAM usage on the client (copying 11 GB in 22 files with Firefox and Nautilus open).  free -m shows 31 M free out of 3930.  The transfer started very fast (~25 MB/s) then dropped down to ~3-5 MB/s with intermittent freezing.

Edit: Same thing using cp -r.  I had to kill the transfer because everything else was freezing up.

---

