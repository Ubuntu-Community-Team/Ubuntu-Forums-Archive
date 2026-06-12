---
title: "mount.nfs4: no such device"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by vista.tec on 2011-12-12
Hi,
maybe already posted.
NFS4 client @boot fails Ubuntu 10.04
FSTAB
```
192.168.0.11:/srv/samba/oiti /var/www  nfs4 auto 0  0
```@ boot
```
mount.nfs4: no such device
mountall: mount /var/www [675] terminated with status 32
mount.nfs4: mounting 192.168.0.11:/srv/samba/mydir failed, reason given byu server: no such file or directory
```this for 3 times

Anyway if I go to M manual or S to skip both cases I can mount it with a charm

Please advise

bsa

---

### Post by vista.tec on 2011-12-13
Ahi ! 
Poor man :(

Nobody reply ...

---

### Post by vista.tec on 2011-12-13
Ok,
this 3D is autoresolved :D

```
 
192.168.0.11:/  /var/www        nfs4    _netdev,auto,nolock  0  0
instead of
192.168.0.11:/srv/samba/oiti  /var/www        nfs4    _netdev,auto,nolock  0  0

```now @boot nfs4 mount correctly


bsa

---

### Post by vista.tec on 2011-12-14
Forgotten ... well explained

[http://www.bermweb.net/?p=41](http://www.bermweb.net/?p=41)

bsa

---

