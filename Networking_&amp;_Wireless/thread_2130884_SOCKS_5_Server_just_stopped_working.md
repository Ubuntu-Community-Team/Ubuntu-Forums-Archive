---
title: "SOCKS 5 Server just stopped working??"
date: 2013-03-30
forum: Networking &amp; Wireless
---

### Post by alexandari on 2013-03-30
Hello! I am having trouble with running a socks 5 server with the **Dante** client. After hours I seemed to get it working just fine. But not for long. About 5 minutes after working,it just went down. I have no idea why,it just did. And since that happened,when I try to start it again all the log file outputs is this

```
Mar 30 05:33:54 (1364614434) danted[2360]: socks_seteuid(): old: 0, new: 1000
Mar 30 05:33:54 (1364614434) danted[2360]: socks_reseteuid(): current: 1000, new: 0
Mar 30 05:33:54 (1364614434) danted[2360]: socks_seteuid(): old: 0, new: 65534
Mar 30 05:33:54 (1364614434) danted[2360]: socks_reseteuid(): current: 65534, new: 0
Mar 30 05:33:54 (1364614434) danted[2360]: fixsettings(): setting the libwrap uid to 0 is not recommended
Mar 30 05:33:54 (1364614434) danted[2360]: serverinit(): bind(84.40.90.118.1080): Cannot assign requested address (errno = 99)
Mar 30 05:33:54 (1364614434) danted[2360]: sockdexit(): terminating
```

I have no idea what error number 99 is. There are no other processes running that are using port 1080,I checked that. Any help would be appreciated :(

---

### Post by alexandari on 2013-03-31
bump

---

### Post by alexandari on 2013-04-01
bump 2

---

### Post by alexandari on 2013-04-02
oh come on

---

### Post by alexandari on 2013-04-16
bump

---

### Post by Genesissx on 2013-06-17
I have no experience with Dante so it might be just my misinterpretation but shouldn't it be ip:port instead of ip.port?

---

