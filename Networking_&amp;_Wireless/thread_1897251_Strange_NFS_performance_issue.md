---
title: "Strange NFS performance issue"
date: 2011-12-18
forum: Networking &amp; Wireless
---

### Post by SwedishWings on 2011-12-18
I have an Ubuntu 10.04 server and an 11.10 client that mounts the server via NFS, like this:
/etc/exports in server:
```
/mnt/320g 192.168.1.0/24(rw,async,no_subtree_check,insecure)
```
/etc/fstab in client:
```
192.168.1.10:/mnt/320g /media/mserver nfs rw,user,noacl,nocto,async 0 0
```

The funny thing is this; if I copy a 300Mb file from the server to the client, i get about 10Mb/s transfer rate, but if i copy a 1Gb file, i get about 2.9Mb/s. The slower copy shows up instantly if I use a GUI copy (drag and drop) - it starts off much slower with the 1Gb file. Both machines performs well on hdparm, and connection is steady at 10Mb/s with iperf, regardless of amount of data sent/received.

The server only have about 750Mb memory. Could it be a caching issue on the server?

Any ideas?

Thanks,
Mike

---

