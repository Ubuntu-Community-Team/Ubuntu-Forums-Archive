---
title: "How to make Ubuntu computers show up on Cisco Switches"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by nutznboltz on 2010-01-25
1. Run:

```
sudo aptitude install build-essential libpcap-dev
```

2. Download the source code from here:

[http://snar.spb.ru/prog/cdpd/](http://snar.spb.ru/prog/cdpd/)

(actual file is [http://snar.spb.ru/prog/cdpd/cdpd-1.0.4.tgz](http://snar.spb.ru/prog/cdpd/cdpd-1.0.4.tgz) )
(md5 7fb767a2e1644456c817bf8477406117  cdpd-1.0.4.tgz )

3. Run:

```
tar xfz cdpd-1.0.4.tgz
cd cdpd-1.0.4
./configure
make all
mkdir -p /usr/local/man/man8
cp cdpd.8 /usr/local/man/man8
cp cdpd /usr/local/sbin
/usr/local/sbin/cdpd -a
```

4. log into Cisco switch and run

```
show cdp neighbors
```

output will look like

```
Device ID        Local Intrfce     Holdtme    Capability  Platform  Port ID
ubuntubox        Fas 0/21          119            H       x86-64    eth0
ubuntubox        Fas 0/22          119            H       x86-64    eth1

```

This software is already part of the FreeBSD and Mac OS X ports trees (software repositories.)  How can it be added to Ubuntu?

[http://www.freshports.org/net-mgmt/cdpd/](http://www.freshports.org/net-mgmt/cdpd/)
[http://cdpd.darwinports.com/](http://cdpd.darwinports.com/)

Thanks

---

### Post by nutznboltz on 2010-01-26
> **nutznboltz said:**
> This software is already part of the FreeBSD and Mac OS X ports trees (software repositories.)  How can it be added to Ubuntu?

Anyone?

---

### Post by nutznboltz on 2010-01-26
> **nutznboltz said:**
> Anyone?

Never mind, I found it myself by just going through a long list of google search keyword permutations.

[https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

---

### Post by nutznboltz on 2010-01-26
[https://bugs.launchpad.net/ubuntu/+bug/512809](https://bugs.launchpad.net/ubuntu/+bug/512809)

---

