---
title: "Totem is broken after fresh 9.10 install"
date: 2009-11-20
forum: Multimedia Software
---

### Post by sharp11 on 2009-11-20
Totem plays DVDs for a while and then stops working, gets jumpy, becomes incomprehensible, etc. I don't know how to debug this and I'm kind of exhausted after all the other problem-fixing I've done on this version. I'm considering downgrading to an older distro, but have already invested a lot of time in this install.

Does Ubuntu not support legacy hardware anymore? My system is on the older side. Here's lshw for my DVD player:

```
           *-cdrom:1
                description: DVD-RAM writer
                product: DVD A  DH20A4P
                vendor: ATAPI
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 9P55
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
```

---

